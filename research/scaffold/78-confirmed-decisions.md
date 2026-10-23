# Confirmed decisions

Source: Andrey's direct response in this chat, 2026-10-18. Overrides earlier hypotheses. Historical-source authorship remains separately labelled.

- **C1 · V1–V13 accepted**, with V7/V12 clarified below. No need to reconfirm the whole list.
- **C2 · Ownership first.** Build it yourself by default; dependencies require a concrete reason. Ownership usually buys control and simplicity. Stronger than the earlier neutral maintenance tradeoff.
- **C3 · Craftsmanship (V14).** Simplicity and elegance matter in themselves. Spend a little extra attention when other costs are comparable. Neglected details make future change a minefield. Concrete costs can justify compromise; no unlimited perfection mandate.
- **C4 · Understand the actual user (V12).** Evaluate wording, screens and workflows through their expectations and attention. Avoid surprise/confusion; assume an error may go unread. Bubblehouse time pressure limits historical execution, not the value.
- **C5 · Privacy — clarified/superseded by C28 for analytics.** Lean private by default; details depend on product requirements and phase. Collect requirements rather than invent a universal policy.
- **C6 · Reliability.** Lean toward no data loss and seconds of downtime hidden from users, potentially by holding connections at a proxy. Establish failure scope and requirements per product; this is an objective, not an implementation guarantee.
- **C7 · Native mobile.** Use native APIs per platform; duplicate implementation effort. AI reduces that cost. Shared-UI frameworks such as React Native are outside the default solution space. Native framework/state/storage choices remain open.

The Steve Jobs analogy explains the value; no exact quotation or factual attribution is needed. The observation about companies moving native is not independently verified and is not used as evidence.

Next: choose supported requirement variants, then architecture decisions. [First scope interview](79-next-scope.md).

## 2026-10-19 · C8 · Optional offline architecture
Support offline editing and multi-device sync in the initial recipe set, but enable only when needed. Prefer simple timestamp-based version selection where losing competing edits is acceptable; otherwise revision-gated client rebasing. Normal server processing/rendering stays the default. [Mechanisms, reasons and open details](80-offline-sync.md).

## 2026-10-19 · C9 · Changes from day one
Choose explicit replayable change objects even online-only, for undo and auditing. Desired model: initial request opens a changeset; handlers add changes; common effect processing iterates until no new effects remain. Prior omission reflects missing framework, not preference; Bubblehouse regret motivates this direction. Atomicity, representation and durable history remain open. [Details](81-changesets.md).

## 2026-10-19 · C10 · Atomic and bulk changes
Most changes are atomic, contained in one transaction. Changesets and large compound changes may span transactions while retaining a single traceable origin. “Bulk changes” is the tentative name for non-atomic changes; they must be easy to code. Supersedes the proposed one-transaction-per-changeset default. Recovery and partial-failure policy remain open. [Details](81-changesets.md).

## 2026-10-19 · C11 · Applied changes vs operations
Refines C10: changeset is atomic within one transaction; several changesets may share a transaction. Most requests use one changeset/transaction. Bulk work spans transactions with a common origin; pending work may be generated lazily or stored separately as a draft. Persistent changes record applied transaction contents and do not resume bulk work. Higher operation tracking can enumerate unfinished procedures and choose manual/automatic resume; avoid dangerous startup avalanches. Validate viability before writes; minimize rollback. Every change must carry enough information for undo.

Operations may be short-lived or long-running. **TODO: gain experience and refine these concepts**, explicitly requested by Andrey. Do not finalize the operations/request taxonomy now. [Details and referenced KVO context](81-changesets.md).

## 2026-10-19 · C12 · Generic inverse changes and shared consequences
Prefer reusable modeling-framework changes: `Increment(+20)` undoes as `Increment(-20)`. Shared rules handle consequences centrally, including actor/permission-sensitive negative-balance notification. Undo uses those rules rather than duplicating them. Specific undo logic is available only where needed; genuinely undo-specific behavior is allowed. [Details](81-changesets.md).

