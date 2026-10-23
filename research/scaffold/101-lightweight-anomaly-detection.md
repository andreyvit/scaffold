# Lightweight anomaly detection

**Deferred · C81 · 2026-10-23:** preserve these options; Andrey will experiment himself before making more detailed recommendations. No further selection, design or trial work now. Existing preferences remain recorded; proposals are not approved defaults.

## Scope · 2026-10-23
Andrey asks whether lightweight anomaly detection exists alongside the inspectability candidates. C75 already records intended anomaly monitoring on selected metrics. This note extends the try-later research under C79; no new tool, algorithm or deployment decision is confirmed.

Primary documentation review only. No installation, benchmarks, detection-quality evaluation or dependency/maintenance audit. Prefer plain Go and one-server simplicity; distinguish an embeddable detector from collection, storage, visualization and alert delivery.

## Options to try later
| Option | Fit | Qualification |
|---|---|---|
| [Grafana PromQL anomaly-detection rules](https://github.com/grafana/promql-anomaly-detection) | Recording and alerting rules run in Prometheus; no separate model service or Grafana Cloud required. Adaptive mean/deviation and robust median/MAD strategies; daily/weekly seasonal bands | Requires a suitable Prometheus/rule setup. Evaluate selected rule/function compatibility if using a different backend. History warmup and rule evaluation have costs; demo is not a production deployment |
| [Anomalyzer](https://github.com/lytics/anomalyzer) | Go library comparing current and reference windows with configurable statistical tests | Scoring component, not a service/UI. Older project; inspect current dependencies and maintenance before adoption. Bootstrap tests cost more than simple rolling statistics; returned scores are not established incident probabilities |
| [anomalia](https://github.com/project-anomalia/anomalia) | Small Go library for time-series anomaly scoring and correlation | README says under development; CLI and benchmarks are roadmap items. Needs integration and quality/maintenance review |
| [Netdata built-in detection](https://learn.netdata.cloud/docs/netdata-ai/anomaly-detection) | Local metric collection with automatic k-means anomaly classification; integrated monitoring experience | A monitoring agent/platform, not a plain-Go detector to embed. [Cloud is optional](https://github.com/netdata/netdata); verify actual resource use and required business-metric coverage |
| [VictoriaMetrics vmanomaly](https://docs.victoriametrics.com/anomaly-detection/) | Separate service reads selected metrics and writes anomaly scores, predictions and bounds | Python service; Enterprise license required even with open-source VictoriaMetrics. Useful comparison, not the smallest plain-Go fit |
| Small owned detector | Embed rolling/seasonal baselines and scoring into an existing Go process | Requires explicit modeling, scheduling, persistence, notification policy and validation; proposed option, not a selected implementation |

## Useful distinctions
The PromQL project is a set of rules, not a requirement to adopt Grafana Cloud or the full demo stack. Its documented strategies use recent variability, minimum band width, and daily/weekly historical patterns. Most strategies need 24–26 hours for initial warmup; useful weekly comparisons require the corresponding history. Treat the README's performance claims as unverified for our workload.

Prometheus supplies [time-series functions](https://prometheus.io/docs/prometheus/latest/querying/functions/) for averages, quantiles and deviations. Current mad_over_time and double_exponential_smoothing require the experimental-functions flag. Double exponential smoothing models level/trend, not full seasonal Holt-Winters behavior. A small PromQL subset such as owl's is not automatically compatible with the complete framework.

Netdata classifies collected metric behavior locally and stores anomaly indicators alongside metric history; alert rules can use [anomaly rates](https://github.com/netdata/netdata/blob/master/src/health/REFERENCE.md). This is distinct from a generic business-metric forecasting service. Do not repeat claims that it eliminates noise or proves root causes.

[vmanomaly quickstart](https://docs.victoriametrics.com/anomaly-detection/quickstart/) documents the Python service entry point and license requirement. VictoriaMetrics being Go/open-source does not make every companion component so.

## Earlier assistant recommendation — superseded as default by C80
C80 prefers file-based telemetry/indexes and treats Prometheus/PromQL as soft exceptions. Embedded anomaly evaluation over stored aggregates is now the closer starting point. Keep the options above for later trials; no algorithm selected.
Try the PromQL rules first if the selected metrics backend supports them. For an owned Go backend, start by comparing small baseline detectors: recent smoothed level for nonseasonal metrics, or comparable hour/weekday history for seasonal metrics, with a robust spread estimate and minimum band width. The detector can run periodically within the existing process; a separate ML service is not inherently required.

Score rates or interval counts rather than raw cumulative counters. For conversion/error ratios retain the denominator and require enough observations. Separate missing telemetry from zero, allow warmup, and require meaningful/persistent deviations before notifying. Daily/weekly seasonality needs enough representative history; a recent-window mean alone will flag routine daily changes.

Detection-quality trials should replay historical data in time order with only past data available to the detector. Compare false alerts, missed incidents and detection delay, plus runtime/memory. Simple synthetic spikes can check mechanics but do not validate usefulness. Keep fixed failure alerts alongside anomaly detection and preserve operator-controlled production recovery. No specific model or thresholds approved.
