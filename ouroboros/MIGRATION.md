# Migration Guide: OpenSpec v1 → Ouroboros v2

**"The serpent sheds its old skin to reveal something stronger."** 🐍

## Overview

This guide helps you migrate existing OpenSpec v1 specs to Ouroboros v2. The good news: **Ouroboros is 100% backward compatible**. Your existing specs will continue to work without changes.

However, to take advantage of new features (adaptive tasks, pattern recognition, auto-generated skills, etc.), follow this guide.

## What Changed?

### Directory Structure

**Before (OpenSpec v1):**
```
.claude/specs/{feature-name}/
├── requirements.md
├── design.md
└── tasks.md
```

**After (Ouroboros v2):**
```
ouroboros/specs/{feature-name}/
├── requirements.md
├── design.md
├── tasks.md
└── phases/                    # NEW: Phase summaries
    ├── phase-1/
    │   └── consolidated.md
    └── phase-2/
        ├── summary-2.1.md
        ├── summary-2.2.md
        └── consolidated.md
```

**Plus:**
```
.claude/skills/
└── {feature-name}.md          # NEW: Auto-generated skill
```

### Skill Name

- **Old**: `openspec`
- **New**: `ouroboros` (but `openspec` still works as alias)

## Migration Options

### Option 1: Do Nothing (Backward Compatible)

Your existing specs work as-is. No migration needed.

**Pros:**
- Zero effort
- No breaking changes

**Cons:**
- Miss out on new features (adaptive tasks, auto-skills, etc.)

### Option 2: Migrate Directory (Recommended)

Move your spec from `.claude/specs/` to `ouroboros/specs/` to enable new features.

**Step-by-step:**

1. **Create new directory structure:**
   ```bash
   mkdir -p ouroboros/specs/{feature-name}
   ```

2. **Move spec files:**
   ```bash
   # Replace {feature-name} with your actual feature name
   mv .claude/specs/{feature-name}/* ouroboros/specs/{feature-name}/
   ```

3. **Create phases directory:**
   ```bash
   mkdir -p ouroboros/specs/{feature-name}/phases
   ```

4. **Update any hardcoded paths in your spec files:**
   - Find/replace: `.claude/specs/` → `ouroboros/specs/`
   - Check requirements.md, design.md, tasks.md for path references

5. **Re-run spec with Ouroboros:**
   ```
   Use ouroboros workflow to implement {feature-name}
   Execute remaining tasks
   ```

**Benefits:**
- ✅ Adaptive task system
- ✅ Phase consolidation
- ✅ Auto-generated skills
- ✅ Pattern recognition
- ✅ Dynamic phase sizing

### Option 3: Fresh Spec with Ouroboros

Create a new spec using Ouroboros from scratch (if starting a new feature).

**Command:**
```
I want to create {feature description}. Use the ouroboros workflow.
```

## Feature-by-Feature Migration

### Enable Adaptive Task System

**What it does:** Tasks evolve based on discoveries during execution.

**How to enable:**
1. Ensure spec is in `ouroboros/specs/{feature}/`
2. Run tasks with Ouroboros workflow
3. Agents will auto-save summaries to `phases/`
4. You'll get interactive task update prompts

**No code changes needed** - automatic when using ouroboros/specs/ location.

### Enable Auto-Generated Skills

**What it does:** Creates `.claude/skills/{feature}.md` for 60-75% context savings.

**How to enable:**
1. Spec must be in `ouroboros/specs/{feature}/`
2. Skills are auto-generated after Phase 1 completion
3. Subsequent tasks automatically use the skill instead of full specs

**Check:**
```bash
ls -la .claude/skills/{feature-name}.md
```

### Enable Pattern Recognition

**What it does:** Detects project pattern and optimizes task structure.

**How to enable:**
1. No changes needed - automatic
2. Ouroboros detects pattern from your requirements/design
3. Applies pattern-specific strategies

**Manual override (if needed):**
Add to `tasks.md`:
```markdown
<!-- DETECTED_PATTERN: creative-iterative -->
```

### Enable Universal Quality Improvement

**What it does:** Quality checks work for ANY project type.

**How to enable:**
1. Call spec-quality agent manually:
   ```
   Review the {component} for quality improvements using spec-quality
   ```