## 2026-10-19 · C13 · Final candidate observation
Intermediate results do not matter. Shared handlers observe the final candidate; their effects may change it and trigger further processing. Usually it matches the eventual final result. Supersedes the assistant's proposed intermediate-transition exception. Exact scheduling and external-effect handling remain open. [Details](81-changesets.md).

## 2026-10-19 · C14 · Simple effect accumulation
Refines C13: observe conditions in the settled state or whenever convenient during processing. Matching conditions may set pending flags or append work. Do not retract processed/scheduled effects if a later handler removes the condition. Prefer the easiest implementation over rare-edge-case reconciliation. This does not settle persistent history compaction. [Details](81-changesets.md).

## 2026-10-19 · C15 · Preserve changes and causal parents
Initially store every change separately with its origin: each change has a parent change ID, forming a causal tree. Do not combine equivalent increments produced by different handlers. Exact root/handler metadata remains unspecified. [Details](81-changesets.md).

## 2026-10-19 · C16 · Ledger snapshots and bounded replay
Ledger is state derived conceptually from changes using the code current when each was processed. Old history need not remain replayable or produce the same result as code evolves. Keep occasional ledger snapshots and support replay since the recovery snapshot. Ledger WAL may narrow required replay to seconds/minutes; generally strive for a week. No permanent compatibility promise; exact replay/deployment mechanics and retention remain open. [Details](81-changesets.md).

## 2026-10-19 · C17 · Simple application, separately derived effects
Replay applies every recorded simple change directly, without business-effect handlers. Complex processing must mutate the ledger only through recorded simple changes. Simple ledger mutations have no complex side effects; effects are derived when adding new changes to a changeset. Exact primitive/API boundary remains open. [Details](81-changesets.md).

## 2026-10-19 · C18 · Initial-handler viability checks
Only the initial request handler may discover a viability problem and reject a request, before writes. Derived effects may not. If an exceptional need appears, solve it then; expected to be extremely rare. Do not build speculative validation/rollback machinery for that hypothetical case. [Details](81-changesets.md).

## 2026-10-19 · C19 · Shared login, company profiles
Default to one login identity with multiple company profiles. All non-login profile fields, including name, are company-specific. Most code should work identically with shared or separate login identities; prepare for multiple simultaneous logins, but choose exposed UI per product. Company policies impose the strictest combined requirements on a shared identity; incompatible requirements can use separate identities. No direct company-admin changes to shared login email or plaintext password handoff; provide first-class account flows. Exact security mechanics remain open. [Decision and reasons](82-identity-and-profiles.md).

## 2026-10-19 · C20 · Defaults and practical convenience
V15: smart defaults matter especially when people will not invest attention in the decision. Strengthen V12: prioritize user convenience, all else equal. Strengthen V8: tester/developer convenience has substantial value and can justify product capability. Shared identity's largely additive flexibility earns its complexity here; this is not a blanket mandate to build speculative features.

## 2026-10-19 · C21 · Personal workspace
Use the same workspace/account ownership model for personal and company data. A personal workspace is a mini company with the individual as owner. **Why: simplicity and internal consistency.** Sharing, conversion and UI exposure remain separate choices. [Details](82-identity-and-profiles.md).

## 2026-10-19 · C22 · Staff/customer separation — deferred by C23
Product decision with a strong default: same login system, separate staff-user and customer records. Expected overlap between customer and staff surfaces can justify combining them. Do not infer separate authentication implementations, shared credentials or customer-data access policy. Rationale beyond the overlap criterion remains open. [Details](82-identity-and-profiles.md).

## 2026-10-19 · C23 · Reopen staff/customer decision later
C22 is no longer an approved default. Andrey wants to reflect and may reverse it entirely; current rationale is insufficient. Strong client-company ownership and deletion of customer records are considerations, not a concluded design. Defer this question; do not implement or prescribe either option meanwhile. [Current status](82-identity-and-profiles.md).

## 2026-10-19 · C24 · Onboarding serves the business
All else equal, favor use before login for convenience. Actual signup timing belongs in the overall monetization/conversion funnel and on a path to measurement and testing. Most products are businesses, not just apps. No unconditional anonymous-first default; strengthens V1. [Details](83-business-and-onboarding.md).

## 2026-10-19 · C25 · Ongoing funnel operation
Clarifies C24: not merely a business decision or a plan to validate later. Cover the funnel with metrics, monitor it and test alternatives as ongoing product work. Exact testing mechanism remains open; do not interpret this as selecting or rejecting concurrent A/B testing. [Details](83-business-and-onboarding.md).

## 2026-10-19 · C26 · Experiments from day one
Include experiments and feature flags in the initial scaffold. Sequential trials must be possible even without parallel testing; concurrent A/B testing is preferred. Reject the assistant's measurement-first/deferred-experiments default. Assignment, metrics and evaluation mechanics remain open. [Details](83-business-and-onboarding.md).

## 2026-10-19 · C27 · Workspace experiments first
Initially assign variants per workspace. Early learning concerns signup and reaching value, not per-user differences inside a workspace. Add per-user assignment as the product matures. Andrey attributes the rationale to Rob Walling; no additional source claims inferred. [Details](83-business-and-onboarding.md).

## 2026-10-19 · C28 · Business requirements before privacy implementation
Order: business measurement goals → necessary metrics/analytics → most private implementation meeting those needs. Usage analytics is almost always required, including free apps where adoption matters. Default to broad usage measurement: hot paths/time spent, time to value, friction/abandonment, conversion, retention/churn, LTV, revenue/expense drivers and useful cohorts. Privacy above metrics requires explicit product-owner choice. Privacy techniques should fit user-base size; no premature sophistication. Supersedes the assistant's privacy-led explicit-events-only default and clarifies C5. [Details](83-business-and-onboarding.md).

## 2026-10-20 · C29 · Session replay is a separate feature
Valuable especially early; capture, storage and playback make it a separate feature with its own file. Watching requires a dedicated security permission. Created [recipe](../../skills/scaffold/references/session-replay.md). No library or universal capture rollout selected.

## 2026-10-20 · C30 · In-app analytics, separate database
Keep analytics and experiments inside each app initially for simplicity. Analytics database must be separate from the main application database. No separate server, database engine or experiment-configuration storage decision implied. [Details](83-business-and-onboarding.md).

## 2026-10-20 · C31 · Small analytics gaps are acceptable
No strict analytics delivery guarantee required. Illustrative disk flush intervals: 5–60 seconds depending on load; roughly 60 seconds likely suits light load/early stages. 300 seconds is pushing it but acceptable for barely used/pre-MVP apps; 3600 seconds undesirable. Examples, not fixed implementation rules. Supersedes the assistant's proposed mandatory durable queue for business-outcome analytics; business records themselves remain distinct. [Details](83-business-and-onboarding.md).

## 2026-10-20 · C32 · Conditional 60-second default
Clarifies C31: if accumulating and flushing periodically, or throttling writes, use 60 seconds by default. Tune for load. These approaches are not themselves mandated; the default is conditional, not merely illustrative. [Details](83-business-and-onboarding.md).

## 2026-10-20 · C33 · Raw analytics first; revisit at scale
Retain raw events initially because requirements are uncertain and reprocessing preserves flexibility. Sequential append-only journals are acceptable; use per-tenant journals in B2B, compression/encryption, external archiving and local removal of archived files. For large volumes, devise efficient binary payloads avoiding repeated page paths/user agents/etc. At higher load, explicitly discuss storage costs and processing feasibility as business/product decisions; retained data may need a different representation/access strategy for quick aggregation. External retention and exact encoding remain open. [Details](85-analytics-journals.md).

