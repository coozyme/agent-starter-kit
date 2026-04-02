# Security Guidelines

Comprehensive security practices for application development.

## OWASP Top 10 — Quick Reference

| # | Risk | Prevention |
|---|------|-----------|
| 1 | Broken Access Control | Enforce least privilege, deny by default |
| 2 | Cryptographic Failures | Use strong encryption, never roll your own crypto |
| 3 | Injection | Parameterized queries, input validation |
| 4 | Insecure Design | Threat modeling, secure design patterns |
| 5 | Security Misconfiguration | Harden defaults, disable unused features |
| 6 | Vulnerable Components | Audit dependencies, keep updated |
| 7 | Auth Failures | MFA, strong password policies, rate limiting |
| 8 | Data Integrity Failures | Verify signatures, use trusted pipelines |
| 9 | Logging Failures | Log security events, monitor for anomalies |
| 10 | SSRF | Validate URLs, restrict outbound requests |

## Input Validation

```
✅ DO:
- Validate on both client AND server side
- Use allowlists over denylists
- Validate data type, length, range, and format
- Sanitize HTML output to prevent XSS
- Use parameterized queries for all database operations

❌ DON'T:
- Trust any user input (including headers, cookies, query params)
- Use string concatenation for SQL queries
- Render unsanitized user input in HTML
```

## Authentication & Authorization

### Authentication
- Use industry-standard protocols (OAuth 2.0, OpenID Connect)
- Hash passwords with bcrypt/argon2 (never MD5/SHA1)
- Implement account lockout after failed attempts
- Use short-lived access tokens + refresh tokens
- Enforce MFA for sensitive operations

### Authorization
- Implement role-based access control (RBAC)
- Check permissions on every request (server-side)
- Never rely on client-side authorization
- Use middleware for consistent enforcement

## Secrets Management

- ❌ Never hardcode secrets in source code
- ❌ Never commit `.env` files to version control
- ✅ Use environment variables for configuration
- ✅ Use secret management tools (Vault, AWS Secrets Manager)
- ✅ Rotate secrets regularly
- ✅ Use different secrets per environment

## Dependency Security

```bash
# Audit dependencies regularly
npm audit                  # Node.js
pip-audit                  # Python
snyk test                  # Multi-language
```

- Pin dependency versions
- Review changelogs on updates
- Remove unused dependencies
- Monitor for CVE notifications

## Data Protection

- Encrypt sensitive data at rest and in transit
- Use TLS/HTTPS for all communications
- Mask sensitive data in logs (emails, IPs, tokens)
- Implement data retention and deletion policies
- Comply with relevant regulations (GDPR, CCPA)
