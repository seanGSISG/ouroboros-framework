# Design - Dynamic Template Generation

**Pattern**: Modern Development Workflow (with Exploratory Research elements)

**Design Philosophy**: Question → Context → Generate → Validate → Refine

---

## Architecture Overview

**Current System** (Broken):
```
User runs /ou-new-spec
  ↓
Select pattern
  ↓
Copy static template files (FULL OF TECH JARGON)
  ↓
User manually rewrites 95% of content
```

**New System** (Dynamic):
```
User runs /ou-new-spec
  ↓
Gather context (domain, pattern, project details)
  ↓
LLM generates contextual spec (80% customized)
  ↓
User reviews and refines (minimal editing)
```

---

## Phase 1 Design: Context Gathering

**Question Flow**:

1. **Feature Name** (unchanged)
   - Input: kebab-case feature name
   - Example: "vacation-planner", "api-docs", "user-auth"

2. **Project Domain** (NEW - replaces confusing "project type" question)
   ```
   What domain is this project in?

   1. Software Development (APIs, CLIs, web apps, scripts)
   2. Documentation (user guides, API docs, blog posts, tutorials)
   3. Planning & Organization (vacation planning, event planning, workflows)
   4. Creative Work (design systems, content creation, branding)
   5. Data & Analysis (research, investigation, optimization)
   6. Not sure / Multiple domains
   ```

3. **Pattern-Specific Questions** (domain-aware)

   **If Software Development**:
   ```
   Does this involve managing stored information (creating, viewing, editing, deleting)?
   → Yes: Resource Management pattern
   → No: Continue to next question

   Is this primarily about automation and deployment?
   → Yes: Modern Dev Workflow pattern
   → No: Continue...
   ```

   **If Documentation**:
   ```
   Is the structure well-defined with clear sections?
   → Yes: Structured Sequential Workflow
   → No: Creative Iterative Process
   ```

   **If Planning & Organization**:
   ```
   Do you know all the steps upfront?
   → Yes: Structured Sequential Workflow
   → No: Exploratory Research or Creative Iterative
   ```

4. **Scope Questions** (pattern-dependent)

   **Example for Resource Management**:
   ```
   What kind of resources are you managing?
   > "Vacation bookings"

   What are the main operations?
   > "Book flights, reserve hotels, plan activities"
   ```

   **Example for Documentation**:
   ```
   What are you documenting?
   > "API endpoints for user service"

   Who is the audience?
   > "External developers"
   ```

**Data Structure**:
```typescript
interface SpecContext {
  featureName: string;          // "vacation-planner"
  domain: Domain;               // "planning"
  pattern: Pattern;             // "structured-sequential"
  scopeAnswers: {
    [key: string]: string;      // Custom Q&A per pattern
  };
  generatedAt: timestamp;
}
```

---

## Phase 2 Design: Template Generation

**Generation Strategy**:

Use LLM with structured prompt to generate specs:

```markdown
You are generating an Ouroboros spec for a {pattern} project in the {domain} domain.

Feature: {featureName}
Domain: {domain}
Pattern: {pattern}

User provided context:
{scopeAnswers}

Generate a {requirements|design|tasks}.md file that:
1. Follows {pattern} structure
2. Uses domain-appropriate language ({domain}-specific terminology)
3. References user's actual project ({featureName}, {scopeAnswers})
4. NO tech jargon unless domain is "software-development"
5. 80% of content is specific to this project

Pattern structure:
{pattern-specific-template-structure}

Output format: {format-spec}
```

**Pattern Templates** (Structure Only):

Store minimal structural templates:

```markdown
# tasks-structure-resource-management.md

### Phase 1: Foundation (Sequential 🐌)
**Goal**: {foundation_goal}
- [ ] **🐌 1.1 {task_name}**
  - {subtask_1}
  - {subtask_2}

### Phase 2: Core Operations ({n} parallel 🐍)
**Goal**: {core_goal}
- [ ] **🐍 2.1 {operation_1}**
- [ ] **🐍 2.2 {operation_2}**
...
```

LLM fills in the `{placeholders}` based on context.

**Examples of Generated Output**:

**Vacation Planner (Planning domain, Structured Sequential)**:
```markdown
### Phase 1: Foundation (Sequential 🐌)
**Goal**: Research destinations and constraints

- [ ] **🐌 1.1 Define vacation parameters**
  - Set budget limits
  - Determine travel dates and duration
  - List must-see destinations
  - _Context: ~5K tokens_
  - _Duration: ~8 minutes_
```

**API Docs (Documentation domain, Structured Sequential)**:
```markdown
### Phase 1: Foundation (Sequential 🐌)
**Goal**: Structure documentation outline

- [ ] **🐌 1.1 Create documentation structure**
  - Define main sections (Authentication, Endpoints, Errors)
  - Create template for each endpoint
  - Establish code example format
  - _Context: ~8K tokens_
  - _Duration: ~10 minutes_
```

