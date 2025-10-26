# List Ouroboros Specs

When the user runs `/list-specs` or `/ouroboros-list`, show all Ouroboros specifications in the project.

## Process

1. **List all specs**:
   ```bash
   ls -1 ouroboros/specs/
   ```

2. **For each spec, check status**:
   - Read `ouroboros/specs/{spec-name}/tasks.md` (if exists)
   - Count total tasks: `grep -c "^- \[" tasks.md`
   - Count completed tasks: `grep -c "^- \[x\]" tasks.md`
   - Calculate progress percentage

3. **Display results**:
   Show a formatted list with:
   ```
   📋 Ouroboros Specs

   {spec-name-1}
     Status: {X/Y tasks complete} ({percentage}%)
     Location: ouroboros/specs/{spec-name-1}/
     Pattern: {pattern-name} (if detectable from tasks.md)

   {spec-name-2}
     Status: {X/Y tasks complete} ({percentage}%)
     Location: ouroboros/specs/{spec-name-2}/
     Pattern: {pattern-name}

   Total: {N} specs
   ```

4. **Handle empty state**:
   If no specs exist:
   ```
   📋 No specs found

   Create your first spec with: /new-spec {feature-name}

   Or see examples in: ouroboros/ouroboros/examples/
   ```

## Additional Options

### Show detailed view
If user asks for details on a specific spec:
```
/list-specs {spec-name}
```

Show:
- Requirements count (from requirements.md)
- Design sections (from design.md)
- Task breakdown by phase
- Execution artifacts (phases directory)
- Auto-generated skill location

### Show only active specs
Filter to show only specs with incomplete tasks:
```
Status: In Progress (3/10 tasks)
```

### Show archived specs
If `ouroboros/specs/archive/` exists, list archived specs separately:
```
📦 Archived Specs
  - {spec-name} (archived on {date})
```

## Example Output

```
📋 Ouroboros Specs

user-authentication
  Status: 8/12 tasks complete (67%)
  Location: ouroboros/specs/user-authentication/
  Pattern: Resource Management
  Last updated: 2 hours ago

vacation-planning-europe
  Status: 15/15 tasks complete (100%)
  Location: ouroboros/specs/vacation-planning-europe/
  Pattern: Creative Iterative Process
  Last updated: 1 day ago

api-documentation
  Status: 0/8 tasks complete (0%)
  Location: ouroboros/specs/api-documentation/
  Pattern: Structured Sequential Workflow
  Last updated: 3 days ago

Total: 3 specs (1 complete, 1 in progress, 1 not started)

💡 Run "/list-specs {name}" for detailed view
💡 Run "/new-spec" to create a new spec
```

## Error Handling

- If `ouroboros/specs/` doesn't exist: "⚠️ Ouroboros specs directory not found. Create it with: mkdir -p ouroboros/specs/"
- If tasks.md is malformed: Show "Status: Unknown (tasks.md malformed)"
- If pattern can't be detected: Show "Pattern: Not detected"

---

🐍 *The serpent surveys all circles it has inscribed, tracking the wisdom of each...* 🐍
