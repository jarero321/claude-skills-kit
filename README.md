<div align="center">

```
      _                 _                _    _ _ _           _    _ _
  ___| | __ _ _   _  __| | ___       ___| | _(_) | |___     | | _(_) |_
 / __| |/ _` | | | |/ _` |/ _ \___  / __| |/ / | | / __|____| |/ / | __|
| (__| | (_| | |_| | (_| |  __/_____ \__ \   <| | | \__ \_____   <| | |_
 \___|_|\__,_|\__,_|\__,_|\___|     |___/_|\_\_|_|_|___/     |_|\_\_|\__|
```

### All the skills. One repo. Zero friction.

![Claude Code](https://img.shields.io/badge/Claude_Code-Skills-f472b6)
[![Version](https://img.shields.io/badge/version-1.0.0-00d4ff?style=flat-square)](package.json)
[![License](https://img.shields.io/badge/license-MIT-brightgreen?style=flat-square)](LICENSE)

</div>

---

## Skills

| Skill | Command | Description |
|-------|---------|-------------|
| [atomic-commits](skills/atomic-commits) | `/commit` | Write clean, atomic commits following Conventional Commits with GitFlow integration |
| [gitflow](skills/gitflow) | `/gitflow` | Manage Git Flow branching strategy with automated branch creation and merging |
| [jira-ticket](skills/jira-ticket) | `/jira` | Generate structured JIRA ticket templates for features, bugs, hotfixes and spikes |
| [dev-docs](skills/dev-docs) | `/docs` | Generate professional README files with badges, tables, and PR automation |

## Installation

```bash
# Install individual skills via claude-skills CLI
claude-skills install atomic-commits
claude-skills install gitflow
claude-skills install jira-ticket
claude-skills install dev-docs
```

Or install manually by copying the `SKILL.md` file from any skill folder into your project's `.claude/skills/` directory.

## Structure

```
claude-skills-kit/
├── skills/
│   ├── atomic-commits/
│   │   ├── SKILL.md
│   │   └── README.md
│   ├── gitflow/
│   │   ├── SKILL.md
│   │   └── README.md
│   ├── jira-ticket/
│   │   ├── SKILL.md
│   │   └── README.md
│   └── dev-docs/
│       ├── SKILL.md
│       └── README.md
├── package.json
├── LICENSE
└── README.md
```

## Contributing

To add a new skill:

1. Create a folder under `skills/` with the skill name
2. Add a `SKILL.md` with frontmatter (`name`, `description`, `license`, `metadata`)
3. Add a `README.md` documenting commands and usage
4. Submit a PR

### Skill Frontmatter Format

```yaml
---
name: my-skill
description: What this skill does
license: MIT
metadata:
  author: your-name
  version: "1.0.0"
  tags:
    - tag1
    - tag2
---
```

## License

MIT © [Carlos](https://github.com/jarero321)
