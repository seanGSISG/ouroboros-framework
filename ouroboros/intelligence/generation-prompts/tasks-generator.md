# Tasks Generation Prompt

**Purpose**: Generate domain-appropriate tasks.md from user context
**Model**: Claude Sonnet 4 (fast, high quality)

---

## System Prompt

You are generating an Ouroboros tasks.md file for a **{pattern}** project in the **{domain}** domain.

**Project Context**:
- Feature: `{featureName}`
- Domain: `{domain}`
- Pattern: `{pattern}`
- User Answers: `{scopeAnswers}`

**Critical Rules**:
1. **Use domain-appropriate language** - No tech jargon unless domain = "software-development"
2. **Reference the user's actual project** - Use `{featureName}` and details from `{scopeAnswers}`
3. **Follow {pattern} structure** exactly (phases, parallel/sequential markers)
4. **80% of content must be project-specific**, not generic boilerplate
5. **Forbidden terms for non-software domains**: Docker, Kubernetes, CI/CD, API (unless docs), database, schema, REST, microservices

**Pattern Structure to Follow**:
```
{pattern_structure_template}
```

**Domain-Specific Vocabulary**:

Software Development: APIs, databases, tests, deployment, code, functions, endpoints
Documentation: sections, chapters, outlines, examples, guides, tutorials
Planning: schedule, booking, itinerary, tasks, checklists, timeline
Creative: design, mockup, iteration, feedback, concept, vision
Data/Research: analysis, findings, hypothesis, research, investigation

**Use the vocabulary that matches domain = "{domain}"!**

---

## Examples

### Example 1: Vacation Planner (Planning + Resource Management)

**Input Context**:
```json
{
  "featureName": "europe-vacation-2024",
  "domain": "planning",
  "pattern": "resource-management",
  "scopeAnswers": {
    "resource_type": "vacation bookings",
    "operations": ["Add", "View", "Update", "Delete"],
    "organization_method": "By date/time"
  }
}
```

**Generated Output**:
```markdown
# Tasks - Europe Vacation 2024

**Pattern**: Resource Management

**Task Philosophy**: Research → Booking Operations (parallel) → Organization → Finalization

---

## Phase Structure

### Phase 1: Foundation (Sequential 🐌)

**Goal**: Research destinations and set up planning framework

- [ ] **🐌 1.1 Research destinations and create shortlist**
  - Identify must-see cities and attractions
  - Check visa requirements and travel restrictions
  - Research best time to visit each location
  - _Context: ~8K tokens_
  - _Duration: ~12 minutes_

- [ ] **🐌 1.2 Set budget and constraints**
  - Define total budget for trip
  - Set daily spending limits
  - Identify non-negotiable requirements (dates, accommodations)
  - _Context: ~5K tokens_
  - _Duration: ~8 minutes_

### Phase 2: Booking Operations (4 parallel 🐍)

**Goal**: Make all necessary bookings

- [ ] **🐍 2.1 Book flights**
  - Compare flight options (direct vs. connections)
  - Select and book main flights
  - Add booking to itinerary with confirmation numbers
  - _Context: ~12K tokens_
  - _Duration: ~15 minutes_
  - **Can run in parallel with 2.2, 2.3, 2.4**

- [ ] **🐍 2.2 Reserve accommodations**
  - Research hotels/Airbnbs in each city
  - Book accommodations for each location
  - Add reservations to itinerary
  - _Context: ~15K tokens_
  - _Duration: ~18 minutes_
  - **Can run in parallel with 2.1, 2.3, 2.4**

- [ ] **🐍 2.3 Plan and book activities**
  - Research top activities in each city
  - Book tickets for museums, tours, events
  - Add to daily itinerary
  - _Context: ~12K tokens_
  - _Duration: ~15 minutes_
  - **Can run in parallel with 2.1, 2.2, 2.4**

- [ ] **🐍 2.4 Arrange transportation**
  - Research inter-city travel (trains, buses, car rental)
  - Book transportation between cities
  - Plan local transportation in each city
  - _Context: ~10K tokens_
  - _Duration: ~12 minutes_
  - **Can run in parallel with 2.1, 2.2, 2.3**

### Phase 3: Organization (Sequential 🐌)

**Goal**: Organize all bookings into coherent itinerary

- [ ] **🐌 3.1 Create day-by-day itinerary**
  - Organize bookings by date
  - Add buffer time between activities
  - Identify gaps or conflicts
  - _Context: ~10K tokens_
  - _Duration: ~12 minutes_

- [ ] **🐌 3.2 Add backup options and contingency plans**
  - Identify alternative activities if plans change
  - Note cancellation policies
  - Create emergency contact list
  - _Context: ~8K tokens_
  - _Duration: ~10 minutes_

### Phase 4: Finalization (Sequential 🐌)

**Goal**: Final preparations

- [ ] **🐌 4.1 Create packing list and final checklist**
  - List items to pack
  - Note important documents needed
  - Create pre-departure checklist
  - _Context: ~5K tokens_
  - _Duration: ~8 minutes_

- [ ] **🐌 4.2 Share itinerary and confirm all bookings**
  - Share itinerary with travel companions
  - Confirm all reservations 24-48 hours before
  - Print or save offline copies
  - _Context: ~5K tokens_
  - _Duration: ~8 minutes_

---

**Generated from Ouroboros Pattern**: Resource Management
**Created**: 2025-10-26
```

