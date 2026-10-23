# Identity and workspaces

Default to a shared login identity with a profile in each company/workspace. Everything beyond login identity belongs to the company profile, including name, avatar and other profile fields.

Most application code uses the selected profile, so it works with either shared or separate login identities. Prepare internally for simultaneous logins and profile/account switching. Exposing additional-login UI is a product decision; do not require that UI everywhere.

This buys convenience for multi-company users and testers without extra ceremony for single-company users. It is a justified common model, not permission to build every speculative capability.

## Ownership
Use the same ownership model for personal and company data. A personal workspace is a small company-like account owned by the individual. Do not give personal data a separate ownership model attached directly to login identity.

Membership, joining, invitations, ownership transfer, sharing and conversion follow actual product needs. Keep login identity, workspace profile, data ownership and billing ownership distinct.

## Login policy
Use [email codes and passkeys](login.md). For shared identities, apply the strictest combined company authentication requirements. Permit separate identities where requirements are incompatible. Design policy combination and joining/leaving enforcement explicitly; this is intent, not a validated security protocol.

Company admins must not directly change shared login email or reset and hand over a plaintext password. Provide ordinary first-class email-change and credential flows. Total lockout is the [one-off staff repair](login.md#total-lockout) exception; an org-admin request is not automatic proof of ownership.

Include [permissions and default roles](permissions.md) from the start. [Customer-data access](customer-data-access.md) covers superstaff access and meaningful-action auditing; it does not give every staff user unrestricted access.

## Product decisions and deferred work
Choose signup timing within the [business funnel](analytics.md), with convenience favoring access before login when other considerations are equal. Do not impose anonymous-first onboarding.

Staff/customer identity separation is deferred. Neither separate nor combined records is an approved default. Required [data export and deletion](data-rights.md) must respect the product's ownership boundaries; they do not settle that model.

Source: [C19–24 and identity rationale](../../../research/scaffold/82-identity-and-profiles.md), [current account decision map](../../../research/scaffold/73-accounts-decisions.md).
