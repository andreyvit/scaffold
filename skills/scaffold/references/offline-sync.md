# Optional offline editing and sync

Support this architecture when needed; keep ordinary server processing/rendering as the default. [Explicit changes](changes.md) belong from day one for undo/audit, but do not incur full offline complexity before the product needs it.

## Choose conflict semantics
Prefer timestamp-based version selection when discarding competing edits is acceptable. This can suit one person syncing devices; it is generally unsuitable for live collaboration.

Recorded scheme:
- Rows carry `client_update_time` and `server_update_time`.
- Cap incoming client time at `min(now, client_update_time)`.
- Pull rows after the greatest server time seen.
- Select competing versions by greatest client time.
- Use per-field or field-group client times when that is the right conflict boundary.

This is the preferred scheme, not a validated protocol. Before shipping, resolve equal timestamps, cursor/pagination safety, clock skew, deletions and retries. Preserve the intended conflict policy when solving those details.

Where competing edits must be rebased accurately, use revision-gated client rebasing:
- Keep ordered change history within the relevant scope, at least the user's data.
- Pull server changes, rebase pending local changes over them, then push.
- The push names the latest observed revision. Accept only atop the current server revision; incorporate intervening changes first.
- Resolve conflicts on clients. Define semantics carefully, especially indices and sort positions.
- Decompose larger actions into smaller changes only when their semantics remain identical.

Conflict UI is possible, not universally required. Exact transport, persistence, retry and rebase mechanics need implementation and tests; no CRDT library or framework selected.

Source: [C8 and protocol qualifications](../../../research/scaffold/80-offline-sync.md).
