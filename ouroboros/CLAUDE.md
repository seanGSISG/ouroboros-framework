# Ouroboros Spec Workflow

This file contains detailed instructions for creating and executing specs using the Ouroboros framework.

## What is Ouroboros?

Ouroboros is a self-adapting, self-improving framework for spec-driven development that works for **ANY project type**:
- Code projects (APIs, CLIs, web apps, scripts)
- Documentation (user guides, API docs, blog posts)
- Planning (vacations, events, business processes)
- Creative work (design systems, content creation)

**The Ouroboros Principle**: The serpent that eats its own tail grows stronger with each iteration. Every execution generates insights that improve future executions.

## When to Create a Spec

Create a spec when:
- Planning new features or capabilities
- Proposing breaking changes
- Designing architecture shifts
- Planning major performance or security work
- Any change requiring structured planning and execution
- Creating complex vacation itineraries
- Automating business processes
- Building documentation systems

**Rule of thumb**: If it takes >1 hour to implement, it deserves a spec.

## How to Create a Spec

### Step 1: Create Spec Directory

```bash
ouroboros/specs/{feature-name}/
├── requirements.md
├── design.md
└── tasks.md
```

**Feature naming**: Use kebab-case (e.g., `user-authentication`, `europe-vacation-2024`, `api-documentation-v2`)

### Step 2: Write Requirements (EARS Format)

Use EARS (Easy Approach to Requirements Syntax):

```markdown
**1.1** WHEN {trigger}, the system SHALL {capability}
  - AC 1.1.1: {Acceptance criterion}
  - AC 1.1.2: {Acceptance criterion}

**1.2** IF {condition}, the system SHALL {capability}
  - AC 1.2.1: {Acceptance criterion}
```

**Keywords**:
- **WHEN** - Event-driven (user clicks button, file uploads, schedule triggers)
- **IF** - Conditional logic (if user has permission, if file exists)
- **WHERE** - Location/scope (where data is stored, where UI appears)
- **WHILE** - Ongoing state (while processing, while user is logged in)

**Examples across domains**:

**Code project**:
```markdown
WHEN a user submits login credentials, the system SHALL validate against database
  - AC: Returns JWT token on success
  - AC: Returns 401 on invalid credentials
```

**Vacation planning**:
```markdown
WHEN booking flights, the plan SHALL include backup options
  - AC: At least 2 flight options per leg
  - AC: Price difference documented
```

**Documentation**:
```markdown
WHERE API endpoints are documented, the system SHALL include request/response examples
  - AC: Every endpoint has ≥1 example
  - AC: Examples use realistic data
```

### Step 3: Write Design

Document:
- **Architecture approach** (how components fit together)
- **Component structure** (what needs to be built)
- **Technology choices** (what tools/frameworks/approaches)
- **Key decisions** (why you chose this approach)

**Be specific about**:
- Data flow
- Component interactions
- External dependencies
- Error handling strategy

### Step 4: Write Tasks

Break down implementation into phases with parallel tasks (🐍) and sequential tasks (🐌).

**Task format**:
```markdown
### Phase 1: Foundation (Sequential 🐌)

- [ ] **🐌 1.1 Set up project structure**
  - Create directories
  - Initialize configuration
  - _Context: ~15K tokens_
  - _Duration: ~10 minutes_

### Phase 2: Core Features (4 parallel 🐍)

- [ ] **🐍 2.1 Implement user authentication**
  - JWT token generation
  - Password hashing
  - _Context: ~45K tokens_
  - _Duration: ~18 minutes_
  - **Can run in parallel with 2.2, 2.3, 2.4**
```

**Parallelization rules**:
- **🐍 Tasks that don't modify the same files** can run in parallel
- **🐌 Tasks with dependencies** must run sequentially
- **Hard cap**: 7 parallel agents (only for small context tasks)
- **Default**: 4-5 parallel agents

### Step 5: Execute with Ouroboros

```
Use ouroboros workflow to implement {feature-name}
Execute all tasks automatically in parallel
```

## Pattern Detection

Ouroboros automatically detects your project pattern and optimizes task structure:

### 1. Structured Sequential Workflow
**Characteristics**: Clear stages, sequential dependencies, validation gates
**Examples**: Data pipelines, deployment scripts, assembly instructions, user guides

### 2. Creative Iterative Process
**Characteristics**: Multiple revisions, feedback loops, subjective quality
**Examples**: UI/UX design, blog posts, vacation planning, performance optimization

### 3. Resource Management
**Characteristics**: CRUD operations, state tracking, validation rules
**Examples**: REST APIs, knowledge bases, budget management, asset libraries

### 4. Exploratory Research
**Characteristics**: Unknown scope, discovery-driven, hypothesis testing
**Examples**: Performance investigation, competitive analysis, vendor selection

### 5. Modern Development Workflow
**Characteristics**: Automation-first, version controlled, observable, API-driven
**Examples**: Microservices, doc-as-code, GitOps infrastructure, design systems

