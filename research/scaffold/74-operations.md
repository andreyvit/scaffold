# Operation belongs in every recipe

Proposed compact contract. Shared recipes define mechanics; each feature supplies its own facts.

| Concern | Each feature must say | Whole-app recipe supplies |
|---|---|---|
| Security | Actor; resource/tenant; allowed actions; abuse limits; sensitive data | Common enforcement, credential/session handling, secrets, safe defaults |
| Metrics | Success/failure/latency/backlog worth measuring; useful alert | Naming, bounded labels, collection, dashboard and alert routing |
| Logs | Useful events, correlation, safe detail, retention | Structured context, redaction, access, transport and search |
| Audit | Which durable who/what/when records matter | Integrity, access, retention; distinct from debug logs |
| Failure | Retryable vs terminal; partial success; idempotency; reconciliation | Durable jobs, deadlines, retry policy, operator tools |
| Data | Durability, migrations, deletion/export, restore expectations | Backup, restore drill, version compatibility, shutdown/export plan |
| Release | Compatibility window, flag/rollout needs, rollback limits | Build identity, deploy check, client/server skew, rollback procedure |
| Support | How to diagnose and safely repair one user’s problem | Scoped access, actor attribution, replay/simulation, support tools |
| Product | Outcome measured, decision it informs, privacy/cost | Broad usage coverage, cohorts, ownership, retention and experiment policy |

## Confirmed starting defaults
Business measurement goals → required analytics capabilities → most private implementation meeting them. Broad usage analytics is normally required; privacy above metrics needs an explicit product decision. No data loss; seconds of downtime hidden where possible. Product phase and requirements determine exact budgets and exceptions. Verify the proposed proxy/restart behavior; it does not itself establish recovery or durability.

## Per-project questions
1. Minimum launch bar vs requirements earned by risk?
2. Default data-loss and downtime budgets for each product profile?
3. What customer data may support staff and telemetry services see?
4. Which failures deserve an alert, a daily queue or no human attention?
5. Who owns the product measures, and when should a feature be removed?

## Proof, not installation
A backup restores. A rollout runs the intended version. An alert reaches an owner. A failed job can be diagnosed and retried safely. A support action respects scope. A metric answers a decision.

Evidence: [Bubblehouse](21-bubblehouse.md), [Happy Grid](10-happy-grid.md), [Ulysses release notes](51-ulysses.md), [watchdog](60-other-code.md). The starting defaults are confirmed in this chat; detailed mechanics above remain proposals.

## Business outcomes — confirmed
Instrument the monetization/conversion funnel, monitor performance and test alternatives. This is ongoing product operation, not just an upfront architecture decision. Experiments and feature flags belong from day one; concurrent A/B testing is preferred, with sequential trials also supported. Specific events, cadence, assignment and evaluation mechanics remain to be chosen. [Context](83-business-and-onboarding.md).
