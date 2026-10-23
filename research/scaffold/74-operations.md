# Operation belongs in every recipe

Proposed compact contract. Shared recipes define mechanics; each feature supplies its own facts.

| Concern | Each feature must say | Whole-app recipe supplies |
|---|---|---|
| Security | Actor; resource/tenant; allowed actions; abuse limits; sensitive data | Common enforcement, credential/session handling, secrets, safe defaults |
| Metrics | Success/failure/latency/backlog worth measuring; useful alert | Naming, bounded labels, collection, dashboard and alert routing |
| Logs | Useful events, correlation, safe detail, retention | Structured context, redaction, access, transport and search |
| Audit | Which durable who/what/when records matter | Integrity, access, retention; distinct from debug logs |
| Failure | Retryable vs terminal; partial success; idempotency; reconciliation | Durable jobs, deadlines, retry policy, operator tools |
| Data | Durability, migrations, deletion/export, restore expectations | Backup, restore drill, version compatibility, shutdown/export plan |
| Release | Compatibility window, flag/rollout needs, rollback limits | Build identity, deploy check, client/server skew, rollback procedure |
| Support | How to diagnose and safely repair one user’s problem | Scoped access, actor attribution, replay/simulation, support tools |
| Product | Outcome measured, decision it informs, privacy/cost | Broad usage coverage, cohorts, ownership, retention and experiment policy |

## Confirmed starting defaults
Business measurement goals → required analytics capabilities → most private implementation meeting them. Broad usage analytics is normally required; privacy above metrics needs an explicit product decision. No data loss; seconds of downtime hidden where possible. Product phase and requirements determine exact budgets and exceptions. Verify the proposed proxy/restart behavior; it does not itself establish recovery or durability.

## Per-project questions
1. Minimum launch bar vs requirements earned by risk?
2. Default data-loss and downtime budgets for each product profile?
3. What customer data may support staff and telemetry services see?
4. Which failures deserve an alert, a daily queue or no human attention?
5. Who owns the product measures, and when should a feature be removed?

## Proof, not installation
A backup restores. A rollout runs the intended version. An alert reaches an owner. A failed job can be diagnosed and retried safely. A support action respects scope. A metric answers a decision.

Evidence: [Bubblehouse](21-bubblehouse.md), [Happy Grid](10-happy-grid.md), [Ulysses release notes](51-ulysses.md), [watchdog](60-other-code.md). The starting defaults are confirmed in this chat; detailed mechanics above remain proposals.

## Business outcomes — confirmed
Instrument the monetization/conversion funnel, monitor performance and test alternatives. This is ongoing product operation, not just an upfront architecture decision. Experiments and feature flags belong from day one; concurrent A/B testing is preferred, with sequential trials also supported. Specific events, cadence, assignment and evaluation mechanics remain to be chosen. [Context](83-business-and-onboarding.md).

## Background jobs — confirmed C61
Queue in the main database by default; persist scheduled jobs with the originating business change in the same transaction where feasible. This follows from the architecture, not a separate preference tradeoff. Execution stays in-process (C35); no automatic retry after unexpected panic (C42). [Recipe](../../skills/scaffold/references/jobs.md).

## Customer-data access audit — confirmed C62
Superstaff may access client data. Audit meaningful access by any user: customer details views count; names in lists do not. Record bulk operations such as exports once, without enumerating each customer touched by default. [Details](92-customer-data-access.md) · [Recipe](../../skills/scaffold/references/customer-data-access.md).

## Uploaded files — confirmed C73
Object storage is authoritative; prefer B2's S3-compatible interface. App-controlled URLs preserve the storage boundary; separate serving domains depend on content. Presigned redirects are allowed. Local disk is only a cache when the app serves bytes. [Details](98-upload-storage.md) · [Recipe](../../skills/scaffold/references/uploads.md).

C74: uploads pass through the server by default for vetting before durable storage. Direct uploads for frequent large media use explicit completion plus a reconciliation job for files present despite missed completion calls, then content vetting. This exception does not change C49's production-recovery policy.

## Observability — confirmed C75
Metrics, analytics, spans and good logging belong from project start, with broad metrics coverage. Anomaly monitoring on selected metrics is planned. BH's current setup is rudimentary, not a selected operational reference. Tooling and mechanics remain open; [solution space and assistant proposals](99-observability.md) · [Recipe](../../skills/scaffold/references/observability.md).

C76: BH uses Grafana Cloud, but reported cost/slowness discourage everyday investigation. Seek a lightweight alternative; no replacement selected. Self-hosting Grafana is not assumed to solve this experience. [Context](99-observability.md).

C77: no Protobuf or OTLP. Seek an integrated lightweight Go solution on one server. Earlier OTLP proposals are superseded; [candidate search](100-lightweight-inspectability.md) found partial fits, no verified complete match. No replacement selected.

C78 clarifies C77: a small handwritten OTLP encoder without a Protobuf dependency is acceptable in principle. Wire format alone no longer excludes a tool; plain-Go simplicity and integrated capability still require evaluation. No full SDK, collector or backend selected.

C79: alternatives recorded for later trials, including Jaeger; backend selection deferred. [Brief candidate list](100-lightweight-inspectability.md).

C80: prefer direct telemetry files with rotation and indexes; Prometheus/PromQL are soft exceptions rather than the default. [Design and critique](102-file-based-observability.md). No exact store/rotation/index mechanism chosen.

C81: observability/anomaly details tabled pending Andrey's own experiments. All candidates and file/index alternatives retained; no further recommendations selected.

C82: transactional email uses Postmark or Mailchimp; sending is a job under the existing database/process defaults. [Details](103-transactional-email.md) · [Recipe](../../skills/scaffold/references/email.md).
