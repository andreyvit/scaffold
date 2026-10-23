# Operation in the scaffold

Current defaults through C87. The [whole-app recipe](../../skills/scaffold/references/app-web.md) assembles these rules. Detailed recipes are the implementation entry points; the [decision record](78-confirmed-decisions.md) retains the interview history.

## Confirmed starting defaults

| Concern | Current rule | Recipe |
|---|---|---|
| Failures | Expected errors handled deliberately; unexpected Go panic recovered at request/job boundary in production; no automatic retry after panic | [Errors](../../skills/scaffold/references/error-handling.md) |
| Deployment | Embedded templates/assets in executable; drain/stop/start behind buffering proxy; no container required | [Deployment](../../skills/scaffold/references/go-deployment.md) |
| Recovery | Operator-directed production recovery/rollback until serious SRE scenario testing earns automation | [Deployment](../../skills/scaffold/references/go-deployment.md) |
| Backups | Scheduled off-server snapshots and tested restore from day one; hourly full backups initially; hourly week then daily 60 days | [Backups](../../skills/scaffold/references/backups.md) |
| Backup protection | Prefer encryption; separate recovery key copy in 1Password; monthly rotation where appropriate, at least annually initially; retain old keys as needed | [Backups](../../skills/scaffold/references/backups.md) |
| WAL | Wait for EDB support; no interim off-server change-history replication | [Backups](../../skills/scaffold/references/backups.md) |
| Standby | Optional second server polls about every 10 minutes, restores and verifies launchability; normally keep app stopped; manual promotion | [Standby](../../skills/scaffold/references/standby.md) |
| Migrations | Small startup migrations, 5-second budget each tested before release; overruns finish safely and log; large rewrites use explicit maintenance | [Migrations](../../skills/scaffold/references/migrations.md) |
| Rollback compatibility | Strong initial best effort; reevaluate after MVP as a business decision | [Migrations](../../skills/scaffold/references/migrations.md) |
| Jobs/email | Main-DB queue, atomic scheduling where feasible, in-process execution; Postmark or Mailchimp mail via jobs | [Jobs](../../skills/scaffold/references/jobs.md), [email](../../skills/scaffold/references/email.md) |
| Support access | Superstaff may access client data; meaningful access audited for any user, bulk once; selected staff raw-data repairs for one-offs | [Access](../../skills/scaffold/references/customer-data-access.md), [permissions](../../skills/scaffold/references/permissions.md) |
| Uploads | B2-preferred S3-compatible authoritative store; app URLs and server upload by default; local disk only a cache | [Uploads](../../skills/scaffold/references/uploads.md) |
| Business learning | Broad analytics, funnel monitoring/testing, experiments and flags from day one; privacy within measurement needs | [Analytics](../../skills/scaffold/references/analytics.md) |
| Visibility | Metrics, analytics, spans and logging from day one; direct files/indexes preferred; detailed tooling deferred | [Observability](../../skills/scaffold/references/observability.md) |
| Data lifecycle | Required export/deletion; ZIP of JSON minimum; ordinary deletion recoverable for 30 days | [Data rights](../../skills/scaffold/references/data-rights.md) |

No data loss and seconds of hidden downtime are objectives, not guarantees of the initial implementation. Hourly snapshots leave a loss window. Verify proxy behavior and set failure scenarios/budgets for the product.

## Guidance for each implemented feature
This is a derived review aid, not a separate set of user-approved features or universal mechanisms. Apply what is relevant; link shared rules rather than copying them.

| Concern | State and verify |
|---|---|
| Security | Actor, resource/workspace, allowed actions, sensitive data and abuse limits |
| Visibility | Useful success/failure/latency/backlog measures, correlated diagnostic detail, and who investigates |
| Audit | Meaningful who/what/when records, access and retention distinct from debug logs |
| Failure | Expected/terminal failures, partial success, safe retry/reconciliation where needed, ambiguous external outcomes |
| Data | Durability, migration, export/deletion and restore behavior |
| Release | Compatibility, rollout/flag needs, rollback limits and correct running version |
| Support | How authorized staff diagnose and repair an actual case |
| Product | Outcome being measured, decision it informs, owner, privacy and cost |

Do not introduce a generic retry policy, automatic recovery, shutdown/export plan or support UI merely because it appeared in an earlier proposal. Resolve actual needs during implementation.

A backup restores. A release runs the intended version. A failed job can be diagnosed. A support action respects scope. A metric answers a decision. If alerts are configured, verify delivery to an owner. These checks prove operation; installing tools alone does not.

## Deferred observability work
C78 clarifies the initial C77 rejection: avoid Protobuf dependencies/tooling; small handwritten OTLP output is acceptable in principle. Prometheus/PromQL remains a soft exception. No backend, collector, SDK, index or anomaly algorithm selected. C81 defers detailed design/trials until Andrey experiments.

Preserve [all inspectability options](100-lightweight-inspectability.md), [anomaly candidates](101-lightweight-anomaly-detection.md) and [files/indexes discussion](102-file-based-observability.md). This deferral does not suspend the instrumentation requirements or settled analytics rules.
