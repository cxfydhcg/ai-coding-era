# From Code Repository to Operational Memory

**English** | [简体中文](../06-repository-as-operational-memory.md)

## A software lifecycle for collaboration between humans and AI agents

AI coding agents can participate in analysis, implementation, review, testing, documentation, and maintenance. The long-term challenge is usually not generating the next block of code. It is answering correctly: Why does the system work this way? Which behavior is current reality and which is a future plan? When can a compatibility path be removed? Does a newly discovered problem belong to the current task?

Those answers are often fragmented across chat, issues, pull requests, documents, monitoring systems, and personal memory. Human teams have compensated through relationships and oral history. An agent entering a temporary task does not have that continuity.

An AI-native lifecycle therefore converts necessary context into versioned, retrievable, verifiable artifacts that move with the lifecycle.

## Expand the repository's role

A repository should help people and agents answer:

- What does the system do now?
- How should it be developed, tested, and operated today?
- Which future changes have been approved?
- Which known problems are deferred?
- Which past decisions still affect current work?
- Which production evidence permits release or retirement?

This does not place all organizational knowledge in Git. Personnel, customer, financial, and sensitive operational data remain in appropriate controlled systems. The principle is **repository-native, not repository-only**.

## Separate knowledge by temporal semantics

| Artifact | Time semantics | Question answered |
| --- | --- | --- |
| Source code and schema | Present | What does the system actually do? |
| Current-state docs | Present | How should it be understood and operated now? |
| Task contract or requirement | Approved future | What have we committed to change? |
| Backlog | Deferred future | What is known but not committed? |
| Decision record | Relevant past | Why did we choose the current direction? |
| Git and PR | Full history | How did implementation and discussion evolve? |
| Production evidence | Operational reality | Does the real environment support our judgment? |

```text
requirement       → approved future
current docs      → present
decision/change   → still-relevant past
Git / PR          → full historical evidence
production signal → operational reality
```

When a requirement is implemented, detailed future intent should be compressed into current behavior and durable rationale. Git preserves the complete process.

## Operational memory is not one giant document

An ever-growing master document becomes noise. Useful operational memory keeps information close to its code and domain, minimizes global rules, assigns each artifact an owner and retirement path, links lifecycle states with stable IDs, retrieves context progressively, and validates deterministic structure automatically.

Document value is not length. It is whether the document changes a decision correctly.

## Move work through lifecycle states

```text
discovered → deferred → contracted → implemented → observed → retired
```

A real but out-of-scope review finding may enter backlog. When approved, it becomes a task contract. After implementation, current behavior enters current-state docs and durable rationale enters a decision record. Once production evidence proves the old path unused, compatibility code and stale documentation are removed.

Each phase has one active canonical record. Promotion is state transition, not copy-and-drift. Stable IDs preserve traceability.

## Route by work shape

| Shape | Carrier |
| --- | --- |
| Safe and verifiable inside the current diff | Fix now |
| Independently describable but out of current scope | Backlog |
| Requires shared scope, acceptance, phases, rollout, or release gates | Requirement or initiative |

Process weight follows uncertainty, coordination, risk, and evidence—not line count.

## Automatic discovery does not grant authority

Agents can systematically scan adjacent concerns, which is valuable and can also create scope creep.

> An agent may discover, classify, gather evidence, and recommend. Scope expansion, product semantics, risk acceptance, and production operations require the corresponding authority.

A review finding receives explicit disposition: invalid, fix now, backlog, or requirement. A real issue should not remain in temporary chat, but preserving it does not commit the current task to solving it.

## Pair policy with mechanism

“Keep documentation current” is policy. Repeatable behavior also needs mechanisms:

- local agent instructions and skills;
- task, backlog, and decision templates;
- CI validation for links, schemas, and indexes;
- path-based retrieval of related backlog items;
- release-tag and requirement-state checks;
- production version, migration, and legacy-traffic reports.

Product judgment and risk acceptance remain human. Formatting, deterministic constraints, and evidence collection should be automated where practical.

## Production reality belongs in the lifecycle

A merge proves the repository changed; it does not prove a safe migration in the real environment. Mixed-version clients, database migrations, offline queues, and compatibility APIs need production evidence.

A compatibility removal gate might require:

```text
For every registered, non-retired client:

version meets the requirement
AND startup succeeded after upgrade
AND required migrations are applied
AND legacy traffic is absent for the observation window
AND the rollback-support window has ended
```

Different mechanisms need different retirement policies. A request adapter may disappear after the fleet gate. Dual read/write waits until old writers vanish and queues drain. A repair migration may remain forever because an old backup can be restored.

Deletion is therefore an evidence-based lifecycle decision, not simple cleanup.

## Relationship to established practices

- Spec-driven development defines expected behavior before implementation.
- Docs-as-code versions and reviews documentation with code.
- ADRs preserve durable technical decisions.
- GitOps uses declarative repositories to drive infrastructure and deployment.
- Issue trackers coordinate scheduling and visibility across teams.

Operational memory connects them across a broader lifecycle:

```text
Discovery → Triage → Contract → Implementation → Verification
→ Release → Production observation → Retirement
```

Its additional focus is cross-task context continuity, temporal semantics, agent authority boundaries, and production-evidence-based retirement.

## Incremental adoption

1. Establish accurate current-state docs for critical domains.
2. Use a short task contract for outcome, scope, and verification.
3. Create fix-now, backlog, and requirement routes.
4. Connect tasks, PRs, decisions, and releases with stable IDs.
5. Automate deterministic structure and link checks.
6. Give temporary compatibility mechanisms an owner and removal gate.
7. Regularly compress stale context and delete mechanisms that meet retirement conditions.

## Conclusion

The principal long-term limitation of AI agents is context continuity, not code generation. A mature AI-native SDLC does not preserve every word. It keeps necessary information under the right semantics, moves it at the right time, and deletes it when it no longer has value.

> An AI-native, repository-native SDLC represents requirements, deferred work, current behavior, historical rationale, operational gates, and retirement rules as versioned artifacts that agents can discover and execute, while consequential product, risk, and production decisions remain under human authority.
