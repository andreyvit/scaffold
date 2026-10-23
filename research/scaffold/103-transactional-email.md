# Transactional email

## Confirmed · C82 · 2026-10-23
Use Postmark or Mailchimp for transactional email. Andrey states these choices emphatically; no preference between the two supplied. Sending an email should be a job.

Apply the existing job architecture: queue in the main database, schedule with the originating business change in the same transaction where feasible, and execute in the app process. Preserve the no-automatic-retry-after-panic rule. Expected delivery failures and ambiguous provider outcomes still need implementation/policy work; this answer does not select retries or an exactly-once guarantee.

Preserve “Mailchimp” as the user's named option; exact product/API/account requirements should be verified during implementation. Do not broaden the provider shortlist or ask for a preference between these two now. No provider setup or code requested.

Login codes follow C71–72; development capture follows C44. [Recipe](../../skills/scaffold/references/email.md).
