# Collaborative Software Development Lifecycle

**English** | [简体中文](../03-team-collaboration.md)

The individual lifecycle makes one execution trustworthy. The team lifecycle ensures that product, design, engineering, security, operations, and multiple agents work toward the same result without losing intent at functional handoffs.

Software development should not be a relay race in which product writes requirements, developers write code, QA finds defects, and operations releases it. A stable team should own the full value stream from user problem to production learning.

## Lifecycle overview

```text
User and business discovery
  → Shared outcome definition
  → Technical discovery and task contract
  → Slicing, assignment, and dependency decoupling
  → Parallel execution and continuous integration
  → Risk-oriented review
  → Progressive release
  → Production learning
  → Retirement and system improvement
```

Every phase needs a shared artifact, explicit decision rights, and a feedback path. Meetings are not collaboration by themselves; collaboration is different disciplines jointly changing one result.

## 1. User and business discovery

Product, design, engineering, support, and operations build a shared picture of the problem. Engineers should encounter original user evidence and operational data when possible, not only a compressed solution request.

The team answers:

- What is the user trying to accomplish?
- Where does current behavior fail?
- What are the value, urgency, and risk?
- Which result deserves investment?
- What will not be addressed now?

**Shared artifact:** outcome, user evidence, success signals, and non-goals.

## 2. Define the outcome together

The team commits to an outcome and quality standard, not every implementation action predicted in advance. The Scrum Guide's Product Goal, Sprint Goal, and Definition of Done illustrate how shared commitments give artifacts direction and transparency. The concept is useful even without adopting Scrum. [Scrum Guide](https://scrumguides.org/scrum-guide.html)

The outcome owner decides priority and product tradeoffs. The team jointly determines technical and operational feasibility. AI may organize evidence and draft criteria, but it does not decide product value.

## 3. Technical discovery and task contract

Before committing delivery, identify:

- system, data, interface, and team dependencies;
- security, privacy, compliance, and operational risks;
- unknowns that must be tested first;
- rollout, migration, support, and retirement requirements;
- which work agents may perform and where authority stops.

Discovery does not mean completing all design upfront. It means exposing unknowns that could invalidate the commitment. Run time-boxed spikes where necessary and return conclusions to the task contract or decision record.

## 4. Slice, assign, and decouple dependencies

### 4.1 The shape of task duration changed

Once implementation is cheap, a task no longer spends most of its time being written:

```text
Before (illustrative): understand ██  implement ████████  verify ██    wait and coordinate █
Now (illustrative):    understand ██  implement ██        verify █████ wait and coordinate █████
```

The shape is illustrative; each team should measure its own time in state (see work item age in [task management](04-task-management.md)). The consequences are direct:

- Estimation is no longer about “how long to implement” but “how long to reach the target completion depth,” including verification, integration, and release.
- The bottleneck moved from implementation to verification and waiting, so assigning by “who has time to write code now” just pushes queue into the bottleneck.
- One person driving several agents raises personal output, but team lead time may not improve—and can degrade—if verification and dependencies are unchanged.
- Slice by the smallest independently verifiable result, not by how many hours someone has this week.

### 4.2 Assign outcomes and decision rights, not hours

For each slice make four things explicit: who is accountable for the result, who executes (human or agent), who validates independently, and who may change the interface.

- Assign vertical, verifiable slices rather than frontend/backend/testing layers, which recreate handoff queues.
- By default keep implementation and verification of a slice with the same person or pair; split executor and independent validator only for high-risk work.
- Give semantically coupled adjacent slices to one owner; split across people only at a clear boundary, and write the interface contract there.
- The number of tasks a person can run in parallel is set by the review and context-switching cost they can carry, not by how many agents they can launch.
- When someone is blocked, have them remove the block or help older work advance instead of pulling a new task.
- Assign the **target completion depth** at the same time. If two people hold different notions of “done,” the difference becomes an invisible queue.

### 4.3 Four kinds of dependency, four responses

| Dependency | Example | Response |
| --- | --- | --- |
| Contract | Task 1 needs task 2's API, schema, or event format | Define the contract together first (often under an hour), then implement in parallel against it; lock the boundary with contract tests |
| True sequence | Migration must precede reading the new field | Split into expand → migrate → contract, each independently releasable and reversible |
| Resource and environment | One pre-production environment, one test account, one approver | Turn it into an explicit queue or rota instead of invisible waiting; platform it away when possible |
| Knowledge and decision | Waiting on a product, security, or compliance answer | Convert to a time-boxed decision: agreed response window, documented default if it lapses, captured in a decision record |

Always ask first whether the order is **genuinely required** or only **an artifact of not agreeing the contract early**. Most of the time it is the latter.

### 4.4 Turn waiting into parallelism

- **Contract first:** merge the interface definition, schema, types, or event format before both sides implement. The contract is a short task that can unlock days of waiting.
- **Fakes:** the dependent side runs behavior and tests against a mock, stub, or fake; contract tests keep the real implementation honest on swap-in.
- **Expand–migrate–contract:** add the compatible new field or path, migrate with dual write and dual read, then delete the old path. Each step ships on its own.
- **Feature flags and dark launches:** an unfinished downstream does not block upstream merges; every flag carries an owner and a removal gate.
- **Single writer:** each shared source of truth—schema, configuration, shared module, one document—has exactly one writer; others raise change requests, which avoids conflict rework.
- **Reverse slicing:** if task 1 must wait for task 2, carve out the part of task 1 that does not depend on task 2 and shrink the dependency to one explicit interface point.
- Do not answer a dependency with “launch another agent.” Independent work parallelizes; an undecided semantic does not.

