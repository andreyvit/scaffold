# Web rendering

Default to server rendering with Turbo and Stimulus. Use Stimulus as the connection point for client behavior; Andrey has found it sufficient in his own work.

When a page needs richer client machinery, consider Svelte before React. This is an evaluation order, not a mandatory dependency. Reasons: lower expected JavaScript loading cost, pragmatic simplicity and low churn. When accepting a compilation step, use it to produce efficient browser code.

Keep rich-page enhancement within the server-rendered app where it meets the need. Choose a full SPA only on explicit user demand or demonstrated limitations that reasonable progressive enhancement cannot solve (C37).

Verify these expectations before adoption: compare delivered JavaScript/loading cost and the complexity/churn of the actual framework and tools. Andrey's favorable Svelte impression comes from limited use; contrary evidence should change the choice. Do not infer zero runtime code or a universal bundle-size advantage.

## Server templates
Good component support is required; no satisfactory template engine selected yet. Andrey plans an owned templating language with components as separate strategic work.

Do not default to minicomponents based on historical use: its template-rewriting scoping limitations proved too restrictive in a large project. Leave the engine choice open pending that work; do not invent an interim standard.
