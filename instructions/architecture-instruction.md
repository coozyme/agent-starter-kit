# Architecture & Design Patterns

Guidelines for structuring applications with clean, maintainable architecture.

## Layered Architecture

Organize code into clear layers with well-defined responsibilities:

```
┌─────────────────────────────┐
│      Presentation Layer     │  ← Controllers, Views, UI
├─────────────────────────────┤
│      Application Layer      │  ← Use cases, orchestration
├─────────────────────────────┤
│        Domain Layer         │  ← Business logic, entities
├─────────────────────────────┤
│     Infrastructure Layer    │  ← Database, external APIs, I/O
└─────────────────────────────┘
```

### Rules
- Dependencies flow **downward** only (upper layers depend on lower layers)
- Domain layer has **zero external dependencies**
- Infrastructure implements interfaces defined by the domain

## Folder Structure Conventions

### Feature-Based (Recommended)
```
src/
├── auth/
│   ├── auth.controller.ts
│   ├── auth.service.ts
│   ├── auth.repository.ts
│   └── auth.test.ts
├── users/
│   ├── users.controller.ts
│   ├── users.service.ts
│   └── users.test.ts
└── shared/
    ├── middleware/
    ├── utils/
    └── types/
```

### Layer-Based (Simple Projects)
```
src/
├── controllers/
├── services/
├── repositories/
├── models/
├── middleware/
└── utils/
```

## Common Design Patterns

### Creational
| Pattern | Use When |
|---------|----------|
| Factory | Object creation logic is complex or varies |
| Builder | Object has many optional parameters |
| Singleton | Exactly one instance is needed (use sparingly) |

### Structural
| Pattern | Use When |
|---------|----------|
| Adapter | Integrating with external APIs or legacy code |
| Facade | Simplifying complex subsystem interfaces |
| Decorator | Adding behavior without modifying existing code |

### Behavioral
| Pattern | Use When |
|---------|----------|
| Strategy | Multiple algorithms can be swapped at runtime |
| Observer | Objects need to react to state changes |
| Command | Actions need to be queued, logged, or undone |

## Architecture Decision Records (ADRs)

Document significant architectural decisions using ADRs:
- **Context**: What is the issue?
- **Decision**: What was decided?
- **Consequences**: What are the trade-offs?

Use the template at `templates/adr-template.md`.

## Anti-Patterns to Avoid

- **God Object**: One class that does everything → Decompose
- **Spaghetti Code**: No clear structure → Apply layered architecture
- **Golden Hammer**: Using one tool for everything → Choose the right tool
- **Premature Abstraction**: Abstracting too early → Wait for patterns to emerge (Rule of Three)
- **Circular Dependencies**: A depends on B depends on A → Introduce interfaces
