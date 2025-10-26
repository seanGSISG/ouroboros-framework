# Requirements - Dynamic Template Generation

**Pattern**: Modern Development Workflow (Exploratory Research)

**Origin**: DISC-001 from ouroboros-meta-test

---

## Project Overview

**What are we fixing?**
The current Ouroboros pattern templates contain hardcoded, tech-specific content (Docker, CI/CD, Kubernetes) that violates the framework's core principle of being "tech-stack and project agnostic." This creates negative UX where templates provide confusing noise rather than helpful structure.

**Why this matters?**
- Templates currently require 95% manual rewriting
- Defeats the purpose of having templates
- Violates core Ouroboros philosophy
- Poor experience for non-technical users (planners, writers, creatives)

**Target outcome**:
Dynamic, context-aware template generation that produces 80% customized specs based on user's actual project, not generic tech jargon.

---

## Requirements (EARS Format)

### 1. Template Content Analysis

**1.1** WHEN analyzing current templates, the system SHALL identify tech-specific content
  - AC 1.1.1: Flag Docker, Kubernetes, CI/CD, GitHub Actions references
  - AC 1.1.2: Flag any technology-specific terminology
  - AC 1.1.3: Identify pattern-agnostic vs pattern-specific content
  - AC 1.1.4: Document violations of tech-agnostic principle

**1.2** WHERE templates exist, the system SHALL categorize content type
  - AC 1.2.1: Structural content (phase names, task format)
  - AC 1.2.2: Pattern-specific content (sequential vs parallel)
  - AC 1.2.3: Domain-specific content (code vs docs vs planning)
  - AC 1.2.4: Tech-specific content (Docker, K8s, etc.)

### 2. Dynamic Generation System

**2.1** WHEN user creates new spec, the system SHALL gather context
  - AC 2.1.1: Ask project domain (code, docs, planning, creative, scripts)
  - AC 2.1.2: Ask pattern-specific questions (not "CRUD" - use plain language)
  - AC 2.1.3: Ask about project scope and constraints
  - AC 2.1.4: Store answers for template customization

**2.2** IF pattern is selected, the system SHALL generate contextual tasks
  - AC 2.2.1: Use LLM to create tasks based on pattern + domain + user answers
  - AC 2.2.2: Tasks reference user's actual project, not generic tech
  - AC 2.2.3: Maintain pattern structure (phases, parallelization)
  - AC 2.2.4: Include realistic context estimates and durations

**2.3** WHERE placeholders exist, the system SHALL use specific project terms
  - AC 2.3.1: Replace `[Project Name]` with actual feature name
  - AC 2.3.2: Replace `[Component X]` with user's actual components
  - AC 2.3.3: Replace tech examples with domain-appropriate examples
  - AC 2.3.4: Preserve EARS format and pattern conventions

### 3. User Experience Improvements

**3.1** WHEN asking clarifying questions, the system SHALL use plain language
  - AC 3.1.1: Never use jargon without explanation
  - AC 3.1.2: Provide examples for each option
  - AC 3.1.3: Explain trade-offs when relevant
  - AC 3.1.4: Allow "I don't know" / "Help me decide" option

**3.2** IF user is non-technical, the system SHALL adapt language
  - AC 3.2.1: Detect domain (planning, creative) and adjust terminology
  - AC 3.2.2: Use domain-appropriate analogies
  - AC 3.2.3: Avoid software development jargon for non-code projects
  - AC 3.2.4: Provide context-sensitive help text

**3.3** WHERE template content is generated, the system SHALL be relevant
  - AC 3.3.1: 80%+ of generated content is project-specific
  - AC 3.3.2: No generic tech examples (Docker, K8s) unless user's domain is DevOps
  - AC 3.3.3: Tasks reference user's actual work, not boilerplate
  - AC 3.3.4: User can proceed with minimal editing

### 4. Backward Compatibility

**4.1** WHEN migrating to dynamic generation, the system SHALL preserve existing specs
  - AC 4.1.1: Existing specs continue to work unchanged
  - AC 4.1.2: Manual template editing still supported
  - AC 4.1.3: Static templates available as fallback
  - AC 4.1.4: Migration guide provided

**4.2** IF user prefers static templates, the system SHALL allow opt-out
  - AC 4.2.1: Flag to skip dynamic generation
  - AC 4.2.2: Direct copy of minimal placeholder templates
  - AC 4.2.3: Clear documentation of both approaches
  - AC 4.2.4: Recommendation toward dynamic for better UX

### 5. Quality & Validation

**5.1** WHEN templates are generated, the system SHALL validate quality
  - AC 5.1.1: Check for tech-specific jargon in non-code projects
  - AC 5.1.2: Verify pattern structure maintained
  - AC 5.1.3: Ensure EARS format compliance
  - AC 5.1.4: Validate parallelization logic

**5.2** WHERE generated content is saved, the system SHALL document provenance
  - AC 5.2.1: Mark files as "Generated via dynamic template"
  - AC 5.2.2: Include generation timestamp
  - AC 5.2.3: Store user answers that informed generation
  - AC 5.2.4: Allow regeneration with different answers

---

## Success Criteria

- [ ] Zero tech-specific jargon in non-code project templates
- [ ] 80%+ of generated content is immediately useful
- [ ] User editing time reduced by 70%+
- [ ] Non-technical users can create specs without confusion
- [ ] All 5 patterns work across all domains (code, docs, planning, creative, scripts)
- [ ] Meta-test can complete without manual template rewriting

---

## Out of Scope (Phase 1)

- AI-powered task estimation (use pattern defaults for now)
- Multi-language template support
- Template marketplace or sharing
- Visual template builders

---

**Created**: 2025-10-26
**Priority**: CRITICAL (blocks meta-test completion)
**Estimated Effort**: 3-5 hours implementation
