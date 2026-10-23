# Bubblehouse mobile

Found iOS Git history inside `~/Developer/prairie/Bubblehouse_2022_ios.zip`. Team-owned app; inspect only Andrey’s changes. Android history has no matching Andrey author; no values inferred from it.

## Strong evidence
- **One clear state-update path.** Asset-picker rewrite replaces scattered updates; preserves animations and interaction during animation. Commit explicitly accepts crashes on inconsistent state to expose bugs. M1.
- **Immediate interaction.** Follow/unfollow updates local state before queued server delivery. Later fix corrects the object whose count changes. M2.
- **Bounded complexity.** Voting comments explain replacing a more complex mmap queue with a small in-memory/file-backed buffer. Preserve a wire format that permits a larger queue later. M3.
- **Protect startup.** Delay background service startup; batch telemetry; flush user actions promptly. M3/M4.
- **One owner for session state.** Move remaining auth-token mutations out of APIService into the two relevant thunks. M5.

## Boundaries
- Instant follow is not evidence for optimistic payments or destructive edits.
- The vote queue silently discards data at its size cap. This is an explicit 2020 tradeoff; not a default for user documents or money.
- SwiftUI/Redux-like state and promises already existed in team code. Do not attribute the whole architecture to Andrey.
- `StyleGuide.md` was committed by Andrey but explicitly describes “Filip-style” conventions. Excluded.
- Old OS/network APIs are historical evidence; modern equivalents still need research.

## Questions to carry forward
- Which actions may appear complete before the server confirms?
- Must offline edits survive crashes, logout and account switching?
- When may telemetry be dropped? Must user actions use a separate queue?
- Should invariant failure crash production mobile, or only development?
- Is a single update path enough, or do you want a particular state architecture?

Sources: [M1–M5](23-bubblehouse-evidence.md).