### 4.5 Dependencies must be visible

```text
Bad assignment (implicit sequence)
A: task 1  ───── waiting on task 2 ─────►  implement ─► verify
B: task 2  ─► implement ─► verify
    A idles; B's finish time becomes A's start time

Good assignment (contract first + reverse slicing)
A+B: interface contract (one short conversation or a small PR)
A: task 1 (implement and test against a mock) ──►┐
B: task 2 (implement the real end) ─────────────►┤ one integration ─► joint verification
    Waiting collapses into one explicit integration point
```

Team agreements:

- Dependencies live in the work item—who blocks whom, at which interface, and when it is expected to clear—not in chat history.
- Blocks escalate automatically past an agreed age, and the discussion is about the queue and the interface, not about individual effort.
- Blocked waiting counts toward work item age so the cost of waiting is visible on the board.
- Synchronization asks three questions only: which item is blocked today, what is the blocking point, and who can clear it.
- Record slices, contracts, and blocking relations in the [dependency map](../../templates/en/dependency-map.md).

### 4.6 What cannot be parallelized

- Undecided product semantics and acceptance criteria;
- two competing assumptions about the same core logic, which produce mutually exclusive implementations;
- concurrent edits to a single-writer source of truth;
- several high-risk changes competing for the same scarce verification resource—they only pile up in the Verify queue.

## 5. Parallel execution and continuous integration

Each contributor follows the [individual lifecycle](02-individual-workflow.md), but changes return continuously to the shared mainline.

Recommended practices:

- small batches, short-lived branches, and frequent synchronization;
- contract tests at team boundaries;
- automated checks before human review;
- progress represented by working increments, not “percentage complete”;
- one triage path for new findings so they do not disappear into private conversations.

DORA treats small batches, continuous integration, test automation, and loosely coupled teams as important continuous-delivery capabilities. [DORA Core Model](https://dora.dev/research/)

## 6. Review according to risk

Review should not force a human to repeat everything the agent did. Allocate attention by layer:

| Layer | Main concern | Best fit |
| --- | --- | --- |
| Mechanical consistency | Formatting, static policy, duplication, known vulnerability patterns | Automation and AI first pass |
| Behavioral correctness | Acceptance criteria, failure paths, test oracles | Domain-aware engineers |
| System impact | Data, interfaces, performance, operability | Technical or service owner |
| Risk acceptance | Product, security, compliance, irreversible impact | Explicit human authority |

Code review also spreads knowledge and shared ownership, but it is not automatically effective functional testing. Microsoft research emphasizes that review is costly, requires the right skills, and has a social dimension; it should be designed precisely rather than applied as a generic approval ritual. [Microsoft Research: Code Reviews](https://www.microsoft.com/en-us/research/publication/code-reviews-do-not-find-bugs-how-the-current-code-review-best-practice-slows-us-down/)

For high-risk changes, separate executor, independent validator, and release authority. Low-risk work can combine responsibilities.

## 7. Release progressively

The team confirms:

- the shared Definition of Done;
- batch, feature-flag, or canary strategy;
- operational and business success signals;
- stop, rollback, and incident-response conditions;
- on-call, support, and communication responsibilities.

A release should not require ad hoc coordination across many teams. If a team cannot independently test and release most changes within its boundary, organization or architecture is obstructing flow. [DORA: Loosely coupled teams](https://dora.dev/capabilities/loosely-coupled-teams/)

## 8. Learn from production

Product, engineering, and operations compare reality with the original outcome:

- Did users receive the intended value?
- Which assumptions were wrong?
- Did the change create reliability, support, or operational cost?
- Should the team continue, adapt, roll back, or stop?
- Which production knowledge belongs in tests and current documentation?

The team reviews outcomes and value flow—not only the number of tasks completed by each person.

## 9. Retire and improve the system

The team removes temporary feature flags, compatibility paths, stale tasks, and duplicate documentation. Retrospectives should locate systemic constraints:

- Where does work wait?
- Which changes cause the most rework?
- Which knowledge exists in one person only?
- Which agent failure pattern repeats?
- Which platform investment would shorten feedback?
- Which team dependency should become a service, facilitation engagement, or new boundary?

## Responsibilities that must be covered

| Responsibility | Core decision |
| --- | --- |
| Outcome owner | Why now, priority, and what result is valuable |
| Domain or technical owner | System boundaries and long-term technical/data tradeoffs |
| Executor | Implementation, local verification, and evidence organization |
| Independent validator | Whether critical assumptions have independent proof |
| Service owner | Operability, SLOs, incidents, and long-term maintenance |
| Release authority | When to release, stop, roll back, or accept residual risk |

These are responsibilities, not mandatory job titles. Agents can participate in every activity; they cannot be the final accountable owner.

## Measure collaboration health

Consistent with SPACE, combine dimensions:

- **Outcomes and quality:** user goals, reliability, escaped defects, rework;
- **Flow:** lead time, cycle time, work item age, and waiting time;
- **Collaboration:** review burden, cross-team blocking, knowledge concentration;
- **Experience:** feedback loops, cognitive load, flow state, and burnout;
- **Sustainability:** technical debt, retirement of legacy mechanisms, and on-call load.

AI-era teamwork is not about making every contributor generate more. It is about making the team's complete loop—from problem to production learning—shorter, clearer, and more reliable.
