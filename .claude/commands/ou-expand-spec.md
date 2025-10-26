---
name: expand-spec
description: Intelligently expand and validate an Ouroboros spec with interactive or automated mode. Transforms basic templates into detailed, execution-ready specifications using pattern recognition, intelligent questioning, and pre-flight validation.
---

# Expand Ouroboros Spec

Transforms a basic spec template into a detailed, validated, execution-ready specification.

## Usage

```bash
/expand-spec {feature-name}
/expand-spec {feature-name} --interactive
/expand-spec {feature-name} --auto
/expand-spec {feature-name} --validate-only
```

## Modes

### Interactive Mode (Default)
Asks targeted questions based on detected pattern to flesh out requirements, design, and tasks.

### Automated Mode (--auto)
Uses pattern defaults and minimal input for rapid expansion.

### Validate Only (--validate-only)
Runs pre-flight validation without making changes.

---

## Process

### Phase 1: Load & Analyze (Sequential 🐌)

**1.1 Load Spec Files**
- Read `ouroboros/specs/{feature-name}/requirements.md`
- Read `ouroboros/specs/{feature-name}/design.md`
- Read `ouroboros/specs/{feature-name}/tasks.md`
- Extract current state and placeholders

**1.2 Detect Pattern**
- Use Pattern Recognizer (`ouroboros/intelligence/pattern-recognizer.md`)
- Analyze keywords, structure, and components
- Identify primary pattern and confidence score
- Detect secondary patterns if applicable

**1.3 Display Analysis**
```
🔍 Spec Analysis: {feature-name}

Pattern Detected: {Pattern Name} ({confidence}% confidence)
Current State:
  - Requirements: {X} defined, {Y} placeholders remaining
  - Design: {X} sections complete, {Y} need details
  - Tasks: {X} phases, {Y} tasks defined

Recommendations:
  - {Recommendation 1}
  - {Recommendation 2}
```

---

### Phase 2: Interactive Expansion (If interactive mode)

**2.1 Requirements Expansion**

Ask pattern-specific questions to expand requirements:

**For Modern Dev Workflow Pattern:**
```
Q1: What is your target deployment environment?
   1. Self-hosted VPS (DigitalOcean, Linode, etc.)
   2. Cloud (AWS, GCP, Azure)
   3. Containerized (Docker + Docker Compose)
   4. Kubernetes cluster
   5. Serverless (Vercel, Netlify, etc.)

Q2: What CI/CD platform will you use?
   1. GitHub Actions
   2. GitLab CI/CD
   3. Jenkins
   4. CircleCI
   5. Other/None

Q3: What's your preferred Infrastructure as Code tool?
   1. Docker Compose (simple)
   2. Terraform
   3. Ansible
   4. CloudFormation
   5. None needed

Q4: What monitoring/observability do you need?
   1. Basic (logs only)
   2. Standard (logs + uptime monitoring)
   3. Advanced (logs + metrics + tracing)
   4. None

Q5: What's your domain/hosting setup?
   1. Have domain, need DNS setup
   2. Need to acquire domain
   3. Using subdomain of existing
   4. Local development only for now
```

**For Resource Management Pattern:**
```
Q1: What resources are you managing? (comma-separated)
   Example: users, posts, comments, categories

Q2: Which operations do you need for each resource?
   1. Full CRUD (Create, Read, Update, Delete)
   2. Read-only
   3. Create and Read only
   4. Custom operations

Q3: What's your data storage approach?
   1. SQL database (PostgreSQL, MySQL)
   2. NoSQL (MongoDB, DynamoDB)
   3. File-based (JSON, Markdown)
   4. In-memory (Redis, cache)

Q4: Authentication/Authorization needed?
   1. Public (no auth)
   2. Simple API key
   3. JWT tokens
   4. OAuth 2.0
   5. Session-based

Q5: Do resources have lifecycle states?
   1. Yes (draft, published, archived, etc.)
   2. No (simple active/deleted)
   3. Not applicable
```