**Notice**:
- Zero tech jargon! ✅
- Uses planning vocabulary (booking, itinerary, reservations) ✅
- References actual project (Europe Vacation 2024) ✅
- Follows Resource Management structure (Foundation → Operations → Organization → Polish) ✅
- NOT generic boilerplate! ✅

---

### Example 2: User Auth API (Software + Resource Management)

**Input Context**:
```json
{
  "featureName": "user-authentication",
  "domain": "software-development",
  "pattern": "resource-management",
  "scopeAnswers": {
    "resource_type": "user accounts",
    "operations": ["Add", "View", "Update", "Delete"],
    "access_method": "REST API endpoints"
  }
}
```

**Generated Output** (abbreviated):
```markdown
### Phase 2: CRUD Operations (4 parallel 🐍)

- [ ] **🐍 2.1 Implement user creation endpoint**
  - POST /users endpoint
  - Validate email uniqueness
  - Hash password with bcrypt
  - Return JWT token
  - **Can run in parallel with 2.2, 2.3, 2.4**

- [ ] **🐍 2.2 Implement user read operations**
  - GET /users/:id endpoint
  - GET /users (list with pagination)
  - Filter by role, status
  - **Can run in parallel with 2.1, 2.3, 2.4**
```

**Notice**:
- Tech terms are APPROPRIATE here (domain = software-development) ✅
- Still references actual project (user-authentication) ✅

---

## Anti-Examples (What NOT to Generate)

### ❌ BAD: Vacation Planner with Tech Jargon

```markdown
### Phase 2: Automation (4 parallel 🐍)

- [ ] **🐍 2.1 Setup CI/CD pipeline**
  - Configure GitHub Actions for booking automation
  - Docker containerize vacation planning
```

**Why This Is Wrong**:
- Domain = "planning" but using software jargon
- Makes no sense for vacation planning
- Violates jargon rules

### ❌ BAD: Generic Boilerplate

```markdown
### Phase 1: Foundation

- [ ] **🐌 1.1 Implement core functionality**
  - Build main components
  - Setup infrastructure
```

**Why This Is Wrong**:
- Too generic, doesn't reference user's project
- "core functionality" is vague
- Not 80% project-specific

---

## Output Format

Generate ONLY the tasks.md content. No explanations, no meta-commentary.

Start with:
```markdown
# Tasks - {Project Name}
```

End with:
```markdown
**Generated from Ouroboros Pattern**: {Pattern Name}
**Template Version**: 2.0 (Dynamic)
**Last Updated**: 2025-10-26
```
