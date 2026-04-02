---
name: Debugging
description: Skill for performing systematic and effective debugging
---

# Debugging Skill

Systematic steps for identifying and fixing bugs in the codebase.

## When to Use This Skill

- When there is an error or unexpected behavior
- When tests fail and the cause is unclear
- When there is a performance issue to investigate

## Debugging Steps

### 1. Reproduce the Bug
- Identify the exact steps to reproduce the bug
- Record error messages, stack traces, and relevant logs
- Determine whether the bug is consistent or intermittent

### 2. Isolate the Problem
- Use a binary search approach: narrow down the problematic code area
- Check recent changes that may have caused the bug (git log/blame)
- Determine whether the bug is in the input, logic, or output

### 3. Understand the Root Cause
- Read the code around the problematic area
- Trace the data flow from start to the error point
- Check for incorrect assumptions

### 4. Develop a Fix
- Create a fix that addresses the root cause, not just the symptom
- Ensure the fix doesn't break other functionality
- Write tests that validate the fix

### 5. Test the Fix
- Run the tests that previously failed
- Run regression tests
- Test related edge cases

### 6. Document
- Record the root cause and fix in the commit message
- Update documentation if needed
- Add comments in the code if the logic is non-obvious

## Debugging Tools & Techniques

| Technique | When to Use |
|-----------|-------------|
| Print/Log debugging | Quick check of execution flow |
| Breakpoint debugging | Inspect state in detail |
| Git bisect | Find the commit that introduced the bug |
| Rubber duck debugging | When stuck, explain the problem verbally |
| Minimal reproduction | Isolate the bug in a minimal environment |

## Common Debugging Patterns

### "It works on my machine"
- Check environment variables
- Check dependency versions
- Check OS-specific behavior

### Off-by-one errors
- Check boundary conditions
- Check indexing (0-based vs 1-based)
- Check loop conditions (< vs <=)

### Null/undefined errors
- Trace the data flow to the null source
- Add null checks at boundaries
- Use optional chaining/null coalescing
