# Accounts: decisions before implementation

Identity/profile default confirmed; other choices remain exploration. [Identity decision and reasons](82-identity-and-profiles.md). [Happy Grid](10-happy-grid.md) has product-specific identity rules; do not silently generalize them.

| Decision | Options | Ask |
|---|---|---|
| Need an account? | Convenience favors use before login; **signup timing follows business funnel and measurement** | What monetization/conversion hypothesis sets the gate, and how will it be tested? |
| Data owner | **Same workspace/account model for individuals and companies**; individual owns personal workspace | Who keeps data when a member leaves? |
| Person across companies | **Default: shared login + per-company profiles**; separate logins supported internally | What product requirement justifies a different default? |
| Customer vs staff | **Deferred; no selected default** | Revisit company ownership/deletion and surface overlap after Andrey has reflected. |
| Joining | Self-signup; invitation; enterprise provisioning | Who may create, join or claim a company? |
| Login | Passkeys; federation; passwords; email link/code; host session | Which users/devices/hosts must work? What is the fallback? |
| Enterprise identity | Optional federation; enforced SSO; provisioning/deprovisioning | Who is authoritative, and how fast must removal take effect? |
| Extra assurance | Normal login; step-up; stronger admin policy | Which actions merit renewed proof? What assurance does a passkey actually provide? |
| Recovery | Spare credentials; provider recovery; recovery codes; assisted recovery | What happens after losing every device/provider? Who may override? |
| Authorization | Ownership + simple roles; object sharing; attribute/relationship rules | Which user/action/resource combinations must differ? |
| Session | Server session; scoped API token; host-bound session | Need immediate revocation, third-party clients or distributed verification? |
| Lifecycle | Rename; merge; transfer; suspend; delete/export | Which operations preserve history and which must sever access? |

## Candidate starting branches
- **Consumer:** personal workspace owned by the individual (confirmed); optional login when useful and passkeys/federation remain proposals.
- **B2B:** company-owned data; explicit membership; lifecycle and SSO rules chosen together.
- **Embedded:** follow the host’s identity contract; test host logout and revocation.

Not approved: treating the identity default as universal, exposing multi-login UI in every product, passkeys-only recovery, custom cryptographic protocols, or “admins bypass everything.”

## Required proof in the eventual recipe
Cross-tenant denial; removed-member access; recovery abuse; credential changes; session revocation; safe audit detail; signup/login/recovery outcome metrics. Exact implementation follows [modern security research](76-modern-options.md).
