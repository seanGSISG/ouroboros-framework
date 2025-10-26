# Dynamic Project-Specific SKILLS Generation

**Purpose**: Automatically generate Claude Skills that capture project-specific knowledge and context, reducing token usage by 10-25K per task while working for ANY project type.

**Location**: `ouroboros/intelligence/skills-generator.md`

---

## Overview

The SKILLS Generator is a core intelligence component of the Ouroboros framework that creates **project-specific skills** from requirements, design, and execution discoveries. These skills serve as compressed context capsules that AI assistants can reference instead of re-reading full specification documents.

**Key Benefits**:
- **Context Savings**: 10-25K tokens per task (vs. reading full requirements + design + phase reports)
- **Project Agnostic**: Works for code, documentation, planning, scripts, creative work, business processes
- **Self-Evolving**: Skills update after each phase with new discoveries and decisions
- **Universal Format**: Same skill structure works across all project types
- **Knowledge Preservation**: Captures critical context, terminology, patterns, and constraints

**The Ouroboros Connection**: Skills are the serpent's memory—distilled wisdom from past iterations that inform future tasks without repeating the same context consumption.

---

## SKILL File Structure

### Location

All project-specific skills are stored at:
```
.claude/skills/{feature-name}.md
```

**Examples**:
- `.claude/skills/vacation-planner-europe-2024.md`
- `.claude/skills/company-infrastructure-automation.md`
- `.claude/skills/customer-portal-api.md`
- `.claude/skills/marketing-campaign-q4.md`
- `.claude/skills/user-manual-redesign.md`

**Naming Convention**: Use kebab-case matching the feature name from `ouroboros/specs/{feature-name}/`

### Universal Template

```markdown
# Skill: {Feature Title}

## Project Context

**Type**: {Pattern Name} ({project domain})
**Goal**: {One-sentence project objective}
**{Domain-Specific-Label}**: {Key project metadata}
**Constraints**:
- {Critical constraint 1}
- {Critical constraint 2}
- {Critical constraint 3}

## Key Decisions Made

### {Decision Category 1}
{Description of decisions in this area}
- **{Specific Choice}**: {Why this was chosen}
- **{Another Choice}**: {Rationale}

### {Decision Category 2}
{More decisions...}

### Discoveries During {Phase/Task}
- **{Phase/Task ID} Discovery**: {What was learned}
  - **Action Taken**: {How this changed the plan}
  - **Tasks Modified**: {Which tasks were updated and how}

## Important Terminology

- **{Term 1}**: {Definition and why it matters for this project}
- **{Term 2}**: {Project-specific meaning}
- **{Term 3}**: {Context-aware explanation}

## Patterns Observed

### {Pattern Name}
{Description of recurring pattern or workflow}
1. {Step 1}
2. {Step 2}
3. {Step 3}

### {Another Pattern}
{Description...}

## {Domain-Specific Section}
<!-- Examples: API Rate Limits, Budget Allocation, Design Principles, etc. -->

## References

- `ouroboros/specs/{feature}/requirements.md` - Full requirements
- `ouroboros/specs/{feature}/design.md` - Architecture details
- `ouroboros/specs/{feature}/phases/{phase-id}/consolidated.md` - Phase discoveries

## When to Use This Skill

Use this skill when:
- Working on tasks for {feature name}
- Need context on {key aspect 1}
- Checking what has already been discovered/decided
- Understanding constraints and priorities
- Implementing tasks from phases {X}-{Y}

**Context Savings**: Using this skill saves ~{N}K tokens vs. re-reading full requirements + design + phase consolidations.

## Version History

- **v1.0** - Initial generation after requirements + design completion
- **v1.1** - Updated after Phase {X} with {discovery summary}
- **v1.2** - Updated after Phase {Y} with {discovery summary}
```

---

## Auto-Generation Process

### Trigger Points

Skills are automatically generated or updated at these points:

1. **Initial Generation** - After requirements.md + design.md are completed
2. **Phase Updates** - After each phase consolidation (phase-{id}/consolidated.md created)
3. **Major Discoveries** - When task summaries reveal significant new insights
4. **Pattern Changes** - When project pattern shifts or evolves

### Generation Workflow

