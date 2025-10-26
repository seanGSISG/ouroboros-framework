# Resource Management - Scope Questions

**Pattern**: Resource Management
**Purpose**: Gather context to generate domain-appropriate tasks

---

## Core Questions

### Q1: What are you managing?
```
What type of items/resources will this project manage?

Examples:
- User accounts (software)
- Recipes (planning/creative)
- Vacation bookings (planning)
- Design assets (creative)
- Article library (documentation)
- Budget entries (planning)
```

**Store as**: `resource_type`

---

### Q2: What operations are needed?
```
What actions do people need to perform? (Select all that apply)

☐ Add new items
☐ View/search existing items
☐ Update/modify items
☐ Remove/delete items
☐ Organize/categorize items
☐ Share items with others
☐ Track history/changes
```

**Store as**: `operations` (array)

---

### Q3: Who controls access?
```
Who can perform these actions?

1. Anyone (no restrictions)
2. Specific people/roles (need permissions)
3. Just me (personal project)
4. Not sure yet
```

**Store as**: `access_control_level`

---

### Q4: What makes a valid item?
```
What rules determine if an item is valid?

Example answers:
- "Recipes must have a title and ingredients list"
- "Bookings need a date and location"
- "Users must have a unique email"
- "No specific rules yet"
```

**Store as**: `validation_rules`

---

## Domain-Specific Variants

### For Software Development:
```
Additional question: How will this be accessed?

1. REST API endpoints
2. GraphQL API
3. Command-line interface
4. Web interface
5. Library/package
6. Not sure yet
```

**Store as**: `access_method`

### For Planning/Creative:
```
Additional question: How will items be organized?

1. By date/time
2. By category/tags
3. By status/state
4. Hierarchical (folders/groups)
5. Not sure yet
```

**Store as**: `organization_method`

---

## Example Context Generated

**Example 1: Vacation Planner (Planning Domain)**
```json
{
  "resource_type": "vacation bookings",
  "operations": ["Add new items", "View/search existing items", "Update/modify items", "Remove/delete items"],
  "access_control_level": "Just me",
  "validation_rules": "Bookings need a date, location, and cost",
  "organization_method": "By date/time"
}
```

**Generated tasks would include**:
- "Add new booking (flight, hotel, activity)"
- "View all bookings for trip"
- "Modify booking details"
- "Cancel/remove booking"

**NOT**:
- "Setup REST API endpoints" ❌
- "Implement database schema" ❌
- "Configure Kubernetes" ❌

---

**Example 2: User Auth API (Software Domain)**
```json
{
  "resource_type": "user accounts",
  "operations": ["Add new items", "View/search existing items", "Update/modify items", "Remove/delete items"],
  "access_control_level": "Specific people/roles",
  "validation_rules": "Users must have unique email and secure password",
  "access_method": "REST API endpoints"
}
```

**Generated tasks would include**:
- "Implement POST /users endpoint (create)"
- "Implement GET /users endpoints (list/search)"
- "Implement PATCH /users/:id (update)"
- "Implement DELETE /users/:id"
- "Add JWT authentication middleware"

**Appropriate here** because domain = software development!
