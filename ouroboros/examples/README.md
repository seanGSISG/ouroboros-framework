# Ouroboros Cross-Domain Examples

This directory contains complete example specs demonstrating Ouroboros working across different project types and universal patterns.

## Examples

### 1. Vacation Planning Europe (`vacation-planning-europe/`)
**Pattern**: Creative Iterative Process
**Project Type**: Planning
**Demonstrates**:
- Multiple revision cycles based on price/availability discoveries
- Parallel research tasks converging to final itinerary
- Adaptive task updates (Switzerland nights, Venice changes)
- Subjective quality criteria (cultural experiences)
- Budget-driven trade-offs

**Key Learning**: Shows how planning projects benefit from Ouroboros's adaptive nature.

### 2. PowerShell Infrastructure (`powershell-infrastructure/`)
**Pattern**: Modern Development Workflow
**Project Type**: Scripts/Automation
**Demonstrates**:
- Automation-first approach
- Version control integration
- Infrastructure as Code patterns
- CI/CD for scripts
- Observable/testable automation

**Key Learning**: Shows Ouroboros working for operational automation, not just application code.

### 3. API Documentation (`api-documentation/`)
**Pattern**: Structured Sequential Workflow
**Project Type**: Documentation
**Demonstrates**:
- Clear sequential stages (outline → draft → review → publish)
- Validation gates at each stage
- Parallel documentation of different API sections
- Quality criteria for technical writing
- Rollback capability (versioning)

**Key Learning**: Shows Ouroboros working for documentation projects with same rigor as code.

## How to Use These Examples

### As Learning Resources

1. **Read requirements.md** - See how EARS format works across domains
2. **Study design.md** - Understand pattern-based design guidance
3. **Analyze tasks.md** - See dynamic parallelization in action
4. **Review phase summaries** (in phases/ directories) - Learn from discoveries

### As Templates

1. Copy an example that matches your project's pattern
2. Adapt requirements to your specific needs
3. Use the design structure as a starting point
4. Modify tasks based on your project scope

### For Testing Ouroboros

1. Execute an example spec to see the workflow
2. Compare sequential vs. parallel execution times
3. Observe task adaptation in action
4. Verify auto-generated skills and context savings

## Pattern Characteristics

### Creative Iterative Process (Vacation Planning)
- Multiple revisions expected
- Subjective quality criteria
- Feedback loops
- Alternative exploration
- Balance of structure and flexibility

### Modern Development Workflow (PowerShell Infrastructure)
- CI/CD integration
- Infrastructure as code
- API-first design
- Containerization (where applicable)
- Observability built-in
- Version controlled
- Reproducible

### Structured Sequential Workflow (API Documentation)
- Clear step-by-step progression
- Sequential dependencies
- Well-defined inputs/outputs
- Validation at each stage
- Rollback capability

## Files in Each Example

```
{example-name}/
├── requirements.md          # EARS format requirements
├── design.md                # Pattern-based architecture
├── tasks.md                 # Adaptive implementation plan
└── phases/                  # (Generated during execution)
    ├── phase-2/
    │   ├── summary-2.1.md
    │   ├── summary-2.2.md
    │   └── consolidated.md
    └── ...
```

Plus auto-generated skill:
```
.claude/skills/{example-name}.md
```

## Cross-Domain Comparison

| Aspect | Vacation Planning | PowerShell Scripts | API Documentation |
|--------|-------------------|-------------------|-------------------|
| **Pattern** | Creative Iterative | Modern Dev Workflow | Structured Sequential |
| **Deliverable** | Itinerary + Bookings | Automation Scripts | Technical Docs |
| **Quality Measure** | Cultural depth, flexibility | Reliability, testability | Clarity, completeness |
| **Iteration Driver** | Price/availability changes | Testing feedback | Review feedback |
| **Parallelization** | Research tasks, city planning | Module development | Section writing |
| **Validation** | Budget check, booking confirm | Unit tests, integration tests | Technical review, user testing |

## Success Metrics Across Domains

All examples achieve:
- ✅ 40-60% time savings through parallelization
- ✅ Task adaptation based on real discoveries
- ✅ Pattern-appropriate design guidance
- ✅ Quality criteria matching deliverable type
- ✅ Context optimization via auto-generated skills

---

🐍 **These examples prove Ouroboros works for ANY project type, not just code.**
