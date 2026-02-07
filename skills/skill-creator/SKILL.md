---
name: skill-creator
description: Create well-structured Claude Code skills with validated frontmatter, prescriptive rules, good/bad examples, and ready-to-publish structure for the claude-skills-kit registry.
license: MIT
metadata:
  author: carlos
  version: "1.0.0"
  tags:
    - skills
    - scaffolding
    - meta
    - claude-code
    - developer-experience
---

# Skill Creator Skill

Create well-structured Claude Code skills that follow the claude-skills-kit conventions. Every generated skill should be valid, prescriptive, and ready to publish.

## Commands

### /skill create <name>

Scaffold a new skill from scratch:

1. **Ask for details** — Skill purpose, commands, target audience
2. **Generate SKILL.md** — With validated frontmatter + full markdown body
3. **Generate README.md** — Companion docs for the skill repo
4. **Validate** — Run `claude-skills validate` to verify
5. **Register** — Add to registry.json if in claude-skills-kit monorepo

### /skill validate

Validate an existing SKILL.md in the current directory against all rules.

### /skill improve

Analyze an existing SKILL.md and suggest improvements based on the quality checklist.

---

## Step 1: Understand What a Skill Is

A Claude Code skill is a **SKILL.md file** — a markdown document with YAML frontmatter that teaches Claude how to perform a specific task. Skills are:

- **Declarative** — They describe rules and patterns, not executable code
- **Prescriptive** — Clear decision tables, not vague guidelines
- **Self-contained** — Everything Claude needs is in one file
- **Composable** — Skills can reference other skills (e.g., `/commit` inside `/docs readme`)

**A skill is NOT**: a plugin, a script, or an executable. It is structured documentation that shapes Claude's behavior.

---

## Step 2: Skill File Structure

Every skill lives in a directory with this structure:

```
skill-name/
├── SKILL.md        # Required — The skill definition
├── README.md       # Required — Human-readable documentation
└── LICENSE         # Optional — Defaults to MIT
```

When inside the `claude-skills-kit` monorepo:

```
claude-skills-kit/
└── skills/
    └── skill-name/
        ├── SKILL.md
        └── README.md
```

---

## Step 3: Frontmatter Rules

The YAML frontmatter is **validated by the CLI**. Every field has strict rules.

### Required Fields

```yaml
---
name: skill-name
description: One-line description of what this skill does (max 1024 chars).
license: MIT
metadata:
  author: carlos
  version: "1.0.0"
  tags:
    - tag1
    - tag2
---
```

### Validation Rules

| Field | Rule | Example |
|:------|:-----|:--------|
| `name` | Lowercase, numbers, hyphens only. Regex: `/^[a-z0-9-]+$/` | `atomic-commits` |
| `description` | Required string, max 1024 characters | `Write clean atomic commits...` |
| `license` | Required string | `MIT` |
| `metadata.author` | Required string | `carlos` |
| `metadata.version` | Semver format: `X.Y.Z` | `"1.0.0"` |
| `metadata.tags` | Optional array of strings | `[git, commits]` |

### Good vs Bad Frontmatter

```yaml
# ✅ Good
---
name: dev-docs
description: Generate visually compelling README files using capsule-render headers and skillicons.dev tech stacks.
license: MIT
metadata:
  author: carlos
  version: "2.0.0"
  tags:
    - documentation
    - readme
---

# ❌ Bad — name has uppercase
---
name: Dev-Docs
description: Generate READMEs
license: MIT
metadata:
  author: carlos
  version: "2.0.0"
---

# ❌ Bad — missing metadata.version
---
name: dev-docs
description: Generate READMEs
license: MIT
metadata:
  author: carlos
---

# ❌ Bad — version not semver
---
name: dev-docs
description: Generate READMEs
license: MIT
metadata:
  author: carlos
  version: "v2"
---
```

---

## Step 4: SKILL.md Body Structure

The markdown body after the frontmatter follows a proven structure. Use this as the skeleton for every skill.

### Mandatory Sections