```xml
<skills-generation-workflow>
  <step-1-extract-key-information>
    <!-- Read source documents -->
    <sources>
      - requirements.md → Extract goals, constraints, critical requirements
      - design.md → Extract architecture decisions, component structure, key choices
      - pattern-detection-result.json → Extract detected pattern, confidence, recommendations
      - (Optional) phases/*/consolidated.md → Extract discoveries, task changes, lessons learned
    </sources>

    <extraction-targets>
      - Project goal (1-2 sentences max)
      - Top 5-7 constraints (must-haves and must-not-haves)
      - Key architecture decisions (3-5 major choices)
      - Critical terminology (5-10 domain-specific terms)
      - Observed patterns (workflows, processes that repeat)
      - Domain-specific metadata (tech stack, budget, timeline, etc.)
    </extraction-targets>
  </step-1-extract-key-information>

  <step-2-identify-pattern-specific-structure>
    <!-- Customize skill based on detected pattern -->
    <pattern-mappings>
      <structured-sequential>
        - Emphasize stage dependencies
        - Include validation checkpoints
        - Document rollback procedures
      </structured-sequential>

      <creative-iterative>
        - Track iteration cycles
        - Document feedback sources
        - Capture refinement decisions
      </creative-iterative>

      <resource-management>
        - List resource types
        - Document CRUD patterns
        - Capture validation rules
      </resource-management>

      <exploratory-research>
        - Track hypotheses tested
        - Document findings synthesis
        - Capture scope evolution
      </exploratory-research>

      <modern-dev-workflow>
        - Document automation decisions
        - Capture deployment strategy
        - List observability choices
      </modern-dev-workflow>
    </pattern-mappings>
  </step-2-identify-pattern-specific-structure>

  <step-3-compress-and-prioritize>
    <!-- Aggressive token reduction while preserving critical context -->
    <compression-techniques>
      - Use bullet lists instead of paragraphs (40% reduction)
      - Remove fluff words ("basically", "essentially", "obviously")
      - Use abbreviations for common terms (after first definition)
      - Link to full docs instead of duplicating large blocks
      - Focus on decisions and constraints, not process
      - Omit obvious or inferable information
    </compression-techniques>

    <prioritization-rules>
      <!-- Include if ANY of these are true -->
      1. Critical constraint that affects multiple tasks
      2. Decision that surprised the designers (non-obvious)
      3. Terminology that has project-specific meaning
      4. Pattern that repeats across multiple components
      5. Discovery that changed subsequent tasks
      6. Rate limit, quota, or external dependency detail
      7. Estimation factor (multipliers, context budgets)

      <!-- Exclude if ALL of these are true -->
      1. Obvious from the domain (e.g., "React uses components")
      2. Easily re-derivable from other information
      3. Only affects one task and is in that task's description
      4. Standard practice with no project-specific variation
    </prioritization-rules>
  </step-3-compress-and-prioritize>

  <step-4-calculate-context-savings>
    <!-- Measure the benefit -->
    <calculation>
      baseline_context = size(requirements.md) + size(design.md) + size(all_phase_consolidations)
      skill_context = size({feature-name}.md)
      savings = baseline_context - skill_context
      savings_percentage = (savings / baseline_context) * 100
    </calculation>

    <typical-ranges>
      - Small projects: 8-12K tokens saved (50-70% reduction)
      - Medium projects: 15-25K tokens saved (60-75% reduction)
      - Large projects: 30-50K tokens saved (65-80% reduction)
    </typical-ranges>
  </step-4-calculate-context-savings>

  <step-5-generate-skill-file>
    <!-- Write to .claude/skills/{feature-name}.md -->
    <file-format>
      - Use universal template structure
      - Customize sections based on project pattern
      - Add domain-specific sections as needed
      - Include version history (starts at v1.0)
      - Add context savings estimate at end
    </file-format>

    <save-location>
      .claude/skills/{feature-name}.md
    </save-location>
  </step-5-generate-skill-file>
</skills-generation-workflow>
```

---

## Skill Evolution Process

Skills are **living documents** that evolve as the project progresses and new discoveries are made.

### Update Triggers

```xml
<update-triggers>
  <automatic-updates>
    <!-- These trigger skill updates automatically -->
    1. Phase consolidation completed with discoveries
    2. Task summaries reveal unexpected constraints
    3. Pattern detection confidence changes significantly
    4. Major architecture decision changed
  </automatic-updates>

  <manual-updates>
    <!-- User can request these updates -->
    1. User explicitly requests skill refresh
    2. Mid-project requirements change
    3. Tech stack or approach pivot
  </manual-updates>
</update-triggers>
```

### Update Workflow

```xml
<skill-update-workflow>
  <step-1-read-new-discoveries>
    <!-- Scan recent phase reports -->
    <sources>
      - Latest consolidated.md from most recent phase
      - All summary-*.md files from recent phase
      - Updated tasks-v{N}.md (compare with previous version)
    </sources>

    <extract>
      - New terminology introduced
      - Unexpected constraints discovered
      - Architecture decisions that changed
      - Rate limits or quotas learned
      - Patterns observed during implementation
      - Task changes made (additions, modifications, removals)
    </extract>
  </step-1-read-new-discoveries>

  <step-2-merge-with-existing-skill>
    <!-- Update existing skill without duplicating -->
    <merge-strategy>
      1. Add new discoveries to "Discoveries During {Phase}" subsections
      2. Update "Key Decisions Made" if decisions changed
      3. Add new terminology to "Important Terminology"
      4. Extend patterns if new variations observed
      5. Add domain-specific sections if new categories emerged
      6. Increment version number (v1.0 → v1.1)
      7. Add version history entry describing changes
    </merge-strategy>

    <de-duplication>
      - Don't repeat information already in skill
      - If discovery contradicts existing info, replace (not add)
      - Merge similar discoveries into single entry
      - Remove outdated information that's no longer relevant
    </de-duplication>
  </step-2-merge-with-existing-skill>

  <step-3-maintain-context-budget>
    <!-- Keep skill under 5K tokens even as it grows -->
    <budget-management>
      - Target: 3-5K tokens per skill
      - Maximum: 7K tokens (hard cap)
      - If approaching cap: consolidate, abbreviate, remove low-value details
      - Strategy: Prioritize recent discoveries over older ones
      - Focus: Keep constraints, critical decisions, non-obvious patterns
    </budget-management>
  </step-3-maintain-context-budget>

  <step-4-save-updated-skill>
    <!-- Overwrite existing skill file -->
    <save>
      Location: .claude/skills/{feature-name}.md
      Action: Overwrite (skills don't version separately, version history is internal)
      Backup: Original v1.0 is preserved in Git history if needed
    </save>
  </step-4-save-updated-skill>
</skill-update-workflow>
```

### Version History Tracking

```markdown
## Version History

- **v1.0** (2025-10-25) - Initial generation after requirements + design completion
- **v1.1** (2025-10-25) - Updated after Phase 2 with Azure CLI rate limit discoveries
- **v1.2** (2025-10-26) - Updated after Phase 3 with air-gapped network fallback pattern
- **v1.3** (2025-10-26) - Updated after Phase 4 with deployment performance optimizations
```

**Purpose**: Track what changed and when, so future agents know which version of knowledge they're working with.

---

## Cross-Domain Examples

### Example 1: Vacation Planning Skill

**Project Type**: Creative Iterative Process (Planning)

