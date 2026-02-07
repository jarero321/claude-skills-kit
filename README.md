<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=0,2,5,30&height=180&section=header&text=claude-skills-kit&fontSize=36&fontColor=fff&animation=fadeIn&fontAlignY=32" />

<div align="center">

![Claude Code](https://img.shields.io/badge/Claude_Code-Skills-f472b6?style=for-the-badge)
![Version](https://img.shields.io/badge/version-1.0.0-00d4ff?style=for-the-badge)
![License](https://img.shields.io/github/license/jarero321/claude-skills-kit?style=for-the-badge)
![Skills](https://img.shields.io/badge/skills-5-7c3aed?style=for-the-badge)

**Curated collection of Claude Code agent skills. All the skills. One repo. Zero friction.**

[Skills](#skills) •
[Installation](#installation) •
[Creating Skills](#creating-skills) •
[Contributing](#contributing)

</div>

---

## Features

| Feature | Description |
|:--------|:------------|
| **Plug & Play** | Install any skill with a single command via `claude-skills` CLI |
| **Curated Quality** | Every skill follows validated frontmatter and prescriptive rules |
| **5 Skills** | Git workflow, commits, JIRA tickets, documentation, and skill scaffolding |
| **Zero Dependencies** | Pure markdown skills — no runtime dependencies |
| **Manual Install** | Copy `SKILL.md` directly into `.claude/skills/` if you prefer |

## Tech Stack

<div align="center">

**Powered By**

<img src="https://skillicons.dev/icons?i=md,git,github&perline=8" alt="tech" />

</div>

---

## Skills

<table>
<tr>
  <td width="50%">
    <h3 align="center">atomic-commits</h3>
    <div align="center">
      <p>Write clean, atomic commits following Conventional Commits with GitFlow integration</p>
      <a href="https://github.com/jarero321/claude-skills-kit/tree/main/skills/atomic-commits">
        <img src="https://img.shields.io/badge/CODE-2ea44f?style=for-the-badge&logo=github&logoColor=white" alt="code" />
      </a>
      <br><br>
      <code>/commit</code> · <code>/commit split</code> · <code>/commit review</code>
    </div>
  </td>
  <td width="50%">
    <h3 align="center">gitflow</h3>
    <div align="center">
      <p>Manage Git Flow branching strategy with automated branch creation and merging</p>
      <a href="https://github.com/jarero321/claude-skills-kit/tree/main/skills/gitflow">
        <img src="https://img.shields.io/badge/CODE-2ea44f?style=for-the-badge&logo=github&logoColor=white" alt="code" />
      </a>
      <br><br>
      <code>/gitflow feature</code> · <code>/gitflow release</code> · <code>/gitflow hotfix</code>
    </div>
  </td>
</tr>
<tr>
  <td width="50%">
    <h3 align="center">jira-ticket</h3>
    <div align="center">
      <p>Generate structured JIRA ticket templates for features, bugs, hotfixes and spikes</p>
      <a href="https://github.com/jarero321/claude-skills-kit/tree/main/skills/jira-ticket">
        <img src="https://img.shields.io/badge/CODE-2ea44f?style=for-the-badge&logo=github&logoColor=white" alt="code" />
      </a>
      <br><br>
      <code>/jira feature</code> · <code>/jira bug</code> · <code>/jira hotfix</code>
    </div>
  </td>
  <td width="50%">
    <h3 align="center">dev-docs</h3>
    <div align="center">
      <p>Generate visual-first README files with capsule-render, skillicons, and PR automation</p>
      <a href="https://github.com/jarero321/claude-skills-kit/tree/main/skills/dev-docs">
        <img src="https://img.shields.io/badge/CODE-2ea44f?style=for-the-badge&logo=github&logoColor=white" alt="code" />
      </a>
      <br><br>
      <code>/docs readme</code> · <code>/docs readme --profile</code>
    </div>
  </td>
</tr>
<tr>
  <td width="50%">
    <h3 align="center">skill-creator</h3>
    <div align="center">
      <p>Scaffold well-structured Claude Code skills with validated frontmatter and prescriptive rules</p>
      <a href="https://github.com/jarero321/claude-skills-kit/tree/main/skills/skill-creator">
        <img src="https://img.shields.io/badge/CODE-2ea44f?style=for-the-badge&logo=github&logoColor=white" alt="code" />
      </a>
      <br><br>
      <code>/skill create</code> · <code>/skill validate</code> · <code>/skill improve</code>
    </div>
  </td>
  <td width="50%">
  </td>
</tr>
</table>

---

## Installation

```bash
# Install individual skills via claude-skills CLI
claude-skills install atomic-commits
claude-skills install gitflow
claude-skills install jira-ticket
claude-skills install dev-docs
claude-skills install skill-creator
```

Or install manually by copying the `SKILL.md` file from any skill folder into your project's `.claude/skills/` directory.

> Don't have the CLI? Install it: `npm install -g @cjarero183006/claude-skills`

---

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
│   ├── dev-docs/
│   │   ├── SKILL.md
│   │   └── README.md
│   └── skill-creator/
│       ├── SKILL.md
│       └── README.md
├── package.json
├── LICENSE
└── README.md
```

| Aspect | Choice |
|:-------|:-------|
| **Type** | Skills registry (pure markdown) |
| **Skills** | 5 curated skills |
| **Format** | YAML frontmatter + Markdown body |
| **Install** | via `claude-skills` CLI or manual copy |

---

## Creating Skills

To create a new skill, use the `skill-creator` skill:

```bash
claude-skills install skill-creator
```

Then in Claude Code:

```
/skill create my-awesome-skill
```

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

### Skill File Structure

```
my-skill/
├── SKILL.md      # What Claude should do (frontmatter + instructions)
└── README.md     # Human-readable documentation
```

---

## Contributing

1. Fork the repository
2. Create a folder under `skills/` with the skill name
3. Add a `SKILL.md` with frontmatter (`name`, `description`, `license`, `metadata`)
4. Add a `README.md` documenting commands and usage
5. Submit a PR

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

<div align="center">

**[Report Bug](https://github.com/jarero321/claude-skills-kit/issues)** · **[Request Feature](https://github.com/jarero321/claude-skills-kit/issues)**

</div>

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=0,2,5,30&height=120&section=footer" />
