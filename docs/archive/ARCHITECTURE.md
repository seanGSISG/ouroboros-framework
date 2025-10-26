# Ouroboros Framework Architecture

## Directory Structure

The Ouroboros framework is organized into two main directories:

### 1. `ouroboros/.claude/` - Claude Code Infrastructure

This directory contains all files that Claude Code needs to discover and use:

```
ouroboros/.claude/
├── agents/                           # Agent specifications
│   └── spec-quality.md               # Universal quality improvement agent
├── commands/                         # Slash commands  
│   └── ouroboros-update.md           # Update managed blocks in CLAUDE.md
├── system-prompts/                   # Workflow orchestrators
│   └── ouroboros-workflow-starter.md # Main orchestrator (937 lines)
└── skills/                           # Auto-generated project skills (empty initially)
    └── {feature-name}.md             # Created during spec execution
```

**Purpose**: These files are discovered by Claude Code when the framework is used in a project.

**Discovery**: When Ouroboros is copied to a project, Claude Code finds these agents, commands, and system prompts automatically.

### 2. `ouroboros/ouroboros/` - Framework Resources

This directory contains templates, intelligence components, validators, and documentation:

```
ouroboros/ouroboros/
├── CLAUDE.md                         # Comprehensive workflow guide (8KB)
├── PATTERNS.md                       # Universal patterns guide
├── CONTEXT_OPTIMIZATION.md           # Context-saving strategies
├── MIGRATION.md                      # Migration guide from OpenSpec v1
│
├── config/                           # Framework configuration
│   └── ouroboros-config.json         # Enhancement toggles
│
├── templates/                        # Templates for generated files
│   ├── subagent-summary-template.md
│   ├── phase-consolidation-template.md
│   ├── preflight-validation-report.md
│   └── patterns/                     # Pattern-based spec templates (15 files)
│       ├── README.md
│       ├── VALIDATION.md
│       ├── structured-sequential-{requirements,design,tasks}.md
│       ├── creative-iterative-{requirements,design,tasks}.md
│       ├── resource-management-{requirements,design,tasks}.md
│       ├── exploratory-research-{requirements,design,tasks}.md
│       └── modern-dev-workflow-{requirements,design,tasks}.md
│
├── intelligence/                     # Intelligence components (specs)
│   ├── pattern-recognizer.md         # Pattern detection algorithm
│   ├── skills-generator.md           # Auto-generates project skills
│   ├── learning-engine.md            # Self-improvement metrics
│   └── template-selector.md          # Template selection wizard
│
├── validators/                       # Validation systems
│   └── preflight.md                  # 5-layer pre-flight validation
│
├── patterns/                         # Learned pattern library
│   ├── resource-management-learned.json
│   └── creative-iterative-learned.json
│
└── examples/                         # Cross-domain examples
    ├── README.md
    ├── vacation-planning-europe/     # Complete example (Creative Iterative)
    │   ├── requirements.md
    │   ├── design.md
    │   └── tasks.md
    ├── powershell-infrastructure/    # Placeholder (Modern Dev Workflow)
    └── api-documentation/            # Placeholder (Structured Sequential)
```

**Purpose**: Resources used by the framework during execution.

**Path References**: All framework files reference these as `ouroboros/ouroboros/{resource}` (e.g., `ouroboros/ouroboros/templates/subagent-summary-template.md`).

### 3. `ouroboros/specs/` - User Feature Specs (Generated)

This directory is empty initially and gets populated during framework usage:

```
ouroboros/specs/
└── {feature-name}/                   # Created when user runs a spec
    ├── requirements.md               # Feature requirements
    ├── design.md                     # Feature design
    ├── tasks.md                      # Implementation tasks
    └── phases/                       # Generated during execution
        └── {phase-id}/
            ├── summary-{task-id}.md  # Task completion summaries
            └── consolidated.md       # Phase consolidation report
```

**Purpose**: User's feature specifications and execution artifacts.

**Path References**: All spec files reference these as `ouroboros/specs/{feature-name}/`.

---

## Path Reference Strategy

### Framework Installation Paths

When Ouroboros is installed in a project, paths are relative to the project root:

**Templates**: `ouroboros/ouroboros/templates/{template-name}.md`
**Intelligence**: `ouroboros/ouroboros/intelligence/{component-name}.md`
**Validators**: `ouroboros/ouroboros/validators/{validator-name}.md`
**Patterns**: `ouroboros/ouroboros/patterns/{pattern-name}.json`
**Config**: `ouroboros/ouroboros/config/ouroboros-config.json`

### User Spec Paths

When users create and execute specs:

