# Architecture decisions

Current map through C87. Use the [whole-app recipe](../../skills/scaffold/references/app-web.md) to apply these defaults; the [decision record](78-confirmed-decisions.md) preserves reasons and supersessions. Earlier option scans are evidence and proposals, not additional selected architecture.

## Confirmed defaults

| Area | Current choice | Scope / change condition |
|---|---|---|
| Server | One Go process for web, jobs and analytics ingestion (C35) | Split only for a very strong reason. |
| Primary storage | EDB/Bolt (C36) | Alternatives need a concrete reason; analytics storage is separate and its engine unselected. |
| Code layout | Responsibility layers, feature packages within them where useful (C38–39) | Shared packages may hold mutually referring types; preserve dependency direction. [Guide](../../skills/scaffold/references/go-layering.md). |
| Changes | Replayable changes from day one; atomic changesets, common effects, semantic undo (C9–18) | C11/C14 refine earlier wording. [Current rules](../../skills/scaffold/references/changes.md). |
| Offline | Opt-in: timestamp selection where competing edits may be lost, revision-gated rebasing otherwise (C8) | Enable only for an actual need; protocol details still need validation. [Recipe](../../skills/scaffold/references/offline-sync.md). |
| Web | SSR + Turbo/Stimulus (C37) | Full SPA only by explicit demand or demonstrated limits that reasonable progressive enhancement cannot solve. |
| Rich pages | Consider Svelte before React (C64–65) | Evaluation order, not a dependency mandate; verify payload, simplicity and churn expectations. |
| Frontend tools | Plain JS, simplest bundling, Tailwind starting point (C66–67) | TS requires compelling benefits; genuinely JS-heavy growth may justify it. [Recipes](../../skills/scaffold/references/frontend-tooling.md). |
| APIs | RPC-style JSON for operations; REST may fit CRUD (C85) | Own-client preference; public API conventions depend on consumers. |
| Accounts | Shared login, per-company profiles, personal workspaces in the same ownership model (C19–21) | Internal multi-login support; UI/lifecycle follow the product. [Accounts](73-accounts-decisions.md). |
| Analytics | Broad usage measurement and experiments in-app; separate analytics DB (C24–34) | Raw events initially; finite 24-month default retention. [Recipe](../../skills/scaffold/references/analytics.md). |
| Jobs/email | Main-DB queue, atomic scheduling where feasible, execution in-process; Postmark or Mailchimp email via jobs (C61/C82) | External-effect delivery and expected-failure handling need operation-specific design. |
| Uploads | S3-compatible authoritative storage, B2 preferred; upload through app (C73–74) | Frequent large media can justify direct uploads with completion/reconciliation/vetting. [Recipe](../../skills/scaffold/references/uploads.md). |
| Data rights | Required deletion/export, ZIP of JSON minimum; ordinary deleted data recoverable for 30 days (C86–87) | Ownership, UI and erasure mechanics remain product-specific. |
| Operation | Self-contained binary; drain/stop/start; manual production recovery; snapshots and tested restore (C47–60) | Recovery objectives and costs can change the starting budgets. [Operations map](74-operations.md). |
| Dependencies/libraries | Build/own by default; project-local units; explicit extraction approval (C2/C69–70) | Dependencies need a concrete benefit; compatibility depends on consumers and user review. |
| Mobile | Native APIs/UI per platform (C7); iOS layering then feature/screen (C40) | Accept duplicated implementation. Usually folders in one module; package boundaries earn their cost. |

## Deferred or not selected
- **Server templates:** component support required; owned language planned separately (C68). No interim engine selected; minicomponents is not the default.
- **Observability/anomaly details:** metrics, logs, spans and analytics required; direct files/indexes preferred, Prometheus/PromQL a soft exception, no Protobuf dependency. Handwritten OTLP output is acceptable in principle. Tools/design await experiments (C75–81).
- **Staff/customer identity separation:** C23 withdraws C22's proposed default; await reflection.
- **Changes/operations mechanics:** vocabulary, effect convergence, bulk progress and related API details need concrete implementation experience.
- **Modern mobile internals:** Apple research deferred (C41); Android internals have not had a comparable pass. Presentation-state ownership and model/persistence mechanics remain unselected.
- **SPA stack and contracts:** a justified SPA does not select a frontend framework/server split. DTOs, client generation and third-party compatibility follow actual consumers.

These are not instructions to restart the interview. [Review scope](104-interview-overview.md).

## Keep separate
- Database choice, logical components and process boundaries.
- Native code sharing and shared UI.
- Cached reads and offline mutation/conflict resolution.
- Audit, undo, replay and off-server recovery guarantees.
- Identity, profile, membership, data ownership and billing.
- Business records, analytics and operational telemetry; each has its own durability and retention.
