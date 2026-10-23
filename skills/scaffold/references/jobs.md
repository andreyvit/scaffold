# Background jobs

Keep the job queue in the main database by default. When a business change schedules a job, persist both in the same transaction where technically feasible. Derive this from the shared database; do not ask it as a preference question.

Run jobs in the app process under the existing one-process default (C35). Unexpected panics fail the job without automatic retry (C42).

Atomic scheduling does not guarantee exactly-once external effects. Delivery, expected-failure retries and crash recovery still need design; no new policies are selected here.

Send transactional email as a job; use [Postmark or Mailchimp](email.md).
