# Frontend language and tooling

Default to plain JavaScript, including Stimulus controllers, with the simplest possible bundling process. Andrey's previous approach declared interfile dependencies in JSON frontmatter and combined files with optional wrapping; use this as a simplicity reference, not a required format or a mandate to build a new bundler.

TypeScript is a last resort. Require compelling benefits that outweigh language/tooling complexity and build cost. A growing, genuinely JavaScript-heavy project may eventually justify transition; ordinary frontend growth or agentic development alone does not.

Dynamic typing is acceptable with excellent integration-test coverage. Prioritize real frontend behavior and test coverage over static typing; keep that coverage if TypeScript is chosen. Follow [testing](testing.md).

If client JavaScript becomes unmanageable, first reconsider the architecture under [web rendering](web-rendering.md). A justified Svelte component does not imply TypeScript or an elaborate build pipeline.

Use Tailwind as the preferred CSS starting point and shared styling vocabulary. Keep its build integration simple; no particular version, custom subset or customer-theming feature is prescribed.
