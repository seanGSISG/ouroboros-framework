# Pre-Flight Validation Report

**Spec**: {feature-name}
**Generated**: {YYYY-MM-DD HH:MM:SS}
**Status**: {✅ READY | ⚠️ WARNINGS | ❌ NOT READY}

---

## Executive Summary

{2-3 sentence summary of validation results and readiness status}

**Quick Stats:**
- ✅ Requirements → Design: {X}/{Y} ({Z}%)
- ⚠️ Design → Tasks: {X}/{Y} ({Z}%)
- ⚠️ Task dependencies: {X} issues found
- ✅ Context budgets: {status}
- ✅ Phase structure: {status}

**Blocking Issues**: {count}
**Warnings**: {count}

**Recommendation**: {Fix issues first | Proceed with caution | Ready to execute}

---

## 1. Requirements → Design Coverage

### ✅ Fully Covered ({X}/{Y} requirements)

**Requirement {ID}**: {brief description}
- ✅ Mapped to: Design Section {X.Y} "{Section Name}"
- **Design Coverage**: {brief note on how requirement is addressed}

{Repeat for each fully covered requirement}

### ⚠️ Partially Covered ({X} requirements)

**Requirement {ID}**: {brief description}

```
{Full requirement text}
```

- ⚠️ Partial coverage in: Design Section {X.Y}
- **Missing**: {What aspects are not covered}
- **Impact**: {High/Medium/Low} - {brief impact description}

**Recommendation**:
```markdown
Enhance design.md Section {X.Y}:

{Specific additions needed}
```

{Repeat for each partially covered requirement}

### ❌ Missing Design Coverage ({X} requirements)

**Requirement {ID}**: {brief description}

```
{Full requirement text}
```

- ❌ **Not found** in design.md
- **Impact**: {High/Medium/Low} - {Cannot implement without design}

**Recommendation**:
```markdown
Add to design.md:

### {X.Y} {Component/Feature Name}

{Suggested design outline based on requirement}

**Components**:
- {Component 1}
- {Component 2}

**Data Flow**:
{Brief flow description}

**Key Decisions**:
- {Decision 1}
- {Decision 2}
```

**Estimated Time to Fix**: ~{X} minutes

{Repeat for each missing requirement}

---

## 2. Design → Tasks Coverage

### ✅ Fully Covered Components ({X}/{Y})

**Component**: {Component Name} (Design Section {X.Y})

- ✅ {Aspect 1} → Task {X.Y}
- ✅ {Aspect 2} → Task {X.Z}
- ✅ {Aspect 3} → Task {X.W}

**Status**: ✅ COMPLETE (100% covered)

{Repeat for each fully covered component}

### ⚠️ Partially Covered Components ({X} components)

**Component**: {Component Name} (Design Section {X.Y})

**Design Aspects**:
- ✅ {Aspect 1} → Task {X.Y}
- ✅ {Aspect 2} → Task {X.Z}
- ❌ {Aspect 3} → **NO TASK**
- ❌ {Aspect 4} → **NO TASK**

**Status**: ⚠️ PARTIAL ({coverage}% covered)

**Recommendation**: Add tasks:

```markdown
Task {X.Y}: Implement {missing aspect 3}
- Description: {what needs to be implemented}
- Context: ~{X}K tokens
- Duration: ~{X} min
- Dependencies: {task IDs}
- Phase: {phase number}

Task {X.Z}: Implement {missing aspect 4}
- Description: {what needs to be implemented}
- Context: ~{X}K tokens
- Duration: ~{X} min
- Dependencies: {task IDs}
- Phase: {phase number}
```

{Repeat for each partially covered component}

### ❌ No Task Coverage ({X} components)

**Component**: {Component Name} (Design Section {X.Y})

**Design Aspects** (all missing tasks):
- ❌ {Aspect 1} → **NO TASK**
- ❌ {Aspect 2} → **NO TASK**
- ❌ {Aspect 3} → **NO TASK**

