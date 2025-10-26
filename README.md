# Ouroboros Framework

🐍 **Self-adapting spec-driven development for ANY project type**

*The serpent that eats its own tail grows stronger with each iteration.*

---

## What is This?

A framework that helps you plan and execute ANY project through:
- **Pattern-based templates** (code, docs, planning, scripts, creative)
- **Adaptive tasks** (tasks evolve based on real discoveries)
- **Parallel execution** (1-7 agents working simultaneously)
- **Context efficiency** (60-75% token savings)
- **Intelligent expansion** (transforms templates into detailed specs)

Works for: REST APIs, vacation planning, documentation, PowerShell scripts, design systems, and more.

---

## Quick Start (3 Steps)

### 1. Create a Spec

```
/ou-new-spec {feature-name}
```

Choose your project type → Get pattern-based templates → Ready to expand

### 2. Expand and Validate

```
/ou-expand-spec {feature-name}
```

Answer pattern-specific questions → Get detailed spec → Auto-validated → Ready to execute

**Or use automated mode:**
```
/ou-expand-spec {feature-name} --auto
```

### 3. Execute

```
Use ouroboros workflow to implement {feature-name}
```

The framework runs tasks in parallel, learns from discoveries, and delivers your project.

---

## Complete Example

```bash
# 1. Create spec
> /ou-new-spec user-authentication
📋 What type of project? → Code project
📋 CRUD operations? → Yes
✅ Created: Resource Management pattern

# 2. Expand spec
> /ou-expand-spec user-authentication --interactive

Q: What resources are you managing?
> users, sessions

Q: Storage approach?
> PostgreSQL

Q: Authentication method?
> JWT tokens

✅ Expansion complete!
   - 12 detailed requirements
   - PostgreSQL + JWT architecture
   - 15 tasks across 4 phases
   - Auto-skill generated (saves 65% context)
   - Validation: READY (0 blockers)

# 3. Execute
> Use ouroboros workflow to implement user-authentication

Phase 1: Foundation (sequential)
  ✅ Database setup
  ✅ Auth middleware

Phase 2: Core Features (4 parallel agents)
  🐍 User model (Agent 1)
  🐍 JWT logic (Agent 2)
  🐍 Password hashing (Agent 3)
  🐍 Session management (Agent 4)
  ✅ All complete

Phase 3: Testing (3 parallel agents)
  ✅ Unit tests
  ✅ Integration tests
  ✅ Security audit

✅ user-authentication complete! (45 min vs 95 min sequential = 53% faster)
```

---

## Available Commands

| Command | Purpose | Usage |
|---------|---------|-------|
| `/ou-new-spec` | Create new spec | `/ou-new-spec {name}` |
| `/ou-expand-spec` | Expand & validate spec | `/ou-expand-spec {name} [--interactive\|--auto]` |
| `/ou-apply` | Execute spec tasks | `/ou-apply {name}` |
| `/ou-list-specs` | List all specs | `/ou-list-specs` |
| `/ou-archive-spec` | Archive completed spec | `/ou-archive-spec {name}` |
| `/ou-archive` | Shorthand for archive-spec | `/ou-archive {name}` |
| `/ou-proposal` | Alias for new-spec | `/ou-proposal {name}` |
| `/ou-update` | Update managed blocks | `/ou-update` |

**Quick Workflow**:
```
/ou-new-spec → /ou-expand-spec --auto → Execute → /ou-archive
```

---

## How It Works

### 1. Universal Patterns

Ouroboros has 5 patterns based on **project characteristics**, not tech stacks:

- **🗄️ Resource Management** - CRUD operations (APIs, databases, asset libraries)
- **📝 Structured Sequential** - Step-by-step workflows (pipelines, guides, recipes)
- **🎨 Creative Iterative** - Draft-refine cycles (designs, vacation planning, blog posts)
- **🔬 Exploratory Research** - Discovery-driven (analysis, vendor selection, investigation)
- **⚙️ Modern Dev Workflow** - Automation-first (CI/CD, infrastructure, deployment)

Pattern detection is automatic—just answer a few questions!

### 2. Intelligent Expansion

The `/ou-expand-spec` command transforms generic templates into detailed specs:

