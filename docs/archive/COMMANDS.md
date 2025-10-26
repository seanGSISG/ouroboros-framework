# Ouroboros Commands Reference

All Ouroboros slash commands available in the framework.

---

## Available Commands

### `/new-spec` - Create New Spec

**Usage**: `/new-spec [{feature-name}]`

**Description**: Scaffold a new Ouroboros specification with pattern-based templates. **Automatically offers to expand the spec** after creation for a seamless workflow.

**Process**:
1. Asks for feature name (if not provided)
2. Detects project type (code, docs, planning, scripts, creative)
3. Selects appropriate pattern template
4. Creates directory structure: `ouroboros/specs/{feature-name}/`
5. Copies pattern templates (requirements.md, design.md, tasks.md)
6. Customizes templates with feature name
7. **Offers immediate expansion** (interactive, automated, or skip)

**Expansion Options After Creation**:
- **Interactive**: Asks pattern-specific questions to customize the spec
- **Automated**: Uses smart defaults based on detected pattern
- **Skip**: User manually edits templates, runs `/expand-spec` later

**Examples**:
```
/new-spec user-authentication
  → Creates spec → Offers expansion → Choose interactive/auto/skip

/new-spec vacation-planning-europe
  → Creates spec → Offers expansion

/new-spec
  → Asks for name → Creates spec → Offers expansion
```

**Why This Workflow**:
Generic templates contain placeholders (like API/database requirements for all projects). The expansion step customizes these for your specific project (e.g., removes database requirements for a static site).

**Location**: `ouroboros/.claude/commands/new-spec.md`

---

### `/expand-spec` - Expand and Validate Spec

**Usage**: `/expand-spec {feature-name} [--interactive|--auto|--validate-only]`

**Description**: Intelligently expand a basic spec template into a detailed, validated, execution-ready specification using pattern recognition, intelligent questioning, and pre-flight validation.

**Modes**:
- **Interactive** (default): Asks targeted pattern-specific questions to flesh out requirements, design, and tasks
- **Automated** (`--auto`): Uses pattern defaults and minimal input for rapid expansion
- **Validate Only** (`--validate-only`): Runs pre-flight validation without making changes

**Process**:
1. Loads and analyzes spec files (requirements.md, design.md, tasks.md)
2. Detects pattern using Pattern Recognizer (with confidence score)
3. Interactive: Asks pattern-specific questions | Auto: Applies sensible defaults
4. Expands requirements with specific acceptance criteria
5. Expands design with technology choices and architecture details
6. Expands tasks with context estimates, duration, and dependencies
7. Generates auto-skill (`.claude/skills/{feature-name}.md`) for context efficiency
8. Creates phase directory structure (`phases/phase-1-*/`, etc.)
9. Runs 5-layer pre-flight validation
10. Generates validation report with warnings/blockers
11. Creates metadata.json with expansion details

**Generated Files**:
- Expanded `requirements.md`, `design.md`, `tasks.md`
- `.claude/skills/{feature-name}.md` (auto-skill for context efficiency)
- `validation-checklist.md` (pre-flight checklist)
- `metadata.json` (expansion metadata)
- `phases/` directory structure

**Validation Layers**:
1. **Requirements Coverage**: All requirements have acceptance criteria
2. **Design Conformance**: Design covers all requirements
3. **Task Dependency DAG**: No circular dependencies, valid parallelization
4. **Context Budget**: No task exceeds 150K token limit
5. **Phase Structure**: Optimal phase boundaries and parallelization

**Examples**:
```
/expand-spec quartz-blog-site
/expand-spec user-api --interactive
/expand-spec vacation-europe --auto
/expand-spec my-feature --validate-only
```

**Pattern-Specific Questions**:
- **Modern Dev Workflow**: Deployment env, CI/CD platform, IaC tool, monitoring level
- **Resource Management**: Resources to manage, CRUD operations, storage, auth
- **Creative Iterative**: What you're creating, iteration cycles, feedback sources
- **Structured Sequential**: Number of stages, validation gates, rollback needs
- **Exploratory Research**: Research question, data sources, stopping criteria

**Context Savings**: Auto-skill generation saves 200-750K tokens per spec execution

**Location**: `.claude/commands/expand-spec.md`

---

### `/list-specs` - List All Specs

**Usage**: `/list-specs [{spec-name}]`

**Description**: Show all Ouroboros specifications with status and progress.

