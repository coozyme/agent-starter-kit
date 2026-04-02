# 🤖 Agent Starter Kit

A general-purpose starter kit for AI coding agents — providing a comprehensive structure for **instructions**, **skills**, **workflows**, **templates**, and **agent configuration** that covers the full end-to-end development lifecycle.

## 📁 Folder Structure

```
agent-starter-kit/
├── agents/                                # Agent configuration
│   └── agent.md                           # Persona, rules, capabilities
├── instructions/                          # Guidelines & standards
│   ├── general.md                         # Coding style, conventions
│   ├── architecture.md                    # Design patterns, folder structure
│   ├── api-design.md                      # RESTful API standards
│   ├── database.md                        # Schema, migrations, queries
│   ├── security.md                        # OWASP, input validation, auth
│   ├── performance.md                     # Profiling, caching, optimization
│   ├── logging-monitoring.md              # Structured logging, alerting
│   ├── code-review.md                     # Review checklist & etiquette
│   ├── git-conventions.md                 # Branching, commits, PR flow
│   └── ai-coding-patterns.md             # AI-assisted coding best practices
├── skills/                                # Skill templates
│   ├── debugging-skill.md                 # Systematic debugging
│   ├── testing-skill.md                   # Testing pyramid, TDD
│   ├── refactoring-skill.md               # Safe refactoring steps
│   ├── api-integration-skill.md           # Building & consuming APIs
│   ├── database-management-skill.md       # Schema design, migrations
│   ├── documentation-skill.md             # Technical writing
│   ├── performance-optimization-skill.md  # Bottleneck resolution
│   ├── security-audit-skill.md            # Security review checklist
│   └── code-generation-skill.md           # Scaffolding & boilerplate
├── workflows/                             # Step-by-step workflows
│   ├── setup-project.md                   # New project initialization
│   ├── feature-development.md             # Feature dev (TDD cycle)
│   ├── bug-fix.md                         # Structured bug fixing
│   ├── code-review.md                     # Code review process
│   ├── deployment.md                      # Build → stage → deploy
│   ├── database-migration.md              # Migration lifecycle
│   ├── release.md                         # Versioning & releases
│   ├── incident-response.md               # Production incident handling
│   └── ai-assisted-development.md         # Full AI dev lifecycle
├── templates/                             # Ready-to-use templates
│   ├── ci-cd.yml                          # CI/CD pipeline (GitHub Actions)
│   ├── dockerfile                         # Multi-stage Dockerfile
│   ├── docker-compose.yml                 # Local dev environment
│   ├── env.example                        # Environment variables
│   ├── pr-template.md                     # Pull request template
│   ├── issue-template.md                  # Issue/bug report template
│   └── adr-template.md                    # Architecture Decision Record
├── .gitignore
└── README.md
```

## 🚀 How to Use

### 1. Clone the Template
```bash
git clone <repository-url> my-project/.agents
# or copy this folder into your project
```

### 2. Customize the Agent
Edit `agents/agent.md` to adjust the agent's persona and rules for your project.

### 3. Add/Edit Instructions
Modify files in `instructions/` to add project-specific guidelines.

### 4. Add Skills
Create a new `<name>-skill.md` file in `skills/` to add new capabilities.

### 5. Add Workflows
Create a new `.md` file in `workflows/` to add project-specific workflows.

### 6. Use Templates
Copy files from `templates/` into your project and customize them.

## 📝 Conventions

| Folder | Purpose | File Naming |
|--------|---------|-------------|
| `instructions/` | Static guidelines that always apply | `<topic>.md` |
| `skills/` | Specific capabilities the agent can invoke | `<name>-skill.md` |
| `workflows/` | Step-by-step procedures for specific tasks | `<action>.md` |
| `templates/` | Ready-to-use project templates | Varies by type |
| `agents/` | Agent identity and behavior config | `agent.md` |

## 🔧 Customization

This template is designed to be flexible. You can:
- Add/remove instructions based on project needs
- Create new skills for specific domains
- Add workflows for custom business processes
- Modify the agent persona in `agents/agent.md`
- Add project-specific templates

## 💬 Contributing & Requests

This is an open-source project — contributions and requests from the community are welcome!

### 🙋 Requesting New Content

Have an idea for a new agent, skill, workflow, or template? Here's how to request it:

1. **Open an Issue** — Go to the [Issues](../../issues) tab and create a new issue
2. **Use the appropriate label**:
   - `request: agent` — Request a new agent configuration (e.g., Database Engineer, Security Auditor)
   - `request: skill` — Request a new skill (e.g., GraphQL, Kubernetes management)
   - `request: workflow` — Request a new workflow (e.g., hotfix process, A/B testing)
   - `request: template` — Request a new template (e.g., Terraform config, K8s manifest)
   - `request: instruction` — Request a new instruction/guideline
3. **Describe your request** — Include:
   - What you need and why it's useful
   - Example use cases
   - Any reference materials or best practices to consider

### 🤝 Contributing Directly

Want to contribute directly? We'd love your help!

1. **Fork** the repository
2. **Create a branch** — `feature/add-<name>-agent` or `feature/add-<name>-skill`
3. **Follow the conventions** — Match the existing file structure and format
4. **Submit a Pull Request** — Use the PR template in `templates/pr-template.md`

#### Contribution Guidelines

- Follow the naming conventions in the [Conventions](#-conventions) table above
- Each file should be **self-contained** and well-documented
- Use best practices and cite references where applicable
- Keep content **language/framework-agnostic** unless it's a specific implementation template
- Test your workflows and templates before submitting

### 💡 Ideas We'd Love to See

Here are some areas where community contributions would be especially valuable:

| Category | Ideas |
|----------|-------|
| **Agents** | Database Engineer, Security Auditor, Performance Engineer, Data Engineer |
| **Skills** | GraphQL, Kubernetes, Terraform, Monitoring setup |
| **Workflows** | Hotfix, A/B testing, Load testing, Disaster recovery |
| **Templates** | Terraform modules, K8s manifests, Monitoring dashboards |

### 📢 Feedback & Discussions

- **Bug reports** → Open an issue with the `bug` label
- **General questions** → Use the [Discussions](../../discussions) tab
- **Feature ideas** → Open an issue with the `enhancement` label

## 📄 License

This project is open-source. See the [LICENSE](LICENSE) file for details.
