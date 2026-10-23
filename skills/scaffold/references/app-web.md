# Go server and web app

Use this recipe to assemble a new app or assess an existing one against the scaffold. Read [values](values.md), then the relevant subsystem recipes. Existing project decisions prevail unless the user requests a change.

These are consolidated interview defaults, not a finished starter implementation. Linked recipes hold the detailed rules; implementation guidance below derives from them. Sources and superseded decisions remain in the [decision record](../../../research/scaffold/78-confirmed-decisions.md).

## Starting architecture

| Area | Default | Detail |
|---|---|---|
| Process | One Go process for web, jobs and analytics ingestion; split only for a very strong reason | [Layering](go-layering.md) |
| Primary data | EDB/Bolt; alternatives need a concrete reason | [Changes and history](changes.md) |
| Analytics | In-app, separate database; broad usage measurement, raw events, finite retention | [Analytics and experiments](analytics.md) |
| Web | Server rendering with Turbo/Stimulus; plain JavaScript and minimal bundling; Tailwind starting point | [Rendering](web-rendering.md), [tooling](frontend-tooling.md) |
| Client data APIs | RPC-style JSON for operations; REST may suit CRUD | [APIs](apis.md) |
| Identity | Shared login, company-specific profiles; same workspace model for personal data | [Accounts](accounts.md) |
| Login | Email code where email is available; passkeys from the start; automatically offer enrollment | [Login](login.md) |
| Authorization | Permissions, roles and default roles in code; audit meaningful customer-data access | [Permissions](permissions.md), [access audit](customer-data-access.md) |
| Async work | Queue in main DB, transactionally with originating changes where feasible; execute in-process | [Jobs](jobs.md) |
| Transactional email | Postmark or Mailchimp, sent by a job | [Email](email.md) |
| Uploaded files | S3-compatible authoritative storage, B2 preferred; app upload/URLs by default | [Uploads](uploads.md) |
| Configuration | JSON config, encrypted secrets/keyring, explicit environments | [Config](app-config.md), [environments](app-environments.md) |
| Packaging | Executable embeds templates/assets; config, secrets and data external; no container requirement | [Deployment](go-deployment.md) |

EDB/Bolt reflects an ongoing investment by Andrey and Bubblehouse; it does not select analytics storage or imply that the new change framework is complete. One process keeps embedded storage access and operation simple; separate logical components need not become services.

## Foundations from the start

- Use replayable changes for undo/audit, atomic changesets and recorded simple mutations for recovery. Refine the framework through implementation; see [changes](changes.md).
- Provide required user-data export and deletion. Minimum export is a ZIP of JSON files containing all user data within actual ownership boundaries. Keep ordinary deletions recoverable for 30 days; see [data rights](data-rights.md) and [deleted data](deleted-data.md).
- Instrument metrics, logs and spans alongside product analytics. Concrete observability tooling remains deferred; use the [qualified direction](observability.md).
- Include experiments and feature flags, workspace assignment initially, concurrent A/B preferred and sequential trials supported; see [analytics](analytics.md).
- Build isolated development instances, shared test fixtures, captured email and inspectable data/logs/metrics. Support fixture-user access and real login tests; see [harness](development-harness.md).
- Aim for near-100% test coverage with real scenarios: algorithm unit tests, mostly whole-app integration tests elsewhere; see [testing](testing.md).
- Handle expected errors deliberately. Recover unexpected Go panics at request/job boundaries in production; fail the operation and do not automatically retry a panicked job. Isolated AI development fails fast by default; see [errors](error-handling.md).
- Include scheduled off-server backups and tested restore from day one. Keep production recovery operator-directed; see [backups](backups.md).

## Optional capabilities and product choices

| Capability | When and what changes |
|---|---|
| Offline editing | Enable for a real need; choose acceptable conflict semantics using [offline sync](offline-sync.md). |
| Rich client page | Consider Svelte before React when Stimulus is insufficient; verify actual cost/churn. Full SPA requires explicit user demand or demonstrated limits that reasonable enhancement cannot solve. |
| Role customization UI | Offer it as a feature; build only when authorized. Internal roles/permissions are already required. |
| Extra-login UI | Internal identity supports it; exposure follows the product. |
| Session replay | Separate feature, useful early; choose rollout and require dedicated viewing permission. See [replay](session-replay.md). |
| Paid web product | Use [Stripe](payments.md); pricing, entitlements and checkout are product choices. |
| Frequent large media | Consider direct uploads with completion, reconciliation and vetting; see [uploads](uploads.md). |
| Second server | When requested, use the [standby](standby.md) restore loop; promotion stays manual. |
| Reusable library | Start project-local; each extraction needs explicit authorization. Compatibility depends on consumers and user review. See [boundaries](library-boundaries.md). |

Signup gates, membership lifecycle, UI, third-party APIs and business rules follow actual requirements. Recommend sensible defaults where context permits; ask only about a real unresolved tradeoff. A foundation does not authorize every possible user interface.

## Recovery and data windows

These windows have different purposes. Do not use one as another's retention or durability guarantee.

| Concern | Initial rule | Limit |
|---|---|---|
| Backup schedule | Hourly full snapshots for small early databases | Data since the last successful snapshot may be lost; WAL awaits EDB support. |
| Backup retention | All hourly backups for a week, then daily backups for 60 days | Adjust for product needs/storage cost; retain required keys. |
| Recent replay | Strive for roughly a week | Compatibility target, not permanent history replay or selected history retention. |
| Ordinary deleted data | Recoverable for 30 days | Separate from permanent erasure and backup expiry. |
| Raw analytics | 24 months, including archives | Finite explicit overrides allowed; aggregate retention is separate. |
| Buffered analytics writes | 60 seconds if buffering/throttling is used | Small gaps acceptable only for analytics. |
| Startup migration | 5 seconds per migration, tested on representative data | Let an overrun finish safely and log it. Large rewrites use explicit maintenance. |
| Standby polling | About 10 minutes, if enabled | Backup frequency determines freshness; polling does not improve it. |

Drain work, stop, then start the new executable; proxy buffering should hide the brief restart. Verify that behavior with the chosen proxy. Failed deployment recovery is manual by default. Keep best-effort previous-executable compatibility initially and reevaluate after MVP; see [migrations](migrations.md).

## Implementation and release guidance

Implement a representative real flow through the layers, then broaden coverage. Exercise login/profile selection, an authorized business change, its effects/job, rendered output, audit and analytics in an isolated instance. Verify denied access as well as success; exercise real email/passkey behavior separately from fixture shortcuts.

Before relying on deployment, demonstrate backup/restore into an isolated instance, migration behavior and the restart procedure. Inspect failures through the same tools used in development. Prove export coverage and deletion behavior against actual data ownership. This is derived verification guidance, not an additional product feature list.

Do not promise zero data loss from hourly snapshots or exactly-once external effects from atomic job scheduling. Set concrete recovery objectives and expected-failure handling for the product.

## Deliberately unresolved

- Component-capable server templating is separate strategic work; no interim engine selected.
- Observability/anomaly tools and detailed design await Andrey's experiments. Candidates remain saved, including Jaeger.
- Staff/customer identity separation awaits reflection; no default selected.
- Detailed changes/operations machinery needs implementation experience.
- Native mobile uses native APIs. [iOS layering](ios-layering.md) is settled; modern Apple internals and Android implementation recipes need separate work.

These are limits of the scaffold, not a new interview queue. See the [review overview](../../../research/scaffold/104-interview-overview.md) for current scope.
