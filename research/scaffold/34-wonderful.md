# Wonderful Todo App

Question entering: what does local-first productivity require beyond a simple saved state?

Source: `~/Developer/wonderfulapp/thewonderfulapp-ios` at `903157a7532098b1b9d7e2cfef2fb7342f6fc11b` (2018-10-30). 63 eligible non-merge commits, all Andrey. README and sampled change/sync/tests lines all attributed to him.

## Evidence
- Changes contain enough prior data to undo without knowing the old state. `README.md:41–100`.
- Explicit change/apply/rebase contracts. `Inbox/Model/Changes/Change.swift`.
- Local changes are recorded and applied; incoming changes rewind and rebase outgoing changes. `Inbox/ChangeHistory.swift`.
- Sync has explicit download/upload states, bounded retries and a persisted result log. `Inbox/SyncManager.swift`.
- Tests exercise edit/undo/rebase scenarios and export JSON cases for other platforms. `README.md:5–8`; `InboxTests/InboxTests.swift`.
- Vendored SQLite.swift is documented as copied third-party code; do not attribute its internals to Andrey.

## Interpretation
More machinery was accepted for offline edits, undo and cross-platform agreement. This is useful precedent for requirements-driven complexity, not a reason to add a sync engine to every app.

## Questions after
- When do edits need undo, sync, audit or replay? Which combinations matter?
- Should platforms share code or just semantics and test vectors?
- How should a user resolve conflicting edits?
- Must conflict handling preserve every rejected edit for recovery?

Limit: old rebase code can turn incompatible edits into no-ops and reports their count. That historical behavior needs review before reuse; no conflict policy is approved.
