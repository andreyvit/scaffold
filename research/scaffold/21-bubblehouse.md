# Bubblehouse

Pre-AI evidence: loyalty backend, original social-app backend, selected iOS commits. [Sources](23-bubblehouse-evidence.md).

## Explicit writing
- Keep API/storage names stable while internal names change. Avoid code generation when it adds little. B1.
- Integration boundaries earn their cost by keeping code simple, isolated and teachable. Use local calls with public API contracts. B2.
- Choose storage with known limits; do not become its largest deployment. Plan tenant splits; count their I/O cost too. B3.
- Prefer simpler backup transport when the alternative adds implementation work and cost. Test restores; suppress external writes when debugging a copy. B4.
- Embedded frontend auth must follow the host’s session. An independent cookie would outlive host logout. B5.
- Treat missing protections as unfinished work: passkeys for privileged users, security logging, rate limits, replication. B6.

## Code inferences — confirm
- Carry diagnosis through execution context. Count business outcomes as well as requests/errors/jobs. B7.
- Persist job state, failures and next run time; reuse this machinery across integrations. B8.
- Enforce tenant ownership in shared loaders; private errors stay private unless given a public message. B9.
- Tests run real app/storage with controlled clock and outgoing HTTP. B10.
- Preserve awkward payment outcomes for reconciliation; test orphaned receipts. B11.
- Broad principles survive tool changes: legacy server used PostgreSQL; later server used Bolt. Neither proves a universal storage choice. B12.

## Counterweights
- Many layers were extracted incrementally from `fireback`; this does not prove every new app needs all layers immediately.
- Some infrastructure and loader code is Stanislav’s. Excluded unless earlier Andrey lines can be traced through moves.
- Old metrics include shop labels; this proves a support need, not an unlimited-cardinality metrics policy.
- Current `_readme` guidance is AI-era context, not evidence of original values.

## Questions after this source
1. What earns a managed dependency: payments, email, storage, database, auth?
2. What loss/downtime budget is acceptable for each product class?
3. Which operations must be replayable, and which may be discarded?
4. Should integrations always share public contracts, or only when external callers need the same capabilities?
5. Which diagnostics belong in metrics, structured logs, audit records or product analytics?
6. How much hardening is mandatory at first release? Historical omissions are not approved exceptions.
7. Should existing code be extracted before a feature, or only once mixing makes it hard to follow?
