# APIs for our own clients

Prefer RPC-style JSON over HTTP for operation-oriented APIs. CRUD-focused APIs may use REST. Choose according to the API's purpose; most APIs Andrey builds are not CRUD.

Keep ordinary server-rendered pages, forms and Turbo under the [web-rendering default](web-rendering.md); use data endpoints where needed by web/native clients. RPC style does not require a framework, generated clients or the JSON-RPC protocol.

Exact naming, envelopes, compatibility and public third-party API conventions remain to be chosen for the project. [Decision](../../../research/scaffold/107-api-style.md).
