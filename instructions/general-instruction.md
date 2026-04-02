# General Coding Guidelines

General guidelines to follow when writing and modifying code.

## Coding Style

### Naming Conventions
- **Variables & Functions**: Use `camelCase` (JavaScript/TypeScript) or `snake_case` (Python)
- **Classes**: Use `PascalCase`
- **Constants**: Use `UPPER_SNAKE_CASE`
- **Files**: Use `kebab-case` for file names
- **Directories**: Use `kebab-case` for folder names

### Formatting
- Use consistent indentation (2 spaces for JS/TS, 4 spaces for Python)
- Maximum 100 characters per line
- Add a newline at the end of each file
- Remove trailing whitespace

### Comments
- Write comments to explain **why**, not **what**
- Use JSDoc/docstrings for public functions and classes
- Remove commented-out code before committing
- Write TODO comments in this format: `// TODO(name): description`

## Code Quality

### SOLID Principles
1. **Single Responsibility** — Each class/function should have only one responsibility
2. **Open/Closed** — Open for extension, closed for modification
3. **Liskov Substitution** — Subclasses must be substitutable for their parent classes
4. **Interface Segregation** — Don't force implementation of unused interfaces
5. **Dependency Inversion** — Depend on abstractions, not concrete implementations

### DRY (Don't Repeat Yourself)
- Extract duplicate code into shared functions/utilities
- Use constants for magic numbers and strings
- Create reusable components for recurring patterns

### KISS (Keep It Simple, Stupid)
- Choose the simplest solution that works
- Avoid over-engineering and premature optimization
- If logic is too complex, break it down into smaller functions

## Error Handling

```
✅ DO:
- Handle specific errors, not catch-all
- Provide clear and actionable error messages
- Log errors with enough context for debugging
- Use custom error classes when needed

❌ DON'T:
- Ignore errors with empty catch blocks
- Expose stack traces to end-users
- Use error handling for flow control
- Catch errors too broadly (catch Exception)
```

## File Organization

- Group files by feature/domain, not by file type
- Place tests close to the source code being tested
- Separate configuration from business logic
- Use barrel files (index) for clean exports

## Dependencies

- Prefer the standard library before adding external dependencies
- Pin dependency versions in lock files
- Review changelogs before upgrading major versions
- Audit dependencies regularly for security vulnerabilities
