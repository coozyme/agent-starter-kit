# Git Conventions

Git conventions for maintaining a clean code history and effective collaboration.

## Branch Naming

Format: `<type>/<description>`

| Type | Description | Example |
|------|-------------|---------|
| `feature/` | New feature | `feature/user-authentication` |
| `bugfix/` | Bug fix | `bugfix/login-timeout` |
| `hotfix/` | Urgent production fix | `hotfix/payment-crash` |
| `refactor/` | Code refactoring | `refactor/database-layer` |
| `docs/` | Documentation changes | `docs/api-reference` |
| `test/` | Adding/fixing tests | `test/user-service-coverage` |
| `chore/` | Maintenance tasks | `chore/update-dependencies` |

## Commit Message Format

Following [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Types
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Formatting, missing semicolons, etc. (not CSS)
- `refactor`: Code refactoring
- `perf`: Performance improvement
- `test`: Adding/fixing tests
- `chore`: Build process, dependencies, etc.
- `ci`: CI/CD changes
- `revert`: Revert a previous commit

### Rules
- Subject line maximum 72 characters
- Use imperative mood: "add feature" not "added feature"
- Don't end the subject with a period
- Body explains **what** and **why**, not **how**
- Reference issues/tickets in the footer: `Closes #123`

### Example
```
feat(auth): add JWT token refresh mechanism

Implement automatic token refresh when the access token is about to
expire. The refresh happens 5 minutes before expiration to avoid
interrupted API calls.

Closes #456
```

## Pull Request Flow

### PR Checklist
- [ ] Branch is up-to-date with the target branch
- [ ] All tests pass
- [ ] Code review has been done
- [ ] Documentation is updated (if needed)
- [ ] PR description clearly explains the changes

### PR Title Format
Same as commit message format: `<type>(<scope>): <subject>`

### Merge Strategy
- **Squash merge** for feature branches (clean history)
- **Merge commit** for release branches (preserve history)
- **Rebase** only for personal branches

## Protected Branches

| Branch | Protection | Description |
|--------|-----------|-------------|
| `main` | 🔒 Full | Production-ready code, minimum 1 reviewer |
| `develop` | 🔒 Partial | Integration branch, CI must pass |
| `staging` | 🔒 Partial | Staging environment |
