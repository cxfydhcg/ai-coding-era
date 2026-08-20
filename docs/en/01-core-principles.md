# Core Principles

**English** | [简体中文](../01-core-principles.md)

## 1. Optimize for trustworthy outcomes, not code production

Code is never the final result. The result may be fewer payment failures, faster user completion, prevention of data loss, or an auditable business process.

AI can produce a convincing implementation quickly, which magnifies an old mistake: treating the appearance of code as evidence that the problem is solved. AI-era engineering needs an evidence chain—requirements, tests, review, release, and production evidence.

## 2. Intent precedes generation

Before asking an agent to change a system, define at least:

- the observable outcome;
- what is in scope and explicitly out of scope;
- compatibility, security, business, and operational constraints;
- how completion will be proven;
- who owns consequential tradeoffs and release decisions.

Without these, an agent is most likely to create a coherent implementation of an incorrect assumption set.

## 3. Verification capacity must keep pace with generation capacity

If implementation throughput increases tenfold while review, testing, and production feedback remain fixed, the organization only creates unverified change faster.

Verification should be layered:

```text
Static constraints → unit behavior → integration boundaries → end-to-end flow → production observation
```

Risk determines depth, but every task declares a minimum verification standard before implementation. Tests written by the same agent are useful evidence; they are not automatically independent evidence.

## 4. Bounded agency

Agents should proactively retrieve context, analyze, propose, run safe checks, and identify adjacent problems. They need explicit authority before they:

- expand task scope;
- change product behavior or public contracts;
- accept security, privacy, financial, or operational risk;
- modify production state;
- delete potentially active compatibility or data paths;
- communicate externally on behalf of a person or organization.

> Discovery is not decision authority. Execution is not release authority.

## 5. Progressive context, not context dumping

Agents need enough context. Loading every organizational document at once adds noise, stale information, and semantic conflicts.

A more reliable sequence is:

1. Read the task contract and local rules.
2. Locate relevant code and current-state documentation.
3. Retrieve related backlog items, decisions, and recent history.
4. Expand to adjacent domains only when a boundary question appears.
5. Report conflicting sources and dates instead of guessing which is authoritative.

## 6. One active source of truth per lifecycle state

One concern may move through backlog, requirements, implementation, current documentation, and history. It should not have several independent “current” versions.

```text
Discovered → Deferred → Contracted → Implemented → Observed → Retired
```

Information moves, compresses, or is superseded as state changes. Stable IDs preserve traceability; the active canonical record remains unique.

## 7. Evidence over confidence

“Looks good,” “should work,” and a confident agent are not delivery evidence. A good conclusion distinguishes:

- directly verified facts;
- inferences from available information;
- unverified assumptions;
- decisions that require a human owner.

This directs reviewer attention to uncertainty instead of forcing a complete re-investigation.

## 8. Deletion is first-class engineering work

Generating new code is easy; safely deleting old code is harder. Every temporary compatibility layer, migration branch, and feature flag should record:

- why it exists;
- who or what still depends on it;
- what evidence permits removal;
- who owns the retirement decision;
- how removal will be verified and rolled back.

A temporary mechanism without a retirement process is usually unnamed permanent complexity.
