# Observability

Detailed design and tool selection are deferred until Andrey experiments himself. Preserve these requirements and preferences; do not promote research proposals into defaults or reopen the topic without new input.

## Required capabilities
Include metrics, product analytics, spans/tracing and good logging from project start. Instrument broadly across features, background work, dependencies and operational tasks. Support individual-operation investigation as well as aggregate behavior; do not defer visibility until an incident.

Follow [analytics and experiments](analytics.md): broad usage coverage, in-process ingestion, separate analytics storage, raw-event history and finite retention. [Customer-data access auditing](customer-data-access.md) is a separate requirement with its own semantics.

Anomaly monitoring on selected metrics is an intended direction; no algorithm or day-one anomaly implementation selected.

## Qualified preferences
- Prefer direct writes to rotated telemetry files/journals with indexes for fast access. Compression/encryption may help; preserve the stronger requirements for analytics journals. Avoid collection infrastructure added solely by copying a distributed-system setup.
- Prefer a simpler default than Prometheus/PromQL. This is a soft stance, not a ban; BH uses Prometheus, and demonstrated benefits can justify it.
- Avoid the Protobuf dependency/toolchain. A small handwritten encoder for needed OTLP fields is acceptable in principle. Wire compatibility alone does not disqualify a tool; this does not approve a general Protobuf library, OpenTelemetry SDK or collector.
- Seek a lightweight integrated tool in plain Go, running on one server with little operational fuss. Routine investigation should be fast and affordable. BH reports Grafana Cloud cost/slowness; do not assume self-hosting the same stack solves that experience.

No complete match, replacement backend or owned implementation selected. Instrumentation libraries, record format, sampling, operational-signal retention, rotation/index mechanics and anomaly details remain open. A partial tool does not fulfill the entire metrics/logs/traces/analytics requirement.

## Saved options for later trials
- [Solution space and historical proposals](../../../research/scaffold/99-observability.md).
- [Backend candidates](../../../research/scaffold/100-lightweight-inspectability.md), including Jaeger with embedded Badger for traces.
- [Anomaly candidates](../../../research/scaffold/101-lightweight-anomaly-detection.md), from small embedded detectors to backend rules and separate services.
- [Direct files, rotation and indexes](../../../research/scaffold/102-file-based-observability.md), including implementation considerations.

Consult these when evaluation resumes; no further selection or trials are part of the current work. Source: C75–81.
