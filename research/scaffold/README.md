# Scaffold research

Initial source research and expanded LifeBase/hiring pass complete, with [coverage gaps](03-coverage.md). Architecture interview ongoing; [confirmed decisions](78-confirmed-decisions.md) currently reach C87. **Resume from the exact unanswered question in [STATE.md](STATE.md#resume-here).**

[Where the interview stands and what remains](104-interview-overview.md)

## Start here
1. [Confirmed values](70-values.md)
2. [Requirements to support](71-requirements.md)
3. [Architecture decisions](72-architecture-decisions.md)
4. [Historical scope outline](79-next-scope.md) · [Interview outline](01-questions.md)

[Latest decisions](78-confirmed-decisions.md) · [Craftsmanship and UX evidence](64-craft-and-ux.md)

[Offline/sync decision](80-offline-sync.md) · [Changesets](81-changesets.md) · [Identity and profiles](82-identity-and-profiles.md) · [Business and onboarding](83-business-and-onboarding.md) · [Session replay research](84-session-replay-options.md) · [Analytics journals](85-analytics-journals.md)

## Later research
[Modern iOS/macOS internal design](88-apple-design-research-plan.md): recommendations and arguments grouped by approach, then interview.

## Recipe design
- [Accounts](73-accounts-decisions.md) · [Operation](74-operations.md)
- [Error handling](89-error-handling.md)
- [Backups](90-backups.md)
- [Migrations](91-migrations.md)
- [Customer data access](92-customer-data-access.md)
- [Rich web pages](93-rich-web-pages.md)
- [Frontend tooling](94-frontend-tooling.md)
- [Server templating — strategic work](95-server-templating.md)
- [Library boundaries](96-library-boundaries.md)
- [Email-code and passkey login](97-login-methods.md)
- [Uploaded-file storage](98-upload-storage.md)
- [Observability](99-observability.md) · [Lightweight candidates](100-lightweight-inspectability.md) · [Anomaly detection](101-lightweight-anomaly-detection.md)
- [Files and indexes for observability](102-file-based-observability.md)
- [Transactional email](103-transactional-email.md)
- [One-off support repairs](105-one-off-support-repairs.md)
- [Payments](106-payments.md)
- [API style](107-api-style.md)
- [Deleted-data recovery](108-deleted-data-recovery.md)
- [Required data export and deletion](109-data-export-and-deletion.md)
- Observability details deferred pending Andrey’s own experiments (C81); all options above retained.
- [Compact recipe shape](75-recipe-shape.md) · [Modern options](76-modern-options.md)
- [Research → interview → recipes](77-research-method.md)

## Best source finds
- [Happy Grid: original instructions](10-happy-grid.md) · [authored Go layout](86-go-package-layout.md)
- [Bubblehouse: authored decisions](21-bubblehouse.md) · [mobile](22-bubblehouse-mobile.md)
- [Heynote: five code values](41-heynote.md)
- [Zoo: what the role models mean](43-zoo.md)
- [Ulysses: values](51-ulysses.md) · [original iOS layout](52-mobile-layout.md) · [confirmed iOS layering](87-ios-layering.md)
- [2024 SSR/Turbo/Stimulus draft](62-more-writing.md)
- [Principal-engineer hiring](65-hiring.md)
- [LifeBase: product, business and original dictations](66-lifebase-expanded.md)

Numbered source files retain the questions, evidence and limits of each pass. TSV files hold exact revisions, authorship checks and source paths. Recipes live separately in `skills/scaffold`.
