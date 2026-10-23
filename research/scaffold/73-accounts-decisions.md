# Accounts: current decisions and product choices

Use [identity/workspaces](../../skills/scaffold/references/accounts.md), [login](../../skills/scaffold/references/login.md), [permissions](../../skills/scaffold/references/permissions.md) and [access auditing](../../skills/scaffold/references/customer-data-access.md) for the current rules. [Identity rationale](82-identity-and-profiles.md) and the [decision record](78-confirmed-decisions.md) preserve the interview.

## Confirmed
- Shared login with per-company profiles, including name. Personal workspaces use the same ownership model (C19–21).
- Prepare for simultaneous logins internally; choose exposed switching/extra-login UI per product. Shared identities follow strictest combined company auth requirements; incompatible requirements can use separate identities.
- Company admins cannot directly change shared login email or hand over reset passwords. Ordinary account changes use first-class flows.
- Email codes initially where email can be sent; passkeys from the start, automatically offered after email login with confirmation. Email remains available under company policy (C71–72).
- Total lockout is a one-off support case, with selected staff permitted raw-data repairs; ownership proof remains case-specific. No blanket org-admin override or generic editor UI selected (C83).
- Permissions, roles and default roles in code from the start. Offer role-customization UI as a separate authorized feature (C63).
- Superstaff may access client data. Audit meaningful access by any user: detail views count, names in lists do not, bulk operations get one entry by default (C62).
- Signup timing follows the measured business funnel; convenience favors use before login all else equal (C24–28).
- Export and deletion required, with JSON files in a ZIP as minimum export; ordinary deletion recovery defaults to 30 days (C86–87).

## Choose for the actual product
These are prompts when relevant, not a new generic interview checklist.

| Concern | Concrete decision |
|---|---|
| Membership | Who creates/joins a workspace, who owns its data after someone leaves, and which transfer/merge operations are needed? |
| Enterprise identity | Is federation/provisioning needed, who is authoritative, and how quickly must removal take effect? |
| Assurance and sessions | Which actions need renewed proof, and what revocation/session behavior meets the threat model? |
| Roles and support | Which permissions/default roles fit, which UI is authorized, and who may make exceptional repairs? |
| Data lifecycle | Which personal/shared/company records belong in export or erasure, and how do history, audit and backups behave? |

Consumer apps start with personal workspaces; B2B apps need company membership/ownership. Embedded products must account for the host's identity contract. These contexts do not override confirmed defaults without a concrete reason.

## Deferred
Staff/customer record separation has **no approved default** (C23). Keep the earlier C22 candidate historical. Customer ownership/deletion concerns do not alone select a model or legal interpretation.

## Derived verification guidance
Test cross-workspace denial, removed-member access, credential/session changes, meaningful audit records and the actual export/deletion flow. Exercise real login as well as fixture shortcuts; verify Apple email-code autofill on supported devices. For a one-off recovery, assess ownership proof for that case instead of inventing a standard lockout product feature.

The [security scan](76-modern-options.md) is research context, not an approved authentication protocol. Current browser/provider behavior still needs validation when implementing.
