# Design - [Project Name]

**Pattern**: Structured Sequential Workflow

**Design Philosophy**: Clear stages with well-defined transitions, validation gates, and rollback capability.

---

## Architecture Overview

**High-Level Approach**:
[Describe the overall architectural approach for your sequential workflow]

**Why This Approach?**:
[Explain why this sequential structure is appropriate for this project]

**Alternatives Considered**:
1. [Alternative 1] - Rejected because [reason]
2. [Alternative 2] - Rejected because [reason]

---

## Sequential Stage Design

### Stage 1: [First Stage Name]

**Purpose**: [What this stage accomplishes]

**Inputs**:
- [Input 1]: [Description, format, source]
- [Input 2]: [Description, format, source]

**Processing**:
1. [Step 1]: [Description]
2. [Step 2]: [Description]
3. [Step 3]: [Description]

**Outputs**:
- [Output 1]: [Description, format, destination]
- [Output 2]: [Description, format, destination]

**Validation Gates**:
- ✅ [Validation 1]: [Pass criteria]
- ✅ [Validation 2]: [Pass criteria]
- ✅ [Validation 3]: [Pass criteria]

**On Failure**:
- [Error handling approach]
- [Rollback procedure]
- [User notification]

**Success Criteria**:
- [ ] [Criterion 1]
- [ ] [Criterion 2]
- [ ] [Criterion 3]

---

### Stage 2: [Second Stage Name]

**Purpose**: [What this stage accomplishes]

**Inputs** (from Stage 1):
- [Output from previous stage]
- [Additional inputs if needed]

**Processing**:
1. [Step 1]: [Description]
2. [Step 2]: [Description]
3. [Step 3]: [Description]

**Outputs**:
- [Output 1]: [Description, format, destination]
- [Output 2]: [Description, format, destination]

**Validation Gates**:
- ✅ [Validation 1]: [Pass criteria]
- ✅ [Validation 2]: [Pass criteria]

**On Failure**:
- [Error handling approach]
- [Rollback procedure to Stage 1]

**Success Criteria**:
- [ ] [Criterion 1]
- [ ] [Criterion 2]

---

### Stage 3: [Third Stage Name]

**Purpose**: [What this stage accomplishes]

**Inputs** (from Stage 2):
- [Output from previous stage]
- [Additional inputs if needed]

**Processing**:
1. [Step 1]: [Description]
2. [Step 2]: [Description]
3. [Step 3]: [Description]

**Outputs**:
- [Final output 1]: [Description, format, destination]
- [Final output 2]: [Description, format, destination]

**Validation Gates**:
- ✅ [Validation 1]: [Pass criteria]
- ✅ [Validation 2]: [Pass criteria]

**On Failure**:
- [Error handling approach]
- [Rollback procedure]

**Success Criteria**:
- [ ] [Criterion 1]
- [ ] [Criterion 2]

---

## Data Flow

```
[Stage 1: Input]
    ↓
[Validation Gate 1]
    ↓
[Stage 2: Processing]
    ↓
[Validation Gate 2]
    ↓
[Stage 3: Output]
    ↓
[Final Validation]
    ↓
[Complete]

(Rollback path: Any stage can return to previous stage on failure)
```

---

## Validation Strategy

### Pre-Stage Validation

**What to validate before each stage starts**:
- [Validation 1]: [Description, how to check]
- [Validation 2]: [Description, how to check]
- [Validation 3]: [Description, how to check]

### Post-Stage Validation

**What to validate after each stage completes**:
- [Validation 1]: [Description, how to check]
- [Validation 2]: [Description, how to check]

### Final Validation

**What to validate before marking entire workflow complete**:
- [Validation 1]: [Description, how to check]
- [Validation 2]: [Description, how to check]

---

## Rollback & Recovery

### Rollback Design

**When rollback is needed**:
- [Scenario 1]: [Trigger]
- [Scenario 2]: [Trigger]
- [Scenario 3]: [Trigger]