## Continuous Adaptation

**The Ouroboros feeds on its own output** 🐍

During execution:

1. **Subagents save discoveries** to phase summaries
   - Location: `ouroboros/specs/{feature}/phases/{phase-id}/summary-{task-id}.md`
   - Content: What was accomplished, discoveries made, recommendations

2. **Orchestrator consolidates findings**
   - Location: `ouroboros/specs/{feature}/phases/{phase-id}/consolidated.md`
   - Content: Cross-task insights, task update recommendations, metrics

3. **You review and approve task updates interactively**
   - Diff-based presentation
   - Accept/skip/modify each change
   - Tasks versioned (tasks.md → tasks-v2.md → tasks-v3.md)

4. **Auto-generated skill captures project knowledge**
   - Location: `.claude/skills/{feature-name}.md`
   - Saves 10-25K tokens per task vs re-reading full specs
   - Updated after each phase with new discoveries

## Context Efficiency

Ouroboros uses aggressive token reduction:

**Strategy 1: XML Tags**
```xml
<task id="2.3" context="45K" status="completed"/>
```
vs verbose JSON (saves ~40%)

**Strategy 2: Progressive Disclosure**
- Read `.claude/skills/{feature-name}.md` (3-5K tokens)
- Instead of requirements.md + design.md (15-30K tokens)
- **Savings**: 200-750K tokens per spec execution

**Strategy 3: Summary Files**
- Read summary-*.md (1-2K tokens each)
- Instead of re-executing tasks
- **Savings**: 50-100K tokens per phase

**Strategy 4: Delta-Based Updates**
- Track only changes, not full rewrites
- **Savings**: 10-20K tokens per update

## Commands

### /ouroboros-update

Refresh managed blocks in CLAUDE.md files:
```
/ouroboros-update
```

Updates the `<!-- OUROBOROS:START --> ... <!-- OUROBOROS:END -->` block in `{PROJECT_ROOT}/CLAUDE.md` while preserving user content.

## Examples

### Example 1: REST API

```markdown
Feature: user-authentication

Pattern: Resource Management
Phases: 3 (Foundation 🐌, Core Features 🐍, Testing 🐌)
Parallel tasks: 5 (authentication, JWT, password hashing, session mgmt, rate limiting)
Time: 45 min (vs 95 min sequential)
```

### Example 2: Vacation Planning

```markdown
Feature: europe-vacation-2024

Pattern: Creative Iterative Process
Phases: 4 (Research 🐌, Initial Planning 🐍, Refinement 🐌, Booking 🐍)
Parallel tasks: 4 (flights, hotels, activities, budget)
Time: 38 min (vs 72 min sequential)

Discovery: Found cheaper early-morning flights → Updated budget task
Adaptation: Swiss hotels require 3-night minimum → Extended stay, reduced Venice
```

### Example 3: Documentation

```markdown
Feature: api-documentation-v2

Pattern: Structured Sequential Workflow
Phases: 3 (Outline 🐌, Content 🐍, Review 🐌)
Parallel tasks: 6 (intro, auth, endpoints, errors, examples, deployment)
Time: 52 min (vs 98 min sequential)
```

## Best Practices

### Requirements
- ✅ Use EARS format (WHEN/IF/WHERE/WHILE + SHALL)
- ✅ Include 3-5 acceptance criteria per requirement
- ✅ Cover happy path AND error scenarios
- ✅ Make requirements testable and measurable

### Design
- ✅ Explain WHY you chose this approach
- ✅ Document alternatives considered
- ✅ Include diagrams for complex flows
- ✅ Specify error handling strategy

### Tasks
- ✅ Break into phases with clear boundaries
- ✅ Mark parallel (🐍) vs sequential (🐌) tasks
- ✅ Estimate context budget per task
- ✅ Identify file conflicts that prevent parallelization
- ✅ Keep tasks focused (single responsibility)

### Execution
- ✅ Review phase consolidations carefully
- ✅ Approve task updates when discoveries warrant changes
- ✅ Use auto-generated skills for context efficiency
- ✅ Let the serpent adapt and grow 🐍

## Troubleshooting

**Problem**: Tasks taking longer than estimated
**Solution**: Check context budgets, split large tasks, reduce parallel count

**Problem**: File conflicts during parallel execution
**Solution**: Reorganize tasks to avoid same-file edits in parallel

**Problem**: Task updates feel overwhelming
**Solution**: Use interactive diff workflow, review changes one at a time

**Problem**: Pattern detection seems wrong
**Solution**: Override in tasks.md with explicit pattern choice

## Philosophy

> "The serpent that eats its own tail grows stronger with each iteration."

Ouroboros doesn't just execute your plan—it learns from execution and improves future plans. Each spec makes the next one better.

**This is spec-driven development evolved**:
- Not just planning, but adaptive planning
- Not just execution, but learning execution
- Not just for code, but for ANY project
- Not just a tool, but a growing intelligence

---

*The ancient serpent coils around your project, protecting and improving it...* 🐍
