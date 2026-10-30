# Core Principles

**English** | [简体中文](../01-core-principles.md)

These are the rules I use to judge whether a workflow helps. The [individual workflow](02-individual-workflow.md) turns them into actions; they need not become another approval layer.

## Define the outcome

Before implementation, state what should change, what must stay intact, how to verify it, and who decides. A small edit needs a few sentences. Cross-system changes, migrations, and irreversible operations need a fuller contract.

## Verify expected behavior

Tests should check the requirement. AI-written tests can share the implementation's mistaken assumptions; another model or session does not automatically provide independent validation. Check consequential behavior against a contract, real samples, domain judgment, or an independent calculation.

Report verified facts, inferences, and unverified assumptions separately. Supply evidence instead of confidence.

## Continue within granted authority

Retrieval, implementation, and verification can proceed without repeated confirmation of already-authorized steps. New product decisions, cross-system contracts, production actions, and irreversible deletion require the corresponding authority. Repository rules can preauthorize bounded adjacent fixes; discovery itself cannot expand permission.

## Retrieve context as needed

Start with relevant rules, code, and current docs; add issue records and history when needed. Resolve conflicting sources by checking their authority and date. Loading everything adds noise, and newer prose is not necessarily more authoritative.

## Give information a home and an exit

Separate current behavior, future work, and historical rationale. Move or compress information when its state changes instead of maintaining competing copies. Temporary code needs a known dependency and removal condition. Age alone does not establish safe deletion while rollout or accepted-backup repair remains unresolved.

Judge these rules by rework, missed behavior, and context-recovery cost. The [research notes](00-research-foundation.md) explain the limits of measuring code volume or AI adoption alone.
