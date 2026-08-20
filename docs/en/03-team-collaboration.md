# Collaborative Software Development Lifecycle

**English** | [简体中文](../03-team-collaboration.md)

The individual lifecycle makes one execution trustworthy. The team lifecycle ensures that product, design, engineering, security, operations, and multiple agents work toward the same result without losing intent at functional handoffs.

Software development should not be a relay race in which product writes requirements, developers write code, QA finds defects, and operations releases it. A stable team should own the full value stream from user problem to production learning.

## Lifecycle overview

```text
User and business discovery
  → Shared outcome definition
  → Technical discovery and task contract
  → Slicing, interfaces, and ownership
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

## 4. Slice work, define interfaces, assign ownership

Break the outcome into independently integrable vertical slices. Avoid recreating handoff queues with separate “frontend,” “backend,” and “testing” tasks that cannot deliver value alone.

Before parallel work, define:

- one accountable owner for each slice;
- inputs, outputs, and acceptance criteria;
- API, schema, event, or UI contracts;
- single-writer ownership for shared facts and files;
- who verifies the integrated result;
- how conflicts and scope expansion escalate.

Agents can parallelize independent research, testing, migration analysis, and bounded module work. Unresolved product semantics cannot be parallelized by adding more agents.

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
