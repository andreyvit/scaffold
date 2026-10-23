# Go layering: HappiGrid baseline

2026-10-20: Andrey confirmed layering as primary organization, with feature subgrouping within layers, and confirmed he wrote HappiGrid's package-layout docs. Use them as primary source; this does not authenticate every later edit or unrelated README section.

Sources: [current README layering](/Users/andreyvit/Developer/andreyvit/happigrid/README.md:239), plus `5fb41bbf:README.md` in that repository (Architecture / Types of code / High-level objects / Layering).

## Confirmed refinement
Call this **layering**, not a balance between feature-first and responsibility-first layouts. Layers reflect responsibilities and dependency direction. Experience repeatedly favors keeping similar code together. Subdivide within a layer to prevent huge packages and tangled dependencies; prefer feature packages where practical.

Allow inter-feature types/code in one package where circular references are useful, especially in-memory representations. Persistent models and model utilities can often be separate. This is not a blanket ban on mutually referring types or permission for cyclic Go package imports.

[Scaffold guide](../../skills/scaffold/references/go-layering.md) reproduces the layering rules with this clarification.

## Responsibilities
| Package family | Role |
|---|---|
| `utils/` | Generic algorithms/helpers; no domain concepts |
| `model/m*/` | Domain/synthetic types and simple algorithms; no persistence/context services; shared primitives in `mcom` |
| `apps/` | App/Ctx interfaces, configuration and shared contracts |
| `db/`, `db/db*/`, `db/txns/` | Persistence mechanics and generic changes, not business decisions |
| `shared/sh*/` | Cross-cutting mechanics such as logging/metrics |
| `core/core*/` | Domain business logic and domain-specific changes; shared handler logic |
| `handlers/h*/` | HTTP integration and limited handler-specific business logic |
| Long-running activity packages | Controllers and other activities |
| `appimpl/` | App/Ctx implementations and application wiring |
| `apptesting/*testing/` | Whole-app integration-test infrastructure |

Feature spans packages: `maccounts`, `coreaccounts`, `haccounts`, `accountstesting`. Prefixes identify responsibility and avoid collisions between layers.

## Boundaries and reasons
- Separate algorithmic, business, integration and wiring code. Small mixing is acceptable; extract as complexity accumulates.
- Pure model code depends on utilities, not runtime services. Current README permits persistence struct tags but not persistence mechanics.
- Handlers do not call peer handlers; move shared logic/constants into core.
- App is shared wiring; Ctx is request/goroutine-local and not safe for concurrent sharing.
- Current documented rules: dependencies go down layers; restrict peer dependencies except core, with designated shared packages elsewhere.
- Current Ctx implements context.Context and edb.Txish. Current shared-service implementation peers live under appimpl to limit rebuilding.

## Version limits
Initial README uses `services/s*` for long-running work; current uses `activities/c*`. Initial utility prefix was `u*`; current utilities are unprefixed. These naming changes are observed, not independently proven manual edits.

Current interview decisions override older change/operation semantics. Do not impose permanent event replay, multi-transaction changesets or generic rollback from older material. Exact new framework package placement will follow concrete implementation experience.

## Research correction
The initial pass found this source but left file authorship uncertain and did not extract its layout into a dedicated output. Authorship is now confirmed for the package-layout docs. Use this baseline instead of asking generic layout questions already answered here.
