# AI-Assisted Coding Patterns

Best practices for effective AI-assisted development.

## Context Management

### Provide Clear Context
- Share relevant files, types, and interfaces before asking for code
- Specify the tech stack, framework, and version
- Reference existing patterns: "Follow the pattern in `users.service.ts`"
- Specify constraints: performance requirements, backward compatibility

### Manage Context Window
- Focus on one task at a time
- Provide the minimum necessary context
- Reference files by name rather than pasting entire contents
- Break large tasks into smaller, focused requests

## Effective Prompting for Code

### Task Specification
```
✅ Good: "Create a REST endpoint POST /api/v1/orders that validates the 
   request body using Zod, calls OrderService.create(), and returns 201 
   with the created order. Follow the pattern in users.controller.ts."

❌ Bad: "Create an order endpoint"
```

### Key Elements
1. **What** to build (specific deliverable)
2. **How** it should work (behavior, edge cases)
3. **Where** it fits (file location, referenced patterns)
4. **Constraints** (performance, compatibility, standards)

## Breaking Down Tasks for AI

### Decomposition Strategy
```
Epic → Features → Tasks → Subtasks
```

| Level | Scope | Example |
|-------|-------|---------|
| Epic | Large initiative | Implement authentication system |
| Feature | User-facing capability | Add JWT login |
| Task | Single implement unit | Create auth middleware |
| Subtask | Atomic code change | Add token validation function |

### Optimal Task Size
- Small enough to get right in one shot
- Large enough to be meaningful
- Clear acceptance criteria
- Self-contained (can be tested independently)

## Iterative Refinement

1. **Generate** — Let AI produce initial code
2. **Review** — Check correctness, style, edge cases
3. **Refine** — Ask for specific improvements
4. **Test** — Verify with tests
5. **Integrate** — Merge into the codebase

## Human Checkpoints

Always require human review for:
- Architecture decisions
- Security-critical code
- Database schema changes
- Public API contracts
- Deletion of code or data
- Configuration changes for production

## Anti-Patterns

- ❌ Blindly accepting AI-generated code without review
- ❌ Asking for an entire application in one prompt
- ❌ Not testing AI-generated code
- ❌ Ignoring AI suggestions to simplify
- ❌ Over-specifying implementation details (let AI use its expertise)
