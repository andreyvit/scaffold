# Interview overview · 2026-10-23

Requested by Andrey to understand progress and remaining scope. Current confirmations reach C87. This is a working map, not a commitment to interview every implementation detail or require every feature in every product. Resume from [STATE](STATE.md).

## Largely settled
- Engineering values and ownership/dependency stance.
- Server/web shape: Go, one process, EDB/Bolt, layering, SSR/Turbo/Stimulus, rich-page exceptions, plain JS and CSS direction.
- Own-client APIs: RPC-style JSON for operation-oriented APIs; REST may fit CRUD.
- Changes/undo/history and offline direction; 30-day recovery for ordinary deleted data. Required data deletion/export; minimum export is a ZIP of JSON files containing all user data. Remaining machinery left to implementation experience.
- Shared login/company profiles, personal workspaces, permissions/roles, customer-data audit, email codes and passkey enrollment.
- Testing and AI development harness; packaging, deployment, backups/standby and migrations.
- Upload storage/transport, library boundaries, transactional email (Postmark or Mailchimp, via jobs), and payment provider (Stripe for paid web products).
- Analytics/business measurement requirements and broad observability requirements. Concrete observability tooling is deferred.

## Remaining work after the general-default interview
The current server/web pass has enough direction to consolidate. This is the assistant's scope assessment, not a new user choice. Avoid extending the interview with obvious engineering or hypothetical product decisions.

- **Account lifecycle:** membership, ownership transfer and session behavior follow concrete product/security requirements. Total lockout is a one-off with selected staff repair capability (C83).
- **Data lifecycle:** deletion/export required, ZIP of JSON minimum (C87); ordinary recovery 30 days (C86). Ownership boundaries, erasure/retention mechanics, UI, imports and shutdown plans follow actual requirements.
- **APIs/integrations:** RPC-style JSON for operations, REST may fit CRUD (C85). Third-party contracts, versioning and webhooks depend on actual consumers; routine correctness is engineering work.
- **Payments:** Stripe for paid web products (C84); pricing, billing models and features are product decisions.
- **Background jobs:** main-DB queue, transaction coupling, in-process execution and no auto-retry after panic are settled. Expected-failure retries and ambiguous external outcomes depend on the operation; ask only if a real unresolved tradeoff appears.

Full-text search, localization or other feature recipes can be added when relevant; they do not automatically extend the interview.

## Separate or deliberately deferred work
- **Observability/anomaly tooling and detailed design:** wait for Andrey's personal experiments (C81); all options saved.
- **Server templating:** owned component-capable language is a separate strategic project (C68).
- **Staff versus customer identities:** wait for reflection; no default selected (C23).
- **Change/operation taxonomy and detailed mechanics:** refine through concrete implementation; don't restart the abstract modeling interview.
- **Native mobile implementation recipes:** native direction and iOS organizational preferences are settled. Modern Apple internals need the separate research step (C41); Android internals have not had a comparable detailed pass.

## Completion work after the useful interview questions
Consolidate the confirmed defaults into coherent whole-app/feature recipes, reconcile stale hypothesis tables against current decisions, and record remaining product-specific choices as prompts at scaffold time. This is synthesis/implementation work, not more questions for Andrey. Do not promise numerical percentage completion from the decision count.