**Process**:
1. Lists all specs in `ouroboros/specs/`
2. Shows completion status (X/Y tasks complete)
3. Displays pattern type
4. Shows last updated time

**Output Example**:
```
📋 Ouroboros Specs

user-authentication
  Status: 8/12 tasks complete (67%)
  Location: ouroboros/specs/user-authentication/
  Pattern: Resource Management

vacation-planning-europe
  Status: 15/15 tasks complete (100%)
  Location: ouroboros/specs/vacation-planning-europe/
  Pattern: Creative Iterative Process

Total: 2 specs (1 complete, 1 in progress)
```

**Location**: `ouroboros/.claude/commands/list-specs.md`

---

### `/archive-spec` - Archive Completed Spec

**Usage**: `/archive-spec [{spec-name}]`

**Description**: Move a completed specification to the archive.

**Process**:
1. Validates spec exists
2. Checks completion status
3. Moves to `ouroboros/specs/archive/{spec-name}/`
4. Creates ARCHIVED.md with metadata
5. Optionally removes auto-generated skill

**Options**:
```
/archive-spec {spec-name} --reason "Project cancelled"
/archive-spec {spec-name} --force  (archive incomplete spec)
```

**Location**: `ouroboros/.claude/commands/archive-spec.md`

---

### `/ouroboros-update` - Update Managed Blocks

**Usage**: `/ouroboros-update`

**Description**: Refresh the Ouroboros managed block in project CLAUDE.md files.

**Process**:
1. Locates all files with `<!-- OUROBOROS:START -->` markers
2. Updates content between START and END markers
3. Preserves user content outside managed blocks
4. Reports what was updated

**Location**: `ouroboros/.claude/commands/ouroboros-update.md`

---

## Command Development

### Creating New Commands

To add a new Ouroboros command:

1. **Create command file**: `ouroboros/.claude/commands/{command-name}.md`

2. **Add frontmatter** (optional):
```markdown
---
name: Command Name
description: Brief description
category: Ouroboros
tags: [ouroboros, tag1, tag2]
---
```

3. **Write instructions**:
```markdown
# Command Title

When the user runs `/{command-name}`, do the following:

## Process
1. Step 1
2. Step 2
...

## Examples
...
```

4. **Test the command**: Use it in a project to verify it works

### Command Naming Conventions

- Use kebab-case: `/new-spec`, not `/newSpec`
- Prefix with `ouroboros-` for framework management commands
- Keep names concise and descriptive
- Use verbs: `/create-spec`, `/list-specs`, `/archive-spec`

---

## Comparison with OpenSpec Commands

Ouroboros uses a simpler command structure compared to OpenSpec:

| OpenSpec | Ouroboros Equivalent | Notes |
|----------|---------------------|-------|
| `/openspec proposal` | `/new-spec` | Creates new specs with pattern templates |
| *N/A* | `/expand-spec` | **NEW**: Expands templates into detailed specs with validation |
| `/openspec apply` | *Use workflow directly* | Say: "Use ouroboros workflow to implement {feature}" |
| `/openspec archive` | `/archive-spec` | Moves completed specs to archive |
| `/openspec list` | `/list-specs` | Shows all specs with status |

**Why Different**:
- Ouroboros doesn't have a CLI tool (no `ouroboros` command)
- Simpler workflow focused on spec execution
- Pattern-based instead of change-based
- Works for ANY project type (not just code)
- **NEW**: `/expand-spec` bridges the gap between template and execution

---

## Command Location

All Ouroboros commands are in:
```
ouroboros/.claude/commands/
├── new-spec.md
├── expand-spec.md
├── list-specs.md
├── archive-spec.md
└── ouroboros-update.md
```

When Ouroboros is installed in a project, Claude Code automatically discovers these commands.

---

## Using Commands

### In Claude Code

Simply type the slash command in the chat:
```
/new-spec user-authentication
```

### In Other Claude Interfaces

Commands may not work automatically. Instead, you can:
1. Read the command file directly
2. Follow the instructions manually
3. Or say: "Follow the instructions in ouroboros/.claude/commands/{command}.md"

---

## Future Commands (Ideas)

Potential commands to add:

- `/show-spec` - Display detailed spec information
- `/clone-spec` - Copy an existing spec as a template
- `/export-spec` - Export spec to shareable format
- `/import-spec` - Import spec from another project
- `/run-spec` - Execute a spec using Ouroboros workflow (alternative to manual invocation)

---

🐍 **Commands are the serpent's incantations—spoken words that summon creation, organization, and completion.** 🐍