## 2026-10-20 · C34 · Finite analytics retention
Always set a finite raw-event retention window; default 24 months, including external archives. Explicit overrides such as 60 months are fine. Reasons: rapidly changing early products make old data less useful; a stated cap is better than indefinite retention for privacy-policy clarity and vendor due diligence. Rejects assistant's indefinite-early-history suggestion. Aggregate retention remains unspecified. [Details](85-analytics-journals.md).

## 2026-10-20 · C35 · Strong one-process default
Run web requests, background jobs and analytics ingestion in one process until a very strong reason justifies splitting. Reasons: simplicity, efficiency, and local embedded databases often being limited to a single process. Clear internal components and separate analytics storage do not require separate processes. No particular database chosen by this decision. [Architecture map](72-architecture-decisions.md).

## 2026-10-20 · C36 · EDB/Bolt for Go servers
Default primary business storage to EDB/Bolt; alternatives require a concrete reason. Andrey and Bubblehouse will keep investing heavily in EDB. This does not select analytics storage or claim the experimental modeling/change framework is production-complete. [Architecture map](72-architecture-decisions.md).

## 2026-10-20 · C37 · SSR until demonstrated limits
Unless the user explicitly demands otherwise, start with SSR and enrich progressively. Switch to SPA only when actual SSR limitations cause problems that progressive enhancement cannot reasonably solve. Reject the assistant's proposed cross-screen-state threshold as sufficient justification. Andrey's Linear comparison illustrates this judgment; Safari behavior and an alternative implementation were not independently evaluated. [Architecture map](72-architecture-decisions.md).

## 2026-10-20 · C38 · Hybrid Go layout; authored source recovered
Choose hybrid package layout. Andrey confirms authorship of HappiGrid package-layout documentation; use that source instead of inventing a generic layout. Responsibility layers contain feature-specific packages, with model/business/integration/wiring boundaries. Later source edits and new change-framework placement retain explicit limits. [Recovered baseline](86-go-package-layout.md).

## 2026-10-20 · C39 · Layering first, flexible grouping within layers
Clarifies C38: call it layering and reproduce HappiGrid's guide. Layers express responsibilities and dependency constraints; experience favors grouping similar code. Within layers, prefer feature packages to avoid huge/tangled packages, but keep inter-feature code/types together when useful circular references justify it. Persistent models/utilities can often separate; interconnected in-memory representations may need one package. Do not force feature separation or equate all circular references with defects. [Guide](../../skills/scaffold/references/go-layering.md).

## 2026-10-20 · C40 · iOS layering and proportional packaging
Use application, cross-cutting, services (non-visual), screens/subcomponents, reusable components and model layers; persistence may be combined with model or separate. Group within layers by feature/screen; large apps may add major-feature level. Usually folders within one compilation module, not many Swift packages; core/platform separation is possible. Reason: proven convenience. Package boundaries earn their cost through build efficiency and dependency clarity; if tooling makes them costly, one module is fine. Current Xcode costs and model/persistence default remain open. [Details](87-ios-layering.md).

## 2026-10-20 · C41 · Defer Apple internal design to research
Do not ask Andrey to choose modern iOS/macOS internals from outdated experience. Later, gather modern recommendations and arguments, group by approach, and evaluate each with him. No research now. Native direction and organizational preferences remain context; model/persistence and other mechanisms are unselected. [Research step](88-apple-design-research-plan.md).

## 2026-10-21 · C42 · Deliberate expected errors, generic unexpected failures
Adopt HappiGrid's Go default: expected errors returned, unexpected/internal failures panic, recover/log at request/job boundaries and fail that operation; no automatic job retry after panic. General principle: carefully handle/propagate expected errors layer by layer; propagate unexpected failures to a suitable top wrapper and handle generically without crashing the entire process/app. Swift must use a different mechanism; Apple research remains deferred. [Details](89-error-handling.md).