**Spec Root**: `ouroboros/specs/{feature-name}/`
**Requirements**: `ouroboros/specs/{feature-name}/requirements.md`
**Design**: `ouroboros/specs/{feature-name}/design.md`
**Tasks**: `ouroboros/specs/{feature-name}/tasks.md`
**Summaries**: `ouroboros/specs/{feature-name}/phases/{phase-id}/summary-{task-id}.md`
**Consolidated**: `ouroboros/specs/{feature-name}/phases/{phase-id}/consolidated.md`

### Auto-Generated Skills

**Location**: `.claude/skills/{feature-name}.md` (project root `.claude/`, NOT `ouroboros/.claude/`)

**Why**: Claude Code discovers skills in the project's `.claude/skills/` directory. Auto-generated skills are project-specific, not framework infrastructure.

---

## Usage Scenario

### Installing Ouroboros in a Project

1. Copy the entire `ouroboros/` directory to your project:
   ```bash
   cp -r path/to/ouroboros/ your-project/
   ```

2. Your project structure becomes:
   ```
   your-project/
   ├── .claude/                      # Project's Claude infrastructure
   │   └── skills/                   # Auto-generated skills go here
   ├── ouroboros/                    # Ouroboros framework
   │   ├── .claude/                  # Framework's Claude infrastructure
   │   ├── ouroboros/                # Framework resources
   │   └── specs/                    # Your feature specs
   └── {your project files}
   ```

3. When you use Ouroboros:
   - Agents in `ouroboros/.claude/agents/` are discovered
   - Commands in `ouroboros/.claude/commands/` are available
   - System prompts in `ouroboros/.claude/system-prompts/` orchestrate execution
   - Templates from `ouroboros/ouroboros/templates/` are used
   - Skills are auto-generated to `.claude/skills/{feature-name}.md`
   - Specs are created in `ouroboros/specs/{feature-name}/`

---

## File Count Summary

**Total Framework Files**: ~50+ files

**Claude Infrastructure** (`.claude/`): 3 files
- 1 agent (spec-quality.md)
- 1 command (ouroboros-update.md)
- 1 system prompt (ouroboros-workflow-starter.md)

**Framework Resources** (`ouroboros/`): ~47 files
- 4 documentation files (CLAUDE.md, PATTERNS.md, CONTEXT_OPTIMIZATION.md, MIGRATION.md)
- 1 config file
- 18 template files
- 4 intelligence components
- 1 validator
- 2 learned patterns
- 1 example (vacation-planning-europe: 3 files)
- Supporting files (READMEs, etc.)

---

## Design Rationale

### Why Two Nested `ouroboros/` Directories?

This structure allows the entire framework to be self-contained and portable:

1. **Top-level `ouroboros/`**: The entire framework
2. **Nested `ouroboros/.claude/`**: Claude infrastructure that's discoverable
3. **Nested `ouroboros/ouroboros/`**: Framework resources (templates, intelligence, etc.)

**Benefits**:
- ✅ **Portable**: Copy one directory, get entire framework
- ✅ **Isolated**: Framework doesn't pollute project's `.claude/` directory
- ✅ **Clear**: Separation between infrastructure and resources
- ✅ **Discoverable**: Claude Code finds agents and commands in `ouroboros/.claude/`

### Alternative Considered (Not Used)

**Flat structure** (all in `ouroboros/`):
```
ouroboros/
├── agents/
├── commands/
├── system-prompts/
├── templates/
├── intelligence/
└── ...
```

**Why rejected**: Less clear separation between Claude infrastructure and framework resources.

---

## Backward Compatibility

**Note**: In the SKILLS project (where Ouroboros was developed), there are duplicate files:

- `.claude/agents/spec-quality.md` ← Original location
- `.claude/commands/ouroboros-update.md` ← Original location
- `.claude/system-prompts/ouroboros-workflow-starter.md` ← Original location

These can remain for backward compatibility but are NOT part of the Ouroboros framework package. When distributing Ouroboros, only the `ouroboros/` directory is needed.

---

## Testing the Architecture

To verify the architecture is correct:

1. **Check Claude Infrastructure Discovery**:
   - Verify `ouroboros/.claude/agents/` contains spec-quality.md
   - Verify `ouroboros/.claude/commands/` contains ouroboros-update.md
   - Verify `ouroboros/.claude/system-prompts/` contains ouroboros-workflow-starter.md

2. **Check Framework Resources**:
   - Verify `ouroboros/ouroboros/templates/` contains template files
   - Verify `ouroboros/ouroboros/intelligence/` contains intelligence components
   - Verify `ouroboros/ouroboros/validators/` contains preflight.md

3. **Check Path References**:
   - Verify workflow starter references `ouroboros/ouroboros/templates/...`
   - Verify agents reference `ouroboros/ouroboros/...` paths
   - Verify no references to old `.claude/` paths

4. **Check Spec Storage**:
   - Verify `ouroboros/specs/` exists and is empty

---

🐍 **The serpent's structure is perfect—each coil precisely placed for maximum adaptability.** 🐍
