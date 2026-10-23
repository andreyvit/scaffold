# Session replay

Separate feature covering capture, storage and playback. Especially valuable early, when learning how people use the product. Choose its rollout per product; broad usage analytics does not automatically enable replay.

- **Capture:** record UI state and interactions; mask/exclude selected content before upload. Define supported surfaces and sampling.
- **Storage:** accept ordered batches with safe retries; associate sessions with workspace/user/experiment context. Set retention and deletion rules.
- **Playback:** provide session lookup and a player. Require a dedicated permission to watch replays; enforce it on recording-data access as well as the UI, within the viewer's authorized scope.
- **Metrics:** capture/upload failures, stored bytes, retention cleanup failures and playback failures.
- **Logs:** ingestion/playback errors and replay access metadata; avoid duplicating recorded content into logs.

For web, evaluate rrweb's recorder/player with owned storage. Candidate, not a mandated dependency. Native capture needs separate evaluation.

Before release, verify representative navigation/playback, masking, retry ordering, retention/deletion and denied access without the dedicated permission.
