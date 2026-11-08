# Great mobile SDKs for existing SaaS APIs: iOS and Android

Research date: **2026-11-08**. Public documentation, source/manifests, releases, incident reports, research papers and one published UI comparison inspected. No SDK build, benchmark, device audit or private financial audit performed.

**Starting recommendation:** build a small Swift and Kotlin core, share contract fixtures, and publish matching samples and support policies. Add generation, shared code, UI or offline machinery when the service's workflows justify their ongoing cost. These are research recommendations, not confirmed scaffold defaults.

Reading guide: [quality](#1-what-makes-an-api-sdk-great) · [runtime contracts](#2-reliability-security-and-data-semantics) · [native integration](#3-native-apis-and-platform-integration) · [compatibility](#4-compatibility-and-delivery) · [generation](#5-architecture-code-generation-and-shared-code) · [case studies](#6-sdk-case-studies-strengths-and-limits) · [DX and economics](#7-developer-experience-adoption-and-economics) · [failures](#8-failures-migration-and-service-retirement) · [practical details](#9-practical-integration-reference) · [optional UI](#10-optional-ui-design-directions-and-resources) · [tools](#11-named-tools-and-libraries) · [avoid/migrate](#12-named-choices-to-avoid-migrate-or-constrain) · [build order](#13-prioritized-build-guidance) · [release tests](#14-release-test-protocol-and-performance-budgets) · [sources](#15-sources-evidence-and-scope-limits).

## Scope

Native client libraries for an existing SaaS API, consumed by other developers in their iOS and Android apps. Includes optional ready-made UI; does not assume every SDK needs UI, offline sync, analytics, payments or background workers. SDK adoption and integration quality replace app-store downloads as primary outcomes. Full consumer-app visual surveys and app pricing are outside this component scope.

Related guidance: [iOS apps](playbook-ios-apps.md), [Android apps](playbook-android-apps.md), [API recipe](apis.md), [iOS layering](ios-layering.md). Existing RPC/JSON preference remains situational; this report accommodates existing REST, RPC and GraphQL APIs. Findings are research recommendations, not newly confirmed scaffold decisions.

## 1. What makes an API SDK great

**A great SDK makes a useful integration easy to ship and safe to keep.** It expresses the service in the host language, survives ordinary mobile failures, exposes enough state to recover, and earns its dependency cost. Endpoint coverage alone is a weak quality measure.

Two customers matter: the developer integrating the library and the person using the resulting app. A short quickstart that later causes account leakage, duplicate purchases or a frozen screen fails both. Developer delight comes from predictable names, useful compiler feedback, readable errors and small upgrades. Customer value comes from correct work, responsive UI and recoverable interruptions. These are design goals, not measured revenue claims.

| Meaning of great | SDK-specific evidence to seek | Misleading substitute |
|---|---|---|
| Developer love | Repeat use; recommendations with reasons; successful debugging; willingness to upgrade | Stars, downloads or attractive docs alone |
| Problem solving | A real workflow completed with less integration code and fewer failure paths | A generated method for every endpoint |
| Adoption and retention | Production integrations; active compatible versions; sustained API use | CI package downloads or anonymous installs |
| Revenue | Qualified integrations reaching paid use; expansion attributable to the service | Assuming every SDK call adds revenue |
| Viability | Maintenance/support costs fit service margins and staffing | Launch speed without ownership |
| Maintainability | Small public surface; shared contract tests; reproducible releases | Identical source code across languages at any cost |
| Platform recognition | Host apps pass review, perform well and respect privacy | Expecting a headless library to win app-store featuring |

### Select the product boundary before the implementation

| SDK shape | Appropriate when | Extra obligations |
|---|---|---|
| Typed API client | Existing endpoints already solve the task | Transport, auth boundary, errors, cancellation, wire compatibility |
| Workflow SDK | Several calls and local states form one business operation | Recovery, idempotency, progress, authoritative terminal state |
| Stateful/realtime client | Subscriptions, local data or device sessions are core value | Connection lifecycle, replay gaps, identity isolation, storage bounds |
| UI kit | A reusable task has costly domain UX, such as payment or identity verification | Host navigation, accessibility, localization, appearance, lifecycle |
| Full synchronization engine | Users must read/write offline and reconcile later | Durable queue, conflict model, migrations, deletion, recovery, observability |

Do not add the last three to a simple client merely because another SDK has them. Conversely, a payments or chat SDK that only wraps HTTP may leave most of the difficult integration work to customers. Keep these capabilities separable where customers have different needs.

### Audit the existing API first

**Mobile-safe authorization is a prerequisite.** Stripe distinguishes publishable keys from privileged keys; restricted keys remain secret. A server API authenticated by one account-wide secret cannot become safe by compiling that secret into Swift or Kotlin. Add user-scoped authorization, short-lived delegated access or a customer-backend step before exposing privileged operations. [Stripe key types](https://docs.stripe.com/keys).

**Compatibility has several dimensions.** Google separates source, wire and semantic compatibility. An optional field can still break generated names; new response enum values can break exhaustive clients; pagination added after launch can silently truncate old callers. Keep old released clients in the server compatibility test matrix. These lessons apply to RPC as well as REST; Google's detailed AIP conventions are not mandatory for an unrelated API. [AIP-180](https://google.aip.dev/180).

**A protocol cannot supply missing business guarantees.** Inventory per-operation authorization, mutation semantics, idempotency, pagination, maximum payloads, errors and version support. If the API cannot tell whether a timed-out order was accepted, the SDK must expose uncertainty or reconcile through an operation ID. It cannot manufacture exactly-once execution.

## 2. Reliability, security and data semantics

The following are research-derived design recommendations. Specific service behavior is cited separately. They do not select a new scaffold architecture.

### Authentication and identity

For OAuth, use the system authorization session/browser and authorization code with PKCE. Native apps are public clients; an embedded client secret does not establish confidentiality. Validate redirect/session binding and delegate protocol details to a maintained OAuth implementation where feasible. Do not embed a login WebView merely to match the app's colors. [RFC 8252, October 2017](https://www.rfc-editor.org/rfc/rfc8252).

Refresh tokens need a real lifecycle. OAuth's current security BCP requires public-client refresh tokens to be sender-constrained or rotated. **Derived SDK design:** coordinate concurrent refreshes, persist replacement credentials atomically, distinguish transient refresh failure from revoked credentials, and prevent an old refresh result from restoring a logged-out session. Rotation and replay policies belong to the server/client contract. [RFC 9700, January 2025](https://www.rfc-editor.org/rfc/rfc9700).

Treat login, logout, tenant changes and environment changes as state transitions. Namespace credentials, cache entries, pending mutations, streams and diagnostic context by their true identity. When identity changes, invalidate or fence work started under the old identity. Keep local logout, server token revocation, cache deletion and account deletion distinct. Applications choose whether queued work is discarded, held or completed; do not silently send it as the next user.

Keep storage injectable when the host owns authentication. If the SDK owns tokens, use platform secret storage and document backup, reinstall, lock-state and extension-sharing behavior. Do not add biometric prompts to an API call without an explicit host-owned authentication flow. A lock-screen-unavailable token is not necessarily an expired token.

Use platform TLS validation. Do not install global trust overrides. Pinning requires a threat model and an operational plan: OWASP includes identity pinning for controlled endpoints, while Android documents backup pins and the connectivity risk when keys change. **Recommendation:** if pinning is required, test rotation and old clients; do not add a single hard-coded certificate with no recovery path. This is a security/availability tradeoff, not a reason to accept invalid TLS. [OWASP control](https://mas.owasp.org/MASVS/controls/MASVS-NETWORK-2/), [Android configuration](https://developer.android.com/privacy-and-security/security-config).

### Requests, retries and ambiguous outcomes

Bound connection time, request time and the total operation budget. Include DNS/TLS and retry delays in the meaning of the exposed deadline. Retry only operations whose semantics permit it; add jitter and bounded attempts/time. Avoid retries at several layers multiplying each other. Mobile network latency makes a datacenter-only timeout unsuitable without adjustment. [Amazon Builders' Library, 2019](https://aws.amazon.com/builders-library/timeouts-retries-and-backoff-with-jitter/).

A timeout does not establish that the server did nothing. Associate one idempotency key with one logical mutation, retain it across retries, and use a new key for a new intent. The server must define key scope, retention, payload mismatch and concurrent execution behavior. [Amazon's idempotency design](https://aws.amazon.com/builders-library/making-retries-safe-with-idempotent-APIs/).

Do not assume every service's idempotency semantics match. Stripe API v1 stores the first execution result, including a `500`; keys can be pruned after at least 24 hours. Its API v2 can retry failed/partial work toward completion. A generic “retry forever with the same key” policy is therefore wrong. Expose the existing API's guarantee and its expiry boundary. [Stripe idempotency](https://docs.stripe.com/api/idempotent_requests).

Respect server delay signals. `Retry-After` can contain seconds or an HTTP date; a long delay may exceed the caller's budget, in which case return a structured retry-later result. Do not translate every non-2xx response into the same retryable exception. [HTTP semantics, RFC 9110](https://www.rfc-editor.org/rfc/rfc9110.html). Service-specific classification matters: GitHub can return either `403` or `429` for rate limits and distinguishes primary from secondary limits. [GitHub rate-limit rules](https://docs.github.com/en/rest/using-the-rest-api/rate-limits-for-the-rest-api).

Cancellation should promptly stop local work, waits and observers. It cannot promise rollback after the server accepted a mutation. Separate “caller stopped waiting” from “server cancelled the job.” A durable upload or job needs a stable identifier and a way to inspect status after app restart.

### Data modeling and evolution

Preserve unknown response fields when round-tripping them is part of the contract; otherwise ignore additions safely. Preserve unknown enum raw values where possible. Do not convert an unknown payment state into `failed` or `succeeded`. Requests and responses often need different types: a response may contain server-only fields or states the client cannot create.

Represent missing, explicit null and value separately when the API distinguishes them. JSON Merge Patch, for example, assigns deletion semantics to null; omitting the field leaves it unchanged. A single nullable property can lose that distinction. Use a patch field wrapper or explicit update operations. Do not impose Merge Patch semantics on an API that uses a different contract. [RFC 7396](https://www.rfc-editor.org/rfc/rfc7396.html).

Honor numeric precision and units. JSON permits numbers beyond what common implementations represent exactly; interoperable exact integers with binary64 fall within ±(2^53−1). Use exact integer/decimal representations or strings according to the existing API, especially for money and identifiers. Reject overflow rather than rounding silently. Test non-ASCII strings and malformed input. [RFC 8259](https://www.rfc-editor.org/rfc/rfc8259.html).

Keep timestamps distinct from calendar dates and durations. Parse the API's specified format and precision; do not use the device's display locale. Store opaque IDs as opaque values. Encode path segments and query values exactly once. For uploads, distinguish source-file lifetime, bytes transferred and server acceptance.

Expose both page-level access and optional lazy iteration. Never eagerly fetch a whole account to make a convenient array. An empty page may still have a next token; stop according to the API's continuation signal. Preserve filters across page requests and handle expired/repeated cursors. Tokens do not replace authorization. [AIP-158](https://google.aip.dev/158).

### Errors developers can act on

Separate transport failure, cancellation, invalid credentials, permission denial, validation, conflict, rate limit, server failure and incompatible response. Keep HTTP status, stable service error code, request ID and safe retry information. Human text is not a stable branching interface. RFC 9457 supplies a standard problem format where the API can adopt it; an existing error envelope need not be replaced merely to build an SDK. Do not surface server internals or raw sensitive bodies in default logs. [Problem Details](https://www.rfc-editor.org/rfc/rfc9457.html).

GraphQL requires a distinct outcome model. Apollo iOS distinguishes execution errors from GraphQL errors, which can accompany usable partial data. Preserve that result rather than throwing away successful fields or presenting partial data as complete. [Apollo iOS error handling](https://www.apollographql.com/docs/ios/fetching/error-handling).

### Cache, offline and realtime are separate promises

HTTP caching, normalized object caching, durable storage and offline writes solve different problems. Apollo Kotlin supports HTTP, normalized and external caches; external storage can retain the host's existing source of truth. **Recommendation:** avoid forcing a second database into a thin client; introduce SDK-owned persistence only when its semantics justify it. [Apollo cache choices](https://www.apollographql.com/docs/kotlin/caching/introduction).

Firestore illustrates a substantial offline contract: native persistence defaults on; cached reads/listeners and writes operate offline; conflicting document changes use last-write-wins. Snapshot metadata identifies cache results, which may be incomplete or stale. This is a service-specific synchronization model, not a property every SDK should claim. [Firestore offline behavior](https://firebase.google.com/docs/firestore/manage-data/enable-offline).

Cache deletion is also a security contract. A 2019 Firebase issue asks for logout-time cache removal because root access can expose prior-user records. Current Firestore Android docs provide `clearPersistence`, require an inactive instance and warn that it does not securely overwrite data; they recommend disabling persistence for apps sensitive to between-session disclosure. Do not repeat the old issue as proof that no clearing API exists. [Issue #466](https://github.com/firebase/firebase-android-sdk/issues/466), [current API](https://firebase.google.com/docs/reference/android/com/google/firebase/firestore/FirebaseFirestore).

Realtime SDKs need explicit connection and continuity states. Ably documents a limited recovery interval, typically around two minutes, after which history/reconciliation is needed. Its currently served page mixes old queued-publish wording with newer device/server SDK error behavior; do not copy a universal disconnected-publish guarantee from that page. Verify the chosen SDK/version. **Derived guidance:** expose gaps and resync state instead of silently treating reconnection as complete recovery. [Ably connection recovery](https://ably.com/docs/connect/states).

Mobile background policy differs by platform. LaunchDarkly documents mobile foreground/background strategies and an iOS exception to background fetching. That difference is useful honesty: parity should cover the business contract, with explicit platform capability differences. [SDK types](https://launchdarkly.com/docs/sdk/concepts/client-side-server-side).

For file transfer, Apple's background URL sessions require lifecycle integration and session reassociation; they are not arbitrary perpetual execution. Host apps must own the required application callbacks. Android initialization guidance likewise supports delayed/on-demand initialization. A client constructor should not unexpectedly create threads, databases, network traffic and background jobs. [Apple background transfer guide](https://developer.apple.com/documentation/foundation/downloading-files-in-the-background), [Android startup guidance](https://developer.android.com/topic/performance/appstartup/best-practices).

### Privacy behavior must match the shipped binary

A 2024 study examined 158 Android SDKs from Google Play and CAICT indexes using static taint analysis and language-model-assisted policy analysis. It reported 49 without privacy policies and many policy/implementation mismatches. This is evidence to inspect actual dependencies and behavior; it is not a current prevalence estimate for SaaS API clients. The authors note no general dynamic testing, incomplete sensitive-method coverage and ambiguous disclosures. Their static “access” definition also differs from proving data was transmitted in a particular host app. **Recommendation:** audit startup traffic, permissions, stored files and optional telemetry in a real release host; publish a versioned data inventory. [Study, methodology and limitations](https://arxiv.org/html/2409.10411v1).

### Release and retirement are API behavior

Declare the public API before promising SemVer. Include public types, callbacks, threading, persistent data, defaults and observable behavior in review; version numbers alone cannot enforce compatibility. Deprecate with a replacement before removing a supported API, and keep published release artifacts immutable. [SemVer 2.0](https://semver.org/).

Expose service deprecation separately from shutdown. RFC 9745's `Deprecation` signal does not change resource behavior; `Sunset` communicates expected unavailability. Surface these to developers through diagnostics and release/operator notices, not repeated customer-facing alerts. Mobile rollout lag means a server cutoff affects installed apps whose developers may already have shipped a fix. [RFC 9745, March 2025](https://www.rfc-editor.org/rfc/rfc9745.html).

For distributed binaries, publish verifiable source revision, build process and checksums; an SBOM helps identify transitive exposure. GitHub artifact attestations can bind an artifact to a build and attest an SBOM, with plan/access limits. They do not prove the code is correct or harmless. Test the exact artifact after staging it; rebuilding for publication can produce different bytes. [GitHub attestations](https://docs.github.com/en/actions/how-tos/secure-your-work/use-artifact-attestations/use-artifact-attestations).



## 3. Native APIs and platform integration

### Swift and iOS

**Read the call site.** Swift's guidelines put clarity at the point of use above brevity and ask authors to document public declarations. Review `try await client.orders.cancel(id: orderID)` in a realistic flow, not only a declaration list. Avoid mechanically exporting server field names when they obscure a Swift call; preserve wire mappings separately. Prefer meaningful parameter labels and noun/verb semantics. This is language guidance, not evidence that one naming scheme increases sales. [Swift API Design Guidelines](https://www.swift.org/documentation/api-design-guidelines/).

**Async contracts.** Offer `async throws` for one-shot operations; use a sequence for ongoing events where appropriate. Define whether cancellation stops local waiting, the HTTP request, or a server operation. Swift cancellation is cooperative; a cancellation handler can run while the task still runs. Check cancellation before retries and large parsing loops; clean resources safely. Do not catch cancellation and silently retry. Callback/Objective-C adapters remain useful for a supported installed base, but should share one implementation. [Swift concurrency chapter](https://github.com/swiftlang/swift-book/blob/main/TSPL.docc/LanguageGuide/Concurrency.md).

**Isolation is public API.** State which values can cross concurrency boundaries and which operations require the main actor. Keep UI presentation on the main actor. Do not make the entire networking client main-actor-bound merely to silence diagnostics. Test from both a main-actor model and detached/background work. This is a design recommendation; the exact isolation model depends on mutable state. The migration guide distinguishes compiler version from language mode: using a Swift 6 compiler does not itself mean the library is compiled in Swift 6 mode. [Swift migration guide](https://www.swift.org/migration/).

**Instances beat hidden global ownership.** Allow separate clients for tests, environments and simultaneous accounts. Isolate request/session dependencies per client. Explicit disposal should terminate listeners and sockets; dropping a client should not leave an immortal task. Supabase 2.55.0 (2026-08-12) fixed a task retaining `SupabaseClient`, WebSocket/session cleanup, auth refresh cleanup and reconnect that previously stopped after one failed retry. Those are shipped fixes, not hypothetical style preferences. [Release 2.55.0](https://github.com/supabase/supabase-swift/releases/tag/v2.55.0).

**Retain structured failures.** Preserve an error category, HTTP status when present, server code, request identifier and useful underlying transport error; redact credentials and personal data. Distinguish cancellation, offline/waiting, timeout, authorization, validation and ambiguous mutation outcomes. A localized message alone is not a stable branching API. Supabase's same release fixed decoding `details` into its singular Swift `detail` property: a typed model can still lose the most useful server error field. [Release 2.55.0](https://github.com/supabase/supabase-swift/releases/tag/v2.55.0).

**Public types outlive today’s schema.** Recommendation: separate request and response types; represent omitted, null and actual values distinctly where the API does; handle new enum values without failing the whole response; preserve money precision and large IDs. Avoid public third-party HTTP types unless their dependency is an intentional part of the SDK contract. These are compatibility consequences, not independently measured Swift UX outcomes.

**Let the app choose waiting behavior.** `waitsForConnectivity` affects initial establishment, not a connection lost midstream. Background sessions always wait. Surface waiting separately from failure so the host can offer cancellation or a manual override; do not add a second reachability-triggered retry over the same pending task. [Apple property documentation](https://developer.apple.com/documentation/foundation/urlsessionconfiguration/waitsforconnectivity?language=objc), [Apple network-conditions talk transcript](https://developer-mdn.apple.com/videos/play/tech-talks/111378/).

**Expensive and constrained networks differ.** Expose sensible configuration for cellular/expensive/Low Data Mode behavior. Defer nonessential prefetches, allow an explicit user action to choose otherwise, and avoid an alert for every transient network change. This is Apple's recommended behavior for apps; an SDK should provide state and configuration so its host can implement it. [Apple network-conditions talk transcript](https://developer-mdn.apple.com/videos/play/tech-talks/111378/).

**Background transfer is a separate product feature.** Background URLSession can transfer while suspended, but uses a different process, needs delegate delivery, supports HTTP/HTTPS and follows redirects without the usual redirect delegate callback. Do not market an arbitrary async JSON request as durable background execution. Persist identifiers, coordinate relaunch events with the host and test interrupted transfers if the SDK promises them. [Apple background download guide](https://developer.apple.com/documentation/foundation/downloading-files-in-the-background?changes=_6).

**Close sessions you own.** URLSession retains its delegate until invalidation or app exit. Reusing a configured session is useful; constructing a retained delegate/session cycle per call leaks. Distinguish caller-owned sessions from SDK-owned sessions so shutdown does not cancel unrelated app work. [Apple URLSession documentation](https://developer.apple.com/documentation/foundation/urlsession?changes=_4_2%2C_4_2).

**Interrupted flow recovery matters more than a spinner.** Stripe issue #6335 reports a network disruption during 3DS leaving the singleton payment handler busy, then returning local errors for repeated attempts across payment IDs. The April 2026 report concerns SDK 25.11.0; it records 418 failures. Linked fix commits exist, but the issue remains open and the July follow-up also used 25.11.0. This does not establish a defect in the latest release or an incidence rate. Design long workflows with a bounded completion, reset/reconciliation path and distinguish server outcome from local UI completion. [Stripe #6335](https://github.com/stripe/stripe-ios/issues/6335).

### iOS compatibility, credentials and host integration details

**Concurrency annotations can be breaking changes.** Adding a generic `T: Sendable` constraint, an `@Sendable` closure parameter or `@MainActor` to existing API can break source and ABI compatibility. Adding `Sendable` to a concrete type is generally source-compatible and ABI-compatible, with overload-resolution caveats. `@preconcurrency` can stage changes, but is not a universal ABI repair: inferred annotations in client declarations complicate mangling. Adding `sending` to a parameter is restrictive; adding it to a result relaxes callers. Remedy: review public API diffs and compile representative old clients before calling annotation work a patch. Do not solve compatibility by indiscriminately asserting `@unchecked Sendable`; prove synchronization. [Swift migration guide: library evolution](https://github.com/swiftlang/swift-migration-guide/blob/main/Guide.docc/LibraryEvolution.md).

**Toolchain changes need their own release note.** A tools-6.0 manifest defaults targets to Swift 6 mode, but per-target/package overrides exist. Swift 5 mode can enable complete concurrency checking as warnings; Swift 6 mode enables it unconditionally. Version-specific manifests can keep older toolchains supported, at a testing cost. Remedy: test the oldest advertised compiler and a Swift-6-mode host, not only the package's selected mode. Publish compiler floor, mode, runtime floor and feature gates separately. [Swift data-race checking guide](https://github.com/swiftlang/swift-migration-guide/blob/main/Guide.docc/EnableDataRaceSafety.md).

**A dependency rename can break the whole host before compilation.** Supabase #1384 (September 26, 2026) reports 2.53.0 conflicting with SnapshotTesting 1.19.6: old `xctest-dynamic-overlay` and renamed `swift-issue-reporting` resolve as separate package identities but export the same targets. The issue proposes updating the dependency URL. This is a reproducible reporter case, not proof every current Supabase release fails. Remedy: use canonical package identities, coordinate renamed dependencies and resolve a host containing likely companion libraries in CI. Deleting DerivedData cannot repair an intrinsically invalid dependency graph. [Supabase #1384](https://github.com/supabase/supabase-swift/issues/1384).

**Do not embed somebody else's singleton twice.** Firebase's maintainer guide warns against bundling its static SDK into a vendor dynamic framework when the host may also link Firebase: duplicate classes and initialization state can cause undefined behavior. It recommends exposing dependencies through the final link rather than hiding them inside a vendor dynamic binary. Static code in separate app/extension executables instead increases size without that same within-process collision. Remedy: test an app that already uses the dependency; keep analytics optional; avoid shipping a private copy of a common SDK inside your binary. This is a Firebase-specific documented failure pattern, not a rule that all dynamic frameworks are bad. [Firebase SDKs in libraries](https://github.com/firebase/firebase-ios-sdk/blob/main/docs/firebase_in_libraries.md).

**An extension-safe core needs a real extension host.** Apple's archived extension guide forbids extension-unavailable APIs and documents the extension-safe build setting. Shared app-group data requires synchronization because app and extension run separately. For a headless API client, keep presentation and app-lifecycle hooks in optional adapters; compile a share/widget extension consumer and archive its containing app. A singleton or actor in the main app cannot serialize access from the extension process. If both can refresh the same rotating credential, define shared coordination or give each a separate session. The latter is research guidance derived from the separate-process boundary; the API's refresh semantics decide the design. [Apple extension guide](https://developer.apple.com/library/archive/documentation/General/Conceptual/ExtensibilityPG/ExtensionScenarios.html).

**Locked is different from logged out.** Choose Keychain accessibility to match promised behavior. `WhenUnlocked` is the default; `AfterFirstUnlock` permits locked-device background use after the first unlock since restart. `ThisDeviceOnly` prevents migration to a different device, not every possible same-device restoration. `WhenPasscodeSetThisDeviceOnly` loses items when the passcode is removed. Remedy: expose a credential-store policy, preserve exact Keychain failure categories and defer locked-device work rather than interpreting unavailable secrets as invalid credentials. Do not silently weaken accessibility to make a background retry succeed. [Apple Keychain accessibility](https://developer.apple.com/documentation/security/restricting-keychain-item-accessibility).

**Uninstall is not an SDK logout protocol.** Apple DTS's 2016–2017 explanation says persistence across uninstall was undocumented implementation behavior; iOS 10.3 beta changed it and rolled back. The supported design lesson is to behave reasonably whether secrets survive. For an actual “lost with installation” requirement, DTS describes encrypting the Keychain secret with a random key kept in the app's disk container. This is historical engineering guidance, not a new guarantee about every 2026 device/backup scenario. Explicit logout should delete the SDK's own credentials; never wipe the whole app's shared Keychain group. [Apple DTS thread](https://developer.apple.com/forums/thread/36442).

**Reinstall policy belongs to the host.** TfL's account-functionality assessment says its iOS app removes saved account data on sign-out and first launch after reinstall because Keychain persistence is possible. This is a first-party product decision, not universal platform policy. Expose a narrowly scoped reset so hosts can implement such a choice; preserve another account's or sibling app's records. Test fresh install, uninstall/reinstall, app transfer/access-group changes and restore-to-new-device separately. [TfL assessment, page 10](https://tfl.gov.uk/cdn/static/cms/documents/tfl-go-account-functionality-dpia-v2.pdf).

**Logout has multiple layers.** Auth0's FAQ separates clearing app credentials from removing the browser SSO cookie. Clearing local tokens alone can lead to immediate sign-in again through the shared cookie. An ephemeral web-auth session avoids shared-cookie SSO, with a deliberate experience tradeoff. The same FAQ documents a screen-lock/background interruption leaving `transactionActiveAlready`; `WebAuthentication.cancel()` clears that transaction before retry. Blind cancellation on every background event can kill a valid login when someone switches to another app. Remedy: document local logout versus browser/provider logout and retain an explicit recovery path. Do not promise control over the system consent alert. [Auth0 maintainer FAQ](https://github.com/auth0/Auth0.swift/blob/master/FAQ.md).

**Account-switch protection must include late results.** Recommendation: bind each operation to its originating session/account generation. On a switch, cancel old observers and clear account-scoped caches; reject late old-account refresh/results before writing current state. Keep credential-store keys scoped by service/environment/account. Auth0's current CredentialsManager source exposes storage/key parameters and namespaces its session-expiry key from the credential key. It also documents that only a subset of operations are thread-safe despite the type being `Sendable`; callers must respect the actual method contract. [Auth0 CredentialsManager source](https://github.com/auth0/Auth0.swift/blob/master/Auth0/CredentialsManager.swift). A `Sendable` label alone is not a complete account-isolation audit.

**Backend releases must be tested against old SDKs.** Firebase's October 2, 2026 postmortem says deleting a legacy configuration flag left a reference behind. Missing-name validation crashed active Apple-platform clients; invalid configuration was served for 2h11m. Server health dashboards stayed green because they did not capture client crashes. The owner committed to payload validation, safe defaults, dependency checks in config changes and phased rollouts. Apply those remedies to SDK-served responses and remote configuration: test shipped client versions, tolerate unusable optional config and monitor host failures. A kill switch must not depend on the same broken parser it is meant to protect. [Firebase postmortem](https://firebase.blog/posts/2026/10/firebase-analytics-outage).

**Read the incident's corrections.** The Firebase issue first suggested cached configuration could keep causing crashes after rollback. Maintainers later said this was unverified and likely delayed crash uploads; they reported no evidence of ongoing crashes and did not require an emergency SDK update to resolve the incident. Later comments identify GoogleUtilities 8.1.4 and Firebase 13.0.0 hardening. Distinguish server mitigation from installed-client hardening, and occurrence time from upload time. [Firebase #16728, maintainer updates](https://github.com/firebase/firebase-ios-sdk/issues/16728#issuecomment-5884287771). This is stronger evidence than inferring cause or duration from raw comment counts.

**Benchmark the actual integration, including no-op startup.** XCTest provides launch, clock, CPU, memory, storage and signpost metrics. Suggested fixtures: host without SDK; linked but not initialized; initialized with networking disabled; first authenticated call; pagination/large response; repeated client creation/destruction; cancellation during stream; reconnect after outage. Fix device/build/configuration and compare against a baseline. Measure Release archive size separately from compressed package download and build-cache size. These are proposed experiments, not measured results. [Apple performance tests](https://developer.apple.com/documentation/xctest/performance-tests).

**Catch accumulation, not only peak memory.** `XCTMemoryMetric` records peak and net growth over the measured block. Test many create/use/dispose cycles; one successful request can hide retained sessions and observers. Track regression against the same host configuration. Combine with an Instruments trace when a baseline regresses; do not substitute a profiler's instrumentation overhead for production memory. [Apple memory-regression guide](https://developer.apple.com/documentation/xcode/preventing-memory-use-regressions).

**Provide three consumer examples, with explicit ownership.** Suggested deliverables: (1) SwiftUI view-model owns a client/task and handles cancellation without showing a failure alert; (2) UIKit controller presents optional auth/UI using the correct scene and releases observers on teardown; (3) extension/headless target uses core only and caller-provided credentials. Compile each against released artifacts in CI, including the supported old toolchain; do not publish pseudocode as a runnable quickstart. These are synthesis recommendations from the packaging, lifecycle and extension cases above; they are not a requirement to ship UI with every SDK.

### Kotlin and Android

**Make the SDK a good guest.** Give callers control over work, credentials, logging and optional features. Keep global state, UI frameworks, persistent jobs and device services out of a basic HTTP client unless its contract requires them. The strongest observed failure is cross-SDK interference: RevenueCat reported Stripe's process-wide `HttpResponseCache.install` changed unrelated requests and mixed cached response headers with its own cache behavior. Issue #14616, opened 2026-09-18, includes affected Stripe 23.19.0 and is now closed through #14812. This is a concrete compatibility failure, not evidence that all Stripe releases are unsafe. Prefer an SDK-owned client/cache; test alongside another SDK. [Issue](https://github.com/stripe/stripe-android/issues/14616).

**Separate the wire client, platform services and UI.** Recommendation: a small transport/model layer; optional Android credential/background modules; optional Compose/View UI. Supabase provides service modules, separate Compose/image integrations and a BoM. Its Ktor engine selection makes dependencies explicit but adds setup work: real-time needs an engine with WebSockets. Its current README lists Android API 26 unless using core-library desugaring, and guarantees compatibility with latest service releases unless stated otherwise. Good modularity does not mean every server/version combination works. [Supabase Kotlin](https://github.com/supabase/supabase-kt).

**Kotlin-first need not mean Java-hostile.** Use suspend functions for one-shot Kotlin calls and Flow for streams. A Java-facing adapter may expose a callback, executor and cancellation handle. Annotate Java nullability; put SAM callbacks last; use real functional interfaces instead of Kotlin `Unit` lambdas exposed to Java. Give top-level APIs deliberate JVM names. Compile small Java and Kotlin consumers in CI. [Kotlin-Java interop](https://developer.android.com/kotlin/interop). Do not promise effortless Java use of every coroutine API; make the supported Java surface explicit.

**Evolve three contracts.** Source compatibility, binary compatibility and behavior are separate. Explicit public return types prevent accidental ABI changes. Adding a default argument can still change JVM signatures; public data-class constructors, `copy` and destructuring make apparently harmless field edits breaking changes. Preserve overloads or introduce new types deliberately. Current Kotlin guidance says `@JvmOverloads` alone does not preserve binary compatibility for Kotlin callers; the newer `@IntroducedAt` alternative is experimental. Avoid relying on experimental language machinery merely to avoid designing an evolution policy. [Kotlin backward compatibility](https://kotlinlang.org/docs/api-guidelines-backward-compatibility.html).

#### Android-specific implementation details

1. **Main-safe requests.** An SDK method may be called from the main thread. Move blocking work internally; `suspend` alone does not make a function nonblocking. Return control promptly and inject dispatchers where useful for deterministic tests. Do not ask every integrator to discover which calls freeze UI. [Coroutine guidance](https://developer.android.com/kotlin/coroutines/coroutines-best-practices).
2. **Caller-owned cancellation.** A suspend request should follow its caller's scope; Flow should state whether collection starts work and when it stops. Avoid unbounded `GlobalScope` work. Long-lived subscriptions need explicit teardown, bounded buffers and a documented reconnect policy. Rethrow `CancellationException` when catching broadly; never turn cancellation into a service error or retry. [Coroutine guidance](https://developer.android.com/kotlin/coroutines/coroutines-best-practices); the last subscription details are design inferences.
3. **Durable work is optional.** WorkManager persists scheduled work across restart/reboot and supports constraints and retries. It is not a substitute for every immediate API call. Put queue/worker integration behind a module or adapter; document force-stop, auth expiry and delayed scheduling instead of promising exact delivery times. [Persistent work](https://developer.android.com/develop/background-work/background-tasks/persistent).
4. **Initialization must earn startup cost.** AndroidX App Startup coordinates dependencies through one provider; it avoids many separate startup providers. It also supports manual/lazy initialization. An ordinary SaaS client can usually wait for explicit construction. Do not perform network/disk work during automatic startup merely to achieve a shorter quickstart. [App Startup](https://developer.android.com/topic/libraries/app-startup).
5. **Inspect the merged manifest.** Library manifest entries become host-app entries. Permissions, activities, providers and required hardware can alter the app's distribution and behavior. Publish the intended manifest contribution and compare a minimal host before/after integration. Do not assume checking the library's own manifest reveals transitive effects: library-module manifest output excludes dependency manifests. [Manifest merging](https://developer.android.com/build/manage-manifests).
6. **Leave network policy with the host.** Respect HTTPS and the app's trust configuration. Document debug-only trust setup for local servers; do not globally enable cleartext or install permissive certificate checks. Domain-specific configuration and debug overrides exist. Pinning adds rotation/recovery duties and should follow an actual threat model. [Network security configuration](https://developer.android.com/privacy-and-security/security-config).
7. **Do not confuse keys with credentials.** Android Keystore protects cryptographic keys, not an arbitrary token string by itself. Hardware protection varies; StrongBox costs more and may be unavailable. If providing token persistence, define encryption, loss/recovery and logout behavior; permit the host to own storage. Do not turn a normal API wrapper into a forced biometric/login policy. [Android Keystore](https://developer.android.com/privacy-and-security/keystore).
8. **Consent precedes collection.** Publish collected data, purpose, permissions and optional behavior. Provide a way to honor host-collected consent before initializing collection. An app owner remains responsible for SDK behavior even for unused functions. Silent telemetry can create a host's store violation and support incident. [SDK safety guidance](https://developer.android.com/guide/practices/sdk-best-practices).
9. **Test release artifacts.** Package narrow consumer R8 rules for reflected/JNI access. Avoid package-wide keep rules and global optimizer switches. Prefer generated serializers where practical. A debug sample passing says little about optimized consumers. [Library optimization](https://developer.android.com/topic/performance/app-optimization/library-optimization).
10. **Resources have separate reachability.** Stripe Terminal #760 reports Tap to Pay 5.8.1/6.0.0 release crashes after an AGP 9.4.1 update: kept R fields did not preserve layouts accessed from hidden runtime code. The reporter supplied an APK check, crash and proposed resource keep file; issue remained open. This is a user report, not independently reproduced. Test minified resource-shrunk UI flows; never make disabling host shrinking the permanent fix. [Issue](https://github.com/stripe/stripe-terminal-android/issues/760).
11. **Publish dependency metadata.** Prefer Maven publication over a loose AAR. An AAR alone lacks identity/version/dependency metadata. A local zipped Maven repository can serve offline/private delivery without discarding POM semantics. Test installation from the repository by a clean external consumer. [Upload guidance](https://developer.android.com/build/publish-library/upload-library).
12. **Ship useful publication metadata.** Maven Central asks for source/Javadoc artifacts, signatures/checksums and POM project/license/developer/SCM data. Make source navigation and documentation work in the IDE. Do not regard a successfully uploaded binary as a finished SDK release. [Central requirements](https://central.sonatype.org/publish/requirements/).
13. **Make unsupported setups fail clearly.** AAR `minCompileSdk` conveys a compile-time floor; runtime `minSdk` conveys a different limit. Use `RequiresApi` for guarded features rather than raising the whole SDK floor without need. Do not instruct users to override manifest checks to hide actual incompatibility. [Release preparation](https://developer.android.com/build/publish-library/prep-lib-release).
14. **Make API misuse discoverable.** Bundle targeted Lint checks with clear fixes for costly mistakes such as missing redirect declarations or forbidden main-thread methods. The Android Lint guide supports checks distributed through AAR `lint.jar`/`lintPublish`; this adds its own Lint API compatibility/testing work. Do not add a custom Gradle plugin when annotations and ordinary compiler errors suffice. [Lint guide](https://googlesamples.github.io/android-custom-lint-rules/api-guide.html).
15. **Protect cached sessions across lifecycle changes.** Recommendations derived from host lifecycle/credential responsibilities: construct clients without retaining an Activity; bind optional UI launchers to the correct lifecycle; cancel obsolete screen work; reject stale responses after logout/account switch; define process-death restoration separately from in-memory retries. Test tenant/account boundaries explicitly, including callbacks arriving after logout. No claim that one Android library solves these service semantics.
16. **Explain all side effects.** Recommendation: a release note should flag new permissions, startup providers, telemetry endpoints, disk files, dependency floors and background work. Such changes can be breaking operationally even when signatures stay intact. The manifest, SDK safety and Stripe cache evidence above establish why API diffs alone miss real integration risk.

## 4. Compatibility and delivery

### Apple distribution and support

**Source SwiftPM first is a practical default.** It keeps debugging and auditing straightforward. Closed-source binaries can justify XCFramework distribution, but require slices for supported platforms and simulators. A URL-based SwiftPM binary artifact has a checksum; changing hosted bytes without updating the manifest fails integrity validation. Package source and binaries can coexist. Apple notes binary packages have reduced portability. [Apple: distributing binary frameworks](https://developer.apple.com/documentation/xcode/distributing-binary-frameworks-as-swift-packages) .

**Binary stability is separate from source compatibility.** Swift's 2020 explanation distinguishes ABI stability, module stability and library evolution. Enable library evolution from the outset for frameworks intended to be updated independently of compiled clients; it changes performance and enum exhaustiveness and is itself a binary-incompatible switch. Source packages rebuilt with their app do not automatically benefit. Do not promise “Swift compatible” without stating source versus binary delivery and tested compiler range. [Swift library evolution](https://www.swift.org/blog/library-evolution/index.html).

**Ship the manifest, then inspect the archive.** `PrivacyInfo.xcprivacy` belongs in package resources; Apple says SwiftPM does not recognize it as a resource automatically, so explicitly declare it. An XCFramework needs the correct manifest in every platform variant. A bare static `.a` cannot contain resources; use a resource-bearing static framework distribution. Invalid manifests can reject the consuming app. Build an actual host archive to verify packaging, not only `swift test`. [Apple: adding a privacy manifest](https://developer.apple.com/documentation/bundleresources/adding-a-privacy-manifest-to-your-app-or-third-party-sdk) .

**Do not generalize signature rules.** Apple requires manifests for its listed commonly used SDKs, including repackaged versions; binary dependencies in the stated cases also require signatures. Apple encourages other SDKs to adopt both. The list is not a rule that every source-only package must carry a binary signature. Independently disclose actual data collection and required-reason API use. A manifest does not transfer the host developer's responsibility away. [Apple third-party SDK requirements](https://developer.apple.com/support/third-party-SDK-requirements/).

**CocoaPods is a migration concern now.** The official plan, updated May 2025, schedules trunk read-only for December 2, 2026, with a November 2–6 test. It stops new podspecs and versions; existing installs, private spec repos and vendored dependencies are separate. As of the research date, do not describe the scheduled permanent switch as already completed. New SDKs should not rely exclusively on trunk for future fixes; support a customer-specific migration window where needed. [CocoaPods owning announcement](https://blog.cocoapods.org/CocoaPods-Specs-Repo/).

**Document four floors separately.** Minimum deployment OS, compiler/tools version, source-language mode and feature availability differ. Supabase's tag `v2.55.5` declares Swift tools 6.1 and iOS 16; its moving main README showed `3.0.0-alpha.1`, Swift 6.2 and Xcode 26.0. Do not cite main as the stable-release contract. RevenueCat's read README lists iOS 13 and Xcode 15 while some UI/features can require newer systems. These examples show different support choices, not market prevalence. [Supabase tagged manifest](https://github.com/supabase/supabase-swift/blob/v2.55.5/Package.swift), [RevenueCat README](https://github.com/RevenueCat/purchases-ios).

**Dependency changes can break an apparently small upgrade.** Stripe's migration guide says 26.7.0 adds `StripeFinancialConnectionsLite` to PaymentSheet: manual/Carthage consumers must embed the extra framework, while package-manager users get the transitive dependency. It also records callback-to-async migration. Put package-channel-specific action in release notes. Do not rely on SemVer alone to explain toolchain or deployment-floor policy. [Stripe migration guide](https://github.com/stripe/stripe-ios/blob/master/MIGRATING.md).

**OAuth redirect setup is versioned too.** AppAuth's read README specifies iOS 17.4+ for its HTTPS redirect route, `webcredentials` associated domains and matching AASA data; an `applinks` association alone is insufficient for that route. Custom schemes remain a separate option. Document the selected SDK/API route precisely rather than telling developers to “add universal links.” AppAuth also states 3.0.0 is its final CocoaPods release. [AppAuth README](https://github.com/openid/AppAuth-iOS).

**Compatibility matrix to publish.** Recommendation: supported iOS floor and newest stable; oldest and newest supported Xcode/Swift; source/binary channels; arm64 devices and promised simulator slices; SwiftUI and UIKit sample hosts; extensions/App Clips only if explicitly supported; optional Objective-C; Catalyst/macOS/watchOS/tvOS/visionOS as separate commitments. A platform compiling is weaker evidence than supported functionality and tested reliability. Keep the plain API core independent of `UIApplication` and UI frameworks where possible.

**Testing matrix to execute.** Recommendation: fresh install, upgrade from previous supported release, Release archive, dependency resolution beside representative customer dependencies, strict concurrency, cancellation/reentrancy, multiple clients, app suspension, screen lock, low-data networks, empty/huge/error payloads, identity switches and release-resource inspection. Simulator tests cannot establish full real-device background, lifecycle and device-only behavior. Pair a consumer project with unit/contract tests; a library's own workspace can hide missing public symbols/resources.

### Android support axes

| Axis | Contract to publish | Work and cost |
| --- | --- | --- |
| Runtime Android floor | Per-module `minSdk`; guarded newer features | Test oldest supported OS; check APIs and transitive floors. Lower floors add TLS, platform and desugaring coverage. Higher UI floors need not force the same core floor. |
| Compile SDK | AAR `minCompileSdk`, required resource attributes | A newer compile floor can force host build upgrades without changing device support. |
| Host target SDK | Known behavior differences under current targets | Test permissions, foreground/background behavior and optional UI under both old and new target behavior. The SDK does not choose the host's Play target. |
| Producer/consumer build tools | Tested AGP, Gradle, JDK, Kotlin ranges | A library producer's build versions are not automatically the minimum versions of every consumer. Verify published artifact consumption rather than copying internal tool versions into requirements. |
| Kotlin language/API/metadata | Document compile/runtime constraints | Kotlin language/API settings affect consumer compilers and stdlib. A newer metadata level can block a host even if runtime APIs remain old. |
| Source, binary, behavior | Compatibility promise and deprecation window | Compile source fixtures; run old compiled consumer fixtures; exercise behavior. ABI dumps cover only part of the contract. |
| Java | Explicit supported API; examples | Callback/future adapters add work; coroutine-only API needs an honest Kotlin-only declaration. |
| JVM reuse | Pure client vs Android-only module | Avoiding Context/resources in the core enables desktop/server tests and reuse; Android services still need instrumentation. |
| R8 and resources | Supported optimized release configuration | Run shrink/obfuscate/resource-shrink flows; inspect final APK/AAB. Reflection and dynamic resources increase maintenance. |
| Native binaries | ABI list, page alignment, emulator/device support | C/C++ dependencies import ABI and page-size duties even if the SDK's own source is Kotlin. Avoid native libraries unless they earn this cost. |
| Google services | Required, optional, unavailable behavior per feature | Test AOSP/emulator without services if claiming support; isolate FCM, Google sign-in, attestation or ML dependencies. |
| Form factor | API core vs adapted/tested UI | Headless HTTP compatibility does not certify TV, Wear, Auto or large-screen UI. Require product-specific testing for UI. |
| Multiple processes | Supported or explicitly excluded | Automatic initialization and caches may happen separately in each process. File locks/auth refresh coordination are extra design work. |
| Network environments | Proxies, captive portals, intermittent connectivity, IPv6 | Test network transitions and response loss; do not equate a connectivity flag with a successful API call. |
| Persistence | Schema upgrades, rollback, storage loss, account switch | Optional queue/cache raises migration and privacy obligations; a stateless client can leave persistence to the host. |

The matrix is proposed acceptance guidance synthesized from the sources above, not a claim that each exemplar supports every row.

**Two real support profiles.** Stripe Android's current README names API 23+, compile SDK 36+, AGP 8.13.2, Gradle 9.3.1 and Kotlin 2.3.10, and maps SDK releases to Compose versions (23.x to Compose UI 1.10.x). This makes the integration burden visible; a small headless SDK should not copy those UI-driven floors blindly. Stripe's low-level APIs and optional prebuilt payment UX show why a richer domain SDK can justify more dependencies. [Stripe README](https://github.com/stripe/stripe-android/blob/master/README.md). Supabase's desugaring/engine/service-version conditions above show a different KMP tradeoff. Neither example measures market prevalence.

**Small-team recommendation.** Support a conservative Android core with a tested floor chosen from actual customer apps, plus a current-toolchain lane and a release-optimized consumer. Keep optional UI on its own support table. Add older compilers/Java/non-Google devices only when promised or required by customers. Preserve an older major with security fixes for a declared interval if raising floors would strand paying integrations. Exact interval needs staffing and installed-client evidence, unavailable from public docs.

**Google services are not synonymous with Firebase.** Firebase documents required, recommended and unnecessary Play-services dependencies per module. Current Auth, Firestore, Storage and Functions rows do not require Play services; FCM and other features differ. Devices sold in some regions and Amazon devices can lack services. Do not impose a Google Play services dependency on a generic API client because a neighboring integration uses one. [Module table](https://firebase.google.com/docs/android/android-play-services).

**16 KB: runtime fact and policy dates differ.** Android 15 introduced 16 KB configurations; pure Java/Kotlin apps including all dependencies already support them, while native `.so` files require inspection, compatible updates or rebuilding where needed, and testing. Current Android developer guidance says Play updates targeting API 35+ will be blocked without support from **2027-02-01**. [Current technical guide](https://developer.android.com/guide/practices/page-sizes). The official 2025-05-08 announcement said **2025-11-01**, and Google's 2025-08-29 community-manager clarification offered extensions to **2026-05-31**; these historical pages remain discoverable. [Original announcement](https://android-developers.googleblog.com/2025/05/prepare-play-apps-for-devices-with-16kb-page-size.html), [historical clarification](https://support.google.com/googleplay/android-developer/thread/368982598/clarification-of-the-16kb-page-size-deadline-and-information-on-extensions?hl=en). Current Play technical-quality help already lists native-code 16 KB support as a requirement, with separate Wear/TV dates. Public pages do not explain every account's rollout; check the consuming app's current Play Console. Do not promise an SDK can wait until 2027. [Play quality rules](https://support.google.com/googleplay/android-developer/answer/17492799).

**Host obligations matter to SDK authors.** Current Play guidance adds optimization and sign-in restoration requirements with 2027 dates. Preserve host support; do not add login to a headless SDK solely for this policy. [Play quality rules](https://support.google.com/googleplay/android-developer/answer/17492799).

### Store submission rules are separate from SDK runtime support

Apple's current requirements page says submissions have needed Xcode 26+ and the corresponding platform SDK 26+ since April 28, 2026; since September 9, 2026, uploaded iOS/iPadOS apps must target iOS 13 or later. These are host submission requirements, not proof that an individual library works on every allowed deployment target. Test the consuming archive with the required build tools. [Apple requirements](https://developer.apple.com/news/upcoming-requirements/).

Google Play's current policy requires ordinary new apps/updates to target Android 16/API 36 from August 31, 2026, with the listed extension ending November 1. Existing-app discovery has a separate API 35 threshold; device categories and permanently private organizational apps have exceptions. A current `targetSdk` does not force the same `minSdk`. SDK authors must tolerate supported host target behavior and expose genuine compile requirements without dictating unrelated runtime exclusions. [Play target policy](https://support.google.com/googleplay/android-developer/answer/11926878?hl=en).

### What “supported” must mean

Publish four separate statements: **installs**, **features available**, **UI adapted**, **tested reliable**. A Swift package compiling for Catalyst does not prove its browser handoff works there; an Android AAR loading on a TV does not make a payment sheet usable by remote control. Do not list platforms solely because the build system accepts them.

| Cross-platform axis | User-visible difference and implementation work | Support-cost decision |
|---|---|---|
| Old OS versus current OS | New auth/presentation/storage APIs may need guards and fallbacks. New target behavior can change a host without changing SDK code. | Choose floors from customer requirements; test oldest promised plus current stable. Beta testing finds upcoming breakage but does not imply supported beta releases. |
| Low memory and slow storage | Large decoding, queues and migrations can block or terminate a host. | Test a low-resource device profile; bound allocations and disk use. High-end simulator results are insufficient. |
| Phone, tablet, foldable, multiwindow | Headless calls often remain identical; presentation anchors, resizing, keyboard and state restoration do not. | Keep UI support explicit and separate from the core. Reuse the platform-app reports' adaptation guidance. |
| Extensions and multiple processes | Separate processes do not share in-memory synchronization or singleton state. Shared credentials/files can race. | Support with coordination and consumer tests, or explicitly exclude. Do not accidentally advertise it through a broad platform manifest. |
| Regional/service variants | AOSP/no-Google devices, blocked domains, regional endpoints and customer-selected data residency alter reachable features. | Core HTTP should not require unrelated device services. Region routing is an explicit service contract; never silently fail over personal data across regions. |
| Enterprise network policy | Proxies, private CAs, VPNs and managed-device restrictions can differ from consumer defaults. | Offer scoped transport/trust integration where required; preserve secure defaults. Test actual contracted environments rather than promising every proxy. |
| Locale, time and accessibility | Protocol parsing must remain locale-independent; UI needs translations, RTL, large text and assistive semantics. Device clock changes affect expiry/retry scheduling. | Keep wire data and display policy separate; use monotonic elapsed-time budgets and server-informed expiry where appropriate. |
| Optional frameworks | Compose/SwiftUI, reactive adapters, databases and analytics add consumer compiler, runtime and privacy constraints. | Publish requirements per module; a high-floor UI should not raise the core floor without a technical reason. |

These rows are design consequences of the platform and protocol evidence above, not measured compatibility claims for any SDK.

### Representative small-team strategies

**Narrow native core:** Swift source package plus Kotlin/JVM or Android library, minimal HTTP/JSON dependencies, optional auth and UI. Best when a modest API surface and explicit customer platforms dominate. It duplicates some code but keeps each consumer idiomatic. Share contract fixtures and release policy first.

**Broad schema-driven API:** pin generators, commit or publish reviewed output, wrap only high-value workflows, and run the same wire tests on both clients. Best when endpoint/model churn dominates. Regeneration is maintenance work: inspect API diffs, binary/source breaks and runtime dependency changes. Customers should not need the vendor's whole generation toolchain merely to consume a release unless that is the stated product.

**Stateful shared core:** KMP can reduce duplicated protocol/state logic when that logic is large. Budget Swift facade, interop, artifacts, native runtime footprint and platform auth/background adapters. A shared implementation does not remove platform-specific tests.

**Long-lived enterprise line:** keep a declared older major for customers whose OS/build-tool upgrades take longer. Backport scoped fixes, publish an end date and migrate with real customer lead time. Wider compatibility has ongoing CI and incident cost; public exemplars do not determine the right support window for this SaaS.

An API used mainly by modern internal workforce apps can choose different floors from a consumer SDK serving older devices or regions with limited Google services. Geography, customer release cadence and the value of the blocked feature matter more than a universal “latest N versions” rule. No customer inventory was provided, so this report supplies strategies rather than inventing a minimum target.

## 5. Architecture, code generation and shared code

**Three viable ownership models.** Handwritten Swift/Kotlin clients suit a small operation surface and allow careful idioms, but must avoid wire drift. Generated wire models/client with a small native facade suits larger APIs while keeping stable domain methods. A shared KMP core suits substantial common logic or protocol state; its value must exceed distribution, runtime and interop cost. Compare the generated and exported API as used by a customer before selecting tooling. This is scope-based guidance, not evidence of one universal winner.

**Apple Swift OpenAPI Generator.** Apache-2.0 project with a package plugin/CLI, runtime and separate transports. Current README supports OpenAPI 3.0/3.1 and preliminary 3.2, streaming bodies and transport/middleware abstractions. URLSession transport fits Apple clients. Its generated output exposes HTTP operation/response structure; a domain facade remains a product decision. Build-time generation keeps output aligned with the schema, not necessarily with an incorrectly documented server. [Repository and examples](https://github.com/apple/swift-openapi-generator).

**OpenAPI Generator Swift.** Current `swift5` metadata says DEPRECATED; `swift6` says STABLE. The FAQ still recommends `swift5` in an older sentence while also describing stable `swift6`; prefer specific generator metadata and release notes when evaluating new work. The release history includes Swift concurrency/thread-safety and minimum-target changes. For new work evaluate `swift6` or Apple's generator; don't reflexively migrate a functioning old SDK without consumer tests. [swift5](https://openapi-generator.tech/docs/generators/swift5/), [swift6](https://openapi-generator.tech/docs/generators/swift6/), [FAQ](https://openapi-generator.tech/docs/faq-generators/), [releases](https://github.com/OpenAPITools/openapi-generator/releases).

**OpenAPI Generator Kotlin.** `kotlin` is marked stable, with several library/serializer combinations. Its own docs warn that `enumUnknownDefaultCase` differs by serializer: Moshi decodes all unknowns to the fallback; Jackson and kotlinx serialization have exceptions; Gson and multiplatform do not decode to it. A generated enum case alone is not forward compatibility. Generate fixtures for new string/integer enum values, nulls, omitted fields, unions and unknown properties, then compile and execute them against the exact pinned generator/options. Avoid server-oriented Spring/MicroProfile targets for an Android consumer SDK. [Generator documentation](https://openapi-generator.tech/docs/generators/kotlin/).

**KMP Swift export is not the same as ordinary XCFramework publication.** Current docs, dated August 28, 2026, call Swift export Alpha, with expected breaking changes and direct-integration-only support. They now document suspend→async and Flow→AsyncSequence, so older claims that it lacks concurrency support are stale. Generic erasure and collection-subclass limitations remain. For a public SDK distributed to arbitrary SwiftPM customers, verify the release artifact route rather than treating an app-local Gradle demo as proof. [Swift export](https://kotlinlang.org/docs/native-swift-export.html).

**Established KMP binary packaging still has costs.** Kotlin's SwiftPM export guide describes an XCFramework ZIP plus manifest/checksum, and combining exposed modules into an umbrella framework. Its native-binaries guide warns that exporting dependencies includes their API/code and inhibits dead-code elimination; transitive export increases size/build cost. Keep implementation dependencies internal and measure final host-app delta. Do not promise a common core is smaller merely because fewer source files are maintained. [SwiftPM publication](https://kotlinlang.org/docs/multiplatform/multiplatform-spm-export.html), [binary export](https://kotlinlang.org/docs/multiplatform/multiplatform-build-native-binaries.html).

**Tooling limitation, not KMP retirement.** JetBrains announced in October 2026 that Swift language IDE features leave the KMP plugin starting with IDEA 2026.3 / Android Studio Rabbit 2 2026.2.2. iOS running, Kotlin debugging and Kotlin/Native/Swift export remain. Budget Xcode in the workflow; do not misread the announcement as KMP being discontinued. [Owning announcement](https://blog.jetbrains.com/kotlin/2026/10/discontinuing-swift-language-ide-support-in-the-kotlin-multiplatform-plugin/).

**Fern.** Fern's current Swift quickstart is Enterprise-only and produces a Swift package; its October 19, 2026 v1 changelog moves configuration to `sdk-config.yml`. The current overview links Kotlin through a request route, while the configuration schema accepts a Kotlin target; that is insufficient evidence of public production maturity or Android minimum compatibility. Verify a real Android artifact and contract before purchase. Its public repository's raw README now states that the open-source project is no longer maintained and directs users to the hosted product. Do not describe the commercial service as abandoned or assume the old Apache-2.0 source provides a maintained self-hosted product. [Swift quickstart](https://buildwithfern.com/learn/sdks/generators/swift/quickstart), [changelog](https://buildwithfern.com/learn/sdks/generators/swift/changelog), [overview](https://buildwithfern.com/learn/sdks/overview/introduction), [schema](https://buildwithfern.com/learn/sdks/reference/sdk-config), [raw README](https://raw.githubusercontent.com/fern-api/fern/main/README.md).

**Speakeasy mobile status is not established by its broad marketing.** Its product FAQ lists Swift and Unity, but its current maturity matrix lists TypeScript, Python, Go, Java, C#, PHP, Ruby and non-language targets; neither Swift nor Kotlin has a maturity row. The public CLI README likewise supplies no Kotlin evidence. The matrix says it is incomplete, so absence is not proof of non-support. These owning sources disagree in scope; the attempted Kotlin docs path failed. Therefore this research cannot label Swift/Kotlin support GA or suitable for a two-platform mobile release. Require maintained platform-specific docs and generated sample packages; Java output is not automatically Android-compatible. [Product FAQ](https://www.speakeasy.com/product/sdk-generation), [maturity matrix](https://www.speakeasy.com/docs/sdks/languages/maturity), [CLI README](https://raw.githubusercontent.com/speakeasy-api/speakeasy/main/README.md).

## 6. SDK case studies: strengths and limits

| SDK | Transferable strength | Cost / boundary |
|---|---|---|
| Stripe iOS | Separates low-level API, payment UI and Apple Pay modules; runnable examples, integration guide, migration guide. Useful model for optional prebuilt workflows. | Payment authentication/UI complexity exceeds a generic API SDK. Privacy/data collection must be visible to host. The SDK 25.11.0 interruption report illustrates recovery risk; latest-release impact is unverified. [README](https://github.com/stripe/stripe-ios), [issue](https://github.com/stripe/stripe-ios/issues/6335). |
| RevenueCat | Native purchase workflows plus server state, named examples, migration guides, Swift and Objective-C support; recommends a smaller SwiftPM mirror for faster fetch/integration. | Its service solves subscriptions, not arbitrary API access. Published “well maintained”/“great support” are vendor claims. [README](https://github.com/RevenueCat/purchases-ios). |
| Supabase Swift | Separate Auth/PostgREST/Realtime/Storage/Functions products; custom client options; real cleanup/reconnect fixes visible in releases. | Feature breadth expands dependency, lifecycle and migration costs. Moving main and stable releases differ. [README](https://github.com/supabase/supabase-swift), [tagged manifest](https://github.com/supabase/supabase-swift/blob/v2.55.5/Package.swift). |
| AppAuth-iOS | Purpose-built OAuth/OIDC library following native-app practices; supports external user agents rather than embedded webviews. | Relevant if the existing service supports these protocols; not a reason to bolt OAuth onto every API. [Repository](https://github.com/openid/AppAuth-iOS). |
| Stripe Android / Supabase Kotlin | Explicit consumer requirements and optional modules; Kotlin coroutine or KMP integration. | Different dependency/service floors; inspect the Android cases and support matrix in §§3–4. No evidence that matching iOS method names ensures semantic parity. |

These are design case studies, not a ranking of the “best” SDKs or a claim of indie ownership. The installed audience, backend value and sales channel confound any association between SDK quality and company success.

**Size is a customer requirement, not just an optimization.** RevenueCat issue #6176 requests a lightweight core and reports roughly 5.2 MB of binary impact through SwiftPM. Treat that as the reporter's build-specific measurement, not a universal SDK size. A minimal host before/after Release archive is the right local experiment; separately measure fetch size, build time, app size, startup and memory. [RevenueCat #6176](https://github.com/RevenueCat/purchases-ios/issues/6176).

**Optional UI inherits accessibility obligations.** RevenueCat issue #7348 reports an unlabeled close button and missing test identifier in its paywall, with source excerpt. A visual X icon does not establish a clear accessible action or stable automation target. Make dismissal usable, localized and testable; include VoiceOver/Dynamic Type/RTL/dark mode in an optional UI module's tests. The issue is a concrete complaint, not a full accessibility audit. [RevenueCat #7348](https://github.com/RevenueCat/purchases-ios/issues/7348).

Additional cases appear where their behavior matters: Firestore for offline semantics, Apollo for GraphQL partial data/cache ownership, Ably for continuity, LaunchDarkly for mobile lifecycle, Auth0 for browser sessions, and Stream for composable UI. These are relevant service SDKs and libraries, not a claim that they are indie apps or that one vendor wins every criterion.

**What to copy:** Stripe's optional domain UI and migration specificity; RevenueCat's integration support artifacts; Supabase's service modules; AppAuth's narrow protocol responsibility. **What to resist:** copying payment complexity into a small API client, treating public source as an unrestricted reuse license, or using vendor size as evidence of reliability.

## 7. Developer experience, adoption and economics

Measure the funnel separately: docs visit → sample builds → authenticated sandbox operation → first domain outcome → production integration → healthy active integration → successful upgrades. Count organizations/apps, distinguish evaluators from existing customers, and record elapsed time plus human effort. Segment platform, existing app/new app, team skill and API complexity. No universal five-minute target is established by the evidence below. Require no hidden app-user analytics to measure vendor adoption; use existing account/API activity and opt-in diagnostics.

**Historical empirical foundation, not mobile-specific causal evidence.** Robillard and DeLine's 2011 mixed-method study collected opinions/experiences from over 440 professional developers at Microsoft. Documentation and learning resources were major obstacles; intent, examples, scenarios, discovering relevant API portions, and presentation mattered. Derived guidance: explain the business operation before enumerating methods; give one runnable end-to-end path, then concepts and reference. This does not establish conversion lift or a universal SDK layout. [Study abstract](https://www.microsoft.com/en-us/research/publication/field-study-api-learning-obstacles/).

**Observed learning paths and adoption correlation.** The CHI 2024 study analyzed over 100,000 users of four Google cloud services: May 2020 documentation visits and successful API calls in June–August. For users without prior API calls, its regression associated guide-documentation visits with 3.92 times the odds of subsequent successful API use; interactions were weaker for the two application APIs than the infrastructure baseline. This is an odds ratio, not a 292% conversion increase or causal effect. Limitations include logged-in users only, monthly aggregation, shared company accounts, approximate dwell time and missing task/skill variables. The researchers also found financial-only and task-oriented reader groups. Derived guidance: audit several journeys, label each page's audience, and repeat critical constraints or link them prominently from multiple entry points. Short guide visits can be copy/paste use, not failure. [Full paper, especially §§3.4, 5.4–5.5, 6](https://cmustrudel.github.io/papers/chi2024doc_logs.pdf).

**Concrete reference: RevenueCat quickstart.** It lists account/project/product prerequisites, initializes with a public key, shows multiple languages, points to samples and troubleshooting, and explains restore/identity behavior. Its breadth shows why an SDK guide must include console configuration and business state, beyond compiling code. Derived improvement: provide one platform-selected path, an expected dashboard result, and a deliberate distinction between client-safe and privileged credentials. A quickstart's line count is not total integration cost. [Quickstart](https://www.revenuecat.com/docs/getting-started/quickstart).

**Versioned docs are part of the artifact.** Stripe's README explicitly warns that `master` instructions may not match the installed release; its migration guide specifies changed imports, minimum OS versions, behavior changes and manual-linking dependencies. Derived guidance: link each package release to matching docs, migration guide and samples; test copied code against that release. Semantic-version labels alone cannot convey behavioral changes, such as payment-method layout defaults. [Repository](https://github.com/stripe/stripe-ios), [migration guide](https://github.com/stripe/stripe-ios/blob/master/MIGRATING.md).

### Practical DX reference

These are proposed build details derived from the evidence above, rather than claims that every exemplar already implements them:

1. **Landing page:** say which API tasks the SDK supports, what still needs a server, and what it intentionally does not do. Avoid claiming complete API parity when mobile exposes a safe subset.
2. **Install:** copyable SwiftPM/Maven coordinates, tested compiler/build ranges, minimal module, and exact imports. Avoid starting with a kitchen-sink sample.
3. **Credential setup:** label public identifier, user token and server secret distinctly. Show obtaining scoped tokens through the customer's backend when required; never normalize shipping an admin credential.
4. **First result:** one complete operation with actual success output and where to see it in the SaaS console. Avoid a request that returns void with no observable effect.
5. **Sample project:** keep a minimal sample and a realistic reference app separate. The first teaches installation; the second teaches lifecycle, retries, logout, error handling and UI ownership.
6. **Error diagnosis:** classify configuration, authorization, rate limit, offline, cancellation, decoding and service failures. Include a safe request ID and next action; avoid `unknown error` or full response logging with credentials.
7. **Support report:** ask for SDK/OS/build versions, request ID, sanitized logs and reproduction. Supply an issue template and security-report channel. Don't require private customer records in public issues.
8. **Search/reference:** index domain verbs and wire/API names; link symbols to recipes. A developer debugging a call should not have to restart onboarding.
9. **Cross-language parity:** document semantic parity and intentional differences. Preserve idiomatic Swift and Kotlin instead of translating method spelling mechanically.
10. **Uninstall and migration:** explain state cleanup, pending work, server-side token revocation and how to return to raw HTTP. A customer should not discover lock-in during an incident.
11. **Upgrade path:** list compile changes, runtime changes, storage migrations, minimum-target increases and rollback limits separately. Show old/new snippets and keep prior docs available.
12. **Support promise:** publish maintained release lines, security backport policy, notice channels and expected end-of-support windows. Do not silently turn a minimum-OS increase into a patch release.

### Commercial outcomes and costs

**Payment UI can reduce repeated integration work; SDK adoption lift remains unproven.** Stripe's October 2021 Payment Element launch quotes OnJam reporting migration in less than a day with one developer and a 6% checkout conversion increase. The source does not isolate native mobile SDK effects, specify randomization, or show sample size. Treat it as a vendor-published customer claim about a checkout integration, not evidence that every mobile SDK raises conversion 6%. The same post describes consolidated payment-method support and country-aware input collection: concrete product scope that can justify a UI SDK. [Launch](https://stripe.com/blog/introducing-the-payment-element).

**Charge for service value, not package downloads.** RevenueCat's current pricing offers no charge up to $2,500 monthly tracked revenue, then 1% of tracked revenue, plus enterprise arrangements. The open-source SDK accompanies subscription infrastructure and tools. This demonstrates one outcome-related pricing model; it does not establish profitability or the incremental revenue caused by the SDK. [Pricing, read 2026-11-08](https://www.revenuecat.com/pricing).

**Connection policy can affect customer bills.** Stream's chat pricing counts monthly active users and concurrent connections; its inspected page lists the Start tier at $399/month billed annually or $499 monthly for 10,000 MAU and 500 concurrent connections, with overages. Derived guidance: document what counts as activity; close unneeded connections, avoid duplicate clients, and expose usage in the console. An SDK that connects every installed app at launch can create costs unrelated to useful chat activity. The price is a dated example, not a recommended vendor budget. [Pricing, read 2026-11-08](https://getstream.io/chat/pricing/).

**Owner economics:** budget native engineering, platform betas, build matrices, security reviews, dependency updates, release packaging, docs, support triage and compatibility maintenance. Add backend cost from retries, refresh polling, realtime fanout, uploads, telemetry and test tenants. Model incremental contribution as added retained service gross profit minus SDK development/support/infra costs. Include integration support before a prospect pays and long-tail releases after a customer stops updating. This is an accounting framework, not a published measured estimate.

**Acquisition and retention:** a free package can lower adoption friction while monetization stays on the API. Paid support or SLA tiers require staffing; promises without ownership create churn. Avoid charging evaluation traffic unexpectedly, making sandbox examples billable by default, or forcing customers to upgrade just to get a security fix when the advertised support window remains active. Test the actual price model with target customers. App-store featuring and SDK package popularity do not demonstrate business viability.

**Evidence limit beside the claim:** targeted searches covered vendor SDK/payment case studies, RevenueCat integration stories, primary API-learning studies, cloud-doc adoption research and public pricing. They yielded customer claims and correlations, but no controlled experiment isolating a general iOS/Android SDK's effect on SaaS activation, retention, profit or support cost. Those outcomes depend on private funnel/cohort data and intervention design not published in the inspected sources. Therefore no universal lift or staffing payback estimate is supportable. Run a staged pilot with the same API and comparable cohorts; record integration labor, production activation, support load and later maintenance.

**Additional business comparator, explicitly non-mobile.** Fern's Frame.io case study says Python/TypeScript SDKs and unified docs launched together in November 2025. It reports first successful API call falling from 1–14 days to under one hour and 1,500+ annual support hours saved; authentication troubleshooting previously consumed 90% of support load. These are vendor-published customer claims, without cohort counts, a controlled experiment, labor-accounting method or mobile SDK treatment. Do not repeat the headline “99%” as a measured universal effect: the given time range does not establish one percentage. The useful mechanism is specific: SDK auth/upload helpers, synchronized examples and a console link to diagnose setup errors. This supports measuring setup/support burden in a pilot, not promising the same result. [Frame.io case study](https://buildwithfern.com/customers/frame).

### Distribution and support channels

Google Play SDK Index exposes version adoption, reliability/safety and data-safety links for eligible commercial SDKs; SDK Console can notify integrators through Play Console and Android Studio. It is a useful support channel, not evidence of product quality or an automatic launch channel for a new SDK. Current listing criteria include Maven distribution, an eligible category, 100 apps and 100 million app installs under Google's counting rules; therefore most new SaaS SDKs cannot count on immediate listing. [Index overview](https://developer.android.com/distribute/sdk-index), [listing rules](https://support.google.com/googleplay/android-developer/answer/12645164?hl=en).

RevenueCat's repository provides a useful process example: separate purchase/UI modules, API tester, integration tests, test apps, baseline profiles and migration material are visible. This supports inspecting release engineering, not a claim those tests establish defect-free operation or causal conversion gains. [Repository](https://github.com/RevenueCat/purchases-android).


**Commercial distribution is a real cost.** Current Sonatype rules require Maven Central Publisher Pro from **2026-10-01** for artifacts supporting adoption, integration or operation of a commercial product/service, explicitly including SDKs and generated clients, regardless of volume. Ordinary unrelated community open source remains a different category; artifact/group exemptions can be requested. Already-published artifacts remain downloadable. Do not budget public SaaS SDK publishing as automatically free because its license is open source or its binary is small. The checked public product page supplies a contact form rather than a price; the Usage Center owns account-specific limits. No quote was requested, so a numeric publishing budget cannot be inferred. [Product contact page](https://www.sonatype.com/products/maven-central-pro/contact). [Publishing rules](https://central.sonatype.org/publish/maven-central-publishing-limits/).

## 8. Failures, migration and service retirement

**Malformed remote data can become an app-launch incident.** In July 2020, Facebook iOS SDK behavior caused many host apps to crash. Sentry's contemporary account links the incident to API response handling at startup and discusses delayed initialization, local defaults, bounded retries and optional kill switches. The app owner receives the complaints even when its own code did not change. Treat this as a historical blast-radius lesson, not a claim that present Meta releases have that bug. [Sentry, 2020-07-13](https://blog.sentry.io/crash-by-api/).

**Harmless-looking setup combinations can be fatal.** A February 2021 Facebook SDK v9 issue includes a reproducer for first-launch deadlock/crash when automatic event logging and explicit activation combine. The reporter acknowledged possible misuse but objected to a trivial configuration regression crashing the host. Derived test: exercise fresh install, repeated initialization, default and disabled auto-features, and unsupported ordering. Return actionable errors or make repeated setup idempotent where possible. This is one historical report, not prevalence evidence. [Issue #1636](https://github.com/facebook/facebook-ios-sdk/issues/1636).

**SDK life and service life differ.** MongoDB deprecated Atlas Device SDKs in September 2024; end of life/removal was September 30, 2025. The local database remains open source, while Device Sync and affected authentication/service capabilities require migration. An open-source library does not make its backend durable. Derived guidance: separate optional service modules, publish data-export and migration routes, and document which capabilities survive offline or after retirement. Do not call all Realm databases dead. [Owning deprecation notice](https://www.mongodb.com/docs/device-sdks-deprecation/).

**Retirement dates must be checked by capability.** Microsoft's April 15, 2026 update extends App Center Analytics & Diagnostics support to end of March 2027 while other App Center features retired March 31, 2025. Azure Monitor Mobile Analytics was announced in public preview. Earlier June 2026 notices are superseded. For new SDK telemetry infrastructure, avoid starting on retired App Center services; migration scope differs for existing analytics users. A replacement service can also alter support boundaries and required infrastructure. [Current retirement notice](https://learn.microsoft.com/en-us/appcenter/retirement), [migration guide](https://github.com/MicrosoftDocs/azure-monitor-docs/blob/main/articles/azure-monitor/app/app-center-migration.md).

**Security can impose a hard SDK cutoff.** Stripe Terminal's current policy says mobile SDK v1–v3 will be blocked from readers in January 2027, with notifications starting June 2026 and migration to v5 or later. This is payment hardware-specific, not a generic API-client policy. Derived guidance: distinguish advisory deprecation, support end and server-enforced cutoff; provide affected-install visibility and an operator notice channel. [Terminal policy](https://support.stripe.com/questions/end-of-life-status-for-terminal-card-readers-and-sdks?locale=en-GB).

## 9. Practical integration reference

These details turn the earlier principles into reviewable behavior. They are proposed acceptance criteria, not claims that every cited SDK passes them. Apply optional capabilities only when the SDK promises them. The platform chapters and case studies supply evidence and exceptions; ordinary app UI details remain in the linked iOS/Android reports.

### Install, configure and inspect

1. **Make the smallest useful install obvious.** Show the core package first, then optional auth/UI/realtime modules with their added requirements. A single umbrella install is convenient for a demo but hides dependency and app-size costs. A genuinely indivisible workflow may justify one module.

2. **Test installation outside the SDK repository.** The sample must resolve published coordinates and use only public declarations. Internal workspace references hide missing exports, resources and dependency metadata. Keep a development sample too, but do not mistake it for an artifact test.

3. **Explain configuration errors before requests.** Reject an empty base URL, malformed public key or incompatible options with a precise message. Do not crash the host to report ordinary integration errors. Fail closed on security errors; a disabled optional feature can return an explicit unavailable state.

4. **Separate construction from side effects.** State whether creating a client reads disk, starts a socket or sends diagnostics. Avoid expensive eager work. Provide explicit start/close for stateful services, with safe repeated calls. A one-shot HTTP client need not invent a lifecycle API.

5. **Use a typed environment setting.** Make sandbox/live differences visible; permit custom endpoints for tests and approved regional deployments. Never silently retry production against sandbox or another data region. Redact endpoint secrets and reject unsafe endpoint changes during an authenticated operation.

6. **Keep configuration local.** Give each client its own auth, cache namespace and transport configuration. Avoid modifying global cookies, TLS defaults, URL handlers or response caches. Where a platform facility is process-wide, document ownership and coexistence explicitly.

7. **Keep dependency constraints deliberate.** Publish tested ranges and dependency impact; avoid floating snapshots in stable releases. Exact pins can conflict with a host, while unlimited ranges claim untested compatibility. Exercise representative dependency combinations before widening support.

8. **Provide useful diagnostics without a second analytics product.** Expose SDK version, operation name, request ID, retry count and safe timing through host-controlled hooks. Do not require remote user tracking to debug an HTTP request. Body/header logging should be deliberate, redacted and bounded.

### Call-site design

9. **Use the domain verb.** `cancelOrder` should express a business operation; `postOrdersIdCancel` exposes transport naming. Retain endpoint/wire names in reference docs for searching. A raw generated client can remain available for advanced use when its stability is stated.

10. **Make required input visibly required.** Prefer typed parameters or validated request objects over string-keyed bags. Do not accept a request that cannot succeed merely to defer every error to the network. Leave server-dependent validation to the server.

11. **Separate defaults from omitted values.** A default page size is not the same as an explicitly sent zero; an omitted patch field is not null. Document what the SDK sends. Test exact wire fixtures, including explicit clear/remove operations.

12. **Keep synchronous work honest.** A property getter should not block on a token refresh or perform network I/O. Use a suspend/async function for work that can wait. Cached access may be synchronous if its freshness and absence are explicit.

13. **Document callback execution.** Deliver callbacks on the documented executor, including immediate validation failures and cached results. An API that sometimes calls inline and sometimes later can create reentrancy bugs. Prefer a consistent contract; preserve existing behavior when compatibility requires it.

14. **Complete each one-shot operation once.** Success, error and cancellation must not race into duplicate completion. Release observers and temporary resources on every path. Multievent operations need a distinct stream API and a documented terminal state.

15. **Make ownership legible.** If a caller supplies a session, coroutine scope, executor or store, state whether the SDK closes it. Closing a client must not cancel unrelated host work. Conversely, an SDK-created socket should not survive indefinitely after disposal.

16. **Keep public extension points small.** Offer transport, credentials, clock and logging seams where they enable real integration or testing. Avoid exposing all internal serializers, interceptors and database tables as a permanent customization contract.

### Network and mutation behavior

17. **One retry policy owns the budget.** Coordinate transport retry, SDK retry and caller retry. A request should report useful attempt context when exhausted. Jitter helps spreading load; a configurable unlimited loop does not make a safe default.

18. **Retain mutation identity.** A retry reuses the logical operation's key; a new purchase or new message gets a new key. If durable retry is supported, persist the key with the payload before sending. Do not derive deduplication solely from identical payload bytes.

19. **Make timeout ambiguity actionable.** Return the operation ID and an inspect/reconcile route where available. Do not tell the UI “nothing happened” after losing the response to a write. A service without reconciliation must disclose that limitation.

20. **Stop cancelled backoff promptly.** Cancellation during a delay should not wait for the whole delay or issue the next request. Cancellation of local waiting does not prove server rollback. Test both cancellation-before-send and cancellation-after-acceptance.

21. **Treat reachability as a hint.** Wi-Fi can lead to a captive portal or unreachable service; a path can change after inspection. Let the actual request establish success. Avoid duplicate work from simultaneous connectivity callbacks and transport retries.

22. **Classify malformed responses separately.** A `200` with HTML, truncated JSON or an unknown required format is a protocol/decoding failure, not successful empty data. Retain safe context and cap diagnostic payload size. Do not loop retries indefinitely on deterministic malformed content.

23. **Bound memory and work.** Limit response/body sizes, active requests, queued events and retained logs. Stream large files instead of copying them into multiple byte arrays. Limits should be explicit and configurable for legitimate large-data customers.

24. **Constrain redirects and credential forwarding.** Scope bearer credentials to intended origins and test redirect behavior. Do not reattach Authorization to every redirected URL. Background transport has different redirect control; if origin restrictions are essential, choose a transfer design that can enforce them.

### Identity, persistence and streams

25. **Refresh once per credential generation.** Concurrent expired-token requests should share refresh work where the contract permits. A failed refresh must wake every waiter. A late success must not overwrite credentials installed by a newer login.

26. **Fence account switches.** Tag in-flight results with the session they belong to; discard or route old-session completions deliberately. Never insert user A's delayed result into user B's cache. Multiple simultaneous accounts need distinct stores or proven namespacing.

27. **Define logout's pending-work policy.** Tell the host whether writes are discarded, paused or completed with old credentials. Make destructive discard explicit. A generic logout helper must not claim remote revocation or secure erasure unless it performs those operations.

28. **Distinguish absent, stale and empty.** “No cached result” differs from a confirmed empty collection. Expose freshness/source metadata when caching affects correctness. A stale balance or entitlement must not look like a new server confirmation.

29. **Treat a queue as user data.** Persist atomically, cap size/age, expose pending and failed states, and define eviction. Silent deletion is unacceptable for a promised durable outbox. Best-effort analytics queues may drop data under a documented policy.

30. **Make migration failure recoverable.** Upgrade a cache schema without destroying the only unsent mutation. Re-downloadable cache can be rebuilt; pending user work needs a migration/recovery path. Test interruption and low disk space during migration.

31. **Separate transport connected from application ready.** A socket can be open before authentication/subscriptions finish. Expose readiness, reconnecting and resync-required states. Do not emit “online and current” until required synchronization completes.

32. **Handle replay gaps explicitly.** Carry sequence/cursor information where the service supplies it; detect duplicates and discontinuities. Resume from history or fetch a new snapshot when continuity expires. Reconnection alone does not imply missed events were recovered.

33. **Bound slow consumers.** Define stream buffering, dropping/coalescing and backpressure. A view that stops consuming must not leak an unbounded event queue. Financial events and replaceable presence updates need different policies.

34. **Unsubscribe when the last owner leaves.** Cancel underlying subscriptions when nobody needs them, with a documented sharing rule. Avoid one socket per screen recomposition. Keep a connection alive only if the advertised feature and host lifecycle require it.

### Optional UI and host cooperation

35. **Let the host present.** Accept the correct presentation context or composable/view controller. Do not guess a global root window. Test two scenes/windows and presentation while another sheet is active; return a recoverable busy state where necessary.

36. **Keep dismissal separate from business success.** Closing a payment or verification sheet does not establish that a server operation failed. Emit cancellation/dismissal distinctly and offer status reconciliation. Do not fire success merely because a browser returned.

37. **Validate return links.** Bind the callback to the pending session; validate scheme, host, path and state. Avoid consuming every URL the app receives. Android's deep-link security guidance requires validation and authorization beyond routing. [Android deep-link risks](https://developer.android.com/privacy-and-security/risks/unsafe-use-of-deeplinks).

38. **Own only required permissions.** Let the host explain camera, microphone or notification access at the relevant step. A headless API client should not request them. Denial should preserve a useful fallback or precise unsupported result, not restart the permission prompt indefinitely.

39. **Expose semantic appearance tokens.** Prefer text, surface, accent, error and spacing roles over arbitrary global view mutation. Maintain contrast and focus visibility across states. Full custom composition is a separate API surface with a larger support cost.

40. **Test every dismissal path.** Close button, swipe, Back, escape, outside tap and programmatic dismissal should release state consistently where supported. A hidden close icon with no accessible name is not an acceptable substitute for a clear action.

41. **Keep content usable under adaptation.** Long translations, RTL, large text, keyboard overlap and narrow/expanded windows must preserve the task. Support host locale changes when promised. Reuse platform controls where they reduce accessibility and input work.

42. **Keep UI state serializable where recovery needs it.** Rotation or activity recreation should not restart a charge, lose the operation ID or double-submit. Persist only necessary state, not an Activity/controller object. The exact mechanism differs on iOS and Android.

### Test, support and evolve

43. **Keep a shared semantic fixture suite.** Feed both platforms the same success/error/unknown-enum/null/precision cases. Compare business outcomes and wire payloads, not language syntax. This finds parity drift without forcing one implementation language.

44. **Use a controllable clock and network.** Test timeout, retry, token expiry and reconnect without real sleeps. Include dropped responses after server acceptance. Happy-path mocks that always return immediately cannot test the failure contract.

45. **Test with another SDK present.** Include representative auth, networking, analytics and UI dependencies in a host build. Shared caches, manifest merges, method swizzling and dependency versions can conflict even when each library passes its own tests.

46. **Test upgrades with old local state and old server behavior.** Fresh install alone misses migration bugs. Maintain supported client/server combinations and rollout ordering. Adding a response field is different from changing the meaning of an old field.

47. **Make a support report safe to share.** Include version/toolchain, sanitized reproduction, request ID and operation timeline. Provide private security reporting. Never ask a customer to paste bearer tokens or production personal records into a public issue.

48. **Document rollback limits before release.** A package downgrade may not reverse a DB migration or server contract change. Preserve prior artifacts and docs; explain recoverable alternatives. A major version number is a warning, not a migration plan.

## 10. Optional UI: design directions and resources

A headless SDK's primary interface is code and documentation. A visual toolkit is justified when the SaaS domain has a repeated complex user flow: checkout, identity verification, chat, subscription management. General list/form/navigation rules belong to the existing iOS/Android app reports. Do not bundle UI frameworks into a headless core just to provide screenshots.

**Fixed task flow with bounded brand customization.** Stripe's mobile Appearance API preserves layout while allowing typography, colors, shapes and selected component changes. Fit: payment/verification workflows where vendor-owned states and validation matter. Risk: customers still need an escape path for genuinely different composition. Directly inspected its published before/after screenshot: both use a white bottom sheet, close button, horizontal payment-method choices, grouped card/address fields, save-card checkbox and full-width payment button. The customized version replaces blue accents/borders with dark charcoal, pale filled fields and a pill-shaped CTA while retaining order and grouping. This demonstrates bounded theming, not tested accessibility, motion or completion quality. The pictured checkout is a vendor example, not a reviewed customer app. [Appearance API and inspected image](https://docs.stripe.com/elements/appearance-api/mobile?platform=ios).

**Composable domain UI over a state layer.** Stream's iOS docs separate SwiftUI components, UIKit components, state/controllers/offline support, theming and component substitution. Fit: a large feature such as chat whose surrounding layout belongs to the host app. Cost: more public extension points and both UIKit/SwiftUI compatibility. A composable architecture is evidence of supported customization, not proof that every customization is easy. Useful resources include the source, component docs and cookbook rather than mockup galleries. [Stream iOS documentation](https://getstream.io/chat/docs/sdk/ios/).

**Remotely configured native templates.** RevenueCat Paywalls uses an optional UI SDK plus dashboard-authored views and experiments. Its docs explicitly gate multi-step flows by SDK version and describe older-version fallback behavior. Fit: frequently tested offers; risk: remotely published configuration can reach old code. Derived guidance: version the schema, validate before publishing, preview text/accessibility states, keep bundled/cached fallback and separate rendering capability from business eligibility. Do not claim remote configuration exempts a host from store rules. [Paywall docs](https://www.revenuecat.com/docs/tools/paywalls).

**Hosted flow with native browser handoff.** Auth0 Universal Login keeps authentication pages on the authorization server and lets the SDK start/finish the redirect flow. This permits authentication-method updates without replacing every app binary; theme controls still exist. Fit: identity flows that benefit from centralized policy and browser/session behavior. Costs: redirect configuration, network availability, interruption/cancellation and restoring app state. Distinguish hosted browser flow from an embedded WebView and from native UI widgets. Auth0 states Classic Login no longer receives updates; avoid choosing it for new work without a documented requirement. These are documented capabilities; no login flow was executed. [Universal Login](https://auth0.com/docs/authenticate/login/auth0-universal-login).

UI extension contract: host chooses presentation point and navigation; vendor exposes completion/cancellation/error without assuming a global window. State who owns deep links, permissions, localization and accessibility. Test rotation, resize, keyboard, text scaling, dark/high contrast, screen readers, RTL, interrupted browser handoff and dismissal. Do not treat a screenshot as evidence those behaviors work. These are recommended acceptance tests, not observed tests of the named SDKs.

### Resource access and reuse

Directly inspected the [published Stripe appearance comparison](https://b.stripecdn.com/docs-statics-srv/assets/ios-appearance-before-after-example.ad6a9aad238be9b198e9ebbc77ebe1d4.png). This is a documentation example, not a live app audit. No motion was observed.

Stripe iOS and RevenueCat purchases-ios repositories each currently carry MIT licenses. Public docs and the referenced code are accessible without signing in; SaaS configuration/production use requires accounts and separate service terms. A code license does not itself grant reuse of every product logo, brand asset or published screenshot. Link design examples rather than treating them as a reusable asset library. [Stripe license](https://raw.githubusercontent.com/stripe/stripe-ios/master/LICENSE), [RevenueCat license](https://raw.githubusercontent.com/RevenueCat/purchases-ios/main/LICENSE).

Stream's current `stream-chat-swift` LICENSE is a proprietary source-code agreement, conditioned on being a Stream customer and not a competitor; it is not a permissive generic UI kit for another SaaS vendor. Its docs remain useful design references. Check the exact package/tag and agreement before copying components or deriving a competing SDK. [Stream license](https://raw.githubusercontent.com/GetStream/stream-chat-swift/main/LICENSE). Auth0 hosted UI is a service/reference, not a source component catalog; account and hosted customization apply. For typography, spacing, controls, motion and accessibility resources, use the [iOS design research](playbook-ios-apps.md) and [Android design research](playbook-android-apps.md). Choose a coherent host style; an API SDK does not need its own visual trend.

## 11. Named tools and libraries

This is a scoped SDK-author toolkit. App navigation, image, map, chart, purchase and animation catalogs belong to the related mobile-app reports unless the SDK itself provides that feature. More dependencies are not evidence of a better SDK.

### Apple

Owning READMEs inspected 2026-11-08; this is a relevant toolkit, not a popularity ranking. Prefer standard frameworks where they suffice. Keep test/documentation dependencies out of the shipped target. Public dependent manifests establish actual adoption, not ecosystem market share.

| Tool | Purpose, fit and alternative |
|---|---|
| Foundation URLSession | Default Apple HTTP transport with caching, delegates, background transfers and async methods. Alternative: an optional custom transport. Reuse/ownership matter. [Apple](https://developer.apple.com/documentation/foundation/urlsession). |
| Foundation Codable / JSONDecoder | Standard typed JSON mapping. Add explicit coding for schema evolution and omitted/null semantics; raw dictionaries are an escape hatch, not the whole public contract. |
| SwiftPM | Source and binary distribution; keep install instructions pinned to released versions. CocoaPods compatibility is audience-driven. |
| XCFramework | Multi-platform binary artifact when needed; test every included slice/resource. Source distribution avoids this artifact matrix. [Apple](https://developer.apple.com/documentation/xcode/distributing-binary-frameworks-as-swift-packages). |
| Swift OpenAPI Generator | Plugin/CLI for OpenAPI clients and servers; typed payloads and streaming. Generated code is transport-decoupled. Use with a trustworthy spec; it does not design auth/retry/lifecycle policy. [Owning README](https://github.com/apple/swift-openapi-generator). |
| swift-openapi-runtime | Runtime required by generated code; a separate runtime version is another compatibility axis. [Generator ecosystem](https://github.com/apple/swift-openapi-generator). |
| swift-openapi-urlsession | URLSession transport for that generator. Avoid pulling server-side NIO transport into a normal iOS SDK without a reason. [Generator ecosystem](https://github.com/apple/swift-openapi-generator). |
| Swift HTTP Types | Shared HTTPRequest/HTTPResponse/HTTPFields, plus Foundation bridges. Useful transport boundaries; ordinary URLRequest may suffice for a small SDK. Used in inspected Supabase manifest. [Repository](https://github.com/apple/swift-http-types). |
| Alamofire | MIT networking layer with interceptors, retries, uploads and progress. Useful when those facilities replace substantial code; extra dependency/version surface for a plain wrapper. Its README separates supported Apple systems from builds on unsupported platforms. [Repository](https://github.com/Alamofire/Alamofire). |
| AppAuth-iOS | OAuth/OIDC flow library; use browser-based native flow where applicable. Alternative: carefully implemented AuthenticationServices integration for narrower needs. [Repository](https://github.com/openid/AppAuth-iOS). |
| Swift DocC / DocC plugin | Symbol reference, tutorials and static web publishing. Apple uses DocC extensively. Pair with task guides, troubleshooting and migration docs; reference generation alone is insufficient. [Repository](https://github.com/swiftlang/swift-docc). |
| Mocker | URLSession/Alamofire request interception for deterministic tests. Avoid leaking global stubs across parallel tests; injectable instance transport is an alternative. Present in Supabase's tagged test dependencies. [Repository](https://github.com/WeTransfer/Mocker), [consumer manifest](https://github.com/supabase/supabase-swift/blob/v2.55.5/Package.swift). |
| SnapshotTesting | MIT snapshots for views, requests and Encodable output. Good request-contract/UI regression aid; fixed simulator required for image comparisons. Add to test targets only. Present in Supabase tests. [Repository](https://github.com/pointfreeco/swift-snapshot-testing). |
| swift-clocks | Injectable clocks for deterministic timeout/retry tests; present in Supabase runtime helpers. An owned clock closure suffices for small clients. [Consumer manifest](https://github.com/supabase/supabase-swift/blob/v2.55.5/Package.swift). |
| swift-concurrency-extras | Concurrency helpers present in Supabase; only adopt for a needed mechanism. Avoid turning “used by Supabase” into mandatory architecture. [Consumer manifest](https://github.com/supabase/supabase-swift/blob/v2.55.5/Package.swift). |
| XCTest / Swift Testing | Native tests; run consumer projects as well as package tests. Swift Testing's availability is a build-tool floor to document, not necessarily an SDK runtime floor. |
| Instruments / Xcode Memory Graph | Profile startup, allocations, retained clients and sockets in a host app. A unit-test pass cannot establish low overhead. |

### Android

The catalog identifies relevant choices, not measured popularity. Repository existence, named usage and documented platform support are the evidence. Keep production dependencies separate from authoring/test tools.

| Tool | Fit and alternative | Constraint/evidence |
| --- | --- | --- |
| OkHttp | Mature Android/JVM HTTP transport; use direct requests for a small SDK | Pooling, compression, caching, HTTP/2; Apache-2.0. Avoid a new client per request; examine SDK vs host-client ownership. [Docs](https://lysine.dev/okhttp/). |
| Retrofit | Annotated service interfaces over OkHttp; optional when direct client code is clearer | Current README: Java 8/API 21+, included R8 rules, Apache-2.0. Do not expose Retrofit types in the public SDK unless intentional. [Repo](https://github.com/lysine-dev/retrofit). |
| Ktor Client | KMP transport abstraction and plugins | Engine features/OS floors differ; KMP callers need correct artifacts. Explicit engine selection reduces surprises when several are present. [Engine docs](https://ktor.io/docs/client-engines.html). |
| kotlinx.serialization JSON | Kotlin/KMP serialization with generated serializers | JSON stable; other format libraries remain experimental in current docs. Runtime library versioning is separate from Kotlin. [Docs](https://kotlinlang.org/docs/serialization.html). |
| Moshi | Java/Kotlin JSON; generated Kotlin adapters | Java reflection alone does not support Kotlin models. Codegen or Kotlin adapter required; reflective models need keep rules. Apache-2.0. [Repo](https://github.com/square/moshi). |
| kotlinx.coroutines | Suspend/Flow primitives; test support and adapters | Stable public APIs have compatibility promises; internal/experimental APIs do not. Apache-2.0. Do not export internal coroutine machinery. [Repo](https://github.com/Kotlin/kotlinx.coroutines), [policy](https://github.com/Kotlin/kotlinx.coroutines/blob/master/docs/topics/compatibility.md). |
| WorkManager | Optional persisted jobs/queue adapter | Adds storage/scheduling behavior; inappropriate for every immediate call. See the platform-specific sources in §3. |
| App Startup | Optional coordinated initialization | Prefer explicit init for simple clients; allow disabling automatic startup. Platform source above. |
| Android Keystore | Protect locally used encryption keys | Device/algorithm/auth constraints; not a complete token/session policy. Platform source above. |
| AppAuth-Android | OAuth/OIDC authorization flows | Uses external user agent/custom tabs; follows RFC 8252 and PKCE rather than embedded WebView login. Apache-2.0; integrates standard providers, not arbitrary SaaS identity semantics. [Repo](https://github.com/openid/AppAuth-Android). |
| Dokka | API reference from Kotlin/Java comments | Supports KDoc/Javadoc; used by coroutines, Ktor, OkHttp. Generated reference complements task guides. [Docs](https://kotlinlang.org/docs/dokka-introduction.html). |
| Kotlin Gradle ABI validation | Compare committed ABI dumps | `checkKotlinAbi`/`updateKotlinAbi`; per-module setup. Check selected KGP's API stability. Existing binary-compatibility-validator plugin is an alternative. [Docs](https://kotlinlang.org/docs/gradle-binary-compatibility-validation.html). |
| Android Lint | API checks and SDK-specific integration diagnostics | Tests and Lint version compatibility needed; package through `lintPublish`. Platform guide above. |
| MockWebServer | Test HTTP interactions without live service | Part of OkHttp; test retry, body, headers, errors, disconnects. A mock cannot prove server contract equivalence. [OkHttp docs](https://lysine.dev/okhttp/). |
| kotlinx-coroutines-test | Virtual time and controlled scheduling | Useful for timeout/cancellation/retry tests; still need real transport integration tests. [Repo](https://github.com/Kotlin/kotlinx.coroutines). |
| Turbine | Assert Flow emissions/completion/error | Small Apache-2.0 test library; makes stream tests readable. Current README warns it depends on an unstable coroutines test API. [Repo](https://github.com/cashapp/turbine). |
| Robolectric | JVM tests exercising Android behavior | Fast local lifecycle/resource tests; shadows/simulated hardware cannot certify real devices. [Docs](https://robolectric.org/). |
| AndroidX Test, AndroidJUnitRunner, Espresso, UI Automator | Instrumented host and optional UI tests | Device/runtime coverage; slower than pure JVM tests. Test API with real consumer rather than mocks mirroring SDK internals. [Docs](https://developer.android.com/training/testing/instrumented-tests/androidx-test-libraries/test-setup). |
| Build-managed devices | Reproducible emulator/device matrices in Gradle | Current documented virtual feature floor API 27; older claimed SDK runtime floors need another test lane. [Docs](https://developer.android.com/studio/test/managed-devices). |
| Maven Publish / Maven Central | Artifact/POM distribution | Repository metadata beats loose AAR; signatures, source/docs and controlled namespaces aid inspection. Publication sources above. |
| Gradle dependency verification | Verify dependency checksums/signatures | Supply-chain control for SDK author builds; does not prove a dependency is safe. [Gradle docs](https://docs.gradle.org/current/userguide/dependency_verification.html). |
| APK Analyzer / R8 Configuration Analyzer | Inspect shipped footprint, native code and keep-rule impact | Measure incremental release cost in a host; AAR size alone is misleading. [16 KB guide](https://developer.android.com/guide/practices/page-sizes), [Play optimization guide](https://support.google.com/googleplay/android-developer/answer/17492799). |

**Ownership change verified.** Old `square/okhttp` and `square/retrofit` GitHub links redirect to `lysine-dev`. On 2026-06-17 maintainer Jake Wharton announced OkHttp, Retrofit and Okio moving, alongside SQLDelight joining Commonhaus. Current docs are under `lysine.dev`; existing Retrofit coordinates remain `com.squareup.retrofit2:retrofit` in its README. Do not invent a coordinate migration from the ownership change. [Maintainer announcement](https://jakewharton.com/the-lysine-contingency/), [Retrofit repo](https://github.com/lysine-dev/retrofit).

### Shared contract and release tools

| Tool | Fit, limits and alternatives |
|---|---|
| oasdiff | OpenAPI breaking-change and full-diff checks; useful before regenerating clients. Does not detect undocumented behavior changes or prove generated source compatibility. Pair with old-client tests. [Repository](https://github.com/oasdiff/oasdiff). |
| Spectral | JSON/YAML rulesets for OpenAPI and related API descriptions; enforce descriptions, conventions and schema consistency. Select rules suited to the existing API rather than importing a blanket REST style. Public company rulesets demonstrate use, not measured market share. [Repository](https://github.com/stoplightio/spectral). |
| Prism | OpenAPI mock server and validation proxy; useful for request/response contract tests. A mock derived from the same wrong schema as the SDK can pass while production fails; include real service tests. [Repository](https://github.com/stoplightio/prism). |
| Apollo iOS / Apollo Kotlin | Generated operation models, transports and optional caches for existing GraphQL APIs. Preserve partial errors and choose cache ownership deliberately; not a reason to replace a JSON/RPC service. See §2. |
| GitHub Actions artifact attestations | Build/source provenance and SBOM attestations for released artifacts; access/plan limits apply. Integrity evidence complements code review and release tests. See §2. |
| OpenAPI Generator, Fern, Speakeasy | Generation alternatives with language-specific maturity, ownership and commercial limits; compare concrete output. See §5 rather than treating “supports SDKs” as an Android/iOS guarantee. |

Keep authoring tools out of consumer runtime dependencies. For each adopted tool, pin the release, read its license and inspect generated-output terms separately from the generator's license. Hosted-service pricing and source availability do not imply the same redistribution rights.

## 12. Named choices to avoid, migrate or constrain

### Apple

| Choice | Status, consequence, replacement, exception |
|---|---|
| AFNetworking for new work | Deprecated and archived January 17, 2023; no further releases. Maintainers suggest Alamofire for modern Swift. URLSession is another fit for a small client. A maintained private fork can serve a legacy Objective-C integration, with explicit ownership. [Owning repository](https://github.com/AFNetworking/AFNetworking). |
| AWS SDK for iOS for new integrations | End of support August 1, 2026; repo archived August 3. Owner recommends Amplify for Swift with migration guide. Existing AWS services need an API-by-API migration check; replacement is not necessarily drop-in. Do not confuse legacy SDK with the separate AWS SDK for Swift. [Owning repository](https://github.com/aws-amplify/aws-sdk-ios). |
| CocoaPods trunk as sole future delivery | Scheduled freeze December 2, 2026. SwiftPM primary; private spec repo or vendored path may be transitional options. Existing versions do not stop installing. [Owning announcement](https://blog.cocoapods.org/CocoaPods-Specs-Repo/). |
| Binary-only packaging by default | Not deprecated; unsuitable when no requirement offsets slice/signing/debugging maintenance. Legitimate for closed IP or measured build-time needs. [Apple binary guide](https://developer.apple.com/documentation/xcode/distributing-binary-frameworks-as-swift-packages). |
| Mandatory reactive/UI framework for plain API calls | Contextual avoidance, not a deprecation claim. Prefer async core and optional adapters unless supported customers need that framework. The public dependency locks consumers into another compatibility surface. |
| Global mutable auth/session/fixture registries | Contextual avoidance. Per-instance dependencies improve multi-client isolation; release-noted leaks and test-state bleed show the practical risk. A documented process-wide coordinator can still be necessary for platform-specific workflows. [Supabase release](https://github.com/supabase/supabase-swift/releases/tag/v2.55.0). |

### Android

| Choice | Status and affected use | Better path / exception |
| --- | --- | --- |
| Gson as default in new Kotlin Android SDK | Current maintainer README: maintenance mode; Kotlin non-null/default constructor semantics unsupported; not recommended for Android because reflection conflicts with optimizers | Prefer generated kotlinx.serialization or Moshi adapters. Existing Java integrations with explicit adapters/tests may remain viable; maintenance mode is not abandonment. [Gson](https://github.com/google/gson). |
| AWS Mobile SDK for Android | Maintenance began 2025-08-01; scheduled EOS 2026-08-01 has passed as of this report | Owner recommends Amplify Android and migration guide. Existing deployments need planned migration; do not claim endpoints stopped working on EOS. [AWS docs](https://docs.amplify.aws/gen1/android/sdk/). |
| Firebase `*-ktx` modules | No new releases since July 2025; removed from BoM 34.0.0 | Use Kotlin APIs now in main modules. Existing versions still function; this is not a rejection of KTX generally. [Firebase migration](https://firebase.google.com/docs/android/kotlin-migration). |
| AndroidX `security-crypto` as a new default | All APIs deprecated during 1.1.0 development (April/June 2025); stable 1.1.0 July 2025 | Existing platform APIs/direct Android Keystore per owner. Design a tested storage migration; do not delete encrypted data or replace it with plaintext. [Release notes](https://developer.android.com/jetpack/androidx/releases/security). |
| Blindly adopting newest RxJava major | Current default branch plans 4.0.0 for 2026-11-30 and describes a Java 26 implementation; explicitly says Android compatibility depends on API level/desugaring. It is not evidence of a released Android-ready upgrade | Prefer suspend/Flow for new Kotlin-only core; if customers use RxJava, publish a version-specific optional adapter. Verify actual artifact/runtime requirements. This is fit guidance, not a claim RxJava is abandoned. [Repo](https://github.com/ReactiveX/RxJava). |
| `-dontoptimize`, global rules, keep-everything consumer rules | Host-wide cost and possible store optimization conflict | Narrow rules/codegen plus minified consumer tests. Short-term emergency workaround must have an SDK fix. [Library guidance](https://developer.android.com/topic/performance/app-optimization/library-optimization). |
| Loose AAR as sole delivery | No transitive identity/version/dependency metadata | Maven repository; zipped Maven layout for restricted environments. [Publication guide](https://developer.android.com/build/publish-library/upload-library). |
| Mandatory Compose/DI/analytics for headless requests | Unnecessary API/build/privacy coupling for this scope | Optional modules/adapters. Appropriate when providing a complete domain UI with explicit requirements; no universal prohibition. Research inference from modular examples and host constraints. |

### Cross-platform

OpenAPI Generator `swift5`, the unmaintained public Fern generator, Alpha Swift export, retired Atlas Device Sync and App Center services have distinct limits described in §§5 and 8. Do not collapse deprecation, unsupported use, a commercial successor and a service shutdown into “abandoned.” A functioning older client may need a planned migration rather than an immediate rewrite.

## 13. Prioritized build guidance

### First: prove one safe, useful integration

1. **Choose a real customer task and its authority boundary.** Inventory the existing API. Identify client-safe calls, backend-only calls and missing server guarantees. Produce one short flow that reaches a useful outcome; do not start by generating every endpoint. Stripe's key split and the idempotency cases explain why this precedes mobile packaging.
2. **Write the Swift and Kotlin call sites before the implementation.** Include success, cancellation, invalid credentials and a timed-out mutation. Review from a consumer app. Decide which public types and extension points you can support for years. Share semantics and fixtures; permit language-specific syntax.
3. **Implement a small core.** Typed models, instance configuration, transport/credential seams, explicit errors, bounded timeouts and safe retry policy. Start with platform networking or a justified small library. Avoid UI, a persistent database, auto-telemetry and background workers until the task needs them.
4. **Ship the actual integration package internally.** SwiftPM and Maven metadata, matching docs, one minimal host per platform, release resource/privacy checks, optimized Android build and supported compiler lanes. Artifact testing addresses the packaging and shrinking failures in §§3–4.
5. **Observe fresh integrators.** Give them the released package and docs, then watch where they stop. Record setup effort, first domain result, help needed and error diagnosis. A successful internal demo is not independent onboarding evidence.

### Before a public stable release

Publish scope, supported targets, public API policy, safe credential setup, data inventory, license/service terms, versioned task docs, migration guide, security contact and support ownership. State retry/timeout/cancellation semantics and optional cache/queue behavior. Verify old SDKs against the next server rollout. Keep an incident path that works even when the SaaS API is down.

Choose a small number of supported configurations and exercise them consistently. Do not publish an enormous matrix whose rows only compile. If customers require Objective-C, Java, extensions, non-Google devices or custom endpoints, give each an explicit consumer fixture and owner.

### Add differentiators when repeated customer work justifies them

| Differentiator | Evidence that it is worth building | Cost to accept |
|---|---|---|
| Workflow helper | Several integrators implement the same fragile multi-call sequence | Stable state machine, reconciliation and upgrade semantics |
| Domain UI | Customers repeatedly rebuild validation, handoff and accessibility for the same task | Localization, platform adaptation, theming and interrupted-flow recovery |
| Offline outbox | Customers need work to survive disconnection/process death | Durable storage, conflict/expiry policy, migration and user-visible failures |
| Realtime state layer | Customers need continuity and shared subscriptions, not only a socket | Replay gaps, buffering, reconnect, identity and lifecycle ownership |
| Generated large API surface | Manual models/endpoints drift frequently and the schema is reliable | Generator/runtime upgrades, public API review and semantic fixtures |
| Shared KMP core | Substantial duplicated domain/protocol logic changes together | Swift facade, artifact distribution, runtime footprint and interop testing |
| Custom Lint / integration validator | A repeated setup mistake is costly and statically detectable | Build-tool compatibility and test maintenance |

### Costly traps

Do not expose a server admin SDK as a mobile SDK; hide ambiguous mutations; force one global client; bundle unrelated analytics; promise offline durability with an in-memory retry; require a host rewrite to match your architecture; ship only debug-tested artifacts; or replace a mature client's public API solely to make generation easier. Do not treat a commercial generator, KMP, a binary framework or an SDK UI kit as automatically wrong. Each needs a concrete benefit and an owned support boundary.

A remote kill switch can disable optional behavior or stop harmful retries, but must have a safe local default and a parser independent of the failing feature. It cannot repair already-crashing launch code if evaluating the switch requires that code. Authentication and authorization must remain fail-closed; “keep the host alive” does not mean pretending a payment or login succeeded. Firebase's incident in §3 motivates this distinction.

### Experiments that resolve actual choices

- Compare handwritten and generated implementations of the same difficult operation: null/omitted fields, unknown enums, errors and cancellation. Inspect call-site clarity, diff noise, artifact size and upgrade work.
- Compare native clients and a KMP core using a real stateful workflow if sharing is under consideration. Measure host build/install/runtime costs, not only lines of shared code.
- Run onboarding sessions with fresh iOS and Android developers. Separate time waiting for account approval/backend setup from SDK work, while counting both in total integration time.
- Pilot an optional UI flow against customers' existing integration. Measure completion, abandonment, accessibility defects, localization work and support effort. Do not import web payment conversion percentages as a forecast.
- Rehearse a failed release: bad optional remote config, exhausted rate limit, expired certificate/pin, auth service outage and unsupported older client. Confirm diagnosis, mitigation and customer notice paths.

These experiments are proposed next implementation work, not tests performed during this research.

## 14. Release test protocol and performance budgets

### A compact representative matrix

| Lane | Minimum useful exercise | What a pass establishes |
|---|---|---|
| Swift consumer | Oldest supported Xcode/compiler plus current stable; SwiftUI and UIKit hosts where relevant | Advertised source compatibility and public API usability for those configurations |
| Apple artifact | Release archive, resources/privacy report, binary slices/signature where applicable | Actual delivery works in a consuming archive; not App Review approval |
| Kotlin/Java consumer | Supported Kotlin/AGP/Gradle/JDK boundaries; Java fixture if promised | Consumer compatibility, separate from producer build success |
| Android optimized host | R8, obfuscation and resource shrinking enabled; key flows executed | Optimized code/resources survive; debug-only tests do not substitute |
| Dependency coexistence | Host already includes representative networking/auth/analytics dependencies | Detects the tested graph/global-state conflicts; not every possible combination |
| Old installed state | Upgrade supported stored data/queue; test failed migration and rollback limits | Stated persistence evolution behavior |
| Real devices | Oldest supported OS profile and current OS; low-resource hardware; non-Google/native page-size cases where promised | Relevant runtime behavior beyond simulator/JVM mocks |
| Server rollout | Old supported SDK artifacts against new server/config plus new SDK against supported server variants | Wire/semantic compatibility for the tested operations |
| UI adaptation | Screen reader, large text, RTL, keyboard, dark/high contrast, resize, browser return/cancel | Promised UI task remains usable in exercised states |

### Failure fixtures with explicit expected outcomes

| Scenario | Required assertion |
|---|---|
| Response lost after mutation accepted | Retry/reconcile does not create a second logical operation; uncertainty remains visible when server lacks a guarantee |
| Twenty concurrent expired-token calls | Refresh policy is coordinated; all waiters finish; logout/new-login generation cannot be overwritten |
| Cancellation during backoff or decoding | No later retry; resources released; no misleading server-rollback claim |
| Unknown enum, new property, missing field, explicit null | Forward-compatible fields survive; invalid required data fails clearly; patch intent is preserved |
| Empty page with continuation; repeated/expired cursor | Iterator follows the contract, detects pathological loops and permits recovery |
| Large body, slow consumer, disk full | Memory/disk remain bounded; promised durable work is not silently discarded |
| Background, process death, screen lock, force quit | Behavior matches platform limits and advertised persistence; restart recovers by stable IDs where supported |
| Account/tenant/environment switch during request | Old data and tokens do not enter the new session; pending-work policy is honored |
| Malformed optional remote configuration | Host remains usable with safe defaults or feature unavailable; security-sensitive failures remain explicit |
| Telemetry disabled or consent withdrawn | Optional collection stops as documented; queue disposal and network behavior match the policy |
| Release artifact installed from clean cache | Imports, dependencies, resources, docs and signatures/checksums work without source-workspace shortcuts |

### Measure integration overhead separately

Measure package-fetch size, dependency count, clean/incremental build time, installed/download app-size delta, linked-but-unused startup, initialized startup, first-call latency, steady memory, memory growth across disposal cycles, idle connections, background wakeups and network bytes. Use a minimal release host with and without the SDK, then a realistic host. Report device, OS, compiler, package version and configuration with each number.

Set budgets from the customers' use case. A chat engine and a ten-endpoint API wrapper cannot share one sensible size or battery budget. Public issue measurements are useful leads, not universal baselines. This report supplies no invented “under 1 MB” or “under 10 ms” target. Battery and long-run lifecycle behavior require device experiments; public docs and screenshot inspection cannot establish them.

Release the bytes that passed the consumer tests. Record source revision and generator/options, review the public API and dependency/permission/data-collection diff, stage artifacts, run external-host tests, then publish immutable versions. Maintain a security and compatibility response path for supported versions. Backend/config deploys need the same old-client fixtures as SDK releases.

## 15. Sources, evidence and scope limits

Sources are linked beside each claim. Research checked owning docs, source/manifests, tagged releases, issue reports and incident corrections on 2026-11-08. Moving branches and policy pages remain changeable; their values are dated observations. Reported bugs are bounded to the stated versions and evidence. A closed issue, a promised fix and a tested fixed release are different claims.

| Source group | What it establishes | What it cannot establish |
|---|---|---|
| IETF RFCs; Google AIPs | Protocol semantics, security practice, compatibility examples | One service's implementation or every SDK's correctness |
| Apple/Android/Kotlin/Swift docs | Platform behavior, distribution and language/tool constraints | Customer-specific compatibility without consumer tests |
| SDK source, tags and migration guides | Public API, dependencies, support statements, shipped changes | Defect-free behavior, market share or low runtime overhead |
| GitHub issues and owner postmortems | Concrete failure reports, fixes and incident chronology | Prevalence from issue counts; latest-version failure without evidence |
| API-learning research | Survey findings and documentation-use correlations with stated methods | Causal mobile SDK conversion or financial return |
| Vendor case studies and pricing | Published customer claims, product economics and dated pricing models | Audited profit, general lift or an identical future quote |
| Published UI screenshot | Visible structure, spacing, color and bounded customization | Motion, screen-reader behavior, task completion or live-app quality |

Primary reading routes: [native OAuth](https://www.rfc-editor.org/rfc/rfc8252), [OAuth security](https://www.rfc-editor.org/rfc/rfc9700), [API compatibility](https://google.aip.dev/180), [Swift API design](https://www.swift.org/documentation/api-design-guidelines/), [Kotlin library evolution](https://kotlinlang.org/docs/api-guidelines-backward-compatibility.html), [Apple SDK distribution/privacy](https://developer.apple.com/support/third-party-SDK-requirements/), [Android library release preparation](https://developer.android.com/build/publish-library/prep-lib-release), [API-learning study](https://www.microsoft.com/en-us/research/publication/field-study-api-learning-obstacles/), [documentation-use paper](https://cmustrudel.github.io/papers/chi2024doc_logs.pdf). The detailed chapters give narrower sources for individual claims and tool choices.

The report adapts all requested research areas to an SDK component: developer experience replaces ordinary home/list/settings screens; optional domain UI gets scoped design coverage; adoption/support economics replace app-store ranking. Whole-app visual trends, general app purchases, full app feature catalogs and unrelated platform integrations remain in [iOS apps](playbook-ios-apps.md) and [Android apps](playbook-android-apps.md). No universal independent “best SDK” ranking is supportable from vendor examples and issue reports. Concrete strengths and weaknesses are more useful.

Causal SaaS activation/profit effects, account-specific publishing quotes, unresolved vendor language-maturity claims and actual device/performance results are qualified beside the affected claims. Those limits prevent universal numeric forecasts and compatibility promises; they do not prevent the practical build guidance above.
