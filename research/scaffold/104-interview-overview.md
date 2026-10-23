# Consolidation review · 2026-10-23

The general server/web interview through C87 is consolidated for review. No interview question is pending. This is a documentation synthesis, not a claim that every mechanism is settled or implemented. [STATE](STATE.md#resume-here) remains the work cursor.

## Review in this order
1. [Go/server/web whole-app recipe](../../skills/scaffold/references/app-web.md): architecture, day-one foundations, optional features, recovery/data windows and implementation guidance.
2. Newly extracted recipes: [values](../../skills/scaffold/references/values.md), [changes/undo/history](../../skills/scaffold/references/changes.md), [identity/workspaces](../../skills/scaffold/references/accounts.md), [analytics/experiments](../../skills/scaffold/references/analytics.md), [optional offline sync](../../skills/scaffold/references/offline-sync.md).
3. [Skill and recipe index](../../skills/scaffold/SKILL.md): targeted reading instead of recursively loading research.
4. [Decision map](78-confirmed-decisions.md#current-recipe-map): all C1–C87 mapped to their current homes, with supersessions called out.

## What changed
The whole-app guide now assembles the existing small recipes. Confirmed foundations previously buried in research have reusable recipe files. Architecture, accounts and operations summaries reflect the final interview state. Historical scope menus and stale next-question pointers are labelled; original evidence and the chronological decision record remain available.

No new user decisions were added. Implementation/verification guidance is labelled separately. Existing JSON configuration and environment rules remain part of the recipe; config wording and a broken sentence were cleaned up without changing the scheme.

## Qualifications worth checking
- Changesets stay atomic; bulk work spans them. Recovery applies recorded simple changes without regenerating effects. Detailed framework mechanics still need experience.
- Required foundations do not authorize all optional UI: role customization, extra-login surfaces, offline editing and replay rollout remain separate choices.
- The no-data-loss objective is stronger than current hourly snapshot recovery. Replay compatibility, backup retention, deleted-data recovery and analytics retention are separate windows.
- Metrics/logging/spans/analytics are required now, while concrete observability tooling is deferred. Existing analytics storage/retention decisions still apply.
- Email codes remain available after automatically offered passkey enrollment, subject to company requirements. Total lockout is a one-off repair case.
- Export/deletion are required capabilities; ZIP of JSON is the export minimum. Shared-data boundaries and permanent erasure are product-specific, distinct from ordinary 30-day deletion recovery.

## Decisions for an actual product
Do not turn these into a mandatory generic interview. Recommend defaults from context and ask only when a concrete tradeoff remains.

| Area | What still needs context |
|---|---|
| Accounts | Membership/invitations, ownership transfer, sessions and stronger authentication policies |
| Data lifecycle | Shared/company ownership boundaries, actual export/erasure behavior, retention interactions and UI |
| APIs/integrations | Actual consumers, public compatibility, webhooks and operation-specific external-effect handling |
| Payments | Pricing, billing model, entitlements and checkout; Stripe is the paid-web default |
| Reliability | Failure scenarios, acceptable loss/downtime, resource costs and tested operating procedures |
| Business learning | Funnel, events, experiments, evaluation and ongoing ownership |

Full-text search, localization and other feature recipes can be added when relevant. Imports and shutdown plans were not selected as universal day-one features.

## Deliberately deferred or separate
- **Observability/anomaly tools and detailed design:** await Andrey's experiments (C81). [Backend options, including Jaeger](100-lightweight-inspectability.md), [anomaly options](101-lightweight-anomaly-detection.md) and [file/index discussion](102-file-based-observability.md) remain saved.
- **Server templating:** owned component-capable language is separate strategic work (C68); no interim engine selected.
- **Staff/customer identities:** await reflection; C23 withdrew C22's default.
- **Change/operation taxonomy and mechanics:** refine through concrete implementation; no further abstract interview now.
- **Native mobile internals:** native direction and iOS organization settled. Modern Apple internals need the separate research step (C41); Android has not had a comparable detailed pass.

The next step is Andrey's review. There is no automatic new research phase, tool trial or application implementation in this consolidation task.
