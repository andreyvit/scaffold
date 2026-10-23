# Modern options: first scan

Checked 2026-10-18. External evidence about capabilities, **not evidence of Andrey’s values**. Native per-platform implementation was subsequently chosen in this chat (C7). Exact native framework choices and production validation remain open.

## Web
- Turbo keeps the browser process alive across navigation and caches pages. Rich widgets need deliberate teardown/restoration; bundles need deployment compatibility. [Turbo handbook](https://turbo.hotwired.dev/handbook/building).
- React supports a component inside an existing page, or a whole subroute. This makes it a candidate for both requested alternatives. [Incremental React](https://react.dev/learn/add-react-to-an-existing-project).
- A Vite-style client build leaves routing, data loading and caching choices to us. React recommends frameworks for integrated needs; keeping a separate Go server is a deliberate tradeoff to evaluate. [React from scratch](https://react.dev/learn/build-a-react-app-from-scratch).

## Native mobile
- **iOS candidate:** SwiftUI with explicit observable state ownership; UIKit where needed. Apple documents State/Environment/Observation and supported UIKit bridges. This is no proof that one MV* pattern fits every screen. [Model data](https://developer.apple.com/documentation/swiftui/model-data), [UIKit integration](https://developer.apple.com/tutorials/swiftui/interfacing-with-uikit).
- **Android candidate:** Compose, data/UI separation, one-way state flow, lifecycle-aware collection and screen state holders. Android recommends repositories, an extra domain/use-case layer for complexity/reuse, and permits manual dependency wiring in simple apps. Its “optional domain layer” does not mean business rules belong in UI. [Architecture recommendations](https://developer.android.com/topic/architecture/recommendations).
- **Offline:** cached reads and queued writes are separate designs; synchronization needs conflict and retry policy. [Android offline guide](https://developer.android.com/topic/architecture/data-layer/offline-first).

## Sharing options — historical scan, no longer candidates
| Option | Documented mechanism | Still needs proof |
|---|---|---|
| Kotlin shared logic, native UI | Native SwiftUI can sit above shared Kotlin. [JetBrains](https://blog.jetbrains.com/kotlin/2026/05/new-kmp-default-structure/) | Swift ergonomics, concurrency, build/debug cost |
| Compose shared UI | SwiftUI/Compose can embed each other through platform bridges. [Integration](https://kotlinlang.org/docs/multiplatform/compose-swiftui-integration.html) | Accessibility, text/editing, navigation, native feel |
| React Native | React components map to native components; custom native components remain possible. [Components](https://reactnative.dev/docs/intro-react-native-components) | Library upkeep, native escapes, startup and complex interactions |
| Flutter | Own widget/rendering architecture with platform integration. [Architecture](https://docs.flutter.dev/resources/architectural-overview) | Platform fidelity, integrations and maintenance fit |
| Hotwire Native | Web content within native navigation, with native extensions. [Overview](https://native.hotwired.dev/overview/how-it-works) | Offline needs and whether the product feels right |

Retained as research history. C7 chooses native APIs and duplicated implementation; do not run this comparison unless Andrey explicitly reopens it.

## Identity and security
- Passkeys are a serious login candidate; Apple and Android provide platform APIs. They do not decide account ownership or recovery. [Apple](https://developer.apple.com/passkeys/), [Android Credential Manager](https://developer.android.com/identity/credential-manager).
- Recovery is part of the security boundary; a weak fallback can defeat strong login. Prefer a maintained server implementation over inventing protocol handling. [OWASP passkeys](https://cheatsheetseries.owasp.org/cheatsheets/Passkey_Security_Cheat_Sheet.html).
- Enforce resource authorization on every relevant request, with deny-by-default behavior. Authentication alone is insufficient. [OWASP authorization](https://cheatsheetseries.owasp.org/cheatsheets/Authorization_Cheat_Sheet.html).
- Diagnostic/security events need deliberate fields and protection; secrets and sensitive payloads do not belong indiscriminately in logs. [OWASP logging](https://cheatsheetseries.owasp.org/cheatsheets/Logging_Cheat_Sheet.html).

## Research after scope selection
Swift concurrency and persistence; Android process death/navigation/storage; shared-code interop; client/server version skew; push/background work; accessibility/localization; app-store release constraints; passkey/federation/recovery threat models; frontend composition and asset delivery.

Use current official docs plus small executable comparisons. No old source code or vendor example alone chooses the recipe.
