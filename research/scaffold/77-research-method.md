# How we build the recipes

1. **Choose supported needs.** Mark profiles first/later/out. Ask about outcomes and constraints before technologies.
2. **Apply confirmed values.** Core values accepted on 2026-10-18. Refine exceptions through concrete choices; recover historical authorship only where it changes a conclusion.
3. **Map decisions.** List viable options and the requirement that separates them. Recommend one, with a reason and cost.
4. **Interview.** Ask only about real tradeoffs, supported requirements or values. One decision at a time: preference, why, counterexample, reversal trigger. Derive obvious implementation consequences from confirmed choices; verify technical feasibility yourself. Update values when a new reason appears.
5. **Research the uncertain parts.** Official docs; current versions; focused comparison for actual product needs.
6. **Prove the architecture.** Small end-to-end app: state, identity, storage, failure, diagnostics, deployment. Exercise the hard path, not just a hello-world screen.
7. **Write the terse recipe.** Default + reason + exception + question + proof; link shared subsystems.
8. **Use and revise.** A real project reveals missing decisions. Preserve why a default changed.

## Comparison tasks — choose only relevant ones
- Rich web: editable grid; save failure; back/forward; component cleanup; new deploy with old tab.
- Native: long list; keyboard/editing; accessibility; process death; offline save; account switch.
- Identity: invitation; two companies; leaving company; lost credential; support recovery.
- Operation: failed migration; restore; duplicate job; downstream outage; one-user diagnosis.

Measure clarity, owned complexity, build/edit feedback, UX and failure behavior. Choose budgets before running the comparison; do not move the goalposts to favor a favorite stack.

## Source rule
Original statement > attributable manual decision > bounded code inference. An AI summary can locate evidence but cannot become evidence by repetition. Old content timestamps and Git names are clues, not absolute authorship proof.

## Stop researching a branch when
Its remaining uncertainty requires a product choice or Andrey’s judgment. Record that question. More unrelated code is not an answer to a missing preference.

## Interview correction · C61 · 2026-10-23
Do not turn obvious engineering consequences into preference questions. With the job queue in the main database by default, saving scheduled jobs in the originating transaction follows naturally when technically feasible. Record the consequence; investigate feasibility rather than asking Andrey to approve it. A useful interview question needs competing benefits or a missing business/value judgment.

## Foundation vs product feature · C63 · 2026-10-23
Separate the internal foundation, optional features the recipe supports, and the choices a specific product owner must authorize. Do not ask Andrey to pick one UI policy for all future products. Roles exemplify the distinction: permissions/roles/default roles are foundational; role-customization UI is offered separately and implemented when authorized. The earlier multiple-login architecture uses the same separation (82). Do not generalize this into prebuilding every speculative capability.
