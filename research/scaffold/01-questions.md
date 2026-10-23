# Interview

Historical interview outline, not the current cursor. **Resume from [STATE.md](STATE.md#resume-here)** and check [confirmed decisions](78-confirmed-decisions.md) before asking anything below. Ask one question at a time. For each answer: **choice → why → scope → exception**. Do not treat my suggested answer as yours.

## Round 1 — which recipes matter first?
1. Which [product profiles](71-requirements.md) are first, later or out?
2. Which must work without an account/server? Which need durable offline edits or collaboration?
3. Native mobile is settled. Defer iOS/macOS internal-design questions until the [modern research step](88-apple-design-research-plan.md).
4. What downtime, data loss, privacy and support limits distinguish these profiles?

## Round 2 — apply the confirmed values
5. Values accepted, including ownership-first, craftsmanship and user understanding. Use concrete decisions to discover any remaining exceptions.
6. Historical authorship remains labelled; only investigate further if it affects a decision. Current confirmation establishes the values directly.
7. When do you accept complexity now to avoid a painful future change? Give one worthwhile and one speculative example.
8. How do you choose between improving the underlying library and making a narrow production fix?
9. Which maintenance do you want to own? When do specialist knowledge, ongoing updates or team capacity make a dependency the simpler choice?
10. What changed between trusted-human reviews and the Zoo AI review workflow?

## Round 3 — architecture choices
11. What concrete experience earns a rich client page? What earns a full SPA?
12. Must frontend tools preserve React-like composition? Which costs would make an owned renderer worthwhile?
13. Which needs override one-process/one-server simplicity? What must the basic scaffold leave easy to change?
14. Apple layering preferences recorded; modern internal design awaits research. Do not force historical mechanisms into current defaults.
15. Which operations need undo, audit, replay, offline writes or automatic merge? Choose separately.
16. Which [identity variants](73-accounts-decisions.md) should be standard recipes? Where must a person remain separate across companies?

## Round 4 — operating the business
17. What evidence must exist before first release, and what may wait for scale?
18. What may telemetry collect? What may support staff inspect or change? What should expire by default?
19. Which product outcomes should every app measure? Who acts on each measure?
20. Which tasks justify managed services: auth, database, payments, email, media, analytics, monitoring?
21. When you stop operating a product, what should remain usable or exportable?

## Contradictions to resolve through examples
- Standard reusable blocks vs a contextual one-off app architecture.
- Testing resolved by C43: algorithm unit tests, mostly whole-app integration tests, near-100% coverage except impractical edge cases.
- Native implementation is chosen despite duplicate effort; exact native mechanisms remain open.
- Stable external contracts vs freely changing internal abstractions.
- Security with little friction vs account recovery and abuse defenses.

These are tensions, not accusations of inconsistency. Earlier source-specific question files preserve how the investigation evolved.