**For Creative Iterative Pattern:**
```
Q1: What are you creating? (blog post, design, plan, etc.)

Q2: How many iteration cycles do you expect?
   1. 2 cycles (draft → final)
   2. 3 cycles (draft → revise → final)
   3. 4+ cycles (multiple revisions)

Q3: Who provides feedback?
   1. Self-review only
   2. Peer review
   3. Stakeholder approval
   4. User testing

Q4: What defines "done"?
   (Describe success criteria)

Q5: Are there multiple alternatives to explore?
   1. Yes, explore 2-3 options before converging
   2. No, single path refinement
```

**For Structured Sequential Pattern:**
```
Q1: How many main stages/phases are in your workflow?
   (Number of sequential stages)

Q2: What validation happens between stages?
   1. Automated tests
   2. Manual review
   3. Quality gates
   4. Approval process

Q3: Can stages run in parallel within themselves?
   1. Yes, parallel subtasks within each stage
   2. No, strictly sequential

Q4: Do you need rollback capability?
   1. Yes, full rollback to any stage
   2. Partial (rollback one step)
   3. No rollback needed
```

**For Exploratory Research Pattern:**
```
Q1: What question are you trying to answer?
   (Research question or hypothesis)

Q2: What data sources will you use?
   1. Web research
   2. Database analysis
   3. Code analysis
   4. User interviews
   5. Experiments/testing

Q3: How will you know you have enough data?
   (Stopping criteria)

Q4: What deliverable do you expect?
   1. Report with recommendations
   2. Decision matrix
   3. Technical findings
   4. Proof of concept
```

**2.2 Design Expansion**

Based on requirements answers, generate specific design sections:

- Fill in technology choices
- Expand component descriptions
- Add architecture diagrams (in markdown/mermaid)
- Define data models
- Specify APIs/interfaces
- Document decision rationale

**2.3 Tasks Expansion**

Transform generic tasks into specific, actionable items:

**Example transformation:**
```markdown
BEFORE:
- [ ] **🐌 1.1 Implement core API/functionality**

AFTER (for Quartz blog):
- [ ] **🐌 1.1 Setup Quartz 4 project structure**
  - Clone Quartz 4 template repository
  - Configure quartz.config.ts with site metadata
  - Setup content folder structure (posts/, pages/, assets/)
  - Test local build with `npx quartz build --serve`
  - _Context: ~8K tokens_
  - _Duration: ~15 minutes_
```

Add context estimates and duration for each task:
- **Context budget**: Estimated tokens needed for task execution
- **Duration**: Estimated time to complete
- **Dependencies**: Explicit task dependencies
- **File scope**: Which files will be modified

---

### Phase 3: Automated Expansion (If --auto mode)

**3.1 Use Pattern Defaults**

Apply sensible defaults based on detected pattern without asking questions:

**For Modern Dev Workflow:**
- Deployment: Docker Compose (self-hosted)
- CI/CD: GitHub Actions
- IaC: Docker Compose
- Monitoring: Basic (logs + uptime)
- Domain: Placeholder for user's domain

**For Resource Management:**
- Storage: File-based or PostgreSQL
- Auth: JWT tokens
- CRUD: Full CRUD for all resources
- Lifecycle: Simple active/inactive

**3.2 Fill Templates Intelligently**

Use feature name and pattern to infer reasonable values:
- Parse feature name for hints (e.g., "quartz-blog" → blogging platform)
- Use common tech stacks for pattern
- Add TODO comments for critical decisions
- Flag items requiring user input with `[USER_INPUT_REQUIRED]`

---

### Phase 4: Generate Supporting Files (Parallel 🐍)

**4.1 Generate Auto-Skill**

Create `.claude/skills/{feature-name}.md` with:
- Project overview
- Pattern type
- Key requirements summary
- Architecture approach
- Task phase summary
- Context-efficient format (saves 200-750K tokens)

