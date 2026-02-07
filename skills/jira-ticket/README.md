<div align="center">

# JIRA Ticket Skill

![Jira](https://img.shields.io/badge/Jira-0052CC?logo=jira&logoColor=white)
![Agile](https://img.shields.io/badge/Agile-009688?logo=agile&logoColor=white)
![Version](https://img.shields.io/badge/version-1.0.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)

**Generate structured JIRA ticket templates with acceptance criteria, test evidence sections, and best practices.**

[Commands](#commands) •
[Templates](#available-templates) •
[Examples](#template-examples) •
[Best Practices](#best-practices)

</div>

---

## Overview

The JIRA Ticket skill helps you create well-structured tickets for your agile workflow. Generate templates for features, bugs, hotfixes, tasks, spikes, and integration test evidence with all the necessary sections for clear communication and traceability.

## Features

| Feature | Description |
|---------|-------------|
| **Multiple Templates** | Feature, Bug, Hotfix, Task, Spike, Integration Tests |
| **Acceptance Criteria** | Built-in sections for clear definition of done |
| **Test Evidence** | Structured format for documenting test results |
| **Bilingual Support** | Templates support English and Spanish sections |

## Installation

```bash
claude-skills install jira-ticket
```

## Commands

| Command | Description |
|---------|-------------|
| `/jira feature` | Generate a Feature ticket template |
| `/jira bug` | Generate a Bug ticket template |
| `/jira hotfix` | Generate a Hotfix ticket template |
| `/jira task` | Generate a Task ticket template |
| `/jira spike` | Generate a Spike/Research ticket template |
| `/jira integration-tests` | Generate Integration Tests evidence template |

## Available Templates

### Feature Template

Includes:
- Summary & Description
- User Story format
- Acceptance Criteria checklist
- Technical Notes (components, approach, dependencies)
- Test Scenarios
- Functional Test Evidence section
- Definition of Done

### Bug Template

Includes:
- Environment details
- Steps to Reproduce
- Expected vs Actual Behavior
- Evidence (screenshots, logs)
- Impact assessment
- Root Cause analysis
- Regression Testing checklist

### Hotfix Template

Includes:
- Severity indicator
- Timeline tracking
- Incident details & metrics
- Root Cause
- Rollback Plan
- Deployment Steps checklist
- Post-Mortem section

### Task Template

Includes:
- Summary & Description
- Subtasks checklist
- Technical Details
- Dependencies
- Estimation

### Spike Template

Includes:
- Research objective
- Questions to Answer
- Research Areas
- Time Box
- Expected Deliverables
- Findings & Recommendation sections

### Integration Tests Template

Includes:
- Components affected table
- Flows tested checklist
- Test evidence for each flow
- Results summary table
- Coverage metrics

## Template Examples

### Feature Ticket

```markdown
## Summary
Add two-factor authentication to user login

## User Story
As a security-conscious user,
I want to enable 2FA on my account,
So that my account is protected from unauthorized access.

## Acceptance Criteria
- [ ] AC1: User can enable 2FA from account settings
- [ ] AC2: System supports authenticator apps (TOTP)
- [ ] AC3: Backup codes are generated and displayed
```

### Bug Ticket

```markdown
## Summary
Login button unresponsive on mobile Safari

## Environment
- **Environment:** Production
- **Browser/Device:** Safari 17, iPhone 15
- **User Type:** Regular User

## Steps to Reproduce
1. Open app on iPhone Safari
2. Enter valid credentials
3. Tap "Login" button
4. Nothing happens

## Expected Behavior
User should be logged in and redirected to dashboard
```

## Best Practices

| Practice | Description |
|----------|-------------|
| **Be specific** | Vague tickets lead to misunderstandings |
| **Include acceptance criteria** | Clear definition of "done" |
| **Add context** | Future readers need background |
| **Link related tickets** | Traceability is important |
| **Update as you go** | Tickets are living documents |

## Related Skills

- [gitflow](../gitflow) - Git Flow branching automation
- [atomic-commits](../atomic-commits) - Clean commit messages

## License

MIT © [Carlos](https://github.com/jarero321)
