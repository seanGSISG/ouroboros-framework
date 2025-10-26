# Universal Pattern Recognition

**Purpose**: Automatically detect project patterns and learn from completed executions to improve future specs, working across ANY project type (code, documentation, planning, scripts, creative work).

**Location**: `ouroboros/intelligence/pattern-recognizer.md`

---

## Overview

The Pattern Recognizer is a core component of the Ouroboros framework that enables project-agnostic pattern detection and learning. Unlike traditional frameworks that rely on technology stacks, this system uses **characteristic-based patterns** that apply universally across domains.

**Key Principles**:
- Patterns are based on **characteristics**, not tech stacks
- Works for code, documentation, planning, scripts, creative projects
- Learns from each execution to improve future pattern detection
- Provides actionable recommendations for task structuring

---

## The Five Universal Patterns

### Pattern 1: Structured Sequential Workflow

**Characteristics**:
- Clear step-by-step progression
- Each step depends on previous completion
- Well-defined inputs and outputs
- Validation at each stage
- Rollback capability

**Pattern Signature**:
```json
{
  "pattern": "structured-sequential",
  "indicators": [
    "clear_stages",
    "sequential_dependencies",
    "validation_gates",
    "rollback_capability"
  ],
  "task_strategy": "mostly_sequential_with_parallel_substeps",
  "phase_approach": "one_stage_per_phase",
  "typical_phase_count": "4-7"
}
```

**Examples Across Domains**:
- **Code**: Data pipeline (ingest → validate → transform → load → verify)
- **Documentation**: User guide (outline → draft → review → revise → publish)
- **Planning**: Event planning (venue → catering → invitations → schedule → execution)
- **Scripts**: Deployment script (backup → test → deploy → verify → rollback-ready)
- **Creative**: Recipe development (ingredients → prep → cook → plate → taste-test)

**Detection Keywords**:
- Requirements: "step-by-step", "sequential", "pipeline", "workflow", "stages"
- Design: "phase", "gate", "validation", "rollback", "linear"
- Tasks: Sequential task numbering, explicit dependencies

**Recommended Task Structure**:
- Sequential phases with parallel substeps
- Validation checkpoints between phases
- Rollback capabilities built in
- Clear phase boundaries

---

### Pattern 2: Creative Iterative Process

**Characteristics**:
- Multiple draft/refinement cycles
- Subjective quality criteria
- Feedback-driven improvements
- Exploration of alternatives
- Convergence to final solution

**Pattern Signature**:
```json
{
  "pattern": "creative-iterative",
  "indicators": [
    "multiple_revisions",
    "subjective_evaluation",
    "feedback_loops",
    "alternative_exploration",
    "refinement_cycles"
  ],
  "task_strategy": "parallel_alternatives_then_converge",
  "phase_approach": "iteration_phases",
  "typical_phase_count": "3-5"
}
```

**Examples Across Domains**:
- **Code**: UI/UX design (mockup → prototype → user-test → refine → repeat)
- **Documentation**: Blog post (brainstorm → outline → draft → edit → polish)
- **Planning**: Vacation itinerary (research → rough-plan → refine → book → adjust)
- **Scripts**: Performance optimization (profile → hypothesize → test → measure → iterate)
- **Creative**: Logo design (concepts → sketches → refinement → variations → finalize)

**Detection Keywords**:
- Requirements: "iterative", "refine", "feedback", "revise", "improve", "alternatives"
- Design: "iteration", "draft", "review cycle", "refinement"
- Tasks: Multiple revision tasks, feedback checkpoints

**Recommended Task Structure**:
- Initial exploration phase (parallel alternatives)
- Iteration cycles with feedback
- Convergence phase
- Quality refinement passes

---

### Pattern 3: Resource Management

**Characteristics**:
- CRUD operations (Create, Read, Update, Delete)
- Data validation and constraints
- State tracking and persistence
- Access control and permissions
- Lifecycle management

**Pattern Signature**:
```json
{
  "pattern": "resource-management",
  "indicators": [
    "crud_operations",
    "state_persistence",
    "validation_rules",
    "access_patterns",
    "lifecycle_stages"
  ],
  "task_strategy": "parallel_by_resource_type",
  "phase_approach": "infrastructure_then_operations",
  "typical_phase_count": "4-6"
}
```

