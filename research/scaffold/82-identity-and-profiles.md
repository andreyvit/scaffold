# Login identity and company profiles

Confirmed by Andrey, 2026-10-19. Product choice with a recommended default, not a universal requirement.

Current recipe: [identity and workspaces](../../skills/scaffold/references/accounts.md).

## Default
- One login identity may belong to multiple companies.
- Everything beyond login identity belongs to a per-company profile: even name, plus avatar, title, biography and other profile fields.
- Most application code operates through the selected company profile, regardless of whether profiles share one login identity or use separate logins.
- Prepare the internal architecture for multiple simultaneous logins and profile/account switching. Exposing an extra-login UI is a separate product decision; it may be hidden or unbuilt.
- Separate identities remain possible where needed. Do not require them merely because companies are distinct.

## Why
- Smart defaults matter most when users will not invest attention in the decision.
- Prefer customer convenience, all else equal. Multi-company users benefit; single-company users need not face additional ceremony.
- Tester/developer convenience is a substantial benefit: switch among test companies or a sandbox. It can justify meaningful product capability, not just small conveniences.
- Impersonation is another possible testing tool, not selected here.
- Multi-company membership is largely additive; its code complexity is worth the flexibility and convenience in this case.
- This is not permission to prebuild every speculative feature. Prepare the common internal model; expose UI according to product needs.

## Company login policies
- Company administrators may require 2FA or restrict allowed federated logins and other login requirements.
- For a shared identity, the strictest combined company requirements apply to the user.
- Separate identities/emails remain available for incompatible requirements.
- Company administrators must not directly change the shared login email or reset a password and hand it to someone in plaintext.
- Provide first-class product flows for email changes and credential recovery instead. Exact authorization/recovery mechanics remain open.
- Policy combination, incompatible policies, joining/leaving, and enforcement need an explicit implementation design; this records product intent, not a validated security protocol.

## Personal workspaces — confirmed
**Why:** simplicity and internal consistency.

Use the same ownership model for personal and company data. A personal workspace is a small company-like account with the individual as owner. Do not attach personal application data directly to login identity under separate ownership rules.

Sharing, conversion and exposed workspace UI remain separate product choices; not inferred from this decision.

## Product staff — deferred
**No selected default. Revisit later.** Andrey may reverse the earlier preference for separate staff/customer records; he does not yet consider its rationale defensible.

- Earlier candidate: reuse login machinery, separate staff/customer records unless their surfaces overlap.
- Consideration to revisit: the client company strongly owns customer records; deletion requests should allow deleting those records.
- This does not yet establish how customer records relate to login identities, how deletion propagates, or what staff model follows.
- Do not promote the earlier preference into a recipe, or treat the deletion example as a legal/compliance conclusion.

## Signup timing
Convenience favors use before login, but the business funnel determines the choice; measure and test the assumption. [Confirmed rule](83-business-and-onboarding.md).

C83: total lockout is handled as a [one-off staff repair](105-one-off-support-repairs.md), not a dedicated recovery flow. This leaves ordinary first-class email-change flows and the restriction on company-admin edits to shared login identity intact.
