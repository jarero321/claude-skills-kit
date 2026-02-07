---
name: jira-ticket
description: Generate structured JIRA ticket templates for features, bugs, hotfixes, tasks, and spikes with acceptance criteria and test evidence sections.
license: MIT
metadata:
  author: carlos
  version: "1.0.0"
  tags:
    - jira
    - tickets
    - templates
    - agile
    - scrum
---

# JIRA Ticket Template Skill

Generate structured JIRA ticket templates based on context and ticket type.

## Commands

### /jira feature
Generate a Feature ticket template.

### /jira bug
Generate a Bug ticket template.

### /jira hotfix
Generate a Hotfix ticket template.

### /jira task
Generate a Task ticket template.

### /jira spike
Generate a Spike/Research ticket template.

### /jira integration-tests
Generate an Integration Tests evidence template based on the development context.

---

## Feature Template

```markdown
## Summary
[One-line description of the feature]

## Description
### Background
[Why is this feature needed? Business context]

### User Story
As a [type of user],
I want [goal/desire],
So that [benefit/value].

## Acceptance Criteria
- [ ] AC1: [Specific, testable criterion]
- [ ] AC2: [Specific, testable criterion]
- [ ] AC3: [Specific, testable criterion]

## Technical Notes
### Affected Components
- [ ] Frontend
- [ ] Backend
- [ ] Database
- [ ] Infrastructure

### Implementation Approach
[High-level technical approach]

### Dependencies
- [List any dependencies on other tickets or external factors]

## Out of Scope
- [What is explicitly NOT included]

## Design/Mockups
[Link to Figma/designs if applicable]

## Test Scenarios
1. [Happy path scenario]
2. [Edge case scenario]
3. [Error handling scenario]

## Evidencia de Pruebas Funcionales

### [Nombre del flujo/funcionalidad]
✅ **Caso de prueba:** [País/Contexto] - [Componente]

**Resultado esperado:** [Descripción de lo que debería ocurrir]

**Resultado obtenido:** [Descripción de lo que realmente ocurrió]

![Evidencia](ruta-imagen.png)

### [Otro caso de prueba]
✅ **Caso de prueba:** [País/Contexto] - [Componente]

**Resultado esperado:** [Descripción]

**Resultado obtenido:** [Descripción]

![Evidencia](ruta-imagen.png)

## Definition of Done
- [ ] Code implemented and reviewed
- [ ] Unit tests written and passing
- [ ] Integration tests passing
- [ ] Evidencia de pruebas funcionales adjunta
- [ ] QA approved
```

---

## Bug Template

```markdown
## Summary
[One-line description of the bug]

## Environment
- **Environment:** [Production/Staging/Development]
- **Browser/Device:** [Chrome 120, iOS 17, etc.]
- **User Type:** [Admin/Regular User/Guest]

## Steps to Reproduce
1. [First step]
2. [Second step]
3. [Third step]

## Expected Behavior
[What should happen]

## Actual Behavior
[What actually happens]

## Evidence
- Screenshot/Video: [Link]
- Error logs: [Link or paste]
- Console errors: [If applicable]

## Impact
- **Severity:** [Critical/High/Medium/Low]
- **Affected Users:** [Percentage or count]
- **Workaround Available:** [Yes/No - describe if yes]

## Technical Investigation
### Root Cause
[To be filled during investigation]

### Affected Code
- File: `path/to/file.ts`
- Function: `functionName()`

## Fix Approach
[Proposed solution]

## Regression Testing
- [ ] [Test scenario 1]
- [ ] [Test scenario 2]

## Evidencia de Pruebas Funcionales (Post-Fix)

### [Escenario de regresión]
✅ **Caso de prueba:** [País/Contexto] - [Componente]

**Resultado esperado:** [Comportamiento correcto después del fix]

**Resultado obtenido:** [Confirmación de que funciona correctamente]

![Evidencia](ruta-imagen.png)
```

---

## Hotfix Template

