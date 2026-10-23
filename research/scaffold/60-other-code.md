# Remaining code: useful checks

Questions entering: do older implementations contradict the emerging defaults? Where does operations change the design?

## Findings
- `router` explicitly aims to make omitted auth/CORS/cache middleware impossible, with deliberate overrides. This predates the same Happy Grid request. **Intent only:** middleware builder methods are empty in this old snapshot.
- `httpserver` binds to localhost by default and distinguishes initiating shutdown from waiting for it. Safety and lifecycle are part of the small API.
- `httpform` uses reflection. The later rejection of reflection for domain mutation is not a universal ban; ask which failure modes are acceptable.
- `minicomponents` adds component syntax by rewriting templates; source-positioned errors. Supports the desire for better SSR composition without moving the whole UI to a client framework.
- `mvp` is a substantial owned framework. `buddyd` uses its hooks, actor/session model and declared changes. Current Happy Grid favors separated pieces. Keep this evolution visible.
- `journal` explains one-second timestamps through the actual query need and compact encoding. Its recovery policy truncates corrupted tail data; that policy needs an explicit loss boundary, not blind reuse.
- `watchdog` monitors freshness of backup/script check-ins. A live server does not imply maintenance work is succeeding.
- Bubblehouse web: an authored change disables paid image optimization to contain cost. Another bypasses failing lint/type build gates during an ESLint failure while adding a separate type-check command. **Incident choice, not an approved release policy.**

## Counterexamples worth asking about
- 2018 `blocks`: assemble apps from standard blocks “like houses,” not cathedrals. December 2025 architecture draft calls an app a one-off cathedral. Likely standard parts vs contextual whole; confirm.
- Older `buddyd` SSO test file is empty. Test-file presence is not test coverage.
- Tiny tools use libraries readily (e.g. URL extraction/scraping in `ReferenceURLsFormatter`). Dependency policy varies with stakes and scope.

## Sources
Pinned revisions and line authors: `61-code-sources.tsv`.
- `router:README.md,doc.go,builder.go:30–35`.
- `httpserver:httpserver.go:49–98`; `httpform:httpform.go:60–89`.
- `minicomponents:components.go:69–108`; `journal:journal.go:1–58`.
- `mvp:context.go,auth.go`; `buddyd:auth.go,changes/change.go,sso_test.go`.
- `prairie/watchdog`, `92c1c74761ab0fd64fe432dea365b99c2b99ddb0:README.md`.
- `prairie/web`: `2bfd48465d19b930ef49064dcf8e709b2f716c41`, `91c94d73cbc4e983ddac0988f65d1c813e9d12fa`.
- `blocks`, `8a8b72e7702e22dfa507d62118c2675e14683ff8:README.md` (all lines Andrey).

## Limits
Selected mechanisms and explicit rationale, not correctness audits. No tests, servers or deployments run. No old code is approved for reuse merely because Andrey wrote it.
