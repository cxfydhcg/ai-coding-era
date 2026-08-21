---
title: Evolving Software Development in the AI Coding Era
markmap:
  colorFreezeLevel: 2
  initialExpandLevel: 2
  maxWidth: 320
  spacingHorizontal: 100
  spacingVertical: 10
---

# Evolving Software Development in the AI Coding Era

## [中文 / Chinese](https://cxfydhcg.github.io/ai-coding-era/)

## Start here

### [Research foundation](docs/en/00-research-foundation.md)

- AI outcomes depend on task and system context
- AI amplifies strengths and bottlenecks
- Measure the whole delivery lifecycle

### [Core principles](docs/en/01-core-principles.md)

- Outcomes over code volume
- Intent before generation
- Evidence over confidence
- Bounded agency
- Deletion is first-class work

## [1. Individual software development lifecycle](docs/en/02-individual-workflow.md)

### Select the problem

- Start from user, business, or operational evidence
- Define the observable outcome

### Understand before changing

- Recover local context
- Separate facts, inferences, and unknowns
- Choose human-led, pairing, delegated, or parallel mode

### Contract and design

- Outcome, scope, non-goals
- Constraints and acceptance criteria
- Risk, reversibility, rollout, rollback

### Implement and verify

- Small behavioral slices
- Static → unit → integration → end-to-end
- Independent oracle for high-risk behavior

### Deliver and learn

- Self-review and team review
- Progressive release
- Production observation
- Update memory and retire temporary mechanisms

## [2. Collaborative software development lifecycle](docs/en/03-team-collaboration.md)

### Shared discovery

- Product, design, engineering, support, operations
- One outcome and common success signals

### Shared contract

- Technical discovery
- Cross-functional Definition of Done
- Explicit decision rights

### Slice, assign, decouple

- Duration shifted: implementation shrank, verification and waiting grew
- Assign outcomes and decision rights, not hours
- Vertical slices, not functional handoffs
- Four dependency types
  - Contract
  - True sequence
  - Resource and environment
  - Knowledge and decision
- Decoupling moves
  - Contract first
  - Mocks and fakes
  - Expand → migrate → contract
  - Feature flags
  - Reverse slicing
  - Single writer
- Make blocks visible and escalate on age
- Undecided semantics cannot be parallelized

### Parallel delivery

- Interface contracts and ownership
- Continuous integration in small batches

### Risk-oriented review and release

- Automation and AI check mechanics
- Humans review semantics and risk
- Independent validation for consequential changes

### Production learning

- Compare reality with the original outcome
- Feed evidence back into tasks, tests, and docs
- Retire flags, compatibility paths, and stale context

## [3. Task management](docs/en/04-task-management.md)

### Keep the levels distinct

- Outcome
  - User or business result
- Initiative
  - Coordinated set of changes
- Task contract
  - Durable, owned, verifiable work unit
- Execution attempt
  - One human or agent session

### Route by work shape

- Fix now
- Backlog
- Requirement or initiative
- Discovery or spike
- Reject or retire

### Manage explicit flow

- Discovery → Triage → Ready
- In Progress → Verify
- Ready to Release → Observe → Done

### Protect the bottleneck

- WIP follows verification capacity
- Manage work item age and blocked queues
- Use historical cycle time and probabilistic SLEs

### Completion depth

- D0 exists: click produces a reaction
- D1 happy path correct
- D2 boundaries and failure paths
- D3 runs in the real system
- D4 outcome validated and old paths removed
- Contract declares target depth
- Risk and reversibility set required depth
- Shallow-completion patterns
  - Only the mentioned inputs
  - Tests derived from the implementation
  - Correct only on demo data
  - Missing operability
  - Additions without removals
- Done is an evidenced claim, not a status click

### Match authority to risk

- Low: agent executes, author confirms
- Medium: peer review and automation
- High: approved plan, independent validation
- Extreme: least privilege and two-person authority

## [4. Team architecture](docs/en/05-organization-structure.md)

### Stable ownership unit

- A person owns a task
- A stable team owns a long-lived system
- An agent is a capability, not an accountable owner

### Four team capabilities

- Stream-aligned domain team
  - Owns design, build, run, and improve
- Platform team
  - Secure self-service delivery and agent infrastructure
- Enabling team
  - Time-bounded capability transfer
- Complicated-subsystem team
  - Specialist capability behind a stable boundary

### Three interaction modes

- Collaboration
  - Temporary joint discovery
- X-as-a-Service
  - Stable self-service relationship
- Facilitation
  - Help another team become independent

### Centralize selectively

- Central: model gateway, identity, policy, audit, common platform
- Local: user outcome, domain rules, task scope, release ownership

### Governance as guardrails

- Clear AI stance
- Least privilege and explicit approval
- Provenance, licensing, security, incident standards
- Automated policy where judgment is not required

## Shared system

### [Repository as operational memory](docs/en/06-repository-as-operational-memory.md)

- Present: code and current-state docs
- Approved future: task contracts and requirements
- Deferred future: backlog
- Relevant past: decision records
- Operational reality: production evidence
- One active canonical record per lifecycle state

### Ready-to-use templates

- [Task contract](templates/en/task-contract.md)
- [Completion depth checklist](templates/en/completion-depth-checklist.md)
- [Dependency and slice map](templates/en/dependency-map.md)
- [Backlog item](templates/en/backlog-item.md)
- [Decision record](templates/en/decision-record.md)

### [Adoption roadmap](docs/en/07-adoption-roadmap.md)

- 1. Safety boundaries
- 2. Repository context
- 3. Task contracts
- 4. Automated verification and policy
- 5. Production evidence and retirement

## One-sentence model

### Humans own intent, consequential judgment, and production authority

### Agents retrieve, propose, implement, and verify inside explicit boundaries

### Automation supplies fast, repeatable evidence

### Production reality closes the loop
