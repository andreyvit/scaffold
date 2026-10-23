# Small tools: final checks

These add context, not whole-app defaults.

- **Christmas Lights:** iOS simulator calls the hardware effect API from a native view. A concrete shared-logic/native-UI precedent, not a modern cross-platform recommendation. The snapshot also has mismatched reset signatures; no claim it currently builds.
- **Protoappserver:** inspectable temporary Bolt store and backup path; patch model is unfinished. Do not mistake the prototype for a validated sync architecture.
- **YNAB expense form:** direct cache, amount type and rendered-page test. Small tools tolerate a simpler structure; no broad policy follows from this sample.
- **Schedule creator:** explicit time/range types and progress reporting; no new architecture judgment inferred.
- **Linear summary bot:** stated goals include avoiding overcommitment and balancing client/internal/strategic work. Fixed, planned and flexible work are distinguished.
- **Virtual Demir:** file-based processing stages are inspectable; paid transcription requires explicit flags. Temporary browser automation is intended to disappear when a suitable API exists.

## Sources
Pinned library revisions: [32-library-sources.tsv](32-library-sources.tsv).
- `christmaslights`: `Christmas Lights/ChristmasLightsView.m`, `ChristmasLightsController/effects.h`; all 188/36 blamed lines Andrey.
- `protoappserver`: `model/model.go`, `store/store.go`; all 36/147 lines Andrey.
- `ynabexpenseform`: `cache.go`, `web_test.go`; all 61/51 lines Andrey.
- `schedule-creator`: `time.go`, `progress.go`; all 108/60 lines Andrey.
- `~/Developer/prairie/linearsummarybot`, `7bc7fe:README.md`.
- `~/Developer/lifehack/virtual-demir`, `329aa:README.md`.

Historical README-only stubs: contextual, tarantsov-chat, audiencebot, smsactions, ticketing. No missing implementation to derive values from at the selected revisions.
