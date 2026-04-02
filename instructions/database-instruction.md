# Database Conventions

Guidelines for database design, schema management, and query optimization.

## Schema Design

### Naming Conventions
- **Tables**: `snake_case`, plural → `users`, `order_items`
- **Columns**: `snake_case` → `first_name`, `created_at`
- **Primary Keys**: `id` (auto-increment or UUID)
- **Foreign Keys**: `<table_singular>_id` → `user_id`, `order_id`
- **Indexes**: `idx_<table>_<columns>` → `idx_users_email`
- **Timestamps**: Always include `created_at` and `updated_at`

### Standard Columns
Every table should have:
```sql
id            BIGINT PRIMARY KEY AUTO_INCREMENT,
created_at    TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
updated_at    TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
```

### Soft Deletes
For data that should not be permanently removed:
```sql
deleted_at    TIMESTAMP NULL DEFAULT NULL
```

## Relationships

| Type | Implementation |
|------|---------------|
| One-to-One | Foreign key with UNIQUE constraint |
| One-to-Many | Foreign key on the "many" side |
| Many-to-Many | Junction/pivot table |

## Migrations

### Rules
- Migrations are **forward-only** in production
- Each migration has an **up** and **down** method
- Never edit existing migrations — create new ones
- Keep migrations small and focused
- Test migrations on a copy of production data
- Name format: `YYYYMMDDHHMMSS_description.sql`

### Example
```sql
-- 20250315120000_add_email_to_users.sql

-- Up
ALTER TABLE users ADD COLUMN email VARCHAR(255) UNIQUE;

-- Down
ALTER TABLE users DROP COLUMN email;
```

## Query Optimization

### Indexing Rules
- Index columns used in `WHERE`, `JOIN`, `ORDER BY`
- Index foreign key columns
- Use composite indexes for multi-column queries
- Don't over-index — each index slows writes

### Common Pitfalls
- ❌ `SELECT *` → ✅ Select only needed columns
- ❌ N+1 queries → ✅ Use JOINs or eager loading
- ❌ No indexes on frequently queried columns → ✅ Add targeted indexes
- ❌ Large `IN` clauses → ✅ Use JOINs or temp tables
- ❌ Missing pagination → ✅ Always paginate list queries

## ORM Best Practices

- Use migrations, not auto-sync in production
- Prefer explicit queries over lazy loading
- Use transactions for multi-step operations
- Log slow queries for monitoring
- Use connection pooling for performance
