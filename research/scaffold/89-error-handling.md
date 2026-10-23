# Expected and unexpected errors

Confirmed by Andrey, 2026-10-21. [Recipe](../../skills/scaffold/references/error-handling.md).

## Principle
Expected errors receive careful handling and propagation layer by layer. Unexpected errors propagate to a reasonable top-level wrapper (request, user action, job, run-loop iteration) and receive generic handling there. Do not crash the entire app merely to terminate the failed operation.

## Go
HappiGrid's proposed policy accepted: returned expected errors; panics for unexpected/internal failures including database I/O; recovery/logging at request/job boundary, HTTP 500 or failed job; no automatic retry after job panic.

Reason: Go supports recovering panics at those boundaries. Recovery does not imply that every operation completed or partial changes are rolled back; previously confirmed change/transaction rules still apply.

## Swift
Do not transplant Go panic behavior into process-terminating traps. Concrete mechanisms remain part of the deferred modern iOS/macOS research. The cross-language intent is confirmed; no Apple internal implementation chosen.
