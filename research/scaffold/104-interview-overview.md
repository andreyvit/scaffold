# Interview overview · 2026-10-23

Requested by Andrey to understand progress and remaining scope. Current confirmations reach C82. This is a working map, not a commitment to interview every implementation detail or require every feature in every product. Resume from [STATE](STATE.md).

## Largely settled
- Engineering values and ownership/dependency stance.
- Server/web shape: Go, one process, EDB/Bolt, layering, SSR/Turbo/Stimulus, rich-page exceptions, plain JS and CSS direction.
- Changes/undo/history and offline direction; remaining machinery explicitly left to implementation experience.
- Shared login/company profiles, personal workspaces, permissions/roles, customer-data audit, email codes and passkey enrollment.
- Testing and AI development harness; packaging, deployment, backups/standby and migrations.
- Upload storage/transport, library boundaries and transactional email (Postmark or Mailchimp, via jobs).
- Analytics/business measurement requirements and broad observability requirements. Concrete observability tooling is deferred.

## Remaining cross-cutting defaults worth discussing
1. **Account lifecycle and recovery:** losing email/credentials, membership and ownership transitions, session revocation and support authority. Choose reusable policies; don't force every UI or enterprise feature into every app. Staff/customer identity separation is separately deferred.
2. **Data lifecycle and portability:** export/import, deletion versus retained history, account closure and product shutdown. Preserve already-selected raw analytics and backup retention; ask only for additional defaults where useful.
3. **API and integration conventions:** own-client versus third-party APIs, compatibility/versioning, incoming/outgoing webhooks and external-service boundaries. Basic correctness/idempotency details are engineering work, not preference votes.
4. **Payments, billing and entitlements:** preferred provider/integration patterns and supported reusable foundations where a product needs payment. Actual prices, billing models and exposed features remain product decisions.
5. **Expected background-job failures:** any cross-project policy for retryable failures, uncertain external outcomes and operator intervention. Queue placement, transaction coupling and panic behavior are settled. Do not turn routine retry mechanics into unnecessary interview questions.

These are topic groups, not one question each or an exhaustive backlog. Prefer experience-based defaults; leave context-specific details to concrete projects. Full-text search, localization or other feature recipes can be added when relevant, not as an automatic extension of this interview.

## Separate or deliberately deferred work
- **Observability/anomaly tooling and detailed design:** wait for Andrey's personal experiments (C81); all options saved.
- **Server templating:** owned component-capable language is a separate strategic project (C68).
- **Staff versus customer identities:** wait for reflection; no default selected (C23).
- **Change/operation taxonomy and detailed mechanics:** refine through concrete implementation; don't restart the abstract modeling interview.
- **Native mobile implementation recipes:** native direction and iOS organizational preferences are settled. Modern Apple internals need the separate research step (C41); Android internals have not had a comparable detailed pass.

## Completion work after the useful interview questions
Consolidate the confirmed defaults into coherent whole-app/feature recipes, reconcile stale hypothesis tables against current decisions, and record remaining product-specific choices as prompts at scaffold time. This is synthesis/implementation work, not more questions for Andrey. Do not promise numerical percentage completion from the decision count.
