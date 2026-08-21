# Task Management in the AI Coding Era

**English** | [简体中文](../04-task-management.md)

Traditional task systems often behave like lists used to allocate work to people. Once AI makes execution concurrency nearly instant, that model breaks: more work starts, review and integration queues grow, and real outcomes become harder to see.

AI-era task management should manage four things: **selection, flow, authority, and evidence**.

## Keep four kinds of object separate

```text
Outcome: the user or business result to change
  └─ Initiative: coordinated changes organized around that result
      └─ Task contract: an independently owned and verifiable unit of work
          └─ Execution attempt: one human or agent session
```

- An outcome may persist for months and be validated by metrics.
- An initiative coordinates tasks, teams, or rollout phases.
- A task is the task system's basic unit of responsibility.
- An agent session is an attempt that may fail, restart, or switch models.

Creating a ticket for every agent conversation produces noise. Giving a large outcome directly to an agent destroys boundaries. Stable IDs belong to tasks and initiatives, not temporary sessions.

## A work item is an outcome contract

A Ready task includes at least:

| Field | Purpose |
| --- | --- |
| Outcome | States what changes, not what gets generated |
| Evidence | Proves the problem is real |
| Scope and non-goals | Controls expansion and review cost |
| Constraints | Preserves product, data, security, compatibility, and operational boundaries |
| Acceptance criteria | Converts intent into decidable behavior |
| Verification plan | Declares evidence sources and independence |
| Owner and authority | Separates execution, decision, and release rights |
| Rollout and retirement | Connects production evidence and cleanup |

Use the [task contract template](../../templates/en/task-contract.md).

## Route work by shape

| Work shape | Route |
| --- | --- |
| Safe to finish and verify inside current scope | Fix now |
| Real and independently describable, but should not expand current scope | Backlog |
| Requires shared scope, phases, cross-team coordination, rollout, or release gates | Requirement or initiative |
| Lacks evidence and needs bounded learning | Discovery or spike |
| Invalid, superseded, or not valuable | Reject or retire |

Agents can discover, deduplicate, gather evidence, and recommend routing. Discovery does not authorize scope expansion.

## Turn a to-do list into an explicit workflow

```text
Discovery
→ Triage
→ Ready
→ In Progress
→ Verify / Review
→ Ready to Release
→ Observe
→ Done
```

Each state needs entry, exit, and WIP policies.

| State | Key question | Exit evidence |
| --- | --- | --- |
| Discovery | Is the problem real and worth continuing? | Evidence and outcome |
| Triage | Do now, defer, or reject? | Priority, owner, and route |
| Ready | Is it clear and executable? | Contract and known dependencies |
| In Progress | Is a bounded increment being produced? | Reviewable change set |
| Verify / Review | Does behavior and risk meet the standard? | Validation and approvals |
| Ready to Release | Can it safely enter the target environment? | Rollout, monitoring, rollback |
| Observe | Does reality support the hypothesis? | Production and user evidence |
| Done | Are learning and cleanup complete? | Documentation, follow-ups, retirement gates |

Low-risk work may combine states. Simplifying the board does not remove the responsibility.

## Constrain WIP by scarce verification capacity

Agents can start many implementations while domain review, integration environments, and security validation remain scarce.

- Stop starting implementation when the Verify queue is full.
- Help old work cross a bottleneck before selecting new work.
- Reserve review capacity for high-risk changes.
- Treat parallel agent attempts as internal to one task, not separate business WIP.
- Make every WIP exception explicit and temporary.

