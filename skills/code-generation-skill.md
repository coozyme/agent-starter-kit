---
name: Code Generation
description: Skill for generating boilerplate, scaffolding, and CRUD code from specifications
---

# Code Generation Skill

Patterns for efficiently generating common code structures.

## When to Use This Skill

- When creating new features with standard patterns (CRUD, forms)
- When scaffolding a new module or service
- When generating boilerplate code
- When creating tests from existing implementations

## Generation Patterns

### 1. CRUD Operations
Generate a complete CRUD module including:
- Model/Entity definition
- Controller with REST endpoints
- Service with business logic
- Repository with data access
- Validation schemas
- Unit tests

### 2. Scaffold a New Module
```
module-name/
├── module-name.controller.ts    # HTTP handlers
├── module-name.service.ts       # Business logic
├── module-name.repository.ts    # Data access
├── module-name.model.ts         # Data model
├── module-name.validation.ts    # Input validation
├── module-name.types.ts         # TypeScript types
└── module-name.test.ts          # Tests
```

### 3. Generate Tests from Code
For any function/class, generate:
- Happy path tests
- Edge case tests (null, empty, boundary values)
- Error case tests
- Integration tests (if applicable)

### 4. Generate API Client
From an API spec or endpoint list, generate:
- Type-safe client functions
- Request/response types
- Error handling
- Retry logic

## Generation Checklist

Before generating code, confirm:
- [ ] Target language and framework
- [ ] Naming conventions to follow
- [ ] Existing patterns to match
- [ ] Required validations
- [ ] Error handling approach
- [ ] Test requirements

## Post-Generation Steps

1. **Review** — Read through all generated code
2. **Customize** — Adjust business logic and validations
3. **Test** — Run generated tests, add missing cases
4. **Integrate** — Wire into the existing application
5. **Document** — Add inline docs and update README
