---
name: Security Audit
description: Skill for performing systematic security reviews
---

# Security Audit Skill

Systematic approach to reviewing application security.

## When to Use This Skill

- Before major releases
- After adding new authentication/authorization features
- When integrating with third-party services
- During regular security review cycles

## Security Audit Process

### 1. Authentication Review
- [ ] Are all endpoints properly authenticated?
- [ ] Are passwords hashed with a strong algorithm (bcrypt/argon2)?
- [ ] Is token expiration implemented?
- [ ] Is session management secure?
- [ ] Is MFA available for sensitive operations?

### 2. Authorization Review
- [ ] Are permissions checked server-side on every request?
- [ ] Is principle of least privilege enforced?
- [ ] Can users access other users' data? (IDOR check)
- [ ] Are admin endpoints properly protected?

### 3. Input Validation Review
- [ ] Is all user input validated server-side?
- [ ] Are SQL queries parameterized?
- [ ] Is output properly encoded/escaped? (XSS prevention)
- [ ] Are file uploads validated (type, size, content)?
- [ ] Are redirects validated against an allowlist?

### 4. Data Protection Review
- [ ] Is sensitive data encrypted at rest?
- [ ] Is TLS/HTTPS enforced?
- [ ] Are secrets stored in environment variables or a vault?
- [ ] Is sensitive data masked in logs?
- [ ] Are backup and recovery procedures in place?

### 5. Dependency Review
```bash
# Run dependency audit
npm audit           # Node.js
pip-audit           # Python
snyk test           # Multi-language
```
- [ ] Are all dependencies up-to-date?
- [ ] Are there known vulnerabilities?
- [ ] Are unused dependencies removed?

### 6. Infrastructure Review
- [ ] Are default credentials changed?
- [ ] Are unnecessary services/ports disabled?
- [ ] Are error messages generic (no internal details leaked)?
- [ ] Is rate limiting implemented?
- [ ] Are CORS policies properly configured?

## Reporting
Document findings with:
- **Severity**: Critical / High / Medium / Low
- **Description**: What the vulnerability is
- **Impact**: What could happen if exploited
- **Remediation**: How to fix it
- **Priority**: When to fix it
