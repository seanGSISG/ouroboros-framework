# Requirements - [Project Name]

**Pattern**: Structured Sequential Workflow

**Pattern Characteristics**:
- Clear step-by-step progression
- Each step depends on previous completion
- Well-defined inputs and outputs
- Validation at each stage
- Rollback capability

---

## Project Overview

**What are we building/creating/planning?**
[Brief description of the project - works for code, documentation, planning, scripts, creative work, etc.]

**What problem does this solve?**
[Problem statement]

**Who will use/benefit from this?**
[Target users or stakeholders]

---

## Requirements (EARS Format)

> **EARS Keywords**:
> - **WHEN** = Event-driven (user clicks button, file uploads, schedule triggers)
> - **IF** = Conditional logic (if user has permission, if file exists)
> - **WHERE** = Location/scope (where data is stored, where UI appears)
> - **WHILE** = Ongoing state (while processing, while user is logged in)

### 1. Stage 1: [First Stage Name]

**1.1** WHEN [trigger event], the system SHALL [capability]
  - AC 1.1.1: [Acceptance criterion - testable, measurable]
  - AC 1.1.2: [Acceptance criterion]
  - AC 1.1.3: [Acceptance criterion]

**1.2** IF [condition], the system SHALL [capability]
  - AC 1.2.1: [Acceptance criterion]
  - AC 1.2.2: [Acceptance criterion]

**1.3** WHERE [location/scope], the system SHALL [capability]
  - AC 1.3.1: [Acceptance criterion]
  - AC 1.3.2: [Acceptance criterion]

### 2. Stage 2: [Second Stage Name]

**2.1** WHEN [trigger event], the system SHALL [capability]
  - AC 2.1.1: [Acceptance criterion]
  - AC 2.1.2: [Acceptance criterion]
  - AC 2.1.3: [Acceptance criterion]

**2.2** IF [condition], the system SHALL [capability]
  - AC 2.2.1: [Acceptance criterion]
  - AC 2.2.2: [Acceptance criterion]

### 3. Stage 3: [Third Stage Name]

**3.1** WHEN [trigger event], the system SHALL [capability]
  - AC 3.1.1: [Acceptance criterion]
  - AC 3.1.2: [Acceptance criterion]

**3.2** IF [condition], the system SHALL [capability]
  - AC 3.2.1: [Acceptance criterion]
  - AC 3.2.2: [Acceptance criterion]

### 4. Validation & Error Handling

**4.1** WHEN validation fails at any stage, the system SHALL [error handling behavior]
  - AC 4.1.1: [Clear error messages]
  - AC 4.1.2: [Graceful degradation]
  - AC 4.1.3: [User guidance for resolution]

**4.2** IF rollback is required, the system SHALL [rollback capability]
  - AC 4.2.1: [Can return to previous stage]
  - AC 4.2.2: [State is preserved]
  - AC 4.2.3: [No data loss]

### 5. Quality Gates & Checkpoints

**5.1** WHERE validation checkpoints exist, the system SHALL [validation behavior]
  - AC 5.1.1: [Validation runs before proceeding]
  - AC 5.1.2: [Clear pass/fail criteria]
  - AC 5.1.3: [Documentation of validation results]

**5.2** WHEN a stage completes, the system SHALL [completion behavior]
  - AC 5.2.1: [Confirmation of completion]
  - AC 5.2.2: [Output artifacts documented]
  - AC 5.2.3: [Ready for next stage]

---

## Cross-Domain Examples

### Example 1: Code - Data Pipeline

**Stage 1: Data Ingestion**
- **1.1** WHEN raw data arrives, the system SHALL ingest and queue it
  - AC: Supports CSV, JSON, XML formats
  - AC: Max file size 500MB
  - AC: Invalid formats logged and rejected

**Stage 2: Data Validation**
- **2.1** WHEN data is queued, the system SHALL validate against schema
  - AC: All required fields present
  - AC: Data types match schema
  - AC: Validation errors logged with line numbers

**Stage 3: Data Transformation**
- **3.1** WHEN data passes validation, the system SHALL transform to target schema
  - AC: Handles missing optional fields gracefully
  - AC: Applies transformation rules correctly
  - AC: Outputs valid target format

**Stage 4: Data Loading**
- **4.1** WHEN transformation completes, the system SHALL load to destination
  - AC: Atomic transactions (all or nothing)
  - AC: Rollback on failure
  - AC: Success confirmation logged

