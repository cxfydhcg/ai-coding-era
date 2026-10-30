# Practice: Give Repository Records Entry and Exit Conditions

**English** | [简体中文](../08-record-lifecycle.md)

In `smrtlite-android` and `bp_employee_app`, I separate four record types and use scripts to retrieve and maintain them. This helps the next session recover context and identifies records that can leave. [Repository memory](06-repository-as-operational-memory.md) defines the categories; this article covers operation and pitfalls.

## Follow one change

Consider a request failure incorrectly displayed as an empty list. Paths and versions here are illustrative.

1. **Discover:** today's task only changes sorting, so record the error-display issue in backlog with a source anchor, deferral reason, fix, and verification.
2. **Implement:** change loading behavior; verify successful empty responses, timeout, and malformed data separately. Rewrite current docs, preserve useful rationale, and tick the verified item.
3. **Coordinate:** if another system's interface must change, establish a requirement contract and remove the duplicate backlog description.
4. **Release:** a qualifying production tag containing the closing commit allows proposed backlog pruning. Move completed requirement specs to `done/` to retain acceptance and rollout evidence.
5. **Observe:** keep device verification explicitly open until performed. A tag does not close it. Retire the spec only after gates, retention, and references are resolved.

```markdown
| Phase | First production release | Status |
| --- | --- | --- |
| [Phase 1](done/phase-1-errors.md) | v1.4.0 | Implemented; device verification pending |
```

## Daily actions

| Moment | Action |
| --- | --- |
| Start | Read relevant lifecycle findings and retrieve open issues by source path. |
| Change behavior | Update current docs, preserve consequential rationale, and mark temporary code. |
| Before committing | Review the diff, verify behavior, check references and indexes, and name adjacent work picked up. |
| Maintenance | Review proposals, apply on a maintenance branch, run checks, and submit a PR. |

The application repositories provide these commands; this blog repository does not install them:

```sh
node scripts/doc-lifecycle.mjs          # report only
./backlog.sh src/orders                 # use the actual source path
./backlog.sh --changed
node --test scripts/doc-lifecycle.test.mjs
node scripts/check-docs.mjs
```

For assistants without Claude Code hooks, put fallback steps in `AGENTS.md`. A context reminder, an executing Git hook, and an enforced CI check provide different guarantees.

## What may leave automatically

| Record | Example policy | Retain when |
| --- | --- | --- |
| Checked backlog | Prune after a production tag contains the closing commit. | Unverified or unreleased. |
| Completed requirement | Hold 60 days from the first production release after entering `done/`. | Gates, missing index data, unclear status, or references remain. |
| Short-lived change log | Review 60 days after landing. | Fallout, unsupported references, or still-needed rationale remains. |
| Current docs and durable decisions | Maintain according to valid behavior and decisions. | No blanket age-based deletion. |
| Temporary code and migrations | Report candidates only. | Removal requires a verified code change. |

Sixty days is a local choice. Scripts recognize prescribed sections and tables, not arbitrary meaning. Put rationale that must survive into a protected record or an explicit retention marker. Omit empty fallout sections: a simple parser may treat “Fallout: none” as an open item.

## Adapt the configuration

| Difference | POS repository | Staff repository |
| --- | --- | --- |
| Source coverage | `mobile/src/` | `src/` and native plugins |
| Production tags | `vX.Y.Z.W` | `vX.Y.Z` |
| Critical contracts | Schema, migrations, cloud registration | POS interfaces and independent release versions |
| Manual evidence | Active devices, migration success, backup recovery | Staff rollout and POS fleet |

Without tags, define equivalent immutable deployment evidence; merging to main is insufficient. Check the clock too: the example scripts use the tagged commit's date. If deployment is materially later, use a trustworthy release timestamp.

Temporary branches can use `COMPAT`, `HOTFIX`, `WORKAROUND`, or `DEPRECATED`, paired with a backlog item naming the file and concrete removal work:

```ts
// COMPAT(gate >= 1.4.0): reads the old shape until active clients upgrade.
// WORKAROUND(when upstream fixes reconnect): temporarily reopens the connection.
```

Scripts can report date and version conditions. Fleet, independent dependencies, and external events need human evidence. Migration retirement also requires successful application, fresh-install correctness, and repair of every backup shape still accepted. Fleet upgrades do not prevent old backups returning; retain necessary repairs and seeds.

## A failure worth carrying into your tests

In temporary test repositories, the older staff sweep accepted a prerelease as shipping evidence and deleted a completed spec without an index row. Those defects were fixed with regression coverage. The lesson: bring the deletion tests when adapting a script.

At minimum, verify:

- Prereleases and wrong version formats cannot trigger cleanup; shipping evidence contains the target commit.
- The clock follows the move into `done/`; release backfill leaves status untouched.
- Missing rows, empty status, open gates, and outside references retain specs.
- Backlog cleanup preserves open items, prose, and navigation; change-log cleanup retains fallout and repairs supported links.
- Tomorrow is not due today; version thresholds ignore unrelated branches.
- Reporting is read-only, repeated application makes no additional changes, and application code is never deleted by the sweep.
- Actual source roots, plugins, tables, and link forms are covered.

Start with reports, then review application results on a clean maintenance branch, then schedule it. Use full history and tags, tests before application, document checks afterward, and verified PR-creation permissions. A green no-change run does not prove a PR can be opened. If permission is unavailable, retain reporting and let a maintainer submit the reviewed changes.

Fill in the [record policy template](../../templates/en/record-lifecycle-policy.md). First establish that a newcomer can find current behavior, open work, and a gate owner; add automation where it helps.
