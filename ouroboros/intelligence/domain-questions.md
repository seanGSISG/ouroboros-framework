# Domain Detection Questions

**Purpose**: Help users identify their project domain without confusing jargon
**Version**: 2.0 (Plain Language)
**Last Updated**: 2025-10-26

---

## Primary Domain Question

**Question**:
```
What type of project is this?

1. Software Development
   Building software: APIs, applications, scripts, tools, libraries

2. Documentation
   Creating written content: user guides, API docs, tutorials, blog posts

3. Planning & Organization
   Organizing activities: vacation planning, event planning, project management

4. Creative Work
   Creating designs or content: branding, visual design, content creation

5. Data & Research
   Analyzing or investigating: research projects, data analysis, optimization studies

6. Not sure / Multiple types
   I'll help you figure it out
```

**User-Friendly Features**:
- ✅ Clear categories with examples
- ✅ No jargon (no "CRUD", "CI/CD", etc.)
- ✅ Real-world language
- ✅ "Not sure" escape hatch

---

## Follow-Up Questions (If "Not sure")

**Clarifying Question Set**:

```
Let me help narrow it down. Which statement best describes your project?

A. "I'm building something that runs on a computer or server"
   → Software Development

B. "I'm writing or creating documentation for others to read"
   → Documentation

C. "I'm planning an event, trip, or organizing a process"
   → Planning & Organization

D. "I'm creating visual designs, branding, or creative content"
   → Creative Work

E. "I'm researching a topic or analyzing data to answer questions"
   → Data & Research

F. "Still not sure - can you ask me different questions?"
   → Alternative question flow
```

**Alternative Question Flow**:

```
What will the end result be?

A. Working software that people can use
   → Software Development

B. A document or website that people can read
   → Documentation (or Creative if visual)

C. A plan, schedule, or organized process
   → Planning & Organization

D. A design, mockup, or creative asset
   → Creative Work

E. A report with findings and recommendations
   → Data & Research
```

---

## Pattern-Specific Questions (Domain-Aware)

### For Software Development Domain

**Pattern Detection Questions**:

```
Does this project involve managing stored information?
(Examples: Creating, viewing, editing, deleting user accounts, recipes, bookings, etc.)

→ Yes: Resource Management pattern
→ No: Continue to next question
```

```
Is this primarily about automation and deployment processes?
(Examples: Build pipelines, automated testing, infrastructure setup)

→ Yes: Modern Dev Workflow pattern
→ No: Continue to next question
```

```
Does this follow a clear sequence of stages with validation at each step?
(Examples: Data pipelines, deployment scripts, multi-stage processes)

→ Yes: Structured Sequential Workflow pattern
→ No: Continue to next question
```

```
Will you be creating multiple versions and getting feedback to improve?
(Examples: UI/UX design, feature prototypes, experimental features)

→ Yes: Creative Iterative Process pattern
→ No: Likely Exploratory Research pattern
```

### For Documentation Domain

**Pattern Detection Questions**:

```
Do you know the exact structure and sections upfront?
(Examples: API reference with fixed sections, tutorial with known steps)

→ Yes: Structured Sequential Workflow pattern
→ No: Continue to next question
```

```
Will you be writing, getting feedback, and revising multiple times?
(Examples: Blog posts, long-form guides, thought leadership content)

→ Yes: Creative Iterative Process pattern
→ No: Exploratory Research pattern (research-heavy docs)
```

### For Planning & Organization Domain

**Pattern Detection Questions**:

```
Do you know all the steps that need to happen?
(Examples: Wedding planning checklist, product launch timeline)

→ Yes: Structured Sequential Workflow pattern
→ No: Continue to next question
```

```
Will you be creating options and refining based on feedback?
(Examples: Vacation itinerary, event design, process improvement)

→ Yes: Creative Iterative Process pattern
→ No: Exploratory Research pattern (researching options)
```

### For Creative Work Domain

**Pattern Detection Questions**:

```
Will you create multiple versions and iterate based on feedback?
(Examples: Logo design, branding, visual identity)

→ Yes: Creative Iterative Process pattern
→ No: Structured Sequential Workflow pattern (production work)
```

### For Data & Research Domain

**Pattern Detection Questions**:

```
Do you know exactly what you're investigating, or are you exploring?

→ Exploring / discovering patterns: Exploratory Research pattern
→ Known investigation steps: Structured Sequential Workflow pattern
```

---

## Anti-Patterns (What NOT to Ask)

❌ **BAD**: "Does this involve CRUD operations?"
- Jargon alert!
- Non-technical users don't know "CRUD"

✅ **GOOD**: "Does this involve managing stored information (creating, viewing, editing, deleting)?"

❌ **BAD**: "Will you use CI/CD?"
- Tech-specific assumption
- Irrelevant to most users

✅ **GOOD**: "Is this primarily about automation?"

❌ **BAD**: "Is this a RESTful API or GraphQL?"
- Too implementation-specific
- Assumes software development knowledge

✅ **GOOD**: "What type of project is this?" (start broad)

---

## Implementation Guide

**In /ou-new-spec command**:

1. Ask primary domain question first
2. If "Not sure", use clarifying questions
3. Once domain identified, ask pattern-specific questions
4. Store answers in context
5. Use context to generate domain-appropriate specs

**Example Flow**:

```
User: /ou-new-spec vacation-planner