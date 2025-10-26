# Universal Pattern Templates

**Purpose**: Project-agnostic templates for the 5 universal patterns in the Ouroboros framework.

**Location**: `/home/adminuser/projects/SKILLS/ouroboros/templates/patterns/`

---

## Template Library Structure

This directory contains **15 templates** (5 patterns × 3 templates each):

### Pattern 1: Structured Sequential Workflow
- `structured-sequential-requirements.md` - EARS requirements with stage-based organization
- `structured-sequential-design.md` - Sequential stage design with validation gates
- `structured-sequential-tasks.md` - Phase structure with mostly sequential progression

**Use for**: Data pipelines, deployment scripts, user guides, event planning, recipes

---

### Pattern 2: Creative Iterative Process
- `creative-iterative-requirements.md` - Requirements for feedback-driven projects
- `creative-iterative-design.md` - Iteration cycle design with quality criteria
- `creative-iterative-tasks.md` - Exploration → Feedback → Refinement cycles

**Use for**: UI/UX design, blog posts, vacation planning, performance optimization, logo design

---

### Pattern 3: Resource Management
- `resource-management-requirements.md` - CRUD operations and validation requirements
- `resource-management-design.md` - Data model, access control, lifecycle design
- `resource-management-tasks.md` - Infrastructure → CRUD → Access control → Lifecycle

**Use for**: REST APIs, knowledge bases, budget management, infrastructure provisioning, asset libraries

---

### Pattern 4: Exploratory Research
- `exploratory-research-requirements.md` - Discovery-driven requirements with hypothesis testing
- `exploratory-research-design.md` - Breadth-first → Pattern recognition → Depth investigation
- `exploratory-research-tasks.md` - Exploration (parallel) → Analysis → Deep dive → Synthesis

**Use for**: Performance investigation, competitive analysis, vendor selection, security audits, market research

---

### Pattern 5: Modern Development Workflow
- `modern-dev-workflow-requirements.md` - Automation, CI/CD, observability requirements
- `modern-dev-workflow-design.md` - Foundation → Automation → Deployment → Observability
- `modern-dev-workflow-tasks.md` - Parallel automation tracks with GitOps workflow

**Use for**: Microservices, doc-as-code, workflow automation, GitOps infrastructure, design systems

---

## Key Features

### ✅ Project-Agnostic
- NOT tech-specific (no "React template" or "Python template")
- Based on workflow characteristics, not technology stack
- Works for code, docs, planning, scripts, creative work

### ✅ Cross-Domain Examples
- Each template includes 4-5 examples across different domains
- Code projects, documentation, planning, scripts, creative work
- Real-world use cases for each pattern

### ✅ Pattern-Specific Guidance
- Requirements use EARS format appropriate for pattern
- Design structure optimized for pattern workflow
- Task phasing reflects pattern characteristics

### ✅ Customizable
- Clear placeholders for project-specific details
- Customization checklists included
- Starting points, not rigid structures

---

## Template Selection

### Automatic Selection (Pattern Recognizer)

When you have requirements/design already:
```
The Pattern Recognizer in ouroboros/intelligence/pattern-recognizer.md
will analyze your documents and recommend the appropriate pattern.
```

### Interactive Selection (Template Selector)

When starting a new project:
```
The Template Selector in ouroboros/intelligence/template-selector.md
guides you through questions to choose the right pattern.
```

**Usage**:
```bash
ouroboros init
```

---

## Template Usage Workflow

### 1. Select Pattern
- Use Template Selector (interactive)
- OR use Pattern Recognizer (automatic)
- OR choose manually from pattern comparison

### 2. Generate Templates
```bash
ouroboros init [project-name]
# Creates:
# ouroboros/specs/[project-name]/requirements.md
# ouroboros/specs/[project-name]/design.md
# ouroboros/specs/[project-name]/tasks.md
```

### 3. Customize Templates
- Replace all [placeholders]
- Review cross-domain examples
- Adapt to your specific domain
- Add/remove sections as needed

### 4. Validate
```bash
ouroboros validate [project-name]
# Checks:
# - Pattern match accuracy
# - Requirement completeness
# - Design coverage
# - Task dependencies
```

### 5. Execute
```bash
ouroboros workflow [project-name]
# Executes tasks with parallelization
# Adaptive task system learns and improves
```

---

## Pattern Comparison

| Pattern | Workflow | Key Trait | Phases | Parallelization |
|---------|----------|-----------|--------|-----------------|
| **Structured Sequential** | Step-by-step | Clear stages | 4-7 | Substeps within stages |
| **Creative Iterative** | Feedback loops | Refinement | 3-5 | Initial alternatives, then sequential iterations |
| **Resource Management** | CRUD lifecycle | State tracking | 4-6 | CRUD operations in parallel |
| **Exploratory Research** | Discovery-driven | Unknown scope | 3-4 | Broad exploration, then focused investigation |
| **Modern Dev Workflow** | Automation-first | Observable | 4-6 | Automation tracks in parallel |

---

## Best Practices

### DO:
✅ Choose pattern based on workflow characteristics
✅ Review cross-domain examples for inspiration
✅ Customize templates to your domain
✅ Use templates as starting points, not rigid structures
✅ Mix patterns if project has multiple aspects

### DON'T:
❌ Choose pattern based on technology stack
❌ Use templates without customization
❌ Treat templates as rigid requirements
❌ Ignore cross-domain examples
❌ Force-fit pattern if it doesn't match workflow

---

## Examples of Pattern Mixing

### Example 1: REST API with GitOps Deployment

**Primary**: Resource Management (core CRUD functionality)
**Secondary**: Modern Dev Workflow (deployment, observability)

**Approach**:
1. Use Resource Management template for requirements/design
2. Add Modern Dev Workflow automation/deployment phases to tasks
3. Include CI/CD and observability in design

---

### Example 2: Research Report with Iterative Refinement

**Primary**: Exploratory Research (investigation and findings)
**Secondary**: Creative Iterative (writing and refining report)

**Approach**:
1. Use Exploratory Research for investigation phases
2. Use Creative Iterative for report writing/refinement phases
3. Two-phase project: Research (Phase 1-2) → Writing (Phase 3-4)

---

### Example 3: Data Pipeline with Exploration Phase

**Primary**: Structured Sequential (pipeline stages)
**Secondary**: Exploratory Research (initial data profiling)

**Approach**:
1. Phase 1: Exploratory Research (understand data)
2. Phases 2-6: Structured Sequential (build pipeline)
3. Informed pipeline design from exploration findings

---

## File Size Summary

```
Requirements templates: ~3-5KB each (comprehensive examples)
Design templates: ~3-5KB each (detailed guidance)
Tasks templates: ~3-4KB each (phasing and examples)

Total: ~100KB for all 15 templates
```

---

## Version History

**v1.0** (2025-10-25)
- Initial release
- 5 universal patterns
- 3 templates per pattern (requirements, design, tasks)
- Cross-domain examples for each pattern
- Template Selector specification

---

## Related Components

- `/home/adminuser/projects/SKILLS/ouroboros/intelligence/pattern-recognizer.md` - Automatic pattern detection
- `/home/adminuser/projects/SKILLS/ouroboros/intelligence/template-selector.md` - Interactive template selection
- `/home/adminuser/projects/SKILLS/ouroboros/CLAUDE.md` - Ouroboros framework guide

---

**Generated by Ouroboros Framework**
**Component**: Universal Pattern Templates
**Version**: 1.0
**Last Updated**: 2025-10-25
