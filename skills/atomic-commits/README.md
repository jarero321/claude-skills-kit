<div align="center">

# Atomic Commits Skill

![Git](https://img.shields.io/badge/Git-F05032?logo=git&logoColor=white)
![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-FE5196?logo=conventionalcommits&logoColor=white)
![Version](https://img.shields.io/badge/version-1.0.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)

**Write clean, atomic commits following Conventional Commits specification with GitFlow integration.**

[Commands](#commands) •
[Commit Format](#commit-message-format) •
[Examples](#commit-examples) •
[Best Practices](#atomic-commit-principles)

</div>

---

## Overview

The Atomic Commits skill helps you write clean, focused commits that follow the Conventional Commits specification. Each commit does one thing, is self-contained, and integrates seamlessly with GitFlow branching.

## Features

| Feature | Description |
|---------|-------------|
| **Conventional Commits** | Standard format with type, scope, and description |
| **GitFlow Integration** | Commit types mapped to branch types |
| **Atomic Principles** | Single responsibility, self-contained commits |
| **Split Suggestions** | Help breaking large changes into atomic units |

## Installation

```bash
claude-skills install atomic-commits
```

## Commands

| Command | Description |
|---------|-------------|
| `/commit` | Analyze staged changes and generate atomic commit message |
| `/commit split` | Suggest how to split current changes into multiple commits |
| `/commit review` | Review recent commits for atomic commit best practices |

## Commit Message Format

```
<type>(<scope>): <subject>

[optional body]

[optional footer]
```

### Types

| Type | Description | GitFlow Branch |
|------|-------------|----------------|
| `feat` | New feature | `feature/*` |
| `fix` | Bug fix | `bugfix/*`, `hotfix/*` |
| `hotfix` | Critical production fix | `hotfix/*` |
| `refactor` | Code refactoring | `feature/*` |
| `perf` | Performance improvement | `feature/*` |
| `test` | Adding/updating tests | Any |
| `docs` | Documentation changes | Any |
| `style` | Code style (formatting) | Any |
| `chore` | Maintenance tasks | Any |
| `ci` | CI/CD changes | Any |
| `build` | Build system changes | Any |
| `revert` | Revert previous commit | Any |

### Scopes

| Scope | Description |
|-------|-------------|
| `(ui)` | User interface components |
| `(api)` | API endpoints and services |
| `(auth)` | Authentication/authorization |
| `(db)` | Database models/migrations |
| `(config)` | Configuration files |
| `(deps)` | Dependencies |
| `(core)` | Core business logic |
| `(utils)` | Utilities and helpers |
| `(i18n)` | Internationalization |
| `(test)` | Test infrastructure |

## Atomic Commit Principles

### 1. Single Responsibility

Each commit should do ONE thing:

```
✅ Good:
feat(auth): add password validation

❌ Bad:
feat(auth): add password validation and fix login bug and update styles
```

### 2. Self-Contained

Commit should not break the build:

```
✅ Good:
feat(api): add user endpoint with tests

❌ Bad:
feat(api): add user endpoint (tests in next commit)
```

### 3. Logical Unit

Group related changes together:

```
✅ Good:
refactor(user): rename UserService to UserRepository
- Rename class
- Update all imports
- Update tests

❌ Bad:
Commit 1: refactor(user): rename class
Commit 2: fix: update imports (build broken between commits)
```

## Commit Examples

### Feature Commit

```
feat(ui): add avatar upload component

- Create AvatarUpload component with drag-and-drop
- Add image cropping functionality
- Implement preview before upload
```

### Bug Fix Commit

```
fix(auth): prevent token refresh loop on 401

Added flag to track refresh attempts and break
infinite loop when refresh token is also expired.
```

### Hotfix Commit

```
hotfix(payments): fix decimal precision in currency conversion

Critical: Users were being overcharged due to floating point errors.
Applied Decimal.js for all currency calculations.
```

### Breaking Change

```
feat(api)!: change authentication from session to JWT

BREAKING CHANGE: All API requests now require Bearer token
instead of session cookie. Update your API clients accordingly.

Migration guide: docs/migration/v2-auth.md
```

## Splitting Large Changes

### Before (Bad)

```
feat: implement entire user module
- Add User model
- Add UserService
- Add UserController
- Add user routes
- Add user tests
```

### After (Good)

```
feat(user): add User model with validation
feat(user): implement UserService with CRUD operations
feat(user): add UserController with error handling
feat(user): configure user routes
test(user): add unit tests for UserService
docs(user): add API documentation for user endpoints
```

## Commit Checklist

Before committing, verify:

- [ ] Changes are related to a single purpose
- [ ] Build passes with this commit alone
- [ ] Tests are included/updated
- [ ] Commit message follows convention
- [ ] No unrelated changes included
- [ ] No console.logs or debug code
- [ ] No commented-out code
- [ ] No secrets or credentials

## Related Skills

- [gitflow](../gitflow) - Git Flow branching automation
- [jira-ticket](../jira-ticket) - JIRA ticket templates

## License

MIT © [Carlos](https://github.com/jarero321)
