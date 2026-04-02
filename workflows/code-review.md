---
description: Workflow for performing a systematic code review
---

# Code Review Workflow

Steps for conducting a thorough and constructive code review.

## Steps

### 1. Understand Context
- Read the PR title and description
- Understand the purpose of the changes
- Check linked issues/tickets for context
- Check if there was any prior discussion

### 2. High-Level Review
- Does the overall approach make sense?
- Does the architecture align with the existing one?
- Is there a better alternative?
- Is the scope of changes reasonable?

### 3. Detailed Code Review
Follow the checklist in `instructions/code-review.md`:
- Correctness
- Readability
- Performance
- Security
- Testing

### 4. Run Tests Locally (if needed)
```bash
# Checkout the PR branch
git checkout <pr-branch>

# Install dependencies
npm install

# Run tests
npm test
```

### 5. Provide Feedback
Use severity labels:
- 🔴 **Blocker**: Must fix before merge
- 🟡 **Suggestion**: Should fix but not blocking
- 🟢 **Nit**: Optional style preference
- 💡 **Idea**: Future improvement suggestion

### 6. Follow Up
- Review the requested changes
- Approve if all blockers have been addressed
- Merge or delegate merge to the author
