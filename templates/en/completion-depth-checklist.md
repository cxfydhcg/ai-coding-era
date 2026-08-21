# Completion Depth Checklist

**English** | [简体中文](../completion-depth-checklist.md)

> Purpose: before marking a task Done, ask “what is still missing?” consistently instead of confirming only that the happy path runs.
> Depth levels are defined in [task management](../../docs/en/04-task-management.md).

## 0. Declaration

- Task ID:
- Target depth (D1 / D2 / D3 / D4):
- Depth explicitly excluded, and why:
- Backlog items and owners for the excluded parts:

## D1 Happy path correct

- [ ] Every acceptance criterion has automated or recorded verification
- [ ] Verification checks the required behavior, not a restatement of the implementation
- [ ] Typical-input results were confirmed independently, not only reported by the agent

## D2 Boundaries and failure paths

- [ ] Empty values, missing fields, oversized input, invalid formats
- [ ] Boundary numbers: zero, negatives, maximums, precision and rounding
- [ ] Duplicate submission, concurrent requests, race conditions, idempotency
- [ ] Dependency failure: timeout, network error, partial success, retry and backoff
- [ ] Insufficient permission, unauthenticated access, privilege escalation, tenant isolation
- [ ] UI states closed out: loading, empty, error, retry, disabled, partial failure
- [ ] Failures are visible rather than silently swallowed
- [ ] The test oracle was not derived by the same session that wrote the implementation

## D3 Runs in the real system

- [ ] Performance at real data volume, including N+1 and slow queries
- [ ] Compatibility with legacy and dirty data
- [ ] Migration, dual write and dual read, backfill, and rollback path
- [ ] Observability: logs, metrics, alerts, traces, or audit trail
- [ ] A diagnostic entry point exists when something breaks
- [ ] Time zones, units, currency, localization, accessibility
- [ ] Verified from other perspectives: non-admin, other tenants, other devices or locales
- [ ] Runtime configuration, permissions, and alert thresholds updated
- [ ] Current-state documentation and runbooks match the new behavior
- [ ] Integration with other slices has a named owner and was verified

## D4 Outcome validated

- [ ] Target signals or user evidence show the expected change
- [ ] The production observation window is complete and anomalies are handled
- [ ] Old paths, dual writes, compatibility layers, feature flags, migration scripts, and dead code are removed, or have an owner and a removal gate
- [ ] Conclusions are written back into tests, documentation, or a decision record

## Conclusion

- Depth actually reached:
- Gap against the target depth and its disposition:
- Completion evidence links (implementation, verification, production observation):
- Confirmed by, and date:
