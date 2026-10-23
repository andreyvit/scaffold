# Scaffold research state

Goal: extract Andrey’s engineering values from original material; use them to choose architecture defaults and useful questions.
Started: 2026-10-18 (Maldives). Initial source pass and expanded LifeBase/hiring pass complete; coverage limits remain recorded. Core values confirmed; native mobile chosen. Interview has reached C58. Two further value candidates remain labelled, not approved.

## Resume here
Canonical repository: `/Users/andreyvit/Developer/andreyvit/scaffold`. Research moved here from `~/env` on 2026-10-23. Continue in this repo.

**Next action: ask the unanswered migration-compatibility question below.** The user interrupted the interview to move repositories; no answer was given. The assistant's proposed choice is not confirmed.

> Must migrations keep the previous executable usable, or is rollback compatibility best-effort—with a forward fix preferred when preserving compatibility would complicate the code? I’d propose the latter.

Context: [C58](78-confirmed-decisions.md) confirms small automatic startup migrations with a **5-second budget per migration**; large rewrites use preview-and-execute maintenance operations. [C49](78-confirmed-decisions.md) rejects automatic rollback/recovery until serious SRE scenario testing. This question concerns whether an operator can run the previous executable against migrated data. See [migration notes](91-migrations.md) and [recipe](../../skills/scaffold/references/migrations.md).

Interview **one question at a time, max terse**, with all necessary context. After each answer, update this resume block, append state/confirmation records, and update the relevant topic and recipe. Preserve reasons and qualifications. Never count an assistant proposal as user approval.

Later: continue server/web architecture and operational defaults; auth/permissions, jobs and observability still need decisions. Modern Apple internals require a separate later research step; staff/customer identity separation and operation taxonomy remain deferred. Do not reopen those now. Older “Next” entries below and the scope/question outlines are historical, not the current cursor.

## Contract
- Work sequentially: Happy Grid → Bubblehouse → personal repos → Heynote → Zoo v1/skills → LifeBase → Ulysses; revisit earlier sources when new evidence helps.
- Before each source: record unanswered value questions. After: answers, counterexamples, remaining questions.
- Explicit user words > attributable manual code > inference. AI text is a locator, never evidence of a user value.
- Git author alone proves no human authorship after 2025-06-01. Earlier Andrey code is eligible per user’s cutoff; inspect authorship of relevant lines.
- Distinguish current user choice, original statement, code inference, proposal, unknown. Historical choices may be obsolete.
- Keep user-facing outputs terse. Put precise provenance in source files. Never copy credentials or unrelated personal records.
- Source repositories read-only. Preserve dirty work. Recipes change after decisions are confirmed.

## Outputs
- [Start here](README.md): short index.
- [Values](70-values.md), [requirements](71-requirements.md), [architecture](72-architecture-decisions.md), [accounts](73-accounts-decisions.md).
- [Operation](74-operations.md), [recipe shape](75-recipe-shape.md), [modern scan](76-modern-options.md), [method](77-research-method.md).
- [Interview](01-questions.md): remaining questions; confirmed answers in [78](78-confirmed-decisions.md), next scope round in [79](79-next-scope.md).
- [Coverage](03-coverage.md): precise limits; [checkout inventory](02-repositories.tsv); source files retain evidence and earlier questions.

## Initial setup — historical
- Read scaffold and skill-creator skills; found Zoo terse skill.
- Existing scaffold: env/skills/scaffold, linked from ~/.codex/skills/scaffold; two short references: environments and JSON config.
- env has existing dirty/untracked work including skills/. No edits to it.
- Found ~/Developer/andreyvit/happigrid and happigrid2. Both contain AI-era work under Andrey’s author identity.
- Initial focus was Happy Grid authorship; completed below.

## Initial plan — historical
1. Interview round 1: supported product profiles and constraints. Ask in small rounds.
2. Apply confirmed values to concrete choices; preserve reasons and exceptions. Historical authorship uncertainty does not undo direct confirmation.
3. Explore server/web and native iOS/Android architecture branches; no default shared-UI comparison.
4. Write only confirmed defaults into scaffold; keep source evidence here.

Core values accepted and amended in the first interview response. See 78 for subsequent confirmed decisions; use “Resume here” for the current question.

## Resumption
Start at “Resume here,” then read only relevant confirmed decisions and topic files. Never restart completed source passes. Record remaining sampling gaps explicitly; do not call an inventory a deep review.

## 2026-10-18 — Happy Grid first pass
- Recovered 43 root chats from read-only Codex index; extracted user-message records, excluding injected instructions and quoted assistant content from evidence.
- Wrote `10-happy-grid.md` and precise source pointers in `10-happy-grid-evidence.md`.
- README philosophy is candidate evidence: user reports manual reorganization, but exact bullet authorship not yet established.
- Direct user corrections establish useful abstraction, separation, inspectable development, real-flow tests and UX priorities.
- Account identity rules evolved; explicitly preserve this tension for interview.
- Repo inventory: 163 nonempty checkouts after excluding vendor/build/research copies; `02-repositories.tsv` is inventory only, not review coverage. Counts include all refs and need duplicate grouping.
- Scratch notes located: iCloud Drive/Notes/scratch.txt and scratch-2.txt. LifeBase: iCloud Drive/Me. Ulysses cloud container located. Not yet analyzed.
- Current: Bubblehouse, questions in `20-bubblehouse-questions.md`; pin historical snapshots and verify Andrey authorship.
- Temporary aids: `/tmp/scaffold-repo-inventory.json`, `/tmp/scaffold-happigrid-threads.json`, `/tmp/scaffold-hg-user-messages.json`. Durable findings do not depend on them.