```markdown
# Skill: Europe Summer 2024 Vacation Planning

## Project Context

**Type**: Creative Iterative Process (vacation planning)
**Goal**: Plan 14-day Europe trip for family of 4 (June 2024)
**Budget**: $8,000 total
**Constraints**:
- Kids aged 8 and 12 (family-friendly activities required)
- Must include Paris and Rome
- Prefer trains over flights for city-to-city travel
- June 10-25 travel window (school schedule)

## Key Decisions Made

### Cities Selected
1. **Paris** (4 days) - Arrival city, Eiffel Tower, Louvre, Versailles day trip
2. **Swiss Alps** (3 days) - Interlaken, scenic mountain activities, family-friendly hiking
3. **Venice** (2 days) - Canals, St. Mark's Basilica, gondola rides
4. **Rome** (4 days) - Colosseum, Vatican, historical sites, gelato tours
5. **Travel days** (1 day) - Train travel between cities

### Budget Allocation
- **Flights**: $2,400 (round-trip family of 4, Discovery: early morning flights 35% cheaper)
- **Accommodation**: $2,800 ($200/night average, mix of hotels and short-term rentals)
- **Food**: $1,400 ($100/day, includes 1 nice dinner every 3 days)
- **Activities**: $1,000 (museum passes, attraction tickets, tours)
- **Transportation**: $400 (Eurail passes for intercity trains, local metro)

### Discoveries During Planning

- **Task 2.1 Discovery**: June 15-20 has "Fête de la Musique" festival in Paris (accommodations 40% more expensive, crowds 2x)
  - **Action Taken**: Shifted Paris dates to June 10-14 (before festival)
  - **Tasks Modified**: Updated booking task to prioritize early June dates

- **Task 2.3 Discovery**: Swiss Alps hotels require 3-night minimum booking in summer season
  - **Action Taken**: Extended Swiss stay from 2 to 3 nights, reduced Venice from 3 to 2 nights
  - **Tasks Modified**: Adjusted itinerary task and accommodation budget

- **Task 3.2 Discovery**: Many Rome sites (Colosseum, Vatican, Borghese Gallery) require advance booking 2-3 weeks ahead
  - **Action Taken**: Added new task 4.3 "Book Rome attractions immediately"
  - **Tasks Modified**: Created high-priority booking task, added calendar reminders

- **Task 2.4 Discovery**: Eurail Pass is more economical than individual train tickets for 4+ intercity trains (family of 4 = 16 tickets)
  - **Action Taken**: Purchased Eurail Global Pass (10 days in 2 months)
  - **Budget Impact**: Saved ~$280 vs individual tickets

## Important Terminology

- **Eurail Pass**: Unlimited train travel pass across Europe (more economical than individual tickets for 4+ trains)
- **Schengen Area**: 27 European countries with no border controls (passport check only at entry/exit)
- **Paris Museum Pass**: €180/person, covers 60+ Paris attractions (Louvre, Versailles, Arc de Triomphe, etc.)
- **City Tax**: Tourist tax charged per person per night in European cities (€2-5/night, not included in accommodation price)
- **Short-term Rental**: Airbnb/VRBO apartments (better value for families vs hotels, but less flexible cancellation)

## Patterns Observed

### Activity Planning Pattern
For each city:
1. Identify 3-5 must-see attractions (based on kids' interests + adult preferences)
2. Book time-sensitive/capacity-limited items first (Vatican, Colosseum, Versailles)
3. Leave 30% of time unscheduled for spontaneity and rest
4. Plan 1 "kid-focused" activity per day (playground, gelato, interactive museum)
5. Balance indoor/outdoor activities (backup plans for rain)

### Budget Management Pattern
- **Book flights and trains FIRST** (prices fluctuate most, limited seat availability)
- **Reserve accommodations 2-3 months out** (better selection, reasonable cancellation policies)
- **Book major attractions 1-2 weeks before** (avoid sold-out dates)
- **Keep 15% budget as buffer** (unexpected expenses, opportunity costs)
- **Track spending in shared spreadsheet** (real-time visibility for whole family)

### Family Harmony Pattern
- **Rotate activity selection** (kids choose 1 activity/day, adults choose others)
- **Build in rest time** (2-hour break mid-afternoon, especially after heavy walking mornings)
- **Set expectations early** (kids understand this is educational + fun, not just theme parks)
- **Snack strategy** (always carry snacks, prevents meltdowns from hunger)

## Budget Breakdown by City

| City       | Nights | Accommodation | Food  | Activities | Transport | Total  |
|------------|--------|---------------|-------|------------|-----------|--------|
| Paris      | 4      | $840          | $400  | $280       | $80       | $1,600 |
| Swiss Alps | 3      | $720          | $300  | $220       | $60       | $1,300 |
| Venice     | 2      | $480          | $200  | $120       | $40       | $840   |
| Rome       | 4      | $760          | $400  | $280       | $80       | $1,520 |
| Flights    | -      | -             | -     | -          | $2,400    | $2,400 |
| Trains     | -      | -             | -     | -          | $140      | $140   |
| **TOTAL**  | **13** | **$2,800**    | **$1,400** | **$900** | **$2,800** | **$7,900** |

*($100 buffer remaining)*

## References

- `ouroboros/specs/europe-vacation-2024/requirements.md` - Full vacation requirements and family preferences
- `ouroboros/specs/europe-vacation-2024/design.md` - Detailed 14-day itinerary with daily breakdown
- `ouroboros/specs/europe-vacation-2024/phases/phase-2/consolidated.md` - Booking discoveries and date optimizations
- `ouroboros/specs/europe-vacation-2024/phases/phase-3/consolidated.md` - Activity booking experiences and tips

## When to Use This Skill

Use this skill when:
- Working on remaining vacation planning tasks (booking, activity research)
- Need quick reference for budget allocations
- Checking what has already been discovered about dates, prices, constraints
- Understanding why certain cities/dates were chosen
- Implementing tasks from Phase 4 (final bookings) and Phase 5 (trip preparation)

**Context Savings**: Using this skill saves ~12K tokens vs. re-reading full requirements (4K) + design (5K) + phase consolidations (3K).

## Version History

- **v1.0** (2025-09-15) - Initial generation after requirements + design completion
- **v1.1** (2025-09-18) - Updated after Phase 2 with Paris festival discovery and date shift
- **v1.2** (2025-09-20) - Updated after Phase 3 with Swiss hotel minimum stay requirement
- **v1.3** (2025-09-22) - Updated after Phase 3 with Rome advance booking requirements and Eurail savings
```

