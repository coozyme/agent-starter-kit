---
name: Refactoring
description: Skill for performing safe and structured code refactoring
---

# Refactoring Skill

Guidelines for refactoring code without breaking existing functionality.

## When to Use This Skill

- When code is hard to understand or maintain
- When there are code smells that need to be addressed
- When adding new features is hindered by existing code
- After a code review requests structural changes

## Golden Rule of Refactoring

> **Don't change behavior!** Refactoring only changes internal structure, not the output/behavior of the code.

## Refactoring Steps

### 1. Ensure Tests Exist
- Run existing tests — they must all **pass**
- If there are no tests, write tests first before refactoring
- Tests are the safety net that ensures behavior doesn't change

### 2. Make Small Changes
- Refactor incrementally, not all at once
- Commit each small successful change
- If something goes wrong, it's easy to revert

### 3. Run Tests After Every Change
- After each refactoring step, run the tests
- If tests fail, revert and try again
- Don't proceed to the next step until tests pass

### 4. Review and Commit
- Review the changes as a whole
- Ensure the code is cleaner/more readable than before
- Commit with a clear message

## Common Code Smells & Fixes

| Code Smell | Refactoring Solution |
|-----------|---------------------|
| **Long Function** | Extract Method — break into smaller functions |
| **Duplicate Code** | Extract Function/Class — create shared utility |
| **Large Class** | Extract Class — separate responsibilities |
| **Long Parameter List** | Introduce Parameter Object |
| **Feature Envy** | Move Method — move to the more appropriate class |
| **God Object** | Decompose — break into multiple classes |
| **Magic Numbers** | Replace with Named Constant |
| **Nested Conditionals** | Replace with Guard Clauses |
| **Dead Code** | Remove — delete unused code |

## Refactoring Techniques

### Extract Function
```
BEFORE: One long function doing many things
AFTER: Several small functions with descriptive names
```

### Rename
```
BEFORE: const d = getData()
AFTER: const userProfile = fetchUserProfile()
```

### Move
```
BEFORE: Utility function inside a specific module
AFTER: Utility function in shared utils
```

### Replace Conditional with Polymorphism
```
BEFORE: Long if/else or switch-case
AFTER: Strategy pattern or polymorphism
```

## Safety Checklist

- [ ] All existing tests pass before starting
- [ ] Refactoring is done in small steps
- [ ] Tests are run after each step
- [ ] No behavior changes (structure only)
- [ ] New code is more readable than before
- [ ] Dependencies are not broken
- [ ] PR contains only refactoring (no mixed feature additions)
