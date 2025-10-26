# Template Selection Wizard

**Purpose**: Guide users to the most appropriate pattern-based template for their project.

**Location**: `ouroboros/intelligence/template-selector.md`

---

## Overview

The Template Selector is an intelligent wizard that helps users choose the right template based on their project characteristics, NOT technology stack. It uses the same pattern recognition logic as the Pattern Recognizer but operates in an interactive, question-driven mode.

**Key Principles**:
- Ask about characteristics, not technologies
- Guide users to appropriate pattern
- Allow manual override if desired
- Provide examples to clarify patterns

---

## Selection Process

### Step 1: Project Type Classification

**Question**: What are you building/creating/planning?

**Options**:
1. **Building something new** (creating from scratch)
2. **Improving something existing** (refining, optimizing, redesigning)
3. **Investigating something** (researching, analyzing, exploring)
4. **Automating something** (workflow, deployment, infrastructure)
5. **Managing resources** (CRUD operations, data management)

**Routing**:
- Building → Ask about workflow characteristics
- Improving → Likely **Creative Iterative Process**
- Investigating → Likely **Exploratory Research**
- Automating → Likely **Modern Dev Workflow**
- Managing → Likely **Resource Management**

---

### Step 2: Workflow Characteristics (if "Building something new")

**Question**: Which best describes your workflow?

**Option A: Step-by-step with clear stages**
- ✅ Each step depends on the previous one
- ✅ Validation needed at each stage
- ✅ Rollback capability important
- ✅ Examples: Data pipeline, deployment script, event planning, user guide creation

**Recommendation**: **Structured Sequential Workflow**

---

**Option B: Multiple revisions and feedback**
- ✅ Will iterate based on feedback
- ✅ Quality is somewhat subjective
- ✅ Exploring alternatives before finalizing
- ✅ Examples: UI/UX design, blog writing, vacation planning, performance tuning

**Recommendation**: **Creative Iterative Process**

---

**Option C: Managing things (create, read, update, delete)**
- ✅ CRUD operations needed
- ✅ Data validation important
- ✅ Need to track state and history
- ✅ Examples: REST API, knowledge base, budget tracker, asset library

**Recommendation**: **Resource Management**

---

**Option D: Don't know scope yet, need to explore**
- ✅ Unknown scope at start
- ✅ Research and discovery needed first
- ✅ Will identify patterns and focus areas
- ✅ Examples: Performance investigation, competitive analysis, vendor selection

**Recommendation**: **Exploratory Research**

---

**Option E: Automation-first, deployment-focused**
- ✅ CI/CD pipeline needed
- ✅ Infrastructure as code
- ✅ Containerization/orchestration
- ✅ Observable and monitored
- ✅ Examples: Microservice, doc-as-code, GitOps infrastructure, workflow automation

**Recommendation**: **Modern Dev Workflow**

---

### Step 3: Confidence Check

**Question**: Does this pattern sound right?

**Pattern**: [Detected Pattern Name]

**Characteristics**:
- [Characteristic 1]
- [Characteristic 2]
- [Characteristic 3]

**Typical use cases**:
- [Example 1]
- [Example 2]
- [Example 3]

**Options**:
- ✅ **Yes, this is right** → Proceed to template generation
- 🔄 **Not quite, let me choose manually** → Show all 5 patterns with descriptions
- ❓ **Tell me more about the patterns** → Show detailed pattern comparison

---

### Step 4: Template Generation

**Templates to generate**:
- ✅ `requirements.md` (from pattern-specific template)
- ✅ `design.md` (from pattern-specific template)
- ✅ `tasks.md` (from pattern-specific template)

**Output location**: `ouroboros/specs/[project-name]/`

**Next steps**:
1. Review generated templates
2. Fill in [placeholder] sections
3. Customize for your specific project
4. Use cross-domain examples for inspiration

---

## Pattern Comparison Matrix

| Pattern | Workflow Style | Key Trait | Best For | Examples |
|---------|---------------|-----------|----------|----------|
| **Structured Sequential** | Step-by-step | Clear stages | Pipelines, guides, deployment | Data pipeline, user guide, event planning |
| **Creative Iterative** | Feedback loops | Refinement cycles | Design, writing, planning | UI/UX, blog posts, vacation itinerary |
| **Resource Management** | CRUD operations | State tracking | APIs, databases, management | REST API, knowledge base, budget tracker |
| **Exploratory Research** | Discovery-driven | Unknown scope | Investigation, analysis | Performance tuning, competitive analysis, vendor selection |
| **Modern Dev Workflow** | Automation-first | Observable | DevOps, GitOps, automation | Microservice, doc-as-code, infrastructure |

