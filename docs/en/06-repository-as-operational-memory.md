# Repository as Handoff: Resume with Any Person or Agent

**English** | [简体中文](../06-repository-as-operational-memory.md)

The repository must preserve enough state to continue: intent, planned work, progress, blockers, and the next verification step. Use chat for discussion, then write decisions and progress back to the repository. They must not exist only in a session, private notes, or one agent's memory.

## Provide one entry point

Link the README and assistant instructions to the same task index, then to each task or requirement record. Reuse an existing index instead of creating a parallel board. The index provides navigation; each task record owns its current state:

| What a successor needs | What to record |
| --- | --- |
| What and why | Outcome, scope, acceptance, and settled decisions. |
| Current progress | Done, in progress, and not started; distinguish implemented from verified. |
| Where to resume | An accessible branch, commit, or PR, and the next concrete action. |
| What blocks progress | Dependencies, pending decisions, owners, and authority boundaries. |
| How to verify | Environment setup, commands, results, evidence locations, and last update. |

The current executor updates this record after a milestone, changed decision, blocker, or before pausing. Replace stale state rather than appending a chat transcript. At handoff, save code and records to a branch the successor can access; local uncommitted work is not a completed handoff.

The successor reads the entry point, checks the branch, diff, and verification results, records taking ownership, and continues. Resolve disagreements between records and code first. Parallel workers need explicit task ownership to avoid duplicate execution. Customer, personnel, secret, and sensitive operational data stay in controlled systems; the repository provides the necessary access and verification instructions.

**Handoff acceptance: without the original chat, an appropriately authorized new person or agent can identify the goal, current state, next action, and verification method. If not, the repository record is incomplete.** The [task template](../../templates/en/task-contract.md) includes a progress section.

## Four records, four questions

| Example location | Question | Update rule |
| --- | --- | --- |
| `docs/<feature>/` | How does it work now? | Rewrite when behavior changes. |
| `docs/change_log/` or existing ADRs | Why this change or design? | Retain useful tradeoffs; durable decisions outlive short-term records. |
| `BACKLOG.md` | Which known issues are deferred? | Record evidence, deferral reason, and fix; close after verification. |
| `requirement_doc/<series>/` | What contract governs coordinated work, and how far has it progressed? | Distinguish proposed from approved; specify acceptance and gates, and update progress and next actions. |

Names can differ; responsibilities should be clear. Code, tests, and schema help establish current behavior, while explicitly authoritative external contracts constrain implementation. Resolve disagreements and correct the wrong side rather than silently choosing a source.

## Move information with the work

```text
Discover → Defer → Contract when coordination is needed
→ Implement and verify → Update current behavior and rationale
→ Observe release → Retire obsolete records
```

Promotion transfers backlog evidence into the requirement instead of maintaining two task descriptions. A completed spec may temporarily retain acceptance and rollout evidence; it does not replace current docs. Git and PRs preserve history while everyday navigation keeps what still changes decisions.

## Describe automation accurately

Path queries retrieve relevant backlog. Checkers find broken links, missing index entries, and omitted contract updates. Sweeps propose maintenance under deterministic rules. None proves product correctness or turns a release tag into evidence that every device upgraded.

Put steps unsupported by the assistant's tools in its entry instructions. Copying a skill does not install hooks; a reminder does not enforce execution. Keep one editable source for shared assistant rules and validate generated copies.

## Give temporary mechanisms an exit

Record their purpose, dependencies, removal conditions, and verification. Old clients, offline queues, and accepted backups can survive a release. Once gates are satisfied, remove code in a reviewed implementation change; do not delete it based on age.

The [record lifecycle walkthrough](08-record-lifecycle.md) covers layouts, markers, and retirement rules. Test context retrieval on one real task before adding automation.
