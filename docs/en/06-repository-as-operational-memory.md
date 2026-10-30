# Keeping Development Memory in the Repository

**English** | [简体中文](../06-repository-as-operational-memory.md)

The next development session should not need to reconstruct everything from chat. A repository can preserve code-related behavior, unfinished work, and rationale for people and agents to retrieve as needed. Customer, personnel, and sensitive operational records still belong in appropriate controlled systems.

## Four records, four questions

| Example location | Question | Update rule |
| --- | --- | --- |
| `docs/<feature>/` | How does it work now? | Rewrite when behavior changes. |
| `docs/change_log/` or existing ADRs | Why this change or design? | Retain useful tradeoffs; durable decisions outlive short-term records. |
| `BACKLOG.md` | Which known issues are deferred? | Record evidence, deferral reason, and fix; close after verification. |
| `requirement_doc/<series>/` | What contract governs coordinated work? | Specify scope, acceptance, phases, and gates; distinguish proposed from approved. |

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
