---
name: atomic-commits
description: Write clean, atomic commits following Conventional Commits specification with GitFlow integration and best practices for single-responsibility commits.
license: MIT
metadata:
  author: carlos
  version: "1.0.0"
  tags:
    - git
    - commits
    - conventional-commits
    - atomic
    - gitflow
---

# Atomic Commits Skill

Write clean, atomic commits following Conventional Commits specification integrated with GitFlow.

**IMPORTANT**: Never include `Co-Authored-By` in commit messages.

## Commands

### /commit
Analyze staged changes and generate an atomic commit message.

### /commit split
Suggest how to split current changes into multiple atomic commits.

### /commit review
Review recent commits for atomic commit best practices.

---

## Commit Message Format

```
<type>(<scope>): <subject>

[optional body]

[optional footer - NO Co-Authored-By]
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

### Scope (REQUIRED)

Always use parentheses with a scope that identifies the affected area:

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

---

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

---

## Commit Message Examples

### Feature Commits

```
feat(ui): add avatar upload component

- Create AvatarUpload component with drag-and-drop
- Add image cropping functionality
- Implement preview before upload
```

```
feat(api): implement user profile endpoints

- Add GET /users/:id endpoint
- Add PATCH /users/:id for profile updates
- Include validation middleware
```

### Bug Fix Commits

```
fix(ui): resolve button alignment in mobile view

Buttons were overlapping on screens smaller than 375px.
Applied flex-wrap and adjusted spacing.
```

```
fix(auth): prevent token refresh loop on 401

Added flag to track refresh attempts and break
infinite loop when refresh token is also expired.
```

### Hotfix Commits

```
hotfix(payments): fix decimal precision in currency conversion

Critical: Users were being overcharged due to floating point errors.
Applied Decimal.js for all currency calculations.
```

### Refactor Commits

```
refactor(core): extract validation logic to middleware

Move request validation from controllers to dedicated middleware
for better separation of concerns.
```

### Style/Chore Commits

```
style(ui): format components with prettier

chore(deps): update react to 18.3.0
```

---

## GitFlow + Atomic Commits Workflow

### Feature Development

```bash
# 1. Create feature branch
git checkout -b feature/PROJ-123-user-profile

# 2. Make atomic commits as you work
git add src/components/Avatar.tsx
git commit -m "feat(profile): add Avatar component"

git add src/api/profile.ts src/api/profile.test.ts
git commit -m "feat(profile): add profile API endpoints"

git add src/pages/Profile.tsx
git commit -m "feat(profile): create profile page with Avatar"

# 3. Squash if needed before merge (optional)
git rebase -i develop

# 4. Merge with --no-ff
git checkout develop
git merge --no-ff feature/PROJ-123-user-profile
```

### Hotfix Flow

```bash
# 1. Create hotfix branch
git checkout -b hotfix/1.2.1

# 2. Single atomic commit for the fix
git add src/payments/converter.ts src/payments/converter.test.ts
git commit -m "hotfix(payments): fix decimal precision in currency conversion

Critical: Users were being overcharged due to floating point errors.
Incident: INC-789"

# 3. Merge to main and develop
git checkout main
git merge --no-ff hotfix/1.2.1
git tag -a v1.2.1 -m "Hotfix: payment precision"
```

---

## Splitting Large Changes

### Before (Bad)
```
feat: implement entire user module
- Add User model
- Add UserService
- Add UserController
- Add user routes
- Add user tests
- Add user documentation
```

### After (Good)
```
# Commit 1
feat(user): add User model with validation

# Commit 2
feat(user): implement UserService with CRUD operations

# Commit 3
feat(user): add UserController with error handling

# Commit 4
feat(user): configure user routes

# Commit 5
test(user): add unit tests for UserService

# Commit 6
docs(user): add API documentation for user endpoints
```

---

## Breaking Changes

Use the `BREAKING CHANGE:` footer or add an exclamation mark after the type:

```
feat(api)!: change authentication from session to JWT

BREAKING CHANGE: All API requests now require Bearer token
instead of session cookie. Update your API clients accordingly.

Migration guide: docs/migration/v2-auth.md
```

---

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
