# Observability from the start

**Deferred · C81 · 2026-10-23:** preserve these options; Andrey will experiment himself before making more detailed recommendations. No further selection, design or trial work now. Existing preferences remain recorded; proposals are not approved defaults.

**Current constraint — C78 clarifies C77:** avoid the Protobuf dependency/toolchain; emitting the needed OTLP fields with a small handwritten encoder is acceptable in principle. No SDK or backend selected. Seek a lightweight integrated Go solution on one server; see [candidate research](100-lightweight-inspectability.md).

**Current starting design — C80:** prefer direct writes to rotated files/journals and fast indexes; Prometheus/PromQL are soft exceptions. [Assessment](102-file-based-observability.md).

## Confirmed · C75 · 2026-10-23
Andrey describes observability at Bubblehouse as still rudimentary and requests guidance, not replication of a proven existing stack. Metrics for everything are required. New projects need metrics, analytics, spans and good logging from the start. He plans anomaly monitoring on selected metrics.

No backend, library, hosting arrangement, sampling rule, retention period or anomaly algorithm selected. “Metrics for everything” establishes breadth; it does not establish unlimited metric labels or recording every function call. Anomaly monitoring is an intended direction, not a selected day-one implementation.

Existing decisions remain: broad product analytics and experiments, in-process ingestion with a separate analytics database, raw-event journals and 24-month default raw retention; small analytics gaps acceptable. Audit records have separate semantics. Application remains one process by default. Production recovery remains operator-controlled.

[Recipe](../../skills/scaffold/references/observability.md).

## Explanation and recommendation — historical assistant proposals

Protocol/stack recommendations in this section were not approved. C77 initially rejected Protobuf/OTLP; C78 permits lightweight handwritten OTLP output without the Protobuf dependency. This does not adopt the proposed stack.

### Signal roles
- Metrics: counters, gauges and distributions over time. Detect error rates, slow requests, queue age, missing backups, resource pressure and business changes. Cheap aggregate history; limited per-event detail.
- Traces: a trace groups spans, each a timed operation with context. A request can include database work and outbound calls; jobs can carry or link originating context. Useful within one process, not only across services. Instrument meaningful boundaries, not every function.
- Logs: structured event detail explaining decisions, failures and unusual conditions. Include operation, build, request/job and trace identifiers; do not repeat the same error at every layer.
- Product analytics: user/workspace behavior, funnels, cohorts, experiments and retention. Raw event history supports questions not known when counters were defined. Metrics can summarize these events, but sampled traces cannot replace them.
- Audit: separate durable record of meaningful access/actions under C62. Debug-log expiry or trace sampling must not silently control audit retention.

The intended investigation path is alert → chart → example trace → relevant logs. Business questions use analytics, possibly linked to operational evidence under appropriate access controls.

### App foundation
Recommend standard Go structured logging (slog or an existing compatible context logger), Prometheus-compatible metrics, and OpenTelemetry traces. OpenTelemetry defines instrumentation/export mechanisms; it is not the storage, search UI or dashboard product. Do not instrument a metric twice merely to support two export formats. Use a small project-local helper only where it removes real repetition; do not build a generic observability framework.

Instrument request and job volume, errors, duration distributions, queue wait/oldest age, database and external-service operations, cache behavior, upload/email paths, backup/restore checks, process/host resources and business outcomes. Include external availability checks: the app cannot report its own host's total failure. Capture browser errors and user-visible timing separately from server processing time.

Bound metric dimensions: route templates, operation names and outcomes are useful; arbitrary URLs, user IDs and request IDs multiply time series. Keep per-user/tenant detail in structured events or deliberately budgeted analyses. This is a storage/query design constraint, not a ban on necessary customer-level analysis.

Telemetry export must have bounded queues, timeouts and disk use, with visible dropped-data counters. A monitoring outage must not stall business operations. This does not weaken transactional business or audit requirements. Access control/redaction apply to payloads; request bodies, tokens and email codes are not default log fields.