**User Auth (Software Development, Resource Management)**:
```markdown
### Phase 1: Foundation (Sequential 🐌)
**Goal**: Build core authentication functionality

- [ ] **🐌 1.1 Implement user model and database schema**
  - Define User table (id, email, password_hash, created_at)
  - Set up database migrations
  - Create indexes for performance
  - _Context: ~12K tokens_
  - _Duration: ~15 minutes_
```

**Notice**: Each uses domain-appropriate language and references the actual project!

---

## Phase 3 Design: Validation & Refinement

**Automated Validation**:

Check generated specs for:
1. **Pattern compliance**: Phases match pattern structure
2. **Jargon detection**: Flag tech-specific terms in non-code domains
3. **EARS format**: Requirements follow EARS syntax
4. **Parallelization logic**: Tasks properly marked 🐍/🐌

**Validation Rules**:
```yaml
# jargon-detector.yaml
forbidden_terms_non_code:
  - Docker
  - Kubernetes
  - CI/CD
  - GitHub Actions
  - Terraform
  - API (unless domain = software-development OR docs)
  - Database (unless domain = software-development)
  - Container
  - Deploy

allowed_terms_by_domain:
  software-development: [all terms]
  documentation: [API, endpoint, code example]
  planning: [itinerary, booking, schedule]
  creative: [design, mockup, iteration, feedback]
```

**User Review Flow**:

```
Generated spec preview shown
  ↓
User options:
  1. Looks great, save it
  2. Refine (ask follow-up questions, regenerate)
  3. Start over with manual template
  ↓
If refined: Store new answers, regenerate
If saved: Write files + store context
```

---

## Phase 4 Design: Backward Compatibility

**Static Templates** (Fallback):

Keep minimal placeholder templates for users who prefer manual editing:

```markdown
# tasks-placeholder-generic.md

### Phase 1: {Phase Name} (Sequential 🐌)
**Goal**: {What needs to be accomplished}

- [ ] **🐌 1.1 {Task name}**
  - {Subtask description}
  - {Subtask description}
  - _Context: ~XK tokens_
  - _Duration: ~X minutes_
```

**Migration Path**:

Existing specs are untouched. New flag in command:

```bash
/ou-new-spec feature-name --static   # Use old static templates
/ou-new-spec feature-name            # Use new dynamic generation (default)
```

---

## Implementation Approach

**Files to Modify**:

1. `.claude/commands/ou-new-spec.md`
   - Add context gathering questions
   - Add LLM generation logic
   - Add validation step

2. `ouroboros/templates/structures/` (NEW directory)
   - `{pattern}-requirements-structure.md`
   - `{pattern}-design-structure.md`
   - `{pattern}-tasks-structure.md`
   - Contains only structural placeholders, no jargon

3. `ouroboros/validators/jargon-detector.yaml` (NEW)
   - Domain-specific term rules
   - Validation logic

4. `ouroboros/intelligence/template-generator.md` (NEW)
   - LLM prompt templates for generation
   - Domain-specific guidance
   - Examples per pattern × domain

**New Command Flow**:

```typescript
function createSpec(featureName: string, options?: {static: boolean}) {
  if (options?.static) {
    return copyStaticTemplates(featureName);
  }

  // Dynamic generation
  const context = await gatherContext(featureName);
  const specs = await generateSpecs(context);
  const validation = await validateSpecs(specs, context);

  if (!validation.passed) {
    console.log("Issues found:", validation.issues);
    const retry = await askRetry();
    if (retry) return createSpec(featureName);
  }

  const approval = await showPreview(specs);
  if (approval === "refine") {
    const moreContext = await askFollowups();
    return createSpec(featureName, {...context, ...moreContext});
  }

  await saveSpecs(featureName, specs, context);
  await offerExpansion(featureName);
}
```

---

## Token Efficiency

**Current Approach** (wasteful):
- Read 30K token template
- User manually rewrites 95%
- Wasted: ~28.5K tokens

**New Approach** (efficient):
- Read 5K structural template
- Generate 12K customized spec
- User edits 20% = 2.4K tokens changed
- **Savings**: 16K tokens per spec creation

---

## Success Metrics

**Quantitative**:
- User editing time: < 5 minutes (vs 30+ minutes currently)
- Jargon violations: 0 in non-code domains
- Generated content relevance: ≥ 80%
- User approval rate: ≥ 90%

**Qualitative**:
- Non-technical users can create specs without confusion
- Templates feel personalized, not generic
- Framework truly feels tech-agnostic

---

## Risks & Mitigations

**Risk**: LLM generates incorrect pattern structure
**Mitigation**: Strict structural templates + validation

**Risk**: Generation takes too long
**Mitigation**: Use fast model (Haiku) for generation, validate with regex

**Risk**: Users prefer static templates
**Mitigation**: Keep static as option, default to dynamic

**Risk**: Domain detection is wrong
**Mitigation**: Always allow manual override, show preview before saving

---

**Next Step**: Create tasks.md with implementation breakdown

🐍 The serpent designs new scales, each one perfectly fitted to its ever-changing form... 🐍
