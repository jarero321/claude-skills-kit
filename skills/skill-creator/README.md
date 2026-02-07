<div align="center">

```
     _    _ _ _                       _
 ___| | _(_) | |     ___ _ __ ___  __ _| |_ ___  _ __
/ __| |/ / | | |__  / __| '__/ _ \/ _` | __/ _ \| '__|
\__ \   <| | | |__| (__| | |  __/ (_| | || (_) | |
|___/_|\_\_|_|_|    \___|_|  \___|\__,_|\__\___/|_|
```

### The skill that creates skills.

![Claude Code](https://img.shields.io/badge/Claude_Code-Skill-f472b6)
[![Version](https://img.shields.io/badge/version-1.0.0-00d4ff?style=flat-square)](SKILL.md)
[![License](https://img.shields.io/badge/license-MIT-brightgreen?style=flat-square)](LICENSE)

**Claude Code skill for scaffolding well-structured, validated skills for the claude-skills-kit ecosystem.**

</div>

---

## Overview

A meta-skill that teaches Claude how to create new Claude Code skills. It codifies the frontmatter validation rules, the proven SKILL.md structure (decision tables, good/bad examples, templates), and the README.md companion format — so every generated skill is valid and ready to publish.

## Installation

```bash
# Using claude-skills CLI
claude-skills install skill-creator

# Or from repository
claude-skills install --repo https://github.com/jarero321/claude-skills-kit
```

## Usage

Once installed, use the `/skill` command in Claude Code:

```
/skill create my-awesome-skill
```

Claude will ask for details, then generate a complete skill with validated frontmatter, prescriptive rules, and companion README.

## Commands

| Command | Description |
|:--------|:------------|
| `/skill create <name>` | Scaffold a new skill from scratch |
| `/skill validate` | Validate an existing SKILL.md against all rules |
| `/skill improve` | Analyze a SKILL.md and suggest improvements |

## Features

| Feature | Description |
|:--------|:------------|
| **Validated Frontmatter** | Generates YAML that passes `claude-skills validate` |
| **Prescriptive Structure** | Decision tables, numbered steps, ALWAYS/NEVER rules |
| **Good/Bad Examples** | Side-by-side comparisons baked into every skill |
| **README Generation** | Companion README.md with figlet header and install instructions |
| **Registry Integration** | Adds skill to registry.json if in monorepo |
| **Quality Checklist** | Verifies completeness before publishing |

## What Makes a Good Skill

| Pattern | Why |
|:--------|:----|
| Decision tables | Claude knows exactly when to do what |
| Good/Bad examples | No ambiguity about expected output |
| ALWAYS/NEVER rules | Stronger than "should" or "consider" |
| Complete templates | Copy-paste-ready output |
| Numbered steps | Clear execution order |

## Requirements

- [Claude Code](https://claude.ai/claude-code) CLI
- [claude-skills](https://github.com/jarero321/claude-skills) package manager

## License

MIT

---

<div align="center">

**[Report Bug](https://github.com/jarero321/claude-skills-kit/issues)** · **[Request Feature](https://github.com/jarero321/claude-skills-kit/issues)**

</div>