| Section | Purpose |
|:--------|:--------|
| **Title + Description** | `# Skill Name` + one-line summary |
| **Commands** | List all `/command` invocations the skill provides |
| **Rules / Decision Tables** | When to do what — tables, not prose |
| **Templates / Snippets** | Ready-to-use code/markdown blocks |
| **Good vs Bad Examples** | Side-by-side comparisons with checkmarks |
| **Best Practices** | Numbered list of principles |

### Optional Sections

| Section | When to Include |
|:--------|:----------------|
| **Step-by-step Workflow** | If the skill involves a multi-step process |
| **Post-Generation Automation** | If the skill should commit/push/PR after generating |
| **Configuration Reference** | If the skill uses env vars or config files |
| **Related Skills** | If the skill works alongside others |

### Skeleton Template

````markdown
---
name: {skill-name}
description: {One-line description of what this skill does.}
license: MIT
metadata:
  author: {author}
  version: "1.0.0"
  tags:
    - {tag1}
    - {tag2}
---

# {Skill Name} Skill

{One-line description.}

## Commands

### /{command} {subcommand}

{What this command does.}

### /{command} {another-subcommand}

{What this command does.}

---

## Rules

{Decision table or numbered rules that tell Claude WHEN to do WHAT.}

| Condition | Action |
|:----------|:-------|
| If X | Do Y |
| If A | Do B |

---

## Templates

{Ready-to-use snippets that Claude should output.}

```{language}
{template content}
```

---

## Good vs Bad Examples

### {Topic}

```
✅ Good:
{correct example}

❌ Bad:
{incorrect example}
```

---

## Best Practices

1. **{Principle 1}** — {Explanation}
2. **{Principle 2}** — {Explanation}
3. **{Principle 3}** — {Explanation}
````

---

## Step 5: Writing Effective Rules

Skills work because they give Claude **prescriptive rules**, not vague advice. Follow these patterns:

### Use Decision Tables (not paragraphs)

```
✅ Good:
| Project Type | Header | Badges | Tech Stack |
|:------------|:------:|:------:|:----------:|
| npm library | capsule-render | npm, build, license | skillicons |
| CLI tool | capsule-render | npm, build | skillicons |

❌ Bad:
If the project is an npm library, you should probably use capsule-render
for the header and add some badges. For CLI tools it's similar but you
might not need all the badges.
```

### Use Numbered Steps (not free-form instructions)

```
✅ Good:
1. Detect project type from package.json
2. Select template based on detection table
3. Replace all placeholders with real values
4. Commit and push

❌ Bad:
Analyze the project and figure out what kind it is, then generate
a README that looks good and push it.
```

### Use Good/Bad Examples (always)

```
✅ Good:
### Commit Messages
```
✅ Good:
feat(auth): add password validation

❌ Bad:
added stuff
```

❌ Bad:
Write good commit messages that describe what changed.
```

### Use ALWAYS/NEVER (not "should" or "consider")

```
✅ Good:
**ALWAYS** use `style=for-the-badge` for action badges.
**NEVER** use plain text where a visual equivalent exists.

❌ Bad:
You should consider using for-the-badge style when appropriate.
It's generally better to use visuals instead of text.
```

---

## Step 6: Writing the README.md

Every skill needs a companion README.md for human readers. Use this template:

````markdown
<div align="center">

```
{figlet ASCII art of the skill name}
```

### {Catchy one-liner tagline}

