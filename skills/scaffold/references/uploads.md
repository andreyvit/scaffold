# Uploaded files

Use S3-compatible object storage as the authoritative store. Prefer Backblaze B2 over Amazon S3 by default.

Keep storage-provider details internal. Expose application-controlled file URLs that go through the server by default. Serve bytes from the app, or optionally redirect to a temporary presigned object-storage URL; do not make provider URLs permanent application identifiers.

Use a separate serving domain when the uploaded content calls for it. This can still route through the application's serving code. Choose the isolation according to the content.

Local disk is only a cache of stored objects. Use it when serving files through the app makes caching useful; do not require it for redirects. Cache eviction must leave the authoritative object intact.

## Incoming uploads
Default to uploading through the app server. Vet raw content before durable storage; this avoids direct-upload completion infrastructure.

Consider direct-to-storage uploads only when frequent large media makes the extra machinery worthwhile. Require a final server completion call after upload, or an equivalent explicit completion step. Add a job to reconcile pending uploads whose completion call was missed even though the object arrived. Vet content after upload; do not serve unvetted objects as accepted files.

Verify completion against storage and make finalization repeatable by client or job. Prefer this flow over adding SNS-style event infrastructure merely to detect completion. Exact checks, reconciliation cadence and cleanup rules remain implementation choices.

## Operational guidance
Enforce the file's access policy before serving or issuing a redirect. Treat presigned URLs as access grants and omit their secrets from logs. Measure storage/delivery failures, latency and cache behavior where used; log useful operation/file IDs without file contents or credentials.

Verify content rejection before durable storage on the server path. For direct uploads, verify missed/duplicate completion calls, reconciliation and post-upload vetting. Also verify persistence, authorized/denied downloads, redirect expiry and serving after cache eviction. Processing details, cache limits and object lifecycle remain to be designed.