Start with all traces at genuinely small volume if measured overhead/storage allow; define a budget and finite retention. At higher volume sample ordinary traffic. Head sampling decides early and cannot guarantee preserving later failures. Tail sampling can favor errors/slow traces but requires buffering and processing; it cannot recover spans discarded upstream. Operational counters should count all operations regardless of trace sampling. Configure separate retention for metrics, logs and traces; the confirmed 24-month analytics window does not automatically apply.

### Backend choices
1. Minimal tools: Prometheus and Grafana for metrics, structured local logs and a trace store/viewer. Fewer centralized capabilities; cross-host log search and signal linking need work. Export alone does not satisfy day-one usable tracing.
2. Composable self-hosted: Prometheus metrics, Loki logs, Tempo traces, Grafana exploration/dashboards, plus collection and alert delivery. A conventional candidate suited to ownership, with several services to configure, secure, size and upgrade. Use small/monolithic deployment modes; no Kubernetes requirement. Prefer monitoring outside the app host's failure domain. Validate selected versions and actual resource use before making this the recipe default.
3. Integrated self-hosted: SigNoz is one option with a shared UI and ClickHouse storage plus a collector. Fewer integration decisions do not mean one dependency-free executable. Compare maintenance, query experience and resource use rather than marketing component counts.
4. Managed backend: less storage/upgrade work in exchange for recurring ingestion/retention cost, external data handling and some vendor-specific queries/dashboards. OpenTelemetry and Prometheus compatibility reduce instrumentation lock-in; they do not make all backend features portable.

Provisional preference given stated values: own the instrumentation and evaluate the small self-hosted Grafana stack first; consider managed hosting if maintaining telemetry takes too much product-development time. Backend selection is still open. Keep product analytics in the app as already decided; an operational telemetry service does not require splitting business execution into microservices. A separate collector is useful for shipping, batching and filtering, but direct export can work at small scale.

### Alerting and anomalies
Start with explicit safety conditions and actionable alerts: sustained error rate, old queued work, missing successful backups, failed external probes, disk exhaustion. Give alerts an owner, diagnostic context and a recovery action. Test notification delivery; dashboards alone do not alert anyone. No automatic production recovery inferred.

Add anomaly rules for selected metrics: deviations from recent/seasonal baselines, normalized by traffic and checked against minimum sample counts. Compare similar hours/weekdays where relevant; annotate releases and campaigns. A drop from two events to zero has different evidential weight from 2,000 to zero. Distinguish no incoming data from a true zero. Fixed safety limits remain useful alongside learned baselines. Treat anomalies as investigation prompts, not proof of failure or authorization to repair automatically. Avoid paging for every statistically unusual metric.

