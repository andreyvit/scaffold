# Transactional email

Use Postmark or Mailchimp. Neither is ranked ahead of the other by the confirmed preference.

Send email through a [background job](jobs.md). Keep queue/execution in the existing database/app process; persist scheduling with the originating business change where feasible. Unexpected panics fail the job without automatic retry. Expected-failure retries and ambiguous delivery outcomes remain to be designed.

Capture outgoing mail in the [development harness](development-harness.md). Email login must preserve the [code/passkey flow](login.md). Verify the chosen provider's current transactional API when implementing.
