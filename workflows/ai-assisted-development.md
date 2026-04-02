---
description: Workflow for full AI-assisted development lifecycle
---

# AI-Assisted Development Workflow

End-to-end workflow for building features with AI coding assistance, with human checkpoints at critical stages.

## Steps

### 1. 📋 Specification (Human)
- Define the feature requirements clearly
- Write acceptance criteria
- Identify constraints (performance, security, compatibility)
- Provide reference to existing patterns

### 2. 🤖 Planning (AI + Human Review)
- AI creates an implementation plan
- Lists files to create/modify
- Identifies dependencies and risks
- **🔍 Human checkpoint**: Review and approve the plan

### 3. 🤖 Architecture (AI + Human Review)
- AI proposes architecture and data models
- Defines interfaces and contracts
- Identifies integration points
- **🔍 Human checkpoint**: Review architecture decisions

### 4. 🤖 Test Specification (AI)
- AI writes test cases based on acceptance criteria
- Covers happy path, edge cases, and errors
- Tests should fail initially (TDD red phase)

### 5. 🤖 Implementation (AI)
- AI implements the feature following the plan
- Follows coding guidelines in `instructions/`
- Uses relevant skills from `skills/`
- Makes incremental, testable changes

### 6. 🔍 Code Review (Human)
- Review all generated code
- Check for correctness, security, and performance
- Verify coding standards compliance
- Request changes if needed → AI iterates

### 7. 🤖 Testing (AI + Human)
- AI runs all tests and fixes failures
- AI adds missing test cases
- Human verifies test coverage is adequate

### 8. 🤖 Documentation (AI)
- AI updates docs, README, and inline comments
- AI generates changelog entry
- Human reviews documentation accuracy

### 9. 🚀 Deployment (Human-Approved)
- Follow `workflows/deployment.md`
- **🔍 Human checkpoint**: Approve production deployment
- Monitor post-deployment metrics

## Flow Diagram

```
Spec (Human)
    ↓
Plan (AI) → Review (Human) → Approved? → No → Revise
    ↓ Yes
Architect (AI) → Review (Human) → Approved? → No → Revise
    ↓ Yes
Write Tests (AI)
    ↓
Implement (AI)
    ↓
Code Review (Human) → Changes needed? → Yes → Iterate (AI)
    ↓ No
Test & Fix (AI)
    ↓
Document (AI)
    ↓
Deploy (Human Approved)
```

## Key Principles

1. **AI generates, humans validate** — AI does the heavy lifting, humans ensure quality
2. **Plan before code** — Always start with a reviewed plan
3. **Test everything** — AI-generated code must be tested
4. **Iterate quickly** — Small changes, fast feedback loops
5. **Document decisions** — Use ADRs for significant choices
