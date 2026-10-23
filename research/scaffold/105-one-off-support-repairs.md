# One-off support repairs

## Confirmed · C83 · 2026-10-23
Total account lockout—no email access, no passkeys and no signed-in session—is rare enough to handle as a one-off. Do not build a dedicated standard recovery flow for this case by default.

Some selected staff should have permission to edit raw data for one-off repairs, including fixing an email address. This is a distinct privileged capability, not unrestricted editing for every staff member or company administrator. No particular editor/UI or direct database-access method selected.

Andrey doubts such email repairs will happen often because proving ownership of the old email is difficult. A B2B organization administrator asking for a correction is a possible case to consider. This is tentative context, not a sufficient-proof rule or automatic authorization to change a shared login identity.

## Relationship to existing decisions
Ordinary email changes/login flows remain first-class; this exception concerns total lockout. Company admins still must not directly change shared login email (C19). Staff may evaluate exceptional repairs; an organization request must be considered in the actual identity/ownership context, including other memberships. Exact proof requirements remain case-specific.

Existing permissions, meaningful customer-access auditing and changes/history requirements still apply. Do not interpret “raw data editing” as authorization to bypass those protections or rewrite every repair through normal business handlers; exact repair mechanics and validation remain implementation work.

[Login recipe](../../skills/scaffold/references/login.md) · [Permissions](../../skills/scaffold/references/permissions.md).
