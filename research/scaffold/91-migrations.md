# Migrations

## Confirmed · C58 · 2026-10-23
Small database migrations run automatically at startup; large rewrites use preview-and-execute maintenance operations. Default budget **5 seconds per migration**. Startup migration work delays readiness and must fit brief deployments.

Per-migration budget is not a total startup limit or an instruction to abort live writes after five seconds. Enforcement/overrun behavior remains unselected. Logs, metrics, access checks and representative-size validation in the [recipe](../../skills/scaffold/references/migrations.md) are implementation guidance.

Next: compatibility with the previous executable—mandatory rollback compatibility vs best-effort compatibility and forward fixes when preservation adds complexity.
