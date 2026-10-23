# Product analytics and experiments

Include analytics, experiments and feature flags from day one. Keep them in the app initially; store analytics in a database separate from primary business data. This does not require another process, server or database engine, or select storage for experiment configuration.

## Business learning
Define business measurement goals, derive required analytics, then choose the most private implementation meeting them. Broad usage analytics is normally required even for free products whose adoption matters. Privacy above required metrics needs an explicit product-owner decision.

Measure hot paths/time spent, time to value, friction and abandoned flows, conversion, retention/churn, LTV, revenue/expense drivers and useful cohorts. Instrument the funnel, monitor it and test alternatives as ongoing product work. Exact events and review cadence follow the product.

Convenience favors useful access before login when other factors are equal. Choose signup timing within the monetization/conversion funnel, then measure and test it.

Prefer concurrent A/B testing; also support sequential trials. Start with workspace-level assignment: early learning concerns signup and reaching value. Add per-user assignment as the product matures. Assignment before workspace creation, exposure/outcome tracking and evaluation mechanics still need concrete design; no vendor or statistical method selected.

## Durability and retention
Small analytics gaps are acceptable. Do not require transaction-coupled delivery merely to avoid occasional missed events. This tolerance does not apply to business, billing or audit records.

If accumulating/flushing periodically or throttling writes, default to **60 seconds**. Tune for load, generally 5–60 seconds. At barely any usage, 300 seconds may be acceptable; 3600 seconds is undesirable. Buffering itself is not mandatory.

Retain raw events initially for flexibility and reprocessing. Always set a finite raw-event retention window: **24 months by default**, including external archives. An explicit longer cap, such as 60 months, is allowed. Aggregate retention remains a separate choice.

Append-only journals are an acceptable starting storage design. If using them:
- Use per-tenant journals for B2B.
- Compress and encrypt them; archive older files externally and remove local copies.
- Expire archived raw events too; archiving is not deletion.
- At high volume, use compact binary event payloads that avoid repeated strings. Binary record framing alone does not accomplish this.

The [journal library](https://github.com/andreyvit/journal/) is a reference, not a mandated dependency or a complete analytics implementation. At scale, revisit storage cost, retention and aggregation with the product owner; do not assume raw scans remain practical.

## Separate capabilities
[Session replay](session-replay.md) is a distinct optional capture/storage/playback feature with dedicated viewing permission. Broad analytics does not automatically enable it.

[Operational observability](observability.md) covers metrics, logs and spans. Its detailed design is deferred; existing analytics requirements remain in force. [Customer-data access audit](customer-data-access.md) has its own semantics and retention. Coordinate all retained data with [export and deletion](data-rights.md).

Source: [C24–32, business and onboarding](../../../research/scaffold/83-business-and-onboarding.md), [C33–34, journals and retention](../../../research/scaffold/85-analytics-journals.md).
