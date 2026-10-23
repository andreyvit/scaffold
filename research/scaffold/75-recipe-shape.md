# Recipe shape

Proposal. Keep research and source history here; publish only confirmed defaults and useful alternatives into the skill.

## Small linked files
- `values.md`: approved values, reasons, conflict rules.
- `app-web.md`, `app-ios.md`, `app-android.md`: choose profile; assemble subsystems; layout; startup; first working flow; release proof.
- `web-rich-page.md`, `web-spa.md`: explicit alternatives to the SSR default.
- `accounts.md`, `permissions.md`: identity/lifecycle separate from authorization.
- `state.md`, `storage.md`, `sync.md`, `jobs.md`, `integrations.md`: ownership, durability, boundaries.
- `logging.md`, `metrics.md`, `analytics.md`: diagnosis, operation, product learning.
- `testing.md`, `release.md`, `operations.md`: evidence and recovery.
- Existing config/environments recipes remain linked; avoid duplicate rules.

These are logical topics, not a requirement to create every file immediately. Split when a file has a distinct decision or reusable subsystem.

## One decision card
**Need. Default. Why. Change when. Ask. Prove.**

Omit empty fields. Link shared mechanics. Add security/metrics/logs/failure facts where relevant. Keep one canonical home for each rule.

## Example — rich web page
**Need:** a page has substantial local interaction.

**Default:** retain SSR navigation and server ownership; mount a client component inside a defined page region.

**Why:** local richness without making every page carry client routing and state.

**Change when:** the user explicitly requires SPA, or demonstrated SSR limitations cannot reasonably be solved with progressive enhancement. Rich interaction or state across screens alone does not establish this.

**Ask:** what user action cannot work well with Turbo/Stimulus?

**Prove:** navigation/back/restore, mount/teardown, keyboard/accessibility, failed saves, authorization and deployed asset compatibility.

The SPA escalation rule is confirmed; the rest of this example remains proposed implementation/verification guidance.

## Recording an interview decision
`ID · choice · why/value · applies to · exception · revisit when · source/date`

Proposed → confirmed / revised / rejected. Record disagreement and supersession; never silently erase the earlier reason.
