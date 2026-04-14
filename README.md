# GitHub Agent Plugin Marketplace

A proof-of-concept repository demonstrating the building blocks used to create **VS Code Agent Plugins** powered by GitHub Copilot.

This repo does **not** contain the plugins themselves – it contains the reusable sample assets (skills, agents, instructions, and prompt files) that plugins are built from.

---

## Repository Structure

```
.
├── .github/
│   ├── copilot-instructions.md   # Workspace-level custom instructions for Copilot
│   └── prompts/                  # Reusable prompt files (.prompt.md)
│       ├── code-review.prompt.md
│       ├── debug-issue.prompt.md
│       ├── generate-unit-tests.prompt.md
│       ├── refactor-code.prompt.md
│       └── write-documentation.prompt.md
├── agents/                       # Custom agent definitions
│   ├── security-analyst.md
│   ├── senior-code-reviewer.md
│   ├── tech-writer.md
│   └── test-engineer.md
├── instructions/                 # Reusable instruction sets
│   ├── coding-standards.md
│   ├── documentation-standards.md
│   ├── security-guidelines.md
│   └── testing-standards.md
└── skills/                       # Skill definitions
    ├── code-analysis.md
    ├── file-operations.md
    ├── run-tests.md
    └── web-search.md
```

---

## Asset Types

### 🧠 Custom Instructions (`.github/copilot-instructions.md`)

Workspace-level instructions that Copilot automatically picks up and applies to all interactions in this repository. Use these to enforce project-wide standards around language use, testing, security, and style.

→ See [`.github/copilot-instructions.md`](.github/copilot-instructions.md)

---

### 💬 Prompt Files (`.github/prompts/`)

Reusable `.prompt.md` files that guide Copilot Chat (or an agent) through a specific workflow. Open a prompt file in VS Code and use it directly in Copilot Chat, or reference it from an agent plugin.

| File | Purpose |
|------|---------|
| `code-review.prompt.md` | Structured code review with severity-rated findings |
| `debug-issue.prompt.md` | Step-by-step root cause analysis and fix |
| `generate-unit-tests.prompt.md` | Generates comprehensive, isolated unit tests |
| `refactor-code.prompt.md` | Improves design without changing behaviour |
| `write-documentation.prompt.md` | Creates inline docs, READMEs, and API references |

---

### 🤖 Agents (`agents/`)

Definitions for specialised AI agents, each with a distinct persona, set of skills, and system prompt template. These serve as blueprints for building agent plugins.

| Agent | Role |
|-------|------|
| `senior-code-reviewer.md` | Reviews code for correctness, design, and security |
| `test-engineer.md` | Generates and improves automated test suites |
| `tech-writer.md` | Produces clear, accurate technical documentation |
| `security-analyst.md` | Identifies vulnerabilities and recommends remediations |

---

### 📋 Instructions (`instructions/`)

Standalone instruction documents that can be embedded into an agent's system prompt or referenced from a prompt file to provide focused domain guidance.

| File | Contents |
|------|----------|
| `coding-standards.md` | Naming, function design, error handling, and commit hygiene |
| `security-guidelines.md` | Secrets, input validation, auth, cryptography, and dependencies |
| `testing-standards.md` | Frameworks, coverage targets, isolation, and anti-patterns |
| `documentation-standards.md` | Doc-comment formats, README structure, ADRs, and writing style |

---

### 🔧 Skills (`skills/`)

Capability definitions that describe what an agent plugin *can do*. Each skill file documents the capability, inputs, outputs, and configuration YAML needed to register the skill in an agent manifest.

| Skill | Capability |
|-------|-----------|
| `code-analysis.md` | Static analysis for quality, complexity, and style |
| `file-operations.md` | Read, write, move, and search workspace files |
| `run-tests.md` | Execute the test suite and report results and coverage |
| `web-search.md` | Query the web for documentation, errors, and advisories |

---

## Getting Started

1. **Clone the repo** and open it in VS Code.
2. Copilot will automatically load `.github/copilot-instructions.md` as workspace instructions.
3. Open any file in `.github/prompts/` and use it in **Copilot Chat** (`Ctrl+Shift+I` / `Cmd+Shift+I`).
4. Use the `agents/` and `skills/` definitions as blueprints when building your own agent plugins.
5. Embed instruction files from `instructions/` into custom agent system prompts to tune behaviour.

---

## Contributing

Contributions of new skills, agents, prompt files, and instruction sets are welcome. Please open a pull request with a clear description of what the new asset does and how it should be used.
