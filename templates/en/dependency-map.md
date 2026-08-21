# Dependency and Slice Map

**English** | [简体中文](../dependency-map.md)

> Purpose: before people or agents work in parallel, write down the slices, the interface contracts, and the blocking relations.
> Decoupling techniques are described in [team collaboration](../../docs/en/03-team-collaboration.md).

## Target

- Outcome / initiative:
- Agreed target completion depth:
- Planned integration point and date:

## Slices

| Slice ID | Result (observable behavior) | Owner | Execution (human / agent) | Target depth | Status |
| --- | --- | --- | --- | --- | --- |
| S1 |  |  |  |  |  |
| S2 |  |  |  |  |  |

## Interface contracts

| Contract | Producer | Consumer | Where defined (file / PR / schema) | Merged | Contract test |
| --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |

Merge the contract before implementing in parallel. Parallel work started without an agreed contract is a primary source of rework.

## Dependencies and blocks

| Blocked item | Blocking item | Type (contract / true sequence / resource / decision) | Blocking point (specific interface or decision) | Decoupling method | Expected clear date | Escalate to |
| --- | --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |  |

Decoupling methods: contract first, mock or fake, expand–migrate–contract, feature flag, reverse slicing, convert to a time-boxed decision.

## Single writer

| Shared source of truth (schema / config / module / document) | Sole writer | How others request changes |
| --- | --- | --- |
|  |  |  |

## Parallel shape

```text
Contract (first)
S1 ──────────►┐
S2 ──────────►┤ integration ─► joint verification ─► release
S3 ──────────►┘
```

## Not parallelizable here

- Undecided semantics or acceptance criteria:
- Decisions required first, with response deadlines:
- High-risk changes competing for the same scarce verification resource:

## Review

- Escalation threshold for blocked items:
- Last review date and conclusion:
