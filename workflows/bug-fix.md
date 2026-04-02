---
description: Workflow for fixing bugs in a structured manner
---

# Bug Fix Workflow

Steps for identifying, fixing, and validating bugs.

## Steps

### 1. Reproduce the Bug
- Understand the error/bug report from the user or logs
- Identify the exact steps to reproduce
- Record the error message and stack trace
- Determine severity and urgency

### 2. Create Branch
```bash
# Use bugfix/ for regular bugs, hotfix/ for urgent production issues
git checkout -b bugfix/<bug-description>
```

### 3. Write a Failing Test
- Write a test that reproduces the bug
- The test should **fail** at this point (proving the bug exists)
- This becomes a safety net to prevent the bug from returning

### 4. Debug & Identify Root Cause
- Follow the steps in `skills/debugging/SKILL.md`
- Trace the data flow to the problem point
- Identify the root cause, not just the symptom
- Document your findings

### 5. Implement the Fix
- Create a fix that addresses the root cause
- Keep the fix minimal and focused
- Don't mix the fix with refactoring or new features

### 6. Verify the Fix
```bash
# Run the previously failing test — it should now pass
npm test -- --grep "bug-description"

# Run the full test suite to check for regressions
npm test
```

### 7. Test Edge Cases
- Test variations of the condition that caused the bug
- Check if the bug could occur elsewhere
- Add edge case tests if needed

### 8. Create Pull Request
- Create a PR with:
  - Bug description
  - Root cause analysis
  - Solution implemented
  - Reference to the issue/ticket

### 9. Close Issue
- Merge the PR after review
- Verify the fix on staging/production
- Close the related issue/ticket
- Notify the reporter that the bug has been fixed
