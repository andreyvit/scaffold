# Frontend language and build tools

## Confirmed · C66 · 2026-10-23
**Strong default: plain JavaScript with the simplest possible bundling process.**

- Andrey's previous bundler used JSON frontmatter to declare interfile dependencies, then combined files with optional wrapping. This is a user-reported example of acceptable simplicity, not a requirement to recreate that exact format. Implementation not located or inspected in this interview turn.
- He strongly dislikes TypeScript. When he last tried it several years ago, he found it pure overhead; perceived language complexity and slow builds count heavily against it. This is historical experience, not a benchmark of current TypeScript tools.
- TypeScript is a last resort: require something compelling enough to outweigh that complexity and build cost. The assistant's proposed TypeScript default is rejected.
- Dynamically typed code is acceptable with integration tests, which should exist anyway. Long experience with JavaScript, Ruby and similar languages informs this judgment.
- Excellent frontend test coverage is a much greater concern than static typing; TypeScript never replaces it.
- Agentic development could change the balance, but he has seen no evidence that plain JavaScript is insufficient. Do not adopt TypeScript merely because agents write the code.
- Excessive/unmanageable client JavaScript should prompt an architecture review, not an automatic TypeScript migration. This reinforces the SSR-first preference, not a prohibition on genuinely rich clients.
- In a project truly dominated by JavaScript, growth may eventually justify transitioning to TypeScript. No code-size threshold or migration trigger beyond compelling need is selected.

C64/C65 remain compatible: consider Svelte when richer client behavior earns compilation; do not infer TypeScript or an elaborate general-purpose build pipeline from that choice.

[Recipe](../../skills/scaffold/references/frontend-tooling.md).

## CSS · confirmed C67 · 2026-10-23
Tailwind remains the preferred CSS starting point. User answered “Yes” when asked whether the 2024 description of Tailwind as a useful shared styling vocabulary still applies.

The earlier [2024 writing](62-more-writing.md) also describes an owned subset for runtime-editable customer themes. This answer does not select that subset, a Tailwind version or a build pipeline as the general default. Preserve C66's minimal-tooling preference.
