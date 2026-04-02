---
name: Database Management
description: Skill for schema design, migrations, and query optimization
---

# Database Management Skill

Guidelines for managing database schemas, migrations, and data operations.

## When to Use This Skill

- When designing a new database schema
- When creating or applying migrations
- When optimizing slow queries
- When setting up data seeding for development/testing

## Schema Design Process

### 1. Identify Entities
- List all entities from the requirements
- Define attributes for each entity
- Identify relationships (1:1, 1:N, N:M)

### 2. Normalize
- Apply normalization rules (at least 3NF)
- Denormalize strategically for read performance
- Document denormalization decisions

### 3. Define Constraints
- Primary keys, foreign keys, unique constraints
- NOT NULL where appropriate
- Default values
- Check constraints for data integrity

### 4. Plan Indexes
- Index foreign keys
- Index columns used in WHERE/ORDER BY/GROUP BY
- Consider composite indexes for multi-column queries
- Balance read speed vs write overhead

## Migration Workflow

### Creating a Migration
1. Generate migration file with timestamp
2. Write the `up` migration (apply change)
3. Write the `down` migration (rollback)
4. Test both directions locally
5. Review before applying to staging/production

### Safety Rules
- Never modify existing migrations that have been applied
- Always backup before running migrations in production
- Test on a copy of production data first
- Run migrations in a maintenance window for large tables
- Monitor for locks and long-running queries

## Query Optimization Steps

1. **Identify slow queries** — Use slow query logs or monitoring
2. **Analyze with EXPLAIN** — Understand the query execution plan
3. **Add missing indexes** — Based on EXPLAIN output
4. **Optimize the query** — Rewrite JOINs, reduce subqueries
5. **Test performance** — Benchmark before and after
6. **Monitor** — Continue tracking after deployment

## Data Seeding

- Create seed files for development and testing
- Use realistic but fake data (never production data)
- Make seeding idempotent (re-runnable without duplicates)
- Include seed data for all edge cases
