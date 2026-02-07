<div align="center">

# GitFlow Skill

![Git](https://img.shields.io/badge/Git-F05032?logo=git&logoColor=white)
![Version](https://img.shields.io/badge/version-1.0.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)

**Automate Git Flow branching strategy with intelligent branch creation, merging, and release tagging.**

[Commands](#commands) •
[Branch Naming](#branch-naming-convention) •
[Workflow](#workflow-diagram) •
[Best Practices](#best-practices)

</div>

---

## Overview

The GitFlow skill enables Claude to manage your Git Flow workflow automatically. Create feature branches, handle releases, manage hotfixes, and merge branches following industry best practices.

## Features

| Feature | Description |
|---------|-------------|
| **Branch Creation** | Automatically create feature, release, and hotfix branches |
| **Smart Merging** | Merge with `--no-ff` to preserve history |
| **Release Tagging** | Automatic version tagging on releases and hotfixes |
| **Branch Cleanup** | Delete merged branches to keep repo clean |

## Installation

```bash
claude-skills install gitflow
```

## Commands

| Command | Description |
|---------|-------------|
| `/gitflow feature <name>` | Create a new feature branch from develop |
| `/gitflow release <version>` | Create a release branch from develop |
| `/gitflow hotfix <version>` | Create a hotfix branch from main |
| `/gitflow finish feature <name>` | Merge feature into develop and delete branch |
| `/gitflow finish release <version>` | Merge release into main/develop, create tag |
| `/gitflow finish hotfix <version>` | Merge hotfix into main/develop, create tag |

## Usage Examples

### Create a Feature Branch

```bash
/gitflow feature user-authentication
```

Executes:
```bash
git checkout develop
git pull origin develop
git checkout -b feature/user-authentication
```

### Finish a Release

```bash
/gitflow finish release 2.0.0
```

Executes:
```bash
git checkout main
git merge --no-ff release/2.0.0
git tag -a v2.0.0 -m "Release 2.0.0"
git checkout develop
git merge --no-ff release/2.0.0
git branch -d release/2.0.0
git push origin main develop --tags
```

## Branch Naming Convention

| Type | Pattern | Example |
|------|---------|---------|
| Feature | `feature/<ticket-id>-<description>` | `feature/PROJ-123-user-auth` |
| Release | `release/<version>` | `release/1.2.0` |
| Hotfix | `hotfix/<version>` | `hotfix/1.2.1` |
| Bugfix | `bugfix/<ticket-id>-<description>` | `bugfix/PROJ-456-fix-login` |

## Workflow Diagram

```
main ─────●─────────────────●─────────────●───────
          │                 ↑             ↑
          │            merge release  merge hotfix
          │                 │             │
          ↓                 │             │
develop ──●───●───●───●─────●─────────────●───────
              │       ↑
              │   merge feature
              ↓       │
feature ──────●───●───●
```

## Best Practices

| Practice | Description |
|----------|-------------|
| **Pull before branching** | Always pull latest changes before creating branches |
| **Use --no-ff merges** | Preserves branch history in the commit graph |
| **Delete after merge** | Remove merged branches to keep repository clean |
| **Tag all releases** | Creates easy reference points for version tracking |
| **Never commit to main** | All changes go through feature/release/hotfix branches |

## Related Skills

- [atomic-commits](../atomic-commits) - Write clean, atomic commits
- [jira-ticket](../jira-ticket) - Generate JIRA ticket templates

## License

MIT © [Carlos](https://github.com/jarero321)
