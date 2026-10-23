# Change objects and changesets

Source: Andrey's direct interview answer, 2026-10-19.

Current recipe: [changes, undo and history](../../skills/scaffold/references/changes.md).

## Confirmed direction
Use explicit replayable change objects from day one, including online-only apps. Undo and auditing justify them independently of offline sync.

Historically omitted largely because a satisfactory architectural framework was missing, not because the capability lacked value. Bubblehouse's omission causes recurring regret. Andrey expects AI to make this framework more practical to implement.

## Desired processing model
1. User request is the initial change; open a changeset.
2. Its handler records further changes as needed.
3. Separate effect handlers react to changes: when X changes, recompute Y or schedule Z.
4. Process iteratively until no new effects remain.

Keep handlers separate while providing one common mechanism for cross-cutting reactions. This is a proposed mechanism to refine, not a validated implementation.

## Transaction boundaries — refined
- Most requests produce one atomic changeset within one transaction; optimize this path.
- A changeset stays entirely within one transaction. Multiple changesets may be batched in one transaction.
- A bulk request may span many atomic changesets/transactions, all traced to one origin.
- This supersedes C10's tentative terminology where a changeset itself could span transactions.
- Validate request viability before starting writes; try hard to avoid transaction rollback. Exact preflight mechanics remain open.
- Every change records enough information to undo it.

## Bulk work and recovery
- Typical cases: imports and maintenance affecting millions of rows, with preview and explicit execution.
- Future changes may be generated during processing, or held in a separate draft. Persistent applied-change history sees only changes included in write transactions, not a preview of future work.
- The persistent changes layer does not auto-resume bulk work; it has no unfinished future changes to execute.
- Higher-level operation tracking can enumerate unfinished work and support manual or automatic resume by procedure.
- Do not auto-resume everything at startup: heavy/dangerous work could worsen precarious recovery conditions.
- Keep bulk work easy to code; do not require materializing all changes in advance.

## Operations — provisional
An operation/request may be short-lived or long-running and may span changesets. A separate operations layer is a candidate, not a settled abstraction.

**TODO: gain implementation/use experience and refine operations, requests and changeset concepts.** Andrey explicitly deferred this design; do not keep interviewing its taxonomy now.

## Modeling context
Read referenced chat **Extend KVO modeling and encoding**, `01a13edf-805e-7472-8adf-2b65f2721b4d` (local). Its original request seeks schema-based generic access and mutation across database rows, with compact/fast representations and future extensibility. This explains the foundation for generic changes; it does not establish that this changeset system is implemented.

Local `edb/research/kvo/README.md` explicitly separates experimental mutation/change machinery from production transaction integration and ordered application. Treat that document as implementation context, not independent evidence of Andrey's values.

## Undo — confirmed
- Prefer reusable generic changes supplied by the modeling framework (such as KVO).
- Preserve operation semantics: a balance increase is `Increment(+20)`; undo is `Increment(-20)`, not restoration of the old balance.
- Run shared consequences centrally for ordinary changes and undo alike. Example: when a balance becomes negative, trigger staff notification unless caused by a staff user with `LeaveNegativeBalancePermission`.
- Do not duplicate those rules in action-specific or undo-specific handlers.
- Change-specific undo remains available when genuinely needed; truly undo-specific behavior is allowed.
- Actor/cause context matters to shared rules. Exact provenance and permission evaluation semantics remain open.

## Effect observation — refined
- Final-candidate observation is a useful model, not a strict scheduling requirement.
- For simplicity, conditions may be observed in the settled state or at any convenient point during processing.
- A matching condition may set a pending flag or append pending work. Do not retract effects already processed/scheduled merely because later changes remove the condition.
- Avoid cancellation/reconciliation machinery for rare edge cases without a concrete need.
- Handlers may add changes and trigger further processing until no effects remain. Exact scheduling and convergence safeguards remain open.
- This refines C13: intermediate-state observation is allowed when convenient. No universal promise that only conditions true in the eventual final state produce effects.

## Persistent history — confirmed initial design
- Store all changes as produced; no initial compaction of equivalent changes.
- Each change records its origin through a parent change ID, forming a causal tree.
- Example: `Increment(+20)` from the original handler stays separate from `Increment(+10)` caused by a handler reacting to an accruable dimension exceeding 100.
- Preserve why each change occurred, not just the net mutation. Root representation and handler metadata details remain open.

## Ledger, history and replay — confirmed
- Conceptually, the database consists of a ledger and change history. The ledger is state to which changes are applied.
- Conceptually it results from all past changes, each processed with the code in use at that time.
- Code evolves: old changes need not remain processable or reproduce their original results under new code. No permanent replay-compatibility promise.
- Take occasional ledger snapshots. History must be replayable from the recovery snapshot used.
- Ledger WAL may reduce required replay to seconds or minutes. Generally strive for roughly a week's changes to remain replayable.
- A week is a design target, not a chosen retention policy or unconditional compatibility guarantee. Snapshot/WAL mechanics and deployment boundaries remain open.
- C53: WAL deferred until EDB technically supports it; none for now. Snapshot backups are the current recovery mechanism; no separate interim off-server change-history replication.
- Supersedes the assistant's false choice between current rows plus audit and permanently replayable history.

## Applying changes vs deriving effects — confirmed
- Recovery applies all recorded simple changes directly; do not rerun business-effect handlers.
- Complex effect processing must express every resulting ledger mutation through simple changes. Those results are recorded too.
- Simple changes mutate the ledger directly without complex side effects.
- Derive effects when adding new changes to a changeset, not when applying recorded changes during replay.
- Example: original `Increment(+20)` and derived `Increment(+10)` both replay once; no handler generates another increment.
- “Simple” still needs a concrete API boundary; do not infer a complete primitive vocabulary yet.

## Request viability — confirmed
- Only the initial request handler may discover a viability problem and reject the request; do this before writes.
- Derived effects are not allowed to introduce request-rejection conditions.
- Do not add a general speculative working view / validation phase just to support derived-effect rejection.
- If a real exception arises, design a reasonable solution then. Expected to be extremely rare; no exception machinery now.
- This addresses business viability, not a claim that storage failures or programming defects cannot occur.

## Still open
- Bulk progress, checkpoint details, retries and partial failure policy; refine through experience.
- Which derived effects belong in each atomic transaction; which run later?
- Exact generic-change vocabulary and initial-request representation; replay already applies recorded simple mutations.
- Effect ordering, repeated triggers, cycles and convergence.
- Undo scope and irreversible external effects.
- Audit provenance, actor, authorization and sensitive fields.
- Snapshot/WAL recovery boundaries and recent-history compatibility across deployments.
- External-action delivery/recovery mechanics; direct ledger replay must not regenerate business effects.

These are remaining design questions, not approved requirements. Ledger snapshots and bounded replay are selected above; avoid importing additional architectural obligations from a label.

## Historical interview handoff
Enough direction for an initial design; remaining machinery should be refined through concrete implementation experience. The interview continued with [accounts](73-accounts-decisions.md). Use [STATE](STATE.md#resume-here) for current work.

C86: ordinary user-deleted data has a [30-day default recovery window](108-deleted-data-recovery.md). This does not reopen the change/undo model or select a storage representation.
