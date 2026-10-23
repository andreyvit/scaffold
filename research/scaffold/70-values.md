# Confirmed values

Confirmed by Andrey in this chat, 2026-10-18; V7/V12 strengthened and V14 added. Current confirmation establishes the preference, not retrospective authorship of old drafts. **Statement** = source wording; **inference** = code pattern.

| ID | Value | Historical evidence | Limits / clarification |
|---|---|---|---|
| V1 | Serve a real user or business outcome. | Statement: [U8b–d, U10](51-ulysses.md), [SundaySchool](62-more-writing.md); original user: [H1](10-happy-grid.md). | Not speed at any cost or vanity metrics. |
| V2 | Keep future effort proportional to the change. | Statement: U1, U7; candidate prompt: [N1, N6](41-heynote.md). | Not anticipation of every future feature. |
| V3 | Make correctness understandable locally. | Statement: U2–3; original user: H2–3; candidate: N1–4. | Common enforcement is allowed; files need not be independent. |
| V4 | Abstractions must earn their cost. | Statement: U3–4; original user: H2, H4; [library exceptions](31-small-libraries.md). | Not a ban on abstraction, dependencies, code generation or frameworks. |
| V5 | Make state, ownership and failure explicit. | Statement: U1, U5; original user: H8–9; inference: [mobile state](22-bubblehouse-mobile.md), [cached data](35-sarekon.md). | Does not require event sourcing, reducers or offline writes. |
| V6 | Keep the running system inspectable. | Original user: H5–6; statement: [LiveReload](36-livereload-and-writing.md); inference: [B7–10](21-bubblehouse.md). | Not indiscriminate logging, private data exposure or unlimited labels. |
| V7 | Build and own it by default; take a dependency for a concrete reason. | Statement: U6; [libraries](31-small-libraries.md), [cost tradeoffs](60-other-code.md). | Ownership usually buys control and simplicity. Specialist knowledge, ongoing upkeep or real cost can justify a dependency. |
| V8 | Fast feedback and convenient testing sustain quality and pace. | Statement: LiveReload, U7, U9b; candidate: N7. | Developer/tester convenience has substantial value and can justify product capability. Does not justify bypassing correctness or unmeasured optimization. |
| V9 | Security should be evident in the design. | Candidate: N4; historical statement: [B5–6](21-bubblehouse.md); inference: B9. | Historical gaps are not endorsed; low friction does not always win. |
| V10 | Prove real behavior; make failures recoverable. | Original user: H5; statement: U9; inference: B4, B8, B10–11. | Scaffold testing now targets near-100% coverage except impractical edge cases (C43), alongside real scenarios. Telemetry loss policies do not apply to user data. |
| V11 | Fit process and architecture to the team and risk. | Statement: U8, U11; [planning exceptions](62-more-writing.md); [EDB](31-small-libraries.md). | Not a ban on planning, reviews, documentation or managed services. |
| V12 | Make the product understandable and convenient for its actual users. | Original user: H1; statement: U10; [workflow examples](64-craft-and-ux.md). | Prefer user convenience, all else equal. Know their expectations, attention and likely reactions. Prevent confusion in workflows, screens and wording; do not rely on an error message being read. |
| V13 | Understand what the machine actually pays for. | Candidate: N1; statement: [hash benchmarks and EDB](31-small-libraries.md); inference: [Bubblehouse storage](21-bubblehouse.md). | Not blanket micro-optimization; measure total cost. |
| V14 | Prefer simplicity and elegance; think through the details. | Confirmed explanation: this chat; [examples and limits](64-craft-and-ux.md). | Spend modest extra attention when other costs are comparable. Compromise for concrete cost; avoid sloppy details that turn future changes into a minefield. |

Current skill guidance: [values](../../skills/scaffold/references/values.md). The evidence and qualifications below remain the source record.

## Defaults and convenience — confirmed 2026-10-19
**V15: Choose smart defaults, especially for decisions users will not spend attention on.** Product-specific does not mean recommendation-free. Explain the value, cost and exception.

Account reasoning explicitly strengthens V8/V12: prioritize convenience for actual users and testers, including the developer as an active tester. Shared login with company profiles earns its complexity through convenience, testing and largely additive flexibility. [Full reasoning](82-identity-and-profiles.md).

## Craftsmanship
Simplicity is a quality goal, not only a limit on abstraction. When choices have comparable runtime, memory and operating cost, prefer the simplest, most coherent design—even in a detail that does not matter yet. A little extra thought is worthwhile: neglected details can become expensive obstacles when the product grows. This is care, not unlimited polishing.

