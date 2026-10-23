# Rich pages within SSR

## Confirmed · C64 · 2026-10-23
Stimulus works well as a connection point in Andrey's experience. He has not personally needed to move to React. If richer client machinery is needed, he would consider a framework that compiles to JavaScript and adds reactivity before React.

Andrey confirmed the name: **Svelte**. Consider Svelte before React when richer client machinery is needed. This is an evaluation preference, not a finalized dependency choice. Rationale supplied in C65 below.

Andrey cites 37signals' calendar as an example of using React. Recorded as his recollection, not independently verified evidence or proof that calendars require React.

C37 remains in force: SSR + Turbo/Stimulus first; full SPA only on explicit user demand or demonstrated limitations that reasonable enhancement cannot solve.

Before adoption, verify the assumptions below against current tools and a representative page. [Recipe](../../skills/scaffold/references/web-rendering.md).

## Rationale · C65 · 2026-10-23
- Less JavaScript to load at runtime. Andrey observes that React adds delay on slower connections. The delay is not crucial, but he dislikes accepting a suboptimal approach when a better one is available.
- His limited interactions with Svelte suggest a pragmatic environment valuing simplicity and low churn. He calls simplicity and low churn primary values. **This assessment is provisional: contrary evidence would change his judgment of Svelte.**
- In his judgment React has moved in the wrong direction since hooks and tends toward excessive complexity and overengineering, amplified by its ecosystem. Record this as his assessment, not an objective characterization of every React app.
- His compilation argument: practical React use wants JSX and thus a compile step; given that step, consider Svelte and use compilation to produce efficient JavaScript.

No payload measurements or current churn/upgrade comparison performed. JSX is not technically required by React; the user's point concerns the workflow he would want. Svelte still emits runtime code; no zero-runtime or universally-smaller-bundle guarantee inferred. Evaluate delivered JavaScript/loading cost and actual framework/ecosystem complexity before adoption.

C66 selects plain JavaScript and minimal bundling; TypeScript is a last resort. [Language, build and test rationale](94-frontend-tooling.md).