## 2026-10-18 — Bubblehouse first pass
- Pinned pre-cutoff backend snapshot `aaa53bdc6fbda464d7d563d696ebca76719469ed`; read historical docs + sampled jobs, metrics, auth/errors, loaders, integration execution and test harness.
- Verified authorship, including code-move tracing. Found mixed infra/health authors; excluded Stanislav decisions.
- Read selected legacy 2019–2021 startup, diagnostics, retention and payment changes.
- Found iOS archive with full Git metadata; extracted only `.git` to `/tmp/scaffold-bubblehouse-ios` for historical reads. Found strong authored rationale on state flow and bounded offline queue. Excluded explicitly Filip-style guide.
- Outputs: `21-bubblehouse.md`, `22-bubblehouse-mobile.md`, `23-bubblehouse-evidence.md`.
- Coverage limit: source samples, not exhaustive 6k-commit review. Need deeper history only where unresolved questions merit it; no current docs as original-value evidence.
- Current: personal repos, initial questions in `30-personal-repos-questions.md`. Inventory needs classification/deduplication and detection of non-Git projects.

## 2026-10-18 — Personal libraries first pass
- Pinned 43 README snapshots and checked line authorship. Coverage in `32-library-sources.tsv`; some short README-only repos still need code sampling.
- Wrote `31-small-libraries.md`: bounded abstractions, stdlib composition, measured performance, explicit exceptions to no-codegen/no-dependencies/100%-coverage slogans.
- Found direct contrary evidence to cutoff assumption: pre-2025 `aidev` labels its README and some code AI-generated. Excluded; apply this exception wherever explicit evidence exists.
- Next: native personal apps (DeepWorkTimer, Wonderful, Sarekon, Maccel), LiveReload and authored public writing; complete remaining repo survey without promoting empty READMEs into findings.

## 2026-10-18 — Native personal apps
- DeepWorkTimer: local state/effects split, saved memento, activity-aware timers, local analytics; platform API adoption removed a helper app. Output `33-deep-work-timer.md`.
- Wonderful iOS: change/undo/rebase sync with JSON test export. Useful older precedent for explicit change machinery; conflict behavior is not an approved recipe. Output `34-wonderful.md`.
- Sarekon iOS: authored ServerValue distinguishes cached data from last fetch result; Android selected Andrey fixes establish cache reset and hit-target care. Analytics removal motive unknown. Output `35-sarekon.md`.
- Maccel/MacAccelerator share history; avoid double-counting. Code sampling pending.
- Next: LiveReload and public writing, remaining small repos; then Heynote, Zoo v1, LifeBase and Ulysses.

## 2026-10-18 — LiveReload and public writing
- Read attributable NodeApp architecture rationale and project-test harness; sampled Maccel improvements. Output `36-livereload-and-writing.md`.
- Found public principles page, first visible September 2025; exact human authorship unresolved. Earlier 2011/2012 essays have original pre-AI commits.
- LiveReload 2/old have stale Git alternate-object paths. Read-only `GIT_ALTERNATE_OBJECT_DIRECTORIES` pointing to LiveReload 3 restores history access; no source edits. Inventory counts need correction.
- Next: notes then Zoo. Questions in `40-notes-questions.md`. Remaining small-code samples/coverage classification follow high-value written sources.

## 2026-10-18 — Heynote
- Found synced Heynote format files in iCloud Drive/Notes. Read targeted instruction blocks; excluded copied assistant answers and unrelated content.
- Outputs `41-heynote.md`, `42-heynote-evidence.md`: five explicit code values, HOW/WHAT separation, malleable abstractions, evident security, actual-flow tests, terse writing.
- Scratchpad lacks per-block authorship. Original-looking instructions remain labelled until matched to user messages or confirmed. Do not treat the whole file as human-authored.
- Zoo v1 at `2aa5125` found. Agent personas visibly contain generated elaboration; next recover original prompts where possible.

## 2026-10-18 — Zoo and LifeBase
- Zoo v1 recovered at `2aa5125`. Public Zoo essay describes persona choices and explicitly identifies generated instructions. Saved `43-zoo.md`; persona elaboration excluded.
- Read relevant LifeBase writing; `50-lifebase.md` records four architecture goals. Dictated/edited draft authorship is not fully established; raw matching transcript not found in targeted search.
- Found Ulysses cloud sheets directly, parsed XML read-only; 514 non-trash sheets indexed temporarily. Selected 2021–2022 drafts corroborate malleability, layering, dependency choices, release strategy.
- Ulysses includes an original iOS project layout and HappiGrid UX prompt. Today’s request also exists there; do not double-count. Source details/output next.

