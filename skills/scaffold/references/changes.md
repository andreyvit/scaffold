# Changes, undo and history

Use explicit replayable change objects from day one, including online-only apps. Undo and auditing justify them independently of [offline sync](offline-sync.md). This is a design direction; the modeling framework is not assumed complete.

## Processing and transactions
- The initial request opens a changeset; handlers record changes and common effect processing iterates until no further effects remain.
- Only the initial handler discovers business viability problems and rejects the request, before writes. Derived effects must not introduce new rejection conditions. Storage failures and programming errors can still occur.
- A changeset is atomic within one transaction. Most requests use one changeset/transaction; several changesets may share a transaction.
- Bulk work spans transactions under one traceable origin. Generate pending work lazily or keep a separate draft; applied-change history records only changes included in write transactions.
- Higher-level tracking can enumerate unfinished procedures and support manual or automatic resume by procedure. Do not resume all bulk work at startup. The change history itself is not a bulk-work queue.

## Undo and effects
Every change carries enough information to undo it. Prefer generic semantic inverses: `Increment(+20)` undoes as `Increment(-20)`, rather than restoring the old balance.

Run shared consequences for ordinary changes and undo alike. Rules may use actor/permission context; a negative-balance notification is one example. Add specific undo behavior only where needed.

Observe conditions in the settled state or whenever convenient during processing. Accumulate pending effects; do not retract already processed or scheduled work merely because a later handler removes the condition. Avoid reconciliation machinery for hypothetical rare cases.

Store every produced change separately, with a parent change ID forming a causal tree. Do not compact equivalent increments from different causes into a net change.

## Ledger and replay
The ledger is the current state to which changes apply. Conceptually it reflects past changes processed with the code then in use; old history need not remain replayable forever.

All complex business processing must express ledger mutations through recorded simple changes. Recovery applies those recorded mutations directly, without running business-effect handlers again. If an original increment caused another increment, replay both once; do not generate the consequence again.

Keep ledger snapshots and support replay from the recovery snapshot used. Strive for roughly a week of recent replay compatibility; this is a design target, not a retention promise. Code/deployment compatibility needs a concrete implementation.

Current off-server recovery uses [snapshot backups](backups.md). WAL waits for EDB support; do not create interim off-server change-history replication. Local change history does not make hourly backups lossless.

## Refine through implementation
Primitive vocabulary, request/operation taxonomy, effect order and convergence, bulk progress/resumption, undo scope and irreversible external effects remain open. Gain experience before finalizing them; do not build a speculative framework or restart the abstract interview.

Keep meaningful [customer-data access auditing](customer-data-access.md), [ordinary deletion recovery](deleted-data.md) and [data export/erasure](data-rights.md) explicit. A mutation history alone does not implement all three.

Source: [C9–18, refined chronology and examples](../../../research/scaffold/81-changesets.md); C11 supersedes C10's tentative transaction boundary, C14 refines C13's observation rule, and C53 defers WAL.
