# API style

## Confirmed · C85 · 2026-10-23
For APIs used by the application's own web and native clients, prefer RPC-style operations with JSON for operation-oriented APIs. User clarified that this is situational: CRUD-focused APIs may use REST. Most APIs he builds are not CRUD, which explains the usual RPC preference. This qualifies the initial “not REST” wording; it is not a blanket ban.

Use ordinary JSON-over-HTTP endpoints organized around application operations. No RPC framework, JSON-RPC specification, gRPC, generated clients, exact endpoint naming, response envelope or versioning policy selected. The suggestion's fit with handlers/changesets is assistant reasoning, not a separately stated user rationale.

SSR pages, HTML forms and Turbo remain the web default; create data APIs where the clients need them. Third-party/public API conventions and compatibility promises were outside this question and remain contextual. Do not infer the REST/RPC choice settles caching, authorization or error semantics.

[Recipe](../../skills/scaffold/references/apis.md).