## 2026-10-18 — Ulysses
- Read selected engineering drafts (2021–2022 content mtimes), plus matching HappiGrid UX instructions. `51-ulysses.md`, `52-mobile-layout.md`, `53-ulysses-sources.tsv`.
- Recovered actual historical iOS layout and detailed dependency decision tree. Draft separates hard model/presentation boundary from contextual MV* choices.
- Original-looking drafts explicitly explain proportional future effort, local reasoning, risk-driven planning, rollout safety, and UX responsibility. Empty headings are not completed guidance.
- 514 non-trash sheets inventoried by title/group; inspected relevant writing, not unrelated personal content. Trash not treated as current intent.
- Source dates are filesystem content mtimes, not verified creation dates. No raw LifeBase transcript recovered yet; public principles exact authorship still open.
- Next: remaining owned repository survey and targeted architecture gaps; update coverage; synthesize values, supported requirement choices and interview.

## 2026-10-18 — Remaining sources / counterexamples
- Targeted samples of mvp, buddyd, httpform, httpserver, minicomponents, journal, router, small tools and watchdog. Own-line checks recorded in `61-code-sources.tsv`; findings in `60-other-code.md`.
- Own Bubblehouse frontend commits reveal cost containment and an incident-time build-gate bypass; do not equate existing Next.js stack with Andrey’s preferred architecture.
- Found untracked 2024 SSR/Turbo/Stimulus draft in mvpalliance, plus tracked planning exceptions. `62-more-writing.md`. Excluded generated-looking outline and sales-copy template.
- Standard-blocks vs cathedral tension recorded for interview. Modern framework choices still unapproved.

## 2026-10-18 — Synthesis and current status
- Created values, requirement profiles, architecture/account decisions, operations contract, compact recipe example and interview method (70–77).
- Replaced initial question queue with four interview rounds. Source-specific files preserve how questions evolved.
- Completed targeted checks of remaining small tools/stubs; findings in 63. Inventory now labels coverage and shared histories; 163 checkout rows and 44 library rows. Corrected stale LiveReload counts.
- Modern scan uses official Apple, Android, React, Hotwire, JetBrains, Flutter and OWASP sources. Capabilities only; no selected mobile stack, no benchmark/prototype claims.
- Strongest original finds: Happy Grid user corrections; Heynote five-value block; older Ulysses dependency decision tree and iOS layout; 2024 SSR/Turbo/Stimulus draft.
- Main unresolved judgments: supported profiles, native vs shared implementation, identity ownership, loss/downtime/privacy budgets, appropriate foresight and AI-specific process.
- Source repositories and actual recipes were not edited. No commits, pushes or external messages.
- Automatic pass is targeted research, not exhaustive line review. Remaining evidence gaps are explicit in 03; further source reads should answer a concrete unresolved judgment.
- Verification: all local Markdown links resolve; all 44 pinned library revisions exist; selected Ulysses and Heynote source hashes still match; no trailing whitespace. Index opened in Codex (queued by app).
- Research deliverables complete. Resume with interview, not another inventory. Only add deeper source work when an unresolved decision calls for it.

## 2026-10-18 — First interview response
- Andrey accepted V1–V13. V7 is stronger: build/own by default; dependencies need a reason. V12 centers actual users, expectations and preventing confusion.
- Added V14: simplicity/elegance and thought-through details; spend modest extra attention at comparable cost. Avoid future minefields; concrete cost can justify compromise.
- Privacy, loss and downtime are per-project requirements with defaults: lean private, no loss, only seconds of hidden downtime. No guarantee inferred from proxy buffering.
- Native APIs per mobile platform are chosen; duplicated implementation accepted under AI. Archived shared-UI options as superseded research.
- New own pre-cutoff Bubblehouse evidence: misleading discount error prevented through sequencing; imported birthday state/eligibility clarified; familiar wording and accessible-tab explanation. Examples, counterexamples and source IDs in 64.
- Updated values, architecture map, operations, modern scan and interview/index. Added 78 confirmation record and 79 scope proposal. Prior source-pass entries above remain historical.
- Next: choose supported requirement variants, starting server/web; then modern native architectures. No need to repeat core-value approval or native-vs-shared interview.

## 2026-10-18 — Principal hiring and expanded LifeBase
- Followed explicit requests to inspect principal postings and broaden the Me review beyond architecture writing. Outputs 65–67; 22 exact source paths and hashes.
- Hiring emphasizes breadth, mechanism-level understanding, learning and judgment under unavoidable complexity. Candidate addition, not silently added to the approved values.
- Traced posting copies and May 18 manual-edit clue (`67ef070`); later expansions and screening prose remain unauthenticated. Derived voice/evaluation guides and candidate records excluded as independent evidence.
- Topic-screened LifeBase text, including older `.txt` drafts; read relevant Core, Details, Raw, Daily/Diary, Past and Inbox material. This is a broad engineering/product pass, not every personal entry.
- Recovered raw architecture dictation (`Raw/2025-12-10-004718.md`) for reasons, practical breadth, velocity and fewer mistakes. This corrects the earlier unsuccessful-search entries; remaining edited essay wording still has source gaps.
- Strong new UX evidence: Mockko discoverability observations; LiveReload compilation/minification workflow critique. Launch diary demonstrates a concrete cost limit on polish.
- Raw helpdesk judgment distinguishes missing MVP features from unacceptable failures in its central customer interaction. Raw admiration for decades-old software suggests longevity and respect for familiarity; candidate only.
- Core early-PMF document is derived synthesis; its managed-auth/database default is not Andrey's source value and conflicts with the now-confirmed ownership-first preference.
- Updated source coverage, values links and evidence. Actual recipes and source repositories remain unchanged. Next: scope interview, then server/web decisions; native research follows selected requirements.
- Verification: all 40 research Markdown files passed local-link and whitespace checks; all 22 expanded LifeBase source hashes match. Expanded findings queued for opening in Codex.

