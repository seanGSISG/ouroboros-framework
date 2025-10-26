# Context Optimization Guide

**How Ouroboros Saves 60-75% Context Through Intelligent Strategies**

🐍 *The serpent conserves its energy, using only what is needed...* 🐍

---

## Overview

Ouroboros employs **aggressive context optimization** to work within Claude's 200K token limit while handling complex projects. Through four key strategies, typical context usage drops from 15-30K tokens per task to 3-5K tokens.

**Savings Example** (20-task project):
- **Without optimization**: 20 tasks × 16K = 320K tokens (fails)
- **With optimization**: 20 tasks × 5K = 100K tokens (succeeds)
- **Total savings**: 220K tokens (69% reduction)

---

## Strategy 1: XML Tags for Structure

###  Why XML?

XML tags provide structure with minimal tokens compared to verbose JSON or natural language.

**Comparison**:

```json
// JSON (Verbose) - 78 tokens
{
  "task": {
    "id": "2.3",
    "status": "completed",
    "context_used": "45000",
    "duration_minutes": 18,
    "files_modified": [
      "src/models/User.ts",
      "src/models/types.ts"
    ]
  }
}
```

```xml
<!-- XML (Concise) - 42 tokens -->
<task id="2.3" status="completed" context="45K" duration="18min">
  <files>src/models/User.ts, src/models/types.ts</files>
</task>
```

**Savings**: 36 tokens (46% reduction) per task entry

### XML Tag Conventions

**For Tasks**:
```xml
<task id="2.3" context="45K" status="completed"/>
```

**For Phase Summaries**:
```xml
<phase id="2" agents="4" duration="22min">
  <discovery>Early morning flights save $400</discovery>
  <recommendation task="3.1" priority="high">Book morning flight</recommendation>
</phase>
```

**For Pattern Detection**:
```xml
<pattern-detection>
  <pattern name="creative-iterative" score="0.85" confidence="high"/>
  <indicators>
    <indicator>multiple_revisions</indicator>
    <indicator>feedback_loops</indicator>
  </indicators>
</pattern-detection>
```

**For File References**:
```xml
<file path="src/models/User.ts" lines="1-45" purpose="User class"/>
```

### When to Use XML

**✅ DO use XML for**:
- Structured data (task lists, metrics, configurations)
- Cross-references between tasks
- Phase summaries and consolidations
- Pattern detection results
- File/code references

**❌ DON'T use XML for**:
- Natural language explanations
- Code snippets (use markdown)
- User-facing documentation
- Requirement descriptions

---

## Strategy 2: Progressive Disclosure via Auto-Generated Skills

### The Problem

Traditional approach:
```
Task Agent reads:
- requirements.md (8K tokens)
- design.md (12K tokens)
- Previous phase reports (6K tokens)
= 26K tokens before starting work
```

**With 20 tasks**: 20 × 26K = 520K tokens (exceeds budget)

### The Solution: Auto-Generated Skills

After Phase 1 (Requirements + Design approved), Ouroboros creates:

```
.claude/skills/{feature-name}.md  (~3-5K tokens)
```

**Skill Contents**:
- Project context (goals, constraints)
- Key architectural decisions
- Important terminology
- Patterns to follow
- Discoveries from previous phases
- References to full specs (for deep dives)

**New Workflow**:
```
Task Agent reads:
- .claude/skills/{feature-name}.md (4K tokens)
- Only reads full specs if skill insufficient
= 4K tokens typically, 10K worst case
```

**With 20 tasks**: 20 × 4K = 80K tokens

**Savings**: 440K tokens (85% reduction!)

### Skill File Structure

```markdown
# {Feature Name} - Project Skill

## Project Context
- Goal: [What we're building]
- Constraints: [Technical/business limits]
- Target: [Who/what this is for]

## Key Decisions
- Architecture: [Chosen approach and why]
- Tech Stack: [If code project]
- Structure: [If non-code project]

## Important Terminology
- Term 1: [Project-specific meaning]
- Term 2: [Project-specific meaning]

## Patterns Observed
- Error Handling: [How we do it]
- Validation: [Approach we use]
- Organization: [File/section structure]

## Discoveries from Previous Phases
- Phase 2: [Key findings]
- Phase 3: [Adaptations made]

## Quick References
- Full requirements: ouroboros/specs/{feature}/requirements.md (read if need detail on requirement X)
- Full design: ouroboros/specs/{feature}/design.md (read if need architecture deep-dive)
```

### When Agents Read Full Specs

**Skill is sufficient** (90% of tasks):
- Implementation matches patterns documented
- Terminology is clear from skill
- No complex algorithm details needed