## 2026-10-21 · C43 · HappiGrid testing default
Adopt the proposed policy: unit tests for substantial algorithmic code, mostly whole-app integration tests elsewhere, feature/use-scenario coverage and near-100% coverage except genuinely impractical edge cases. Source: direct “Yes!” to adopting that policy. [Recipe](../../skills/scaffold/references/testing.md).

## 2026-10-21 · C44 · AI harness from day one
Crucial to include strong AI development support from the start. Adopt isolated concurrent instances, fixtures shared with integration tests, captured outgoing emails, easy database/log/metrics inspection and browser access for real web flows. [Recipe](../../skills/scaffold/references/development-harness.md). Auth shortcuts and failure-mode overrides were not part of the accepted list and remain open.

## 2026-10-21 · C45 · Fixture-user authentication shortcut
Provide direct access as a chosen fixture user in development/testing, without completing login. Also support real signup/login flows for authentication tests. Keep the shortcut confined to development/testing. Source: direct acceptance of this proposed default. [Recipe](../../skills/scaffold/references/development-harness.md).

## 2026-10-21 · C46 · Fail fast in AI development
Isolated AI development stops the app on unexpected failures by default, making failures hard to overlook. Normal request/job recovery remains available for failure-handling tests; production recovery policy is unchanged. Expected application/validation errors are not promoted to crashes. [Harness](../../skills/scaffold/references/development-harness.md).

## 2026-10-21 · C47 · Self-contained Go executable
Go production defaults to one executable with templates/frontend assets embedded; configuration, secrets and databases external. No container runtime required. Explicitly scoped to Go. Supervision, restart/deployment and standby mechanics remain unselected. [Recipe](../../skills/scaffold/references/go-deployment.md).

## 2026-10-21 · C48 · Drain, stop, start behind a buffering proxy
Go deployment default: finish in-flight work, stop old process, start new process; proxy briefly holds incoming requests. Keep one process owning the embedded database and target seconds of downtime hidden from users. Confirms the proposed sequence; proxy implementation and failed-deploy recovery remain open. [Recipe](../../skills/scaffold/references/go-deployment.md).

## 2026-10-21 · C49 · Dumb infrastructure before tested recovery automation
Reject automatic failed-deploy rollback, even when the previous executable appears database-compatible. Keep infrastructure dumb until serious focus on testing SRE scenarios: undertested automation may misread the situation and do more harm than good. Default to operator-directed recovery. No blanket ban on scheduled tasks or backups inferred. [Recipe](../../skills/scaffold/references/go-deployment.md).

## 2026-10-21 · C50 · Scheduled backups, manual production restore
Include scheduled off-server backups and a tested restore procedure from day one; production restore is operator-initiated. Support S3-compatible storage or SSH uploads, with S3 details or SSH key and SCP destination address/path in config. Use Bubblehouse implementation as reference. Schedule, retention and backup-content encryption remain unselected. [Source details](90-backups.md) · [Recipe](../../skills/scaffold/references/backups.md).

## 2026-10-23 · C51 · Prefer backup encryption; sealer candidate
Ideally encrypt backups before upload. Andrey is unsure of implementation and suggests his sealer library for writing backups. Record preference and candidate, not a finalized mechanism or key-custody policy. [Inspection](90-backups.md) · [Recipe](../../skills/scaffold/references/backups.md).

## 2026-10-23 · C52 · Backup key custody and rotation
Dedicated backup key in encrypted config, recovery copy in 1Password, old keys retained while their backups exist. Rotate monthly where appropriate, at least annually while starting out. No automatic rotation mechanism selected. [Details](90-backups.md) · [Recipe](../../skills/scaffold/references/backups.md).

## 2026-10-23 · C53 · WAL waits for EDB
Add WAL once EDB technically supports it; none for now. Use snapshot backups without a separate interim change-history replication system. Future WAL transport and recovery details remain open. [Details](90-backups.md).