## 2026-10-19 — Offline interview
- Interview format: one question at a time, max terse, include all necessary context.
- C8: offline editing/sync belongs in initial recipe scope as optional architecture, never the app default. Server processing/rendering preferred.
- Saved both user-described mechanisms and reasons in 80; updated 78, 79 and architecture map. Protocol details are not yet validated.
- Next question: minimum preparation in online-only apps for future offline support. Do not infer change logs or replay machinery are required upfront.

## 2026-10-19 — Changeset interview
- C9: explicit replayable change objects from day one for undo/auditing; supersedes the proposed central-functions-only preparation.
- Recorded user-described iterative changes/effects model and reasons in 81; linked from 80 and confirmation record. Not equated with event sourcing or a finished protocol.
- Next interview question: atomic changeset boundary and post-commit external effects. One question, with concrete context.

## 2026-10-19 — Atomic and bulk changes
- C10: changeset identity is independent of transaction boundary. Most changes atomic; large compound/bulk changes span transactions, traced to one origin. Bulk API must stay easy to code; name tentative.
- Updated 81 and confirmation record; previous atomic-whole-changeset proposal superseded. No automatic compensation or recovery policy inferred.
- Next: bulk interruption/recovery default, with concrete partial-completion example.

## 2026-10-19 — Bulk recovery and deferred operations design
- C11 refines C10: atomic changesets, potentially many per transaction; bulk operations span transactions. Record one origin without forcing one transaction.
- Applied change persistence excludes future preview/draft work; bulk generation may be lazy. Resume belongs to higher-level procedure tracking, with explicit manual/auto policy and startup load/safety concerns.
- Viability checks before writes; try hard to avoid rollback; each change contains undo information.
- Read referenced KVO chat via read_thread and checked relevant local research context. No other-chat instructions executed, no messages sent, no EDB edits. Experimental modeling infrastructure is not a completed changeset implementation.
- User explicitly deferred operations taxonomy: operations can be short-lived or long-running; TODO gain experience and refine. Updated 81 and confirmation record.
- Next interview: undo semantics after intervening edits; leave deferred operations concepts alone.

## 2026-10-19 — Undo semantics
- C12: reusable generic changes retain semantics; Increment undoes by inverse increment. Modeling framework supplies common machinery.
- Shared consequences apply centrally to changes including undo, with relevant actor/permission context. Reserve custom undo logic for actual special cases.
- Updated 81 and confirmation record. Next: whether state-derived rules observe intermediate changes or final net state within an atomic changeset. Operations taxonomy remains deferred.

## 2026-10-19 — Final candidate
- C13: handlers observe final candidates, not intermediate mutation states. Handlers can produce further changes/candidates until effects settle; first candidate usually matches final result.
- Rejected assistant's suggested intermediate-transition branch; no such requirement inferred.
- Updated 81 and confirmation record. Next: notifications whose triggering condition disappears during later effect processing. Operations taxonomy remains deferred.

## 2026-10-19 — Effect accumulation refinement
- C14 supersedes strict C13 observation wording: final-state or any convenient processing-time condition checks are allowed.
- Pending flags/lists accumulate matched work; do not undo processed/scheduled effects when conditions later disappear. Avoid complexity for rare edge cases.
- Updated 81 and confirmation record, preserving chronology. Next: persistent history detail/compaction, distinct from effect scheduling. Operations taxonomy remains deferred.

## 2026-10-19 — Causal change history
- C15: initially persist all changes, each with parent change ID. Preserve original-handler vs triggered-handler origins; no initial compaction.
- Updated 81 and confirmation record. Next: current-state storage vs replayable-history source of truth; undo/auditing does not imply complete state reconstruction.

## 2026-10-19 — Ledger and bounded replay
- C16: ledger plus history; conceptual derivation uses each change's contemporaneous code. No indefinite old-change replay compatibility.
- Occasional snapshots plus replay since recovery snapshot; ledger WAL may need only seconds/minutes, but aim for a week of replayability. Not a retention decision.
- Corrected the assistant's overly binary source-of-truth question. Updated 81 and confirmation record.
- Next: whether recovery applies recorded derived changes directly with effect handlers suppressed, or regenerates them. Operations taxonomy remains deferred.

