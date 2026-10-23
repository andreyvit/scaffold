# Which needs should recipes cover?

Historical proposed scope menu, not an approved profile catalog or an instruction to restart the interview. Product profiles can overlap. Current scope is in the [review overview](104-interview-overview.md); resume from [STATE](STATE.md#resume-here). The original menu follows.

| Product | Distinct pressure | First question |
|---|---|---|
| Personal utility | Tiny maintenance budget; long useful life | Must it work without your server? |
| Consumer productivity | Durable personal work; sync; undo | What may users edit offline? |
| Consumer entertainment/media | Responsive feed/playback; uploads; abuse | What is the core experience, and what can fail independently? |
| B2B workflow | Company ownership; permissions; integrations; support | Who owns data when a person leaves? |
| Embedded merchant app | Host identity, lifecycle and deployment constraints | Which host guarantees can we rely on? |
| Collaborative editor | Concurrent writes; conflicts; presence | Must simultaneous edits merge automatically? |
| Internal tool | Few trusted users; low ceremony | What changes when exposed outside the team? |
| Specialized high-stakes app | Strict availability, isolation or compliance needs | Support now, or require a separate design review? |

## Requirements that change the architecture
- **Outcome:** task success, learning, retention, revenue or operator time. How will we know?
- **Users:** anonymous / individual / household / company members / multiple companies.
- **Ownership:** person / tenant / shared object; moves, merges, deletion and export.
- **Client:** public web / rich workspace / embedded widget / iOS / Android / desktop.
- **Interaction:** forms / local rich editing / live collaboration / media / device integrations.
- **Connectivity:** online / cached reads / durable offline writes / peer or multi-device merge.
- **Data:** size, sensitivity, lifespan, acceptable loss, migration and portability.
- **Operation:** expected load, geography, downtime/recovery limits, on-call capacity, budget.
- **Business:** billing, entitlements, support access, experiments, abuse handling, shutdown plan.
- **Team:** owner, skills, number of maintainers, AI role, release cadence.

## Scope proposal
Start with web/B2B and consumer productivity. Keep entertainment, embedded apps and local utilities as named variants. Treat collaboration and stringent availability as explicit branches; no accidental promises.

This ordering is my proposal. No scope selection has been approved.
