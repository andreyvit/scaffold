# Later: iOS/macOS internal design research

Deferred by Andrey, 2026-10-20. Do not conduct this research or request Apple internal-design choices during the current server interview.

## Why
Andrey's historical experience is outdated. Historical preferences inform evaluation; they do not choose today's UI, state, persistence or internal-design mechanisms.

## Research step
1. Gather modern recommendations and their supporting arguments from primary sources and concrete implementations.
2. Group recommendations by approach; make assumptions and disagreements explicit.
3. Compare each approach against confirmed values and representative app requirements, including both iOS and macOS.
4. Present approaches one at a time, with enough context to judge tradeoffs. Then select defaults and exceptions with Andrey.
5. Prototype/measure only where an unresolved question requires evidence.

Cover model/persistence boundaries, native UI/state/observation, concurrency, navigation, services, testing and package/core/platform boundaries as relevant. These are research topics, not predetermined design choices.

Native platform APIs remain confirmed. Layering and packaging preferences remain useful context; UIKit/SwiftUI, Active Record vs pure model and exact module boundaries are not selected.

No timed reminder or background automation requested; this is a later project step. Resume date not set.