**Examples Across Domains**:
- **Code**: REST API (endpoints for user CRUD, auth, validation)
- **Documentation**: Knowledge base (create articles, organize, update, archive)
- **Planning**: Budget management (add expenses, categorize, track, report)
- **Scripts**: Infrastructure management (provision resources, monitor, update, destroy)
- **Creative**: Asset library (import assets, tag, organize, version, export)

**Detection Keywords**:
- Requirements: "create", "read", "update", "delete", "manage", "store", "retrieve"
- Design: "CRUD", "database", "storage", "state", "persistence"
- Tasks: Separate tasks for create/read/update/delete operations

**Recommended Task Structure**:
- Phase 1: Infrastructure setup (storage, validation)
- Phase 2-4: CRUD operations (can parallelize by resource type)
- Phase 5: Access control and permissions
- Phase 6: Lifecycle and maintenance

---

### Pattern 4: Exploratory Research

**Characteristics**:
- Unknown scope at start
- Discovery-driven approach
- Hypothesis testing
- Data gathering and analysis
- Synthesizing findings

**Pattern Signature**:
```json
{
  "pattern": "exploratory-research",
  "indicators": [
    "unknown_scope",
    "discovery_driven",
    "hypothesis_testing",
    "synthesis_required",
    "flexible_approach"
  ],
  "task_strategy": "breadth_first_then_depth",
  "phase_approach": "exploration_then_focus",
  "typical_phase_count": "3-4"
}
```

**Examples Across Domains**:
- **Code**: Performance investigation (profile → analyze → experiment → measure → conclude)
- **Documentation**: Competitive analysis (identify competitors → research → compare → synthesize)
- **Planning**: Vendor selection (requirements → research options → evaluate → decide)
- **Scripts**: Security audit (scan → investigate findings → test vulnerabilities → report)
- **Creative**: Market research (identify trends → gather data → analyze → recommend)

**Detection Keywords**:
- Requirements: "investigate", "research", "explore", "analyze", "discover", "find"
- Design: "hypothesis", "exploration", "investigation", "analysis"
- Tasks: Exploratory tasks before focused tasks

**Recommended Task Structure**:
- Phase 1: Broad exploration (gather data points)
- Phase 2: Initial analysis (identify patterns)
- Phase 3: Deep investigation (focus on findings)
- Phase 4: Synthesis and recommendations

---

### Pattern 5: Modern Development Workflow

**Characteristics**:
- CI/CD integration
- Infrastructure as code
- API-first design
- Containerization/orchestration
- Observability and monitoring built-in
- Automation-first approach

**Pattern Signature**:
```json
{
  "pattern": "modern-dev-workflow",
  "indicators": [
    "automation_first",
    "version_controlled",
    "reproducible",
    "observable",
    "api_driven",
    "containerized"
  ],
  "task_strategy": "parallel_automation_tracks",
  "phase_approach": "foundation_automation_deployment_observability",
  "typical_phase_count": "4-6"
}
```

**Examples Across Domains**:
- **Code**: Microservice (API design → containerize → CI/CD → deploy → monitor)
- **Documentation**: Doc-as-code (write markdown → version control → auto-publish → analytics)
- **Planning**: Workflow automation (define process → codify → test → deploy → measure)
- **Scripts**: GitOps infrastructure (define → version → auto-apply → observe → iterate)
- **Creative**: Design system (components → version → publish → consume → track usage)

**Detection Keywords**:
- Requirements: "automate", "CI/CD", "deploy", "monitor", "containerize", "pipeline"
- Design: "automation", "infrastructure as code", "observability", "metrics"
- Tasks: Automation, deployment, monitoring tasks

**Recommended Task Structure**:
- Phase 1: Foundation (core functionality)
- Phase 2: Automation (CI/CD, testing)
- Phase 3: Deployment (containerization, orchestration)
- Phase 4: Observability (monitoring, logging, metrics)
- Phase 5: Iteration (improvements based on metrics)

---

## Pattern Detection Algorithm

