---
name: API Integration
description: Skill for designing, implementing, and integrating APIs
---

# API Integration Skill

Guidelines for building APIs and integrating with external services.

## When to Use This Skill

- When creating a new API endpoint
- When integrating with third-party APIs
- When refactoring existing API architecture

## Building an API Endpoint

### 1. Define the Contract
- Determine the HTTP method and URL path
- Define request/response schemas
- Follow standards in `instructions/api-design.md`

### 2. Implement the Layers
```
Route → Middleware → Controller → Service → Repository → Database
```

- **Route**: Define URL and HTTP method
- **Middleware**: Auth, validation, rate limiting
- **Controller**: Parse request, call service, format response
- **Service**: Business logic
- **Repository**: Data access

### 3. Add Validation
- Validate request body, query params, and path params
- Return `400` with specific error details on invalid input
- Use schema validation libraries (Joi, Zod, Pydantic)

### 4. Handle Errors
- Return appropriate HTTP status codes
- Use consistent error response format
- Log errors with context for debugging
- Never expose internal details in error responses

### 5. Write Tests
- Unit test the service layer
- Integration test the full request cycle
- Test error cases and edge cases

## Integrating with External APIs

### Best Practices
- **Wrap in a service**: Create a dedicated service class for each external API
- **Use timeouts**: Always set request timeouts (default: 10s)
- **Retry with backoff**: Implement exponential backoff for transient failures
- **Circuit breaker**: Prevent cascading failures when external service is down
- **Cache responses**: Cache GET responses where appropriate
- **Log requests/responses**: Log for debugging (sanitize sensitive data)

### Error Handling for External APIs
```
Timeout          → Retry with backoff, then fallback
4xx Client Error → Log, don't retry, return appropriate error
5xx Server Error → Retry with backoff, then circuit break
Network Error    → Retry with backoff, then fallback
```

### API Key Management
- Store API keys in environment variables
- Never hardcode or commit API keys
- Use different keys per environment
- Rotate keys periodically
