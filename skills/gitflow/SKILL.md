---
name: gitflow
description: Manage Git Flow branching strategy with automated branch creation, merging, and release tagging following best practices.
license: MIT
metadata:
  author: carlos
  version: "1.0.0"
  tags:
    - git
    - gitflow
    - branching
    - workflow
    - release
---

# GitFlow Skill

Manage Git Flow branching strategy with automated branch creation and merging.

## Commands

### /gitflow feature <name>
Create a new feature branch from develop.

```bash
git checkout develop
git pull origin develop
git checkout -b feature/<name>
```

### /gitflow release <version>
Create a release branch from develop.

```bash
git checkout develop
git pull origin develop
git checkout -b release/<version>
```

### /gitflow hotfix <version>
Create a hotfix branch from main.

```bash
git checkout main
git pull origin main
git checkout -b hotfix/<version>
```

### /gitflow finish feature <name>
Merge feature into develop and delete branch.

```bash
git checkout develop
git pull origin develop
git merge --no-ff feature/<name>
git branch -d feature/<name>
git push origin develop
```

### /gitflow finish release <version>
Merge release into main and develop, create tag.

```bash
git checkout main
git pull origin main
git merge --no-ff release/<version>
git tag -a v<version> -m "Release <version>"
git checkout develop
git merge --no-ff release/<version>
git branch -d release/<version>
git push origin main develop --tags
```

### /gitflow finish hotfix <version>
Merge hotfix into main and develop, create tag.

```bash
git checkout main
git pull origin main
git merge --no-ff hotfix/<version>
git tag -a v<version> -m "Hotfix <version>"
git checkout develop
git merge --no-ff hotfix/<version>
git branch -d hotfix/<version>
git push origin main develop --tags
```

## Branch Naming Convention

| Type | Pattern | Example |
|------|---------|---------|
| Feature | `feature/<ticket-id>-<short-description>` | `feature/PROJ-123-user-auth` |
| Release | `release/<version>` | `release/1.2.0` |
| Hotfix | `hotfix/<version>` | `hotfix/1.2.1` |
| Bugfix | `bugfix/<ticket-id>-<short-description>` | `bugfix/PROJ-456-fix-login` |

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

1. **Always pull before creating branches** - Ensure you have the latest changes
2. **Use --no-ff for merges** - Preserves branch history
3. **Delete branches after merge** - Keep repository clean
4. **Tag releases and hotfixes** - Easy version tracking
5. **Never commit directly to main or develop** - Always use branches