## 2026-10-19 — Change application and effects
- C17: direct replay of recorded simple changes; derived results are already recorded. No rerunning business handlers during replay.
- Complex effects must express ledger mutations through simple changes. Derive effects when adding new changes, separate from applying recorded changes.
- Updated 81 and confirmation record. Next: how pre-write viability checking interacts with proposed mutations and derived effects; clarify in-memory staging vs database writes. Operations taxonomy remains deferred.

## 2026-10-19 — Initial-handler validation
- C18: only initial request handler may reject for viability, before writes. Derived effects cannot introduce rejection conditions.
- User expects any exception to be extremely rare; solve a real exception when encountered, not with generic upfront machinery.
- Updated 81 and confirmation record; removed stale replay/source-of-truth questions already answered.
- Next interview topic: B2B identity across companies. Changeset/operation implementation details remain for experience-driven refinement.

## 2026-10-19 — Identity, profiles and smart defaults
- C19: shared login identity, per-company profiles including name/avatar; common application surfaces regardless of shared vs separate logins. Internal readiness for multi-login; UI exposure separate.
- Strictest combined company login policies; incompatible needs may use separate identities. First-class credential/email flows, not direct company-admin takeover of shared credentials. Security implementation remains unselected.
- C20: V15 smart defaults, especially low-attention decisions; V8 testing convenience and V12 user convenience strengthened. Preserve tradeoff: added code complexity earns its cost through convenience, testing and additive flexibility.
- Saved 82; updated values, accounts map and confirmation record. Next: personal-data ownership alongside company accounts.

## 2026-10-19 — Personal workspace
- C21: personal workspace uses the company/account model, with the individual as owner. Updated 82, accounts map and confirmation record.
- Next: whether the product's own staff share the login identity system or use a separate staff identity system. No staff access policy implied by shared identity.

- C21 rationale supplied: simplicity and internal consistency. Staff identity question remains unanswered; do not infer a choice from this rationale-only reply.

## 2026-10-19 — Staff/customer records
- C22: reuse login system, strongly default to separate staff/customer records unless expected surface overlap justifies combining them.
- Supersedes assistant's shared-identity default proposal; exact credential linkage and access policy not inferred.
- Updated 82, accounts map and confirmation record. Next: elicit underlying value/reason for separation rather than invent one.

## 2026-10-19 — Staff/customer decision deferred
- C23 supersedes C22's approval: no selected staff/customer default. User may reverse it and explicitly requests revisiting later.
- Preserve company ownership/customer deletion as an unresolved consideration; no legal conclusion or identity-deletion policy inferred.
- Updated 82, accounts map and decision record. Do not keep pursuing this question now.
- Next interview: account-free initial use when the product permits it.

## 2026-10-19 — Business viability and signup
- C24: convenience favors use before login, but signup timing is a business hypothesis within monetization/conversion funnel; measure and test. No universal anonymous-first default.
- Saved 83; updated V1 clarification, accounts map and confirmation record.
- Next: initial measurement vs controlled A/B experiment machinery. Staff/customer separation remains deferred.

## 2026-10-19 — Funnel operation clarification
- C25 clarifies C24: metrics, monitoring and testing alternatives are ongoing product capabilities, not just decision-making criteria or future validation intentions.
- Updated 83, values and operations; preserved confirmation history.
- Prior question about initial A/B experiment machinery remains unanswered. Do not infer an answer from this correction.

## 2026-10-19 — Experiments from day one
- C26: initial scaffold includes experiments and feature flags; sequential trials supported, concurrent A/B preferred. Measurement-only first is rejected.
- Updated 83, operations and confirmation record. No vendor/statistical method chosen.
- Next: default experiment assignment unit in B2B (company/workspace vs user), with context about shared workflows.

## 2026-10-19 — Experiment assignment scope
- C27: workspace assignment initially; per-user experiments later as product matures. Reason is early signup/activation learning, not primarily colleague consistency.
- User attributes reasoning to Rob Walling. Preserved attribution without treating derived LifeBase framework summaries as original user evidence or adding unverified quotations.
- Updated 83 and confirmation record. Next: default product analytics collection scope, explicit funnel/outcome events vs broader automatic interaction capture.

## 2026-10-19 — Business analytics before privacy implementation
- C28 corrects prior privacy framing: goals first, required analytics second, most private implementation third. Necessary usage measurement is not optional by default.
- Broad usage data supports hot paths, value, friction, funnels, retention/churn/LTV, economics and cohorts; free products may still need growth learning.
- Explicit owner choice needed to put privacy above metrics. Scale privacy methods to user-base size; techniques not yet selected.
- Updated 83, values, operations and confirmation record; old C5 flagged as clarified. No inference that usage tracking includes screen/session recordings.
- Next: session replay scope versus usage events. Staff/customer separation remains deferred.

## 2026-10-20 — Session replay feasibility
- User asked effort without SaaS, OSS candidate and exact capture scope before deciding replay default.
- Checked primary rrweb docs/repository and OpenReplay self-host deployment docs. Saved 84 with sources, owned-infrastructure proposal and explicit untested limits.
- rrweb candidate covers web recorder/player; DOM mutations/interactions, optional extensions, client masking. Production storage/access/retention and fidelity remain ours.
- Native replay not evaluated. No new confirmed decision, deployment or user-session capture. Next: resume replay default decision after user reviews feasibility.

