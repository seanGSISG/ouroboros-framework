# Create New Ouroboros Spec (Dynamic Generation v2.0)

When the user runs `/ou-new-spec {feature-name}` or `/ou-new-spec`, help them create a new Ouroboros specification using **dynamic template generation**.

## NEW in v2.0

- ✅ **Plain language questions** (no "CRUD" jargon!)
- ✅ **Dynamic spec generation** (80% customized to your project)
- ✅ **Domain-aware** (vacation planner gets "bookings", NOT "Docker")
- ✅ **Jargon validation** (catches tech terms in non-tech projects)
- ✅ **Context storage** (saves your answers for future use)

---

## Process

### Step 1: Get Feature Name
```
If not provided, ask: "What is the name of your feature? (use kebab-case)"
Examples: 'vacation-planner', 'user-auth', 'blog-post-series'
```

### Step 2: Identify Domain (NEW - User Friendly!)
```
Read: ouroboros/intelligence/domain-questions.md

Ask: "What type of project is this?"

1. Software Development
   Building software: APIs, applications, scripts, tools

2. Documentation
   Creating written content: guides, tutorials, blog posts

3. Planning & Organization
   Organizing activities: vacation planning, events, processes

4. Creative Work
   Creating designs: branding, visual design, content

5. Data & Research
   Analyzing or investigating: research, data analysis

6. Not sure / Need help
   I'll ask clarifying questions

Store answer as: domain
```

### Step 3: Select Pattern (Domain-Aware)
```
Based on domain, ask pattern-specific questions from:
ouroboros/intelligence/domain-questions.md

Example for Planning domain:
"Do you know all the steps that need to happen?"
→ Yes: Structured Sequential
→ No: "Will you refine based on feedback?" 
   → Yes: Creative Iterative
   → No: Exploratory Research

NO MORE "CRUD" QUESTIONS! ✅
Instead: "Does this involve managing stored information (creating, viewing, editing, deleting)?"
```

### Step 4: Gather Scope Context (Pattern-Specific)
```
Read: ouroboros/intelligence/pattern-questions/{pattern}.md

Ask pattern-specific questions to gather project details.

Example for Resource Management + Planning domain:
- "What are you managing?" → "vacation bookings"
- "What operations are needed?" → [Add, View, Update, Delete]
- "How will items be organized?" → "By date/time"

Store all answers in scopeAnswers object.
```

### Step 5: Generate Specs Dynamically (THE MAGIC!)
```
1. Load generation prompt:
   ouroboros/intelligence/generation-prompts/tasks-generator.md

2. Build LLM prompt with context:
   - featureName: {feature-name}
   - domain: {domain}
   - pattern: {pattern}
   - scopeAnswers: {all user answers}

3. Call Claude Sonnet 4 to generate tasks.md
   (Use prompt from tasks-generator.md)

4. Repeat for requirements.md and design.md

5. Validate generated content:
   - Check against jargon-detector.yaml
   - Flag any domain-inappropriate terms
   - Show violations to user

6. If violations found:
   Ask: "I found some technical jargon that might not fit. Regenerate?"
   → Yes: Regenerate with stronger anti-jargon instructions
   → No: Proceed anyway
```

### Step 6: Save Specs + Context
```bash
# Create directory
mkdir -p ouroboros/specs/{feature-name}

# Save generated specs
echo "{generated-requirements}" > ouroboros/specs/{feature-name}/requirements.md
echo "{generated-design}" > ouroboros/specs/{feature-name}/design.md
echo "{generated-tasks}" > ouroboros/specs/{feature-name}/tasks.md

# Save context for future use
cat > ouroboros/specs/{feature-name}/.context.json <<EOF
{
  "featureName": "{feature-name}",
  "domain": "{domain}",
  "pattern": "{pattern}",
  "generatedAt": "{ISO-8601-timestamp}",
  "scopeAnswers": {user answers},
  "generationMethod": "dynamic",
  "version": "2.0"
}
EOF
```

### Step 7: Confirm Creation
```
✅ Created new Ouroboros spec: {feature-name}

📁 Location: ouroboros/specs/{feature-name}/
📋 Pattern: {Pattern Name}
🌍 Domain: {Domain}
⚡ Generation: Dynamic (v2.0)

✨ This spec is 80% customized to your project!
   (Not generic boilerplate - it references YOUR actual work)

📝 Files created:
- requirements.md (EARS format, domain-appropriate)
- design.md (architecture approach)
- tasks.md (phase breakdown with parallel tasks)
- .context.json (your answers saved)
```

### Step 8: Offer Next Steps
```
Next steps:

1. Review the generated specs
   (They should already be 80% ready!)

2. Make any final tweaks
   (Edit files if needed)

3. Execute with Ouroboros:
   "Use ouroboros workflow to implement {feature-name}"

OR

Run tests first:
   "Validate {feature-name} spec quality"
```

---

## Example Interaction (NEW v2.0 Flow)

```
User: /ou-new-spec vacation-euro-2025
```