### Input Sources

The pattern detector analyzes three primary sources:

1. **Requirements Document** (`ouroboros/specs/{feature}/requirements.md`)
   - Extract keywords and phrases
   - Identify requirement categories
   - Analyze acceptance criteria patterns

2. **Design Document** (`ouroboros/specs/{feature}/design.md`)
   - Extract architectural components
   - Identify workflow structures
   - Analyze design patterns mentioned

3. **Tasks Document** (`ouroboros/specs/{feature}/tasks.md`)
   - Analyze task dependencies (sequential vs. parallel)
   - Identify phase structure
   - Extract task categorization

### Detection Process

```xml
<pattern-detection>
  <step-1-extract-characteristics>
    <!-- Scan all three documents for pattern indicators -->
    <keywords>
      - "sequential", "pipeline", "stages" → Structured Sequential
      - "iterative", "refine", "feedback" → Creative Iterative
      - "CRUD", "manage", "store" → Resource Management
      - "research", "explore", "investigate" → Exploratory Research
      - "automate", "CI/CD", "deploy" → Modern Dev Workflow
    </keywords>

    <task-structure>
      - Sequential dependencies → Structured Sequential
      - Parallel with convergence → Creative Iterative
      - Grouped by resource type → Resource Management
      - Breadth-first then depth → Exploratory Research
      - Automation tracks → Modern Dev Workflow
    </task-structure>

    <component-types>
      - Pipeline stages → Structured Sequential
      - Draft/review cycles → Creative Iterative
      - CRUD endpoints → Resource Management
      - Analysis tools → Exploratory Research
      - CI/CD components → Modern Dev Workflow
    </component-types>
  </step-1-extract-characteristics>

  <step-2-score-patterns>
    <!-- Calculate match score for each pattern (0.0 - 1.0) -->
    <scoring>
      For each pattern:
        score = (matched_indicators / total_indicators) * confidence_weight

      Confidence weight factors:
      - Keyword frequency: +0.2 per strong match
      - Structural alignment: +0.3 if task structure matches
      - Component types: +0.2 if components match pattern
      - Cross-document consistency: +0.3 if all docs agree
    </scoring>
  </step-2-score-patterns>

  <step-3-select-patterns>
    <!-- Select primary pattern (highest score) -->
    <primary-pattern>
      pattern_with_highest_score (must be >= 0.5 to be confident)
    </primary-pattern>

    <!-- Select secondary patterns (score > 0.4) -->
    <secondary-patterns>
      all_patterns_with_score_above_0.4 (excluding primary)
    </secondary-patterns>
  </step-3-select-patterns>

  <step-4-generate-recommendations>
    <!-- Based on detected patterns, recommend task structure -->
    <recommendations>
      - Suggested phase structure
      - Task parallelization opportunities
      - Validation checkpoints
      - Iteration cycles (if applicable)
      - Automation priorities (if applicable)
    </recommendations>
  </step-4-generate-recommendations>
</pattern-detection>
```

### Output Format

```json
{
  "detection_result": {
    "primary_pattern": {
      "name": "structured-sequential",
      "confidence": 0.85,
      "matched_indicators": ["clear_stages", "sequential_dependencies", "validation_gates"],
      "evidence": {
        "requirements": ["Keywords: 'pipeline', 'stages', 'validate'"],
        "design": ["5 sequential stages with validation gates"],
        "tasks": ["Tasks numbered 1-5 with sequential dependencies"]
      }
    },
    "secondary_patterns": [
      {
        "name": "resource-management",
        "confidence": 0.45,
        "matched_indicators": ["crud_operations", "validation_rules"]
      }
    ],
    "recommendations": {
      "phase_structure": "5 phases, one per pipeline stage",
      "parallelization": "Parallelize substeps within each stage",
      "checkpoints": "Add validation checkpoint after each stage",
      "estimated_phases": 5
    }
  }
}
```

---

## Pattern Learning System

### Learning from Completed Projects

After a spec execution completes successfully, the pattern recognizer extracts insights to improve future pattern detection and recommendations.

### Learning Process