---

## Interactive Selection Flow

```
START
  ↓
What are you building?
  ├─ Building new → Workflow type?
  │   ├─ Step-by-step → Structured Sequential
  │   ├─ Iterative → Creative Iterative
  │   ├─ CRUD → Resource Management
  │   ├─ Unknown scope → Exploratory Research
  │   └─ Automation-first → Modern Dev Workflow
  ├─ Improving → Creative Iterative (likely)
  ├─ Investigating → Exploratory Research
  ├─ Automating → Modern Dev Workflow
  └─ Managing → Resource Management
  ↓
Confidence check
  ├─ Yes → Generate templates
  ├─ Not quite → Manual selection
  └─ Tell me more → Show comparison
  ↓
Generate templates
  ↓
DONE
```

---

## Template Customization Guide

After template generation, users should:

### For ALL patterns:
1. **Replace placeholders**:
   - `[Project Name]` → Actual project name
   - `[Description]` → Actual description
   - All `[placeholders]` in brackets

2. **Review cross-domain examples**:
   - Find examples similar to your domain
   - Adapt patterns to your specific needs

3. **Customize acceptance criteria**:
   - Make them testable and measurable
   - Add domain-specific criteria

4. **Adjust phase structure**:
   - Add/remove phases as needed
   - Identify parallelization opportunities

### Pattern-Specific Customization:

**Structured Sequential**:
- Define all stages clearly
- Specify validation gates
- Document rollback procedures

**Creative Iterative**:
- Define quality criteria (subjective measures)
- Set max iterations (prevent infinite loops)
- Identify stakeholders for feedback

**Resource Management**:
- Define resource schema
- Choose soft delete vs hard delete
- Design permission model

**Exploratory Research**:
- Define research questions
- Choose breadth-first data sources
- Plan hypothesis testing (if applicable)

**Modern Dev Workflow**:
- Choose CI/CD platform
- Select IaC tool
- Define observability stack

---

## Implementation as CLI Command

### Usage

```bash
ouroboros init
```

**Interactive prompts**:
1. What's your project name?
2. What are you building? [5 options]
3. [Follow-up questions based on choice]
4. Does [pattern] sound right? [yes/no/show-more]
5. Generate templates? [yes/no]

**Output**:
```
✅ Created ouroboros/specs/[project-name]/
   ├── requirements.md (Structured Sequential pattern)
   ├── design.md (Structured Sequential pattern)
   └── tasks.md (Structured Sequential pattern)

Next steps:
1. Review templates in ouroboros/specs/[project-name]/
2. Fill in [placeholder] sections
3. Review cross-domain examples for inspiration
4. Run: ouroboros validate [project-name]
```

---

## Implementation as Agent/Skill

### Usage

```
Help me choose a template for my project
```

**Agent workflow**:
1. Ask classification question
2. Present pattern recommendation
3. Confirm or refine
4. Generate templates
5. Provide customization guidance

**Agent response format**:
```markdown
Based on your description, I recommend the **[Pattern Name]** pattern.

This pattern is characterized by:
- [Characteristic 1]
- [Characteristic 2]
- [Characteristic 3]

Typical use cases:
- [Example 1]
- [Example 2]

Does this sound right? I can:
1. Generate templates for this pattern
2. Show you other patterns
3. Explain patterns in more detail
```

---

## Learning & Adaptation

The Template Selector can improve over time by:

### Tracking Selection Accuracy

**After project completion**:
- Was the suggested pattern correct?
- Did the user switch patterns mid-project?
- What characteristics led to pattern match?

**Store learnings**:
```json
{
  "pattern": "structured-sequential",
  "user_keywords": ["pipeline", "stages", "sequential"],
  "project_type": "data-pipeline",
  "pattern_match_accurate": true,
  "confidence": 0.95
}
```

### Improving Question Phrasing

**Track**:
- Which questions cause confusion?
- Which options are most frequently chosen?
- Where do users need clarification?

**Adapt**:
- Rephrase confusing questions
- Add examples to clarify options
- Reorder options by popularity

### Expanding Pattern Library

**When users succeed with custom patterns**:
- Offer to extract as new template
- Generalize pattern characteristics
- Add to pattern library

---

## Edge Cases & Fallbacks