### Example 2: Documentation - User Guide Creation

**Stage 1: Outline Creation**
- **1.1** WHEN outline is needed, the system SHALL create structured outline
  - AC: Covers all major features
  - AC: Logical flow for target audience
  - AC: Reviewable by stakeholders

**Stage 2: Content Drafting**
- **2.1** WHEN outline approved, the system SHALL draft content for each section
  - AC: Each section complete and coherent
  - AC: Screenshots and examples included
  - AC: Technical accuracy verified

**Stage 3: Review & Revision**
- **3.1** WHEN draft complete, the system SHALL conduct review
  - AC: Technical review by SMEs
  - AC: Editorial review for clarity
  - AC: All feedback documented

**Stage 4: Publishing**
- **4.1** WHEN revisions complete, the system SHALL publish to docs site
  - AC: All links functional
  - AC: Images render correctly
  - AC: Search indexing updated

### Example 3: Planning - Event Organization

**Stage 1: Venue Selection**
- **1.1** WHEN event date confirmed, the system SHALL identify venue options
  - AC: Capacity meets attendee estimate
  - AC: Within budget constraints
  - AC: Available on event date

**Stage 2: Catering Arrangement**
- **2.1** WHEN venue booked, the system SHALL arrange catering
  - AC: Dietary restrictions accommodated
  - AC: Serving time coordinated with schedule
  - AC: Budget allocation respected

**Stage 3: Invitations & Registration**
- **3.1** WHEN catering confirmed, the system SHALL send invitations
  - AC: All stakeholders invited
  - AC: RSVP mechanism functional
  - AC: Confirmation emails automated

**Stage 4: Day-of Execution**
- **4.1** WHEN event day arrives, the system SHALL execute event plan
  - AC: All vendors confirmed
  - AC: Setup timeline followed
  - AC: Contingency plans ready

### Example 4: Scripts - Deployment Automation

**Stage 1: Pre-Deployment Checks**
- **1.1** WHEN deployment initiated, the system SHALL run pre-flight checks
  - AC: Environment variables validated
  - AC: Dependencies available
  - AC: Backup created

**Stage 2: Deployment Execution**
- **2.1** WHEN checks pass, the system SHALL deploy application
  - AC: Zero-downtime deployment
  - AC: Health checks at each step
  - AC: Progress logged

**Stage 3: Post-Deployment Validation**
- **3.1** WHEN deployment completes, the system SHALL validate deployment
  - AC: All services responding
  - AC: Smoke tests pass
  - AC: Metrics baseline established

**Stage 4: Rollback Ready**
- **4.1** IF validation fails, the system SHALL rollback automatically
  - AC: Previous version restored
  - AC: Rollback time < 5 minutes
  - AC: Incident logged

---

## Success Criteria

**The project is successful when**:
- [ ] All stages complete in defined sequence
- [ ] Validation gates pass at each stage
- [ ] Rollback capability tested and functional
- [ ] Error handling graceful and informative
- [ ] Output artifacts meet quality standards
- [ ] Documentation complete and accurate

---

## Constraints & Dependencies

**Constraints**:
- [Budget, time, resources, technology, compliance]

**Dependencies**:
- [External systems, third-party services, prerequisite projects]

**Assumptions**:
- [What we're assuming is true]

---

## Non-Functional Requirements

**Performance**:
- [Speed, throughput, latency requirements]

**Reliability**:
- [Uptime, error rates, recovery time]

**Security**:
- [Authentication, authorization, data protection]

**Maintainability**:
- [Documentation, code quality, extensibility]

**Usability**:
- [User experience, accessibility, learnability]

---

**Generated from Ouroboros Pattern**: Structured Sequential Workflow
**Template Version**: 1.0
**Last Updated**: 2025-10-25

---

## Customization Checklist

Before using this template, customize:
- [ ] Replace [Project Name] with actual project name
- [ ] Replace [Stage Names] with your actual stages
- [ ] Fill in all [placeholder] sections
- [ ] Add/remove stages as needed for your specific workflow
- [ ] Adapt acceptance criteria to your domain
- [ ] Review cross-domain examples for inspiration
- [ ] Ensure all validation gates are defined
- [ ] Document rollback procedures
- [ ] Add domain-specific requirements as needed