## Business viability — confirmed 2026-10-19
V1 includes the business, not just the app. Customer convenience is preferred all else equal; onboarding must fit the monetization/conversion funnel, with ongoing metrics, monitoring and testing of alternatives as part of operating the product. Do not turn a convenience preference into an unconditional signup rule. [Details](83-business-and-onboarding.md).

## Packaging follows practical cost — confirmed 2026-10-20
Layering does not require a package per layer. Use cheap package boundaries for build efficiency and explicit dependencies; accept folders in one compilation module where packaging adds too much fuss. Historical convenience informs the layout; verify current toolchain costs. [iOS reasoning](87-ios-layering.md).

## AI development support — confirmed 2026-10-21
Build a good harness from day one. Isolated instances, shared fixtures and inspectable runtime state are essential development capabilities, not optional polish. [Recipe](../../skills/scaffold/references/development-harness.md).

## Operational automation — confirmed 2026-10-21
Keep infrastructure dumb until serious SRE scenario testing earns automated recovery. Recovery logic can misread a failure and cause more harm than the original problem. Manual failed-deploy recovery is the default. Strengthens V10/V11: recoverability does not imply automatic intervention. [C49](78-confirmed-decisions.md).

## Simplicity, low churn and avoidable costs — confirmed C65 · 2026-10-23
**V16: Value low churn alongside simplicity.** Andrey calls these primary values when judging a framework and its ecosystem. Prefer pragmatic tools without recurring complexity or unnecessary changes. His Svelte impression is provisional; change the tool judgment when evidence contradicts it.

V13/V14 also apply to modest costs: an avoidable loading delay need not be business-critical to prefer a better approach. When already accepting compilation, consider using it to produce efficient runtime code. This does not establish an unlimited optimization budget or a universal preference for extra build machinery. [Full frontend rationale](93-rich-web-pages.md).

## Dynamic languages and tool cost — confirmed C66 · 2026-10-23
Dynamic typing is acceptable with strong integration coverage; Andrey has long experience with JavaScript and Ruby. Plain JavaScript and minimal bundling are preferred. Frontend test coverage matters more than static typing. Additional language/build machinery needs compelling evidence, including in agentic work; future evidence may change the balance. A genuinely JS-heavy codebase can eventually justify TypeScript. Strengthens V4/V8/V10/V14 without prescribing dynamic typing for every platform. [Details](94-frontend-tooling.md).

## Library boundaries mature through use — confirmed C69 · 2026-10-23
V4/V7 favor a clear scope, not automatic extraction. Build a separate package/unit inside the project by default. Entirely domain-independent reusable code benefits from separation; offer extraction after production proof and a few months of API stability. Each extraction needs explicit user authorization. [Details](96-library-boundaries.md).

## Count coordination costs — confirmed C74 · 2026-10-23
The upload example strengthens V4/V11/V13: avoiding server bandwidth is not automatically simpler when it adds completion events, reconciliation and later content checks. Default to the server path; frequent large media may justify direct upload with explicit finalization and a reconciliation job. [Details](98-upload-storage.md).

## Working decision rule — proposed
State the need → choose the smallest sufficient design → name its limits → check failure and operation → preserve the reason.

When values conflict, ask about the concrete cost or risk. Do not invent a permanent ranking from one incident.

## Confirmed defaults
- **Privacy within business requirements:** establish business measurement goals, derive required analytics, then choose the most private implementation that meets them. Broad usage analytics is normally required, including for free products whose adoption matters. Prioritizing privacy above metrics requires an explicit product-owner decision. Scale privacy techniques to the user base. [Goals and reasoning](83-business-and-onboarding.md).
- **Reliability:** aim for no data loss and only seconds of downtime, hidden from users where possible. Holding connections at a proxy is a desired option to evaluate, not proof of durability or recovery. Failure scope, product phase and budget still need explicit requirements.
- **Mobile:** native APIs and UI on each platform; accept duplicated implementation. AI changes the cost tradeoff. Do not reopen React Native/shared-UI selection by default. Exact native frameworks and state/storage choices remain research work.

## Still project-specific
Privacy detail, retention, recovery objectives, failure scenarios, support access and product phase. These are requirements to collect, not unresolved universal values.

Exact pointers: [Happy Grid](10-happy-grid-evidence.md), [Bubblehouse](23-bubblehouse-evidence.md), [Heynote](42-heynote-evidence.md), [Ulysses](53-ulysses-sources.tsv). [Confirmation and reasoning](78-confirmed-decisions.md).

Later research adds two candidates, not yet additional confirmed values: [breadth and mechanism-level judgment](65-hiring.md), and [long useful life without needless user relearning](66-lifebase-expanded.md).
