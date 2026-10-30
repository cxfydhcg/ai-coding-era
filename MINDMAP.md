---
title: Software Development in the AI Era
markmap:
  colorFreezeLevel: 2
  initialExpandLevel: 2
  maxWidth: 320
  spacingHorizontal: 100
  spacingVertical: 10
---

# Software Development in the AI Era

## [简体中文](https://cxfydhcg.github.io/ai-coding-era/)

## [Individual workflow](docs/en/02-individual-workflow.md)

- Confirm the problem and current behavior
- Define outcome, scope, constraints, and acceptance
- Implement in small steps; verify according to risk
- Review, release, observe, and clean up
- [Task template](templates/en/task-contract.md)

## [Team collaboration](docs/en/03-team-collaboration.md)

- Assign verifiable outcomes
- Distinguish contract, sequence, resource, and decision dependencies
- Agree on interfaces before parallel work
- Fakes enable early checks; real integration remains necessary
- Name blocker and integration owners
- [Dependency map](templates/en/dependency-map.md)

## [Task management](docs/en/04-task-management.md)

- Prioritize value, risk, and complete delivery cost
- Limit work in progress by verification capacity
- Agree on completion depth before execution
  - D0 Demonstrable
  - D1 Happy path correct
  - D2 Boundaries and failures correct
  - D3 Operates in the real system
  - D4 Outcome observed
- Status changes cannot replace missing evidence
- [Completion checklist](templates/en/completion-depth-checklist.md)
- [Backlog template](templates/en/backlog-item.md)

## [Organization design](docs/en/05-organization-structure.md)

- Domains retain responsibility for outcomes
- Shared platforms reduce duplication and waiting
- Add capabilities when needed, not by headcount thresholds
- Clarify services and decision boundaries
- Improve recurring blocking points

## Reference as needed

- [Core principles](docs/en/01-core-principles.md)
- [Repository memory](docs/en/06-repository-as-operational-memory.md)
- [Record lifecycle practice](docs/en/08-record-lifecycle.md)
  - Four record types with separate responsibilities
  - Report → reviewed diff → scheduled maintenance
  - Release evidence, manual gates, and deletion tests
  - [Record policy template](templates/en/record-lifecycle-policy.md)
- [Small trials](docs/en/07-adoption-roadmap.md)
- [Research and evidence boundaries](docs/en/00-research-foundation.md)
- [Decision template](templates/en/decision-record.md)
