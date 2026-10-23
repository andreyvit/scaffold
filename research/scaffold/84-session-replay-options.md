# Self-hosted session replay

Research checked 2026-10-20. Assistant assessment, not a selected recipe/default. No prototype or performance measurement yet.

## Web candidate: rrweb
MIT-licensed recorder and player; no hosted service required. Records initial DOM/state, then timed mutations and interactions; replay reconstructs the page without running original application JavaScript. [Project](https://github.com/rrweb-io/rrweb).

Captures additions/removals, attributes/text, mouse movement/clicks, focus, touch, scrolling, window size and input changes. This can include application content, not just event names. [Recorded events](https://rrweb.com/docs/observer).

Mask inputs/text or block regions in the browser. Current guide defaults mask passwords but not all inputs. Canvas and cross-origin iframe recording are opt-in; iframe capture needs instrumentation in child frames. Logs/network recording use extensions. [Options](https://rrweb.com/docs/guide), [network](https://rrweb.com/docs/recipes/network), [iframes](https://rrweb.com/docs/recipes/cross-origin-iframes).

## Owned implementation — proposal
Recorder → compressed, ordered batches → own ingestion/storage → session index → embedded player in staff UI.

Library supplies browser recording/reconstruction. Application owns upload retries/order/deduplication, limits, session linking, access, retention/deletion and useful lookup. Preserve starting snapshots for replayable segments. [Storage contract](https://rrweb.com/docs/library/storage).

Assessment: a basic demo is straightforward; production is a moderate subsystem. Highest uncertainty is browser/layout fidelity, assets surviving deployments, capture overhead and masking representative screens. SSR/Turbo flows need actual navigation tests. No asserted delivery time, byte rate or tested compatibility.

Alternative: a fuller self-hosted OpenReplay deployment, trading custom tooling for operating its stack. Its source deployment guide lists minimum 2 vCPU / 8 GB RAM / 50 GB storage, x86. Not a full license or architecture evaluation. [Deployment](https://docs.openreplay.com/en/deployment/deploy-source/).

## Boundary
rrweb is a web solution. Native iOS/Android recording needs separate evaluation; no equivalent maturity or effort inferred.

## Confirmed feature scope — 2026-10-20
Session replay can be very valuable, especially early. Keep it a separate feature/file covering capture, storage and playback. Watching replays requires a dedicated security permission. [Recipe](../../skills/scaffold/references/session-replay.md).

No universal capture rollout, library selection or approval to collect real sessions inferred. Recipe operational checks apply the existing security/metrics/logging requirements; implementation remains future work.
