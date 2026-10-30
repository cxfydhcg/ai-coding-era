# Record Lifecycle Policy Template

**English** | [简体中文](../record-lifecycle-policy.md)

Copy the policy section into your repository's existing documentation policy. Replace every bracketed value, remove unused lanes, and link to it from assistant instructions. This is a policy template, not an installer. See the [adoption playbook](../../docs/en/08-record-lifecycle.md) for examples and automation acceptance cases.

## Policy

- Maintainer: [role or team]
- Repository task index: [path linked from README and assistant instructions]
- Current progress: [section within each task record; update at milestones, blockers, and before pausing]
- Current behavior: [path]
- Significant change history: [path]
- Durable decisions: [existing ADR location, or retained change records]
- Independently deferred work: [repository backlog path; link external trackers for association]
- Coordinated future work and completion evidence: [requirement location]

One fact has one canonical home. Current docs describe present behavior; plans clearly distinguish proposed, approved, and implemented work. Promotion transfers evidence and removes the duplicate task. Before editing, retrieve open work against the affected paths. Fix adjacent work only within the authorized task boundaries; retain work requiring a new product, schema, or cross-system decision.

## Release and retention

- Production evidence: [exact tag grammar or immutable deployment record]
- Excluded evidence: [preview/prerelease/local builds]
- Release timestamp source: [deployment time or documented approximation]
- Checked backlog items: [verification required, then release evidence before pruning]
- Completed requirements: [duration] after [first release containing completion]; retain while gates or references remain.
- Change records: [duration] after [landing/release]; retain unresolved fallout and still-needed rationale.
- Current docs and durable decisions: [review trigger]; no blanket age-based deletion.
- Unavailable, malformed, or ambiguous evidence: retain and report.

## Gates and source coverage

- Source roots, native plugins, and other temporary-code locations: [paths]
- Changes requiring contract docs: [schema/API/permissions/etc.]
- Marker grammar and parser: [location, supported conditions]
- Client rollout evidence and accountable verifier: [source and role]
- Independently deployed dependency evidence: [source and role]
- Migration retirement: verify application, fresh installs, accepted backup repair, and rollback/support obligations. Keep necessary repairs and seeds.

The sweep proposes record maintenance. It does not delete application code, infer a fleet version, or close a manual gate. A marker becoming due starts a reviewed implementation task.

## Daily workflow and automation

- Session report: [actual command, or manual review]
- Path-based backlog lookup: [actual command, or search procedure]
- Before-commit checks: [tests, links, indexes, generated skill validation]
- Assistant fallback when hooks are unavailable: [entry file and explicit steps]
- Schedule and report destination: [cadence and location]
- Application mode: [command, restricted to a maintenance branch]
- Reviewer: [role]; merge authority: [role]
- PR creation account and repository policy verified by: [successful real maintenance PR]
- Fallback when automation cannot open a PR: [maintainer procedure]

Only list commands that actually exist. Keep a single editable source for duplicated assistant rules; name generated copies and the synchronization command if used.

## Pilot acceptance

- [ ] Without the original chat, a new person or agent can find the goal, progress, next action, and verification method in the repository.
- [ ] Production and preview evidence are distinguished in tests.
- [ ] Missing metadata, open gates, and unresolved references retain records.
- [ ] Report mode is read-only; application mode is idempotent.
- [ ] Source coverage and local table/link formats have regression tests.
- [ ] The maintenance diff passes document checks and reaches a reviewed PR.
- [ ] No application code is removed by the record sweep.
- [ ] Review date: [date]; evidence and policy owner: [location and role].
