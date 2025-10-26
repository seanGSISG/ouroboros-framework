# Ouroboros Quickstart

**Get your first spec running in 5 minutes.**

---

## What is Ouroboros?

A framework for planning and executing ANY project type through:
- Universal patterns (works for code, docs, planning, creative work)
- Intelligent expansion (templates → detailed specs)
- Parallel execution (40-60% faster)
- Context savings (60-75% less tokens)

---

## The 3-Step Workflow

### Step 1: Create

```
/ou-new-spec {your-feature}
```

Answer 2 questions → Get pattern-based templates

### Step 2: Expand

```
/ou-expand-spec {your-feature} --auto
```

Get detailed, validated specs ready to execute

### Step 3: Execute

```
Use ouroboros workflow to implement {your-feature}
```

Watch tasks run in parallel, adapt to discoveries, deliver results

---

## Complete Example: Build a User API

```bash
# Create the spec
> /ou-new-spec user-api

  What type of project?
  > 1 (Code project)

  CRUD operations?
  > Yes

  ✅ Created spec: user-api (Resource Management pattern)

# Expand with auto-mode (uses smart defaults)
> /ou-expand-spec user-api --auto

  🔍 Analyzing...
  ✅ Expansion complete!
     - 10 detailed requirements
     - RESTful API architecture
     - 12 tasks across 4 phases
     - Auto-skill generated (60% context savings)
     - Validation: READY

# Execute
> Use ouroboros workflow to implement user-api

  Phase 1: Foundation
    ✅ API structure
    ✅ Database setup

  Phase 2: CRUD Operations (4 parallel agents 🐍)
    ✅ Create user
    ✅ Read user
    ✅ Update user
    ✅ Delete user

  Phase 3: Testing (3 parallel agents 🐍)
    ✅ Unit tests
    ✅ Integration tests
    ✅ API docs

  ✅ user-api complete! (42 min vs 90 min sequential)

# Archive when done
> /ou-archive user-api
```

---

## All 8 Commands

| Command | What it does |
|---------|--------------|
| `/ou-new-spec` | Create spec from templates |
| `/ou-expand-spec` | Transform templates into detailed specs |
| `/ou-apply` | Execute spec tasks manually |
| `/ou-list-specs` | View all specs and progress |
| `/ou-archive-spec` | Archive completed specs |
| `/ou-archive` | Shorthand for archive-spec |
| `/ou-proposal` | Alias for new-spec |
| `/ou-update` | Update framework blocks |

**Quick workflow**:
```
/ou-new-spec → /ou-expand-spec --auto → Execute → /ou-archive
```

---

## Two Expansion Modes

### Interactive (asks questions)
```
/ou-expand-spec my-feature
```
Best for: Custom projects where you want control

**Example questions**:
- What resources are you managing?
- What's your storage approach?
- Which authentication method?
- How many iteration cycles?

### Automated (uses defaults)
```
/ou-expand-spec my-feature --auto
```
Best for: Rapid prototyping, common patterns

**Smart defaults based on pattern**:
- Resource Management → PostgreSQL, JWT, REST API
- Creative Iterative → 3 cycles, peer review
- Modern Dev Workflow → Docker, GitHub Actions

---

## The 5 Universal Patterns

Ouroboros auto-selects the best pattern for your project:

1. **🗄️ Resource Management** - CRUD (APIs, databases)
2. **📝 Structured Sequential** - Step-by-step (pipelines, guides)
3. **🎨 Creative Iterative** - Draft-refine (designs, planning)
4. **🔬 Exploratory Research** - Discovery (analysis, investigation)
5. **⚙️ Modern Dev Workflow** - Automation (CI/CD, infrastructure)

You don't pick the pattern—it's detected automatically from your answers.

---

## More Examples

### Vacation Planning
```
/ou-new-spec japan-trip-2025
→ Pattern: Creative Iterative

/ou-expand-spec japan-trip-2025 --auto

Use ouroboros workflow to implement japan-trip-2025

Result: Complete itinerary in ~90 minutes
```

### Documentation
```
/ou-new-spec api-documentation
→ Pattern: Structured Sequential

/ou-expand-spec api-documentation --interactive
→ Q: How many sections? A: 5

Use ouroboros workflow to implement api-documentation

Result: Professional docs in ~50 minutes
```

### Infrastructure
```
/ou-new-spec k8s-deployment
→ Pattern: Modern Dev Workflow

/ou-expand-spec k8s-deployment --auto

Use ouroboros workflow to implement k8s-deployment

Result: Automated deployment pipeline in ~75 minutes
```

---

## Tips

✅ **Do:**
- Use `/ou-expand-spec --auto` for speed
- Let patterns guide you (they're proven)
- Trust pre-flight validation warnings
- Check `/ou-list-specs` regularly

❌ **Don't:**
- Skip expansion (templates need it!)
- Ignore validation blockers
- Create specs for <1 hour tasks
- Manually edit phase directories

---

## What Happens During Execution?

1. **Pre-flight check** - Validates spec is ready
2. **Phase-by-phase execution** - Runs sequential phases in order
3. **Parallel tasks** - Up to 7 agents work simultaneously
4. **Discovery tracking** - Saves findings after each task
5. **Consolidation** - Reviews all discoveries per phase
6. **Task evolution** - Recommends updates (you approve)
7. **Completion** - All tasks done, artifacts created

---

## Quick Troubleshooting

**Q: Expansion says "blockers detected"?**
A: Fix the issues listed, then run `/ou-expand-spec {name} --validate-only` to check

**Q: Can I edit the spec after expansion?**
A: Yes! Just edit requirements.md, design.md, or tasks.md directly

**Q: How do I know which pattern I got?**
A: Run `/ou-list-specs` - shows pattern for each spec

**Q: Can I skip expansion?**
A: Not recommended - templates have placeholders that won't work in execution

---

## Next Steps

### Just Starting?
1. Run `/ou-new-spec` with YOUR project idea
2. Choose interactive or auto expansion
3. Execute and watch the magic!

### Want More Control?
- Use interactive mode: `/ou-expand-spec {name}`
- Manually edit the 3 spec files
- Re-run validation: `/ou-expand-spec {name} --validate-only`

### Need Help?
- Full guide: [README.md](README.md)
- Patterns explained: [ouroboros/PATTERNS.md](ouroboros/PATTERNS.md)
- Real examples: [ouroboros/examples/](ouroboros/examples/)
- Deep dive: [ouroboros/CLAUDE.md](ouroboros/CLAUDE.md)

---

## Summary

```
1. /ou-new-spec {name}        # Create from template
2. /ou-expand-spec {name}      # Make it detailed & valid
3. Execute                     # Run the workflow
4. /ou-archive {name}          # Clean up when done
```

**That's it!** The whole framework in 4 commands.

---

🐍 *The serpent welcomes you—each cycle makes you stronger!* 🐍