**Rollback procedure by stage**:

**From Stage 3 → Stage 2**:
1. [Step 1]: [Action]
2. [Step 2]: [Action]
3. [Step 3]: [Action]

**From Stage 2 → Stage 1**:
1. [Step 1]: [Action]
2. [Step 2]: [Action]

**From Stage 1 → Clean state**:
1. [Step 1]: [Action]
2. [Step 2]: [Action]

### State Preservation

**What state to preserve for rollback**:
- [State 1]: [Storage location, retention period]
- [State 2]: [Storage location, retention period]

---

## Error Handling Strategy

### Error Categories

**Category 1: Validation Errors**
- **Detection**: [How to detect]
- **Handling**: [What to do]
- **User Impact**: [What user experiences]
- **Recovery**: [How to recover]

**Category 2: Processing Errors**
- **Detection**: [How to detect]
- **Handling**: [What to do]
- **User Impact**: [What user experiences]
- **Recovery**: [How to recover]

**Category 3: System Errors**
- **Detection**: [How to detect]
- **Handling**: [What to do]
- **User Impact**: [What user experiences]
- **Recovery**: [How to recover]

### Error Logging

**What to log**:
- [Log item 1]: [Format, destination]
- [Log item 2]: [Format, destination]

**Log retention**: [Retention policy]

---

## Component Structure

### Component 1: [Component Name]

**Responsibility**: [What this component does]

**Stage**: [Which stage(s) this component belongs to]

**Interfaces**:
- Input: [Interface definition]
- Output: [Interface definition]

**Dependencies**:
- [Dependency 1]: [Why needed]
- [Dependency 2]: [Why needed]

**Error Handling**:
- [Error type 1]: [Handling approach]
- [Error type 2]: [Handling approach]

---

### Component 2: [Component Name]

**Responsibility**: [What this component does]

**Stage**: [Which stage(s) this component belongs to]

**Interfaces**:
- Input: [Interface definition]
- Output: [Interface definition]

**Dependencies**:
- [Dependency 1]: [Why needed]
- [Dependency 2]: [Why needed]

---

## Cross-Domain Examples

### Example 1: Code - Data Pipeline Design

**Stages**:
1. **Ingest**: Raw data → Queued data (validation: format check)
2. **Validate**: Queued data → Validated data (validation: schema compliance)
3. **Transform**: Validated data → Transformed data (validation: output schema)
4. **Load**: Transformed data → Database (validation: atomic transaction)
5. **Verify**: Database → Confirmation (validation: data integrity)

**Rollback**: Each stage can rollback to previous. Load stage uses database transactions.

**Error Handling**:
- Format errors → Log and skip file, alert admin
- Schema errors → Log invalid records, continue with valid
- Transaction errors → Full rollback, retry with exponential backoff

---

### Example 2: Documentation - User Guide Design

**Stages**:
1. **Outline**: Research → Structured outline (validation: stakeholder approval)
2. **Draft**: Outline → Content draft (validation: completeness check)
3. **Review**: Draft → Reviewed content (validation: SME sign-off)
4. **Revise**: Reviewed content → Final content (validation: editorial check)
5. **Publish**: Final content → Live docs (validation: link/image check)

**Rollback**: Can return to previous drafts. Git-based version control.

**Error Handling**:
- Incomplete sections → Flag for author, block progression
- Broken links → Auto-detect, alert before publish
- Failed publish → Rollback to previous live version

---

### Example 3: Planning - Event Organization Design

**Stages**:
1. **Venue**: Requirements → Booked venue (validation: contract signed)
2. **Catering**: Venue capacity → Catering contract (validation: menu approved)
3. **Invitations**: Guest list → Sent invitations (validation: all sent)
4. **Registration**: Invitations → RSVP tracking (validation: deadline passed)
5. **Execution**: Plan → Completed event (validation: post-event survey)

