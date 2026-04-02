---
description: Workflow for creating and applying database migrations
---

# Database Migration Workflow

Steps for safely creating, reviewing, testing, and applying database migrations.

## Steps

### 1. Plan the Change
- Identify what schema changes are needed
- Consider impact on existing data
- Check for breaking changes to application code
- Follow conventions in `instructions/database.md`

### 2. Generate Migration File
```bash
# Naming format: YYYYMMDDHHMMSS_description
# Example commands by framework:
npx prisma migrate dev --name add_email_to_users    # Prisma
alembic revision -m "add_email_to_users"            # Alembic (Python)
npx sequelize migration:generate --name add-email   # Sequelize
```

### 3. Write Migration
- Write the **up** migration (apply the change)
- Write the **down** migration (rollback the change)
- Keep migrations atomic — one logical change per migration
- Add data transformations if needed

### 4. Test Locally
```bash
# Apply migration
npm run migrate:up

# Verify schema is correct
# Run application tests

# Test rollback
npm run migrate:down

# Re-apply to confirm idempotency
npm run migrate:up
```

### 5. Code Review
- Review the migration SQL/code
- Verify backward compatibility
- Check for potential locks on large tables
- Ensure down migration properly reverses changes

### 6. Apply to Staging
- Run migration on staging environment
- Verify the application works with the new schema
- Test both old and new code paths if doing a phased rollout

### 7. Apply to Production
- Schedule during low-traffic window for large changes
- Backup the database before applying
- Monitor for locks and long-running queries
- Verify the application works after migration

### 8. Post-Migration
- Verify all data integrity constraints
- Update seed files if needed
- Document the change in the changelog