## 2026-10-23 · C54 · Hourly full backups initially
Default to hourly full backups for small, early-stage databases; adjust to project data-loss requirements and I/O/storage cost. Retention remains unselected. [Details](90-backups.md) · [Recipe](../../skills/scaffold/references/backups.md).

## 2026-10-23 · C55 · Generous backup retention until storage matters
Off-server: retain all hourly backups for the last week, then daily backups for 60 days, unless storage space becomes a concern. Replaces assistant's proposed 24-hour/30-day policy. No automatic space-driven retention reduction selected. [Details](90-backups.md) · [Recipe](../../skills/scaffold/references/backups.md).

## 2026-10-23 · C56 · Second server continuously restores newer backups
When the user requests higher availability via hot standby, have the second server poll for newer backups about every 10 minutes, download and restore them, ready to run. Automatic standby refresh is allowed; production recovery/failover is not thereby automated. App execution/readiness checks remain open. [Recipe](../../skills/scaffold/references/standby.md).

## 2026-10-23 · C57 · Verify launchability; keep standby app stopped
Verify that the app can launch against restored data, but for most apps keep it stopped until standby becomes primary. Exact verification mechanism remains open; continuous execution in standby is not the default. [Recipe](../../skills/scaffold/references/standby.md).

## 2026-10-23 · C58 · Startup migration budget
Small migrations run automatically at startup; large rewrites use preview-and-execute maintenance operations. Default budget is 5 seconds per migration. No total startup limit or forced-abort mechanism selected. [Details](91-migrations.md) · [Recipe](../../skills/scaffold/references/migrations.md).

## 2026-10-23 · C59 · Best-effort migration compatibility until MVP review
Compatibility with the previous executable is ultimately a business decision. Start with a strong default of best-effort rollback compatibility; reevaluate once MVP is reached. This milestone requires review, not an automatic switch to mandatory compatibility. [Details](91-migrations.md) · [Recipe](../../skills/scaffold/references/migrations.md).

## 2026-10-23 · C60 · Migration overruns finish safely
Allow startup migrations exceeding the 5-second budget to finish safely and log the overrun. Enforce the budget through testing rather than a runtime cutoff. User accepted this proposal; no total startup limit selected. [Details](91-migrations.md) · [Recipe](../../skills/scaffold/references/migrations.md).

## 2026-10-23 · C61 · Main-database job queue; skip obvious choices
Job queue lives in the main database by default. Saving scheduled jobs in the same transaction as the originating business change is the obvious choice when technically feasible. Interview real design tradeoffs and values, not consequences already determined by the architecture. [Method](77-research-method.md) · [Recipe](../../skills/scaffold/references/jobs.md).

## 2026-10-23 · C62 · Superstaff access and meaningful access auditing
Superstaff may access client data. Keep a customer-data access journal for any user: opening details counts; seeing a name in a list does not. Record bulk actions such as exports as bulk operations, without enumerating every customer touched by default. [Details](92-customer-data-access.md) · [Recipe](../../skills/scaffold/references/customer-data-access.md).

## 2026-10-23 · C63 · Roles in the foundation; customization UI optional
Code includes permissions and roles from the start, with default roles. Offer role-customization UI as a separate feature and implement it only when authorized for the product. Supersedes the assistant's fixed-vs-custom-roles framing: internal capability and exposed product UI are separate decisions. [Details](73-accounts-decisions.md) · [Recipe](../../skills/scaffold/references/permissions.md).

## 2026-10-23 · C64 · Stimulus proven; consider Svelte before React
Stimulus works well as a connection point; Andrey has not needed React himself. For richer client behavior, consider Svelte before React; Andrey confirmed the initially forgotten name. This selects an evaluation preference, not a mandatory dependency. Reasons and qualifications recorded in C65. [Details](93-rich-web-pages.md) · [Recipe](../../skills/scaffold/references/web-rendering.md).

