# Error handling

**Expected failures:** handle deliberately; propagate layer by layer, preserving useful context and deciding the appropriate response at each boundary.

**Unexpected failures:** propagate to a reasonable top-level wrapper—request, user action, job or run-loop iteration—and handle generically there. Fail the affected operation without deliberately crashing the entire app/process.

## Go default

- Return expected application errors normally.
- Panic for unexpected/internal failures, including database I/O failures.
- Recover at request/job boundaries; log the failure and return HTTP 500 or mark the job failed.
- Do not automatically retry a job after panic.
- Keep code panic-safe; recovery must not assume the operation completed.

## Development exception

The [AI development harness](development-harness.md) fails fast on unexpected failures by default. Enable normal recovery when testing failure handling. Production keeps request/job recovery.

## Other languages

Preserve the principle, not Go's mechanism. Do not substitute a process-terminating Swift trap for a recoverable Go panic. Exact Swift handling awaits the separate modern iOS/macOS design research.
