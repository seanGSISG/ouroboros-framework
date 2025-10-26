# Create New Ouroboros Spec (Proposal)

**Note**: This command is an alias for `/new-spec`.

When the user runs `/proposal {spec-name}` or `/proposal`, create a new Ouroboros specification.

## Usage

```
/proposal {spec-name}
```

This command is equivalent to:
```
/new-spec {spec-name}
```

## Process

Run `/new-spec` with the provided spec name (or without if not provided). See `.claude/commands/new-spec.md` for full documentation.

## What This Does

Creates a new Ouroboros specification with:
1. Pattern detection based on project type
2. Requirement gathering (EARS format)
3. Design document creation
4. Task breakdown with parallelization

## Example

```
User: /proposal user-authentication
→ Redirects to /new-spec user-authentication
```

---

🐍 *The serpent welcomes new visions, ready to shape them into reality...* 🐍