# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Repository Is

A skill library for AI coding assistants (Claude and Gemini). Skills are markdown-based behavioral instruction sets that guide AI agents to produce high-quality, production-ready output within a specific domain. There is no executable code, build system, or test runner — all content is markdown and YAML.

## Repository Layout

Skills are split by agent:

- `.claude/skills/` — Skills consumed by Claude Code
- `.gemini/skills/` — Skills consumed by Gemini-based agents

Each skill lives in its own directory and follows this convention:

```
<skill-name>/
├── SKILL.md          # Main instruction set (required)
├── skill.yaml        # Metadata: name, description, version, prompt (optional)
└── references/       # Deep-dive guides on subtopics (optional)
    └── <topic>.md
```

Single-file skills (no subfolder) use a flat `.md` file directly in `skills/` (e.g., `architecture.md`).

## skill.yaml Schema

```yaml
name: <skill-name>          # kebab-case, matches directory name
description: <one-line>     # Used by the agent to decide when to activate this skill
version: 1.0
prompt: SKILL.md            # Entry point — always SKILL.md
```

## SKILL.md Authoring Conventions

Skills in this repo follow a consistent structure:

1. **Role declaration** — "You are an expert in X"
2. **Mandatory rules** — MUST/MUST NOT constraints the agent enforces unconditionally
3. **Design/pattern rules** — Preferred approaches and patterns
4. **Anti-patterns** — Explicitly forbidden approaches
5. **Output format** — How the agent should structure its response (e.g., "1. brief explanation, 2. full typed code, 3. example usage")

Reference guides (`references/*.md`) contain deep-dive material on a single subtopic and are supplementary to `SKILL.md` — they do not need the role declaration or output format sections.

## Adding or Modifying Skills

- **New Claude skill**: create `.claude/skills/<skill-name>/SKILL.md` (add `skill.yaml` if it needs metadata for activation)
- **New Gemini skill**: create `.gemini/skills/<skill-name>/SKILL.md`
- **New reference guide**: add `references/<topic>.md` inside an existing skill folder; the topic should be narrow enough to fit in one focused guide
- Keep skill names in kebab-case; keep `skill.yaml` `name` field in sync with the directory name

## Ignore Files

`.claude/.claudeignore` and `.gemini/.geminiignore` control which files the respective agents read. Both already exclude standard Python artifacts, build output, IDE files, and AI workspace temporaries. Extend these files — not SKILL.md content — when a new file type should be hidden from agents.
