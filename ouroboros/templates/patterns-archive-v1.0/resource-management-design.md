# Design - [Project Name]

**Pattern**: Resource Management

**Design Philosophy**: Infrastructure first, then CRUD operations, access control, and lifecycle management.

---

## Architecture Overview

**Resource Model**: [Define the primary resource(s) being managed]

**Storage Strategy**: [Database, file system, cloud storage, etc.]

**API Style**: [REST, GraphQL, RPC, function calls, etc.]

---

## CRUD Operation Design

### Create
- Endpoint/Interface: [Definition]
- Validation: [What to validate]
- ID Generation: [Strategy]
- Atomicity: [How to ensure atomic creation]

### Read
- Single resource: [Endpoint/interface]
- List/Search: [Endpoint/interface with filters]
- Caching: [Strategy]

### Update
- Full vs Partial: [Approach]
- Concurrency Control: [Optimistic locking, versioning]
- Validation: [Changed fields only or full re-validation]

### Delete
- Soft vs Hard: [Approach and rationale]
- Cascade Behavior: [How related resources handled]
- Constraints: [What prevents deletion]

---

## Data Model

**Primary Resource**: [Resource Name]
```
{
  "id": "unique identifier",
  "field1": "type (validation rules)",
  "field2": "type (validation rules)",
  "created_at": "timestamp",
  "updated_at": "timestamp",
  "created_by": "user_id",
  "updated_by": "user_id",
  "status": "lifecycle state"
}
```

**Relationships**:
- One-to-many: [Description]
- Many-to-many: [Description]

---

## Validation Rules

**Field-Level**:
- Required: [List]
- Format: [Patterns, regex]
- Range: [Min/max]

**Business Rules**:
- [Rule 1]: [Description]
- [Rule 2]: [Description]

---

## Access Control Design

**Permission Model**: [RBAC, ABAC, etc.]

**Permissions**:
- read:[resource]
- create:[resource]
- update:[resource]
- delete:[resource]
- admin:[resource]

**Authorization Flow**: [How permissions checked]

---

## Lifecycle States

**States**: [draft, active, archived, deleted, etc.]

**Transitions**:
```
draft → active (on publish)
active → archived (on archive)
archived → active (on restore)
active → deleted (on delete)
```

---

## Cross-Domain Examples

**REST API**: Standard CRUD endpoints with JWT auth
**Knowledge Base**: Article lifecycle with review states
**Budget Management**: Expense categories with approval workflow
**Infrastructure**: VM lifecycle with health monitoring

---

**Generated from Ouroboros Pattern**: Resource Management
**Template Version**: 1.0
**Last Updated**: 2025-10-25
