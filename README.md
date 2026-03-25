# AgentSkills

A curated library of domain-specific **skills** for AI coding assistants — Claude and Gemini. Each skill is a structured set of behavioral instructions, code examples, and reference guides that guide AI assistants to produce high-quality, production-ready code following established best practices.

---

## What Is a Skill?

A skill is a markdown-based instruction set (optionally with a `skill.yaml` config) that an AI agent loads when helping with a specific domain. When activated, a skill tells the assistant:

- What principles to follow (e.g., SOLID, TDD)
- What tools/libraries to use (e.g., `mypy --strict`, `pytest`)
- What patterns to apply or avoid
- How to approach problems step-by-step

Skills are **not executable code** — they are knowledge and behavioral guidelines consumed by AI agents.

---

## Repository Structure

```
AgentSkills/
├── .claude/                    # Skills for Claude (Anthropic)
│   ├── .claudeignore
│   └── skills/
│       ├── architecture.md             # High-level software architecture
│       ├── debugging-wizard/           # Bug diagnosis & root cause analysis
│       ├── devops-engineer/            # CI/CD, Docker, Kubernetes, Terraform
│       ├── fastapi-expert/             # Async Python APIs with FastAPI & Pydantic V2
│       ├── postgres-pro/               # PostgreSQL optimization & administration
│       ├── python-architecture/        # SOLID principles, dependency injection
│       ├── python-patterns/            # Pythonic idioms & PEP 8 best practices
│       ├── python-pro/                 # Modern Python 3.11+ with type safety
│       ├── python-testing/             # pytest, TDD, fixtures, mocking, coverage
│       └── python-typing/              # Strict type hints & mypy
│
└── .gemini/                    # Skills for Gemini (Google)
    ├── .geminiignore
    └── skills/
        ├── python-architecture/        # SOLID principles, testable design
        ├── python-clean-code/          # Code clarity, readability, naming
        ├── python-performance/         # Optimization, Big-O, profiling
        └── python-typing/              # Strict typing, mypy compatibility
```

Each skill folder typically contains:

- `SKILL.md` — the main instruction set, loaded when the skill is activated
- `skill.yaml` *(optional)* — skill metadata (name, description, version)
- `references/` *(optional)* — deep-dive reference guides on specific subtopics

---

## Skills Reference

### Claude Skills (`.claude/skills/`)

| Skill | Description |
|-------|-------------|
| `architecture.md` | Expert guidance on software architecture: SOLID, clean design, separation of concerns |
| `debugging-wizard/` | Systematic bug diagnosis — parsing errors, tracing stack traces, root cause analysis |
| `devops-engineer/` | CI/CD pipelines, Docker, Kubernetes, Terraform, Helm, GitOps, incident response |
| `fastapi-expert/` | FastAPI endpoints, Pydantic V2 models, async SQLAlchemy, JWT auth, OpenAPI docs |
| `postgres-pro/` | EXPLAIN ANALYZE, index tuning, JSONB, replication, VACUUM, extensions |
| `python-architecture/` | SOLID, dependency injection, composition over inheritance, testability |
| `python-patterns/` | Pythonic idioms, context managers, comprehensions, decorators, concurrency |
| `python-pro/` | Modern Python 3.11+, type-safe and async-first, strict mypy, pytest >90% coverage |
| `python-testing/` | TDD (red-green-refactor), pytest fixtures, parametrize, mocking, async tests |
| `python-typing/` | Full type hints on all functions, mypy `--strict`, no implicit `Any` |

#### Reference Guides

Many skills include a `references/` folder with detailed topic-specific guides:

| Skill | Reference Guides |
|-------|-----------------|
| `debugging-wizard/` | debugging-tools, common-patterns, strategies, quick-fixes, systematic-debugging |
| `devops-engineer/` | ci-cd-pipelines, docker, kubernetes, terraform, helm, deployment-strategies, gitops, incident-response |
| `fastapi-expert/` | endpoints-routing, pydantic-v2, async-sqlalchemy, authentication, testing-async, openapi |
| `postgres-pro/` | performance, jsonb, extensions, replication, maintenance |
| `python-pro/` | type-system, async-patterns, standard-library, testing, packaging |

### Gemini Skills (`.gemini/skills/`)

| Skill | Description |
|-------|-------------|
| `python-architecture/` | SOLID principles, low coupling, high cohesion, dependency injection |
| `python-clean-code/` | Code clarity, small functions (20-30 lines), meaningful naming, explicit error handling |
| `python-performance/` | Algorithmic improvements, generators, asyncio, Big-O analysis, profiling |
| `python-typing/` | Python 3.10+ typing, `Protocol` over ABC, no implicit `Any`, mypy `--strict` |

---

## How to Use

### With Claude Code

Skills in `.claude/skills/` are automatically available to Claude Code. Claude will activate the relevant skill based on context — for example, when working on a FastAPI project it will apply the `fastapi-expert` skill.

You can also invoke a skill explicitly using a slash command:

```
/python-pro
/debugging-wizard
/devops-engineer
```

### With Gemini

Skills in `.gemini/skills/` follow the same pattern and are picked up by Gemini-based agents configured to read from this directory.

### Adding a New Skill

1. Create a directory under `.claude/skills/<skill-name>/` or `.gemini/skills/<skill-name>/`
2. Write a `SKILL.md` with instructions — include:
   - Purpose and scope of the skill
   - Principles and constraints (`MUST`, `MUST NOT`)
   - Code examples demonstrating correct behavior
   - References to external tools/docs where appropriate
3. *(Optional)* Add a `skill.yaml` with metadata:
   ```yaml
   name: my-skill
   description: What this skill does
   version: 1.0
   prompt: SKILL.md
   ```
4. *(Optional)* Create a `references/` subfolder with deep-dive guides for specific subtopics

### Skill File Conventions

- **`SKILL.md`** — Main instruction file. Written in plain markdown. Should be opinionated and concrete.
- **`skill.yaml`** — Optional config. Fields: `name`, `description`, `version`, `prompt`.
- **`references/<topic>.md`** — Supplementary reference material for a specific concept within the skill's domain.

---

## Technologies Covered

**Languages & Frameworks**
- Python 3.10+ (primary focus)
- FastAPI, Pydantic V2, SQLAlchemy (async)

**Databases**
- PostgreSQL (advanced features: JSONB, EXPLAIN, replication, extensions)

**DevOps & Infrastructure**
- Docker, Kubernetes, Helm
- Terraform, Pulumi, Crossplane
- GitHub Actions, GitLab CI, Jenkins
- AWS, GCP, Azure

**Quality & Tooling**
- pytest, mypy, black, ruff
- TDD, SOLID, clean architecture
- CI/CD, GitOps, infrastructure as code

---

## Ignore Files

- `.claude/.claudeignore` — Tells Claude which files to skip (build artifacts, virtual environments, generated files)
- `.gemini/.geminiignore` — Same for Gemini, with extended patterns

These prevent AI agents from reading irrelevant files (e.g., `node_modules/`, `__pycache__/`, `.env`) and keep context focused on source code.