## 2026-10-20 — Separate replay recipe
- C29: session replay valuable especially early; separate feature/file for capture, storage and playback; dedicated viewing permission required.
- Created skills/scaffold/references/session-replay.md and linked from skill entrypoint, per user's request. This is the first recipe promoted from this research; earlier source-only status is historical.
- Kept rrweb a candidate and recording rollout unspecified. Added concise security/metrics/logging and verification guidance per original recipe requirements. No implementation or real session capture.
- Next interview: whether analytics/experiment infrastructure lives within each app or a shared service; no choice inferred yet.
- Validation: bundled validator could not run because its Python lacks PyYAML; manual checks passed for required frontmatter, changed-file local links and whitespace.

## 2026-10-20 — Analytics deployment/storage
- C30: analytics/experiments inside app initially for simplicity; analytics database separate from main database.
- Updated 83 and confirmation record. Separate database is not inferred to require separate host or determine experiment configuration storage.
- Next: event delivery guarantees across databases, distinguishing business outcomes from incidental usage events.

## 2026-10-20 — Analytics loss and flushing
- C31: small analytics gaps acceptable. User gave load-sensitive 5–60 second flushing as one possible design; 300 seconds borderline but okay with tiny usage; hourly undesirable.
- Do not mandate transaction-coupled analytics outbox or turn timing examples into fixed timers. Analytics loss policy does not permit losing business ledger/billing records.
- Earlier availability question wrongly suggested a separate service; corrected to local crash/buffer gaps. Updated 83 and confirmation record.
- Next: individual analytics events vs predefined aggregates; separate retention decision from collection coverage.

## 2026-10-20 — Flush default clarified
- C32 corrects the earlier illustrative-only wording: 60 seconds is the default for periodic accumulation/flushing or throttled writes; tune for load. No implementation approach selected yet.
- Updated 83 and confirmation record. Individual events vs aggregates question remains unanswered.

## 2026-10-20 — Raw analytics journals
- C33: raw events by default initially; uncertainty makes future reprocessing valuable. Append-only/sequential journal storage acceptable.
- B2B journals per tenant; compress/encrypt; archive older files externally and remove local archived copies. High-volume payloads must avoid repeated common strings with efficient binary encoding.
- At scale explicitly revisit cost and ability to reprocess/aggregate; no indefinite keep-everything or full-scan promise.
- Checked user-linked journal public README and selected local files at e29e3db; recorded existing framing/sealing vs unverified external archiving/payload format in 85. No code changes.
- Updated 83 and confirmation record. Next: archived-event retention policy.

## 2026-10-20 — Analytics retention
- C34: finite raw analytics retention always; default 24 months, explicit product overrides such as 60 months allowed. Applies to external archives, not just local copies.
- Reasons: early-product data relevance declines as product changes; a clear cap helps explain retention in privacy policies/vendor due diligence. User rationale, not legal advice.
- Updated 85, 83 and confirmation record. Aggregate retention/deletion mechanics not inferred.
- Next interview: overall server process boundary, one deployable process vs separate web/background workers. Analytics/experiments remain in-app with separate database.

## 2026-10-20 — One process
- C35: strong one-process default for server web/jobs/analytics; split only for a very strong concrete reason.
- Reasons: simplicity, efficiency, embedded databases often limited to single-process access. Not a universal claim about every embedded database or selection of a specific engine.
- Updated architecture map and confirmation record. Next: embedded storage default and exceptions; deployment redundancy remains a separate decision.

## 2026-10-20 — EDB/Bolt default
- C36: Go-server primary business database defaults to EDB/Bolt. Reason: substantial continued investment by Andrey and Bubblehouse.
- Updated architecture map and confirmation record. Analytics storage and production readiness of new KVO/change machinery not inferred.
- Next interview: boundary between rich pages in SSR and a full SPA. SSR + Turbo/Stimulus remains confirmed default; both escalation paths requested.

## 2026-10-20 — SSR/SPA boundary
- C37: default SSR + progressive enhancement. SPA only for explicit user demand or demonstrated limitations that reasonable enhancement cannot solve.
- No hypothetical class of rich/cross-screen interactions automatically requires SPA. Linear example is user's design judgment, not a verified browser/product comparison.
- Updated architecture map, recipe-shape escalation rule and confirmation record.
- Next interview: initial Go package layout by responsibility, feature or hybrid. Historical extracted layers do not automatically prescribe new-app structure.

## 2026-10-20 — HappiGrid package-layout authorship
- C38: hybrid Go layout; user confirms writing the HappiGrid layout docs. Re-read README Layering and initial 5fb41bbf architecture sections; hidden .docs matches mainly review/testing references, not another source layout specification.
- Initial research had found the README but left authorship uncertain and failed to extract dedicated layout output. Corrected with 86 and H13, without authenticating unrelated philosophy or later edits wholesale.
- Updated architecture map, Happy Grid findings/evidence and confirmation record. Use authored boundaries/naming as baseline; reconcile new changeset/operations work through implementation experience.

