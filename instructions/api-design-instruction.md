# API Design Standards

Guidelines for designing consistent, maintainable, and developer-friendly APIs.

## RESTful Conventions

### URL Structure
```
GET    /api/v1/users          # List users
GET    /api/v1/users/:id      # Get a single user
POST   /api/v1/users          # Create a user
PUT    /api/v1/users/:id      # Full update a user
PATCH  /api/v1/users/:id      # Partial update a user
DELETE /api/v1/users/:id      # Delete a user
```

### Naming Rules
- Use **plural nouns** for resources: `/users`, not `/user`
- Use **kebab-case** for multi-word resources: `/order-items`
- Use **query parameters** for filtering: `/users?role=admin&active=true`
- Nest related resources: `/users/:id/orders`
- Maximum **3 levels** of nesting

### HTTP Methods
| Method | Purpose | Idempotent | Safe |
|--------|---------|------------|------|
| GET | Read | ✅ | ✅ |
| POST | Create | ❌ | ❌ |
| PUT | Full Replace | ✅ | ❌ |
| PATCH | Partial Update | ❌ | ❌ |
| DELETE | Remove | ✅ | ❌ |

## Response Format

### Success Response
```json
{
  "data": { ... },
  "meta": {
    "page": 1,
    "per_page": 20,
    "total": 150
  }
}
```

### Error Response
```json
{
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid input data",
    "details": [
      { "field": "email", "message": "Must be a valid email address" }
    ]
  }
}
```

## HTTP Status Codes

| Code | Meaning | When to Use |
|------|---------|-------------|
| 200 | OK | Successful GET, PUT, PATCH |
| 201 | Created | Successful POST |
| 204 | No Content | Successful DELETE |
| 400 | Bad Request | Validation error, malformed request |
| 401 | Unauthorized | Missing or invalid authentication |
| 403 | Forbidden | Authenticated but not authorized |
| 404 | Not Found | Resource doesn't exist |
| 409 | Conflict | Duplicate resource, state conflict |
| 422 | Unprocessable Entity | Semantically invalid input |
| 429 | Too Many Requests | Rate limit exceeded |
| 500 | Internal Server Error | Unexpected server error |

## Versioning

- Use **URL versioning**: `/api/v1/users`
- Increment major version for breaking changes
- Support previous version for a deprecation period
- Document deprecation timeline

## Pagination

```
GET /api/v1/users?page=2&per_page=20
```

Response includes meta:
```json
{
  "meta": {
    "page": 2,
    "per_page": 20,
    "total": 150,
    "total_pages": 8
  }
}
```

## Authentication

- Use **Bearer tokens** for API authentication
- Return `401` for missing/invalid tokens
- Return `403` for insufficient permissions
- Never expose tokens in URLs or logs
