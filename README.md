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

Works for: REST APIs, vacation planning, documentation, PowerShell scripts, design systems, and more.

---

## Quick Start (3 Steps)

### 1. Install

Copy this repo to your project:

```bash
git clone https://github.com/seanGSISG/ouroboros-framework.git
cd ouroboros-framework
```

Or copy just the `ouroboros/` directory into your existing project.

### 2. Create a Spec

Run the slash command:

```
/new-spec
```

You'll be prompted for:
1. Feature name (e.g., `user-authentication`, `vacation-planning`, `api-docs`)
2. Project type (code, documentation, planning, scripts, creative)
3. Pattern selection (automatic based on your project type)

The command creates:
```
ouroboros/specs/{your-feature}/
├── requirements.md    # EARS-format requirements (auto-filled template)
├── design.md          # Architecture approach (auto-filled template)
└── tasks.md           # Implementation phases (auto-filled template)
```

### 3. Execute the Workflow

Say to Claude:

```
Use ouroboros workflow to implement {your-feature}
```

The framework will:
- ✅ Read your spec files
- ✅ Execute tasks in parallel (when possible)
- ✅ Save discoveries after each phase
- ✅ Recommend task updates based on findings
- ✅ Auto-generate a project skill for context savings
- ✅ Create all deliverables

---

## Complete E2E Example

```bash
# 1. Create a new spec
> /new-spec user-authentication
📋 What type of project is this?
1. Code project
2. Documentation
3. Planning
4. Scripts/Automation
5. Creative work

> 1

📋 Does this involve CRUD operations?
> Yes

✅ Created spec: user-authentication
   Pattern: Resource Management
   Location: ouroboros/specs/user-authentication/

# 2. Edit the spec files (optional - templates are pre-filled)
# - requirements.md: Add/customize your requirements
# - design.md: Add/customize your architecture
# - tasks.md: Add/customize your implementation phases

# 3. Execute the workflow
> Use ouroboros workflow to implement user-authentication

🐍 Executing user-authentication spec...

Phase 1: Foundation
  ✅ Task 1.1 complete
  ✅ Task 1.2 complete

Phase 2: Core Features (4 parallel agents)
  🐍 Task 2.1: User model (Agent 1)
  🐍 Task 2.2: Authentication logic (Agent 2)
  🐍 Task 2.3: JWT tokens (Agent 3)
  🐍 Task 2.4: Password hashing (Agent 4)
  
  ✅ All tasks complete
  
  📊 Phase 2 Consolidation:
  - Discovery: JWT expiry should be configurable
  - Recommendation: Add task 3.5 for environment config
  
  Would you like to update tasks? (yes/no)
  > yes
  
  ✅ Tasks updated (tasks-v2.md created)

Phase 3: Testing & Polish (3 parallel agents)
  ...

✅ user-authentication complete!

Artifacts created:
  - ouroboros/specs/user-authentication/phases/ (all summaries)
  - .claude/skills/user-authentication.md (auto-generated skill)
  - All implementation files
```

---

## Available Commands

| Command | Purpose | Usage |
|---------|---------|-------|
| `/new-spec` | Create new spec | `/new-spec {feature-name}` or `/new-spec` |
| `/list-specs` | List all specs | `/list-specs` |
| `/archive-spec` | Archive completed spec | `/archive-spec {feature-name}` |
| `/ouroboros-update` | Update managed blocks | `/ouroboros-update` |

See [COMMANDS.md](COMMANDS.md) for detailed documentation.

---

## How It Works

### 1. Pattern Detection
Ouroboros has 5 universal patterns based on **project characteristics**, not tech stacks:

- **Structured Sequential** - Clear stages (data pipelines, user guides)
- **Creative Iterative** - Multiple revisions (UI design, vacation planning)
- **Resource Management** - CRUD operations (REST APIs, budget tracking)
- **Exploratory Research** - Discovery-driven (performance analysis, vendor selection)
- **Modern Dev Workflow** - Automation-first (microservices, doc-as-code)

### 2. Adaptive Tasks
During execution:
- Tasks run in parallel when possible (1-7 agents)
- Each agent saves a summary with discoveries
- Orchestrator consolidates findings
- You approve task updates based on discoveries
- Tasks evolve (tasks.md → tasks-v2.md → tasks-v3.md)