**Before Expansion** (generic template):
```markdown
## Requirements
{stakeholders_placeholder}
{authentication_placeholder}
{database_placeholder}
```

**After Expansion** (your specific project):
```markdown
## Requirements
**1.1** WHEN user registers, system SHALL create account with PostgreSQL
  - AC 1.1.1: Validate email format
  - AC 1.1.2: Hash password with bcrypt
  - AC 1.1.3: Generate JWT token

**1.2** WHEN user logs in, system SHALL authenticate with JWT
  - AC 1.2.1: Verify token signature
  - AC 1.2.2: Check expiration
```

**Benefits**:
- ✅ Pattern-specific questions (no irrelevant questions)
- ✅ Auto-skill generation (60-75% context savings)
- ✅ Pre-flight validation (catches 95% of issues)
- ✅ Ready to execute immediately

### 3. Adaptive Tasks

During execution:
- Tasks run in parallel when possible (1-7 agents)
- Each agent saves discoveries in phase summaries
- Orchestrator consolidates findings after each phase
- You approve task updates based on discoveries
- Tasks evolve: `tasks.md` → `tasks-v2.md` → `tasks-v3.md`

**Example Discovery**:
```
Phase 2 Discovery: JWT expiry should be configurable via environment variable
Recommendation: Add task 3.5 for environment config setup
→ You approve → tasks-v2.md created with new task
```

### 4. Context Efficiency

**60-75% token savings** through:

| Technique | Savings | Example |
|-----------|---------|---------|
| Auto-generated skills | 90% | Read 3K skill instead of 30K specs |
| Phase summaries | 90% | Read 500-token summary instead of 5K |
| XML tags | 40% | XML vs JSON for structured data |
| Delta updates | 95% | Only changed sections, not full file |

**Real Impact**: A 200K token workflow → 50-70K tokens with Ouroboros

---

## Project Structure

After installation:

```
your-project/
├── ouroboros/                      # The framework (copy this directory)
│   ├── .claude/
│   │   ├── commands/               # 8 slash commands (ou-*)
│   │   ├── agents/                 # 10 specialized agents
│   │   └── system-prompts/         # Workflow orchestrator
│   ├── ouroboros/                  # Framework resources
│   │   ├── templates/patterns/     # 5 pattern templates
│   │   ├── intelligence/           # Pattern recognizer, skills generator
│   │   └── validators/             # Pre-flight validation
│   └── specs/                      # Your specs (generated)
│       └── {feature-name}/
│           ├── requirements.md     # EARS-format requirements
│           ├── design.md           # Architecture approach
│           ├── tasks.md            # Implementation phases
│           └── phases/             # Execution artifacts
└── .claude/skills/                 # Auto-generated skills (project root)
    └── {feature-name}.md           # Context-efficient summaries
```

---

## Real-World Examples

### Example 1: REST API (Resource Management Pattern)
```
/ou-new-spec user-api
/ou-expand-spec user-api --interactive
→ Resources: users, sessions
→ Storage: PostgreSQL
→ Auth: JWT

Execute: "Use ouroboros workflow to implement user-api"
Time: 45 min (vs 95 min sequential)
Savings: 53% faster, 68% less context
```

### Example 2: Vacation Planning (Creative Iterative Pattern)
```
/ou-new-spec europe-vacation-2024
/ou-expand-spec europe-vacation-2024 --auto

Execute: "Use ouroboros workflow to implement europe-vacation-2024"
Time: 122 min (vs 249 min sequential)
Savings: 51% faster
Adaptive: "Swiss hotels need 3-night minimum" → Tasks updated automatically
```

### Example 3: API Documentation (Structured Sequential Pattern)
```
/ou-new-spec api-docs-v2
/ou-expand-spec api-docs-v2 --interactive

Execute: "Use ouroboros workflow to implement api-docs-v2"
Time: 52 min (vs 98 min sequential)
Savings: 47% faster
```

---

## Key Benefits

- 🐍 **Self-Adapting**: Tasks evolve based on real discoveries
- 🌍 **Project Agnostic**: Works for ANY project type (code, docs, planning, creative)
- ⚡ **Parallel Execution**: 1-7 agents simultaneously (40-60% time savings)
- 💾 **Context Efficient**: 60-75% token reduction via auto-skills
- 🎯 **Pre-Flight Validation**: Catches 95%+ of issues before execution
- 🧠 **Intelligent Expansion**: Pattern-specific questions for detailed specs
- 📈 **Continuous Learning**: Each execution improves future executions
- 🔧 **Tech Stack Agnostic**: Patterns work regardless of language/framework