**Example auto-skill:**
```markdown
---
name: quartz-blog-site
description: Self-hosted Quartz 4 blog with automated deployment
pattern: modern-dev-workflow
---

# Quartz Blog Site

## Overview
Static blog using Quartz 4 (markdown → HTML), self-hosted with Docker + Nginx, automated CI/CD via GitHub Actions.

## Key Requirements
- Markdown-based content authoring
- Automated build on git push
- Self-hosted deployment (Docker)
- Simple CI/CD pipeline
- Basic monitoring (uptime, logs)

## Architecture
- **Generator**: Quartz 4 (Node.js static site generator)
- **Deployment**: Docker container with Nginx
- **CI/CD**: GitHub Actions workflow
- **Hosting**: Self-hosted VPS or cloud VM

## Phases
1. Foundation: Setup Quartz, configure, test locally
2. Automation: GitHub Actions, Docker build, tests
3. Deployment: Docker Compose, Nginx config, domain setup
4. Observability: Logging, uptime monitoring
5. Hardening: SSL/TLS, backup strategy, docs

## Context Notes
- Total estimated context: ~85K tokens
- Parallel phases: 2, 3, 4 (up to 4 agents)
- Sequential phases: 1, 5
- Estimated duration: 2-3 hours
```

**4.2 Generate Phase Structure**

Create `ouroboros/specs/{feature-name}/phases/` directory structure:
```
phases/
├── phase-1-foundation/
├── phase-2-automation/
├── phase-3-deployment/
├── phase-4-observability/
└── phase-5-hardening/
```

Each phase directory ready to receive:
- `summary-{task-id}.md` - Task execution summaries
- `consolidated.md` - Cross-task insights
- `artifacts/` - Generated files, configs, etc.

**4.3 Generate Validation Checklist**

Create `ouroboros/specs/{feature-name}/validation-checklist.md`:
```markdown
# Pre-Flight Validation Checklist

## Layer 1: Requirements Coverage
- [ ] All requirements have acceptance criteria (≥3 per requirement)
- [ ] EARS format used consistently (WHEN/IF/WHERE/WHILE + SHALL)
- [ ] Requirements cover happy path AND error scenarios
- [ ] Requirements are testable and measurable

## Layer 2: Design Conformance
- [ ] Design addresses all requirements
- [ ] Technology choices justified
- [ ] Component interactions defined
- [ ] Error handling strategy documented

## Layer 3: Task Dependencies
- [ ] All tasks have clear inputs/outputs
- [ ] No circular dependencies (DAG validated)
- [ ] Parallel tasks don't modify same files
- [ ] Sequential tasks have explicit ordering

## Layer 4: Context Budget
- [ ] No task exceeds 150K token limit
- [ ] Context estimates provided for complex tasks
- [ ] Total context under recommended limits

## Layer 5: Phase Structure
- [ ] Phases have clear boundaries
- [ ] Parallelization opportunities identified
- [ ] Phase completion criteria defined
- [ ] Rollback strategy considered
```

---

### Phase 5: Pre-Flight Validation (Sequential 🐌)

**5.1 Run Validator**

Use `ouroboros/validators/preflight.md` to validate:

**Layer 1: Requirements Coverage**
- Count requirements with acceptance criteria
- Check EARS format compliance
- Verify testability

**Layer 2: Design Conformance**
- Map design components to requirements
- Check for uncovered requirements
- Verify technology choices documented

**Layer 3: Task Dependency DAG**
- Build dependency graph
- Detect cycles
- Validate parallel task file conflicts

**Layer 4: Context Budget**
- Sum context estimates per task
- Flag tasks over 150K tokens
- Suggest task splitting if needed

**Layer 5: Phase Structure**
- Verify phase boundaries
- Check parallelization strategy
- Validate completion criteria

**5.2 Generate Validation Report**