**Key Features**:
- Budget-focused (planning project characteristic)
- Family dynamics patterns captured
- Date discoveries documented with task impacts
- Terminology specific to European travel
- 3.5K tokens vs 12K baseline (71% reduction)

---

### Example 2: PowerShell Infrastructure Automation Skill

**Project Type**: Modern Development Workflow (Scripts/Automation)

```markdown
# Skill: Company Infrastructure Automation

## Project Context

**Type**: Modern Development Workflow (infrastructure automation)
**Goal**: Automate Azure infrastructure provisioning for dev/staging/prod environments
**Tech Stack**: PowerShell 7.4, Azure CLI 2.50+, ARM templates, Azure DevOps pipelines
**Constraints**:
- Must be idempotent (safe to run multiple times without side effects)
- Must support rollback to previous state
- Must log all operations for compliance audit trail
- Must work in air-gapped network (no direct internet access)
- Must complete provisioning in <30 minutes (SLA requirement)

## Key Decisions Made

### Architecture Approach
- **Infrastructure as Code**: ARM templates define all resources (declarative, version-controlled)
- **Orchestration Layer**: PowerShell scripts sequence deployment (imperative control flow)
- **Configuration Management**: JSON files per environment (dev.json, staging.json, prod.json)
- **Secrets Handling**: Azure Key Vault for cloud environments, encrypted local JSON for air-gapped
- **Error Recovery**: Exponential backoff retry (3 attempts) + rollback on critical failures

### Script Structure
```
scripts/
├── Deploy-Infrastructure.ps1      # Main orchestrator (entry point)
├── modules/
│   ├── Network.psm1               # VNet, subnets, NSGs, route tables
│   ├── Compute.psm1               # VMs, scale sets, availability sets
│   ├── Database.psm1              # Azure SQL, Redis, storage accounts
│   ├── Monitoring.psm1            # Log Analytics, Application Insights, alerts
│   └── Common.psm1                # Shared utilities (retry logic, logging)
└── config/
    ├── dev.json                   # Dev environment config
    ├── staging.json               # Staging environment config
    └── prod.json                  # Production environment config
