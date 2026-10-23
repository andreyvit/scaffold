---
name: sync
description: Commit all scaffold changes, rebase onto the upstream branch, and push. Use when asked to sync this scaffold repository.
---

# Sync scaffold

scaffold uses Git for syncing. Treat commits lightly: small edits and mixed updates can share a simple sync commit. Run when the user asks to sync this repository; that request authorizes commit and push. Merely copying or editing this skill does not invoke it.

1. Inspect status, branch, upstream, and any unfinished Git operation. Include all current scaffold changes, including untracked files; honor ignore rules.
2. Resolve existing conflicts before committing. Preserve both sides' new information; compare each side with the base to avoid restoring obsolete text. Preserve existing stashes. Ask only if competing edits require a user decision.
3. Stage all changes with `git add -A`. Check the staged diff for conflict markers and accidental changes. Commit if needed with a short message such as `Sync scaffold`.
4. Fetch the configured upstream remote and rebase onto the upstream branch. Resolve clear conflicts and continue; do not discard changes or skip commits to get past a conflict.
5. Push to the upstream branch without force. If rejected because the remote advanced, fetch, rebase, and retry once. If still blocked, report the cause and preserve local work.
6. Verify the working tree is clean and local HEAD matches the remote branch. Report completion or the exact remaining blocker.

Use the existing branch and upstream. If either is missing or ambiguous, ask rather than inventing a destination. Never reset away work or force-push for routine sync.
