# Architecture decisions

Options to explore after [scope](71-requirements.md). Web direction and native mobile are confirmed. Other defaults below are hypotheses applying the [confirmed values](70-values.md).

| Decision | Options | Working preference / reason | Question that changes it |
|---|---|---|---|
| Web rendering | **SSR + Turbo/Stimulus, progressively enhanced**; rich-page tools as needed; SPA exception | **Confirmed:** full SPA only on explicit user demand or demonstrated SSR limitations enhancement cannot reasonably solve. | What actual limitation remains after reasonable progressive enhancement? |
| Rich page tooling | Small owned controller/renderer; React; another component library | Compare with the same demanding screen. V4, V7, V12. | Which composition problem does Stimulus fail to solve? |
| SPA stack | Client router + API; integrated frontend framework | Candidate: keep the established server; add only needed frontend services. | Need frontend SSR, public SEO routes, offline shell or another frontend team? |
| Server shape | **One process**, including web, jobs and analytics ingestion | **Confirmed:** split only for a very strong reason. Simplicity, efficiency and local embedded databases that often require one process. | What concrete need is strong enough to justify the operational and data-access cost of splitting? |
| Primary storage for Go servers | **EDB/Bolt by default**; alternatives need a concrete reason | **Confirmed:** Andrey and Bubblehouse will keep investing heavily in EDB. | What concrete requirement justifies departing from this investment? |
| iOS organization | **Layers → feature/screen**, usually folders in one module | **Confirmed:** historical convenience; avoid excessive Swift packages. [Details](87-ios-layering.md). | Does a core/platform split earn its packaging cost? |
| Mobile UI | Native APIs per platform; select native frameworks and state ownership | **Confirmed:** native, accepting duplicated implementation. AI changes the cost tradeoff. | Which native interactions, OS versions and release constraints must work? |
| Presentation state | Local view state; screen state holder; shared app store | Candidate: smallest owner matching state lifetime. V3, V5. | Who else reads/writes it, and must it survive navigation/process death? |
| Go package layout | **Layering first; feature packages within layers where practical** | **Confirmed:** reproduce HappiGrid layering; allow shared packages for useful inter-feature references. [Details](86-go-package-layout.md). | Which new framework responsibilities require a concrete adjustment? |
| Business logic | Domain types/services; use-case layer; workflow engine | Keep it separate from UI; add machinery for actual complexity. V3–5. | Which rules must work from multiple entry points? |
| Offline | Online only; timestamp-based version selection; revision-gated client rebasing | **Confirmed:** opt-in; use simplest acceptable conflict semantics. [Details](80-offline-sync.md). | Which competing edits may be discarded? What preparation belongs in online-only apps? |
| Contracts | Shared internal types; explicit API DTOs; generated clients | Stable external contracts, cheap internal change. V2, V4. | Independent deployments, third-party callers or durable formats? |
| Async work | Inline; durable app jobs; external queue | Candidate: persisted jobs when work must survive a crash. V5, V10. | Retry safety, latency, ordering and loss limits? |
| Dependencies | Use; copy narrow part; implement; drop capability | **Confirmed:** build/own by default; dependency requires a concrete reason. V7. | Which expertise and ongoing updates are we buying? |
| Deployment | One host; managed platform; redundant regional/multi-region setup | Decide from recovery needs and operating budget. | How long can the service be down, and who restores it? |

## Keep separate
- Database choice from single-process architecture.
- Code sharing from shared UI.
- Cached reads from offline mutation and conflict resolution.
- Audit trail from event sourcing; undo from replay; metrics from analytics.
- User identity from tenancy, membership, credentials and billing ownership.

Each approved choice needs a reason, exception and reversal trigger. A fashionable architecture name is not a reason.