2. Or enable in config:
   ```json
   {
     "enhancements": {
       "qualityImprovement": true
     }
   }
   ```

## Path Reference Updates

If you have hardcoded paths in your spec files, update them:

### Find and Replace

**In requirements.md, design.md, tasks.md:**
- Find: `.claude/specs/`
- Replace: `ouroboros/specs/`

**Example (before):**
```markdown
See design details in `.claude/specs/user-auth/design.md`
```

**Example (after):**
```markdown
See design details in `ouroboros/specs/user-auth/design.md`
```

### Agent Path References

Agent files automatically use correct paths when you use `ouroboros/specs/`. No changes needed.

## Configuration

### ouroboros-config.json

Located at: `ouroboros/config/ouroboros-config.json`

**Toggle features:**
```json
{
  "enhancements": {
    "adaptiveTaskSystem": true,       // Enable task evolution
    "patternRecognition": true,       // Auto-detect patterns
    "dynamicSkillsGeneration": true,  // Auto-generate skills
    "requirementElicitation": true,   // Enhanced questioning
    "qualityImprovement": true,       // Universal quality checks
    "gapDetection": true,             // Validate coverage
    "preFlightValidation": true,      // Pre-execution checks
    "dynamicPhaseSizing": true,       // 1-7 agents optimization
    "smartScheduling": true,          // Intelligent task ordering
    "versionControlIntegration": true, // Git integration
    "selfImprovementMetrics": true,   // Learning engine
    "progressVisualization": false    // (Future feature)
  }
}
```

**To disable a feature:** Set to `false`

## Common Migration Issues

### Issue 1: "Can't find spec files"

**Cause:** Spec still in `.claude/specs/` but trying to use Ouroboros features

**Fix:**
```bash
mv .claude/specs/{feature}/* ouroboros/specs/{feature}/
```

### Issue 2: "Skills not being generated"

**Cause:** Spec not in `ouroboros/specs/` location

**Fix:** Move spec to ouroboros/specs/ (see Option 2 above)

### Issue 3: "Phase consolidation not working"

**Cause:** Missing `phases/` directory

**Fix:**
```bash
mkdir -p ouroboros/specs/{feature}/phases
```

### Issue 4: "References to old paths broken"

**Cause:** Hardcoded `.claude/specs/` paths in spec files

**Fix:** Find/replace `.claude/specs/` → `ouroboros/specs/` in all spec files

## Testing Your Migration

After migrating, verify everything works:

1. **Check directory structure:**
   ```bash
   ls -R ouroboros/specs/{feature-name}/
   ```

   Should show:
   ```
   requirements.md
   design.md
   tasks.md
   phases/
   ```

2. **Run a single task:**
   ```
   Execute task 1.1 from {feature-name} spec
   ```

   Should create: `ouroboros/specs/{feature}/phases/phase-1/summary-1.1.md`

3. **Check for auto-generated skill:**
   ```bash
   ls .claude/skills/{feature-name}.md
   ```

4. **Verify agents work:**
   ```
   Use spec-requirements to review {feature-name} requirements
   ```

## Rollback (If Needed)

If migration causes issues, rollback:

```bash
# Move spec files back
mv ouroboros/specs/{feature-name}/* .claude/specs/{feature-name}/

# Remove phases directory
rm -rf ouroboros/specs/{feature-name}/phases

# Remove auto-generated skill (optional)
rm .claude/skills/{feature-name}.md
```

Your spec will work as before with OpenSpec v1 behavior.

## Benefits Summary

**After migration, you get:**
- 🐍 Tasks that adapt based on real discoveries
- 📊 60-75% context savings via auto-generated skills
- ⚡ Smarter parallelization (1-7 agents dynamically)
- 📝 Phase consolidation with task update recommendations
- 🔄 Self-improvement from execution learnings
- 🌍 Universal quality checks (works for ANY project type)
- ✅ Pre-flight validation catches issues before execution

## Support

**Questions?** Check:
- `ouroboros/CLAUDE.md` - Workflow guide
- `ouroboros/config/ouroboros-config.json` - Configuration options
- `.claude/specs/openspec-enhancements/README-v2.md` - Full documentation

---

🐍 **The serpent welcomes you to the circle of continuous improvement.** 🐍
