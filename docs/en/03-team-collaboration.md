# Team Collaboration: Resolve Dependencies Before Adding Parallel Work

**English** | [简体中文](../03-team-collaboration.md)

Faster individual implementation may not shorten team delivery. When work waits for interfaces, decisions, or review, starting more tasks adds waiting. Locate the delay before deciding how to divide the work.

## Assign verifiable outcomes

Product, design, and engineering agree on the user problem, success conditions, and exclusions. Split work into increments that can be demonstrated, verified, or released independently, rather than only frontend and backend tickets.

Each increment names an accountable owner, executor, verification method, and integration owner. One person can cover several roles for low-risk work; consequential changes need independent validation. Agree on [completion depth](04-task-management.md) so one person's completion does not become another's hidden backlog.

## Distinguish four dependencies

| Blocking point | Response |
| --- | --- |
| Undefined interface or data format | Agree on fields, error semantics, versions, and acceptance samples; then implement against the contract. |
| Required sequence of data or runtime changes | Expand compatibility, migrate, then remove the old path; verify recovery conditions at each step. |
| Shared device, environment, account, or reviewer | Make the queue and capacity explicit; consider self-service environments when the problem repeats. |
| Undecided product behavior or risk | Name a decision-maker and deadline; escalate on expiry. Continue only under an already-approved default. |

Unsettled semantics need a decision. Parallel agents guessing independently produce incompatible answers.

## A cross-application example

This illustrates POS and staff-app coordination; it is not a record of a particular release.

```text
Agree: request, response, errors, minimum POS version
                         ↓
Staff app: implement against samples/fake ──┐
POS: implement the real endpoint ──────────┤ Real integration → Joint acceptance → Ordered rollout
```

A fake service starts UI and boundary testing earlier; real integration remains necessary. Define success, timeout, and unsupported-version behavior in the contract. If the new staff app requires a new POS, release order still matters. Give any compatibility path or flag an exit condition.

Use the [dependency map](../../templates/en/dependency-map.md) to record the blocking point, who removes it, and when integration happens. Assign one editor for the current change to shared schema, configuration, or core files to reduce overlapping edits.

## Integrate early

Use small batches and short branches; connect real implementations early. Passing slice-level tests still leaves someone responsible for combined behavior. Divide review simply:

- Automation checks formatting, types, and known rules.
- Domain reviewers check acceptance, failures, and data consequences.
- Authorized people decide release and residual risk.

AI can assist at every layer. Passing tests and AI review do not settle outstanding domain judgments.

## Discuss blockers and outcomes

At each sync, ask which task is stuck, which interface or decision blocks it, and who can unblock it. Waiting counts toward task age. When it exceeds an agreed threshold, adjust scope, split the work, or escalate.

Before release, name observation signals, stop conditions, and an owner. Afterward, compare results with intent and turn discrepancies into tests, docs, or follow-up work. Persistent delays at team boundaries suggest an [organization-design problem](05-organization-structure.md); a review backlog calls for [work-in-progress limits](04-task-management.md).