**Status**: ❌ MISSING (0% covered)
**Impact**: {High/Medium/Low} - {This entire component won't be implemented}

**Recommendation**: Add comprehensive task set:

```markdown
Task {X.Y}: {Primary implementation task}
- Description: {detailed description}
- Context: ~{X}K tokens
- Duration: ~{X} min
- Dependencies: {task IDs}
- Phase: {phase number}

Task {X.Z}: {Secondary implementation task}
- Description: {detailed description}
- Context: ~{X}K tokens
- Duration: ~{X} min
- Dependencies: {task IDs}
- Phase: {phase number}

{Additional tasks as needed}
```

{Repeat for each component with no coverage}

---

## 3. Task Dependency Validation

### ✅ Valid Dependencies ({X}/{Y} tasks)

All other task dependencies form a valid DAG (Directed Acyclic Graph).

**Example Valid Dependency**:
```
Task {X.Y}: {Description}
└─ Depends on: Task {A.B} ({Earlier task})
   ✅ VALID (correct ordering)
```

### ❌ Circular Dependencies ({X} cycles found)

**Cycle {#}**: {Task chain}

```
Task {A}: {Description}
└─ Depends on: Task {B}

Task {B}: {Description}
└─ Depends on: Task {C}

Task {C}: {Description}
└─ Depends on: Task {A}

❌ CIRCULAR DEPENDENCY DETECTED
Cycle path: {A} → {B} → {C} → {A}
```

**Impact**: High - Prevents execution, tasks cannot determine run order

**Recommendation**:
```markdown
Break the cycle by removing dependency: Task {C} → Task {A}

Reasoning: {Why this dependency should be removed}

Updated Task {C}:
- Remove "Depends on: Task {A}"
- {Explanation of why this works}
```

{Repeat for each cycle}

### ❌ Impossible Orderings ({X} issues)

**Issue {#}**: Backward phase dependency

```
Task {X.Y}: {Description} (Phase {N})
└─ Depends on: Task {A.B} ({Description}, Phase {N+1 or higher})

❌ IMPOSSIBLE ORDER
Task in Phase {N} cannot depend on task in Phase {N+1}
```

**Impact**: High - Task cannot execute when scheduled

**Recommendation**:
```markdown
Option 1: Move Task {A.B} to Phase {N-1} or earlier
- Rename to Task {earlier}.{X}
- Update phase assignment in tasks.md

Option 2: Remove dependency if not truly needed
- Task {X.Y} can proceed without Task {A.B}

Option 3: Move Task {X.Y} to later phase
- Move to Phase {N+2}
- Ensure no downstream impacts
```

{Repeat for each impossible ordering}

---

## 4. Context Budget Analysis

### ✅ All Tasks Safe (<150K limit)

| Task | Context | % of Limit | Status |
|------|---------|------------|--------|
| {X.Y} | {N}K | {P}% | ✅ Safe |
| {X.Z} | {N}K | {P}% | ✅ Safe |
| ... | ... | ... | ... |

**Total Estimated Context**: {sum}K tokens across {N} tasks
**Average per Task**: {avg}K tokens
**Highest Context Task**: {task ID} ({N}K tokens)

### ⚠️ High Context Tasks ({X} warnings)

**Task {X.Y}**: {Description}

- **Estimated Context**: {N}K tokens
- **% of Limit**: {P}% (of 150K safety threshold)
- **Status**: ⚠️ WARNING - High context usage

**Recommendation**:
- Monitor actual context usage during execution
- Consider splitting if approaches or exceeds 150K
- Review if context can be reduced via:
  - Smaller file scope
  - Progressive disclosure
  - Skill-based context loading

{Repeat for each high-context task}

### ❌ Exceeds Limit ({X} tasks)

**Task {X.Y}**: {Description}

- **Estimated Context**: {N}K tokens
- **% of Limit**: {P}% (EXCEEDS 150K safety threshold)
- **Status**: ❌ BLOCKER - Must split before execution

**Recommendation**: Split into subtasks:

```markdown
Task {X.Y}a: {First portion}
- Description: {detailed description}
- Context: ~{N}K tokens ({within limit})
- Duration: ~{X} min
- Dependencies: {task IDs}
- Phase: {phase number}

Task {X.Y}b: {Second portion}
- Description: {detailed description}
- Context: ~{N}K tokens ({within limit})
- Duration: ~{X} min
- Dependencies: {X.Y}a
- Phase: {phase number}

{Additional subtasks as needed}
```

{Repeat for each oversized task}

---

## 5. Phase Structure Validation

### ✅ Valid Phase Organization

```
{Spec Name} - Phase Structure

Phase 1: {Phase Name} ({Sequential | N parallel 🐍})
├── {Task X.Y}: {Description}
├── {Task X.Z}: {Description}
└── {Task X.W}: {Description}

Phase 2: {Phase Name} ({Sequential | N parallel 🐍})
├── {Task X.Y}: {Description}
├── {Task X.Z}: {Description}
├── {Task X.W}: {Description}
└── {Task X.V}: {Description}

{Continue for all phases}
```

**Phase Analysis**:
- Total Phases: {N}
- Sequential Phases: {N}
- Parallel Phases: {N}
- Max Parallel Agents: {N} 🐍 (in Phase {X})
- Circular Dependencies: {0 or count} ✅|❌

**Execution Estimates**:
- Sequential Execution: ~{X} minutes
- With Parallelism: ~{Y} minutes
- Time Savings: {Z}% ✅

---

## 6. Execution Readiness

### {✅ READY | ⚠️ WARNINGS | ❌ NOT READY}

**Coverage Health**:
- Requirements → Design: {X}/{Y} ({P}%) {status icon}
- Design → Tasks: {X}/{Y} ({P}%) {status icon}
- Dependency Graph: {X} issues {status icon}
- Context Budgets: {status description} {status icon}
- Phase Structure: {Valid/Invalid} {status icon}

**Issue Summary**:
- ❌ Blocking Issues: {count}
- ⚠️ Warnings: {count}
- ✅ Passed Checks: {count}

### Must Fix Before Execution (Blockers)

{If blocking issues exist:}

1. **{Issue title}** (Priority: CRITICAL)
   - **Problem**: {description}
   - **Impact**: {why this blocks execution}
   - **Fix**: {specific action needed}
   - **Estimated Time**: ~{X} minutes

{Repeat for each blocking issue}

{If no blocking issues:}
(none) ✅

### Should Fix (Recommended)

{If warnings exist:}

1. **{Issue title}** (Priority: HIGH)
   - **Problem**: {description}
   - **Impact**: {potential issues if not fixed}
   - **Fix**: {specific action needed}
   - **Estimated Time**: ~{X} minutes

{Repeat for each warning}

{If no warnings:}
(none) ✅

### Nice to Have (Optional)

{If minor improvements exist:}

1. **{Improvement title}** (Priority: LOW)
   - **Enhancement**: {description}
   - **Benefit**: {value of making this change}
   - **Estimated Time**: ~{X} minutes

{Repeat for each optional improvement}

{If none:}
(none)

---

## 7. Recommended Next Steps

{For ✅ READY status:}

**Status: ✅ READY FOR EXECUTION**

Your spec is complete and ready to execute!

**Next Steps**:
1. Review this validation report for awareness
2. Proceed with `ouroboros execute {spec-name}`
3. Monitor execution progress
4. Review consolidated results after completion

**Estimated Execution Time**: ~{X} minutes ({with/without} parallelism)

{For ⚠️ WARNINGS status:}

**Status: ⚠️ PROCEED WITH CAUTION**

Your spec is mostly complete but has {X} warnings.

**You have two options**:

**Option A: Fix issues first** (Recommended)
- Estimated fix time: ~{X} minutes
- Results in cleaner, more complete implementation
- Reduces risk of gaps during execution

**Option B: Proceed with warnings**
- Acknowledge that {list main gaps}
- May need to manually implement missing pieces
- Post-execution validation will catch gaps

**Recommended**: Fix {highest priority} issues, then re-run validation

{For ❌ NOT READY status:}

**Status: ❌ NOT READY - MUST FIX BLOCKERS**

Your spec has {X} blocking issues that prevent execution.

**Required Fixes** (estimated {X} minutes total):

1. {Blocker 1 summary + time estimate}
2. {Blocker 2 summary + time estimate}
{Continue for all blockers}

**Process**:
1. Address all blocking issues above
2. Re-run pre-flight validation: `{command to re-run}`
3. Verify status changes to ✅ READY or ⚠️ WARNINGS
4. Then proceed with execution

**Need Help?**
- Review individual issue recommendations above
- Check design.md and tasks.md templates
- Consult Ouroboros documentation

---

## 8. Validation Metadata

**Validation Details**:
- Validator: spec-validator agent
- Validation Mode: pre-flight
- Requirements Parsed: {count}
- Design Components Analyzed: {count}
- Tasks Analyzed: {count}
- Dependencies Checked: {count}
- Total Analysis Time: ~{X} seconds

**Coverage Thresholds Used**:
- Requirements → Design: 90% (current: {actual}%)
- Design → Tasks: 85% (current: {actual}%)
- Context Budget: <150K per task
- Dependency Health: 0 cycles, 0 impossible orders

**Report Template**: `ouroboros/templates/preflight-validation-report.md`

---

**End of Pre-Flight Validation Report**

{Optional: Add project-specific notes or context here}
