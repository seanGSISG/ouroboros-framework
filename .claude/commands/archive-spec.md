# Archive Completed Ouroboros Spec

When the user runs `/archive-spec {spec-name}` or `/archive-spec`, archive a completed Ouroboros specification.

## Process

1. **Determine which spec to archive**:
   - If spec name provided in command: Use it
   - If not provided: Run `/list-specs` and ask user which spec to archive
   - Wait for confirmation before proceeding

2. **Validate spec exists**:
   ```bash
   ls ouroboros/specs/{spec-name}
   ```
   - If not found: "⚠️ Spec '{spec-name}' not found in ouroboros/specs/"
   - If already archived: "⚠️ Spec '{spec-name}' is already in archive/"

3. **Check completion status**:
   - Read `ouroboros/specs/{spec-name}/tasks.md`
   - Count completed vs total tasks
   - If not 100% complete: Ask user "⚠️ This spec is only {X}% complete. Archive anyway? (yes/no)"
   - Wait for confirmation if incomplete

4. **Create archive directory**:
   ```bash
   mkdir -p ouroboros/specs/archive
   ```

5. **Move spec to archive**:
   ```bash
   mv ouroboros/specs/{spec-name} ouroboros/specs/archive/{spec-name}
   ```

6. **Create archive metadata**:
   Create `ouroboros/specs/archive/{spec-name}/ARCHIVED.md`:
   ```markdown
   # Archived: {Feature Name}

   **Archived on**: {current-date}
   **Pattern**: {pattern-name}
   **Status**: {X/Y tasks complete}

   ## Summary
   {Brief summary from requirements.md or design.md}

   ## Reason for Archival
   {User-provided reason or "Completed successfully"}

   ## Location
   Originally: `ouroboros/specs/{spec-name}/`
   Archived: `ouroboros/specs/archive/{spec-name}/`

   ---

   🐍 The serpent has consumed this circle—its wisdom integrated, its work complete. 🐍
   ```

7. **Clean up auto-generated skill** (optional):
   - Ask user: "Would you like to remove the auto-generated skill file at `.claude/skills/{spec-name}.md`?"
   - If yes: `rm .claude/skills/{spec-name}.md`
   - If no: Leave it for reference

8. **Confirm archival**:
   Display success message:
   ```
   ✅ Archived spec: {spec-name}

   📦 Location: ouroboros/specs/archive/{spec-name}/
   📊 Final status: {X/Y tasks complete} ({percentage}%)
   📅 Archived: {date}

   The spec has been moved to the archive. All files are preserved.

   To restore: mv ouroboros/specs/archive/{spec-name} ouroboros/specs/
   ```

## Options

### Archive with reason
```
/archive-spec {spec-name} --reason "Project cancelled"
```
Includes the reason in ARCHIVED.md

### Force archive incomplete spec
```
/archive-spec {spec-name} --force
```
Archives without asking for confirmation on incomplete specs

### Archive multiple specs
```
/archive-spec {spec-1} {spec-2} {spec-3}
```
Archives multiple specs at once

## Example Interaction

```
User: /archive-spec vacation-planning-europeAssistant: Checking vacation-planning-europe...

✅ Spec is 100% complete (15/15 tasks)

Archiving vacation-planning-europe...

✅ Archived spec: vacation-planning-europe

📦 Location: ouroboros/specs/archive/vacation-planning-europe/
📊 Final status: 15/15 tasks complete (100%)
📅 Archived: 2025-10-25

Would you like to remove the auto-generated skill file at .claude/skills/vacation-planning-europe.md?

User: Yes