## Primary-source research · 2026-10-23
Documentation review only; no installation, benchmark or production sizing test.
- [OpenTelemetry signals](https://opentelemetry.io/docs/concepts/signals/): collection/export of traces, metrics and logs.
- [Collector](https://opentelemetry.io/docs/collector/): direct export can suit small setups; collector offloads handling.
- [Sampling](https://opentelemetry.io/docs/concepts/sampling/): head versus tail tradeoffs.
- [Prometheus instrumentation](https://prometheus.io/docs/practices/instrumentation/) and [labels](https://prometheus.io/docs/practices/naming/): broad instrumentation with bounded series cardinality.
- [Loki modes](https://grafana.com/docs/loki/latest/get-started/deployment-modes/): single-process mode supports small installations.
- [Tempo modes](https://grafana.com/docs/tempo/latest/set-up-for-tracing/setup-tempo/plan/deployment-modes/): monolithic mode does not require Kafka. Some general deployment documentation says Tempo 3 requires Kafka without this qualification; detailed mode/setup docs distinguish microservices from monolithic mode. Verify chosen release rather than repeating the broad claim.
- [Grafana all-in-one development image](https://grafana.com/docs/opentelemetry/docker-lgtm/): explicitly intended for development/demo/testing, not a turnkey production recommendation.
- [SigNoz architecture](https://signoz.io/docs/architecture/): collector, ClickHouse and application/UI components.

## Historical interview question — no longer pending
The assistant asked how strongly infrastructure ownership should apply to the monitoring backend. Subsequent discussion produced C76–81 and deferred detailed selection. Do not ask this again as the next question.

## Grafana Cloud experience · confirmed C76 · 2026-10-23
BH uses Grafana Cloud. Andrey reports high cost and enough slowness that the team avoids it except as a last resort during investigations; it still serves that last-resort role. He would love a lightweight project covering the observability needs. This is user-reported experience, not an independently measured claim about Grafana Cloud generally.

This changes the prior assistant recommendation: do not assume self-hosting the Grafana stack solves the cost/usability problem. Investigate lightweight alternatives. No replacement, build instruction or universal prohibition on managed telemetry selected. Ownership-versus-hosting selection remains deferred under C81; do not repeat the historical question or treat self-hosting as chosen.

## Trace representation and storage — researched explanation, not decisions
A trace is a set of spans sharing a trace ID. Each span has its own ID, optional parent ID, name, kind, start/end timestamps, attributes, status, events and links. Service/resource and instrumentation-scope metadata accompany spans. Parent IDs reconstruct the hierarchy; links express additional relationships. Spans can arrive separately, out of order, and after a root span completes. Missing spans are possible; receiving the root is not proof of completeness.

[OpenTelemetry's span schema](https://github.com/open-telemetry/opentelemetry-proto/blob/main/opentelemetry/proto/trace/v1/trace.proto) and [OTLP](https://opentelemetry.io/docs/specs/otlp/) provide a common data model and interchange protocol. OTLP normally transports Protobuf batches over gRPC or HTTP; OTLP/HTTP also specifies JSON encoding. Its envelopes group spans by resource and instrumentation scope. A flattened illustrative JSON span is not the actual OTLP JSON envelope. OTLP standardizes interchange, not a universal database/file layout. Protobuf records can be stored in framed files; messages need record boundaries. One span per JSONL line is also feasible as an application-specific storage representation.

Logs likewise may be emitted as JSONL without remaining JSONL inside a searchable backend. Trace backends choose layouts according to queries and scale:
- [Tempo](https://grafana.com/docs/tempo/latest/reference-tempo-architecture/block-format/) writes Parquet blocks with metadata and lookup aids. Columnar reads help search selected attributes without decoding every span field.
- [Jaeger with Badger](https://www.jaegertracing.io/docs/2.22/storage/badger/) demonstrates persistent embedded key-value storage in one binary. Suitable for single-node operation; not evidence that it supplies the full metrics/logs/analytics experience or meets the user's performance needs.
- Relational/columnar tables or indexed encoded records are also possible. Encoding alone does not determine query speed.

For a deliberately small owned store, a plausible design is append-only span records or an embedded database, with trace-ID lookup and selected time/operation/error/duration indexes. Build a waterfall from timestamps and parent relationships; correlate logs by trace/span IDs. OTLP ingestion preserves compatibility with existing instrumentation. This is a candidate architecture, not an implementation instruction or extracted-library authorization.

The substantial work is fast searches across many traces, bounded retention/storage, late or missing spans, ingestion behavior and a useful investigation UI. Keep query scope deliberate; reproducing an arbitrary analytics engine is a different undertaking. No benchmark or installation performed.

## Evaluation deferred · confirmed C79
Keep the [brief list of all discussed options](100-lightweight-inspectability.md), including Jaeger with embedded Badger, for later hands-on trials. No backend selected. Do not continue forcing a monitoring decision in the interview now.

Lightweight anomaly-detection candidates are recorded [separately](101-lightweight-anomaly-detection.md). User requested the comparison; recommendations remain unconfirmed.
