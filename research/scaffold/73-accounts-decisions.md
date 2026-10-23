# Accounts: decisions before implementation

Identity/profile default confirmed; other choices remain exploration. [Identity decision and reasons](82-identity-and-profiles.md). [Happy Grid](10-happy-grid.md) has product-specific identity rules; do not silently generalize them.

| Decision | Options | Ask |
|---|---|---|
| Need an account? | Convenience favors use before login; **signup timing follows business funnel and measurement** | What monetization/conversion hypothesis sets the gate, and how will it be tested? |
| Data owner | **Same workspace/account model for individuals and companies**; individual owns personal workspace | Who keeps data when a member leaves? |
| Person across companies | **Default: shared login + per-company profiles**; separate logins supported internally | What product requirement justifies a different default? |
| Customer vs staff | **Deferred; no selected default** | Revisit company ownership/deletion and surface overlap after Andrey has reflected. |
| Joining | Self-signup; invitation; enterprise provisioning | Who may create, join or claim a company? |
| Login | **Email code initially when email is available; passkeys offered from the start (C71)**; other methods product-specific | Enrollment, recovery and stronger company requirements |
| Enterprise identity | Optional federation; enforced SSO; provisioning/deprovisioning | Who is authoritative, and how fast must removal take effect? |
| Extra assurance | Normal login; step-up; stronger admin policy | Which actions merit renewed proof? What assurance does a passkey actually provide? |
| Recovery | Spare credentials; provider recovery; recovery codes; assisted recovery | What happens after losing every device/provider? Who may override? |
| Customer-data access | **Superstaff allowed; audit meaningful access by any user (C62)** | Project-specific exceptions, audit visibility and retention |
| Authorization | **Permissions, roles and default roles from the start (C63)**; offer role-customization UI as an optional feature | Is customization UI authorized for this product? Which permissions and default roles fit it? |
| Session | Server session; scoped API token; host-bound session | Need immediate revocation, third-party clients or distributed verification? |
| Lifecycle | Rename; merge; transfer; suspend; delete/export | Which operations preserve history and which must sever access? |

## Candidate starting branches
- **Consumer:** personal workspace owned by the individual (confirmed); signup timing remains product-specific; email codes and passkeys follow C71, federation is a product choice.
- **B2B:** company-owned data; explicit membership; lifecycle and SSO rules chosen together.
- **Embedded:** follow the host’s identity contract; test host logout and revocation.

Not approved: treating the identity default as universal, exposing multi-login UI in every product, passkeys-only recovery, custom cryptographic protocols, or “admins bypass everything.”

## Required proof in the eventual recipe
Cross-tenant denial; removed-member access; recovery abuse; credential changes; session revocation; safe audit detail; signup/login/recovery outcome metrics. Exact implementation follows [modern security research](76-modern-options.md).

## Customer-data access — confirmed C62
Superstaff may inspect client data. Audit access by any user at the meaningful-action level: opening customer details counts, merely seeing names in a list does not. Bulk exports produce a bulk-operation entry rather than an enumeration of customers touched by default. This does not settle staff/customer identity separation or grant all staff every permission. [Details](92-customer-data-access.md).

## Permissions and roles — confirmed C63
Include permissions and roles in the code from the start, with default roles. Offer role-customization UI as a separate feature; implement it only when authorized for the product. Do not confuse a capable internal model with a decision to expose all its capabilities in the UI.

Supersedes the assistant's fixed-roles-vs-custom-roles framing. Exact permissions, default role names and UI design remain product-specific. [Recipe](../../skills/scaffold/references/permissions.md).

## Login methods — confirmed C71
Email codes by default where sending email is possible; retain codes even when including a link, so email can be read on another device. Require Apple code recognition/autofill. Passkeys offered from the start with smooth “passkey or email” UX; other methods are product choices. Discoverable passkeys technically allow login before email entry; details and validation limits in [login methods](97-login-methods.md).

C72: after email-code signup/login, automatically offer passkey creation with a normal confirmation prompt; email-code login remains available afterward. User explicitly accepts confirmation; no silent-creation requirement. [Enrollment findings](97-login-methods.md).
