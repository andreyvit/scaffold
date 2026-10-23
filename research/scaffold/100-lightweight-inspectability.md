# Lightweight inspectability search

**Deferred · C81 · 2026-10-23:** preserve these options; Andrey will experiment himself before making more detailed recommendations. No further selection, design or trial work now. Existing preferences remain recorded; proposals are not approved defaults.

**Current preference — C80:** direct rotated files/journals plus fast indexes. Prometheus/PromQL remain options when justified, not the starting recommendation. [Design assessment](102-file-based-observability.md).

## Try later · confirmed C79 · 2026-10-23
Keep all discussed options for hands-on evaluation later, including Jaeger. No winner selected; no trials requested now. OTLP is compatible with the proposed handwritten exporter and is not by itself a disqualifier.

| Option | What to try / main qualification |
|---|---|
| [Traceway](https://github.com/tracewayapp/traceway) | Integrated Go/Svelte tool; compare SQLite and DuckDB deployment cost and query speed |
| [Waggle](https://github.com/danielloader/waggle) | Single Go/SQLite explorer for metrics, logs and traces; local-development focus |
| [Fanout](https://github.com/labstack/fanout) | One Go process with Parquet/DuckDB, queries and alerts; assess dependency/UI complexity |
| [otelite](https://github.com/planetf1/otelite) | Embedded SQLite with UI/CLI across signals; local/LLM-development focus |
| [Jaeger + Badger](https://www.jaegertracing.io/docs/2.22/storage/badger/) | Go tracing backend and viewer; all-in-one deployment with persistent embedded storage. Trace component, not full metrics/logs/analytics suite |
| [VictoriaMetrics](https://docs.victoriametrics.com/victoriametrics/) / [VictoriaLogs](https://docs.victoriametrics.com/victorialogs/) / [VictoriaTraces](https://docs.victoriametrics.com/victoriatraces/) | Evaluate the Go tools together or individually; separate products, not one integrated executable |
| [OpenObserve](https://openobserve.ai/docs/) | Integrated logs/metrics/traces; Rust rather than Go |
| [SigNoz](https://signoz.io/docs/architecture/) | Integrated experience; ClickHouse and collector add operational components |
| [Gotcha](https://getgotcha.ru/en/) | Broad Go observability application; requires PostgreSQL and ClickHouse |
| [Prometheus](https://prometheus.io/) + [Grafana](https://grafana.com/oss/grafana/) + [Loki](https://grafana.com/oss/loki/) + [Tempo](https://grafana.com/oss/tempo/) | Conventional self-hosted comparison, together or by component; assess setup, search speed and maintenance |
| Grafana Cloud / managed backend | Existing BH comparison: reported expensive and slow; no new managed provider selected |
| [owl](https://neverbot.github.io/owl/) | Small Go/SQLite metrics dashboard using text scraping; partial solution |
| [gospan](https://github.com/akmadian/gospan) | Small in-process Go span library with slog/SQLite output; pre-1.0, partial solution |
| [Peek](https://github.com/mchurichi/peek) | Go log collector/viewer with Badger; partial solution |
| [Outrig](https://outrig.run/docs/getting-started) | Go development inspection: logs, goroutines, watches and runtime metrics |
| [SigLens](https://github.com/siglens/siglens) | Archived integrated Go project; reference or deliberate fork candidate, not maintained adoption |
| Small owned implementation | One Go server, local storage and focused UI; optional handwritten OTLP adapter. Design fallback, not an approved build/extraction |

Later trials should compare setup/upgrade effort, real query/UI latency, resource/storage cost, retention/restart behavior, signal correlation and gaps in alerts/product analytics. No measured results yet. Jaeger's Badger option was verified from its primary documentation during the trace-storage discussion; its single-node limitation is consistent with the desired starting scale.

## Current constraint · C78 clarifies C77 · 2026-10-23
Andrey initially said “I draw the line at protobufs; no OTLP” (C77), then clarified that producing OTLP likely can be done without a Protobuf dependency by hardcoding the relevant fields like a custom binary format (C78).

Avoid the dependency/toolchain; a small handwritten OTLP encoder is acceptable in principle. This is not an instruction to implement it now or approval of a general Protobuf library, OpenTelemetry SDK, collector, backend or arbitrary receiver dependencies. Wire compatibility alone no longer disqualifies a candidate. Receiver internals and overall complexity still need evaluation.

Desired scope remains plain Go, one-server simplicity, metrics, logs, spans/traces and the previously stated analytics needs. No format, database, library or extraction selected. [Requirements and earlier discussion](99-observability.md).

## Search findings · 2026-10-23 · evaluated before C78
Primary README/documentation review; no installation, benchmark, dependency audit or proof of production readiness. Resource/speed claims in project marketing were not verified. Found close projects, but no verified match for the complete combination: plain Go, one-server simplicity, integrated capabilities, and no Protobuf/OTLP. This is not proof that no such project exists. C78 relaxes the wire-format constraint: OTLP entries below are compatibility facts, not automatic exclusions. Reevaluate promising tools under the clarified dependency/simplicity requirements.

| Project | Relevant capability | Gap against this request |
|---|---|---|
| [Traceway](https://github.com/tracewayapp/traceway) | Go backend, embedded Svelte UI; metrics, logs, tracing and broader investigation features; SQLite deployment avoids external databases | Current documented ingestion is OTLP. [SQLite docs](https://docs.tracewayapp.com/server/sqlite) now recommend DuckDB for telemetry growth; DuckDB build requires CGO. Not a verified lightweight fit |
| [Waggle](https://github.com/danielloader/waggle) | Single static pure-Go binary, SQLite, unified traces/logs/metrics explorer | OTLP; explicitly a local-development viewer; React UI. Production operation not established |
| [Fanout](https://github.com/labstack/fanout) | One Go process/data directory with embedded UI, Parquet, DuckDB, querying and alerting | OTLP; embedded DuckDB. Single deployed process does not establish plain-Go internals or small operational footprint |
| [SigLens](https://github.com/siglens/siglens) | Go project describing one binary for logs, metrics and traces | Archived March 12, 2026. Not a maintained adoption recommendation. A plain ingestion path for all signals was not verified |
| [VictoriaTraces](https://docs.victoriametrics.com/victoriatraces/quick-start/) | Single-node binary with its own storage and viewer | Trace input is OTLP; metrics/logs are other products. Not the requested unified tool |
| [OpenObserve](https://openobserve.ai/docs/) | Combined logs/metrics/traces; plain JSON log and metric endpoints | Rust; [trace ingestion](https://openobserve.ai/docs/reference/api/ingestion/traces/) remains OTLP |
| [Gotcha](https://getgotcha.ru/en/) | Go application covering errors, traces, metrics, logs and uptime; JSONL log input | Requires PostgreSQL and ClickHouse; OTLP features. “Single Go binary” excludes required database services |
| [otelite](https://github.com/planetf1/otelite) | One binary, embedded SQLite, logs/metrics/traces, CLI and UI | OTLP-centered local/LLM development tool; JSONL import alone does not establish a complete non-OTLP production path |

Traceway's current setup documentation says its separate Go SDK was retired in favor of OpenTelemetry. Older README examples mention a Go client; do not mistake them for a supported current non-OTLP integration. C78 permits considering a handwritten exporter to its OTLP endpoint; this does not establish that its implementation or operating cost meets the remaining requirements.

## Small tools that cover part of the need
- [owl](https://neverbot.github.io/owl/): static Go binary, SQLite, Prometheus text scraping, dashboards and a PromQL subset. Relevant example for small metrics monitoring; no complete logs/traces/product-analytics solution established. Text metric exposition does not require Protobuf on the wire; dependencies not audited.
- [gospan](https://github.com/akmadian/gospan): in-process Go spans to slog or optional SQLite; core described as standard-library-only. Explicitly pre-1.0; not a metrics server, log aggregator or distributed tracing backend. Useful design reference, not a complete platform recommendation.
- [Peek](https://github.com/mchurichi/peek): Go log collector/viewer, JSON/logfmt, embedded Badger. Logs-focused; no complete metrics/tracing platform established.
- [Outrig](https://outrig.run/docs/getting-started): Go development inspection with logs, goroutines, watches and runtime metrics, using a separate monitor. Not established as a durable production observability/analytics platform.

## Assistant recommendation — not yet selected
A deliberately small owned design is reasonable if candidates keep missing the constraints. Start with one Go server, local storage and an embedded UI; plain versioned JSON batches for structured records and an explicit metrics representation. Logs, spans and business events can share ingestion metadata and correlation IDs while retaining distinct semantics and retention. Metrics need counters/distributions and time aggregation; a generic event table alone does not settle that design.

Focus searches on time, operation, error, duration and appropriate customer context; connect records to a trace waterfall and metric charts. Keep product analytics requirements and audit rules intact. Reuse design ideas from small tools rather than assuming a full observability framework is necessary. Storage engine, exact protocol, alert/anomaly evaluation and package boundaries still need design; do not imply this search authorizes library extraction or proves a full implementation trivial.

## Handwritten OTLP output — feasibility research
[Protobuf wire encoding](https://protobuf.dev/programming-guides/encoding/) permits a schema-specific implementation: field tags, varints, fixed-width values and length-delimited strings/bytes/nested messages. Go standard-library encoding/binary and net/http suffice for those mechanisms and HTTP transport. No code generation, reflection or general-purpose Protobuf runtime is inherently required.

[OTLP/HTTP](https://opentelemetry.io/docs/specs/otlp/) accepts a binary Protobuf ExportTraceServiceRequest at /v1/traces with application/x-protobuf; analogous endpoints exist for metrics/logs. gRPC is unnecessary for that transport. Implement only a documented, valid subset of fields/messages while preserving their schema semantics. A working exporter also needs bounded delivery and correct handling of response/partial-success/error behavior, not merely bytes that resemble spans. Interoperability fixtures and receiver tests should verify any implementation. No encoder written or tested in this interview.

Assistant guidance: keep any such exporter a small adapter around the app's own records. This separates backend compatibility from internal storage/API choices. OTLP support alone no longer establishes a need to invent a whole backend; previous candidates warrant assessment on their remaining merits.

## Anomaly detection companions
See the [brief anomaly-detection options](101-lightweight-anomaly-detection.md): PromQL rules, Go libraries Anomalyzer/anomalia, Netdata, vmanomaly and a small owned detector. These are additional try-later candidates; no selection or trial performed.
