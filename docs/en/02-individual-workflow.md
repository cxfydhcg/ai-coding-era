# Individual Workflow: Finish One Change Properly

**English** | [简体中文](../02-individual-workflow.md)

I want AI to handle clear, verifiable execution so I can concentrate on intent, consequential choices, and results. Ambiguous work needs joint clarification; well-bounded work is easier to delegate continuously.

## The daily loop

```text
Confirm the problem → Recover context → Define completion
→ Implement and verify in small steps → Review and release → Observe and clean up
```

| Step | Action | Ready to continue when |
| --- | --- | --- |
| Confirm | Read original feedback, logs, or a reproduction; name the behavior to change. | The problem is real and worth addressing now. |
| Recover context | Resume from the repository task record; read relevant code, tests, rules, and issues. | Current behavior, impact, and unknowns are understood. |
| Define completion | Set the outcome, exclusions, constraints, acceptance, and authority. | Another person could judge completion. |
| Implement and verify | Change one inspectable behavior, run useful nearby checks, and inspect the diff. | Results match expectations and failures remain visible. |
| Review and release | Check scope, configuration, docs, and release conditions. | Risks have owners; failure can be stopped or recovered. |
| Observe and clean up | Check user and system results; update docs and temporary mechanisms. | Evidence supports the result and remaining work has a home. |

A small edit can cover this in one session; it does not need six documents. Use the [task template](../../templates/en/task-contract.md) for more complex work.

## Make acceptance concrete

An illustrative task:

```text
Outcome: a failed order-list request shows a retryable error.
Scope: loading and error display; no sorting or API changes.
Acceptance: a successful empty response shows the empty state;
a timeout or malformed response shows an error; a successful retry restores the list.
Verification: test the three responses and exercise retry in the actual UI.
```

This is easier to delegate than “improve error handling.” It also exposes an implementation that silently converts parse failures into empty arrays.

## Choose the collaboration mode

- **Implement yourself, ask AI to review:** a short change or familiar critical details.
- **Work together:** product semantics, design, or risk still needs discussion.
- **Delegate continuously:** scope, acceptance, and verification are available.
- **Investigate in parallel:** evidence can be gathered independently; reconcile it before deciding.

Limit concurrency by your ability to review. If work grows or repeatedly fails, revisit assumptions, boundaries, and the verification method before generating more.

## Review what is missing

Beyond the happy path, select checks for timeout, duplicate submission, concurrency, permissions, legacy data, and recovery according to risk. Expected results should come from requirements or independent evidence. This matters especially for payments, authorization, and migrations.

Small changes shorten feedback and make course correction easier, a direction supported by [DORA's small-batch guidance](https://dora.dev/capabilities/working-in-small-batches/). Choose verification depth for the actual task.

Before pausing or handing off, write progress, next actions, and verification results back to the repository task record. The handoff should say what changed, what was verified, and what remains unverified. If production observation comes later, name its owner, signal, and check time, and keep that work pending. See [task management](04-task-management.md) for completion depth and the [record lifecycle](08-record-lifecycle.md) for maintaining context.