## 2026-10-20 — Layering terminology and exceptions
- C39 clarifies C38: layering is primary, features subgroup within layers; useful inter-feature circular references may require grouping types/code, especially in-memory models. Not a blanket prohibition on such references.
- Reproduced HappiGrid layering in skills/scaffold/references/go-layering.md and linked it from skill entrypoint. Updated 86 and architecture map; source history retained.
- Next possible interview topic: generalize HappiGrid error-handling policy (expected returned errors vs panics at request/job boundaries); unlike layout, this has not yet been explicitly adopted as a general recipe.

## 2026-10-20 — iOS layering and package tradeoffs
- C40: iOS layers and feature/screen subgrouping; large apps may use layer/major-feature/screen. Mostly folders, not one Swift package per layer; optional core/platform boundary.
- Rationale: repeated practical convenience. Package boundaries for build speed and clear/acyclic dependencies when cheap; one module acceptable when package machinery costly. Historical Xcode cost not treated as current benchmark.
- Created ios-layering scaffold guide plus source note 87; linked skill entrypoint and updated historical mobile layout, values and architecture map.
- Go error-handling question remains unanswered. Current next question: iOS model combined with persistence vs pure model/separate persistence; user described history and alternatives, not selected a default.

## 2026-10-20 — Apple internal design research deferred
- C41: current iOS/macOS design choices require modern research first; user explicitly says later, not now. Group approaches and arguments, consider each, then interview.
- Saved 88 and marked 87/ios-layering guide as organizational context, not modern mechanism selection. Preserved native/layering preferences; no Active Record/pure-model default inferred.
- This is a later project step, not a timed reminder/automation. No Apple research started.
- Resume server interview with pending Go error-handling policy, providing full context again.

## 2026-10-21 — Error policy confirmed
- C42 adopts Go error policy and its reason: recover unexpected panics at request/job boundaries, do not deliberately crash whole process; expected failures handled/propagated deliberately by layer.
- General principle also applies to user-action/run-loop boundaries elsewhere; Swift trapping is not the implementation. Apple mechanics still deferred.
- Created error-handling recipe and research note 89, linked skill entrypoint. Pending Go error question resolved.
- Next interview: whether HappiGrid's near-100% coverage target generalizes; context includes algorithm unit tests and mostly whole-app integration tests elsewhere.

## 2026-10-21 — Testing policy
- C43: user accepted HappiGrid testing policy, including near-100% coverage except impractical edge cases; substantial algorithms get unit tests, most other tests exercise whole app and real feature scenarios.
- Created testing recipe and linked skill entrypoint; confirmation record updated. No implementation tests needed for this documentation change.
- Next interview: whether to generalize HappiGrid's isolated, inspectable development harness and shared test fixtures into every scaffold.

## 2026-10-21 — AI development harness
- C44: good AI harness is crucial from day one. Confirmed list: isolated instances, shared fixtures, captured email, DB/log/metrics inspection, real browser flows.
- Created development-harness recipe, linked from entrypoint/testing. No particular tool or runtime implementation selected; Apple-specific mechanics remain deferred.
- Next: development authentication shortcut vs real auth flows; distinguish local fixture-user convenience from auth integration testing.

## 2026-10-21 — Development authentication
- C45: fixture-user login shortcut in development/testing accepted; real signup/login mode retained for auth tests. Not a permission bypass for arbitrary users/environments.
- Updated development-harness recipe and confirmation record.
- Next: fail-fast behavior in isolated AI development vs normal request/job recovery, using HappiGrid's historical development mode as context.

## 2026-10-21 — AI development fail-fast mode
- C46: unexpected failures stop isolated AI development by default; normal recovery selectable for testing error handling. Production keeps boundary recovery.
- Updated harness and error-handling recipes plus confirmation record. Do not turn ordinary expected validation failures into crashes.
- Next: production packaging, using HappiGrid's self-contained binary with embedded assets as the proposed general default; external config/data remain separate.

## 2026-10-21 — Go production packaging
- C47: self-contained executable with embedded templates/assets accepted specifically for Go; external config/secrets/databases, no container requirement.
- Added go-deployment recipe and entrypoint link; confirmed decision recorded. No deployment performed.
- Next: deployment handling for one process holding embedded databases, with a proxy buffering requests during brief restart; ask before selecting a procedure.

## 2026-10-21 — Go deployment sequence
- C48: finish in-flight work → stop old process → start new process, with proxy holding incoming requests during brief restart. User accepted this default.
- Updated Go deployment recipe and confirmation record. Desired behavior only; no proxy implementation selected or deployment tested.
- Next: failed-deploy recovery—automatically restart previous executable when database-compatible, or require manual action.

## 2026-10-21 — Recovery automation must earn trust
- C49: rejected proposed automatic rollback. Infrastructure stays dumb until serious SRE scenario testing; automation can misread failures and worsen them.
- Saved manual recovery default in deployment recipe and rationale in values. No recovery automation implemented; scheduled backups remain a separate unanswered question.
- Next: day-one scheduled off-server backups and a tested restore procedure, with operator-initiated production restores.

