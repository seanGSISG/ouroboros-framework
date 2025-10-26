# Create New Ouroboros Spec

When the user runs `/new-spec {feature-name}` or `/new-spec`, help them create a new Ouroboros specification.

## Process

1. **Get feature name** (if not provided):
   - Ask user: "What is the name of your feature? (use kebab-case, e.g., 'user-authentication', 'vacation-planning', 'api-docs')"
   - Wait for response

2. **Detect project pattern**:
   - Ask user: "What type of project is this?"
   - Present options:
     1. Code project (APIs, CLIs, web apps, scripts)
     2. Documentation (user guides, API docs, blog posts)
     3. Planning (vacation itineraries, event planning, business processes)
     4. Scripts/Automation (deployment, infrastructure, migrations)
     5. Creative work (design systems, content creation)
     6. Not sure / Need help deciding

3. **Select pattern template**:
   Based on user's project type, suggest the most appropriate pattern:
   - Code project → Ask: "Does this involve CRUD operations?"
     - Yes → Resource Management pattern
     - No → Modern Dev Workflow pattern
   - Documentation → Structured Sequential Workflow pattern
   - Planning → Creative Iterative Process pattern
   - Scripts → Modern Dev Workflow pattern
   - Creative → Creative Iterative Process pattern
   - Not sure → Ask clarifying questions to detect pattern

4. **Create spec structure**:
   ```bash
   mkdir -p ouroboros/specs/{feature-name}
   ```

5. **Copy pattern templates**:
   Based on selected pattern (e.g., resource-management):
   ```bash
   cp ouroboros/ouroboros/templates/patterns/{pattern}-requirements.md ouroboros/specs/{feature-name}/requirements.md
   cp ouroboros/ouroboros/templates/patterns/{pattern}-design.md ouroboros/specs/{feature-name}/design.md
   cp ouroboros/ouroboros/templates/patterns/{pattern}-tasks.md ouroboros/specs/{feature-name}/tasks.md
   ```

6. **Customize templates**:
   - Replace `{feature-name}` placeholder with actual feature name
   - Replace `{Feature Name}` placeholder with title-case feature name
   - Update any other placeholders specific to the user's project

7. **Confirm creation**:
   Display success message:
   ```
   ✅ Created new Ouroboros spec: {feature-name}

   📁 Location: ouroboros/specs/{feature-name}/
   📋 Pattern: {Pattern Name}

   Next steps:
   1. Edit requirements.md - Add your EARS-format requirements
   2. Edit design.md - Document your architecture approach
   3. Edit tasks.md - Break down implementation into phases
   4. Execute: "Use ouroboros workflow to implement {feature-name}"

   📖 See ouroboros/ouroboros/CLAUDE.md for detailed guidance
   ```

8. **Open files for editing**:
   - Ask user: "Would you like me to open the requirements.md file so you can start adding requirements?"
   - If yes, display the requirements.md file for editing

## Pattern Template Paths

Available patterns in `ouroboros/ouroboros/templates/patterns/`:

1. **Structured Sequential Workflow**
   - `structured-sequential-requirements.md`
   - `structured-sequential-design.md`
   - `structured-sequential-tasks.md`

2. **Creative Iterative Process**
   - `creative-iterative-requirements.md`
   - `creative-iterative-design.md`
   - `creative-iterative-tasks.md`

3. **Resource Management**
   - `resource-management-requirements.md`
   - `resource-management-design.md`
   - `resource-management-tasks.md`

4. **Exploratory Research**
   - `exploratory-research-requirements.md`
   - `exploratory-research-design.md`
   - `exploratory-research-tasks.md`

5. **Modern Dev Workflow**
   - `modern-dev-workflow-requirements.md`
   - `modern-dev-workflow-design.md`
   - `modern-dev-workflow-tasks.md`

## Example Interactions

### Example 1: With feature name provided
```
User: /new-spec user-authentication
Assistant: Creating spec for 'user-authentication'...

What type of project is this?
1. Code project
2. Documentation
3. Planning
4. Scripts/Automation
5. Creative work
6. Not sure

User: 1
Assistant: Does this involve CRUD operations (Create, Read, Update, Delete)?

User: Yes
Assistant: Perfect! Using Resource Management pattern.
[Creates files and displays confirmation]
```

### Example 2: Without feature name
```
User: /new-spec
Assistant: What is the name of your feature? (use kebab-case)

User: europe-vacation-2024
Assistant: What type of project is this?
[Continues with pattern selection...]
```

## Error Handling

- If spec already exists: "⚠️ Spec '{feature-name}' already exists at ouroboros/specs/{feature-name}/. Would you like to overwrite it or choose a different name?"
- If templates not found: "⚠️ Pattern templates not found. Please ensure ouroboros/ouroboros/templates/patterns/ exists."
- If invalid feature name: Suggest valid kebab-case format

## Notes

- Always use kebab-case for feature names (e.g., `user-auth`, not `UserAuth` or `user_auth`)
- The feature name will be used for:
  - Directory name: `ouroboros/specs/{feature-name}/`
  - Auto-generated skill: `.claude/skills/{feature-name}.md`
  - Phase directories: `ouroboros/specs/{feature-name}/phases/`

---

🐍 *The serpent inscribes a new circle, ready to consume and transform the user's vision into reality...* 🐍