**Need full spec** (10% of tasks):
- Complex algorithm implementation (read design section X)
- Novel edge case not in skill (read requirement Y)
- Integration details not summarized (read design integration section)

---

## Strategy 3: Summary Files Instead of Re-Execution

### The Problem

Without summaries, orchestrator must re-execute or re-read all task outputs to understand phase results.

**Example**:
```
Phase 2: 4 parallel tasks completed
Orchestrator needs to know what happened

Traditional approach:
- Read task 2.1 output (full files created, 15K tokens)
- Read task 2.2 output (full files created, 18K tokens)
- Read task 2.3 output (full files created, 12K tokens)
- Read task 2.4 output (full files created, 16K tokens)
= 61K tokens to consolidate
```

### The Solution: Summary Files

Each task agent saves a summary:
```
ouroboros/specs/{feature}/phases/phase-2/summary-2.1.md
```

**Summary Template** (~1-2K tokens each):
```markdown
# Task 2.1 Completion Summary

## What Was Accomplished
- Created User model with validation
- Added database schema
- 12 unit tests, all passing

## Discoveries Made
- Email validation pattern can be reused
- JWT expiry needs configuration

## Recommendations for Future Tasks
- Task 3.3: Reuse email validator from User.ts:52
```

**Orchestrator reads**:
```
- summary-2.1.md (1.5K tokens)
- summary-2.2.md (1.8K tokens)
- summary-2.3.md (1.2K tokens)
- summary-2.4.md (1.6K tokens)
= 6.1K tokens to consolidate
```

**Savings**: 55K tokens (90% reduction) per phase consolidation

### Summary File Best Practices

**✅ DO include**:
- Concrete deliverables (files created, decisions made)
- Unexpected discoveries
- Recommendations for future tasks
- Dependencies discovered
- Metrics (estimated vs. actual context/time)

**❌ DON'T include**:
- Full code listings
- Repetition of requirements
- Verbose explanations
- Redundant information

**Length Target**: 200-400 words (~1-2K tokens)

---

## Strategy 4: Delta-Based Task Updates

### The Problem

When discoveries require task updates, traditional approach rewrites entire tasks.md file.

**Example**:
```
tasks.md has 25 tasks (~15K tokens)
Discovery: Need to add 1 new task

Traditional: Rewrite entire tasks.md (15K tokens)
Delta: Describe change only (0.5K tokens)
```

### The Solution: Version and Delta

**Version Tasks File**:
```
tasks.md       → Original (v1)
tasks-v2.md    → After Phase 2 discoveries
tasks-v3.md    → After Phase 4 discoveries
```

**Delta Format**:
```markdown
## Task Updates (Phase 2 → v2)

### Modified Tasks
- **Task 3.1**: Added "Book morning flight (saves $400)"
  - BEFORE: Book roundtrip flights
  - AFTER: Book morning roundtrip flights (saves $400 vs afternoon)

### Added Tasks
- **Task 3.6**: Configure JWT expiry via environment variable
  - Reason: Discovery in Phase 2 showed hardcoded expiry insufficient

### Removed Tasks
- **Task 4.5**: Venice gondola tour
  - Reason: Reduced Venice from 2 to 1 night due to cost
```

**Savings**: 14.5K tokens per update (97% reduction)

---

## Strategy 5: Context-Aware Dynamic Phase Sizing

### The Problem

Fixed parallelization (always 5 agents) wastes context or causes overflow.

**Example Problems**:
- 5 small tasks (20K each) = 100K total → Could run 7 agents
- 5 large tasks (140K each) = 700K total → Context overflow!

### The Solution: Dynamic Sizing

**Context-Based Formula**:
```
Max Agents = min(7, floor(600K / max_task_context))

Where:
- 600K = Conservative total budget
- max_task_context = Largest task in the phase
- Safety margin: Always leave 50K per agent unused
```

**Examples**:

**Small Tasks**:
```
Phase has 6 tasks, largest is 35K tokens
Max Agents = min(7, floor(600K / 35K)) = min(7, 17) = 7
Result: Run all 6 in parallel (with 1 slot unused)
```

**Medium Tasks**:
```
Phase has 5 tasks, largest is 85K tokens
Max Agents = min(7, floor(600K / 85K)) = min(7, 7) = 7
Result: Run all 5 in parallel
```

**Large Tasks**:
```
Phase has 4 tasks, largest is 140K tokens
Max Agents = min(7, floor(600K / 140K)) = min(7, 4) = 4
Result: Run all 4 in parallel (at capacity limit)
```

**Extra-Large Tasks**:
```
Phase has 3 tasks, largest is 180K tokens
Max Agents = min(7, floor(600K / 180K)) = min(7, 3) = 3
Result: Run 3 in parallel OR split large tasks first
```