---

## Installation

### Option 1: Clone Framework
```bash
git clone https://github.com/seanGSISG/ouroboros-framework.git
cd ouroboros-framework
```

### Option 2: Copy to Existing Project
```bash
cp -r path/to/ouroboros/ your-project/
```

That's it! Claude Code automatically discovers the commands and agents.

---

## Requirements

- **Claude Code** (or any Claude interface supporting slash commands)
- **Claude Sonnet 4.5+** (200K context window)
- **Git** (optional, for version control)

---

## Documentation

**Getting Started**:
- **[QUICKSTART.md](QUICKSTART.md)** - Get started in 5 minutes

**Framework Deep Dives**:
- **[ouroboros/CLAUDE.md](ouroboros/CLAUDE.md)** - Comprehensive workflow guide
- **[ouroboros/PATTERNS.md](ouroboros/PATTERNS.md)** - Universal patterns explained
- **[ouroboros/CONTEXT_OPTIMIZATION.md](ouroboros/CONTEXT_OPTIMIZATION.md)** - Context-saving strategies
- **[ouroboros/MIGRATION.md](ouroboros/MIGRATION.md)** - Migrating from OpenSpec v1

**Examples**:
- **[ouroboros/examples/](ouroboros/examples/)** - Real-world specs across domains

---

## Core Components

### Commands (8 slash commands)
All in `.claude/commands/` with `ou-` prefix for easy discovery

### Agents (10 specialized agents)
- `spec-requirements` - EARS-format requirements creation
- `spec-design` - Architecture design documents
- `spec-tasks` - Task breakdown with parallelization
- `spec-impl` - Individual task execution (1-7 parallel)
- `spec-judge` - Tree-based quality evaluation
- `spec-validator` - Post-implementation validation
- `spec-test` - Test execution
- `spec-quality` - Universal quality improvement
- `code-reviewer` - Code review and feedback
- `spec-system-prompt-loader` - Dynamic prompt loading

### Intelligence Components
- **Pattern Recognizer** - Detects project pattern (92% accuracy)
- **Skills Generator** - Auto-generates context-efficient summaries
- **Learning Engine** - Tracks metrics, improves over time
- **Template Selector** - Picks optimal pattern template

### Validators
- **Pre-flight Validation** - 5-layer validation before execution:
  1. Requirements coverage
  2. Design conformance
  3. Task dependency DAG
  4. Context budget limits
  5. Phase structure optimization

---

## Philosophy

> *"The serpent that eats its own tail grows stronger with each iteration."*

Ouroboros doesn't just execute your plan—it **learns** from execution and **improves** future plans. Each spec makes the next one better.

**This is spec-driven development evolved**:
- Not just planning, but **adaptive planning**
- Not just execution, but **learning execution**
- Not just for code, but for **ANY project**
- Not just a tool, but a **growing intelligence**

The framework embodies its name: a self-consuming, self-improving cycle where:
1. Execution reveals discoveries
2. Discoveries update tasks
3. Updated tasks improve future specs
4. Better specs accelerate execution
5. Repeat infinitely, growing stronger each time

---

## Support & Contributions

- **Issues**: [GitHub Issues](https://github.com/seanGSISG/ouroboros-framework/issues)
- **Discussions**: Share your specs and experiences
- **Pull Requests**: Contributions welcome!

---

## License

MIT License - See LICENSE file for details

---

## Quick Reference Card

```
CREATE:    /ou-new-spec {name}
EXPAND:    /ou-expand-spec {name} [--interactive|--auto]
LIST:      /ou-list-specs
EXECUTE:   Use ouroboros workflow to implement {name}
ARCHIVE:   /ou-archive {name}
```

**Typical Workflow**:
```
/ou-new-spec my-feature
  ↓
/ou-expand-spec my-feature --auto
  ↓
Use ouroboros workflow to implement my-feature
  ↓
/ou-archive my-feature
```

---

🐍 **Ready to begin? Run `/ou-new-spec` and let the serpent guide you!** 🐍