```

### Deployment Sequence
1. **Pre-flight Validation** (syntax check ARM templates, verify Azure CLI auth, check quotas)
2. **Network Layer** (VNet, subnets, NSGs - foundation for all other resources)
3. **Storage Layer** (storage accounts, blobs - needed by VMs and databases)
4. **Compute Layer** (VMs, scale sets - can run after network + storage ready)
5. **Database Layer** (Azure SQL, Redis - depends on network)
6. **Monitoring Layer** (Log Analytics, alerts - connects to all resources)
7. **Post-deployment Verification** (health checks, connectivity tests)

### Discoveries During Implementation

- **Task 2.2 Discovery**: Azure CLI has rate limits (12,000 requests/hour across all operations)
  - **Symptom**: Deployments failing with 429 errors after ~40 resource creations
  - **Action Taken**: Added exponential backoff retry logic to all Azure CLI calls
  - **New Task Added**: 3.4 "Implement rate limit handling with exponential backoff for all API calls"
  - **Code Location**: `modules/Common.psm1:Invoke-AzureCliWithRetry()` function

- **Task 3.1 Discovery**: Air-gapped network can't reach Azure Key Vault directly (firewall blocks outbound HTTPS)
  - **Symptom**: Timeout errors when retrieving secrets in air-gapped test environment
  - **Action Taken**: Implemented fallback to encrypted local JSON for air-gapped scenarios
  - **New Task Added**: 3.3b "Implement local encrypted JSON secret storage with AES-256"
  - **Code Location**: `modules/Common.psm1:Get-Secret()` function with environment detection

- **Task 2.4 Discovery**: ARM template deployment via Azure CLI is asynchronous but CLI blocks for 20+ minutes
  - **Symptom**: Script appears frozen, no progress indication, violates <30min SLA
  - **Action Taken**: Switched to `--no-wait` flag + poll deployment status with progress bar
  - **New Task Added**: 4.2 "Add deployment progress visualization with Write-Progress"
  - **Code Location**: `Deploy-Infrastructure.ps1:Wait-ArmDeployment()` function

- **Task 4.1 Discovery**: Azure SQL firewall rules must include Azure DevOps agent IPs (not documented in requirements)
  - **Symptom**: Pipeline could deploy database but couldn't run validation queries
  - **Action Taken**: Added Azure DevOps service tag to SQL firewall rules
  - **Tasks Modified**: Updated Task 4.3 (validation) to document this requirement

## Important Terminology

- **Idempotent**: Script produces same result whether run once or multiple times (e.g., create-or-update, not create-and-fail-if-exists)
- **ARM Template**: Azure Resource Manager JSON template (declarative infrastructure definition, version-controlled)
- **Air-gapped Network**: Network isolated from internet (common in high-security/compliance environments, requires local secret storage)
- **RBAC**: Role-Based Access Control (Azure permission system, scripts run as service principal with Contributor role)
- **What-If Deployment**: ARM template dry-run that shows what changes would be made without applying them (used in pre-flight validation)
- **Service Tag**: Azure-managed IP range identifier (e.g., "AzureDevOps" includes all ADO agent IPs, avoids hardcoding)
- **Exponential Backoff**: Retry strategy that waits 2^n seconds between attempts (1s, 2s, 4s) to avoid overwhelming rate-limited APIs

## Patterns Observed

### Deployment Pattern (Per Environment)
1. **Validate** ARM templates (syntax, policy compliance, quota availability)
2. **Simulate** deployment (what-if analysis, show planned changes)
3. **Deploy** infrastructure in dependency order (Network → Storage → Compute → Database → Monitoring)
4. **Verify** deployment (health checks, connectivity tests, smoke tests)
5. **Tag** resources (cost-center, environment, owner, created-date)
6. **Log** operations (all Azure CLI calls logged to file + Azure Log Analytics)

### Error Handling Pattern
- **All Azure CLI calls** wrapped in try/catch blocks
- **Retry with exponential backoff** (3 attempts with 1s, 2s, 4s delays)
- **Log all errors** to file (`logs/deploy-{timestamp}.log`) AND Azure Log Analytics
- **Rollback on critical failures** (if database deployment fails, delete VMs to avoid orphaned resources)
- **Graceful degradation** (if monitoring fails, continue deployment but warn - not critical)

### Idempotency Pattern
- **Use create-or-update semantics** (ARM templates are inherently idempotent)
- **Check existence before deletion** (rollback only deletes resources created by this run)
- **Tag resources with deployment ID** (enables selective rollback)
- **Use `-WhatIf` flag in PowerShell** (for testing without side effects)

## API Rate Limits Learned

| Service          | Limit                           | Mitigation Strategy                                    |
|------------------|---------------------------------|--------------------------------------------------------|
| Azure CLI (all)  | 12,000 requests/hour            | Exponential backoff, batch operations where possible   |
| ARM Deployments  | 1,200 writes/hour/subscription  | Use async deployments (`--no-wait`), poll for status  |
| Resource Groups  | 800 writes/hour/subscription    | Batch resource creation in single ARM template         |
| Azure SQL        | 200 requests/min/database       | Connection pooling, cache query results                |

**Key Learning**: Rate limits are per subscription (shared across all scripts/users), not per script. Exponential backoff is CRITICAL.

## Environment Configuration Differences

| Setting                  | Dev             | Staging         | Production      |
|--------------------------|-----------------|-----------------|-----------------|
| VM Size                  | Standard_B2s    | Standard_D2s_v3 | Standard_D4s_v3 |
| VM Count                 | 1               | 2               | 4 (HA)          |
| Database SKU             | Basic           | Standard S2     | Premium P2      |
| Backup Retention         | 7 days          | 14 days         | 30 days         |
| Log Retention            | 30 days         | 90 days         | 365 days        |
| Auto-scaling             | Disabled        | Enabled         | Enabled         |
| Multi-region             | No              | No              | Yes (East+West) |

## References

- `ouroboros/specs/azure-automation/requirements.md` - Full requirements and compliance needs
- `ouroboros/specs/azure-automation/design.md` - Architecture diagrams and decision rationale
- `ouroboros/specs/azure-automation/phases/phase-2/consolidated.md` - Rate limit discoveries and retry logic design
- `ouroboros/specs/azure-automation/phases/phase-3/consolidated.md` - Air-gapped network solutions and secret handling
- `scripts/Deploy-Infrastructure.ps1` - Main orchestrator (see line 145-230 for deployment sequencing)
- `modules/Common.psm1` - Shared utilities (retry logic at lines 45-78, secret handling at lines 120-165)

## When to Use This Skill

Use this skill when:
- Implementing remaining infrastructure automation tasks (Phase 4-5)
- Debugging deployment issues (check rate limits, idempotency patterns)
- Understanding rate limit constraints and mitigation strategies
- Checking environment-specific configuration differences
- Verifying what has already been discovered about Azure APIs and limitations

**Context Savings**: Using this skill saves ~15K tokens vs. re-reading full requirements (5K) + design (6K) + phase reports (4K).

## Version History

- **v1.0** (2025-10-10) - Initial generation after requirements + design completion
- **v1.1** (2025-10-12) - Updated after Phase 2 with Azure CLI rate limit discoveries
- **v1.2** (2025-10-14) - Updated after Phase 3 with air-gapped network fallback pattern
- **v1.3** (2025-10-15) - Updated after Phase 4 with Azure DevOps firewall rule requirement
```

**Key Features**:
- Technical depth (code project characteristic)
- Rate limits and API constraints documented
- Idempotency patterns captured
- Environment-specific configurations
- Code references with line numbers
- 4.2K tokens vs 15K baseline (72% reduction)

---

### Example 3: API Development Skill

**Project Type**: Resource Management (Code)