```xml
<pattern-learning>
  <step-1-extract-execution-data>
    <!-- Collect data from completed execution -->
    <data-sources>
      - Pattern detection result (what pattern was detected)
      - Phase consolidation reports (what actually happened)
      - Task summaries (discoveries, challenges, metrics)
      - Final metrics (actual vs. estimated time/context)
    </data-sources>
  </step-1-extract-execution-data>

  <step-2-validate-pattern-match>
    <!-- Did the detected pattern match reality? -->
    <validation>
      - Compare estimated phase count vs. actual
      - Check if recommended task structure worked well
      - Verify parallelization opportunities were valid
      - Assess whether validation checkpoints were needed
    </validation>

    <accuracy-score>
      pattern_match_accuracy = (predictions_correct / total_predictions)
    </accuracy-score>
  </step-2-validate-pattern-match>

  <step-3-extract-insights>
    <!-- What did we learn? -->
    <insights>
      - Pattern variations discovered
      - Unexpected characteristics found
      - Task structure adjustments that worked well
      - Estimation accuracy deltas
    </insights>
  </step-3-extract-insights>

  <step-4-update-pattern-library>
    <!-- Save learned insights -->
    <save-to>
      ouroboros/patterns/{pattern-name}-learned.json
    </save-to>

    <learned-data>
      - Pattern variations and sub-patterns
      - Context multipliers (e.g., +30% for auth-heavy projects)
      - Common task additions discovered during execution
      - Successful task structures for this pattern
    </learned-data>
  </step-4-update-pattern-library>

  <step-5-update-estimation-models>
    <!-- Improve future estimations -->
    <estimation-improvements>
      - Adjust context estimates based on actual usage
      - Refine time estimates for pattern-specific tasks
      - Update phase count recommendations
      - Improve parallelization suggestions
    </estimation-improvements>
  </step-5-update-estimation-models>
</pattern-learning>
```

### Learned Pattern File Structure

```json
{
  "pattern": "resource-management",
  "base_characteristics": {
    "crud_operations": true,
    "state_persistence": true,
    "validation_rules": true,
    "access_patterns": true
  },
  "learned_variations": [
    {
      "variation_name": "resource-management-with-auth",
      "triggers": ["authentication", "authorization", "permissions"],
      "additional_tasks_needed": [
        "Password hashing validation",
        "Token generation/refresh",
        "Session management",
        "Security audit"
      ],
      "context_multiplier": 1.3,
      "time_multiplier": 1.2,
      "learned_from": ["user-authentication", "customer-portal-api"],
      "confidence": 0.92
    },
    {
      "variation_name": "resource-management-with-versioning",
      "triggers": ["version", "history", "audit trail"],
      "additional_tasks_needed": [
        "Version tracking implementation",
        "History storage",
        "Rollback capability"
      ],
      "context_multiplier": 1.15,
      "time_multiplier": 1.1,
      "learned_from": ["document-management", "config-system"],
      "confidence": 0.87
    }
  ],
  "estimation_refinements": {
    "error_handling_context": "+2000 tokens (learned from 15 projects)",
    "security_tasks_time": "+30% (learned from 8 auth-heavy projects)",
    "validation_complexity": "1.2x for each resource type"
  },
  "successful_task_structures": [
    {
      "structure": "infrastructure → create → read → update → delete → permissions",
      "success_rate": 0.94,
      "used_in": 23
    }
  ]
}
```

---

## Cross-Domain Examples

### Example 1: Vacation Planning (Creative Iterative)

**Pattern Detection**:
```json
{
  "primary_pattern": "creative-iterative",
  "confidence": 0.88,
  "evidence": {
    "requirements": [
      "Keywords: 'research', 'refine', 'alternatives', 'adjust'",
      "Multiple stakeholders providing feedback",
      "Subjective criteria: 'family-friendly', 'budget-conscious'"
    ],
    "design": [
      "Iterative refinement of itinerary",
      "Multiple options for activities",
      "Feedback loops with family members"
    ],
    "tasks": [
      "Task 1: Initial research (parallel exploration)",
      "Task 2: Draft itinerary",
      "Task 3: Refine based on feedback",
      "Task 4: Final adjustments"
    ]
  },
  "recommendations": {
    "phase_structure": "Research → Draft → Refine → Finalize",
    "parallelization": "Research multiple cities in parallel",
    "iteration_cycles": "2-3 refinement cycles expected"
  }
}
```