## 2026-10-23 · C65 · Svelte rationale: payload, simplicity and low churn
Prefer less runtime JavaScript and avoid unnecessary loading delay even when not business-critical if a better approach exists. Simplicity and low churn are primary values. Limited Svelte experience suggests a pragmatic fit; contrary evidence would change that judgment. Andrey dislikes React's direction since hooks and the overengineering he sees especially in its ecosystem. If JSX already calls for compilation, he would rather consider Svelte compiling to efficient JavaScript. These are reasons for the preference, not benchmark results or unconditional Svelte adoption. [Details](93-rich-web-pages.md) · [Values](70-values.md).

## 2026-10-23 · C66 · Plain JavaScript and minimal bundling; TypeScript last resort
Strongly prefer plain JavaScript and the simplest bundling. Previous owned bundler used JSON dependency frontmatter and concatenation with optional wrapping. TypeScript needs compelling benefits over its perceived complexity/build cost; last use was years ago. Dynamic typing is acceptable with integration tests; excellent frontend coverage matters more. Agentic work could change the balance, but no evidence yet. Reconsider excessive client code architecturally; genuinely JavaScript-heavy projects may eventually grow into a justified TS transition. [Details](94-frontend-tooling.md) · [Recipe](../../skills/scaffold/references/frontend-tooling.md).

## 2026-10-23 · C67 · Tailwind remains the CSS starting point
Tailwind remains the preferred CSS starting point and useful shared styling vocabulary. User confirmed the earlier preference; no specific version, custom subset or build pipeline selected. [Details](94-frontend-tooling.md) · [Recipe](../../skills/scaffold/references/frontend-tooling.md).

## 2026-10-23 · C68 · Templating needs strategic replacement
No fully satisfactory templating solution yet. Good component support is required. Minicomponents remains the best hack so far, but template-rewriting scoping limitations led Andrey to largely stop using it in a large project. He plans an owned templating language with components; treat this as separate strategic work, not a selected or implemented engine. [Details](95-server-templating.md) · [Recipe](../../skills/scaffold/references/web-rendering.md).

## 2026-10-23 · C69 · Project-local first; deliberate library extraction
Default to a separate package/unit inside the project. Entirely domain-independent, reusable, non-project-specific code benefits from separation to keep boundary and scope crystal clear; a templating language is an example. Normally offer extraction after production proof and API stability over a few months of use. Every extraction is an explicit decision requiring user authorization. [Details](96-library-boundaries.md) · [Recipe](../../skills/scaffold/references/library-boundaries.md).

## 2026-10-23 · C70 · Library compatibility depends on consumers
Library API compatibility decisions depend on who uses the library and must be vetted by the user. No blanket preference for coordinated breaking changes or preserving old APIs. [Details](96-library-boundaries.md) · [Recipe](../../skills/scaffold/references/library-boundaries.md).

## 2026-10-23 · C71 · Email codes by default; passkeys from the start
Where sending email is possible, default initial login to email codes for security/ease of access. Code required for cross-device use; accompanying link optional. Require macOS/iOS recognition and autofill. Offer passkeys from the start with smooth “passkey or email” UX. Other methods are product decisions. Passkey-before-email capability was researched separately; enrollment/recovery details are not yet selected. [Details](97-login-methods.md) · [Recipe](../../skills/scaffold/references/login.md).

## 2026-10-23 · C72 · Enroll passkey after email login; retain email access
Signup/login flow: verify email code, automatically offer passkey creation with the normal confirmation prompt, then allow either passkey or email-code login. User clarified that “automatic” means offering enrollment without waiting for a request; confirmation is welcome and silent creation is not required. Email login stays available. [Details](97-login-methods.md) · [Recipe](../../skills/scaffold/references/login.md).

