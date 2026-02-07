<div align="center">

```
     _                     _
  __| | _____   __      __| | ___   ___ ___
 / _` |/ _ \ \ / /____ / _` |/ _ \ / __/ __|
| (_| |  __/\ V /_____| (_| | (_) | (__\__ \
 \__,_|\___| \_/       \__,_|\___/ \___|___/
```

### I got tired of writing READMEs from scratch. So I taught Claude to do it.

![Claude Code](https://img.shields.io/badge/Claude_Code-Skill-f472b6)

[![Version](https://img.shields.io/badge/version-1.0.0-00d4ff?style=flat-square)](SKILL.md)
[![License](https://img.shields.io/badge/license-MIT-brightgreen?style=flat-square)](LICENSE)

**Claude Code skill for generating professional documentation**

</div>

---

## Overview

A Claude Code agent skill that generates professional, developer-friendly README files with badges, tables, and structured sections.

## Installation

```bash
# Using claude-skills CLI
claude-skills install dev-docs

# Or from repository
claude-skills install --repo https://github.com/jarero321/skill-dev-docs
```

## Usage

Once installed, use the `/docs` command in Claude Code:

```
/docs readme
```

Claude will analyze your project and generate a professional README with:

- **Project badges** - Build status, version, license
- **Clear description** - What the project does
- **Installation** - Step-by-step setup
- **Usage** - Code examples
- **API reference** - If applicable
- **Contributing** - Guidelines
- **License** - Project license

## Features

| Feature | Description |
|---------|-------------|
| Badge templates | Pre-built badges for common services |
| Tech stack badges | TypeScript, React, Node, Python, Go, Rust, etc. |
| Table formatting | Clean, aligned markdown tables |
| Structure templates | Professional README layout |

## Badge Examples

### Status Badges

```markdown
![Build](https://img.shields.io/github/actions/workflow/status/{owner}/{repo}/{workflow}.yml)
![Version](https://img.shields.io/github/package-json/v/{owner}/{repo})
![License](https://img.shields.io/github/license/{owner}/{repo})
```

### Tech Stack

| Technology | Badge |
|------------|-------|
| TypeScript | ![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white) |
| React | ![React](https://img.shields.io/badge/React-61DAFB?logo=react&logoColor=black) |
| Node.js | ![Node.js](https://img.shields.io/badge/Node.js-339933?logo=node.js&logoColor=white) |

## Best Practices

1. **Keep badges minimal** - Only show relevant badges (3-5 max)
2. **Use tables for structured data** - Commands, config, API endpoints
3. **Include code examples** - Real, working examples
4. **Add screenshots** - For UI projects, show don't tell
5. **Keep it scannable** - Use headers, lists, and whitespace

## Requirements

- [Claude Code](https://claude.ai/claude-code) CLI
- [claude-skills](https://github.com/jarero321/claude-skills) package manager

## License

MIT © [Carlos](https://github.com/jarero321)

---

<div align="center">

**[Report Bug](https://github.com/jarero321/skill-dev-docs/issues)** · **[Request Feature](https://github.com/jarero321/skill-dev-docs/issues)**

</div>
