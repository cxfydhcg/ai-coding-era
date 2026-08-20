# Individual Software Development Lifecycle

**English** | [简体中文](../02-individual-workflow.md)

Here, “software development” means the complete process by which one developer takes responsibility for a change—from understanding the problem to observing the production result. AI can participate in every phase, but the individual's job is not merely to send prompts. It is to maintain intent, a system model, evidence, and risk boundaries throughout the work.

## Lifecycle overview

```text
Select the problem
  → Recover context
  → Define the task contract
  → Design and analyze risk
  → Implement in small batches
  → Verify in layers
  → Self-review
  → Integrate and release
  → Observe production
  → Learn and retire
```

This is not a one-way waterfall. Verification may invalidate an assumption and send the work back to context, contract, or design. Each loop should add evidence rather than trigger another blind generation attempt.

## 0. Choose the human–AI collaboration mode

Do not assume every task should be delegated completely.

| Mode | Suitable context | Human involvement |
| --- | --- | --- |
| Human-led | Implicit semantics, high repository familiarity, very short implementation | Human implements; AI retrieves or checks |
| Pairing | Design requires continuous judgment and interdependent steps | Human and agent exchange assumptions and evidence frequently |
| Delegated | Clear contract, stable boundaries, strong automated verification | Agent executes continuously; human reviews key gates |
| Parallel research | Independent options, evidence searches, or checks | Multiple paths investigate; human synthesizes |

The best mode depends on the cost of verifying generated output—not only the cost of generating it. Different results from large field experiments and the METR maintainer study reinforce the need to evaluate AI by task context. See the [research foundation](00-research-foundation.md).

## 1. Select the problem: confirm that it is worth solving

Start with evidence: user feedback, business signals, reproduction steps, operational logs, or a changed constraint—not only “build this feature.”

Ask:

- Who is experiencing what problem?
- What happens if nothing changes?
- Is success a user outcome, system behavior, or reduced maintenance cost?
- Is this problem worth addressing now?

AI makes low-value features cheaper to build, not more valuable. [DORA's user-centric focus](https://dora.dev/capabilities/user-centric-focus/) matters because speed without a user outcome accelerates the wrong direction.

**Output:** one outcome statement and the evidence supporting it.

## 2. Recover context: build a model of the current system

The developer and agent retrieve:

- current implementation, tests, schemas, and interfaces;
- local engineering rules and current-state documentation;
- related tasks, backlog items, decisions, and recent changes;
- production constraints, version distribution, monitoring, and known incidents.

Require the agent to separate observed facts, inferred behavior, unverified assumptions, and conflicting sources. Verify every inference that can change the solution.

**Exit condition:** you can explain current behavior, the likely change points, major dependencies, and known unknowns.

## 3. Define the task contract

Use the [task contract](../../templates/en/task-contract.md) to specify:

- Outcome;
- scope and non-goals;
- product, compatibility, data, security, performance, and operational constraints;
- acceptance criteria;
- the verification plan;
- the agent's authority and stop conditions.

Turn acceptance criteria into examples, test oracles, or observable signals before implementation when possible. The [TiCoder study](https://www.microsoft.com/en-us/research/publication/llm-based-test-driven-interactive-code-generation-user-study-and-empirical-evaluation/) supports test-driven intent clarification as a way to improve evaluation of AI-generated code.

**Exit condition:** another developer or agent can determine what “done” means without the original conversation.

## 4. Design and analyze risk

Do the minimum design necessary to answer:

- Which boundary should own the behavior?
- How will data, state, and errors flow?
- Can existing abstractions carry the change without adding accidental complexity?
- What can fail, and is failure reversible?
- Does the task affect authorization, privacy, money, migration, or a public contract?
- What rollout, compatibility, and rollback support is required?

Low-risk tasks may need a few lines. Cross-system or irreversible changes need a decision record, migration plan, and independent review. Design depth follows risk and uncertainty, not line count.

## 5. Implement in small, verifiable batches

```text
Choose one behavioral slice
  → Implement with a human or agent
  → Run the nearest, fastest validation
  → Inspect the diff against scope
  → Preserve evidence or revise the assumption
  → Continue to the next slice
```

Small batches reduce blast radius, review cost, and the cost of agent drift. DORA connects [working in small batches](https://dora.dev/capabilities/working-in-small-batches/) to delivery performance and fast feedback.

Do not expand the task indefinitely as adjacent problems appear. Route each finding to fix now, backlog, requirement, or not-a-problem.

## 6. Verify in layers

```text
Formatting and static policy
→ unit behavior
→ component and integration boundaries
→ end-to-end user flows
→ security, performance, and compatibility
→ target environment and production observation
```

An agent can generate and run tests, but its tests may repeat the same mistaken assumption. High-risk criteria need an independent oracle: an established contract, real samples, another implementation, domain judgment, or production signals.

NIST's [SSDF](https://csrc.nist.gov/pubs/sp/800/218/final) supports integrating security requirements, protection, verification, and vulnerability response into the SDLC instead of saving security for the end.

## 7. Self-review: reduce the next person's comprehension cost

Before requesting team review, inspect:

- whether the diff delivers the outcome rather than merely satisfying the prompt;
- unrelated changes, duplicate abstractions, or hidden compatibility paths;
- error, boundary, concurrency, and recovery behavior;
- whether tests would detect the intended regression;
- synchronized documentation, configuration, monitoring, and rollback;
- verified conclusions versus residual inferences.

AI is well suited to a first pass over mechanical and consistency issues. Humans retain product semantics, architectural cost, and risk acceptance.

**Output:** a small, explainable change set, verification summary, residual risks, and review focus.

## 8. Integrate and release

Connect the individual task to the team system: respond to review, satisfy the shared Definition of Done, resolve integration concerns, select a rollout strategy, and identify release authority.

Release should be small, observable, stoppable, and reversible where possible. Database migrations, mixed-version clients, and irreversible operations need predeclared release gates.

## 9. Observe production

Observe three classes of signals:

- **Product:** user task success, adoption, satisfaction, or target business indicators;
- **System:** errors, latency, resources, data consistency, and security signals;
- **Change quality:** rollback, hotfixes, support requests, unexpected compatibility traffic, and manual intervention.

If direct production observation is impossible, define a proxy signal, observation window, and owner. Otherwise “observe after release” becomes an unowned intention.

## 10. Learn and retire

- Update current-state documentation with observed behavior.
- Preserve only the rationale that still affects future decisions.
- Route real out-of-scope findings to backlog.
- Remove one-off scaffolding and low-value generated text.
- Give feature flags, compatibility paths, and legacy data flows an owner and removal gate.
- Convert incidents and deviations into better tests, guardrails, or task-system rules.

The goal is not to accumulate artifacts. Information should move into the correct lifecycle state and leave when it expires.

## Individual completion standard

Before calling a change trustworthy, answer:

1. Which observable problem did we solve?
2. Which facts and critical assumptions support the implementation?
3. What evidence proves the acceptance criteria?
4. Who accepted the residual risk?
5. How will production prove the outcome, and how will failure stop or roll back?
6. How will future maintainers understand current behavior, and when will temporary mechanisms be removed?

AI can absorb more execution. Professional responsibility remains the ability to select the right problem, create the right constraints, reject weak evidence, and own the result.
