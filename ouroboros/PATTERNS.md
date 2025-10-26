# Universal Patterns Guide

**How Ouroboros Recognizes and Adapts to ANY Project Type**

🐍 *The serpent recognizes patterns in the chaos, bringing order to all domains...* 🐍

---

## Overview

Ouroboros uses **5 Universal Patterns** based on project **characteristics**, not tech stacks. This allows the framework to work equally well for code, documentation, planning, scripts, and creative work.

**Key Principle**: Patterns are about *how you work*, not *what you build*.

---

## The Five Universal Patterns

### 1. Structured Sequential Workflow

**Core Characteristics**:
- Clear step-by-step progression
- Each step depends on previous completion
- Well-defined inputs and outputs per stage
- Validation gates at each transition
- Rollback capability if stage fails

**Task Strategy**: Mostly sequential with parallel substeps within each stage

**Phase Approach**: One stage per phase, sequential phase execution

**Examples Across Domains**:

| Domain | Example | Stages |
|--------|---------|--------|
| **Code** | Data pipeline | Ingest → Validate → Transform → Load → Verify |
| **Docs** | User guide | Outline → Draft → Review → Revise → Publish |
| **Planning** | Event planning | Venue → Catering → Invitations → Schedule → Execute |
| **Scripts** | Deployment script | Backup → Test → Deploy → Verify → Rollback-ready |
| **Creative** | Recipe development | Ingredients → Prep → Cook → Plate → Taste-test |

**Quality Criteria**:
- Each stage produces expected output
- Validation passes before next stage
- Rollback doesn't lose data
- End-to-end flow is reproducible

