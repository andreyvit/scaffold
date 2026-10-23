# Observability

Detailed design and tool selection are deferred until Andrey experiments himself. Preserve the requirements and qualified preferences below; do not promote research proposals into defaults or reopen the topic without new input.

Include metrics, product analytics, spans/tracing and good logging from project start. Instrument broadly across features, background work, dependencies and operational tasks. Do not defer visibility until an incident.

Prefer direct writes to rotated telemetry files/journals with indexes for fast access. Compression/encryption may be useful; preserve the stronger existing requirements for analytics journals. Avoid introducing collection infrastructure solely by copying a distributed-system setup.

Prefer a simpler default than Prometheus/PromQL. This is a soft stance, not a ban; BH uses Prometheus and a demonstrated benefit can justify it. Rotation/index/storage tools remain open. [Assessment and implementation considerations](../../../research/scaffold/102-file-based-observability.md).

Support investigating individual operations as well as aggregate behavior. Preserve the existing product-analytics decisions: broad usage coverage, in-process ingestion, separate analytics storage, raw-event history and finite retention. Customer-data access auditing is a separate requirement; see [customer data access](customer-data-access.md).

Anomaly monitoring on selected metrics is an intended direction. No particular algorithm or day-one anomaly implementation is selected.

Avoid the Protobuf dependency/toolchain. A small handwritten encoder for the needed OTLP fields is acceptable in principle; OTLP wire compatibility alone does not disqualify a tool. This clarifies the earlier blanket rejection. Do not infer approval of a general Protobuf library, OpenTelemetry SDK or collector. Seek a lightweight integrated tool in plain Go that runs on one server with little operational fuss. The specific backend, instrumentation libraries, record format, sampling and operational-signal retention remain open. Earlier full-stack recommendations remain unapproved; optional dependency-free OTLP output is distinct from adopting that stack. See [research and options](../../../research/scaffold/99-observability.md).

Prefer evaluating lightweight tools that make routine investigation fast and affordable. BH uses Grafana Cloud but reports high cost and slowness; do not make it or a self-hosted equivalent the default without evaluation. No replacement selected.

See [lightweight candidate research](../../../research/scaffold/100-lightweight-inspectability.md) before proposing a tool. No complete match or owned implementation selected.

Backend selection is deferred until hands-on trials. Keep the [candidate list](../../../research/scaffold/100-lightweight-inspectability.md) available, including Jaeger with embedded Badger as a tracing option. Partial tools do not replace the full metrics/logs/traces/analytics requirement.

For later anomaly-monitoring evaluation, see [candidate notes](../../../research/scaffold/101-lightweight-anomaly-detection.md). No algorithm or service selected; small embedded detectors and metrics-backend rules are options alongside separate services.