```
🔍 Pre-Flight Validation Report: quartz-blog-site

✅ Layer 1: Requirements Coverage (95%)
  - 18/20 requirements have ≥3 acceptance criteria
  - ⚠️ Warning: Requirement 3.2 has only 2 AC (add 1 more)
  - ⚠️ Warning: Requirement 5.1 missing EARS keyword

✅ Layer 2: Design Conformance (100%)
  - All requirements covered by design
  - Technology choices documented
  - Architecture diagram present

✅ Layer 3: Task Dependencies (100%)
  - DAG validated (no cycles)
  - 11 parallel tasks identified
  - No file conflicts detected

✅ Layer 4: Context Budget (90%)
  - Total estimated context: 85K tokens
  - Max task context: 45K tokens (Task 2.1)
  - ⚠️ Warning: Task 2.1 near limit, consider splitting

✅ Layer 5: Phase Structure (100%)
  - 5 phases with clear boundaries
  - 3 parallel phases (2, 3, 4)
  - Completion criteria defined

Overall: READY FOR EXECUTION (4 warnings, 0 blockers)

Recommendations:
1. Add 1 more AC to Requirement 3.2
2. Update Requirement 5.1 to use EARS format
3. Consider splitting Task 2.1 if it grows during execution
4. Run validation again after making changes
```

**5.3 Handle Validation Results**

Based on validation mode:

**Standard mode (default):**
- Display warnings
- Ask: "Continue despite warnings? (y/n)"
- If yes, proceed to summary
- If no, offer to help fix issues

**Strict mode:**
- Block on any warning or error
- Require all issues resolved
- Re-run validation after fixes

**Permissive mode:**
- Display warnings but don't block
- Auto-proceed to summary

---

### Phase 6: Summary & Next Steps (Sequential 🐌)

**6.1 Display Completion Summary**

```
✅ Spec Expansion Complete: quartz-blog-site

📋 Pattern: Modern Development Workflow
📁 Location: ouroboros/specs/quartz-blog-site/

📊 Stats:
  - Requirements: 20 (100% complete)
  - Design sections: 8 (100% complete)
  - Tasks: 18 across 5 phases
  - Parallel opportunities: 11 tasks
  - Estimated context: ~85K tokens
  - Estimated duration: 2-3 hours

📝 Generated Files:
  ✅ requirements.md (expanded)
  ✅ design.md (expanded)
  ✅ tasks.md (expanded with estimates)
  ✅ .claude/skills/quartz-blog-site.md (auto-skill)
  ✅ validation-checklist.md
  ✅ phases/ directory structure

🎯 Validation: READY FOR EXECUTION
  - 4 warnings (non-blocking)
  - 0 blockers
  - See validation-checklist.md for details

Next Steps:
1. Review expanded spec files
2. Address validation warnings (optional)
3. Execute: "Use ouroboros workflow to implement quartz-blog-site"

💡 Tips:
  - Use the auto-skill (.claude/skills/quartz-blog-site.md) for context efficiency
  - Parallel phases will run up to 4 agents simultaneously
  - Phase summaries will be saved to phases/ directory
  - Adaptive task updates will be offered interactively during execution
```

**6.2 Offer Interactive Review**

Ask: "Would you like to review any expanded files before execution? (requirements/design/tasks/all/none)"

- If specific file chosen, display with markdown formatting
- Highlight key changes from template
- Offer to make edits

**6.3 Update Spec Metadata**

Create or update `ouroboros/specs/{feature-name}/metadata.json`:
```json
{
  "feature_name": "quartz-blog-site",
  "pattern": "modern-dev-workflow",
  "created_at": "2025-10-25T23:00:00Z",
  "expanded_at": "2025-10-25T23:15:00Z",
  "status": "ready",
  "validation": {
    "last_validated": "2025-10-25T23:15:00Z",
    "mode": "standard",
    "result": "pass_with_warnings",
    "warnings": 4,
    "blockers": 0
  },
  "estimates": {
    "total_context_tokens": 85000,
    "total_duration_minutes": 150,
    "parallel_phases": 3,
    "sequential_phases": 2
  },
  "auto_skill_generated": true,
  "phase_structure_created": true
}
```

---

## Interactive Question Templates by Pattern

### Pattern 1: Structured Sequential Workflow