**Rollback**:
- Before venue booking: Full cancellation possible
- After venue booking: Financial penalties may apply
- After catering: Minimize waste through guest count adjustments

**Error Handling**:
- Venue unavailable → Secondary venue list ready
- Catering issue → Backup caterer on standby
- Low RSVP → Marketing push, extended deadline

---

### Example 4: Scripts - Deployment Design

**Stages**:
1. **Pre-flight**: Environment → Ready state (validation: all checks pass)
2. **Backup**: Current state → Backup created (validation: backup verified)
3. **Deploy**: New version → Running (validation: health checks pass)
4. **Smoke Test**: Running → Validated (validation: critical paths work)
5. **Monitor**: Validated → Production (validation: metrics stable)

**Rollback**: Automated rollback if any validation fails. One-command rollback to backup.

**Error Handling**:
- Pre-flight fails → Block deployment, alert operator
- Health check fails → Auto-rollback, incident logged
- Smoke test fails → Auto-rollback, detailed logs captured

---

## Technology Choices

**Choice 1: [Technology/Tool/Approach]**
- **Why chosen**: [Rationale]
- **Alternatives**: [What else was considered]
- **Trade-offs**: [What we gain/lose]

**Choice 2: [Technology/Tool/Approach]**
- **Why chosen**: [Rationale]
- **Alternatives**: [What else was considered]
- **Trade-offs**: [What we gain/lose]

---

## Key Decisions

### Decision 1: [Decision Title]

**Context**: [What led to this decision]

**Decision**: [What was decided]

**Rationale**: [Why this was the right choice]

**Implications**: [What this means for implementation]

---

### Decision 2: [Decision Title]

**Context**: [What led to this decision]

**Decision**: [What was decided]

**Rationale**: [Why this was the right choice]

**Implications**: [What this means for implementation]

---

## Non-Functional Design

### Performance Design

**Target metrics**:
- [Metric 1]: [Target value]
- [Metric 2]: [Target value]

**Optimization strategy**:
- [Strategy 1]: [How to achieve]
- [Strategy 2]: [How to achieve]

### Reliability Design

**Failure modes**:
- [Failure 1]: [Detection & recovery]
- [Failure 2]: [Detection & recovery]

**Redundancy**:
- [Component 1]: [Redundancy approach]
- [Component 2]: [Redundancy approach]

### Security Design

**Threat model**:
- [Threat 1]: [Mitigation]
- [Threat 2]: [Mitigation]

**Security controls**:
- [Control 1]: [Implementation]
- [Control 2]: [Implementation]

---

## Testing Strategy

**Unit Testing**:
- [What to test]: [Coverage target]

**Integration Testing**:
- [What to test]: [Coverage target]

**End-to-End Testing**:
- [Scenario 1]: [Expected outcome]
- [Scenario 2]: [Expected outcome]

**Rollback Testing**:
- [Test 1]: [Validation]
- [Test 2]: [Validation]

---

## Observability & Monitoring

**Metrics to track**:
- [Metric 1]: [Why important, threshold]
- [Metric 2]: [Why important, threshold]

**Logs to capture**:
- [Log 1]: [Format, destination]
- [Log 2]: [Format, destination]

**Alerts to configure**:
- [Alert 1]: [Condition, severity, action]
- [Alert 2]: [Condition, severity, action]

---

**Generated from Ouroboros Pattern**: Structured Sequential Workflow
**Template Version**: 1.0
**Last Updated**: 2025-10-25

---

## Customization Checklist

Before using this template, customize:
- [ ] Replace [Project Name] with actual project name
- [ ] Define all stages with clear boundaries
- [ ] Specify inputs/outputs for each stage
- [ ] Document validation gates and pass criteria
- [ ] Design rollback procedures for each stage
- [ ] Define error handling strategy
- [ ] Choose appropriate technologies/tools
- [ ] Document key architectural decisions
- [ ] Add domain-specific design elements
- [ ] Review cross-domain examples for patterns
