# Offline editing and sync

Confirmed by Andrey, 2026-10-19, direct interview answer. Supported optional architecture; never enabled by default.

## Default
Use ordinary server processing/rendering, especially on web. Keep the change system expandable to offline editing; do not pay its substantial complexity upfront. Use explicit replayable change objects from day one for undo and auditing; [changeset design](81-changesets.md).

## Simple version selection
Prefer when discarding competing edits is acceptable, for the whole app or particular data types. Often sufficient for one person syncing their own devices; generally unsuitable for live collaboration.

- Rows have `client_update_time` and `server_update_time`.
- Server caps incoming client time: `min(now, client_update_time)`.
- Pull rows whose server time is after the maximum server time seen.
- Resolve competing row versions by greatest client time.
- Use per-field or field-group client timestamps when that is the right conflict boundary.

This records the preferred scheme, not a fully validated protocol. Before implementation, specify equal timestamps, pagination/cursor safety, clock skew, deletions and retries. Do not silently replace the user's scheme with an inferred solution.

## Revision-gated changes
Use when accurate rebase semantics are necessary.

- One ordered change history within the relevant scope (at least the user's data), with revision numbers.
- Client pulls server changes, rebases pending local changes over them, then pushes.
- Push names the latest observed revision; server accepts only atop its current revision. Incoming changes must be incorporated first.
- Clients resolve conflicts. Conflict UI is possible; Andrey has not needed to build it in prior implementations.
- Define rebase semantics meticulously, especially indices and sort positions.
- Express larger actions through smaller changes when semantics remain identical. This reduces rebase cases; edge cases can invalidate decomposition.

Similar to operational transformation; prefer describing the mechanism in plain language over a grand name.

## Reasons
Pay complexity only for real requirements. Accept a simpler conflict policy when product semantics allow it. Reuse a small set of changes without erasing meaningful action semantics.

## Preparation decision
B confirmed: explicit replayable change objects from day one. Undo and auditing independently justify them. History persistence, sync and rebasing details remain separate decisions. See [changesets](81-changesets.md).
