# Code Review Guidelines

Standards and checklist for conducting effective code reviews.

## Review Checklist

### ✅ Correctness
- [ ] Code does what it is intended to do
- [ ] Edge cases are handled
- [ ] Error handling is proper
- [ ] No race conditions or concurrency issues

### ✅ Readability
- [ ] Variable/function names are descriptive and clear
- [ ] Logic is easy to understand without excessive comments
- [ ] No dead code or commented-out code
- [ ] Formatting is consistent with the codebase

### ✅ Performance
- [ ] No obvious performance bottlenecks
- [ ] Database queries are optimized (avoid N+1)
- [ ] No memory leaks
- [ ] Caching is used where appropriate

### ✅ Security
- [ ] Input validation is in place
- [ ] No hardcoded secrets/credentials
- [ ] SQL injection/XSS is prevented
- [ ] Authentication/authorization is correct

### ✅ Testing
- [ ] Unit tests are added for new logic
- [ ] Edge cases are tested
- [ ] Tests are meaningful and not just increasing coverage
- [ ] Integration tests are included if needed

### ✅ Architecture
- [ ] Changes align with existing architecture
- [ ] No breaking changes without documentation
- [ ] New dependencies have been reviewed
- [ ] API contracts are maintained

## Review Etiquette

### As a Reviewer
- Focus on the code, not the person
- Give concrete suggestions, not just criticism
- Distinguish between "must fix" vs "nice to have"
- Appreciate good code as well

### As an Author
- Include enough context in the PR description
- Respond to every review comment
- Don't take it personally
- Accept feedback with an open mind

## Severity Levels

| Level | Label | Description |
|-------|-------|-------------|
| 🔴 | **Blocker** | Must be fixed before merge (bug, security issue) |
| 🟡 | **Suggestion** | Should be fixed but not blocking |
| 🟢 | **Nit** | Minor style/preference, optional |
| 💡 | **Idea** | Idea for future improvement |
