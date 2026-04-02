---
description: Workflow for setting up a new project from scratch
---

# Setup Project Workflow

Steps for creating a new project using this template.

## Steps

### 1. Determine Tech Stack
Discuss with the user to determine:
- Primary programming language
- Framework to use
- Database (if needed)
- Package manager

### 2. Initialize the Project
Create a new project based on the chosen tech stack:

```bash
# Example for Node.js
mkdir my-project && cd my-project
npm init -y

# Example for Python
mkdir my-project && cd my-project
python -m venv venv
pip init
```

### 3. Set Up Folder Structure
Create the folder structure following best practices:
```
my-project/
├── src/                 # Source code
├── tests/               # Test files
├── docs/                # Documentation
├── config/              # Configuration files
├── scripts/             # Build/deploy scripts
├── .gitignore
├── README.md
└── package.json / requirements.txt / go.mod
```

### 4. Set Up Git
```bash
git init
git add .
git commit -m "chore: initial project setup"
```

### 5. Configure Linting & Formatting
Set up linting and formatting tools based on the tech stack:
- **JS/TS**: ESLint + Prettier
- **Python**: Ruff / Black + isort
- **Go**: golangci-lint + gofmt

### 6. Set Up Testing Framework
Install and configure the testing framework:
- **JS/TS**: Jest / Vitest
- **Python**: pytest
- **Go**: built-in testing package

### 7. Create README
Write a README.md with:
- Project description
- How to install dependencies
- How to run the project
- How to run tests
- Contributing guidelines

### 8. First Commit
```bash
git add .
git commit -m "chore: project setup complete with linting, testing, and docs"
```