```
Core Questions:
1. Number of sequential stages? (3-7 typical)
2. What validation happens between stages? (tests, review, approval)
3. Rollback capability needed? (yes/no/partial)
4. Can stages parallelize internally? (yes/no)
5. What triggers stage transitions? (auto/manual/conditional)

Requirements Expansion:
- Generate stage-specific requirements
- Add validation gate requirements
- Include rollback requirements if needed
- Define stage completion criteria

Design Expansion:
- Create stage flow diagram
- Define stage inputs/outputs
- Document validation mechanisms
- Specify rollback procedures

Tasks Expansion:
- One phase per stage
- Add validation tasks between stages
- Include rollback preparation tasks
- Estimate stage duration and context
```

### Pattern 2: Creative Iterative Process

```
Core Questions:
1. What are you creating? (design, content, plan)
2. Number of iteration cycles? (2-5 typical)
3. Who provides feedback? (self, peer, stakeholder, users)
4. Success criteria? (when is it "done")
5. Explore alternatives? (yes/no)

Requirements Expansion:
- Quality criteria requirements
- Feedback loop requirements
- Iteration completion criteria
- Alternative exploration if applicable

Design Expansion:
- Iteration cycle design
- Feedback collection mechanism
- Quality assessment approach
- Convergence strategy

Tasks Expansion:
- Initial creation phase
- Iteration phases (parallel alternatives possible)
- Feedback collection tasks
- Refinement tasks
- Convergence/finalization phase
```

### Pattern 3: Resource Management

```
Core Questions:
1. What resources? (comma-separated list)
2. Operations per resource? (CRUD, read-only, custom)
3. Storage approach? (SQL, NoSQL, file, memory)
4. Auth/authz needed? (public, API key, JWT, OAuth, session)
5. Resource lifecycle? (simple, stateful, complex)

Requirements Expansion:
- CRUD requirements per resource
- Validation rules per resource
- Access control requirements
- Lifecycle state requirements if applicable
- Audit/history requirements

Design Expansion:
- Data model for each resource
- API/interface design per operation
- Storage schema design
- Auth/authz mechanism design
- State machine for lifecycle

Tasks Expansion:
- Infrastructure phase (storage, validation framework)
- CRUD phase (parallel by resource or operation)
- Access control phase
- Lifecycle management phase
- Testing and polish
```

### Pattern 4: Exploratory Research

```
Core Questions:
1. Research question/hypothesis?
2. Data sources? (web, DB, code, interviews, experiments)
3. Stopping criteria? (how much is enough)
4. Deliverable? (report, decision, findings, POC)
5. Timeline constraints? (deadline, milestones)

Requirements Expansion:
- Data collection requirements
- Analysis requirements
- Synthesis requirements
- Deliverable requirements
- Timeline requirements

Design Expansion:
- Research methodology
- Data collection approach
- Analysis techniques
- Synthesis framework
- Deliverable format

Tasks Expansion:
- Broad exploration phase
- Initial analysis phase
- Deep investigation phase
- Synthesis and recommendations phase
- Deliverable creation
```

### Pattern 5: Modern Dev Workflow

```
Core Questions:
1. Deployment environment? (self-hosted, cloud, K8s, serverless)
2. CI/CD platform? (GitHub Actions, GitLab, Jenkins, Circle)
3. IaC tool? (Docker Compose, Terraform, Ansible, CloudFormation)
4. Monitoring level? (basic, standard, advanced)
5. Domain/hosting setup? (have domain, need domain, subdomain, local)

Requirements Expansion:
- Core functionality requirements
- CI/CD automation requirements
- Infrastructure requirements
- Containerization requirements
- Observability requirements
- Security requirements
- GitOps requirements

Design Expansion:
- Application architecture
- CI/CD pipeline design
- Infrastructure as code design
- Container and orchestration design
- Observability design (logs, metrics, traces)
- Security design
- GitOps workflow design

Tasks Expansion:
- Foundation phase (core functionality)
- Automation phase (CI/CD, tests, quality, build) - PARALLEL
- Deployment phase (IaC, orchestration, automation) - PARALLEL
- Observability phase (logs, metrics, alerts) - PARALLEL
- Hardening phase (security, docs, launch prep)
```