### Adaptive Sizing Benefits

- **No waste**: Use all available parallelism
- **No overflow**: Prevent context budget violations
- **Optimal speed**: Maximum safe parallelization

---

## Combined Impact: Real-World Example

### Scenario: REST API with 18 Tasks

**Without Optimization**:
```
Per Task:
- Read requirements.md: 8K
- Read design.md: 12K
- Read previous task outputs: 6K
- Write new code: 10K
= 36K tokens per task

18 tasks × 36K = 648K tokens
Result: FAILS (exceeds 200K per agent, even with parallelization)
```

**With Optimization**:
```
Per Task:
- Read .claude/skills/user-auth-api.md: 4K (XML structured)
- Read previous task summaries: 2K (if needed)
- Write new code: 10K
= 16K tokens per task

18 tasks × 16K = 288K tokens distributed
With 5 agents in parallel: 288K / 5 = ~58K per agent

Result: SUCCESS with room to spare
```

**Savings**: 360K tokens (56% reduction)

---

## Token Reduction Checklist

### Planning Phase

- [ ] Estimate context budget per task
- [ ] Apply dynamic sizing formula
- [ ] Identify tasks that can share skill file
- [ ] Plan summary file usage

### Execution Phase

- [ ] Use XML tags in all structured data
- [ ] Generate skill file after Phase 1
- [ ] Have task agents read skill first
- [ ] Save summary files after each task
- [ ] Use delta format for task updates
- [ ] Version tasks.md instead of rewriting

### Validation Phase

- [ ] Verify agents used skill file (check logs)
- [ ] Confirm summary files created
- [ ] Check actual context vs. estimated
- [ ] Adjust sizing for next phase if needed

---

## Advanced Techniques

### Technique 1: Lazy Loading

Read full specs only when skill is insufficient:

```markdown
## Task Implementation

1. Read skill file
2. Check if sufficient for task
   - YES: Proceed with implementation
   - NO: Read specific design section needed
3. Implement
4. Save summary
```

**Savings**: Avoid reading 10-20K tokens 90% of the time

### Technique 2: Skill Updating

Update skill file with discoveries after each phase:

```markdown
## Discoveries from Phase 3

- Found: Rate limiter requires Redis
- Pattern: All async operations use Promise.all
- Convention: Error messages prefixed with [ERR-{code}]
```

**Benefit**: Subsequent tasks have latest context without reading summaries

### Technique 3: Reference Compression

Instead of copying code, use references:

```markdown
## Code Reference

User validation at: src/models/User.ts:45-67
Reuse this pattern for Post validation

DON'T: Copy 22 lines of code (3K tokens)
DO: Reference location (50 tokens)
```

**Savings**: 2.95K tokens per reference

---

## Monitoring Context Usage

### Per-Task Tracking

**In task summaries**:
```markdown
## Metrics
- Estimated context: 45K tokens
- Actual context: 38K tokens
- Variance: -15% (under-budget, good!)
```

### Per-Phase Tracking

**In phase consolidation**:
```markdown
## Phase Metrics

### Context Budget
- Estimated: 180K tokens distributed
- Actual: 152K tokens distributed
- Variance: -16% (under-budget)

### Agent Context Usage
| Agent | Task | Estimated | Actual | Notes |
|-------|------|-----------|--------|-------|
| 1     | 2.1  | 45K       | 38K    | Skill file helped |
| 2     | 2.2  | 52K       | 48K    | Efficient |
| 3     | 2.3  | 42K       | 35K    | Reused patterns |
| 4     | 2.4  | 41K       | 31K    | Skill + summaries |
```

### Red Flags

⚠️ **Warning Signs**:
- Agent exceeds 150K tokens
- Actual > 130% of estimated
- Skill file not being used
- Summary files too verbose (>3K tokens)

**Actions**:
- Review skill file quality
- Split tasks further
- Reduce parallel agent count
- Compress summaries

---

## Best Practices Summary

### XML Tags
- ✅ Use for all structured data
- ✅ Keep attributes concise
- ✅ ~40% savings vs. JSON

### Auto-Generated Skills
- ✅ Create after Phase 1
- ✅ Update with discoveries
- ✅ 60-75% savings per task

### Summary Files
- ✅ 200-400 words each
- ✅ Focus on discoveries and recommendations
- ✅ 90% savings for consolidation

### Delta Updates
- ✅ Version tasks files
- ✅ Describe changes only
- ✅ 95% savings per update

### Dynamic Sizing
- ✅ Apply sizing formula
- ✅ Monitor and adjust
- ✅ Optimal parallelization

---

🐍 **The serpent's wisdom: Conserve context as you conserve energy—use only what advances the goal.** 🐍