The [Kanban Guide](https://kanbanguides.org/the-kanban-guide/) requires explicit control of work between started and finished, using WIP, throughput, work item age, and cycle time to understand flow.

## Manage aging, not only deadlines

Show the age of every started item. Use historical cycle time to form a probabilistic Service Level Expectation—for example, “85% of standard items finish within eight days.” When an item approaches or exceeds the SLE, ask:

- Is it waiting for a dependency or decision?
- Is its scope growing?
- Is the verification environment missing?
- Should it be split, downgraded, canceled, or escalated?
- Is the agent continuing to generate without convergence?

Historical flow is often a better forecasting tool for uncertain software work than a single-point effort promise.

## Priority connects outcomes and cost

Consider:

- user or business value;
- time criticality;
- risk reduction or opportunity enablement;
- cost of delay;
- verification and coordination cost;
- reversibility and cognitive load;
- whether the work removes future WIP or dependencies.

“AI can do it quickly” is not a priority argument. Cheap implementation with expensive verification may consume more system capacity.

## Risk determines agent authority

| Risk | Example | Authority and gates |
| --- | --- | --- |
| Low | Copy, mechanical refactor, local tests | Continuous execution and self-check; author confirms |
| Medium | Normal business logic, internal interfaces | Agent implements; peer review and automation required |
| High | Authorization, payments, public API, migrations | Plan and key choices approved first; independent validation and progressive release |
| Extreme | Irreversible data or production safety boundary | Least privilege, two-person authorization, rehearsal, explicit release authority |

Authority is a task property, not merely a model property. The same agent should have different capabilities when editing tests and deleting production data.

## Triage new findings

```text
Real problem?
  ├─ No: record why it is invalid; do not pollute backlog
  └─ Yes
      ├─ In scope and verifiable: fix now
      ├─ Independently durable but not committed: backlog
      ├─ Needs coordination or approval: requirement / initiative
      └─ Insufficient evidence: time-boxed discovery
```

A backlog item must stand alone without the original conversation. Use the [backlog template](../../templates/en/backlog-item.md). Regularly remove duplicates, expired concerns, and work the organization will never pursue.

## Completion depth: demo-able is not done

AI makes the first working version very cheap, so the “done” signal arrives earlier. What got faster is the time to reach a **demo-able** state, not the time to reach a **production-worthy** one. Generated implementations cover happy-path patterns well and systematically under-serve boundary semantics, failure paths, and operational reality, so the distance between a demo and real completion usually widens rather than shrinks.

“The button exists and clicking it does something” is the shallowest layer, not completion.

### Depth levels

| Depth | Meaning | Exit evidence |
| --- | --- | --- |
| D0 Exists | Code merged, UI present, click produces a reaction | Screenshot or demo |
| D1 Happy path correct | Typical input produces the correct result | Automated tests against acceptance criteria |
| D2 Boundaries and failure paths correct | Empty, oversized, invalid input, concurrency, duplicate submission, retry, timeout, insufficient permission, partial failure, idempotency | Boundary tests and exploratory records |
| D3 Runs in the real system | Real data volume and legacy dirty data, migration and compatibility, performance, observability, rollback, multi-user and multi-tenant views | Pre-production or canary evidence |
| D4 Outcome validated | Target signals moved; old paths and temporary mechanisms removed | Production evidence and retirement record |

Depth is not a quality score. It is the **scope of the commitment**. A task contract must declare its target depth; without it, both humans and agents default to stopping at D0 or D1.

### Shallow-completion patterns to expect in the AI era

Asking about these finds real gaps faster than asking “is this code correct?”

- **Unclosed state:** a success state exists, but loading, empty, error, retry, disabled, and partial-failure states do not; failures are silently swallowed.
- **Only the mentioned inputs:** inputs named in the prompt are handled; unmentioned input types, boundary values, concurrency, and duplicate submissions are skipped.
- **Tests derived from the implementation:** assertions restate the code instead of the requirement—high coverage, no independent oracle.
- **Correct only on demo data:** passes on small clean datasets and fails at real volume, on legacy dirty data, or across tenants and time zones.
- **Single-perspective validation:** verified only as the author, with admin rights, on desktop, in the default locale.
- **Additions without removals:** the new path ships while the old path, dual writes, migration scripts, feature flags, and dead code remain.
- **Missing operability:** no logs, metrics, alerts, audit trail, or diagnostic entry point when something breaks.
- **Documentation and configuration drift:** behavior changed; current-state docs, runbooks, alert thresholds, and permission configuration did not.
- **Locally done, integration undone:** every slice passes its own checks and nobody owns the combined behavior.
- **Deep omissions:** performance and N+1 queries, concurrent writes, time zones and units, localization, accessibility, data retention and deletion.

### Risk and reversibility set the required depth

| Work type | Reasonable target depth |
| --- | --- |
| One-off internal script, copy change, throwaway prototype | D1 |
| Normal internal feature, low-risk business logic | D2 |
| User-facing feature, cross-team interface | D3 |
| Authorization, payments, data migration, public API, security boundary | D3, and must reach D4 |

Do not force maximum depth on every task. Excess depth consumes the team's scarcest verification capacity and crowds out genuinely high-risk work; insufficient depth pushes cost into future rework, incidents, and other teams. Teams delivering one product must agree on a minimum target depth, or one team's “done” becomes another team's invisible queue—see [team collaboration](03-team-collaboration.md).

### Make depth operational

- Write the **target depth** and the **explicitly excluded depth** into the task contract; excluded parts become backlog items with an owner and a review date.
- State acceptance criteria as observable behavior under stated conditions, not as “implement feature X.”
- Do not let the same agent session that wrote the implementation generate the tests for high-risk behavior; use a separate session and derive tests from the requirement rather than the diff to keep the oracle independent.
- The first review question is “what is missing?” rather than “is this code correct?”—which inputs, states, failure paths, and user perspectives are uncovered.
- Completion must carry evidence links. Done is an evidenced claim, not a status click.
- Use the [completion depth checklist](../../templates/en/completion-depth-checklist.md) so depth does not depend on individual habits.
- Treat shallow completion as a system signal, not a personal failing: watch reopen rate, patch tasks spawned shortly after Done, escaped defects, and review rework.

## Definition of Ready

- Outcome, owner, and priority are clear.
- Critical evidence is accessible.
- Scope, non-goals, and agent authority are explicit.
- Acceptance criteria are verifiable.
- The target completion depth and its verification method are explicit.
- Dependencies name the blocking point, the way it is removed, and who owns it—see the [dependency map](../../templates/en/dependency-map.md).
- Major unknowns are identified.
- The task fits the current feedback cycle.

## Definition of Done

- Acceptance criteria have risk-appropriate evidence.
- The declared target depth is reached; any depth not reached is recorded explicitly with an owner and a review date.
- Boundary, failure-path, and operability results are inspectable, not just a happy-path demo.
- Scope deviations are explained and authorized.
- Code, tests, current documentation, and runtime configuration agree.
- Release, rollback, and required observation are complete.
- Out-of-scope findings have explicit disposition.
- Temporary mechanisms are gone or have an owner and removal gate.

Multiple teams delivering one product should share a minimum Definition of Done; otherwise one team's “done” becomes another team's invisible queue. [Scrum Guide](https://scrumguides.org/scrum-guide.html)

## What to measure

- Outcome attainment, not only closure count;
- lead time from Ready to production evidence;
- waiting time and work item age in each state;
- throughput, cycle time, and WIP;
- review rework, scope expansion, and reopen rate;
- patch tasks spawned shortly after Done (a shallow-completion signal);
- share of waiting time caused by dependency or decision blocks;
- generation time relative to verification time;
- failed releases, rollback, and production defects;
- legacy mechanisms that survive past their removal gate.

Do not use story points, lines of code, agent calls, or task closures as individual performance measures. [SPACE](https://www.microsoft.com/en-us/research/publication/the-space-of-developer-productivity-theres-more-to-it-than-you-think/) shows why productivity cannot be reduced to one activity metric.

A good AI-era task system does not make everything start faster. It makes the most valuable work finish more reliably.
