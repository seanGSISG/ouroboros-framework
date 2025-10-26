# Ouroboros Commands Reference

All Ouroboros slash commands available in the framework.

---

## Available Commands

### `/new-spec` - Create New Spec

**Usage**: `/new-spec [{feature-name}]`

**Description**: Scaffold a new Ouroboros specification with pattern-based templates.

**Process**:
1. Asks for feature name (if not provided)
2. Detects project type (code, docs, planning, scripts, creative)
3. Selects appropriate pattern template
4. Creates directory structure: `ouroboros/specs/{feature-name}/`
5. Copies pattern templates (requirements.md, design.md, tasks.md)
6. Customizes templates with feature name

**Examples**:
```
/new-spec user-authentication
/new-spec vacation-planning-europe
/new-spec
```

**Location**: `ouroboros/.claude/commands/new-spec.md`

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
| `/openspec apply` | *Use workflow directly* | Say: "Use ouroboros workflow to implement {feature}" |
| `/openspec archive` | `/archive-spec` | Moves completed specs to archive |
| `/openspec list` | `/list-specs` | Shows all specs with status |

**Why Different**:
- Ouroboros doesn't have a CLI tool (no `ouroboros` command)
- Simpler workflow focused on spec execution
- Pattern-based instead of change-based
- Works for ANY project type (not just code)

---

## Command Location

All Ouroboros commands are in:
```
ouroboros/.claude/commands/
├── new-spec.md
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

- `/validate-spec` - Run pre-flight validation on a spec
- `/show-spec` - Display detailed spec information
- `/clone-spec` - Copy an existing spec as a template
- `/export-spec` - Export spec to shareable format
- `/import-spec` - Import spec from another project
- `/run-spec` - Execute a spec using Ouroboros workflow (alternative to manual invocation)

---

🐍 **Commands are the serpent's incantations—spoken words that summon creation, organization, and completion.** 🐍
