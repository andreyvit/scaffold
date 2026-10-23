# LiveReload and older writing

Questions entering: native fidelity vs shared code? Inspectability vs framework magic? Product survival vs openness?

## Direct statements
- NodeApp: native views, shared model/controllers. Drop into native code whenever easier. Cross-platform did not mean uniform UI.
- Keep the backend runnable from a terminal with readable JSON input/output. Inspectability matters even when embedded execution might be possible.
- UI tree updates chosen over many RPC calls for readable code and easier testing.
- 2011 launch story: fast feedback while editing was the product’s origin. Track people actually trying builds, not only attention.
- 2012 openness essay: share as much as sustainable; earn enough to keep building; permit continuation after abandonment. Historical licensing views, not legal advice or a current licence choice.

## Code inference
- Named reactive computations + invocation traces make automatic behavior inspectable.
- Real project fixtures exercise processing and file changes (`ProjectTestCase.swift`, 76/76 lines Andrey).
- Maccel: stable input-source IDs replace ordering assumptions; action execution consolidated. Small corroboration of explicit state and shared mechanics, not a complete architecture.

## Limits
- NodeApp’s own README labels parts experimental. A described architecture is not proof it shipped successfully.
- Large shared runtime is a counterexample to “always native-only” or “never frameworks.” Do we still endorse this tradeoff?
- Current `content/principles.md` first appears in September 2025. Strong lead; exact human authorship unresolved. Do not promote its wording to confirmed values yet.

## Sources
- `~/Developer/livereload/3`, `af9b5ce8d5cf1f7065b8e70e4ddff8bce6963633`: `nodeapp/README.md:3–41,183–283`; all 587 lines attributed to Andrey. `LRProjectKit/Tests/ProjectTestCase.swift:16–74`.
- `~/Developer/pub/tarantsov`: original posts `599cb12` (2011 anniversary), `77f69a7` (2012 openness); modern ports read alongside original history. Personal anecdotes omitted from research.
- Principles candidate: `bdd8213e74e8dd05243e57638967158bc3c51716:content/principles.md`.
- `~/Developer/andreyvit/Maccel`: `b99545b2ad779f67736a678f4a72a7b59427cff0`, `09e99c46aa7f84370295876dfe71a1a9f985ffd3`.

## Ask later
1. What product quality must survive cross-platform code sharing?
2. Which old framework investments paid off, and which would you now avoid?
3. Is source access / data export / abandonment protection a product default?
4. How should recipes balance an excellent small product against a broader, slower launch?
