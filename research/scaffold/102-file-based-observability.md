# Files and indexes as the observability starting design

**Deferred · C81 · 2026-10-23:** preserve these options; Andrey will experiment himself before making more detailed recommendations. No further selection, design or trial work now. Existing preferences remain recorded; proposals are not approved defaults.

## Confirmed · C80 · 2026-10-23
Andrey prefers avoiding Prometheus and PromQL as overengineering by default. This is a soft stance: BH currently uses Prometheus, and a justified exception remains possible.

For the expected non-distributed application, he prefers writing telemetry directly to files, rotating with something like logrotate or his journal library, possibly adding encryption/compression, then indexing those files for fast access. He questions collection infrastructure copied from large distributed systems and asks for a critical assessment.

This sets a preferred starting architecture, not a selected file format, rotation tool, index implementation or instruction to build now. Encryption/compression are possibilities in this broader scope; previously confirmed analytics-journal requirements remain in force. Existing candidates remain available for later trials. No universal ban on separate processes or justified collection inferred.

[Observability requirements](99-observability.md) · [Candidate list](100-lightweight-inspectability.md) · [Anomaly options](101-lightweight-anomaly-detection.md).

## Assessment — assistant reasoning, not new decisions
The design fits a single application/server well. Direct append can avoid protocol translation, collectors and network queues. App-owned instrumentation and a shared record vocabulary can make diagnosis easier. Local indexing and anomaly evaluation need no distributed pipeline.

The absence of a distributed system alone does not make Prometheus useless. Its [storage is local and single-node](https://prometheus.io/docs/prometheus/latest/storage/); time-series queries, compression, counter/reset semantics, rule evaluation and existing integrations have value on one host too. The relevant comparison is total effort and usability for the actual questions, not number of servers alone. Existing tools can earn their cost; the preference for simpler owned defaults remains valid.

### Work the file/index design must cover
1. **Rotation and recovery.** Index stable segment/record identities, handle a partially written final record, resume indexing from a checkpoint, and avoid double counting after replay. logrotate can work with coordinated close/reopen. Its [copytruncate mode explicitly permits data loss](https://github.com/logrotate/logrotate/blob/main/logrotate.8.in). Writer-owned immutable segments may be simpler when the writer is ours; no rotation implementation selected.
2. **Metrics and aggregation.** Some metrics derive from events; others need periodic state/resource sampling. Persist counters/deltas, gauges and distributions deliberately, with units/intervals/reset semantics. Precompute time buckets for dashboards and anomaly scans where needed. Averaging minute p99 values does not produce a correct monthly p99; merge compatible histograms or retain suitable raw observations. Sampling traces must not silently sample operational counters.
3. **Indexed retrieval and compression.** Indexes should answer intended queries, such as trace ID, time, operation, severity and customer context. Whole-segment compression/encryption may require reading/decompressing a large segment for a single matching record. Select segment sizes or independently readable blocks, or retain recent query data in an embedded store. An index alone does not guarantee bounded retrieval cost. Index contents can also contain sensitive data.
4. **Failure visibility.** An app can report internal failures, but a stopped app or dead host cannot issue its own alert. Add an independent liveness observer where required. A single external probe can supply that boundary without requiring an entire distributed collection architecture. Off-host telemetry preservation depends on how much investigation history must survive host loss; not a new durability decision here.
5. **Bounded operating cost.** Indexing/querying should not overwhelm application CPU/disk or let a telemetry backlog fill the disk. Make index lag, dropped records and capacity limits visible. Sharing one process is feasible; these concerns do not automatically justify another service.

The strongest objection to owning this layer is cumulative maintenance: file recovery, indexing, query semantics, aggregation, retention and an investigation UI amount to a small telemetry database/application. This can still be an appropriate owned component. Existing embedded engines may provide indexing/recovery without an external service; no reason to invent a general database or query language unless actual needs demand it.

## Proposed minimal shape
Appends to rotated structured journals → incremental, rebuildable indexes and metric aggregates → focused query/UI and periodic anomaly evaluation. Keep retained raw data authoritative for rebuilds; any aggregate intended to outlive raw retention becomes separately retained data and needs its own policy. Use one Go program with background work if it meets resource/isolation needs. An independent availability check covers process/host failure.

This is an implementation sketch, not approved mechanics. Existing analytics per-tenant journals, compression/encryption, archiving and finite raw retention still apply in their own scope. Audit records remain distinct from lossy diagnostic telemetry. OTLP output stays an optional adapter under C78; no ingestion protocol is required merely to move records within one program.

No code, file-format prototype, crash recovery test or performance benchmark performed. Later evaluation should compare representative investigation queries and normal-operation overhead against shortlisted tools, keeping the user's default preference explicit.

## Why metrics are “collected” — follow-up explanation
User asks why metrics are collected rather than written like logs, and whether the distinction is merely file format. No new architectural choice inferred.

Collection describes measuring/reading, sampling and moving observations; serialization is separate. In a usual Prometheus pull setup, the app increments in-memory counters and updates histograms when operations occur. A scraper periodically requests a snapshot of exposed metric state. Gauges may read current state at that point. Every request need not create its own metric record.

The app can instead periodically append the same counter/gauge/histogram snapshots to a local journal. This gives the same basic sampling pattern without a network collector. Metrics could share a record envelope/file infrastructure with logs; separate files are an organization/retention/indexing choice, not a mathematical requirement. A specific indexed time-series layout may improve storage/query efficiency but is not required to record metrics.

Distinguish event logs, sampled gauges and aggregated counters/distributions. Writing one metric event per operation is possible but higher volume than periodic aggregates; tracing may also sample events and cannot silently determine metric totals. Track timestamps, units, dimensions and process identity/counter resets, or emit clearly defined interval deltas. Histogram buckets/count/sum need defined aggregation semantics. A periodic gauge cannot reveal every transient between samples, irrespective of whether the sample is scraped or written locally.

A pull collector supplies central cadence/configuration, reusable exporters, a separate process to assess scrape failures and separation from the application's write path. Those are practical conveniences, not requirements imposed by metrics. Local file writing still needs a scheduling decision and failure/disk policy, but neither requires another daemon. An external observer remains necessary for detecting total host failure.

Concrete proposal: app updates small in-memory accumulators, periodically journals snapshots alongside independently appended log/span/event records, then local indexing/time aggregation supplies charts and anomaly input. Exact intervals/encoding remain unselected. This is consistent with C80 and preserves the existing analytics/audit distinctions.