## 2026-10-23 · C73 · S3-compatible uploads, B2 preferred, app-owned URLs
Store uploads in S3-compatible storage; recommend Backblaze B2 over Amazon S3. Keep the provider internal and route file URLs through the app by default, using a separate serving domain when the content warrants it. Presigned redirects are an option. Local disk is only a cache of stored objects, useful when the app serves files itself. [Details](98-upload-storage.md) · [Recipe](../../skills/scaffold/references/uploads.md).

## 2026-10-23 · C74 · Upload through server; direct media uploads need finalization
Default to uploads through the app server and vet raw content before durable storage. Consider direct uploads for frequent large media; require a final server call/equivalent, a job to recover missed completion calls when objects actually arrived, and post-upload content vetting. Avoid the completion-event infrastructure burden experienced with SNS. [Details](98-upload-storage.md) · [Recipe](../../skills/scaffold/references/uploads.md).

## 2026-10-23 · C75 · Metrics, analytics, spans and logs from the start
Metrics for everything are required; new projects need metrics, analytics, spans and good logging from day one. Andrey plans anomaly monitoring on selected metrics. Bubblehouse's setup is still rudimentary; he requests guidance on the solution space. No stack or anomaly algorithm selected. [Details and proposals](99-observability.md) · [Recipe](../../skills/scaffold/references/observability.md).

## 2026-10-23 · C76 · Grafana Cloud costly and slow; seek lightweight observability
BH runs Grafana Cloud. Andrey reports high cost and slowness that makes it a last resort during investigations, though the team still uses it then. He would love a lightweight project covering the required observability capabilities. No replacement or build decision selected. [Experience and trace-format explanation](99-observability.md).

## 2026-10-23 · C77 · Initial Protobuf/OTLP rejection; clarified by C78
Initially reject Protobuf and OTLP for the observability design. Seek a lightweight integrated project in plain Go running on one server with little operational fuss; Andrey expects an owned alternative may be needed. No concrete format, store or project selected. Earlier assistant OTLP recommendations are superseded. [Candidate research](100-lightweight-inspectability.md).

## 2026-10-23 · C78 · Handwritten OTLP output may avoid the rejected dependency
Clarifies C77: producing OTLP is acceptable in principle if the relevant binary fields are hardcoded in a lightweight encoder without a Protobuf dependency. This reopens wire compatibility, not adoption of a Protobuf library/toolchain, OpenTelemetry SDK or backend. No implementation selected. [Details](100-lightweight-inspectability.md).

## 2026-10-23 · C79 · Save inspectability options; evaluate later, including Jaeger
Record the discussed alternatives briefly for later hands-on trials. Include Jaeger; no backend selected and no trials requested now. [Consolidated list](100-lightweight-inspectability.md#try-later--confirmed-c79--2026-10-23).

## 2026-10-23 · C80 · Prefer direct telemetry files and indexes; Prometheus stance is soft
Prefer a simpler default than Prometheus/PromQL, which Andrey views as overengineering for the expected non-distributed system; BH currently uses Prometheus and justified exceptions remain possible. Write directly to rotated files/journals, possibly compressed/encrypted, and index for fast access. Exact tools/mechanics remain open; user requests critique, not immediate implementation. [Assessment](102-file-based-observability.md).

## 2026-10-23 · C81 · Defer observability details until personal experiments
Save all observability, anomaly-detection and file/index options and table the topic. Andrey needs to experiment himself before making more detailed recommendations. Preserve requirements and qualified preferences; no backend, format, algorithm or implementation selected. [Tools](100-lightweight-inspectability.md) · [Anomaly detection](101-lightweight-anomaly-detection.md) · [Files/indexes and metric output](102-file-based-observability.md).

## 2026-10-23 · C82 · Postmark or Mailchimp; email is a job
Use Postmark or Mailchimp for transactional email. Sending an email should be a job. No ranking between providers or new retry/delivery guarantee selected. [Details](103-transactional-email.md) · [Recipe](../../skills/scaffold/references/email.md).