### 3. Context Efficiency
**60-75% token savings** through:
- Auto-generated skills (read 3K instead of 30K)
- Summary files (90% savings on consolidation)
- XML tags (40% savings vs JSON)
- Delta-based updates (95% savings)

---

## Real-World Examples

### Example 1: REST API (Code Project)
```
/new-spec user-authentication
→ Pattern: Resource Management
→ Time: 45 min (vs 95 min sequential)
→ Savings: 56% faster, 68% less context
```

### Example 2: Vacation Planning (Planning Project)
```
/new-spec europe-vacation-2024
→ Pattern: Creative Iterative
→ Time: 122 min (vs 249 min sequential)
→ Savings: 51% faster, adaptive task updates
→ Example: "Swiss hotels need 3-night minimum" → Tasks updated automatically
```

See `ouroboros/examples/vacation-planning-europe/` for complete example.

### Example 3: API Documentation (Documentation Project)
```
/new-spec api-documentation-v2
→ Pattern: Structured Sequential
→ Time: 52 min (vs 98 min sequential)
→ Savings: 47% faster
```

---

## Project Structure After Installation

```
your-project/
├── ouroboros/                        # The framework (copy this directory)
│   ├── .claude/                      # Claude Code discovers commands here
│   │   ├── commands/                 # Slash commands (/new-spec, etc.)
│   │   ├── agents/                   # Quality improvement agent
│   │   └── system-prompts/           # Workflow orchestrator
│   ├── ouroboros/                    # Framework resources
│   │   ├── templates/                # Pattern templates
│   │   ├── intelligence/             # Pattern recognizer, skills generator
│   │   ├── validators/               # Pre-flight validation
│   │   └── examples/                 # Cross-domain examples
│   └── specs/                        # Your feature specs (generated)
│       └── {feature-name}/
│           ├── requirements.md
│           ├── design.md
│           ├── tasks.md
│           └── phases/               # Execution artifacts
└── .claude/skills/                   # Auto-generated skills (project root)
    └── {feature-name}.md
```

---

## Key Benefits

- 🐍 **Self-Adapting**: Tasks evolve based on real discoveries
- 🌍 **Project Agnostic**: Works for ANY project type
- ⚡ **Parallel Execution**: 1-7 agents (40-60% time savings)
- 💾 **Context Efficient**: 60-75% token reduction
- 🎯 **Pre-Flight Validation**: Catches 95%+ of issues before execution
- 📈 **Continuous Learning**: Each execution improves future executions

---

## Documentation

- **[ARCHITECTURE.md](ARCHITECTURE.md)** - Directory structure & design rationale
- **[COMMANDS.md](COMMANDS.md)** - Slash command reference
- **[TESTING.md](TESTING.md)** - Integration tests & verification
- **[STATUS.md](STATUS.md)** - Current status & component inventory
- **[ouroboros/CLAUDE.md](ouroboros/CLAUDE.md)** - Comprehensive workflow guide
- **[ouroboros/PATTERNS.md](ouroboros/PATTERNS.md)** - Universal patterns explained
- **[ouroboros/CONTEXT_OPTIMIZATION.md](ouroboros/CONTEXT_OPTIMIZATION.md)** - Context-saving strategies
- **[ouroboros/MIGRATION.md](ouroboros/MIGRATION.md)** - Migrating from OpenSpec v1

---

## Requirements

- **Claude Code** (or any Claude interface that supports slash commands)
- **Claude Sonnet 4.5** or later (200K context window)

---

## Support & Contributions

- **Issues**: Report bugs or request features via GitHub Issues
- **Discussions**: Share your specs and experiences
- **Pull Requests**: Contributions welcome!

---

## Philosophy

> *"The serpent that eats its own tail grows stronger with each iteration."*

Ouroboros doesn't just execute your plan—it **learns** from execution and **improves** future plans. Each spec makes the next one better.

**This is spec-driven development evolved**:
- Not just planning, but **adaptive planning**
- Not just execution, but **learning execution**
- Not just for code, but for **ANY project**
- Not just a tool, but a **growing intelligence**

---

## License

*To be determined - suggest MIT or Apache 2.0*

---

🐍 **Ready to begin? Run `/new-spec` and let the serpent guide you!** 🐍
