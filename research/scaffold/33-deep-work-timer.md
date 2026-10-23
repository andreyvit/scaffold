# Deep Work Timer / Buddy

Question entering: does a small personal app need the server architecture?

Source: `~/Developer/andreyvit/DeepWorkTimer` at `d3bc1a45b0da025f3c8bc49d489e1b48d2227317` (2024-12-03). 72 eligible commits, all Andrey. Sampled model, presentation, storage, analytics and release changes.

## Code inferences
- Keep domain state separate from platform effects. `Source/Model/State.swift`; `Source/Presentation/AppModel.swift`.
- One mutation path updates state, saves it, adjusts timers and emits effects. `AppModel.mutate`.
- Persist enough state to resume; retain old decoding keys. `Source/Model/Memento.swift`.
- Spend resources according to activity: different timer frequencies/tolerances for active and idle use. `AppModel.setUpdateTimerFrequency`.
- Local feature counters can exist without a remote analytics SDK. `Source/Application/Analytics.swift` only uses UserDefaults; do not infer a universal privacy policy.
- Platform improvements can remove custom infrastructure: `9eada8f` adopts SMAppService; `e9a9bfa` deletes helper app (224 lines removed).

## Written choice
README describes a paid app built in public with user modification rights and an abandonment clause. Ownership and control may apply to customers too; this license is not a general licensing decision.

## Questions after
- Is local state + optional sync the productivity-app default?
- Which state must survive restart? What can safely reset?
- Who uses feature metrics: the user, support, or product team?
- How much OS backward compatibility is worth retaining custom code?

Limit: this is a macOS app, not evidence of iOS architecture. `Store.swift` includes unfinished behavior; implementation presence is not proof of correctness.
