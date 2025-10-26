# Requirements - [Project Name]

**Pattern**: Resource Management

**Pattern Characteristics**:
- CRUD operations (Create, Read, Update, Delete)
- Data validation and constraints
- State tracking and persistence
- Access control and permissions
- Lifecycle management

---

## Project Overview

**What resources are we managing?**
[Brief description - works for REST APIs, knowledge bases, budget management, asset libraries, etc.]

**What problem does this solve?**
[Problem statement]

**Who will use/benefit from this?**
[Target users or stakeholders]

---

## Requirements (EARS Format)

### 1. Resource Creation

**1.1** WHEN a user creates a [resource], the system SHALL validate and store it
  - AC 1.1.1: All required fields present
  - AC 1.1.2: Data types validated
  - AC 1.1.3: Constraints enforced (unique, format, range)
  - AC 1.1.4: Unique identifier generated
  - AC 1.1.5: Creation timestamp recorded

**1.2** IF validation fails, the system SHALL return descriptive errors
  - AC 1.2.1: Error messages identify specific fields
  - AC 1.2.2: Error codes standardized
  - AC 1.2.3: No partial creation (atomic operation)

### 2. Resource Retrieval

**2.1** WHEN a user requests a [resource], the system SHALL return it if authorized
  - AC 2.1.1: Resource found and returned with all fields
  - AC 2.1.2: Response time < [X]ms for single resource
  - AC 2.1.3: 404 returned if not found
  - AC 2.1.4: 403 returned if unauthorized

**2.2** WHEN a user lists [resources], the system SHALL support filtering and pagination
  - AC 2.2.1: Filter by [field1], [field2], [field3]
  - AC 2.2.2: Sort by [field], ascending/descending
  - AC 2.2.3: Pagination with configurable page size
  - AC 2.2.4: Total count included in response

### 3. Resource Updates

**3.1** WHEN a user updates a [resource], the system SHALL validate and apply changes
  - AC 3.1.1: Partial updates supported
  - AC 3.1.2: Validation applied to changed fields
  - AC 3.1.3: Update timestamp recorded
  - AC 3.1.4: Version/etag updated (if versioned)

**3.2** IF concurrent updates occur, the system SHALL prevent conflicts
  - AC 3.2.1: Optimistic locking via etag/version
  - AC 3.2.2: 409 Conflict returned on version mismatch
  - AC 3.2.3: Client can retry with latest version

### 4. Resource Deletion

**4.1** WHEN a user deletes a [resource], the system SHALL handle it appropriately
  - AC 4.1.1: Soft delete (mark as deleted) OR hard delete (remove permanently)
  - AC 4.1.2: Cascade behavior defined for related resources
  - AC 4.1.3: Deletion timestamp recorded (if soft delete)
  - AC 4.1.4: 404 if already deleted or not found

**4.2** IF deletion would violate constraints, the system SHALL prevent it
  - AC 4.2.1: Foreign key constraints enforced
  - AC 4.2.2: Descriptive error returned
  - AC 4.2.3: Alternative actions suggested (e.g., archive instead)

### 5. Access Control

**5.1** WHERE permissions are required, the system SHALL enforce authorization
  - AC 5.1.1: Read permission for retrieval operations
  - AC 5.1.2: Write permission for create/update operations
  - AC 5.1.3: Delete permission for deletion operations
  - AC 5.1.4: Admin permission for sensitive operations

**5.2** IF user lacks permission, the system SHALL deny access
  - AC 5.2.1: 403 Forbidden returned
  - AC 5.2.2: Required permission indicated in response
  - AC 5.2.3: Audit log entry created

### 6. Data Validation & Constraints

**6.1** WHEN validating data, the system SHALL enforce all constraints
  - AC 6.1.1: Required fields enforced
  - AC 6.1.2: Data type validation (string, number, date, etc.)
  - AC 6.1.3: Format validation (email, URL, phone, etc.)
  - AC 6.1.4: Range validation (min/max length, value ranges)
  - AC 6.1.5: Business rules enforced

### 7. Lifecycle Management

**7.1** WHERE resources have lifecycle states, the system SHALL manage transitions
  - AC 7.1.1: Valid states defined (e.g., draft, active, archived, deleted)
  - AC 7.1.2: Allowed transitions defined
  - AC 7.1.3: Invalid transitions prevented
  - AC 7.1.4: State change history tracked

### 8. Audit & History

**8.1** WHEN resources are modified, the system SHALL log changes
  - AC 8.1.1: Who made the change
  - AC 8.1.2: When the change occurred
  - AC 8.1.3: What was changed (before/after)
  - AC 8.1.4: Audit log queryable

---

## Cross-Domain Examples

**Code - REST API**: User management endpoints (create user, get user, update profile, delete account)

**Documentation - Knowledge Base**: Article management (create article, search, edit, archive)

**Planning - Budget Management**: Expense tracking (add expense, categorize, update, report)

**Scripts - Infrastructure**: Resource provisioning (create VM, query status, update config, destroy)

**Creative - Asset Library**: Design asset management (import asset, tag, organize, export)

---

## Success Criteria

- [ ] All CRUD operations functional
- [ ] Validation comprehensive
- [ ] Access control enforced
- [ ] Audit trail complete
- [ ] Error handling graceful

---

**Generated from Ouroboros Pattern**: Resource Management
**Template Version**: 1.0
**Last Updated**: 2025-10-25
