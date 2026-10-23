# Server templating — strategic work

## Confirmed · C68 · 2026-10-23
Andrey has no templating solution he is fully happy with. Address this strategically; good component support is part of the requirement.

Minicomponents is his best hack so far, but he largely stopped using it in a large project. Its template-rewriting approach causes too many scoping limitations and is too restrictive. Historical ownership/use is not an endorsement as the new scaffold default.

He plans to build his own templating language with component support soon. This records a planned direction, not an implemented language or a request to build it in this interview. No syntax, execution model, full requirements or interim engine selected.

Preserve the SSR-first architecture. Keep the template engine unresolved pending the separate strategic work. Do not launch a language-design interview or prescribe minicomponents as the universal solution.

[Historical source](60-other-code.md) · [Web recipe](../../skills/scaffold/references/web-rendering.md).