---

## Error Handling

**Spec not found:**
```
⚠️ Spec '{feature-name}' not found at ouroboros/specs/{feature-name}/

Did you mean:
  - {closest-match-1}
  - {closest-match-2}

Or create it first: /new-spec {feature-name}
```

**Already expanded:**
```
⚠️ Spec '{feature-name}' appears to be already expanded.

Detected:
  - Auto-skill exists (.claude/skills/{feature-name}.md)
  - Metadata shows: expanded_at: {date}
  - Requirements: {X}% complete

Options:
1. Re-expand (overwrite existing expansion)
2. Validate only (check current state)
3. Cancel

Your choice: (1/2/3)
```

**Pattern detection failed:**
```
⚠️ Unable to detect pattern for '{feature-name}' (confidence < 50%)

Detected signals:
  - Keyword matches: {list}
  - Structure: {description}
  - Confidence: {X}%

Please choose pattern manually:
1. Structured Sequential Workflow
2. Creative Iterative Process
3. Resource Management
4. Exploratory Research
5. Modern Dev Workflow

Your choice: (1-5)
```

**Validation blockers:**
```
❌ Pre-Flight Validation FAILED: {X} blockers found

Critical Issues:
1. [BLOCKER] Requirement 2.1 has no acceptance criteria
2. [BLOCKER] Task 3.2 has circular dependency with Task 3.5
3. [BLOCKER] Task 4.1 exceeds 150K token limit (estimated 180K)

You must resolve these blockers before execution.

Would you like help fixing these issues? (y/n)
```

---

## Examples

### Example 1: Interactive Expansion
```
User: /expand-spec quartz-blog-site

🔍 Analyzing spec: quartz-blog-site...

Pattern Detected: Modern Development Workflow (92% confidence)
Current State: Templates populated, 12 placeholders remaining

Starting interactive expansion...

Q1: What is your target deployment environment?
   1. Self-hosted VPS
   2. Cloud (AWS, GCP, Azure)
   3. Docker + Docker Compose
   4. Kubernetes
   5. Serverless

User: 1

Q2: What CI/CD platform will you use?
   1. GitHub Actions
   2. GitLab CI/CD
   ...

[Interactive questions continue...]

✅ Expansion complete! Generated 8 files, ready for execution.
```

### Example 2: Automated Expansion
```
User: /expand-spec quartz-blog-site --auto

🔍 Analyzing spec: quartz-blog-site...
Pattern Detected: Modern Development Workflow (92% confidence)

Applying pattern defaults...
✅ Requirements expanded (20 requirements, 78 AC)
✅ Design expanded (8 sections)
✅ Tasks expanded (18 tasks across 5 phases)
✅ Auto-skill generated
✅ Validation passed (4 warnings)

Ready for execution in 3.2 seconds!
```

### Example 3: Validate Only
```
User: /expand-spec quartz-blog-site --validate-only

🔍 Running pre-flight validation...

✅ Layer 1: Requirements Coverage (95%)
✅ Layer 2: Design Conformance (100%)
✅ Layer 3: Task Dependencies (100%)
⚠️ Layer 4: Context Budget (90% - see warnings)
✅ Layer 5: Phase Structure (100%)

Overall: READY (4 warnings, 0 blockers)

No changes made (validate-only mode).
```

---

## Notes

- **Context efficiency**: Expansion uses intelligent defaults to minimize token usage
- **Adaptive**: Pattern-specific questions ensure relevant details captured
- **Validated**: Pre-flight checks prevent execution failures
- **Flexible**: Interactive or automated modes for different workflows
- **Documented**: All expansions logged in metadata.json
- **Reversible**: Original templates preserved, expansions can be re-run

---

🐍 *The serpent expands its circle, transforming simple intent into detailed wisdom, ready for the great consumption...* 🐍
