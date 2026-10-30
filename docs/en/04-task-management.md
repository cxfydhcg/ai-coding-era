# Task Management: Control Starts and Define Completion

**English** | [简体中文](../04-task-management.md)

I treat a task as an owned, bounded, verifiable outcome. An agent conversation is an execution attempt; goals, progress, blockers, next actions, and evidence live in the repository's task record. A different person or agent resumes from that record; see [repository handoff](06-repository-as-operational-memory.md).

## Select worthwhile work

Consider user impact, urgency, risk reduction, and the cost of complete delivery: understanding, implementation, verification, coordination, and release. Fast code generation alone does not justify priority.

| Finding | Disposition |
| --- | --- |
| Within current authority and verifiable now | Fix now. |
| Real and independently actionable, but deferred | Backlog with evidence, deferral reason, and a concrete fix. |
| Needs shared interfaces, phases, rollout, or product decisions | Requirement contract identifying decisions not yet approved. |
| Insufficient evidence | Time-boxed investigation with a specific question. |
| Invalid or no longer worth doing | Remove or close with a reason. |

Before starting, name the outcome, scope, constraints, acceptance, and owner. Complex work also needs dependencies, authority, and release plans. Use the [task template](../../templates/en/task-contract.md).

## Make waiting visible with few states

```text
Needs clarification → Ready → Implementing → Verifying → Release/observation pending → Done
```

Ready means acceptance is clear and critical dependencies have a plan. Done means the agreed verification depth was reached. Small tasks can combine states; renaming a column cannot complete a missing device check or production observation.

Limit work that has started but not finished (WIP). When verification is full, prioritize review, integration, and unblocking older work. Several parallel agents do not represent several completed business outcomes.

Show task age, its blocking point, and who can remove it. With enough history, use cycle time to forecast delivery ranges. WIP, throughput, work item age, and cycle time are basic flow measures in the [Kanban Guide](https://kanbanguides.org/the-kanban-guide/); experiment locally with limits and escalation thresholds.

## Agree on completion depth

This is a checking method used in these notes, not an industry standard. Depth describes the task's commitment, not a team score.

| Depth | What must be established | Example evidence |
| --- | --- | --- |
| D0 Demonstrable | The feature exists and reacts. | A demo; insufficient alone to establish correctness. |
| D1 Happy path correct | Typical input meets acceptance. | Behavioral tests or reproducible verification. |
| D2 Boundaries and failures correct | Relevant errors, permissions, duplicates, and concurrency are handled. | Boundary tests, fault injection, or exploration records. |
| D3 Operates in the real system | Data, dependencies, compatibility, performance, and recovery meet the need. | Real integration, pre-production, or limited rollout. |
| D4 Outcome observed | User or system results are verified and temporary mechanisms addressed. | Production evidence; removal records or retained mechanisms with owners and gates. |

A prototype may target D1. User-facing features commonly need D2 and D3; payments, authorization, and migrations also need follow-up observation. Consequences and reversibility set depth: even a one-off deletion script may be high risk.

If the commitment is D3, moving unfinished integration testing into backlog does not complete it. Changing the commitment requires an explicit decision. Mark irrelevant checks as not applicable with a reason instead of creating unnecessary tasks.

## Look for four omissions

- **States:** what happens on empty results, errors, timeout, retries, and partial success?
- **Perspectives:** does it work for ordinary users, other tenants, legacy data, and real volume?
- **Circular evidence:** do tests merely restate the implementation? Where do expected results come from?
- **Delivery:** who owns integration, configuration, diagnosis, recovery, and temporary paths?

A separate agent session can add another perspective. Independent evidence still comes from contracts, real samples, domain judgment, or independent calculations. Select relevant items from the [completion checklist](../../templates/en/completion-depth-checklist.md).

## Authority and evaluation

State what the agent may complete continuously, which new decisions require authorization, and who may release. Authority follows consequences, not model names; do not reapprove already-authorized steps.

Track delivery time, waiting, rework, escaped defects, and user results. Avoid judging individuals by code volume, agent calls, or closure counts alone. [SPACE](https://www.microsoft.com/en-us/research/publication/the-space-of-developer-productivity-theres-more-to-it-than-you-think/) likewise argues against reducing productivity to a single activity metric.
