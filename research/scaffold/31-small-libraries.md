# Small libraries

Pre-June-2025 README history; authorship checked. [Pinned revisions](32-library-sources.tsv).

## Findings
- **Extend familiar tools.** `jsonfix` preprocesses input and keeps `encoding/json`; preserves diagnostics and future compatibility.
- **Remove mundane work, keep control.** `sqlexpr` uses plain structs/slices, normal branches/loops, raw SQL escape hatch. `sqlstruct` handles scanning/building without owning the app.
- **Buy only useful generality.** SQL dialect is global because multiple dialects in one app are rare. `multierr` hides its type and only wraps multiple errors.
- **Small APIs can finish.** `signedstrings` is feature-complete; `jsondiff` deliberately drops patch application and options to focus on readable differences.
- **Own the abstraction, reuse primitives.** `plainsecrets` and `sealer` use established crypto libraries. Their value is packaging, configuration and rotation—not inventing cryptography.
- **Performance buys simpler application code.** EDB’s stated payoff: direct loops and serialized writes; fewer services and less team overhead. Availability and security boundaries are explicit exceptions.
- **Measure on relevant machines.** Hash benchmarks preserve multiple CPUs and account for laptop throttling.

## Useful corrections
- “Never generate code” is wrong: `sqlstruct` generates repetitive SQL/scanning code. Bubblehouse avoids generation when the benefit is too small.
- “Always use stdlib JSON” is wrong: `tinyjson` accepts narrower input guarantees to reduce TinyGo/WASM size. That is a constrained use case.
- “Always require 100% coverage” is wrong: `jsonfix` and `tinyjson` explicitly say it is often the wrong choice, but right for those libraries.
- “Always build a custom framework” is wrong: MVP exists, yet Happy Grid explicitly chooses its component libraries without its framework.
- “Zero dependencies at any cost” is wrong: crypto/compression libraries are accepted. The relevant cost appears to be owning and understanding the result.
- Old `envloader` is not today’s config recipe: current scaffold explicitly chooses JSON over env vars.

## Questions after these sources
- What makes code generation worth another build step?
- Which compatibility surface stays stable: APIs, files, config, operator habits?
- When do availability or security needs override single-server simplicity?
- What is the smallest useful abstraction, and when should we stop adding features?
- Does dependency size matter mainly for auditability, build cost, portability or control?
- How should test depth scale with risk, algorithm complexity and change frequency?

## Excluded
`aidev/README.md` explicitly says it and some code were AI-written. Excluded despite being before June 2025. The cutoff is a useful default, not proof against contrary evidence.
