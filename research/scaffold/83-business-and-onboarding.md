# Business viability and onboarding

Source: Andrey's direct interview answer, 2026-10-19.

Current recipe: [analytics and experiments](../../skills/scaffold/references/analytics.md).

## Signup timing — confirmed decision rule
- All else equal, favor customer convenience: useful access before login.
- Do not prescribe anonymous-first onboarding universally. Evaluate signup timing within the overall monetization/conversion funnel.
- Instrument the funnel with metrics, monitor its performance, and test alternatives as ongoing product work. This is a capability to provide and operate, not just a decision to justify or a promise to measure later.
- Usually we are building a business, not merely an app. Business viability belongs in architecture/recipe requirements.
- No particular signup gate, migration design, analytics vendor, event vocabulary or experimentation system selected yet.

## Recipe consequence
Cover how value reaches the customer, how the product earns money, where signup fits, and the metrics/monitoring/testing loop. Recommend a contextual starting choice; keep observing outcomes and testing alternatives. Exact events, review cadence, test methods and tooling remain open.

## Experimentation — confirmed
- Include experiments and feature flags from day one.
- Support trying alternatives sequentially even when concurrent A/B testing is not used.
- Prefer actual concurrent A/B testing; do not default to measurement-only infrastructure.
- Variant assignment, exposure/outcome measurement and evaluation details remain to be designed. No vendor or statistical method selected.

## Assignment scope — confirmed
- Start with experiment assignment per workspace.
- Early experiments focus on signups and people reaching value, not differences among users within one workspace.
- Expand to per-user assignment as the project matures; it need not be initial machinery.
- Andrey attributes this reasoning to Rob Walling. This records his stated rationale, not an independently verified quotation or a wholesale adoption of another framework.
- The assistant's colleague-consistency rationale is not the reason supplied by Andrey; lifecycle and learning priorities are.

## Analytics and privacy — confirmed order
1. Define business goals for measurement.
2. Determine required metrics and analytics capabilities.
3. Find the most private implementation that fulfills them.

Usage analytics is almost always a hard business requirement, including free apps whose adoption matters. Collect broad usage data to understand what users do and how often; do not limit measurement to a few handpicked outcomes by default. Learning from actual usage is essential to product quality and growth.

Privacy is valued **within business requirements**, not as a reason to remove necessary measurement. The exception is an explicit product-owner choice to prioritize privacy above metrics, especially when privacy is a selling point or optimization is not a goal. Open source/free status alone does not establish the exception.

### Required learning
- Hot paths and where users spend time.
- Time to value.
- Friction and abandoned flows: started but not completed.
- Conversion funnels, retention/churn and user value, including LTV.
- Revenue and expense drivers: what is charged for and what costs money.
- Useful cohort grouping and analysis across these dimensions.

Implementation may use anonymization, differential privacy or other techniques as appropriate to the user-base size. These are possibilities, not requirements to deploy sophisticated machinery immediately. Exact event capture, analytics identity, tooling and privacy mechanisms remain open. C34 below selects finite raw-event retention; aggregate retention remains separate.

This supersedes the assistant's explicit-events-only recommendation based on privacy. Broad measurement does not yet decide whether to record screen/session content.

## Hosting and storage — confirmed
Keep analytics and experiments inside the app initially, for simplicity. Use a separate analytics database from the main application database. This does not select a separate server, database engine, or storage location for experiment definitions/assignments.

Session replay is a [separate feature](../../skills/scaffold/references/session-replay.md), with a dedicated viewing permission.

## Analytics durability — confirmed
Small gaps are acceptable. Do not require transaction-coupled durable analytics delivery merely to prevent occasional missing events. This applies to analytics, not the business ledger or billing records.

**Default: 60 seconds** when using accumulate-and-flush or throttled writes. Those approaches themselves are not mandated. Load-based guidance:
- Flush every 5–60 seconds depending on load; high volume warrants shorter intervals.
- Start at 60 seconds for either approach; tune for load.
- 300 seconds pushes it, but may be acceptable with barely any usage, e.g. pre-MVP.
- 3600 seconds is undesirable.

The 60-second default is confirmed for these approaches; other timing examples guide tuning. No mandatory adaptive algorithm or database choice. Separate local databases do not imply an independently unavailable remote analytics service; the relevant ordinary gap is process failure before buffered events are persisted.

## Raw events and aggregation — confirmed
Initially retain raw events for flexibility and reprocessing. Sequential append-only journals are acceptable; B2B journals are per tenant, compressed/encrypted, with older files archived externally and removed from the server. High-volume analytics needs compact binary payloads avoiding repeated strings. At scale, explicitly revisit cost, retention and efficient aggregation. [Details and journal reference](85-analytics-journals.md).

## Raw-event retention — confirmed
Use a finite window: **24 months by default**, including external archives. Product owners may explicitly choose a longer cap, e.g. 60 months. [Reasons](85-analytics-journals.md).
