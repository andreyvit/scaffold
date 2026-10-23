# Sarekon iOS and Android

Question entering: how should server-backed mobile handle stale data, account changes and uneven device support?

## iOS evidence
Repo `~/Developer/sarekon/sarekon-consumer-ios`; snapshot `dd19a022899023b7e223127556366903cf1336f9` (2025-01-03). 202/283 eligible commits Andrey.

- Separate usable data from latest fetch status. Authored `Source/Model/ServerValue.swift` (595 lines) models refresh reasons, retries, cancellation and successful data separately.
- Keep loaded content visible after a refresh fails: `d0c8fd99d132848735f145b6a377659ea6ad3f03`.
- Clear identity-dependent cache on impersonation change: `c2ae8245948e194056c3d8b1cecd2fd1f180a2b5`.
- Use data-specific refresh policies: authored `Source/Model/Repository.swift` (991/992 lines Andrey).
- Device capabilities and missing data need explicit behavior; sampled commit history identifies further cases, not all reviewed.

## Android evidence
Repo `~/Developer/sarekon/sarekon-consumer-android`; 78/343 eligible commits Andrey. Selected diffs only; do not attribute its Rx/ViewModel architecture to him.

- Refresh vehicles after impersonation: `8a7adbb92fd872179dc8777298dca91738718519`.
- Increase the settings hit target while preserving icon size: `8e9486f2bcc6f32cfdf4244af55744ae0c6a182d`.
- Remove Firebase Analytics, keep Crashlytics: `7a1c2f707f3dd62e12e42bf87b72693e64eef9e3`, `44daf56ed0f22f288cf64a75e87ed80a6940caa4`. Reason not stated; no privacy motive inferred.

## Questions after
- Is stale-but-usable data the default? When is it dangerous?
- What must be cleared or canceled on logout/tenant switch?
- Which refresh policies should be shared, and which remain feature-specific?
- Why was analytics removed: privacy, noise, cost, policy or lack of use?
- What should identical behavior across platforms mean when native conventions differ?

Duplicate checkouts under `sarekon-consumer-native` share histories; not independent evidence.