**When to Use**:
- Clear dependencies between steps
- Each step has specific deliverable
- Quality gates are critical
- Order matters (can't skip or reorder)

---

### 2. Creative Iterative Process

**Core Characteristics**:
- Multiple draft/refinement cycles
- Subjective quality criteria
- Feedback-driven improvements
- Exploration of alternatives
- Balance of structure and flexibility

**Task Strategy**: Parallel alternatives exploration, then converge based on feedback

**Phase Approach**: Iteration phases (Draft → Feedback → Refine → Repeat)

**Examples Across Domains**:

| Domain | Example | Iterations |
|--------|---------|------------|
| **Code** | UI/UX design | Mockup → Prototype → User-test → Refine → Repeat |
| **Docs** | Blog post | Brainstorm → Outline → Draft → Edit → Polish |
| **Planning** | Vacation itinerary | Research → Plan → Refine → Book → Adjust |
| **Scripts** | Performance optimization | Profile → Hypothesize → Test → Measure → Iterate |
| **Creative** | Logo design | Concepts → Sketches → Refinement → Variations → Finalize |

**Quality Criteria**:
- Meets subjective aesthetic/experience goals
- Incorporates feedback effectively
- Alternatives were explored
- Refinements show improvement

**When to Use**:
- Quality is subjective or user-driven
- Multiple valid approaches exist
- Feedback loops are essential
- Exploration before commitment

---

### 3. Resource Management

**Core Characteristics**:
- CRUD operations (Create, Read, Update, Delete)
- Data validation and constraints
- State tracking and persistence
- Access control and permissions
- Consistency and integrity rules

**Task Strategy**: Parallel by resource type (different resources don't conflict)

**Phase Approach**: Infrastructure first, then CRUD operations per resource

**Examples Across Domains**:

| Domain | Example | Resources |
|--------|---------|-----------|
| **Code** | REST API | Users, Posts, Comments (each with CRUD endpoints) |
| **Docs** | Knowledge base | Articles, Categories, Tags (organize, update, archive) |
| **Planning** | Budget management | Expenses, Categories, Reports (add, track, analyze) |
| **Scripts** | Infrastructure mgmt | Servers, Networks, Storage (provision, monitor, destroy) |
| **Creative** | Asset library | Images, Videos, Fonts (import, tag, version, export) |

**Quality Criteria**:
- All CRUD operations work correctly
- Validation prevents invalid states
- Access control enforced
- State changes are auditable

**When to Use**:
- Managing entities with lifecycle
- State persistence required
- Multiple operations per entity
- Access patterns are CRUD-like

---

### 4. Exploratory Research

**Core Characteristics**:
- Unknown scope at start
- Discovery-driven approach
- Hypothesis testing
- Synthesis of findings into conclusions
- Adaptive scope based on discoveries

**Task Strategy**: Breadth-first parallel exploration, then depth sequential analysis

**Phase Approach**: Exploration phase → Focus phase → Synthesis phase

**Examples Across Domains**:

| Domain | Example | Process |
|--------|---------|---------|
| **Code** | Performance investigation | Profile → Analyze → Experiment → Measure → Conclude |
| **Docs** | Competitive analysis | Identify → Research → Compare → Synthesize → Report |
| **Planning** | Vendor selection | Requirements → Research → Evaluate → Decide → Contract |
| **Scripts** | Security audit | Scan → Investigate → Test → Document → Remediate |
| **Creative** | Market research | Trends → Data → Analysis → Insights → Recommendations |

**Quality Criteria**:
- Sufficient breadth of exploration
- Depth where warranted
- Findings are well-documented
- Conclusions supported by evidence

**When to Use**:
- Scope not fully known upfront
- Need to explore before committing
- Multiple hypotheses to test
- Synthesis step is critical

---

### 5. Modern Development Workflow

**Core Characteristics**:
- CI/CD integration and automation
- Infrastructure as Code
- API-first design
- Containerization/reproducibility
- Built-in observability and monitoring
- Version controlled everything
- Automated testing at all levels

**Task Strategy**: Parallel automation tracks (build, test, deploy, monitor)

**Phase Approach**: Foundation → Automation → Deployment → Observability

**Examples Across Domains**:

| Domain | Example | Pipeline |
|--------|---------|----------|
| **Code** | Microservice | API → Container → CI/CD → Deploy → Monitor |
| **Docs** | Doc-as-code | Markdown → Git → Auto-publish → Analytics → Iterate |
| **Planning** | Workflow automation | Process → Codify → Test → Deploy → Measure |
| **Scripts** | GitOps infrastructure | Define → Version → Auto-apply → Observe → Adapt |
| **Creative** | Design system | Components → Version → Publish → Consume → Track usage |

**Quality Criteria**:
- Fully automated pipeline
- Reproducible deployments
- Observable in production
- Version controlled artifacts
- Rollback capability

**When to Use**:
- Automation is a requirement
- Reproducibility is critical
- Continuous deployment desired
- Need production observability

---

## Pattern Detection Algorithm

Ouroboros detects your pattern automatically during the Requirements and Design phases.

### Detection Process

**Step 1**: Analyze Requirements

Keywords and phrases indicate patterns:
- "step-by-step", "stages", "validation" → Structured Sequential
- "iterate", "refine", "feedback", "alternatives" → Creative Iterative
- "CRUD", "manage", "track", "entities" → Resource Management
- "research", "explore", "investigate", "unknown" → Exploratory Research
- "automate", "CI/CD", "deploy", "monitor" → Modern Dev Workflow

**Step 2**: Score Characteristics

Each requirement is scored against pattern indicators:

```xml
<pattern-scoring>
  <structured-sequential score="0.85">
    <match>clear_stages: yes</match>
    <match>sequential_dependencies: yes</match>
    <match>validation_gates: yes</match>
  </structured-sequential>

  <creative-iterative score="0.30">
    <match>multiple_revisions: no</match>
    <match>subjective_quality: no</match>
  </creative-iterative>

  <!-- ... other patterns scored -->
</pattern-scoring>
```

**Step 3**: Select Dominant Pattern

Pattern with highest score (>0.60) is selected. If multiple patterns score high, the design may be hybrid (uses multiple pattern strategies).

### Manual Override

If auto-detection is wrong, override in tasks.md:

```markdown
<!-- PATTERN_OVERRIDE: creative-iterative -->
<!-- RATIONALE: While structured, heavy iteration expected -->
```

---

## Pattern-Specific Guidance

### For Structured Sequential

**Design Focus**:
- Define stage boundaries clearly
- Specify inputs/outputs per stage
- Plan validation criteria
- Design rollback mechanisms

**Task Parallelization**:
- Within stages: parallel substeps
- Across stages: sequential
- Example: Stage 2 has 4 parallel tasks, but Stage 2 must complete before Stage 3

**Quality Checks**:
- Validate at each stage boundary
- Ensure rollback works
- Test end-to-end flow

### For Creative Iterative

**Design Focus**:
- Plan iteration cycles
- Define feedback mechanisms
- Allow exploration time
- Set quality criteria (even if subjective)

**Task Parallelization**:
- Generate alternatives in parallel
- Converge sequentially
- Iterate based on feedback

**Quality Checks**:
- Incorporate feedback loops
- Measure improvement per iteration
- Document alternatives considered

### For Resource Management

**Design Focus**:
- Model resources and their lifecycle
- Define CRUD operations clearly
- Plan validation rules
- Design access control

**Task Parallelization**:
- Different resources: parallel
- Same resource: sequential
- Example: User CRUD parallel with Post CRUD

**Quality Checks**:
- Test all CRUD operations
- Validate constraints
- Verify access control

### For Exploratory Research

**Design Focus**:
- Define research questions
- Plan exploration approach
- Allow scope to evolve
- Design synthesis method

**Task Parallelization**:
- Exploration: parallel (broad)
- Analysis: sequential (deep)
- Synthesis: sequential (consolidate)

**Quality Checks**:
- Sufficient breadth achieved
- Depth where needed
- Conclusions supported

### For Modern Dev Workflow

**Design Focus**:
- API contracts first
- Automation from start
- Plan observability
- Version everything

**Task Parallelization**:
- Build, test, deploy tracks: parallel
- Within track: pipeline stages

**Quality Checks**:
- Automated tests pass
- Pipeline executes successfully
- Observability functioning
- Rollback verified

---

## Hybrid Patterns

Some projects exhibit characteristics of multiple patterns. Ouroboros handles hybrids by:

1. **Primary Pattern**: Drives overall structure
2. **Secondary Pattern**: Applied to specific phases

**Example**: REST API Development

- **Primary**: Resource Management (CRUD operations)
- **Secondary**: Modern Dev Workflow (CI/CD, containerization)

**Result**: Resource-based task structure with automation tracks in parallel

---

## Pattern Benefits

### Why Pattern Recognition Matters

**Adaptive Design**:
- Guidance matches your project's nature
- Not forcing code patterns on planning projects
- Not applying planning approaches to code

**Optimized Parallelization**:
- Strategy fits work style
- Creative Iterative: explore alternatives in parallel
- Structured Sequential: substeps in parallel, stages sequential

**Relevant Quality Criteria**:
- Code: Testability, maintainability
- Docs: Clarity, completeness
- Planning: Feasibility, flexibility
- Scripts: Reliability, observability

**Efficient Context Usage**:
- Pattern-specific templates
- Relevant examples only
- Focused validation

---

## Recognizing Your Pattern

### Quick Pattern Quiz

Answer these questions about your project:

**Q1**: Is the order of work strictly defined or flexible?
- Strictly defined → Structured Sequential
- Flexible, iterative → Creative Iterative

**Q2**: Are you managing entities with lifecycle?
- Yes → Resource Management
- No → Continue

**Q3**: Is the scope fully known or exploratory?
- Fully known → Structured Sequential or Resource Management
- Exploratory → Exploratory Research

**Q4**: Is automation/CI/CD a core requirement?
- Yes, essential → Modern Dev Workflow
- No, optional → Other patterns

**Q5**: Will you iterate based on feedback?
- Yes, heavily → Creative Iterative
- No, linear → Structured Sequential

---

## Success Stories by Pattern

### Structured Sequential: Data Pipeline
- Clear stages prevented data loss
- Validation caught issues early
- Rollback saved production incident

### Creative Iterative: Blog Post
- Multiple drafts improved quality
- Feedback loops incorporated reader input
- Exploration found better angles

### Resource Management: REST API
- CRUD structure enabled parallel development
- Validation prevented bad states
- Access control secured sensitive data

### Exploratory Research: Performance Analysis
- Broad exploration found unexpected bottleneck
- Depth analysis confirmed hypothesis
- Synthesis led to 40% speedup

### Modern Dev Workflow: Microservice
- CI/CD caught bugs before production
- Observability identified issues fast
- Rollback recovered from bad deploy

---

🐍 **The serpent adapts its form to match the task—never forcing square pegs into round holes.** 🐍