```markdown
# Skill: Customer Portal REST API

## Project Context

**Type**: Resource Management (REST API development)
**Goal**: Build customer-facing REST API for account management, billing, and support tickets
**Tech Stack**: Node.js 20, Express 4.18, PostgreSQL 15, Redis 7, JWT authentication
**Constraints**:
- Must support 10,000 concurrent users (load requirement)
- Must respond within 200ms for 95th percentile (performance SLA)
- Must be backwards compatible (v1 API continues running)
- Must implement rate limiting (100 req/min per user)
- Must log all requests for compliance audit

## Key Decisions Made

### API Architecture
- **RESTful Design**: Standard HTTP methods (GET/POST/PUT/DELETE), resource-oriented URLs
- **Versioning**: URL-based (`/api/v2/customers`, not header-based) for simplicity
- **Authentication**: JWT tokens (15-min access + 7-day refresh) with Redis session tracking
- **Authorization**: Role-based (customer, support-agent, admin) enforced at middleware level
- **Error Format**: RFC 7807 Problem Details (consistent error responses across all endpoints)

### Resource Types
1. **Customers** (`/api/v2/customers`) - Profile, preferences, contact info (CRUD)
2. **Billing** (`/api/v2/billing`) - Invoices, payment methods, transactions (mostly read-only)
3. **Support Tickets** (`/api/v2/tickets`) - Create, update, list tickets (complex state machine)
4. **Notifications** (`/api/v2/notifications`) - In-app notifications, read receipts (event-driven)

### Database Schema Decisions
- **UUID Primary Keys** (not auto-increment integers) for security + distributed systems compatibility
- **Soft Deletes** (deleted_at timestamp) for all user-facing resources (compliance requirement)
- **Optimistic Locking** (version column) for concurrent update protection
- **Composite Indexes** on frequently queried combinations (customer_id + created_at)
- **Partitioning** (by month) for support_tickets table (millions of records expected)

### Discoveries During Implementation

- **Task 2.3 Discovery**: PostgreSQL connection pool exhaustion under load testing (default pool size too small)
  - **Symptom**: 503 errors during load test at 8,000 concurrent users (before 10K target)
  - **Action Taken**: Increased pool size from 10 to 50, added connection timeout monitoring
  - **New Task Added**: 4.4 "Add database connection pool metrics to monitoring dashboard"
  - **Code Location**: `src/db/pool.js` (config at lines 12-18)

- **Task 3.2 Discovery**: JWT payload size impacts response times (was including full user object, 2KB token)
  - **Symptom**: 95th percentile response time was 320ms (missed 200ms SLA by 60%)
  - **Action Taken**: Reduced JWT to only user_id + role (128 bytes), fetch user details from Redis cache
  - **Performance Gain**: Response time reduced to 180ms (10% under SLA)
  - **Tasks Modified**: Updated Task 3.4 (caching) to cache user profiles in Redis

- **Task 2.5 Discovery**: Support ticket state machine needs "awaiting_customer" state (not in original design)
  - **Symptom**: Support agents couldn't distinguish between "new tickets" and "tickets waiting for customer response"
  - **Action Taken**: Added `awaiting_customer` state to state machine, updated allowed transitions
  - **Database Impact**: Migration added new enum value, existing tickets unaffected
  - **Tasks Modified**: Updated Task 3.3 (ticket endpoints) to handle new state

- **Task 4.1 Discovery**: Rate limiting by user_id doesn't work for unauthenticated endpoints (login, signup)
  - **Symptom**: Bot could spam login endpoint 1000x/sec (bypassing per-user rate limit)
  - **Action Taken**: Implemented IP-based rate limiting (10 req/min) for unauthenticated endpoints
  - **New Task Added**: 4.5 "Add IP-based rate limiting middleware for public endpoints"
  - **Code Location**: `src/middleware/rate-limit.js:ipRateLimiter()`

## Important Terminology

- **UUID (Universally Unique Identifier)**: 128-bit identifier (e.g., `550e8400-e29b-41d4-a716-446655440000`), avoids exposing sequential IDs
- **Soft Delete**: Marking record as deleted (deleted_at timestamp) instead of removing from database (compliance, audit trail)
- **Optimistic Locking**: Prevent concurrent updates by checking version number (fails if version changed between read and write)
- **JWT (JSON Web Token)**: Self-contained authentication token (signed, not encrypted, validated without database lookup)
- **Redis Session Tracking**: Store active sessions in Redis (fast lookup, automatic expiration, token revocation support)
- **RFC 7807 Problem Details**: Standard error response format (`{"type": "...", "title": "...", "status": 400, "detail": "..."}`)
- **95th Percentile**: 95% of requests complete within this time (ignores outliers, better than average for SLA)

## Patterns Observed

### CRUD Endpoint Pattern
For each resource type:
1. **GET /api/v2/{resource}** - List resources (pagination required, max 100 per page)
2. **GET /api/v2/{resource}/:id** - Get single resource (cached in Redis for 60 seconds)
3. **POST /api/v2/{resource}** - Create resource (validate input, return 201 + Location header)
4. **PUT /api/v2/{resource}/:id** - Update resource (optimistic locking, return 200)
5. **DELETE /api/v2/{resource}/:id** - Soft delete (set deleted_at, return 204)

### Request Flow Pattern
```
Request → Rate Limiter → Auth Middleware → Authorization Check → Controller → Service → Repository → Database
                                                                                              ↓
                                                                                           Response
