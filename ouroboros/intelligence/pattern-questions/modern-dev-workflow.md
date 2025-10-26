# Modern Dev Workflow - Scope Questions

**Pattern**: Modern Development Workflow
**Purpose**: This pattern should RARELY be used for non-software projects

---

## Domain Check (CRITICAL)

**Before asking any questions, verify**:
```
⚠️ WARNING: This pattern uses automation and deployment concepts.

Is your project related to:
- Software development
- Infrastructure automation
- Documentation-as-code (with build systems)
- Automated workflows/scripts

→ No? Consider using a different pattern:
  - Structured Sequential Workflow (for step-by-step processes)
  - Creative Iterative Process (for design/creative work)
  - Resource Management (for managing items/data)
```

---

## Core Questions (Software/Automation Projects Only)

### Q1: What are you building/automating?
```
Describe what this project creates or automates:

Examples:
- "A REST API for user management"
- "Automated deployment pipeline"
- "Documentation build system"
- "Infrastructure provisioning scripts"
```

**Store as**: `project_description`

---

### Q2: What are the main quality checks?
```
How will you ensure quality? (Select all that apply)

☐ Automated tests
☐ Code quality checks (linting, formatting)
☐ Security scanning
☐ Performance testing
☐ Manual review
☐ Not sure yet
```

**Store as**: `quality_gates` (array)

---

### Q3: How will this be deployed/delivered?
```
How does this get delivered to users?

Examples:
- "Deployed to cloud hosting"
- "Published as npm package"
- "Deployed to GitHub Pages"
- "Run as cron job"
- "Manual execution"
- "Not sure yet"
```

**Store as**: `deployment_method`

---

### Q4: What needs to be monitored?
```
What indicators show this is working correctly?

Examples:
- "API response times and error rates"
- "Build success/failure"
- "Website uptime"
- "Script execution logs"
- "Nothing specific"
```

**Store as**: `observability_needs`

---

## Generated Task Examples

**For API Project**:
- Phase 1: Build core API functionality
- Phase 2: Add automated testing + quality checks (parallel)
- Phase 3: Setup deployment automation
- Phase 4: Add monitoring and logging

**For Doc-as-Code Project**:
- Phase 1: Create documentation structure
- Phase 2: Add build automation + link checking (parallel)
- Phase 3: Setup GitHub Pages deployment
- Phase 4: Add analytics and monitoring

**NOT for vacation planning** ❌
**NOT for creative design** ❌
**NOT for manual research** ❌
