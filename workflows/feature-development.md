---
description: Workflow for developing a new feature end-to-end
---

# Feature Development Workflow

Steps for implementing a new feature from start to finish.

## Steps

### 1. Understand Requirements
- Read and understand the feature specification from the user
- Identify acceptance criteria
- Ask for clarification if there is ambiguity
- Note edge cases and constraints

### 2. Plan Implementation
- Identify files that need to be changed/created
- Determine the implementation order (dependency order)
- Consider backward compatibility
- Create an implementation plan if complex

### 3. Create Branch
```bash
git checkout -b feature/<feature-name>
```

### 4. Write Tests First (TDD Approach)
- Write tests based on acceptance criteria
- Tests should fail at this stage (red phase)
- Tests should cover the happy path and edge cases

### 5. Implement Feature
- Write the minimal code to make tests pass (green phase)
- Follow coding guidelines in `instructions/general.md`
- Commit regularly with clear messages

### 6. Refactor
- Clean up the code without changing behavior
- Follow the guide in `skills/refactoring/SKILL.md`
- Ensure tests still pass after refactoring

### 7. Run Full Test Suite
```bash
# Run all tests to ensure no regressions
npm test        # or pytest / go test ./...
```

### 8. Update Documentation
- Update README if there are new user-facing features
- Update API docs if there are new endpoints
- Add comments/docstrings to new code

### 9. Create Pull Request
- Push the branch to remote
- Create a PR with a clear description
- Follow the PR format in `instructions/git-conventions.md`
- Request a code review

### 10. Address Review Feedback
- Respond to every review comment
- Make requested changes
- Re-request review after changes are complete

### 11. Merge
- Squash merge to the target branch
- Delete the feature branch after merge
- Verify on staging/production