```markdown
## 🚨 HOTFIX - [Brief Description]

## Severity
**CRITICAL** - Requires immediate attention

## Issue Summary
[What is broken and its business impact]

## Affected Systems
- [ ] Production
- [ ] Staging
- [ ] Specific region/tenant

## Timeline
- **Detected:** [DateTime]
- **Reported by:** [Name/System]
- **Target Resolution:** [DateTime]

## Incident Details
### Symptoms
[What users are experiencing]

### Error Messages
```
[Paste relevant error messages/logs]
```

### Metrics Impact
- Error rate: [X%]
- Affected requests: [Count]
- Revenue impact: [If applicable]

## Root Cause
[Brief explanation of what went wrong]

## Fix
### Changes Required
1. [Change 1]
2. [Change 2]

### Files Modified
- `path/to/file1.ts`
- `path/to/file2.ts`

## Rollback Plan
[How to revert if fix causes issues]

## Deployment Steps
1. [ ] Code review approved
2. [ ] Hotfix branch created from main
3. [ ] Fix implemented and tested locally
4. [ ] Deploy to staging
5. [ ] Smoke test on staging
6. [ ] Deploy to production
7. [ ] Monitor metrics for 30 minutes
8. [ ] Merge to develop

## Evidencia de Pruebas Funcionales (Validación del Hotfix)

### [Escenario crítico corregido]
✅ **Caso de prueba:** [País/Contexto] - [Componente afectado]

**Resultado esperado:** [Comportamiento correcto después del hotfix]

**Resultado obtenido:** [Confirmación de que el issue está resuelto]

![Evidencia](ruta-imagen.png)

## Post-Mortem
- [ ] Schedule post-mortem meeting
- [ ] Document lessons learned
- [ ] Create follow-up tickets for permanent fix
```

---

## Task Template

```markdown
## Summary
[One-line description of the task]

## Description
[Detailed explanation of what needs to be done]

## Subtasks
- [ ] [Subtask 1]
- [ ] [Subtask 2]
- [ ] [Subtask 3]

## Technical Details
[Any technical specifications or requirements]

## Dependencies
- Blocked by: [Ticket IDs]
- Blocks: [Ticket IDs]

## Estimation
- **Story Points:** [X]
- **T-Shirt Size:** [S/M/L/XL]

## Definition of Done
- [ ] Task completed
- [ ] Code reviewed (if applicable)
- [ ] Documentation updated (if applicable)
```

---

## Spike Template

```markdown
## Summary
[Research question or investigation topic]

## Objective
[What are we trying to learn or decide?]

## Background
[Context and why this spike is needed]

## Questions to Answer
1. [Question 1]
2. [Question 2]
3. [Question 3]

## Research Areas
- [ ] [Area 1 - e.g., "Evaluate library X"]
- [ ] [Area 2 - e.g., "Performance benchmarks"]
- [ ] [Area 3 - e.g., "Security considerations"]

## Time Box
**Maximum:** [X hours/days]

## Expected Deliverables
- [ ] Technical document with findings
- [ ] Proof of concept (if applicable)
- [ ] Recommendation with pros/cons
- [ ] Estimation for implementation

## Success Criteria
[How do we know the spike is complete?]

## Findings
[To be filled after investigation]

### Recommendation
[Final recommendation based on research]
```

---

## Integration Tests Evidence Template

```markdown
## Evidencia de Pruebas de Integración

### Resumen de Componentes Afectados
| Componente | Tipo | Descripción |
|------------|------|-------------|
| [Componente 1] | Frontend/Backend/DB | [Breve descripción del cambio] |
| [Componente 2] | Frontend/Backend/DB | [Breve descripción del cambio] |

### Flujos Probados
- [ ] [Flujo 1: descripción del flujo E2E]
- [ ] [Flujo 2: descripción del flujo E2E]

---

### [Nombre del flujo de integración]
✅ **Test de integración:** [Contexto] - [Componentes involucrados]

**Componentes tocados:**
- `[path/to/component1.ts]` → [Función/Módulo afectado]
- `[path/to/component2.ts]` → [Función/Módulo afectado]

**Escenario:** [Descripción del flujo completo que se está probando]

**Resultado esperado:** [Descripción de lo que debería ocurrir en la integración]

**Resultado obtenido:** [Descripción de lo que realmente ocurrió]

**Estado:** ✅ Passed / ❌ Failed

![Evidencia](ruta-imagen.png)

---

### [Otro flujo de integración]
✅ **Test de integración:** [Contexto] - [Componentes involucrados]

**Componentes tocados:**
- `[path/to/component.ts]` → [Función/Módulo afectado]

**Escenario:** [Descripción del flujo]

**Resultado esperado:** [Descripción]

**Resultado obtenido:** [Descripción]

**Estado:** ✅ Passed / ❌ Failed

![Evidencia](ruta-imagen.png)

---

### Resumen de Resultados
| Test | Estado | Observaciones |
|------|--------|---------------|
| [Flujo 1] | ✅ Passed | - |
| [Flujo 2] | ✅ Passed | - |

### Cobertura de Integración
- **Endpoints probados:** [X/Y]
- **Flujos E2E cubiertos:** [X/Y]
- **Integraciones externas validadas:** [Lista si aplica]
```

---

## Usage Tips

1. **Be specific** - Vague tickets lead to misunderstandings
2. **Include acceptance criteria** - Clear definition of "done"
3. **Add context** - Future readers need background
4. **Link related tickets** - Traceability is important
5. **Update as you go** - Tickets are living documents
