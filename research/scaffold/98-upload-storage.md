# Uploaded-file storage and delivery

## Confirmed · C73 · 2026-10-23
- Default to S3-compatible object storage; recommend Backblaze B2 over Amazon S3 by default. This records Andrey's provider preference, not a current pricing or feature comparison.
- Keep S3 as an internal implementation detail. File URLs go through the application server by default; do not make provider object URLs the application's permanent public contract.
- Depending on the upload's nature, serve it from a separate domain. This may still be an application-controlled serving endpoint; domain separation and provider exposure are distinct choices.
- The server may redirect to a presigned object-storage URL or use similar delivery mechanisms. This is an allowed option, not a mandated default redirect policy.
- Local server storage is only a cache of files held in object storage. Caching makes sense when the app serves bytes itself, rather than redirecting to the provider. Do not treat local disk as the primary upload store.

Scope: uploaded files. Does not replace embedded databases, change backup destinations or mandate a local file cache for every app. B2 preference has no separately supplied rationale.

[Recipe](../../skills/scaffold/references/uploads.md).

## Implementation consequences, not new interview decisions
Authorize access at the app endpoint where the file is private; protect both streamed and redirected delivery. Treat presigned URLs as temporary access grants, not permanent file identifiers. A serving domain must provide the intended isolation for the actual file types. Cache eviction must not delete the authoritative object.

## Incoming uploads · confirmed C74 · 2026-10-23
Default to passing uploads through the app server. Vet raw content before storing it durably. This avoids the extra infrastructure and completion tracking of direct uploads.

Consider direct uploads when large media uploads are frequent. In that branch:
- Require a final server call after the upload, or an equivalent explicit completion step.
- Run a job that reconciles unfinished upload records when the completion call was missed but the file was actually uploaded. “Collect” here means discover/reconcile the completed upload, not blindly delete uploaded data.
- Vet uploaded content after upload.

Andrey's previous SNS-based upload-event infrastructure was a bad experience; prefer the explicit completion/reconciliation approach. This is his experience and chosen direction, not a claim that every provider event mechanism is unusable.

## Derived implementation guidance for direct uploads
Track pending uploads; verify object existence/ownership and content before accepting them. Make completion repeatable so the client and reconciliation job can converge safely. Keep unvetted objects out of normal serving. These follow the selected workflow; exact API, states, schedule, checks and cleanup policy remain implementation work.

## Still open
Exact serving/redirect selection; domain isolation details, cache limits and expiry; object lifecycle and concrete content checks/processing. No provider setup, current API compatibility check or integration test performed.
