# Database migrations

Run small migrations automatically at startup, before readiness. Default budget: **5 seconds per migration**. Keep overall startup compatible with brief deployments; this is not a 5-second total startup budget.

Move large rewrites to explicit preview-and-execute maintenance operations. Follow the bulk-operation policy for transaction boundaries and resumption; do not assume automatic resume.

Check duration against representative data sizes. The budget does not prescribe killing or interrupting a write transaction; overrun handling remains open.

Restrict maintenance preview/execution to authorized operators. Measure migration duration and failures; log migration ID, result and duration without customer data or secrets.

Compatibility with older executables and rollback policy remain open.