### Case 1: No Pattern Fits Well

**Symptom**: User says "Not quite" to all patterns

**Resolution**:
1. Ask more detailed questions about workflow
2. Suggest hybrid approach (combine patterns)
3. Offer to start with closest pattern and customize
4. Provide contact for custom pattern creation

---

### Case 2: Multiple Patterns Apply

**Symptom**: Project has characteristics of 2+ patterns

**Example**: Building a REST API (Resource Management) with GitOps deployment (Modern Dev Workflow)

**Resolution**:
1. Identify primary pattern (core functionality)
2. Identify secondary pattern (supporting aspects)
3. Generate primary pattern templates
4. Note where to incorporate secondary pattern elements
5. Provide guidance on pattern combination

---

### Case 3: User Unsure of Workflow

**Symptom**: User doesn't know how they'll approach the project

**Resolution**:
1. Default to **Exploratory Research** pattern (discovery-first)
2. Plan initial research phase
3. Re-run pattern detection after research complete
4. Migrate to appropriate pattern

---

## Integration with Pattern Recognizer

The Template Selector works in tandem with the Pattern Recognizer:

**Template Selector**: Used at **project initialization** (no requirements/design yet)
- Question-driven
- Interactive
- Guides user to pattern

**Pattern Recognizer**: Used when **requirements/design exist**
- Analysis-driven
- Automatic
- Validates pattern choice

**Workflow**:
1. User runs `ouroboros init`
2. Template Selector suggests pattern via questions
3. Templates generated
4. User fills in requirements/design
5. Pattern Recognizer validates pattern choice
6. If mismatch: Suggest pattern change or confirm override

---

## Success Metrics

**Template Selector is successful when**:
- ≥85% of users accept first suggested pattern
- ≥90% of users complete template generation
- ≥75% pattern accuracy (validated post-project)
- <2 minutes average time to select pattern

**User satisfaction measured by**:
- Did templates match project needs?
- Were templates helpful starting points?
- Would user use Template Selector again?

---

## Future Enhancements

### V2: Smart Defaults

- Pre-fill common fields based on pattern
- Suggest typical acceptance criteria
- Recommend phase structures
- Estimate context/time budgets

### V3: Template Previews

- Show template snippets before generation
- Preview task structure
- Compare pattern templates side-by-side

### V4: Team Templates

- Share custom templates across team
- Template marketplace (community patterns)
- Pattern voting and ratings

### V5: AI-Enhanced Selection

- Natural language project description
- LLM-based pattern detection
- Automatic template customization

---

## Example Session

```
$ ouroboros init

Welcome to Ouroboros! Let's set up your project.

Project name: customer-portal-api

What are you building?
1. Building something new
2. Improving something existing
3. Investigating something
4. Automating something
5. Managing resources

Your choice: 5

Great! Managing resources typically involves CRUD operations, data
validation, and state tracking. Is that correct for your project?

(y/n): y

Perfect! I recommend the Resource Management pattern.

This pattern is characterized by:
- CRUD operations (Create, Read, Update, Delete)
- Data validation and constraints
- State tracking and persistence
- Access control and permissions

Typical use cases:
- REST APIs
- Knowledge bases
- Budget trackers
- Asset libraries

Does this sound right?
1. Yes, generate templates
2. No, let me choose manually
3. Tell me more about patterns

Your choice: 1

✅ Creating templates for customer-portal-api...

Created:
- ouroboros/specs/customer-portal-api/requirements.md
- ouroboros/specs/customer-portal-api/design.md
- ouroboros/specs/customer-portal-api/tasks.md

Next steps:
1. Open requirements.md and fill in [placeholders]
2. Review cross-domain examples for inspiration
3. Define your resource schema
4. Specify CRUD operations needed
5. Run: ouroboros validate customer-portal-api

Happy building! 🐍
```

---

**Generated by Ouroboros Framework**
**Component**: Template Selection Wizard
**Version**: 1.0
**Last Updated**: 2025-10-25

---

## Implementation Checklist

For developers implementing this wizard:

- [ ] Create interactive CLI command (`ouroboros init`)
- [ ] Implement question flow logic
- [ ] Create template generation functions
- [ ] Add pattern comparison display
- [ ] Implement confirmation workflow
- [ ] Add helpful examples and descriptions
- [ ] Test all edge cases
- [ ] Integrate with Pattern Recognizer
- [ ] Add success metrics tracking
- [ ] Document API for programmatic use
