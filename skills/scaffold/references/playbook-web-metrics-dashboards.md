# Great web metrics dashboards, uptime status boards and health dashboards

Research completed 2026-11-07. Browser-based products for individuals and small teams; larger products serve as references. Health means system/service health. Public status, internal operations, business metrics and unattended wallboards have different jobs. No locale restriction supplied.

Research recommendations are not confirmed scaffold defaults. Existing observability preferences remain unchanged.


**Build trust before adding charts:** define the decision, preserve measurement meaning, show freshness and uncertainty, and make the next action clear. Public status, diagnosis, analytics and wallboards need different views.

Reading guide: [build order](#build-order-and-choices-to-test) · [products/business](#products-and-business-evidence) · [visual directions](#visual-directions) · [110 details](#screens-and-components-110-practical-details) · [architecture](#architecture-choices-that-change-the-product) · [compatibility](#compatibility-supported-targets-and-real-costs) · [82 ecosystem entries](#named-ecosystem-catalog) · [avoid/migrate](#named-choices-to-avoid-migrate-or-limit) · [sources/method](#sources-and-method).

## Purpose before layout

Separate four jobs: monitor a condition, investigate a cause, communicate impact, and review business performance. A wallboard adds distance and unattended operation; it is a viewing mode, not a universal information model. Few's 2007 essay distinguishes monitoring from analysis. Later dashboard research describes broader genres rather than enforcing one screen everywhere. Keep the glanceable overview; allow scrolling and drill-down where the task needs them. [Few, 2007](https://perceptualedge.com/articles/visual_business_intelligence/dboard_confusion_revisited.pdf); [Bach et al., 2022](https://arxiv.org/html/2205.00757).

The 2022 study examined 144 dashboards and ran a two-week workshop with 23 participants. Its patterns are descriptive, not proof of business or usability gains. Its sample includes 36 COVID dashboards. Use it to discuss alternatives, not to claim every dashboard needs a feature. [Paper](https://arxiv.org/html/2205.00757).

Independent designer Data Rocks accepts Few's lessons on context, precision, color and layout, but criticizes his narrow definition and dismissive treatment of newer approaches. This is a useful disagreement: one-screen monitoring fits wallboards; forcing analytical or mobile use into that rule can hurt comprehension. The review covers the 2013 second edition; the book itself was not fully inspected here. [Review](https://www.datarocks.co.nz/blog/data-viz-bookshelf_information-dashboard-design-stephen-few).

## What “great” means here

Evaluate these separately; one success does not establish the others.

| Meaning | Useful evidence for this category | What can mislead |
| --- | --- | --- |
| User love | Reassurance, confidence in definitions, fast repeated tasks, voluntary recommendations; see independent-use accounts below | A beautiful screenshot, selected testimonials, NPS without sample size |
| Problem solving | Detect a missed job, locate an affected region, explain a queue, make an incident update useful | More charts, more refreshes, more raw telemetry |
| Adoption and retention | Successful first connection, returning use where needed, maintained checks, renewals and cohort survival | GitHub stars as active installations; free accounts as a conversion cohort; visits as value |
| Cash earned | Net paid subscriptions and collectible usage; distinguish annual cash from MRR | ARR projections as bank balance; tax/refunds/currency mixing |
| Viable business | Capacity, margins after labor, dependable support, owner continuity and affordable integrations | Revenue without workload or cost; acquisition as a promise of continuity |
| Maintainable code | Clear metric contracts, bounded queries, few owned layers, tested upgrades and exports | A small frontend over an unbounded or fragile ingestion system |
| Featured | A working, distinctive product and a reviewable task; see editorial evidence below | Launch votes as retention or guaranteed press coverage |

This table is a decision framework synthesized from the report, not a scored industry ranking. Public data cannot establish the most profitable dashboard business or the most loved product across the entire market.

## Build order and choices to test

These recommendations apply to a new small-team product. Select the product job first; do not implement all branches.

1. **Define the promise.** Specify audience, decision, service boundary, measurement, delay tolerance and failure response. For “Is checkout working?”, an HTTP home-page check is insufficient. For “Did backup finish?”, a heartbeat deadline may be enough. Use the product and architecture comparisons in this report.
2. **Build one trustworthy vertical slice.** One source → validated records → explicit aggregation → useful overview → drill-down or incident history. Include unknown, late, empty and failed states immediately. Prove that time, units and denominators survive the whole path before adding more cards.
3. **Make the first real success obvious.** Give a minimal integration, safe sample view, receipt confirmation and one useful result. Add guided defaults without removing expert exploration. The Console interview and Healthchecks accounts support this direction; neither supplies a universal conversion uplift.
4. **Test the bad day.** Disconnect sources; expire credentials; inject old/out-of-order samples; saturate queries; restart a kiosk; restore storage; simulate incident readership. The board must distinguish service failure from monitoring blindness. Notification delivery needs its own end-to-end test.
5. **Add sharing appropriate to the job.** Public status needs safe publishing and subscriber updates. Internal diagnosis needs scoped links with frozen time. Business review needs timestamped exports and definitions. A public URL is not the default answer for private operational metrics.
6. **Budget growth before free ingestion.** Limit costly backfill, retention, cardinality, probe frequency and notification bursts. Measure support time per connected account. The Baremetrics failure shows why signup conversion is an insufficient guardrail.
7. **Expand the useful workflow.** Add a second source, templates, comparisons or alert context only when it removes a repeated step. Decide whether users need a flexible builder or a carefully maintained fixed view. Flexibility brings saved-state migration, support and authorization costs.
8. **Invest in durability.** Version definitions and layouts; make backup/restore and exports usable; publish support boundaries. Test upgrades with old data and large configurations. Ducksboard's history and Kuma migration reports make this a product concern.

**Expected basics:** clear current state, observation age, interval/zone, units and definitions; useful default view; accessible controls and data alternative; scoped authorization; honest errors; reliable notification testing where alerts exist.

**Useful differentiators:** explain why a state changed; connect a metric to a representative event; surface the affected customer workflow; provide genuinely readable mobile triage; make team setup and vendor migration easy. These are proposed opportunities, not proof of market demand.

**Costly traps:** building a general query language before one real question works; copying an enterprise observability stack without its need; arbitrary animation; unreliable free checks at unlimited scale; dozens of shallow connectors; making a status page depend on the failing system; confusing monitoring tools' internal health with customers' experience.

**Experiments worth running:** compare guided setup with blank configuration using time-to-first-valid-signal and seven-day successful monitoring; compare focused and customizable overviews using task accuracy/time; compare contextual onboarding with tours using completed useful setup; compare pricing gates using paid upgrades plus invitations, support cost and churn. Predefine cohorts and guardrails. Do not reuse vendor improvement percentages as forecasts.

## Products and business evidence

This shortlist maps products to jobs, not an overall ranking. Evidence and qualifications follow; larger references are labelled.

| Product | Best-fitting job | Strongest quality | Main limit | Supported meaning of great |
| --- | --- | --- | --- | --- |
| Healthchecks.io | Missing cron/background jobs | Narrow, legible promise | One-person operational continuity | Problem fit, paying longevity; some user affection |
| Plausible | Small-team web analytics | Focused overview and export | Scope and overage policy need scrutiny | Adoption, retention evidence, reported revenue |
| Oh Dear | Agency/site health | Coherent monitoring bundle | Bundle price; no formal SLA | Problem fit; selected long-term user accounts |
| Uptime Kuma | Self-hosted service checks | Glanceable admin/public views | Upgrade/backup and large-fleet workload | User affection, control; finances unestablished |
| Gatus | Code-managed health checks | Explicit check conditions | Configuration-oriented audience | Maintainability/fit hypothesis, not measured revenue |
| Geckoboard | Team wallboards | Distance-oriented shared metrics | Connector/platform costs | Larger reference; reported workflow outcomes |
| Grafana | Technical diagnosis | Broad query/visualization ecosystem | Operational and UI complexity | Larger reference; flexibility, not simplicity for all |
| Linear status / incident.io | Customer status communication | Quiet hierarchy and accessible history summaries | Desktop sample only; no outcome study | Larger reference; visual/semantic execution |


Financial disclosures below are founder/vendor claims, not audited accounts. Prices checked 2026-11-07; historical figures retain their dates.

### Business premise

Sell an outcome: detect missing work, explain an incident, reduce queue delays, reconcile revenue, or replace manual reporting. A dashboard is the surface. Freshness, correct definitions, dependable ingestion and response workflow determine its continuing value. This is an inference from the cases below, not an experimentally measured universal rule.

## Independent/small-team success examples

### Healthchecks.io — narrow scope and candid operations

[About/open data](https://healthchecks.io/about/), manually updated November 1, 2026: one-person company; 11 years operating; 1,420 paying accounts; $29,300 MRR; 199,000 free accounts; 645,000 checks; 134 million pings/day. Vendor says profitable/sustainable. These are not a conversion cohort: dividing paying by free accounts would misstate conversion. Strength: sharply defined missed-job problem, simple UI/API, self-hostable BSD code. Weakness: founder explicitly warns that one-person operations and manual DB failover permit multi-hour or multi-day outages. Reported historical availability >99.9% is distinct from an SLA. Good evidence of durable small-business value; no disclosed net profit or workload ledger.

[Unlimited Team Sizes for All](https://blog.healthchecks.io/2026/02/unlimited-team-sizes-for-all/), February 18, 2026: removed team-member limits because years of account data showed upgrades overwhelmingly followed check limits; team-size-driven upgrades were rare. Simpler code/pricing/docs is an observed design consequence. More word of mouth through invitations is the founder's hypothesis; no measured lift yet. This supports checking which restriction earns money before charging for collaboration; it does not prove all seats should be free.

[Pricing](https://healthchecks.io/pricing/), current: free 20 jobs/100 log entries per job; $5 supporter has identical limits; $20/month buys 100 jobs/1,000 log entries, $80 buys 1,000 jobs. Annual billing saves 20%. SMS/WhatsApp/phone credits are capped. Cancellation has no prorated refund, except mistaken-account upgrades. Explain retention in time as well as record counts: At one stored entry per run, 100 entries cover ~8 hours for a five-minute job or ~2 years for a weekly one; extra start/error/log pings shorten coverage. Capacity pricing, storage history and notification cost belong together.

[FAQ](https://healthchecks.io/docs/faq/): self-service purchasing, published common prices; no vendor-management-platform enrollment or questionnaires. This deliberately rejects support-heavy procurement work. Late payments receive retries and weekly notices; >60 days past due triggers downgrade. Eventually over-limit abandoned accounts may be deleted after warnings. This documents a small-team business boundary, not a universal sales strategy.

[Hosting Q&A](https://blog.healthchecks.io/2022/05/healthchecks-io-hosting-questions-and-answers/), May 27, 2022: approximate €800/month infrastructure cost; integrations added incrementally; Signal particularly costly to implement. Founder sees open source as likely positive commercially but explicitly cannot establish causation. Historical cost excludes a complete salary/tax/support model and must not be subtracted from 2026 MRR to invent current profit. His candid bus-factor concern complements the current availability disclosure.

### Plausible — clear alternative to a dominant free incumbent

[$1M ARR story](https://plausible.io/blog/open-source-saas), June 22, 2022: four-person, self-funded team; >7,000 paying subscribers; >50,000 tracked sites; >1 billion monthly pageviews. Took 324 days to reach $400 MRR; early traction was slow. No paid advertising reported. Positioning combines simple one-page analytics, privacy and open-source inspection, with paid managed hosting. Marketing partnership and topical writing were part of growth; do not credit UI simplicity alone. Early Hacker News traffic to a generic technical essay did not establish immediate sales value. Developer-reported profit, no audited margin.

[Current about page](https://plausible.io/about/), read November 7, 2026: 11-person team, self-funded/profitable claim, subscription-only funding; >2,400 teams have paid for five years or longer. That is meaningful longevity evidence, but not a retention rate without the initial cohort denominator. Product fit: owners who need traffic answers quickly. Boundary: its deliberately reduced scope is not a substitute for full behavioral analytics, financial reconciliation or operational health.

### Simple Analytics — transparency with visible measurement limits

[Open dashboard](https://dashboard.simpleanalytics.com/open), read November 7, 2026: approximately $49.6k MRR, 1,291 paying customers, ~$595.8k ARR. The page explains that its intermediate “unified currency” simply sums USD/EUR/GBP units, then presents a converted estimate. This is not audited GAAP revenue. It also says its profit chart is 950 days stale while MRR updated minutes ago. Excellent teaching example: freshness belongs to each metric, not just the page. NPS 50 over 30 days versus 57 all-time lacks visible respondent counts; don't rank customer love from it. Strong evidence of paying demand, weak evidence of current profitability. Its public dashboard can demonstrate the product and build trust; no controlled acquisition lift is disclosed.

### Oh Dear — a coherent bundle for agencies/site owners

[Pricing](https://ohdear.app/pricing/), read November 7, 2026: all features on every plan; limits based on sites/servers, not seats. EUR monthly prices exclude VAT: 2 sites €15, 10 €49, 25 €99, 50 €149. Ten-day no-card trial, 30-day first-payment refund; annual billing gives two months free. Includes uptime, SSL, links, DNS, cron, status pages, SSO and unlimited users. Agency fit: branded pages/reports and client read-only access. Tradeoff: buyers needing only one probe may not value the bundle. Testimonials on this sales page are selected vendor evidence; no revenue/profit or comparative false-alarm benchmark disclosed.

[Terms](https://ohdear.app/terms), January 19, 2026: no formal uptime SLA/service credits; reselling monitoring as its own service requires reseller agreement, while monitoring client sites within broader development/IT service does not. The distinction affects agency economics. Don't infer a contractual guarantee from polished “enterprise” language.

## Larger references, not indie-success rankings

[Geckoboard pricing](https://www.geckoboard.com/pricing/), current: Essentials from $79/month annually, two dashboards/one editor/one screen; Performance $319, twenty dashboards/three editors/five screens. Unlimited viewers; higher plan adds alerts, drilldowns, templates, ownership/verification. Enterprise offers custom metric work, procurement support and training. Useful product distinction: TV display, passive sharing and active analysis have different jobs and costs. Its connector count is not evidence of connector accuracy; inspect relevant data-volume limits. No profit inference from pricing.

[Better Stack pricing](https://betterstack.com/pricing/), current: free personal tier has 10 monitors/heartbeats and one status page. Responder $34/month or $29 annually; team members without responder access free. Status-page white labeling and SSO each $250/page/month monthly; password protection $50; additional page $15. Subscriber additions and telemetry usage add dimensions. Sixty-day money-back guarantee. Compare a whole intended configuration, not the starting price. Integrated monitoring/incident workflows are convenient, but the bill can hinge on branding/security, beyond check count. This is a product/packaging reference, not evidence of indie economics.

[Atlassian Statuspage pricing](https://www.atlassian.com/software/statuspage/pricing/), current: public free plan 100 subscribers/25 components/two team members/two metrics; Hobby $29, Startup $99, Business $399, Enterprise $1,499 monthly. Component subscriptions and role controls start at Business. Public, private and audience-specific pages have separate pricing. Statuspage sells communication and distribution; do not compare it solely with a single HTTP probe. Need-based notifications may be commercially gated, which matters when evaluating fit for a large mixed audience.

## Outcomes, experiments and their limits

**Baremetrics freemium failure, November 2015.** [Founder report](https://baremetrics.com/blog/freemium-saas-implode): >1,000 free signups in 11 weeks; only 461 eligible for paid product; 53 upgraded (11.5%), almost $5k new MRR at ~$90 ARPU. Data/processing load doubled; support population tripled. Delayed/inaccurate metrics and outages followed; almost 60 paying customers left, revenue churn doubled. Existing distribution included 7,000 email subscribers. This is a confounded before/after, not proof freemium fails. It is strong evidence that conversion alone can conceal damage to paying users. Founder switched to full-feature 14-day trials with processing stopped afterward. Bound imports, compute, retention and support before making ingestion free.

**Independent challenge to that interpretation.** [Contemporaneous HN discussion](https://news.ycombinator.com/item?id=10540377), November 10, 2015: readers argued capacity planning failed despite good conversion. Founder clarified departing customers predated free tier and cited technical/service problems learned through exit discussions. Others strongly objected to mandatory contact for cancellation. Preserve disagreement: a healthy signup metric, poor operational preparation and damaged trust can all coexist.

**Baremetrics churn intervention.** [Founder account](https://baremetrics.com/blog/how-we-reduced-churn) claims user churn fell ~10%→3% (reported 68% reduction), revenue churn ~13%→5% (63%), after two months combining required contact to cancel, new historical plan breakdowns/time grouping, and education. It reports saving ~15% of cancellation requests. No control group, sample counts or durable follow-up; rounded values explain approximate arithmetic. Current page labels May 2024/updated October 2026, but the 2015 HN thread already links it: treat as historical, not a 2026 experiment. Do not recommend obstructing cancellation from this result. Better test visible useful features, contextual teaching and optional exit help while keeping self-service cancellation.

**Sycous and Geckoboard.** [Vendor interview](https://www.geckoboard.com/blog/how-sycous-reduced-dropped-calls-by-97-with-geckoboard/), May 5, 2023: analyst previously spent an hour/day assembling Zendesk reports; agents saw metrics monthly. Live call-queue visibility plus scheduled snapshots reportedly reduced dropped calls 97% within months. Incentives changed too. No raw count/time-series or control; claim cannot isolate dashboard effect. The quoted rough “double digits” baseline and “2 or 3 on a bad day” are insufficient to independently recompute 97%. Useful mechanism: put an actionable queue in front of people who can answer calls while calls still wait. Don't extrapolate that percentage to all dashboards.

**Statuspage support deflection.** [Atlassian article](https://www.atlassian.com/blog/statuspage/why-you-need-a-status-page), December 4, 2019: customers reported 24% fewer support tickets. Article lacks sample size, sampling method and controlled comparison; vendor-selected self-report. Read as plausibility evidence for support deflection, not forecastable savings. Separate uptime service hosting from the failing application, publish partial failures, and put updates where affected customers look. Its extrapolated ticket-saving estimate from pageviews is speculation, not measured deflection.

**Controlled UI evidence is thinner.** [GoodUI public test catalog](https://goodui.org/tests/filter/metric/signups-trials/power/5/page2) documents Baremetrics test #357 (June 2, 2021): focused signup vs comparison table, n=4,947; #351 (April 30, 2021): static integrations vs selectable explanation/CTA, n=24,416. Results/effects are membership-gated. Public listed power for a 5% minimum detectable effect is only 5.5% and 7%. No winning direction or sales lift can be asserted. Searched founder accounts and public experiment catalogs; public dashboard-specific causal conversion evidence remained unavailable. Use these as test ideas, not proven uplift recipes.

## Economics to model explicitly

The following is a proposed accounting checklist derived from cases, not sourced average costs:

- Revenue: paid accounts × net recurring price; distinguish MRR, annual prepaid cash, recognized revenue, discounts, refunds, tax and currencies.
- Acquisition: content/community labor, partner commissions, support-assisted trials and paid acquisition. “No ads” does not mean zero CAC.
- Direct costs: ingest volume, backfills, retention, replication, queries, egress, browser/cron checks, regional probes, notifications and bursts during incidents.
- Labor: integration breakage, source-schema/API changes, reconciliation, onboarding, abuse, billing, security review, support and 24-hour availability.
- Resilience: independent status hosting, failover/restore drills, spare capacity, notification-provider alternatives and operator coverage.
- Margin: calculate after infrastructure, processor/refund costs, paid labor and realistic founder compensation. None of the reviewed open dashboards supplies enough current cost detail to compare audited net margins across products.
- Price by a unit customers understand and can budget; align allowances with expensive work. Test whether limiting editors, viewers, monitors, subscribers, history or security actually drives upgrades or only blocks adoption.
- Internal dashboards need no standalone subscription business: compare prevented incidents/time saved with build, data correctness and maintenance costs. Public board readership is not retention; quiet background monitors can be valuable with few UI sessions.


## Shutdown and continuity

**Ducksboard.** [New Relic acquisition release](https://newrelic.com/press-release/20141008?is_us=true), October 8, 2014: >700 business customers, >50,000 dashboards, 65 integrations; continued standalone offering promised then. [June 6, 2016 user thread](https://news.ycombinator.com/item?id=11848797) (full text read through [Algolia API](https://hn.algolia.com/api/v1/items/11848797)) asks where to migrate before shutdown and praises its friendliness versus clunky alternatives. [AlternativeTo listing](https://alternativeto.net/software/ducksboard/?p=2) marks discontinued. Acquisition success and user continuity differ. No verified owner shutdown rationale found; don't attribute closure to bad UX or failure to monetize. Lesson/inference: retain metric definitions, exportable config/data, and a migration path when source vendors or dashboard vendors disappear.

## Independent reviews, switching and distribution

**Healthchecks/Uptime Kuma user love, with a discoverability gap.** [r/homelab discussion](https://www.reddit.com/r/homelab/comments/1aqoy5k), February 2024, full thread read: original author values explicit expected-run deadlines and reports pleasure from seeing both dashboards green. Other users praise one-command setup, optional richer start/stop/error data and self-hosting. A years-long Healthchecks user had never discovered start/end timing until this discussion. This is unusually concrete emotional appeal: reassurance from expected work finishing, plus progressive depth. Inference: show one minimal integration first, then surface duration/error capture beside the first successful check. Positive self-selected comments are not a satisfaction survey. A later reply reports iOS ntfy delivery failure; it illustrates the need for end-to-end alert testing, not proof that Kuma itself lost notifications.

**Uptime Kuma: strong glanceability, weak rebuild workflow in one review.** [Matthew Hunter](https://matthewjayhunter.com/post/reviews/software/uptime_kuma/), March 25, 2026, reports several weeks' use: easy Docker setup, readable service state, useful admin/public separation, email notification setup and broad check types. He objects to groups that do not inherit intervals, a broken/deprecated backup control, and DB-owned configuration that makes rebuilds awkward. No exact app version supplied; do not generalize his API claims. [Current v1→v2 migration guide](https://github.com/louislam/uptime-kuma/wiki/Migration-From-v1-To-v2), edited April 28, 2026, explicitly says JSON backup/restore was removed and `data` directory backup is the supported method. Therefore his visible-broken-backup criticism is historical/version-dependent, while preservation and migration testing remain current costs. The guide reports a seven-minute migration for 20 monitors/90 days; slower/larger instances can take hours, and interrupted migrations need backup restoration. No “cannot back up” conclusion.

**Plausible: expert use under a real traffic spike.** [Simon Willison](https://simonwillison.net/2023/Feb/17/analytics/), February 17, 2023, explains using Plausible during a roughly 1.1M-pageview article spike. He likes the focused data subset, open source/privacy and no cookies. Its ZIP-of-CSVs export enabled further work in Datasette; Cloudflare required API extraction. He identifies different collection methods, page filters and time zones when comparing results. This is direct expert use, with exported data linked, rather than a generic endorsement. Inference: offer simple overview plus export; do not force every advanced analysis into the dashboard or imply that different source counts prove one is inaccurate.

**Plausible: older independent review shows why dates matter.** [Ben Hoyt, LWN](https://lwn.net/Articles/822568/), June 17, 2020, directly tried GoatCounter and Plausible. He found Plausible more visually polished, but its then-experimental self-host install failed on a migration; GoatCounter installed readily. He questioned unclear bounce-rate definition and limited export granularity. These are historical findings, not current bugs/license/stack facts. The useful durable comparison is hosted visual polish versus install, definition and portability quality. Don't import its old MIT license or vanilla-JS description into the current stack catalog.

**Oh Dear: independently hosted review records, material recruitment bias.** [Capterra review page](https://www.capterra.com/p/190028/Oh-Dear/reviews/) search retrieval returned full individual review records, including dates and incentive disclosures; direct page fetching failed due to `text/markdown` handling. Matt R. (December 18, 2024, >2 years) praises reliability plus broken-link bundle after Jetpack, but misses a mobile dashboard. André K. (January 10, 2026) praises manageable snooze/maintenance options and useful client metrics; asks for better multilingual-URL guidance and notes a pure uptime tool could be cheaper. Chris P. (February 4, 2025, >2 years) likes Laravel application health and client reporting but reports occasional graphs failing to load. These records were vendor-referred and incentivized. They are specific user accounts, not independent sampling or verified present-day defects. Do not count Capterra/GetApp/Software Advice copies as separate corroboration.

**Plausible: billing trust complaint verified against current rules.** [Software Advice reviews](https://www.softwareadvice.com/product/464707-Plausible-Insights/) search retrieval returned full records; direct fetch failed (`text/markdown`, then 403). Rob H. (November 2023, organic review) likes simple daily use but misses path tracking. Nicu C. (February 2024, organic) praises easy install yet objects to losing dashboard access after sustained overages despite annual prepayment. [Current subscription docs](https://plausible.io/docs/subscription-plans), updated October 29, 2026, confirm a single spike month needs no upgrade; after two over-limit months the customer gets notice, then dashboards lock if no upgrade within a week. Collection continues; settings remain available; downgrade/upgrade prorates. Explain these states before purchase and before the limit. Current Business includes user journeys, so the old path-tracking criticism cannot stand as a current absence. A separate March 2022 incentivized reviewer found active properties/filters hard to notice—useful hypothesis for filter visibility tests, not current audit evidence.

**Industry featuring has concrete criteria, not guaranteed sales.** [Product Hunt featuring guidelines](https://help.producthunt.com/en/articles/9883485-product-hunt-featuring-guidelines), March 10, 2026: live digital products; useful, novel, crafted or creative; strength in one or two can suffice. Minimal undifferentiated monetization products and waitlists without immediate access are poor candidates. Editorial choice is distinct from votes; no inclusion guarantee. [How Product Hunt works](https://help.producthunt.com/en/articles/17734306-1-how-product-hunt-works) says real engagement matters and purchased votes can cause removal. For a metrics app, a working demo with meaningful example data and a clear novel task is stronger submission material than attractive empty chart scaffolding. That last sentence is inference, not a platform rule or measured conversion promise.

**Expert publication coverage rewards a useful technical stance.** [Thoughtworks Radar](https://www.thoughtworks.com/radar/techniques/privacy-focused-web-analytics), April 13, 2021, placed privacy-focused web analytics at Assess, using Plausible as an implementation example. Its rationale included avoiding intrusive consent UX. This was a technique mention, not a current “Adopt Plausible” award; the page explicitly says it is outside the current edition. LWN's above comparison is another verified industry feature. Evidence supports privacy, simplicity and accessible implementation as newsworthy distinctions in those publications, not a universal editorial checklist.

**Distribution beyond precisely attributed clicks.** [Sentry's two-year follow-up](https://blog.sentry.io/two-years-without-cookies-on-the-site/), April 27, 2026: reports no return to advertising cookies, ~70% growth budget to awareness, self-reported attribution and annotated weekly signup trends. Start with audience-specific technical communities, expand channels in stages. Sentry is a larger company; sports sponsorships and its budget split are not indie defaults. Its claim of growing activated users alongside marketing changes is not causal proof. Dashboard implication: show campaign annotations and attribution uncertainty; do not make trackable last-click activity look like the entire business.


## Independent long-term reports: mixed experience, useful failure cases

In [r/UptimeKuma’s comparison thread](https://www.reddit.com/r/UptimeKuma/comments/1owlsfj/statusheroio_vs_uptimerobot_vs_uptimekuma/), one user reports switching from UptimeRobot a year earlier over cost and monitoring roughly 180 endpoints. Another reports a year of successful Kuma use for about 75 sites. A user with over 700 endpoints reports slow dashboard loads and reluctance to recreate configuration to change databases. Others report good v2 performance around 250 monitors. These are unverified, self-selected reports with different versions, databases and hardware; they establish test cases, not a scale limit or benchmark. Product lesson: test large saved configurations and long history, and make migration discoverable before asking users to rebuild years of setup.

In [r/selfhosted’s alternatives thread](https://www.reddit.com/r/selfhosted/comments/1m1g5mt/looking_for_alternatives_to_uptime_kuma/), the requester reports increasing instability and values grouped notifications, ping, DNS and HTTP assertions. A Gatus user prefers configuration files over manual setup; another Kuma user reports no problems around 100 endpoints. A commenter claims no migration exists, then acknowledges missing the linked instructions. This disagreement supports two design needs: accommodate both code-managed and UI-managed fleets when serving those audiences; make migration paths visible. It does not establish that every dashboard needs both configuration models. Do not adopt commenters’ blanket claims that a database change fixes every issue or that a language guarantees speed.

## Podcast: guided entry without trapping exploration

Read the full published transcript of [Console DevTools S02E03, Charity Majors, 2022-01-20](https://console.dev/podcast/s02e03-observability-charity-majors-honeycomb), 27:37. Did not listen to audio or inspect video; a native transcript made video ingestion unnecessary.

Majors describes Parse’s difficulty diagnosing unfamiliar failures from preselected dashboards, contrasting this with iterative filtering of high-cardinality events. More surprisingly, she says Honeycomb’s onboarding improved when an empty query interface became a familiar landing page showing errors, latency and request rate, alongside automatic instrumentation. These are founder recollections, not controlled conversion measurements. Her near-zero churn and roughly 90% fewer paging alerts claims lack a cohort, observation period and independent audit here; do not repeat them as benchmarks.

Useful synthesis: **give novices a meaningful first view, then let them leave its assumptions.** A dashboard should offer a path from “something changed” into cohorts and individual events; it should not require users to predict every future failure. Her claim that time-series tools are not “observability” reflects a disputed definition and her product position. It does not invalidate inexpensive metrics for bounded health questions or require an indie developer to build a database.

## Industry coverage: what reviewers actually inspect

[TechRadar’s monitoring roundup, updated 2025-03-20](https://www.techradar.com/best/best-website-monitoring-software), discloses affiliate links and describes testing trial accounts, induced outages, integrations and support responses. It praises Uptime.com’s range of checks and escalation, UptimeRobot’s affordability, and Site24x7’s breadth. This is evidence of editorial selection criteria, not independent revenue or retention data. The article’s unlinked claim that more than 9% of visitors never return after downtime should not be used as a measured conversion result. For press readiness, provide a testable onboarding path, demonstrable outage/recovery, clear plan limits and responsive support; no source proves these guarantee coverage.


## Findings that change the design

- **Treat reported uptime as a defined calculation.** Statuspage history comes from component states, not automatic proof of successful requests. Partial outages count as 30% of major outage duration; incidents that do not change component state need not appear in component history. This is a concrete reason to disclose methodology and never compare unlabeled uptime percentages. [Statuspage historical uptime](https://support.atlassian.com/statuspage/docs/display-historical-uptime-of-components/).
- **Live updates can defeat investigation.** Grafana issue #112604, opened 2025-10-17, reports disappearing tooltips under live refresh, preventing data-link and annotation actions; the maintainer closed it as expected behavior on 2025-11-05. Reported version: 12.2.20/Chrome. Current troubleshooting docs recommend disabling live refresh or increasing intervals. Do not claim all current Grafana versions reproduce it. [Issue](https://github.com/grafana/grafana/issues/112604), [documentation](https://github.com/grafana/grafana/blob/main/docs/sources/visualizations/dashboards/troubleshoot-dashboards/index.md).
- **Dual axes are disputed, not universally forbidden.** Grafana recommends them for differing units/ranges. Datawrapper’s 2018 critique warns arbitrary scales imply relationships; its July 2026 revision accepts specialist uses and now offers the feature. Default to aligned small multiples or indexing for general readers; retain explicit dual axes where trained users need them. [Grafana guidance](https://grafana.com/docs/grafana/latest/visualizations/dashboards/build-dashboards/best-practices/), [Datawrapper updated critique](https://www.datawrapper.de/blog/dualaxis).
- **Silence destroys status-page usefulness.** A 2025 r/sysadmin thread complains about unacknowledged outages. A commenter describes engineering updates delayed by messaging approvals, then customer-service ownership producing vague, late updates. These are unverified individual reports, not proof about named vendors. The useful failure mechanism is divided authority; prepare plain-language templates and an owner before an incident. [User discussion](https://www.reddit.com/r/sysadmin/comments/1k9sjxa/to_vendors_please_use_your_status_pages/).
- **Dashboard screenshots cannot prove incident readiness.** Google’s free SRE books discuss actionable alerts, false-positive cost and low-traffic edge cases. They support testing decisions and signals under failure, not requiring Google’s scale or tooling. [Monitoring chapter](https://sre.google/sre-book/monitoring-distributed-systems/), [Alerting chapter](https://sre.google/workbook/alerting-on-slos/).

## Direct visual and interaction inspection

Inspected public browser views on 2026-11-07 at the available desktop viewport. No account creation, private telemetry, device lab, screen-reader session, prolonged use or performance benchmark. The observations below support appearance and the named interactions only.

- **Linear status, powered by incident.io:** narrow centered column; charcoal surfaces; restrained borders; explicit overall status above regional component rows; green historical bars with amber/red exceptions. History images expose text summaries including dates and incident categories in the accessibility tree. A calendar and subscription/report-problem actions follow the same simple hierarchy. This is a larger-product reference, not evidence about indie finances. [Live page](https://linearstatus.com/).
- **Plausible public demo:** metric strip, dominant purple trend, paired breakdowns and compact filters. The time menu offers named/custom ranges, comparison and keyboard hints. Seven-day selection updated the URL. Back restored the bare URL but the view retained seven days; cause unverified. Back restoration was not established. [Live demo](https://plausible.io/plausible.io).
- **Grafana Play time-series examples:** dense persistent navigation, breadcrumbs, range stepping, refresh controls, copy/share and edit entry points; dark panels with fine borders and restrained chart grids. Example sections expose interpolation, soft bounds, multiple axes, null handling and thresholds. This is a learning sandbox, not a production team's proven layout. Owner-filter loading failed in the catalog while other navigation worked; one observation does not establish general reliability. [Demo](https://play.grafana.org/d/000000016/time-series-graphs).
- **Geckoboard IT wallboard:** inspected a vendor-published screenshot, not an interactive account. Large values, compact rectangular tiles, navy surfaces, cyan bars, green health and a conspicuous red exception. Ticket age, onboarding, projects, uptime and budget share the view. Useful distance-oriented composition; some secondary labels remain small. Vendor describes several-times-daily use. [Example and rationale](https://www.geckoboard.com/dashboard-examples/operations/IT-dashboard/).

## Visual directions

These are distinct directions observed in shipped/public product material, not measured trends or claims that dark mode is universally better.

### Quiet service bulletin

Use Linear's status page as a reference: limited width, strong current-status sentence, repeated component rows, sparse actions, history below. Typography and whitespace carry hierarchy; status color has one job. Fits anxious customers seeking impact and updates. Costs: regional/component modeling and readable incident history. Avoid making the green banner stronger than the evidence, hiding unknown state, or putting branding above impact. Dense troubleshooting controls belong in an internal view. [Observed reference](https://linearstatus.com/).

### Focused analytics workspace

Use Plausible's demo: one dominant trend, a related summary strip, compact breakdowns, one brand accent. Selected metrics and filters should remain visible; comparisons require an explicit period and direction. Fits owners with recurring, bounded questions. Costs: good defaults and carefully constrained scope. Adding every possible report to the first screen destroys the point. Dark styling was observed; no light-theme comparison or contrast audit was performed. [Observed reference](https://plausible.io/plausible.io).

### Dense diagnostic workspace

Use Grafana's examples: consistent panels, compact global controls, explicit units/ranges and multiple levels of navigation. Fits trained responders who correlate evidence. Costs: query semantics, permission boundaries, discoverability, browser load and panel consistency. Small labels are a tradeoff, not permission to ignore zoom or contrast. Decorative gradients and many colored series can obscure the anomaly. The demo establishes capabilities, not the merit of every chart option. [Observed reference](https://play.grafana.org/d/000000016/time-series-graphs).

### Distance-readable team board

Use Geckoboard's published IT example: large totals, shallow grouping and strong exception signals. Fits rooms where nobody is holding a mouse. Costs: physical distance testing, display hardware, authentication renewal and source freshness. Do not hide necessary facts in hover tooltips or rely on rotating slides for urgent state. A wallboard's large type is not the right density for an analyst's desk. [Observed screenshot](https://www.geckoboard.com/dashboard-examples/operations/IT-dashboard/).

### Design resources

- **Dashboard Design Patterns:** research-backed vocabulary for content, structure, space and interaction; public examples help compare choices. Describes patterns rather than supplying production components or causal rankings. [Catalog](https://dashboarddesignpatterns.github.io/patterns.html).
- **Carbon Charts:** coordinated chart family, demos, Figma kit and vanilla/React/Angular/Vue tutorials. Useful for enterprise consistency; verify the actual chart package's accessibility and license before adopting it. The catalog labels some spatial patterns design-only: mockup availability is not implementation availability. [Official catalog](https://www.carbondesignsystem.com/building-blocks/data-visualization/overview).
- **Geckoboard examples:** role-specific public screenshots with source and cadence context. Good composition references, but vendor selection and static screenshots cannot establish usability or customer outcomes. [Catalog](https://www.geckoboard.com/dashboard-examples/).
- **Grafana Play:** inspect real control states and chart choices without a signup. Treat it as an interactive component reference; do not copy the entire navigation or every visualization into a small app. [Sandbox](https://play.grafana.org/).

### Motion, type and disputed advice

Use motion to explain a user-triggered change, not to make monitoring look alive. Karan Rawal's 2025 practitioner article recommends pause/snapshot controls, brief history and freshness indicators; it also proposes numeric animation durations and about five visible elements without controlled evidence establishing universal limits. Treat those numbers as design suggestions. Constant count-up animations can delay reading the actual value. Keep a frozen view visibly frozen, preserve focus during updates, and honor reduced motion. [Article](https://www.smashingmagazine.com/2025/09/ux-strategies-real-time-dashboards/).

Meriem Benhabiles's 2026 case study argues for task/audience-first design and reports that side-by-side comparison resonated with a client. It does not provide a controlled usability study or retention result. Its claim that radar charts are the best way to compare equal-scale skill dimensions is too broad: test actual comparison tasks against bars or small multiples. A memorable shape and an accurate magnitude comparison are different goals. [Article](https://www.smashingmagazine.com/2026/08/rethinking-data-visualisation-ux-approach-dashboards/).

Geckoboard advises restrained decoration but explicitly allows personality when it improves engagement. That tension matters: a sales celebration can fit a team board, while playful outage animations can undermine trust. Test usefulness and attention, not whether a screenshot attracts likes. [Vendor design guide](https://www.geckoboard.com/resources/dashboard-design/).

**Inter:** useful UI/display optical sizes, tabular numbers and optional slashed zero. Tabular digits keep live values and table columns steady; avoid forcing every label into monospace. SIL OFL 1.1; preserve the license and check needed scripts. System fonts remain a lower-dependency alternative. [Font and features](https://rsms.me/inter/).

**Lucide:** coherent outline icons for controls and state. ISC, with listed Feather-derived icons under MIT; preserve the applicable notices. Pair ambiguous icons with labels, and use shape plus text for status. Icon licensing does not make a control accessible. [License](https://lucide.dev/license).

**Observable Plot:** ARIA labels/descriptions are available at plot and mark level; top-level descriptive labels default to null. Supply meaningful chart summaries and data alternatives. A library supporting ARIA is not a verified accessible dashboard. Hide redundant decorative marks rather than making assistive users traverse every segment. [Official accessibility documentation](https://observablehq.github.io/plot/features/accessibility).

## Screens and components: 110 practical details

These are design recommendations inferred from the cited behavior or rule. A source documents the underlying issue; it does not necessarily prescribe every UI detail below.

### Overview and metric cards

1. **Name the question.** Use “Checkout health” or “Orders awaiting dispatch,” not “Overview 2.” A clear purpose makes missing metrics apparent. Exploratory workspaces may stay broad. [Grafana guidance](https://grafana.com/docs/grafana/latest/visualizations/dashboards/build-dashboards/best-practices/).

2. **Pair the number with context.** Put the target or comparable period next to a KPI. A large number alone cannot tell readers whether action is needed. [Few, 2006](https://www.perceptualedge.com/articles/Whitepapers/Common_Pitfalls.pdf).

3. **Show useful precision.** Use compact values in overview cards, exact values in inspection/export. Ten decimal places create scanning work without helping most overview decisions. [Few](https://www.perceptualedge.com/articles/Whitepapers/Common_Pitfalls.pdf).

4. **Show the difference directly.** When the task is target tracking, display variance as well as actual. Making tired readers calculate the difference invites mistakes. [Few](https://www.perceptualedge.com/articles/Whitepapers/Common_Pitfalls.pdf).

5. **Group related measures.** Keep volume, errors and latency together for a service. Scattering related signals across pages makes correlation slower; details can still drill down. [Google monitoring](https://sre.google/sre-book/monitoring-distributed-systems/).

6. **Distinguish healthy from unobserved.** A missing measurement needs a distinct label and age, not a reassuring green badge. Null handling can otherwise manufacture continuity. [Grafana troubleshooting](https://github.com/grafana/grafana/blob/main/docs/sources/visualizations/dashboards/troubleshoot-dashboards/index.md).

7. **Design the first screen for decisions.** Keep the essential summary together; send diagnosis to linked detail. Do not shrink everything until unreadable merely to enforce a one-screen rule. [Few](https://www.perceptualedge.com/articles/Whitepapers/Common_Pitfalls.pdf); responsive exception is synthesis.

8. **Retire redundant boards.** Prefer a shared dashboard with filters over dozens of near-identical copies. Copies drift and make incident search ambiguous. [Grafana guidance](https://grafana.com/docs/grafana/latest/visualizations/dashboards/build-dashboards/best-practices/).

### Chart meaning and correctness

9. **Keep gaps honest.** Break a time-series line where collection failed. Joining across the gap implies knowledge that does not exist; interpolation requires an explicit domain justification. [Grafana troubleshooting](https://github.com/grafana/grafana/blob/main/docs/sources/visualizations/dashboards/troubleshoot-dashboards/index.md).

10. **Do not turn null into zero by default.** Zero errors and absent error samples differ. Only fill absent events when collection semantics guarantee absence means none. [Grafana troubleshooting](https://github.com/grafana/grafana/blob/main/docs/sources/visualizations/dashboards/troubleshoot-dashboards/index.md).

11. **Show tail latency.** Include percentiles or a distribution when slow requests matter. Mean latency can hide a bad experience for a minority. [Google workbook monitoring](https://sre.google/workbook/monitoring/).

12. **Never average instance percentiles.** Aggregate compatible distributions before computing a service percentile. Averaging reported p95s produces a misleading service number. [Prometheus histograms](https://prometheus.io/docs/practices/histograms/).

13. **Label the percentile window.** “p95, last 5 min” is clearer than “Latency.” Summary quantiles may be fixed at instrumentation time; a UI must not offer impossible recomputation. [Prometheus histograms](https://prometheus.io/docs/practices/histograms/).

14. **Expose estimation limits.** Explain histogram resolution near a threshold. Many decimal places do not make an estimated quantile exact; use thresholds compatible with the data. [Prometheus histograms](https://prometheus.io/docs/practices/histograms/).

15. **Keep bar/area baselines truthful.** Include zero when magnitude is encoded by length or area. Truncated axes exaggerate changes; lines may use a labelled narrower range. [Datawrapper dual-axis guide](https://www.datawrapper.de/blog/dual-axis-charts-guide).

16. **Separate unrelated scales.** Prefer aligned small multiples to dual axes for general audiences. Two lines crossing on independently scaled axes does not mean the measures became equal. Specialist use can justify explicit dual axes. [Datawrapper](https://www.datawrapper.de/blog/dualaxis).

17. **Avoid decorative gauges.** Use a labelled value, compact trend and target when these communicate more per pixel. Gauges fit genuine bounded operating ranges better than arbitrary business totals. [Few](https://www.perceptualedge.com/articles/Whitepapers/Common_Pitfalls.pdf).

18. **Do not stack by habit.** Stack additive parts when the total matters; use unstacked lines for individual trend comparison. Stacking can hide the series being investigated. [Grafana guidance](https://grafana.com/docs/grafana/latest/visualizations/dashboards/build-dashboards/best-practices/).

### Time, filters and navigation

19. **Show the active interval.** Keep a visible time control near the board title. A remembered filter hidden in settings can make an incident appear absent. [Grafana controls](https://grafana.com/docs/grafana/latest/visualizations/dashboards/use-dashboards/).

20. **Separate calendar and rolling periods.** Offer “Today” and “Last 24 hours” as different choices. Their boundaries differ; fiscal periods need equally explicit names. [Grafana controls](https://grafana.com/docs/grafana/latest/visualizations/dashboards/use-dashboards/).

21. **Make the timezone visible.** Include timezone in detailed timestamps and exported incident evidence. Browser-local defaults otherwise make collaborators describe different clock times. [Grafana time settings](https://grafana.com/docs/grafana/latest/visualizations/dashboards/build-dashboards/modify-dashboard-settings/).

22. **Freeze incident links.** Share absolute start/end times by default for a past anomaly. A relative “last hour” link can lose the event before the recipient opens it. [Grafana sharing](https://grafana.com/docs/grafana/latest/visualizations/dashboards/share-dashboards-panels/).

23. **Distinguish panel overrides.** Label a panel whose interval differs from the board. Silent overrides defeat comparisons across apparently aligned charts. [Grafana panel overview](https://grafana.com/docs/grafana/latest/visualizations/panels-visualizations/panel-overview/).

24. **Offer an easy zoom reset.** Keep zoom-out and time reset accessible. Dragging into an anomaly should not strand the reader in an unexplained narrow range. [Grafana controls](https://grafana.com/docs/grafana/latest/visualizations/dashboards/use-dashboards/).

25. **Carry context into detail.** Preserve service and time range in links to related dashboards. Sending every click to a generic landing page forces repeated setup. [Grafana guidance](https://grafana.com/docs/grafana/latest/visualizations/dashboards/build-dashboards/best-practices/).

26. **Make view and edit distinct.** Viewing filters should not silently change the shared dashboard definition. An explicit edit mode protects stable team views. [Grafana controls](https://grafana.com/docs/grafana/latest/visualizations/dashboards/use-dashboards/).

### Live data and investigation

27. **Offer pause or cadence control.** Let readers stop automatic updates while comparing values. Nonessential automatic updates require user control under WCAG; “live dashboard” is not a blanket exception. [WCAG 2.2.2](https://www.w3.org/WAI/WCAG22/Understanding/pause-stop-hide.html).

28. **Preserve pinned inspection.** Keep an inspected point and its actions stable during refresh. Grafana’s documented tooltip failure shows why redrawing everything can make links unusable. [Issue #112604](https://github.com/grafana/grafana/issues/112604).

29. **Match refresh to source cadence.** Hourly data rarely benefits from a five-second query loop. Wasteful refresh adds load without fresher evidence. [Grafana guidance](https://grafana.com/docs/grafana/latest/visualizations/dashboards/build-dashboards/best-practices/).

30. **Mark a paused view.** Show “Paused at…” beside Resume. Otherwise a deliberate freeze resembles a current healthy system. Derived from pause semantics. [WCAG 2.2.2](https://www.w3.org/WAI/WCAG22/Understanding/pause-stop-hide.html).

31. **Separate trend retention from detail retention.** Keep a usable long-term view while stating when raw detail expires. A smooth month chart must not imply every original sample remains inspectable. [Google workbook monitoring](https://sre.google/workbook/monitoring/).

32. **Do not require constant watching.** Use the board for comprehension and diagnosis; actionable notifications handle urgent detection. A wallboard cannot replace reliable alerting. [Google monitoring](https://sre.google/sre-book/monitoring-distributed-systems/).

### Status page and incident history

33. **Lead with customer impact.** Name affected actions and scope, then the response. Internal hostnames alone make customers translate infrastructure into their own risk. [Statuspage communication](https://support.atlassian.com/statuspage/docs/incident-communication-tips/).

34. **Acknowledge before root cause is known.** Publish a bounded “Investigating” update when impact is established. Waiting for a complete explanation leaves customers diagnosing their own systems. [Statuspage communication](https://support.atlassian.com/statuspage/docs/incident-communication-tips/).

35. **Promise the next update.** Give a realistic communication cadence even without an ETA. Do not invent a repair time; Atlassian’s 30-minute suggestion is contextual guidance, not a universal rule. [Statuspage communication](https://support.atlassian.com/statuspage/docs/incident-communication-tips/).

36. **Keep channel facts consistent.** Derive email, page and embedded banner from the same incident record. Contradictory states force users to choose whom to believe. [Statuspage communication](https://support.atlassian.com/statuspage/docs/incident-communication-tips/).

37. **Show component scope.** A whole-product badge needs affected components beneath it. Aggregate labels can hide which customer workflow is broken. [Statuspage aggregation rules](https://support.atlassian.com/statuspage/docs/top-level-status-and-incident-impact-calculations/).

38. **Explain aggregate status.** Define how component severity produces the headline. A partial outage of one component need not mean a partial outage for every user. [Statuspage aggregation rules](https://support.atlassian.com/statuspage/docs/top-level-status-and-incident-impact-calculations/).

39. **Show history methodology.** State whether uptime comes from probes, request success or editorial states. Identically formatted percentages can measure different things. [Statuspage uptime](https://support.atlassian.com/statuspage/docs/display-historical-uptime-of-components/).

40. **Keep unmeasured days distinct.** Start history at actual monitoring commencement and label missing days. Filling a new service’s past with green invents evidence. [Statuspage uptime](https://support.atlassian.com/statuspage/docs/display-historical-uptime-of-components/).

41. **Prepare publishing authority.** Give an incident communicator agreed templates and authority. Vague ownership and repeated approval negotiations delay acknowledgement. Individual practitioner reports support this failure mechanism, not a prevalence claim. [User discussion](https://www.reddit.com/r/sysadmin/comments/1k9sjxa/to_vendors_please_use_your_status_pages/).

42. **Provide incident-specific updates.** A general “all operational” page is insufficient while users report a scoped problem. Report known scope and uncertainty without claiming every report proves an outage. [User discussion](https://www.reddit.com/r/sysadmin/comments/1k9sjxa/to_vendors_please_use_your_status_pages/).

### Alerts and noisy states

43. **Name the human action.** An alert should say what needs attention and why. A surprising CPU shape alone is not sufficient reason to wake someone. [Google monitoring](https://sre.google/sre-book/monitoring-distributed-systems/).

44. **Separate page from ticket.** Show urgency and routing explicitly. Gradual budget loss may warrant planned work; fast service failure may warrant immediate response. [Google SLO alerting](https://sre.google/workbook/alerting-on-slos/).

45. **Show the evaluated windows.** A burn-rate alert should expose rate, time windows and objective. A red badge without its evaluation basis is hard to verify. [Google SLO alerting](https://sre.google/workbook/alerting-on-slos/).

46. **Account for low traffic.** Display event counts with error percentages. One failure among ten requests should not be mistaken for evidence about thousands of users. High-value single failures may still justify urgent action. [Google SLO alerting](https://sre.google/workbook/alerting-on-slos/).

47. **Keep synthetic and real experience legible.** Distinguish probe health from user success. Healthy artificial traffic can conceal failures in user paths probes never exercise. [Google SLO alerting](https://sre.google/workbook/alerting-on-slos/).

48. **Explain delayed clearing.** Show why an alert remains active after recovery. Long windows can keep firing on past failures; readers need the evaluation interval. [Google SLO alerting](https://sre.google/workbook/alerting-on-slos/).

### Accessibility, touch and presentation

49. **Pair state color with words.** Write “Degraded” and use a distinguishable icon; green/red dots alone exclude readers who cannot distinguish them. [WCAG 1.4.1](https://www.w3.org/WAI/WCAG22/Understanding/use-of-color.html).

50. **Distinguish series beyond hue.** Direct labels, symbols or line styles help when similar colors collide. A legend containing only colored swatches still leaves the problem. [WCAG 1.4.1](https://www.w3.org/WAI/WCAG22/Understanding/use-of-color.html).

51. **Provide chart meaning in text.** Include a short description plus the relevant trend or structured data. “Chart” as alt text does not communicate its evidence. [WAI complex images](https://www.w3.org/WAI/tutorials/images/complex/).

52. **Make detail available to everyone.** A visible table or description can help low vision, unfamiliar users and exports. Do not hide useful explanations exclusively from sighted readers. [WAI complex images](https://www.w3.org/WAI/tutorials/images/complex/).

53. **Make tooltips dismissible.** Escape or another mechanism should remove an obscuring tooltip without forcing pointer movement. This matters under magnification. [WCAG 1.4.13](https://www.w3.org/WAI/WCAG22/Understanding/content-on-hover-or-focus.html).

54. **Let users reach tooltip content.** Keep it open while moving onto it or retaining focus. A tooltip that disappears en route cannot support links or copying. [WCAG 1.4.13](https://www.w3.org/WAI/WCAG22/Understanding/content-on-hover-or-focus.html).

55. **Provide non-drag chart zoom.** Add date fields or clickable range controls beside brushing. Keyboard support alone does not satisfy users who need a simple touch alternative. [WCAG 2.5.7](https://www.w3.org/WAI/WCAG22/Understanding/dragging-movements.html).

56. **Provide non-drag panel reordering.** Offer Move before/after or position controls in addition to drag handles. Precision dragging excludes some touch and adaptive-input users. [WCAG 2.5.7](https://www.w3.org/WAI/WCAG22/Understanding/dragging-movements.html).

57. **Announce meaningful results without moving focus.** Expose “Refresh failed” or “Filter applied” as status messages. Moving focus on every update interrupts investigation. [WCAG 4.1.3](https://www.w3.org/WAI/WCAG22/Understanding/status-messages.html).

58. **Avoid announcing every sample.** Use concise, controlled status changes; continuous spoken metric updates can overwhelm screen-reader use. This is application guidance, not a requirement that every data change be a live region. [WCAG 4.1.3](https://www.w3.org/WAI/WCAG22/Understanding/status-messages.html).

59. **Give kiosk mode a clear exit.** Hide editor chrome for distant viewing, retain necessary state and an obvious recovery path. Grafana uses Escape; unattended displays also need operational recovery testing. [Grafana controls](https://grafana.com/docs/grafana/latest/visualizations/dashboards/use-dashboards/).

60. **Distinguish shared links from public publication.** Label audience and preview exposed data before publishing. A convenient URL must not imply that access checks vanished or that snapshots contain no sensitive values. [Grafana sharing](https://grafana.com/docs/grafana/latest/visualizations/dashboards/share-dashboards-panels/).


### Connections and application behavior

These complement the chart/status reference above. They are implementation recommendations derived from the cited mechanisms, not measured conversion results or claims that every product needs every feature.

### Connections, loading and empty states

61. **Separate setup from measurement.** Show connection saved, first sample received and useful history as distinct milestones. A working credential does not prove ingestion. A no-card trial still needs visible progress toward real value. [Oh Dear trial](https://ohdear.app/pricing/).

62. **Label sample data.** Keep a persistent demo label and a clear path to connect real data. A plausible sample must never look like the customer's healthy infrastructure. The public demo is a useful acquisition pattern when its provenance is obvious. [Plausible demo](https://plausible.io/plausible.io).

63. **Keep a failed panel local.** Preserve successful panels and identify the failed source. Replacing the whole board with one error discards usable evidence. Distinguish partial results from complete results. [Grafana troubleshooting](https://grafana.com/docs/grafana/latest/visualizations/dashboards/troubleshoot-dashboards/).

64. **Name rate limiting.** Show when another attempt is allowed, honoring `Retry-After` when supplied. An endless immediate Retry loop can prolong the failure. Automatic backoff should remain visible when it affects freshness. [HTTP 429](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status/429).

65. **Explain no matches.** Show active filters and a clear reset when a query returns no rows. “No incidents match this region and period” differs from “No incidents exist.” This is a product consequence of explicit filtering. [Dashboard patterns](https://dashboarddesignpatterns.github.io/patterns.html).

66. **Show age per source.** Put the observation timestamp beside delayed metrics. A global successful page refresh must not imply every source updated. Simple Analytics' public profit and revenue metrics illustrate independent freshness. [Open dashboard](https://dashboard.simpleanalytics.com/open).

### Forms, settings and editing

67. **Use action-specific success.** “Notification route saved” confirms more than “Done.” Do not claim delivery until a test has actually arrived. A saved configuration and a working downstream service differ. [WAI feedback](https://www.w3.org/WAI/tutorials/forms/notifications/).

68. **Put errors beside inputs and in a summary.** Name the invalid threshold or destination and explain the correction. Link summary entries to fields; a red outline alone is insufficient. Preserve valid inputs. [WAI feedback](https://www.w3.org/WAI/tutorials/forms/notifications/).

69. **Do not fight typing.** Validate complete values or on suitable focus/submit boundaries. Showing “invalid duration” after the first character adds noise before the user can finish. Reserve immediate feedback for useful, stable facts. [WAI feedback](https://www.w3.org/WAI/tutorials/forms/notifications/).

70. **Contain modal focus.** Focus a meaningful element on open, keep Tab inside, support Escape and return focus sensibly on close. An incident dialog must not leave keyboard users operating the obscured board. [APG dialog](https://www.w3.org/WAI/ARIA/apg/patterns/dialog-modal/).

71. **Fit initial focus to risk and length.** A long publication review may need heading focus; an irreversible action may favor its safe alternative. Blindly focusing Publish encourages accidental action. [APG dialog](https://www.w3.org/WAI/ARIA/apg/patterns/dialog-modal/).

72. **Detect concurrent edits.** Warn when another editor changed the dashboard or incident. Preserve the local draft; let the user compare/reload instead of silently overwriting it. Revision checks or ETag/If-Match can enforce this. [ETag](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/ETag).

73. **Show save state accurately.** Keep unsaved, saving, saved and failed states distinct. A conflict is not a successful save. Auto-save fits low-risk preferences; shared thresholds and publications need a deliberate change boundary. The latter is design inference, not an HTTP rule. [ETag](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/ETag).

74. **Preview effective cost.** Show the price consequence of another site, responder or protected status page before confirming. A cheap starting plan can conceal the buyer's actual configuration. [Better Stack pricing](https://betterstack.com/pricing/).

### Navigation, search and tables

75. **Use tabs for peer panels.** Make selected state and keyboard movement clear. A horizontal tab strip should not consume Up/Down keys needed for scrolling. Ordinary page navigation can remain links. [APG tabs](https://www.w3.org/WAI/ARIA/apg/patterns/tabs/).

76. **Avoid slow automatic tab activation.** If each focus movement launches a slow query, use explicit activation. Automatically switching on focus works best when the panel appears without noticeable latency. [APG tabs](https://www.w3.org/WAI/ARIA/apg/patterns/tabs/).

77. **Keep search text separate from a selection.** A typed service prefix is not necessarily a chosen service. Provide clear selection, Escape and editing behavior in a searchable picker. Native selects may suffice for short lists. [APG combobox](https://www.w3.org/WAI/ARIA/apg/patterns/combobox/).

78. **Name tables by purpose.** Use a caption such as “Slow endpoints, last 15 minutes.” Several unnamed tables make assistive navigation and exports ambiguous. [WAI captions](https://www.w3.org/WAI/tutorials/tables/caption-summary/).

79. **Explain unusual table structure.** Describe grouped rows/columns when their organization is not obvious. Do not repeat the caption as a redundant summary. Simple tables need less explanation. [WAI captions](https://www.w3.org/WAI/tutorials/tables/caption-summary/).

80. **Test browser Back with actual state.** Verify URL, visible range, filters and loaded results together. The Plausible inspection showed why a changed URL alone is insufficient evidence of restoration; it did not establish a reproducible product defect. [Observed demo](https://plausible.io/plausible.io).

### Live sessions and recovery

81. **Revalidate on return.** Refresh stale state after a hidden tab becomes visible. Browser timer throttling makes timer tick counts a poor freshness clock. Use timestamps; do not imply continuous observation while asleep. [Page Visibility](https://developer.mozilla.org/en-US/docs/Web/API/Page_Visibility_API).

82. **Do not confuse blur with invisibility.** A board on a second display may be visible while unfocused. Throttle based on real visibility and workload needs, not merely focus loss. [Page Visibility](https://developer.mozilla.org/en-US/docs/Web/API/Page_Visibility_API).

83. **Budget multiple tabs.** Share or limit streams when needed; HTTP/1.x SSE connections can exhaust the per-origin browser limit. Test the intended number of simultaneous dashboards through the real proxy. [EventSource](https://developer.mozilla.org/en-US/docs/Web/API/EventSource).

84. **Describe reconnect state.** Connected transport does not prove fresh measurements. Show the last observation and whether backfill is complete after reconnect. This is a design consequence of persistent streams, not a guarantee from SSE. [EventSource](https://developer.mozilla.org/en-US/docs/Web/API/EventSource).

85. **Keep an outage page independently reachable.** Avoid requiring the failed application's login, API or deployment to read status. Separate infrastructure and test that dependency boundary. A separate hostname alone proves little. [Statuspage rationale](https://www.atlassian.com/blog/statuspage/why-you-need-a-status-page).

86. **Plan vendor exit.** Export metric definitions, connector mappings and configuration in addition to screenshots. A vendor can disappear even after acquisition and customer adoption. Confirm data rights and export limits before the emergency. [Ducksboard acquisition](https://newrelic.com/press-release/20141008?is_us=true); [migration discussion](https://news.ycombinator.com/item?id=11848797).

### Exports, localization and meaning

87. **Protect spreadsheet exports.** Untrusted labels can become executable formulas in spreadsheet software. CSV quoting alone is not a universal fix; test the actual consumer and consider a typed format. [OWASP CSV injection](https://community.owasp.org/attacks/CSV_Injection).

88. **Separate display and machine values.** A human-facing “1.2k” needs an exact numeric export. Locale-aware formatting belongs in presentation; do not make machines parse abbreviations. [Intl.NumberFormat](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/NumberFormat).

89. **Format locale deliberately.** Test decimal/grouping separators, digit systems and compact forms. Replacing commas manually fails for Indian grouping and Arabic digits. [Intl.NumberFormat](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/NumberFormat).

90. **Name currency and conversion rules.** A dollar sign and a total of mixed currencies are insufficient. Show currency, exchange-rate basis and whether figures are estimates. Simple Analytics discloses its unusual intermediate aggregation; preserve such caveats beside figures. [Open dashboard](https://dashboard.simpleanalytics.com/open).

91. **Stabilize numeric alignment.** Use tabular digits for changing values and right-aligned comparable numbers. Proportional digits can make stationary cards appear to move. Preserve readable ordinary text. [Inter features](https://rsms.me/inter/).

92. **Keep identifiers distinguishable.** For hostnames, IDs and codes, choose glyphs that separate zero/O and one/l. Use slashed zero or a suitable code font where helpful; do not sacrifice normal reading everywhere. [Inter features](https://rsms.me/inter/).

### Pricing, account lifecycle and ownership

93. **Explain history limits in usable terms.** A record cap translates into different durations at different event rates. Show expected coverage for the configured cadence; “100 records” alone conceals the tradeoff. [Healthchecks pricing](https://healthchecks.io/pricing/).

94. **Keep collaboration pricing purposeful.** Do not gate invitations merely because competitors price per seat. Healthchecks removed team caps after actual upgrade evidence favored check count. Validate the mechanism for this product. [Founder change](https://blog.healthchecks.io/2026/02/unlimited-team-sizes-for-all/).

95. **Make cancellation direct.** Explain access/export timing and refund rules; offer optional help without trapping the user. Historical Baremetrics cancellation claims are confounded and drew direct customer objection. [Contemporaneous discussion](https://news.ycombinator.com/item?id=10540377).

96. **Warn before destructive downgrades.** Identify affected checks, history or delivery allowances and their timeline. Silent loss after a payment failure turns billing trouble into monitoring trouble. [Healthchecks FAQ](https://healthchecks.io/docs/faq/).

97. **Scope the trial's expensive work.** Tell users which import, retention or query limits apply. Unbounded ingestion can harm paying customers even when free-to-paid conversion looks healthy. [Baremetrics failure](https://baremetrics.com/blog/freemium-saas-implode).

98. **Separate monitor ownership from billing ownership.** Show who can fix a failing source and who can resolve an account restriction. A low-touch service must make its support boundaries visible before users rely on it. [Healthchecks FAQ](https://healthchecks.io/docs/faq/).

99. **Describe support and continuity honestly.** Show what assistance and availability the product promises. A one-person product can be valuable without implying staffed round-the-clock response. [Healthchecks disclosure](https://healthchecks.io/about/).

100. **Evaluate time saved, not visits alone.** A dependable heartbeat monitor may need little daily interaction. Track completed setup, useful interventions and renewals; compulsive dashboard checking is not the goal. This is synthesis from the narrow missed-job product and its long-running business. [Healthchecks](https://healthchecks.io/about/).

### Incident operations, subscriptions and maintenance

101. **Separate investigation from recovery.** Use clear stages such as Investigating, Identified, Monitoring and Resolved. A deployed mitigation is not yet confirmed recovery; show what is being verified. Components and incidents may have separate states. [Statuspage model](https://support.atlassian.com/statuspage/docs/what-is-statuspage/).

102. **Keep event time and publication time.** Preserve when impact began, when the team learned it and when each update was published. Record later corrections rather than making a backfilled event look contemporaneously announced. Statuspage's API separates created/display/updated timestamps; this audit recommendation is synthesis. [API example](https://support.status.atlassian.com/api).

103. **Make notification scope explicit.** Let subscribers choose relevant components and see what “all” includes. Keep a management link in updates; after changes, show the saved selection. Do not silently replace a carefully scoped subscription with every component. [Component subscriptions](https://support.atlassian.com/statuspage/docs/enable-component-subscriptions/).

104. **Distinguish pending from subscribed.** Confirm the address/channel before promising updates; show how to resend and unsubscribe. A submitted form is not proof that notifications will arrive. Keep delivery failures visible to operators instead of mislabeling the recipient as successfully reached. [Subscriber confirmation](https://support.atlassian.com/statuspage/docs/enable-subscribers/); delivery-state guidance is synthesis.

105. **Show a real maintenance window.** Include affected components, zone, expected impact and start/end. Support Scheduled, In progress, Verifying and Completed, or equally clear equivalents. Don't make users infer whether a planned event has begun. [Maintenance model](https://support.atlassian.com/statuspage/docs/schedule-maintenance/).

106. **Do not resolve by clock alone without an explicit policy.** Statuspage can automate completion and restore component state at the scheduled end. An owned product should make that choice visible; late work needs an extension/update, and cancelled work needs a clear cancellation message. Do not leave a stale promise in the calendar. [Automation behavior](https://support.atlassian.com/statuspage/docs/schedule-maintenance/); recommended safeguards are synthesis.

107. **Keep silence separate from health.** Show muted alerts in the incident context with scope and expiry. A silence suppresses notifications, not the underlying failure. Avoid turning muted rows green; the operator still needs the evidence. [Alertmanager silence semantics](https://prometheus.io/docs/alerting/latest/alertmanager/).

108. **Name ownership and suppression reason.** Show who acknowledged an incident and who silenced notifications, why, and until when. Preview affected alerts before broad matching rules are saved. Acknowledgement means a human has taken responsibility; recovery is a separate signal. These are UI recommendations derived from matcher-based silences and inhibition. [Alertmanager](https://prometheus.io/docs/alerting/latest/alertmanager/).

### Aggregation and comparisons

109. **Weight ratios by their denominators.** Sum compatible numerators and denominators before dividing. Illustrative arithmetic: one failure in ten requests plus zero in ninety is 1% overall, not the 5% average of 10% and 0%. Align time windows/populations; never combine unrelated denominators. This follows from the ratio definition, not a product benchmark.

110. **Distinguish percent from percentage points.** A conversion rate rising from 10% to 12% rose two percentage points, or 20% relative. Label which comparison the card shows. Neither statement alone supplies statistical confidence; retain the sample counts and avoid presenting tiny cohorts as settled trends. This is arithmetic and proposed presentation guidance.

## Architecture choices that change the product

**Status page, monitoring engine and analytical dashboard are different components.** A status page publishes an interpretation of service health. Probes measure selected paths; telemetry explains causes; an analyst explores dimensions. Reusing one data source is useful; pretending one UI serves all three is not. Gatus tests response bodies, time and certificate expiry as well as status codes; Healthchecks detects missing background-job signals; Prometheus collects metrics. This supports combining independent checks with internal telemetry rather than declaring a successful HTTP response sufficient. [Gatus](https://github.com/TwiN/gatus), [Healthchecks](https://github.com/healthchecks/healthchecks), [Prometheus](https://github.com/prometheus/prometheus).

**Small owned app:** server-rendered overview and incident pages, ordinary links/forms, small chart islands, bounded JSON queries, polling or SSE, one authoritative store. Turbo/Stimulus or htmx support HTML updates without a full client application. Keep chart lifecycle explicit: dispose old chart instances, retain user's zoom, cancel superseded queries. This is a fit-based proposal, not a measured speed ranking. [Turbo](https://github.com/hotwired/turbo), [Stimulus](https://github.com/hotwired/stimulus), [htmx](https://github.com/bigskysoftware/htmx).

**Interactive analysis product:** React/Vue/Svelte plus a suitable chart library, URL-owned filters, server-query cache, table virtualization when measured necessary. React-specific Recharts/visx and headless TanStack packages make this a coherent ecosystem. A client framework pays for itself when many coordinated interactions exist; it does not remove query correctness, access control or aggregation work. [Recharts](https://github.com/recharts/recharts), [visx](https://github.com/airbnb/visx), [TanStack Query](https://github.com/TanStack/query).

**Existing operator platform:** Grafana or Perses over existing metrics/log/trace stores avoids rebuilding explorers and query editors. Grafana has a broad integration surface; Perses provides embeddable npm components and dashboard-as-code tooling. Perses is a CNCF sandbox project, not evidence of equivalent adoption or plugin coverage. Treat embedding, login, permissions and upgrades as integration work. [Grafana](https://github.com/grafana/grafana), [Perses](https://github.com/perses/perses).

**Static public status:** pre-rendered HTML, incident history and small optional enhancements provide a simpler read path. cState uses Hugo with minimal client code. Upptime combines Actions checks, Issues incidents and Pages hosting. This reduces servers to operate but creates build/provider dependencies; Actions schedules can be late or dropped and have a five-minute minimum. Do not promise precise detection latency from cron configuration. [cState](https://github.com/cstate/cstate), [Upptime](https://github.com/upptime/upptime), [GitHub schedule behavior](https://docs.github.com/en/actions/reference/workflows-and-actions/events-that-trigger-workflows#schedule).

**Separate failure domains.** The public status read path and independent probe should survive the application's failure. This is a failure-model inference, also explicitly recommended by Statping's README. Separate hosting alone is insufficient if DNS, credentials, deployment or incident publication still depend on the failed system. [Statping](https://github.com/statping/statping).

## Data semantics before chart polish

1. **Metric type is part of the schema.** Counters rise and reset; gauges can move both ways. Render rates for event counters and state for gauges. A generic “rate” control is unsafe without metric types. [Prometheus instrumentation](https://prometheus.io/docs/practices/instrumentation/).
2. **Bound labels.** Each labelset consumes series storage and query resources. User IDs, full URLs and request IDs belong in event/log analysis unless a bounded use case proves otherwise. A dimension picker needs cardinality limits and safe defaults. [Instrumentation](https://prometheus.io/docs/practices/instrumentation/).
3. **Bound returned points and series.** Server aggregation, range limits and top-N views address network and database cost; chart decimation addresses drawing cost. Both are needed. Preserve extrema relevant to incidents rather than visually smoothing them away. Chart.js recommends decimating before rendering and warns that worker execution limits DOM-dependent plugins. [Chart.js performance](https://www.chartjs.org/docs/latest/general/performance.html).
4. **A cache timestamp is not the measurement timestamp.** Carry observation, ingestion and response freshness separately when delays matter. This is an implementation inference from intermittent data and live-refresh problems, not a standard field-name requirement.
5. **Budget the whole stack.** Grafana's 512 MB/one-core minimum concerns its server process, not Prometheus/Loki/Tempo or production workload. Panel count, concurrent viewers, interval and alerts drive demand. Benchmark representative queries and hours-long wallboard sessions; avoid quoting one process's minimum as total cost. [Grafana installation and sizing](https://grafana.com/docs/grafana/latest/setup-grafana/installation/).

## Compatibility: supported targets and real costs

Separate four promises: page loads; features work; layout/input fits; sustained reliability was tested. A successful desktop screenshot proves none of the other targets.

| Axis | User difference and required work | Reasonable small-team strategy / cost |
| --- | --- | --- |
| Browser engines | Chromium, Firefox and WebKit differ in rendering, input and APIs. Build transforms handle syntax, not all missing APIs. | Test all three engines; pin a browser support policy. Grafana supports current Chrome/Chromium, Firefox, Safari and Edge with JS enabled. A public status page can support a wider baseline than an editor. [Grafana](https://grafana.com/docs/grafana/latest/setup-grafana/installation/); [test engines](https://playwright.dev/docs/browsers) |
| Build target vs runtime | Current Vite docs list Chrome/Edge 111, Firefox 114 and Safari 16.4 defaults. Lower syntax target still has ESM/import.meta floors; polyfills are separate. | Record the chosen Vite major and target date. Test actual oldest supported runtime; don't copy default targets as an audience decision. [Vite](https://vite.dev/guide/build) |
| Older corporate browsers | Managed updates and restricted devices may lag. Unsupported CSS can break layout even if JS parses. | Offer a basic HTML read view or explicitly exclude old editing clients. Add legacy tooling only when audience/support revenue warrants it. |
| Mobile phone | Touch-only input has no hover; screen is narrow; keyboard consumes space; scrolling competes with chart gestures. | Keep incident summary, service search, time range and numeric detail usable. Replace hover-only values with tap/focus or table. Do not shrink desktop widgets until illegible. |
| Zoom and low vision | At 400% zoom, a 1280 CSS-pixel viewport becomes effectively 320 CSS pixels. | Reflow controls/text. Genuine two-dimensional charts/tables may scroll in their own region; that exception does not exempt the whole page. [Reflow](https://www.w3.org/WAI/WCAG22/Understanding/reflow.html) |
| Touch vs mouse vs keyboard | Tiny legend controls and drag handles fail touch and motor accessibility. | WCAG 2.2 AA minimum targets are 24×24 CSS pixels, with specified exceptions; larger is usually easier. Provide non-drag reorder/resize paths. [Targets](https://www.w3.org/WAI/WCAG22/Understanding/target-size-minimum.html) |
| TV/kiosk | Distant reading, unattended login expiry, sleep and stale data dominate. | Read-only wallboard mode, large key values, obvious last success, reconnect, bounded memory and safe device authorization. Run a multi-hour soak test on actual hardware. |
| Wake lock | HTTPS and browser support required; power saving, hidden documents or low battery can reject/release it. | Optional “keep display awake” with feedback and off switch; reacquire on visibility where appropriate. Browser wake lock is not a fleet-management guarantee. [API](https://developer.mozilla.org/en-US/docs/Web/API/Screen_Wake_Lock_API) |
| Background tabs/sleep | Timers and animation callbacks are throttled or stopped. | Pause wasteful hidden refresh; on return fetch current state and mark stale until success. Never implement reliable paging with a hidden-tab timer. [Visibility](https://developer.mozilla.org/en-US/docs/Web/API/Page_Visibility_API) |
| Many windows/tabs | Independent filters should coexist; many SSE connections can hit HTTP/1 limits. | URL-local view state, one stream per page, HTTP/2 or polling fallback; test several simultaneous windows. Don't globally overwrite filters on every change. [SSE](https://developer.mozilla.org/en-US/docs/Web/API/Server-sent_events/Using_server-sent_events) |
| Slow/offline network | A cached “all systems operational” page can be dangerously stale. | Preserve last data with age/error; never silently present cached health as live. Small HTML status payload and resilient text-first rendering help. |
| High-DPI/low GPU | Canvas resolution, huge SVG DOMs and many WebGL contexts cost memory. | Fit the renderer to data and chart count; test low-resource hardware. Chart.js supports decimation; uPlot uses Canvas 2D. Vendor benchmarks are not universal. [Chart.js](https://www.chartjs.org/docs/latest/general/performance.html) |
| Screen reader/keyboard | Canvas pixels are not accessible content; SVG alone does not define meaningful interaction. | Provide summary, units, range and tabular values; keyboard-accessible exploration where needed. Highcharts has a dedicated accessibility module; ECharts requires accessibility setup. [Canvas](https://www.chartjs.org/docs/latest/general/accessibility.html); [Highcharts](https://www.highcharts.com/docs/accessibility/accessibility-module); [ECharts](https://github.com/apache/echarts-handbook/blob/master/contents/en/best-practices/aria.md) |
| Reduced motion | Continuous line interpolation, pulse and count animations can distract or trigger discomfort. | Respect prefers-reduced-motion; provide pause/frequency control for auto-updating information unless essential. “Live dashboard” does not automatically establish the exception. [CSS preference](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/At-rules/@media/prefers-reduced-motion); [updating content](https://www.w3.org/WAI/WCAG22/Understanding/pause-stop-hide.html) |
| Locales/time zones | Decimal separators, date ordering, RTL and DST affect interpretation. | Use Intl or tested date libraries; display named zone and precise timestamp on inspection. Define whether “day” means calendar day or 24-hour window. Test DST and translated long labels. |
| Embed/private mode | Third-party cookies, iframe policy and blocked scripts can break embedded login or wake lock. | Test embedded mode explicitly; prefer scoped server-authorized data and an open-in-app path. Don't assume a normal logged-in browser tab proves embeds work. |
| Print/export | Canvas, hidden scroll regions and dark backgrounds may print poorly. | Export a frozen timestamped view with units, filters and full legends; test PDF/print separately. Static report and live dashboard serve different tasks. |
| Server architectures | Collector OS support differs from browser support. node_exporter targets Unix-like kernels; Windows has its own exporter. | Document probes/agents separately from viewer compatibility. Containerized host metrics need host mounts/namespaces or they may report the container. [node_exporter](https://github.com/prometheus/node_exporter) |


Suggested support tiers, not observed market prevalence: (1) public status: broad text-first read access, current mobile/desktop enhancements; (2) operator dashboard: current evergreen engines plus measured mobile triage; (3) enterprise deployment: a contracted browser/device matrix; (4) dedicated kiosk: a managed hardware/browser version and soak-tested configuration. Audience constraints and ability to update devices determine the right choice.

## Additional compatibility decisions

**Baseline is an input, not a support promise.** Its core-browser feature coverage does not establish assistive-technology support, older devices, embedded webviews or this application's correctness. A build target handles a different problem from tested UX. Keep the public text read path simple and make richer charting an enhancement when practical. [MDN Baseline](https://developer.mozilla.org/en-US/docs/Glossary/Baseline/Compatibility).

**Manage wallboard hardware.** Geckoboard's July 2026 guidance favors a dedicated device with current Chrome/Firefox and automatic recovery. Its Windows kiosk minimum is dual-core/4 GB RAM/32 GB storage; recommendations are higher. It recommends Pi 4/5, with at least 4 GB on Pi 4, and names Raspberry Pi OS Trixie. These are vendor-specific support facts, not universal minimums. Test your board for memory growth, power interruption, unattended authentication and readability at the real distance. A smart TV that opens a URL may still be a poor supported target. [Owner guidance](https://support.geckoboard.com/en/articles/6055736-recommended-computer-devices-for-displaying-geckoboard-on-a-screen).

**Localize data and interface separately.** Set document language/direction; use UTF-8; allow longer labels and local formats. Mixed hostnames, IDs and RTL labels need careful text direction. Do not mirror quantitative axes automatically with surrounding chrome: Highcharts documents configurable axis reversal as a choice for RTL use. Verify the user's reading convention and preserve explicit time direction. [W3C](https://www.w3.org/International/quicktips/index); [Highcharts internationalization](https://www.highcharts.com/docs/advanced-chart-features/internationalization).

**Geography changes economics and support.** A nearby probe measures one network path; regional probes and notification channels add costs. Mobile-heavy audiences need usable triage before a sophisticated desktop builder. Locked-down corporate buyers may justify an older browser or embedded-auth support contract; a small self-serve product may explicitly support fewer clients. These are scope decisions, not inferred regional market shares. This research has no representative customer geography/device dataset from which to prescribe universal coverage.

## Named ecosystem catalog

These are alternatives, not a shopping list. Primary repos below were read 2026-11-07. Where inspected GitHub metadata reported a recent push and no archive flag, “active repository” means only that; it is not a support SLA. Licenses identify the inspected code repository unless a row says mixed/commercial. Do not transfer a server's license to its hosted service or SDK.

### Charts and analysis

| Tool | Fit, tradeoff and evidence |
| --- | --- |
| [uPlot](https://github.com/leeoniya/uPlot) | MIT; compact Canvas 2D time-series plots. Good candidate for many dense operational charts. Supply accessibility and application controls. README performance numbers are author benchmarks, not this research's measurements. |
| [Chart.js](https://github.com/chartjs/Chart.js) | MIT; common chart types on canvas. Practical framework-neutral option with decimation and worker guidance. Must add accessible names/alternatives; worker plugins cannot assume DOM access. |
| [Apache ECharts](https://github.com/apache/echarts) | Apache-2.0; broad interactive charting, Apache project. Good for heatmaps and rich chart options. Enable/import ARIA support and decals; configuration breadth adds integration work. |
| [Recharts](https://github.com/recharts/recharts) | MIT; declarative React/SVG charts using D3. Fits React dashboards; not a framework-neutral package. SVG point counts still need measurement. |
| [D3](https://github.com/d3/d3) | ISC; low-level SVG/Canvas/HTML visualization primitives. Use for distinctive domain encodings or custom interaction. More owned chart behavior than a high-level library. README identifies higher-level dependent ecosystem; no market share inferred. |
| [visx](https://github.com/airbnb/visx) | MIT; low-level React components using D3 calculations. Current README says v4 stable, React 18/19 required. Fits an owned chart system; upgrading from v3 needs migration. |
| [nivo](https://github.com/plouc/nivo) | MIT; React charts with SVG/HTML/Canvas variants, theming, patterns and motion. Select packages/chart renderer deliberately; do not inherit decorative transitions for live metrics. |
| [Vega](https://vega.github.io/vega/) / [Vega-Lite](https://github.com/vega/vega-lite) | Vega-Lite BSD-3-Clause; declarative grammar compiles to Vega specs. Good for saved analytical specifications and reproducible views; introduces a grammar/runtime rather than ordinary UI components. Vega-Lite repo identifies UW visualization research lineage. |
| [Observable Plot](https://github.com/observablehq/plot) | ISC; concise layered marks for exploratory tabular data. Good for analytical reports and embedded explorations. A chart library, not the hosted Observable product or a full dashboard editor. |
| [Plotly.js](https://github.com/plotly/plotly.js) | MIT; broad scientific/statistical/3D/financial charts; powers Python/R Plotly. Use partial bundles where possible. Rich scientific capability may be unnecessary for a handful of status sparklines. |
| [Highcharts](https://www.highcharts.com/docs/accessibility/accessibility-module) | Commercial licensing must match use. Dedicated accessibility module, descriptions and keyboard interaction reduce custom work. Add meaningful labels/descriptions; the module cannot infer the chart's business meaning. |
| [ApexCharts](https://apexcharts.com/license/) | Current community/commercial/OEM model matters. Suitable only after checking organization and redistribution terms; not safe to assume old MIT terms apply to current packages. See avoid section. |

### Dashboard and status products / foundations

| Tool | Fit, tradeoff and evidence |
| --- | --- |
| [Grafana](https://github.com/grafana/grafana) | AGPL-3.0 repository; dashboards across heterogeneous metrics/logs/traces/SQL. Existing ecosystem reduces explorer work but adds plugin, upgrade, permission and operating complexity. Hosted and commercial editions differ. |
| [Perses](https://github.com/perses/perses) | Apache-2.0; Go/React dashboard project, embedding packages, Go/CUE SDKs, auth and plugins. CNCF sandbox. Promising interoperable/dashboard-as-code foundation; assess actual data-source coverage. |
| [Uptime Kuma](https://github.com/louislam/uptime-kuma) | MIT; self-hosted monitoring UI with status pages. Fits users who want an application rather than code-managed probes. Large GitHub interest is not proof of reliability or paid viability. |
| [Gatus](https://github.com/TwiN/gatus) | Apache-2.0; developer-oriented Go health checks, conditions and alerts, configuration as files. Useful lightweight health board reference. HTTP 200 alone is not its limit; can test body and timings. |
| [Upptime](https://github.com/upptime/upptime) | MIT; GitHub Actions/Issues/Pages status stack; public repo history provides inspectability. README claims 3,000+ users/teams and names Canonical/Wakatime; vendor claim, not audited adoption. Schedule precision/provider dependency is the tradeoff. |
| [cState](https://github.com/cstate/cstate) | MIT; Hugo static status pages with minimal HTML/CSS/JS. Useful broad-read compatibility and incident publishing model; not a full telemetry explorer. Its IE8+ claim is project documentation, not a new independent browser test. |
| [Healthchecks](https://github.com/healthchecks/healthchecks) | BSD-3-Clause; Python/Django job/cron heartbeat monitoring; self-hostable. Detects missing success signals. Production migrations and backups remain operator duties; headers from auth proxies must be protected. |
| [Cachet](https://github.com/cachethq/cachet) | Self-hosted status-page system with custom Cachet license restricting standalone redistribution (3.x LICENSE.md); current 3.x README requires PHP 8.3+, Composer and MariaDB/MySQL/PostgreSQL/SQLite. Rebuild/migration branch matters; avoid old assumptions that all Cachet work is abandoned. |

### Collection, query and storage

| Tool | Fit, tradeoff and evidence |
| --- | --- |
| [Prometheus](https://github.com/prometheus/prometheus) | Apache-2.0 metrics/time-series system and query model. Strong existing exporter path; label/retention/query design still determines cost. An option, not a reversal of scaffold's deferred observability decisions. |
| [Alertmanager](https://github.com/prometheus/alertmanager) | Apache-2.0; deduplication, grouping, routing, silences and inhibition. Complements metric/rule evaluation; do not rebuild notification storms into each chart. |
| [blackbox_exporter](https://github.com/prometheus/blackbox_exporter) | Apache-2.0; HTTP(S), DNS, TCP, ICMP and gRPC probes. Gives independent endpoint signals in Prometheus; probe location and timeout affect meaning. |
| [node_exporter](https://github.com/prometheus/node_exporter) | Apache-2.0; Unix hardware/OS metrics. Container deployment needs explicit host access. Windows users should use the separately named windows_exporter. |
| [OpenTelemetry Collector](https://github.com/open-telemetry/opentelemetry-collector) | Apache-2.0 vendor-neutral receive/process/export pipeline. Good for multiple telemetry destinations. Adds a service/configuration and dependency surface; not required for every small app. |
| [Grafana Alloy](https://github.com/grafana/alloy) | Apache-2.0 collector distribution with Prometheus and OpenTelemetry pipelines. Supported replacement for Grafana Agent/Promtail; programmable config is powerful but another operational language. |
| [VictoriaMetrics](https://github.com/VictoriaMetrics/VictoriaMetrics) | Apache-2.0 single-node and cluster time-series storage. Evaluate single-node before distributed deployment. README links named case studies; performance/cost superiority remains vendor claim unless tested for workload. Enterprise features have separate terms. |
| [Grafana Loki](https://github.com/grafana/loki) | AGPL-3.0 log aggregation; indexes labels rather than full log text. Good correlation with metrics labels, different search/cost behavior from full-text engines. Alloy replaced Promtail. |
| [Grafana Tempo](https://github.com/grafana/tempo) | AGPL-3.0 tracing backend with object-storage architecture and Grafana integration. Fits request investigation, not a replacement for metric aggregation. README labels TraceQL metrics experimental. |
| [ClickHouse](https://github.com/ClickHouse/ClickHouse) | Apache-2.0 column-oriented analytical database. Fit for large event analytics/aggregations. Additional database operations; don't infer required scale from its presence in successful products. |
| [DuckDB](https://github.com/duckdb/duckdb) | MIT in-process analytical SQL, remote files and many language/Wasm bindings. Useful for local/batch/report exploration. Not automatically a multiuser transactional service. |
| [TimescaleDB](https://github.com/timescale/timescaledb) | PostgreSQL extension for time-series/event analytics. Preserves SQL ecosystem; Apache-compatible outside tsl; Timescale License within tsl, per owning LICENSE. Check selected features and service distribution rights. Current quick-start explicitly says its one-line script is for local testing, not production. |

### UI, state and time

| Tool | Fit, tradeoff and evidence |
| --- | --- |
| [TanStack Table](https://github.com/TanStack/table) | MIT headless sorting/filtering/grouping/selection with many framework adapters. Own semantic markup, styling and keyboard behavior; headless does not mean finished accessible grid. |
| [TanStack Virtual](https://github.com/TanStack/virtual) | MIT large-list/grid virtualization. Use for measured row-count problems; test focus, screen-reader traversal and search because unmounted rows are absent from DOM. |
| [TanStack Query](https://github.com/TanStack/query) | MIT server-state cache/refetch/cancellation/mutations. Good for interactive clients; specify freshness policy rather than equating cache success with fresh telemetry. |
| [AG Grid](https://github.com/ag-grid/ag-grid) | Community MIT plus commercial Enterprise. Useful complex tables across React/Vue/Angular/plain JS; confirm desired grouping/export/server-side features belong to the edition budgeted. |
| [GridStack](https://github.com/gridstack/gridstack.js) | MIT TypeScript dashboard drag/resize with framework bindings. Good configurable layouts; keyboard alternatives and saved layout migrations remain app work. |
| [React-Grid-Layout](https://github.com/react-grid-layout/react-grid-layout) | MIT responsive grid. Current v2 README describes hooks/TypeScript rewrite and legacy API import; migration changes callback semantics. Repo shows production BitMEX example, not universal adoption. |
| [Radix Primitives](https://github.com/radix-ui/primitives) | MIT unstyled accessible UI primitives maintained by WorkOS. Useful menus/dialogs/controls in React apps; labels, composition and product accessibility still require review. |
| [React Aria / React Spectrum](https://github.com/adobe/react-spectrum) | Apache-2.0 unstyled hooks/components or Adobe-styled system; keyboard, screen-reader and adaptive behavior. Strong for interaction complexity; React dependency and design fit matter. |
| [Floating UI](https://github.com/floating-ui/floating-ui) | MIT anchor/collision positioning; React interaction layer. Good chart tooltips near viewport edges. Popper migration is documented; tooltip content still needs keyboard/touch access. |
| [shadcn/ui](https://github.com/shadcn-ui/ui) | MIT customizable component source. Fits an owned design system; copied code transfers update/review work to the app. It does not guarantee chart semantics. |
| [Tailwind CSS](https://github.com/tailwindlabs/tailwindcss) | MIT styling utilities. Good shared vocabulary; no built-in answer to information density, accessible colors or browser support. Check the selected major's browser requirements. |
| [Lucide](https://github.com/lucide-icons/lucide) | SVG icon toolkit with framework packages. Good coherent operational symbols; use visible labels for unfamiliar status meanings. Owning LICENSE is ISC, with MIT terms for listed Feather-derived icons; retain notices. |
| [date-fns](https://github.com/date-fns/date-fns) | Modular immutable native-Date utilities; v4 README highlights first-class time zones. Select imports and explicit zone handling. Published 4.4.0 package LICENSE.md inspected from npm tarball: MIT; repository-root metadata alone was incomplete. |
| [Luxon](https://github.com/moment/luxon) | MIT immutable DateTime/Duration/Interval using native Intl/time-zone support. Good explicit zone calculations; depends on runtime Intl data. v4 roadmap is not a shipped-version claim. |
| [Day.js](https://github.com/iamkun/dayjs) | MIT small immutable Moment-like API. Useful compact date handling; required plugins/locales change actual bundle and capability. “2 kB” is author core-size claim, not your full app cost. |
| [FullCalendar](https://github.com/fullcalendar/fullcalendar) | MIT core; scheduling/maintenance calendars with framework connectors. Specialized rather than needed for a simple incident list. Selected release/plugin license and peer dependencies require review. |
| [react-big-calendar](https://github.com/jquense/react-big-calendar) | MIT React event calendar, modern browsers. Alternative maintenance schedule UI; container height and date localization are explicit integration requirements. |

### App construction, diagnostics and testing

| Tool | Fit, tradeoff and evidence |
| --- | --- |
| [Turbo](https://github.com/hotwired/turbo) | MIT HTML navigation, frames and streams; good server-rendered operations apps. Preserve graph instances/selection across replacement. |
| [Stimulus](https://github.com/hotwired/stimulus) | MIT behaviors attached to existing HTML. Good chart lifecycle, keyboard shortcuts and small controls; not a rendering/data-cache framework. |
| [htmx](https://github.com/bigskysoftware/htmx) | Zero-Clause BSD; HTML attributes for requests/transitions and SSE/WebSocket extensions. Good partial refresh; decide focus/history/swapping semantics. Owning LICENSE verified directly after inconclusive API metadata. |
| [Alpine.js](https://github.com/alpinejs/alpine) | MIT local behavior in markup. Good modest client state; complex cross-chart analysis can outgrow ad hoc state wiring. |
| [Vue](https://github.com/vuejs/core) | MIT progressive UI framework. Appropriate reactive dashboard client; coherent framework choice matters more than mixing component ecosystems. |
| [SvelteKit](https://github.com/sveltejs/kit) | MIT app framework with deployment adapters. Fit when server rendering plus reactive client is wanted; adapter/runtime compatibility must match hosting. |
| [TypeScript](https://github.com/microsoft/TypeScript) | Apache-2.0 typed JS tooling. Useful complex query/result contracts; types do not validate runtime source data or fix unit mistakes. Plain JS remains viable for smaller chart islands. |
| [Vite](https://github.com/vitejs/vite) | MIT dev/build tooling; current repo uses Rolldown. Explicit target configuration and API polyfills remain separate. Useful interactive frontend development, not mandatory for simple shipped JS. |
| [esbuild](https://github.com/evanw/esbuild) | MIT fast bundling/minification with JS/TS/JSX/CSS and Go API. Fits small build pipelines; type checking and runtime polyfills are separate work. |
| [Playwright](https://github.com/microsoft/playwright) | Apache-2.0 cross-engine browser tests, screenshots, network control. Use outage/reconnect, filtering, sharing and accessibility flows. Bundled WebKit is not a substitute for every real iOS/device test. |
| [axe-core](https://github.com/dequelabs/axe-core) | MPL-2.0 automated accessibility checks. Project claims average detection of 57% of WCAG issues; manual review remains necessary. Test keyboard/data meaning as well as scanner output. |
| [MSW](https://github.com/mswjs/msw) | MIT network mocking in browser/tests. Useful delayed, partial, malformed and out-of-order telemetry responses. Avoid only testing ideal fixtures. |
| [Vitest](https://github.com/vitest-dev/vitest) | MIT Vite-integrated tests, mocks and browser mode. Useful aggregation/time-range transforms; DOM mocks cannot establish real layout/input reliability. |
| [k6](https://github.com/grafana/k6) | AGPL-3.0 Go load tool with JS scripts and multiple protocols. Measure concurrent refresh and incident traffic; generator capacity and backend workload must be representative. |
| [Sentry JavaScript SDK](https://github.com/getsentry/sentry-javascript) | Client error/performance diagnostics across JS environments. Useful finding dashboard failures invisible to server monitoring; redact tenant data and budget volume. Owning SDK LICENSE is MIT; it explicitly warns some packages depend on Sentry CLI under FSL-1.1-Apache-2.0. SDK/service/dependency terms differ. |

### Backend, persistence, packages and release

These alternatives affect collection, persistence and shipping. Sources checked 2026-11-07; no performance comparison.

| Tool | Fit, tradeoff and evidence |
| --- | --- |
| [Go and net/http](https://pkg.go.dev/net/http) | BSD-3-Clause standard library HTTP client/server; useful probe workers, bounded concurrent ingestion and a small web server in one language. Gatus/Prometheus establish concrete category use of Go. Go's [compatibility promise](https://go.dev/doc/go1compat) concerns source, with security/unspecified-behavior exceptions; it does not guarantee unchanged performance or OS support. |
| [Go modules](https://go.dev/ref/mod) | Built-in dependency/version mechanism; commit go.mod/go.sum and control toolchain updates. Avoid adding another package manager for ordinary Go dependencies. Separate third-party licenses and platform/C dependencies remain relevant. |
| [Go embed](https://pkg.go.dev/embed) | Standard-library compile-time files; package templates/chart JS/static public status assets into a binary. Useful portable deployment; changing bundled assets requires rebuild. A file embedding API, not a database or hot-update system. |
| [Python/Django migrations](https://docs.djangoproject.com/en/5.2/topics/migrations/) | Integrated schema migration workflow, models and Python web ecosystem. Concrete fit: Healthchecks uses Python/Django. Migration files are generated once, reviewed/versioned, then applied consistently; “automatic” does not remove database lock and data migration review. 5.2 docs inspected, not a claim that it is newest. |
| [FastAPI](https://fastapi.tiangolo.com/) | MIT typed Python APIs built on Pydantic/Starlette. Good when a dashboard fronts Python analytics or detection logic; fewer integrated app conventions than Django. Uvicorn serves ASGI; optional standard extras add dependencies. Performance claims are not dashboard workload guarantees. |
| [uv](https://docs.astral.sh/uv/) | Python package/project and interpreter management with lockfile, workspace and pip-compatible workflows; backed by Astral. Useful reproducible Python analytics service. Alternative is existing pip/venv toolchain; switching tools is unnecessary if current builds are reproducible. Vendor speed claims depend on cache/workload. |
| [Node.js](https://nodejs.org/en/about/previous-releases) | JS server/runtime and build ecosystem; fits full-stack JS or frontend build only. Owning docs recommend Active/Maintenance LTS for production. As read: 26/24/22 LTS; 25 EOL; 27 Alpha. Pin supported runtime compatible with selected tooling instead of “latest.” |
| [React](https://react.dev/learn/creating-a-react-app) | UI component foundation for Recharts, visx, React Aria and many editors. Official guidance favors a framework, but explicitly permits custom setups; full-stack framework does not imply mandatory SSR/server hosting. For one graph island, framework breadth is not automatically useful. |
| [PostgreSQL](https://www.postgresql.org/docs/current/ddl-partitioning.html) | General relational store for users, monitor definitions, incidents and modest time-series aggregates. Built-in partitioning supports large time-window queries/retention, but docs say benefits normally arise for very large tables. Start with appropriate indexes/queries; partitioning adds planning/schema work. |
| [SQLite](https://sqlite.org/whentouse.html) | Embedded local persistence; useful single-instance monitor/configuration/history without another server. Unlimited readers but one writer at a time; short transactions can still sustain useful concurrency. Don't put one shared file on unreliable network storage or assume multi-server write scalability. Web clients are fine through one application server. |
| [golang-migrate](https://github.com/golang-migrate/migrate) | Go library/CLI with SQL migration sources and database drivers. v4 is supported stable line; repo says v3 unsupported. Fits explicit SQL migrations with up/down files; a down file is not proof that lost data can be recovered. |
| [Goose](https://github.com/pressly/goose) | MIT SQL and Go-function migrations. Useful when data rewrites need code; check selected driver's transactional behavior. README warns ClickHouse deployment modes need care and recommends a version-ordering workflow; choose deliberately against golang-migrate or framework migrations. |
| [npm ci](https://docs.npmjs.com/cli/v11/commands/npm-ci/) | Frozen clean install for CI/deployment; requires lockfile and fails if package manifest disagrees. Supports repeatable frontend artifacts; install flags affecting dependency shape must match lockfile generation. Alternative pnpm has a different lockfile/install model. |
| [pnpm](https://pnpm.io/cli/install) | JS package/workspace install tool; CI normally fails when existing lockfile needs updating. Good monorepo/shared-component setup; explicit frozen lockfile behavior prevents release-time drift. Pin package-manager version and don't mix npm/pnpm locks casually. |
| [Docker Compose](https://docs.docker.com/compose/intro/compose-application-model/) | Declarative services/networks/volumes/configs/secrets for small multi-service deployment and local testing. Useful Grafana + data store or app + DB setup. A volume declaration is not a backup; Compose does not itself establish cross-host failover or production durability. |
| [Caddy](https://caddyserver.com/docs/automatic-https) | Reverse-proxy/web server with automatic TLS provision/renewal and redirects. Useful small self-hosted dashboard. Public certificate issuance needs correct DNS/network reachability; internal self-signed trust must be installed on clients. Avoid treating successful local HTTPS as universal client trust. |
| [GitHub Actions](https://docs.github.com/en/actions/concepts/workflows-and-actions/reusing-workflow-configurations) | Reusable build/test/release workflows can standardize chart tests and artifact creation. Hosted runner cost/availability is a service constraint. Build pipeline and continuous health monitoring have different reliability needs; schedules are not a precise pager scheduler. |
| [Dependabot](https://docs.github.com/en/code-security/concepts/supply-chain-security/dependabot-version-updates) | Version/security update PRs for supported ecosystems and Actions. Useful keeping chart/browser/runtime dependencies reviewable. Update proposals still need interaction/visual/data-contract tests; automatic version updates do not prove compatibility. GitHub service terms apply. |

Additional avoid cases: Node 25 is EOL in the owning release table; use supported LTS for production. golang-migrate v3 is explicitly unsupported in the owning repo; prefer v4 for new use and review existing migration behavior before changing imports. Neither implies all older version numbers are unusable without inspecting their support policy.

## Named choices to avoid, migrate or limit

| Choice / classification | Verified reason and date | Replacement / legitimate exception |
| --- | --- | --- |
| Grafana Agent — migrate | Official docs: EOL 2025-11-01; no vendor support/security/bug fixes. | Grafana Alloy or another supported collector. Existing deployment migration needs config/output validation. [Source](https://grafana.com/docs/agent/latest/). |
| Promtail — migrate | Official docs: EOL 2026-03-02, no future support/updates. lambda-promtail explicitly excluded. | Alloy or supported log client; test labels, parsing and delivery positions. [Source](https://grafana.com/docs/loki/latest/send-data/promtail/). |
| AngularJS Grafana plugins — migrate | Disabled by default in Grafana 11; removed in 12. Older 2023 announcements predicted earlier removal and are superseded. | React plugin replacements/core panel migrations; snapshot dashboards and test data source behavior before upgrade. [2025 primary notice](https://grafana.com/blog/angularjs-support-will-be-removed-in-grafana-12-what-you-need-to-know/). |
| Create React App — avoid new work; plan migration | React deprecated it 2025-02-14; no active maintainers; maintained compatibility release does not restore recommendation. | React framework or Vite/Parcel/Rsbuild. Existing apps do not instantly stop working. [Source](https://react.dev/blog/2025/02/14/sunsetting-create-react-app). |
| Moment — avoid default for new work; existing viable | 2026-08-17 policy: legacy maintenance, no new user-facing features; technical maintenance and possible semver-major release are permitted. Security and timezone maintenance continue with volunteer capacity caveats. | Intl/date-fns/Luxon/Day.js when suitable. Don't rewrite proven date logic solely because of “legacy,” or claim no future v3. [Source](https://momentjs.com/news/). |
| ApexCharts selected under assumed MIT — avoid assumption | Current licensing page has <$2M annual revenue/budget/funding resource limit for free community; controlled affiliates considered; commercial and OEM rules differ. | ECharts/Chart.js/Recharts/uPlot or budget applicable license. Static-chart exception and OEM rules require exact use review. Older legally acquired versions are a separate question. [Source](https://apexcharts.com/license/). |
| Upptime as precise low-latency pager — unsuitable for that promise | GitHub schedules minimum five minutes; high-load delays/drops documented; public inactive repos can disable schedules after 60 days. | Dedicated external probe scheduler; Upptime remains useful low-cost status/history with understood latency. [Source](https://docs.github.com/en/actions/reference/workflows-and-actions/events-that-trigger-workflows#schedule). |
| Canvas-only chart as accessible UI — unsuitable | Chart.js explicitly says canvas content is not screen-reader accessible. | Summary + meaningful labels + data table; consider dedicated chart accessibility support. Canvas rendering itself remains viable. [Source](https://www.chartjs.org/docs/latest/general/accessibility.html). |
| Popper v2 assumed to be current project direction — assess migration | Owning repo says Popper is now Floating UI and links separate v2 branch/migration guide. | Floating UI for new integration; don't call installed Popper code universally broken. [Source](https://github.com/floating-ui/floating-ui). |
| Timescale quick-start script for production — unsuitable | Owning README explicitly limits script to local development/testing. | Supported production install/backup/upgrade process. Timescale itself remains viable. [Source](https://github.com/timescale/timescaledb). |
| Current Loki OSS Helm chart assumed at old location — migrate chart source | Repo says effective 2026-03-16 community chart moved to grafana-community/helm-charts; chart in Loki repo maintained for GEL users. | Review community chart migration; don't conflate this with abandoning Loki. [Source](https://github.com/grafana/loki). |


## Category security and failure testing

**Monitor URLs are an SSRF interface.** Public monitoring SaaS lets customers request server-side connections. Validate destination/protocol, redirects and resolved addresses; block unauthorized private/link-local/metadata targets, constrain egress and re-check redirects. Private-network monitoring should use an explicit authorized probe deployment, not a bypass hidden in validation. These are category applications of [OWASP SSRF guidance](https://cheatsheetseries.owasp.org/cheatsheets/Server_Side_Request_Forgery_Prevention_Cheat_Sheet.html).

**Permissions apply to every data path.** Share links, exports, panel queries, saved views, thumbnail rendering and websocket/SSE subscriptions need server authorization. Hidden controls are not a boundary. Bind cache keys to authorized scope; revoke capability links; test cross-tenant identifiers and metric-label filters. Derived application of [OWASP authorization guidance](https://cheatsheetseries.owasp.org/cheatsheets/Authorization_Cheat_Sheet.html).

**Test failure states as product behavior.** Fixtures: no samples; partial samples; old samples; clock skew; reset counters; DST; cancelled request completing late; auth expiry midstream; probe network down; source quota; schema change; oversized label; long outage; disk full; restored backup; incident traffic spike. Expected: accurate status, preserved context, clear freshness, bounded retry/load, recoverable editing, no cross-tenant leaks. These are engineering test proposals from the documented platform/data constraints, not measured feature rankings.



## Sources and method

Near-claim links form the source register; this index explains their evidentiary role. Sources were inspected on 2026-11-07 unless a historical publication/inspection date is stated. Technical claims use owning docs/repositories; review and financial claims retain their source type. Links to mutable main-branch docs require a release-specific check before adoption.

| Evidence | What was inspected | What it can establish |
| --- | --- | --- |
| Live screens | Linear status, Plausible public analytics, Grafana Play; desktop screenshots/accessibility trees; Plausible range selection and Back | Appearance and named observations only; no full accessibility, performance or reliability certification |
| Published visual example | Geckoboard IT wallboard screenshot and rationale | Composition and vendor-described task; no live interaction or measured customer gain |
| Books and research | Few's accessible 2006/2007 papers; 2022 Dashboard Design Patterns paper/catalog; independent review of Few's second edition | Historical design reasoning, descriptive patterns and disagreement; no claim of reading every cited book |
| Podcast | Console's complete native transcript of the Charity Majors interview | Attributed founder experience; no audio/video viewing or controlled uplift inferred |
| Independent use | Willison's documented analysis/export; LWN's historical trial; Hunter's weeks-long review; specific Reddit reports | Concrete task/failure accounts with dates; no representative prevalence or benchmark |
| Review catalogs | Full retrieved individual Capterra/Software Advice records; direct-page failures and incentives disclosed in the relevant passages | Attributed reports only; copied review syndication is not independent corroboration |
| Commercial evidence | Owner pricing, open dashboards, founder accounts, published customer cases and accessible experiment catalog | Pricing and reported outcomes; no audited net-profit ranking, undisclosed cohort reconstruction or gated experiment result |
| Technical ecosystem | Official docs, README/license files, published package metadata and identified issue discussions | Capabilities, documented constraints and maintenance/licensing status; no installed dependency audit or workload benchmark |

No private accounts, paid reports, purchase flow or production telemetry were needed. No contacts were solicited. Public evidence cannot supply private current margins, unpublished experiments or representative retention denominators; the affected business passages explain those limits. Direct-page failures were supplemented with native transcripts, owner docs, full retrieved review records and independent accounts where available. Claims from contradictory reviews and unlinked statistics were excluded.

The catalog is deliberately selective: 82 entries span charting, status systems, collection, storage, UI/state/time, app construction, diagnostics, tests, packages and release. It is not a download ranking, a requirement to use every tool, or a universal stack. The 110 details combine documented behaviors, mathematical facts and clearly labelled design inference. The compatibility matrix proposes support strategies; no device lab or long-running deployment test was performed.

License texts checked 2026-11-07: [Lucide](https://github.com/lucide-icons/lucide/blob/main/LICENSE), [htmx](https://github.com/bigskysoftware/htmx/blob/master/LICENSE), [Sentry SDK](https://github.com/getsentry/sentry-javascript/blob/develop/LICENSE), [Timescale](https://github.com/timescale/timescaledb/blob/main/LICENSE), [Gatus](https://github.com/TwiN/gatus/blob/master/LICENSE), [Upptime](https://github.com/upptime/upptime/blob/master/LICENSE), [cState](https://github.com/cstate/cstate/blob/master/LICENSE.md), [Healthchecks](https://github.com/healthchecks/healthchecks/blob/master/LICENSE), [Cachet 3.x](https://github.com/cachethq/cachet/blob/3.x/LICENSE.md), [date-fns published metadata](https://registry.npmjs.org/date-fns/latest). Cachet custom restrictions are material for redistribution; do not infer MIT from historical Cachet descriptions.
