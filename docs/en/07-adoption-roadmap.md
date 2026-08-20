# Adoption Roadmap

**English** | [简体中文](../07-adoption-roadmap.md)

AI-native development does not require an immediate reorganization. Begin with one team, one repository, and a few frequent task types. Build trustworthy feedback loops in stages.

## Stage 1: Establish safety boundaries

- Define data, secret, vendor, and licensing boundaries.
- Define approval rules for destructive actions, production changes, and external communication.
- Make every AI-assisted change traceable to a human owner.
- Begin with low-risk, easily verified tasks.

**Completion signal:** people know when they may continue autonomously and when they must stop and escalate.

## Stage 2: Organize repository context

- Add short, accurate current-state documentation for critical domains.
- Keep local rules close to relevant code; avoid one infinite global instruction file.
- Separate present behavior, future plans, deferred work, and historical rationale.
- Remove obviously stale, conflicting, and duplicate documentation.

**Completion signal:** a new participant can locate authoritative context without oral history.

## Stage 3: Standardize task contracts

- Use a common template for medium- and high-risk work.
- Define Ready, Done, and scope-expansion policies.
- Establish fix-now, backlog, discovery, and requirement routes.
- Use stable IDs across tasks, PRs, release evidence, and decisions.

**Completion signal:** review discussions focus on real tradeoffs rather than repeatedly reconstructing task background.

## Stage 4: Automate verification and policy

- Shorten unit, integration, and end-to-end feedback.
- Automate formatting, link, schema, permission, and release-policy checks.
- Add independent validation and rollout evidence for high-risk changes.
- Require agents to distinguish verified facts, inference, and unverified assumptions.

**Completion signal:** common defects are found before scarce human review attention is consumed.

## Stage 5: Connect production evidence and retirement

- Link releases, operational signals, migrations, and legacy traffic to tasks.
- Give feature flags and compatibility layers owners and removal gates.
- Review code, documentation, and process that has reached retirement conditions.
- Feed production deviations back into current docs and verification.

**Completion signal:** the team can delete old paths safely with evidence instead of preserving everything “just in case.”

## Pilot selection

Choose a domain with a clear owner, stable but imperfect tests, enough work to observe change, controllable risk, real maintenance cost, and a team willing to record a baseline.

Run the pilot for 6–12 weeks before generalizing to every software context.

## Suggested measures

| Dimension | Example |
| --- | --- |
| Speed | Median time from Ready to production evidence |
| Rework | Review rounds and reopened tasks |
| Scope | Unauthorized scope-expansion rate |
| Quality | Escaped defects, rollback, incidents, recovery time |
| Context | Queries and human explanations before effective work starts |
| Documentation | Broken links, code/doc conflicts, duplicate facts |
| Lifecycle | Legacy survival time after the removal gate |
| Economics | Model, compute, and human cost per trustworthy outcome |

Record a baseline before intervention. Use measures to learn about the system, not to reward superficial AI adoption.

## Monthly review questions

1. Which tasks produced the most rework because their intent was unclear?
2. Where is the current bottleneck: generation, review, testing, release, or production feedback?
3. Which agent assumptions fail repeatedly, and can local context or automation prevent them?
4. Which rules are stale or produce low-value ceremony?
5. Which temporary mechanisms have reached removal conditions?
6. Which high-risk decisions lack a clear owner or independent evidence?

Maturity is not the highest automation ratio. It is the ability to continuously deliver software that is understandable, verifiable, operable, and safely removable—with lower cognitive cost.