```

### Error Handling Pattern
- **400 Bad Request**: Invalid input (validation errors, malformed JSON)
- **401 Unauthorized**: Missing or invalid JWT token
- **403 Forbidden**: Valid token but insufficient permissions (role-based)
- **404 Not Found**: Resource doesn't exist or is soft-deleted
- **409 Conflict**: Optimistic locking failure (version mismatch)
- **429 Too Many Requests**: Rate limit exceeded
- **500 Internal Server Error**: Unexpected errors (logged to Sentry, not exposed to client)

### Caching Strategy Pattern
- **User Profiles**: Redis, 60-second TTL (read-heavy, changes infrequent)
- **Billing Invoices**: Redis, 5-minute TTL (expensive query, updates only monthly)
- **Support Tickets**: NO caching (state changes frequently, must be real-time)
- **Notifications**: Redis, 30-second TTL (read-heavy, acceptable staleness)

## API Rate Limits

| Endpoint Type           | Rate Limit          | Scope      | Reset Window |
|-------------------------|---------------------|------------|--------------|
| Authenticated (general) | 100 req/min         | Per user   | 60 seconds   |
| Authenticated (search)  | 20 req/min          | Per user   | 60 seconds   |
| Unauthenticated         | 10 req/min          | Per IP     | 60 seconds   |
| Webhooks (outbound)     | 50 req/min          | Per tenant | 60 seconds   |

**Rate limit headers** (included in all responses):
- `X-RateLimit-Limit`: Total requests allowed
- `X-RateLimit-Remaining`: Requests remaining in window
- `X-RateLimit-Reset`: Unix timestamp when limit resets

## Database Performance Metrics

| Operation                    | Target Latency | Actual (p95) | Notes                          |
|------------------------------|----------------|--------------|--------------------------------|
| Customer profile lookup      | <10ms          | 8ms          | Redis cache (90% hit rate)     |
| Ticket creation              | <50ms          | 42ms         | Includes FK validation         |
| Billing invoice generation   | <200ms         | 180ms        | Complex joins, Redis cached    |
| Full-text ticket search      | <150ms         | 120ms        | PostgreSQL full-text index     |

## References

- `ouroboros/specs/customer-portal-api/requirements.md` - Full API requirements and SLAs
- `ouroboros/specs/customer-portal-api/design.md` - Database schema, architecture diagrams
- `ouroboros/specs/customer-portal-api/phases/phase-2/consolidated.md` - Connection pool tuning discoveries
- `ouroboros/specs/customer-portal-api/phases/phase-3/consolidated.md` - JWT optimization and state machine updates
- `src/controllers/` - API endpoint implementations
- `src/middleware/auth.js` - JWT validation and authorization logic
- `src/db/schema.sql` - Full database schema with indexes

## When to Use This Skill

Use this skill when:
- Implementing remaining API endpoints (Phase 4-5)
- Debugging performance issues (check caching strategy, connection pool config)
- Understanding rate limiting behavior (per-user vs per-IP)
- Checking database schema decisions (UUIDs, soft deletes, optimistic locking)
- Verifying what has been discovered about JWT sizing, state machine states

**Context Savings**: Using this skill saves ~18K tokens vs. re-reading full requirements (6K) + design (7K) + phase reports (5K).

## Version History

- **v1.0** (2025-10-01) - Initial generation after requirements + design completion
- **v1.1** (2025-10-05) - Updated after Phase 2 with connection pool tuning
- **v1.2** (2025-10-08) - Updated after Phase 3 with JWT optimization and state machine changes
- **v1.3** (2025-10-10) - Updated after Phase 4 with IP-based rate limiting for unauthenticated endpoints
```

**Key Features**:
- Technical API details (resource management pattern)
- Performance metrics and SLA tracking
- Database optimization decisions
- Rate limiting strategies
- Error handling standards
- 4.5K tokens vs 18K baseline (75% reduction)

---

## Usage Instructions for Subagents

### When to Use Skills

**Subagents** (executing tasks via `spec-impl.md` agent) should use project-specific skills to reduce context consumption:

```xml
<when-to-use-skills>
  <instead-of-reading-full-specs>
    <!-- DON'T DO THIS -->
    ❌ Read requirements.md (5K tokens)
    ❌ Read design.md (7K tokens)
    ❌ Read phase-1/consolidated.md (2K tokens)
    ❌ Read phase-2/consolidated.md (2K tokens)
    TOTAL: 16K tokens consumed

    <!-- DO THIS INSTEAD -->
    ✅ Read .claude/skills/{feature-name}.md (4K tokens)
    TOTAL: 4K tokens consumed
    SAVINGS: 12K tokens (75% reduction)
  </instead-of-reading-full-specs>

  <when-implementing-task>
    1. Read skill file first (.claude/skills/{feature-name}.md)
    2. Understand project context, constraints, terminology
    3. Check "Discoveries" section for relevant learnings
    4. Implement task according to skill knowledge
    5. If skill doesn't have enough detail for your specific task:
       - Read ONLY the specific section of design.md you need
       - Read ONLY relevant code files
       - Don't re-read entire spec documents
  </when-implementing-task>

  <when-skill-is-insufficient>
    <!-- Some tasks need deeper detail than skill provides -->
    <examples>
      - Implementing complex algorithm (need detailed design spec)
      - Debugging subtle edge case (need to trace through code)
      - Understanding third-party API integration (need design details)
    </examples>

    <strategy>
      1. Start with skill (get project context)
      2. Identify specific gap in knowledge
      3. Read ONLY the relevant section of full spec
      4. Proceed with implementation
    </strategy>
  </when-skill-is-insufficient>
</when-to-use-skills>
```

### Skill Reference Pattern

**Recommended workflow for spec-impl subagents**:

```markdown
## Task Execution Process

1. **Read skill file**: `.claude/skills/{feature-name}.md`
   - Understand project goals and constraints
   - Review relevant discoveries from previous phases
   - Check terminology for domain-specific meanings
   - Note patterns that apply to this task

2. **Identify task-specific needs**:
   - Does skill have enough context for this task? (Yes → proceed)
   - Need deeper design details? (Read specific design.md sections)
   - Need to understand existing code? (Read specific code files)

3. **Implement task**:
   - Follow constraints documented in skill
   - Apply patterns documented in skill
   - Use terminology consistently with skill definitions
   - Reference discoveries to avoid repeating mistakes

4. **Report completion**:
   - Mark task complete in tasks.md
   - Save summary to phases/{phase-id}/summary-{task-id}.md
   - Note any NEW discoveries not in skill (will be added in next skill update)
```

---

## Context Savings Analysis

### Token Budget Breakdown

**Without Skills** (traditional spec-driven approach):
```
Per task context consumption:
- requirements.md: 5,000 tokens
- design.md: 7,000 tokens
- phase consolidations (avg 2): 4,000 tokens
- TOTAL PER TASK: 16,000 tokens

For 20-task project:
- 20 tasks × 16,000 tokens = 320,000 tokens
```