## 2026-10-21 — Backup transports and configuration
- C50: scheduled off-server backups and tested restore from day one accepted; manual production restore. S3-compatible storage or SSH/SCP with connection details/key/destination in config.
- Inspected Bubblehouse current implementation, then pre-June-2025 snapshot aaa53bdc6. All 445 historical backups.go lines attributed to Andrey. Recorded historical behavior and limits in 90; newer ZFS/secondary machinery not promoted into defaults.
- Added backups recipe and index links. Config credentials follow existing encrypted JSON/keyring policy. No code execution, backup upload or restore; source/config schema reads only.
- Next: backup-content encryption by app vs relying on storage-provider encryption; key custody and frequency/retention remain open.

## 2026-10-23 — Backup encryption direction
- C51: ideally encrypt before upload; sealer suggested as candidate. Preserved user's uncertainty about mechanism.
- Read upstream README and local sealer HEAD 9af18a9c; streaming compression/encryption and key-ID-based opening fit a candidate backup pipeline. Saved mechanics/limits in 90 and recipe. No audit, integration or restore tests claimed.
- Next: dedicated backup key in existing encrypted config, separate recovery copy and retention of keys for retained backups. This custody proposal is not yet confirmed.

## 2026-10-23 — Backup key custody and rotation
- C52: accepted dedicated key in encrypted config, separate recovery copy in 1Password and old-key retention for retained backups. Added monthly rotation where appropriate, at least annual while starting out.
- Updated recipe, source note and confirmations. Cadence does not select automated rotation or require re-encrypting old backups.
- Next: whether initial scaffold should frequently copy change history off-server between full backups, or make that conditional on project recovery requirements. No cadence or implementation proposed yet.

## 2026-10-23 — WAL deferred to EDB support
- C53: WAL once EDB technically supports it; none now. No parallel application-level replication workaround.
- Updated backup recipe, source note, changeset recovery notes and confirmations. EDB capability not independently audited; user supplied the dependency.
- Next: initial full-backup frequency, with hourly proposed for small early-stage databases and adjustment for snapshot cost/data-loss requirements. Not yet confirmed.

## 2026-10-23 — Initial backup frequency
- C54: hourly full backups accepted for small, early-stage databases; adjust for data-loss requirements and I/O/storage cost.
- Updated backup recipe, source note and confirmations. No hard recovery-point guarantee inferred from schedule alone.
- Next: propose off-server retention of all hourly backups for 24 hours, then one daily for 30 days; project override allowed. Not yet confirmed.

## 2026-10-23 — Backup retention
- C55: all hourly backups for the last week, then daily backups for 60 days, unless storage space becomes a concern. Replaces proposed 24-hour/30-day policy.
- Updated recipe, source note and confirmations. Local staging policy and automatic low-space responses not inferred.
- Next: periodic isolated restore/smoke checks vs manual restore drills initially. Tested restore procedure is already required; ongoing verification mechanism is not selected.

## 2026-10-23 — Optional standby restore loop
- C56: after user requests higher availability through a second server, poll for newer backups roughly every 10 minutes; download/restore new backups to keep standby ready to run.
- Created standby recipe, linked backup/deployment recipes, updated source note and confirmations. Explicit automated standby refresh does not imply automatic failover or production restore.
- Hourly backup cadence unchanged. No second server provisioned or restore performed.
- Next: run restored app with jobs/external effects disabled for readiness checks, or keep it stopped until operator activation.

## 2026-10-23 — Standby launchability
- C57: verify app can launch; for most apps keep it stopped until standby becomes primary.
- Updated standby recipe, source note and confirmations. Verification mechanism left open; no continuous standby execution or mandatory full launch per restore inferred.
- Next: small automatic startup migrations vs large preview-and-execute maintenance operations; startup work must fit the brief-deployment goal. Policy not yet confirmed.

## 2026-10-23 — Startup migration budget
- C58: accepted small automatic startup migrations and large preview-and-execute maintenance operations; specified default 5-second budget per migration.
- Added migrations recipe/source note and linked deployment/research index. Budget is per migration; total startup budget and overrun enforcement unselected. No hard abort inferred.
- Next: mandatory compatibility with previous executable vs best-effort rollback and forward fixes when compatibility complicates code.

## 2026-10-23 — Moved to dedicated scaffold repository
- Canonical root now `/Users/andreyvit/Developer/andreyvit/scaffold`. Moved all 57 research files and 13 scaffold-skill files from env; verified file hashes during move. Preserved relative layout and historical evidence.
- Copied terse unchanged; copied sync and adapted its scope from LifeBase to this repository. Sync runs when requested; migration did not invoke it. Env's original sync/terse copies remain.
- Updated existing global Codex/Claude scaffold links. Added repository-local `.agents/skills` links for scaffold, sync and terse.
- README and AGENTS.md lead to the “Resume here” block at the top of this file. Older interview/scope outlines explicitly point there. Migration-compatibility question is still unanswered; C58 is the latest confirmed decision.
- Verified all relative Markdown targets, skill frontmatter and discovery links. Bundled validator remains unavailable under system Python because PyYAML is missing; manual checks passed. No commit or push performed.
