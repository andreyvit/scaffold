# Happy Grid

Strongest source: original user messages, Feb–Mar 2026. Git identity alone was insufficient. [Evidence](10-happy-grid-evidence.md).

## Explicit choices
- Build UX people want to use. Content first; direct editing; subtle but visible controls; show the next action. H1.
- Remove wrappers and repeated declarations that add no behavior. H2.
- Keep business logic out of app wiring; generic email sending out of auth. H3.
- Fix first-party libraries at their source; avoid caller workarounds. H4.
- Test real startup, shutdown, login and browser use. Capture sent mail in tests. H5.
- Make development inspectable: shared fixtures, isolated state, DB dumps, raw metrics. H6.
- Write short, concrete specs. Evidence should let a person check the result. H7.

## Package layout — authorship confirmed 2026-10-20
Andrey confirms he wrote the package-layout docs and chooses their hybrid approach. [Recovered layout and version limits](86-go-package-layout.md). This resolves layout authorship, not every philosophy bullet or later edit.

## Architecture specifics
- Request context carries services, actor and transaction access. H8.
- Typed, serializable changes record cause and account. Validate before writing; app errors do not roll back. H9.
- Shared structs reduce App accessor clutter: services and metrics. H3.
- Routing can add metadata and replace middleware without prescribing middleware behavior. H10.
- Account/organization rules depend on the business. March SSO: account = customer company; organization = its client. Resolve account first; account controls its users and organizations. H11.

These are project decisions. Their reuse scope still needs agreement.

## Candidate philosophy
README’s Feb 22 revision: pace through low debt; simple architecture; ownership; modularity; useful abstraction; broad integration tests; inspectable development; all durable knowledge in repo.

Andrey says he reorganized README and will maintain its context himself (H12). Exact authorship of every philosophy bullet remains unproved. Keep as candidates, corroborate elsewhere; do not count AI summaries as independent support.

## After this source
- Which abstractions earn their cost? Useful mechanics and domain vocabulary seem welcome; empty forwarding and mixed concerns do not.
- Is “near 100%” coverage universal, or specific to this AI-built product?
- Does simple deployment imply single-server by default beyond small B2B products?
- When should UX richness justify a client app rather than Turbo?
- Which products need change records, undo or replay? These are different requirements.
- Should identity span accounts? Early vision says yes; March SSO refuses cross-account moves. Resolve the intended variants.
- Which account rules protect a trust boundary, and which merely encode this product’s organization model?

## Limits
Reviewed original messages for 43 root chats; 410 indexed chats include subagents. Read README/history and selected corrections. Modern implementation and AI-generated specs are not value evidence. Quoted go-to-market copy in a user message has uncertain original authorship; excluded as a source value.
