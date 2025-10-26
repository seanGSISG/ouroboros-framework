# Apply/Implement Ouroboros Spec

When the user runs `/apply {spec-name}` or says "implement {spec-name}" or "execute {spec-name} tasks", implement an approved Ouroboros specification by executing its tasks.

## Process

**Track these steps as TODOs using the TodoWrite tool and complete them one by one.**

### 1. Read Spec Context

Read the spec files to understand scope and acceptance criteria:

```bash
# Read all spec documents
ouroboros/specs/{spec-name}/requirements.md
ouroboros/specs/{spec-name}/design.md
ouroboros/specs/{spec-name}/tasks.md
```

- Understand the requirements (EARS format)
- Review the design approach
- Identify all tasks to be executed
- Note any phase structure or parallelization opportunities

### 2. Check for Auto-Generated Skill

Check if a skill file exists for context efficiency:

```bash
.claude/skills/{spec-name}.md
```

- If exists: Read it for quick context (3-5K tokens vs 15-30K from full specs)
- If not exists: Will be auto-generated during execution

### 3. Determine Execution Mode

Ask the user how they want to proceed:

**Options:**
1. **Manual mode** (default): Execute tasks one by one with user approval
2. **Auto mode**: Execute all tasks automatically with parallelization
3. **Phase mode**: Execute one phase at a time

### 4. Execute Tasks

Based on chosen mode:

#### Manual Mode (Default):
- Execute tasks sequentially
- After each task completion:
  - Mark task as `- [x]` in tasks.md
  - Update TodoWrite list
  - Wait for user to approve next task

#### Auto Mode:
-  Invoke the Ouroboros workflow:
  ```
  Use ouroboros workflow to implement {spec-name}
  Execute all tasks automatically in parallel
  ```
- The ouroboros-workflow-starter system prompt will handle:
  - Phase-based execution
  - Parallel task orchestration (1-7 agents)
  - Phase consolidation reports
  - Task updates based on discoveries
  - Auto-generated skill creation/updates

#### Phase Mode:
- Execute one phase at a time
- Wait for user approval between phases
- Use parallelization within each phase (if tasks marked with ⚡)

### 5. Track Progress

Use TodoWrite extensively:

```markdown
- [ ] Phase 1: Foundation (Sequential)
  - [ ] Task 1.1: Setup
  - [ ] Task 1.2: Configuration
- [ ] Phase 2: Core Features (Parallel ⚡)
  - [ ] Task 2.1: Feature A
  - [ ] Task 2.2: Feature B
  - [ ] Task 2.3: Feature C
```

Mark tasks as complete in real-time:
- Update TodoWrite status
- Update tasks.md file with `- [x]`

### 6. Confirm Completion

Before marking the spec as complete:

- Verify ALL tasks in tasks.md are checked `- [x]`
- Verify all acceptance criteria met
- Run any validation/tests specified
- Create final consolidation report

### 7. Offer Next Steps

After completion, ask the user:

```
✅ All tasks completed for {spec-name}!

Would you like to:
1. Archive this spec (/archive-spec {spec-name})
2. Create a pull request
3. Validate implementation (use spec-validator agent)
4. Keep spec active for future reference
```

## Guardrails

- Favor straightforward, minimal implementations first
- Keep changes tightly scoped to the requested outcome
- Refer to `ouroboros/CLAUDE.md` for Ouroboros conventions
- Ask clarifying questions if task descriptions are ambiguous

## Examples

### Example 1: Manual Execution

```
User: /apply user-authentication