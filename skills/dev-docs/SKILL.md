---
name: dev-docs
description: Generate professional README files with badges, tables, and developer-friendly structure. Automatically commits, pushes, and creates PRs via GitHub MCP.
license: MIT
metadata:
  author: carlos
  version: "1.0.0"
  tags:
    - documentation
    - readme
    - badges
    - markdown
    - developer-experience
---

# Dev Docs Skill

Generate professional, developer-friendly README files with badges, tables, and structured sections.

## Commands

### /docs readme

Analyze the current project and generate a professional README.md with:

1. **Project badges** - Build status, version, license, etc.
2. **Clear description** - What the project does
3. **Installation** - Step-by-step setup
4. **Usage** - Code examples
5. **API reference** - If applicable
6. **Contributing** - Guidelines
7. **License** - Project license

## Badge Templates

### Status Badges

```markdown
![Build Status](https://img.shields.io/github/actions/workflow/status/{owner}/{repo}/{workflow}.yml?branch=main)
![Version](https://img.shields.io/github/package-json/v/{owner}/{repo})
![License](https://img.shields.io/github/license/{owner}/{repo})
![Last Commit](https://img.shields.io/github/last-commit/{owner}/{repo})
```

### Tech Stack Badges

| Technology | Badge |
|------------|-------|
| TypeScript | `![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white)` |
| React | `![React](https://img.shields.io/badge/React-61DAFB?logo=react&logoColor=black)` |
| Node.js | `![Node.js](https://img.shields.io/badge/Node.js-339933?logo=node.js&logoColor=white)` |
| Python | `![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)` |
| Go | `![Go](https://img.shields.io/badge/Go-00ADD8?logo=go&logoColor=white)` |
| Rust | `![Rust](https://img.shields.io/badge/Rust-000000?logo=rust&logoColor=white)` |
| Docker | `![Docker](https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white)` |
| PostgreSQL | `![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?logo=postgresql&logoColor=white)` |

### Package Manager Badges

| Manager | Badge |
|---------|-------|
| npm | `![npm](https://img.shields.io/npm/v/{package})` |
| PyPI | `![PyPI](https://img.shields.io/pypi/v/{package})` |
| Crates.io | `![Crates.io](https://img.shields.io/crates/v/{package})` |

## README Structure Template

```markdown
<div align="center">

# Project Name

![Build](https://img.shields.io/badge/build-passing-brightgreen)
![Version](https://img.shields.io/badge/version-1.0.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)

**Short, compelling description of what this project does.**

[Getting Started](#getting-started) •
[Documentation](#documentation) •
[Contributing](#contributing)

</div>

---

## Features

| Feature | Description |
|---------|-------------|
| Feature 1 | What it does |
| Feature 2 | What it does |
| Feature 3 | What it does |

## Getting Started

### Prerequisites

- Requirement 1
- Requirement 2

### Installation

\`\`\`bash
# Clone the repository
git clone https://github.com/owner/repo.git

# Install dependencies
npm install

# Start the application
npm start
\`\`\`

## Usage

\`\`\`typescript
import { example } from 'package';

const result = example();
\`\`\`

## API Reference

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/resource` | GET | Get all resources |
| `/api/resource/:id` | GET | Get resource by ID |
| `/api/resource` | POST | Create new resource |

## Configuration

| Variable | Description | Default |
|----------|-------------|---------|
| `PORT` | Server port | `3000` |
| `NODE_ENV` | Environment | `development` |

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'feat: add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
```

## Table Formatting Guidelines

### Alignment

```markdown
| Left | Center | Right |
|:-----|:------:|------:|
| Data | Data   | Data  |
```

### Complex Tables

```markdown
| Command | Description | Example |
|---------|-------------|---------|
| `install` | Install dependencies | `npm install` |
| `build` | Build for production | `npm run build` |
| `test` | Run test suite | `npm test` |
```

## Post-Generation: Commit & PR Automation

After generating or updating the README, **always** execute the following workflow:

### 1. Commit the changes

```bash
git add README.md
git commit -m "docs: format README with dev-docs style"
```

### 2. Detect branching strategy

Check if the repo uses Git Flow (has a `develop` branch) or pushes directly to `main`:

```bash
git branch -a | grep -q develop
```

### 3. Push and create PR

**If Git Flow (develop branch exists):**
- Push to current branch (usually `develop`)
- Create a PR from `develop` → `main` using `gh`:

```bash
git push
gh pr create --base main --head develop --title "docs: update README with dev-docs format" --body "$(cat <<'EOF'
## Summary
- Formatted README with dev-docs style

## Test plan
- [ ] CI passes
- [ ] Release workflow triggers on merge
EOF
)"
```

**If single branch (main only):**
- Push directly to `main`:

```bash
git push
```

### 4. Verify CI status

After pushing, use the MCP `repo_check_ci` tool to verify the CI pipeline was triggered:

```
mcp__repo-monitor__repo_check_ci(repo: "owner/repo")
```

Report the CI status and PR URL back to the user.

---

## Best Practices

1. **Keep badges minimal** - Only show relevant badges (3-5 max)
2. **Use tables for structured data** - Commands, config, API endpoints
3. **Include code examples** - Real, working examples
4. **Add screenshots** - For UI projects, show don't tell
5. **Keep it scannable** - Use headers, lists, and whitespace
6. **Update regularly** - Outdated docs are worse than no docs