![Claude Code](https://img.shields.io/badge/Claude_Code-Skill-f472b6)
[![Version](https://img.shields.io/badge/version-{version}-00d4ff?style=flat-square)](SKILL.md)
[![License](https://img.shields.io/badge/license-MIT-brightgreen?style=flat-square)](LICENSE)

**{Short description}**

</div>

---

## Overview

{2-3 sentence description of what this skill does and why it exists.}

## Installation

```bash
# Using claude-skills CLI
claude-skills install {skill-name}

# Or from repository
claude-skills install --repo https://github.com/{owner}/{repo}
```

## Usage

Once installed, use the `/{command}` command in Claude Code:

```
/{command} {subcommand}
```

## Commands

| Command | Description |
|:--------|:------------|
| `/{command} {sub1}` | {What it does} |
| `/{command} {sub2}` | {What it does} |

## Features

| Feature | Description |
|:--------|:------------|
| **{Feature 1}** | {Description} |
| **{Feature 2}** | {Description} |

## Requirements

- [Claude Code](https://claude.ai/claude-code) CLI
- [claude-skills](https://github.com/jarero321/claude-skills) package manager

## License

MIT
````

---

## Step 7: Registry Integration

If the skill is part of the `claude-skills-kit` monorepo, add it to `registry.json`:

```json
{
  "name": "{skill-name}",
  "description": "{Same description as frontmatter}",
  "version": "1.0.0",
  "author": "carlos",
  "repository": "https://github.com/jarero321/claude-skills-kit",
  "path": "skills/{skill-name}",
  "tags": ["{tag1}", "{tag2}"],
  "license": "MIT"
}
```

Add this entry to the `skills` array in `registry.json`. Also update the `README.md` at the root of `claude-skills-kit` to include the new skill in the skills table.

---

## Step 8: Post-Creation Workflow

After generating the skill files:

### 1. Validate

```bash
claude-skills validate ./skills/{skill-name}
```

If validation fails, fix the frontmatter errors before proceeding.

### 2. Commit

```bash
git add skills/{skill-name}/
git commit -m "feat(skills): add {skill-name} skill"
```

### 3. Update registry (if in monorepo)

```bash
git add registry.json README.md
git commit -m "docs(registry): register {skill-name} skill"
```

### 4. Push and verify

```bash
git push
```

Use `mcp__repo-monitor__repo_check_ci(repo: "owner/repo")` to verify CI passes.

---

## Quality Checklist

Before considering a skill complete, verify ALL of these:

### Frontmatter
- [ ] `name` is lowercase with hyphens only
- [ ] `description` is under 1024 characters and describes the skill clearly
- [ ] `metadata.version` follows semver (`X.Y.Z`)
- [ ] `metadata.tags` are relevant and lowercase

### Commands
- [ ] Every command starts with `/` and has a clear name
- [ ] Each command has a one-line description of what it does
- [ ] Command names are short and memorable

### Rules
- [ ] Decision tables used instead of paragraphs for conditional logic
- [ ] Numbered steps for multi-step processes
- [ ] ALWAYS/NEVER used instead of "should"/"consider"
- [ ] No ambiguity — Claude knows exactly what to do in every case

### Examples
- [ ] Good vs Bad examples for every major pattern
- [ ] Examples use real-world content, not lorem ipsum
- [ ] Checkmark/cross format: `✅ Good:` / `❌ Bad:`

### Templates
- [ ] Ready-to-use snippets with proper language tags on code blocks
- [ ] Placeholders use `{curly-braces}` format
- [ ] Templates are complete — not fragments

### README.md
- [ ] Has figlet ASCII art header
- [ ] Has installation instructions (`claude-skills install`)
- [ ] Has commands table
- [ ] Has features table

---

## Best Practices

1. **Be prescriptive, not descriptive** — Tell Claude exactly what to do, not what might be nice. Decision tables > paragraphs.
2. **Show, don't tell** — Every rule needs a Good/Bad example. If you can't show it, the rule is too vague.
3. **One skill, one job** — A skill should do one category of things well. Don't combine unrelated commands.
4. **Commands are the API** — Users discover skills through `/commands`. Make them short, intuitive, and memorable.
5. **Templates are the output** — Claude's generated output should match your templates exactly. Include complete, copy-paste-ready templates.
6. **Test with real projects** — Run the skill against a real codebase before publishing. If the output doesn't look right, the rules need work.
7. **Version honestly** — Use semver. Breaking changes to commands or output format = major version bump.
8. **Compose with other skills** — Reference other skills when appropriate (e.g., `dev-docs` references `/commit` for post-generation).

---

## Existing Skills Reference

These skills in the kit follow the patterns above. Use them as references:

| Skill | Key Pattern | Best For Learning |
|:------|:-----------|:------------------|
| `atomic-commits` | Good/Bad examples, type tables, checklist | How to write prescriptive commit rules |
| `gitflow` | Workflow diagrams, bash snippets, branch tables | How to structure multi-step workflows |
| `dev-docs` | Visual toolkit, detection tables, template nesting | How to build visual-first generation skills |
| `jira-ticket` | Multiple templates per type, structured sections | How to handle multiple output variants |