### Example 2: PowerShell Deployment Script (Modern Dev Workflow)

**Pattern Detection**:
```json
{
  "primary_pattern": "modern-dev-workflow",
  "confidence": 0.92,
  "evidence": {
    "requirements": [
      "Keywords: 'automate', 'idempotent', 'rollback', 'metrics'",
      "Version controlled (Git)",
      "CI/CD integration (Jenkins)",
      "Monitoring and alerting"
    ],
    "design": [
      "Infrastructure as code approach",
      "Automated deployment pipeline",
      "Built-in observability"
    ],
    "tasks": [
      "Task 1: Core deployment logic",
      "Task 2: Idempotency and rollback",
      "Task 3: Jenkins integration",
      "Task 4: Monitoring and alerts"
    ]
  },
  "recommendations": {
    "phase_structure": "Foundation → Automation → Deployment → Observability",
    "parallelization": "Automation and monitoring can run in parallel",
    "automation_priorities": "Focus on idempotency and rollback first"
  }
}
```

### Example 3: API Documentation (Structured Sequential)

**Pattern Detection**:
```json
{
  "primary_pattern": "structured-sequential",
  "confidence": 0.79,
  "secondary_patterns": ["resource-management"],
  "evidence": {
    "requirements": [
      "Keywords: 'outline', 'draft', 'review', 'publish'",
      "Clear stages with dependencies",
      "Validation at each stage"
    ],
    "design": [
      "Sequential workflow: outline → content → review → publish",
      "Each stage depends on previous completion"
    ],
    "tasks": [
      "Task 1: Create documentation outline",
      "Task 2: Write endpoint documentation",
      "Task 3: Add examples and error codes",
      "Task 4: Technical review",
      "Task 5: Publish to docs site"
    ]
  },
  "recommendations": {
    "phase_structure": "Outline → Content → Review → Publish",
    "parallelization": "Write documentation for different endpoints in parallel",
    "checkpoints": "Review checkpoint before publishing"
  }
}
```

---

## Usage Guide

### When to Run Pattern Detection

1. **After Requirements Completion**: Initial pattern detection to guide design
2. **After Design Completion**: Refined pattern detection to guide task planning
3. **After Task Planning**: Final validation that tasks match detected pattern

### How to Use Pattern Detection Results

**During Design Phase**:
- Use detected pattern to structure design document
- Apply pattern-specific design templates
- Include pattern-appropriate validation checkpoints

**During Task Planning**:
- Structure tasks according to pattern recommendations
- Apply pattern-specific parallelization strategies
- Estimate context/time using pattern-specific multipliers
- Add pattern-appropriate validation and iteration tasks

**During Execution**:
- Track whether pattern predictions held true
- Note variations and unexpected characteristics
- Collect data for pattern learning

**After Execution**:
- Run pattern learning to extract insights
- Update pattern library with learned variations
- Improve estimation models for next execution

---

## Integration with Ouroboros Framework

The Pattern Recognizer integrates with other Ouroboros components:

1. **Requirement Elicitation**: Uses detected pattern to ask pattern-specific questions
2. **Task Planning**: Uses pattern recommendations to structure tasks and phases
3. **SKILLS Generation**: Includes detected pattern in project-specific skill
4. **Quality Analysis**: Uses pattern-specific quality criteria
5. **Adaptive Task System**: Pattern learning informs task update recommendations
6. **Estimation**: Pattern-specific multipliers improve context/time estimates

---

## Future Enhancements

- **Pattern Combination Detection**: Detect when multiple patterns apply simultaneously
- **User-Defined Patterns**: Allow users to define custom patterns for their domain
- **Pattern Confidence Thresholds**: Configurable thresholds for pattern selection
- **Visual Pattern Visualization**: Diagrams showing pattern structure and flow
- **Pattern Migration**: Detect when a project shifts from one pattern to another

---

**Generated by Ouroboros Framework**
**Version**: 1.0
**Last Updated**: 2025-10-25
