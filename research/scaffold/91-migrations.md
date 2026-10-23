# Migrations

## Confirmed · C58 · 2026-10-23
Small database migrations run automatically at startup; large rewrites use preview-and-execute maintenance operations. Default budget **5 seconds per migration**. Startup migration work delays readiness and must fit brief deployments.

Per-migration budget is not a total startup limit or an instruction to abort live writes after five seconds. Overrun behavior is confirmed below in C60. Logs, metrics, access checks and representative-size validation in the [recipe](../../skills/scaffold/references/migrations.md) are implementation guidance.

## Confirmed · C59 · 2026-10-23
Rollback compatibility is ultimately a business decision. Start with a strong best-effort default for keeping the previous executable usable; reevaluate once MVP is reached. No mandatory post-MVP policy selected. Operator-directed recovery remains C49.

User: “For migrations, it’s a business decision eventually, but we start with strong default for best effort, and reevaluate once MVP is reached.”

## Confirmed · C60 · 2026-10-23
User accepted: let a startup migration exceeding 5 seconds finish safely and log the overrun; enforce the budget through testing rather than a runtime cutoff. Total startup limit remains unselected.