**With Skills** (Ouroboros approach):
```
Per task context consumption:
- {feature-name}.md skill: 4,000 tokens
- (Occasional design.md section reads): 1,000 tokens (average)
- TOTAL PER TASK: 5,000 tokens

For 20-task project:
- 20 tasks × 5,000 tokens = 100,000 tokens
- SAVINGS: 220,000 tokens (69% reduction)
```

### Real-World Savings Examples

| Project Type              | Baseline Tokens | Skill Tokens | Savings | % Reduction |
|---------------------------|-----------------|--------------|---------|-------------|
| Small API (8 tasks)       | 128K            | 40K          | 88K     | 69%         |
| Vacation Planning (12 tasks) | 144K         | 48K          | 96K     | 67%         |
| PowerShell Scripts (15 tasks) | 240K        | 75K          | 165K    | 69%         |
| Documentation (10 tasks)  | 160K            | 50K          | 110K    | 69%         |
| Large Enterprise API (30 tasks) | 480K     | 150K         | 330K    | 69%         |

**Average Savings**: 68-70% context reduction across all project types

### Cost Savings (Claude API)

Based on Claude Sonnet 4.5 pricing (as of 2025-10):
- Input tokens: $3 per 1M tokens
- Output tokens: $15 per 1M tokens

**Example: Medium project (20 tasks)**:
```
Without skills: 320K input tokens = $0.96
With skills: 100K input tokens = $0.30
SAVINGS PER PROJECT: $0.66 (69% reduction)

For teams running 100 projects/year:
ANNUAL SAVINGS: $66 (input tokens only)
```

*Note: Cost savings are modest but context savings enable fitting more complex projects within model limits.*

---

## Implementation Guide

### For Orchestrator Agent

When implementing SKILLS generation in the orchestrator workflow:

1. **After requirements + design complete**:
   ```
   Generate initial skill file at .claude/skills/{feature-name}.md
   ```

2. **After each phase consolidation**:
   ```
   Update skill file with discoveries from phases/{phase-id}/consolidated.md
   Increment version number
   Add version history entry
   ```

3. **Instruct subagents to use skills**:
   ```
   Pass skill file path to subagents
   Remind subagents to read skill BEFORE full specs
   ```

### For Subagent Agent (spec-impl)

Update `open-spec/agents/kfc/spec-impl.md` with:

```markdown
<context-efficiency>

## Using Project-Specific Skills

**CRITICAL**: To reduce context consumption, use project-specific skills instead of re-reading full specs.

<skill-usage-workflow>

1. **Check for skill file**:
   - Location: `.claude/skills/{feature-name}.md`
   - If exists: Read this FIRST (before requirements.md or design.md)

2. **Read skill file** (~3-5K tokens):
   - Project context and goals
   - Key constraints and decisions
   - Important terminology
   - Patterns to follow
   - Discoveries from previous phases

3. **Assess if skill is sufficient**:
   - ✅ Skill has enough context → Proceed with task implementation
   - ❌ Need deeper detail → Read ONLY specific sections of design.md or code files

4. **Implement task** using skill knowledge:
   - Follow constraints documented in skill
   - Apply patterns from skill
   - Use terminology consistently
   - Reference discoveries to avoid repeating issues

</skill-usage-workflow>

<context-savings>

Using skills saves **10-25K tokens per task** vs. reading full specs:

| Approach          | Tokens | Notes                           |
|-------------------|--------|---------------------------------|
| Read full specs   | 15-30K | requirements + design + phases  |
| Read skill        | 3-5K   | Compressed, essential context   |
| **Savings**       | **12-25K** | **60-75% reduction**        |

</context-savings>

<when-skill-insufficient>

If skill doesn't have enough detail for your task:

1. Read ONLY the specific section of design.md you need
2. Read ONLY the relevant code files you need
3. Don't re-read entire spec documents
4. Note the gap in your task summary (skill will be updated)

**Example**:
- Task: Implement complex validation algorithm
- Skill: Doesn't have algorithm details (too large for skill file)
- Action: Read skill for context + design.md section 3.4 for algorithm spec
- Total: 4K (skill) + 2K (design section) = 6K tokens (vs 16K full specs)

</when-skill-insufficient>

</context-efficiency>
```

---

## Future Enhancements

### Skill Templates by Pattern

Create pattern-specific skill templates that automatically include pattern-appropriate sections:

- **Structured Sequential**: Include stage dependencies, rollback procedures
- **Creative Iterative**: Include iteration tracking, feedback loops
- **Resource Management**: Include CRUD patterns, validation rules
- **Exploratory Research**: Include hypothesis tracking, findings synthesis
- **Modern Dev Workflow**: Include automation decisions, observability choices

### Multi-Project Skill Synthesis

For organizations with many similar projects:

- Extract common patterns across multiple project skills
- Create "meta-skills" (e.g., "REST API Best Practices" synthesized from 10 API projects)
- Reference meta-skills from project-specific skills
- Further reduce token usage by factoring out common knowledge

### Skill Quality Metrics

Track skill effectiveness:

- **Context savings per task** (actual vs baseline)
- **Skill insufficiency rate** (how often subagents need to read full specs)
- **Discovery coverage** (% of discoveries captured in skill)
- **Skill freshness** (time since last update)

---

## Summary

The SKILLS Generator is a critical component of the Ouroboros framework that:

1. **Captures project knowledge** in compressed, efficient format
2. **Works universally** across all project types (code, docs, planning, scripts, creative)
3. **Evolves continuously** with new discoveries from each phase
4. **Saves 60-75% context** per task vs. reading full specs
5. **Preserves critical information** (constraints, decisions, terminology, patterns)
6. **Enables subagents** to work efficiently without re-reading full documentation

**The serpent remembers what it has learned, growing wiser with each coil.** 🐍

---

**Generated by Ouroboros Framework**
**Version**: 1.0
**Last Updated**: 2025-10-25
