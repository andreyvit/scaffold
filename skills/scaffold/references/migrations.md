# Database migrations

Run small migrations automatically at startup, before readiness. Default budget: **5 seconds per migration**. Keep overall startup compatible with brief deployments; this is not a 5-second total startup budget.

Move large rewrites to explicit preview-and-execute maintenance operations. Follow the bulk-operation policy for transaction boundaries and resumption; do not assume automatic resume.

Enforce the budget through testing against representative data sizes. If a startup migration exceeds 5 seconds at runtime, let it finish safely and log the overrun; do not impose a runtime cutoff for this budget.

Restrict maintenance preview/execution to authorized operators. Measure migration duration and failures; log migration ID, result and duration without customer data or secrets.

Strong initial default: best-effort compatibility with the previous executable. Rollback compatibility is ultimately a business decision; reevaluate once MVP is reached. The milestone triggers review, not a mandatory compatibility guarantee. Recovery remains operator-directed.
