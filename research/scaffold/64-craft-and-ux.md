# Craft, ownership and user understanding

Follow-up questions: does care extend beyond abstractions? Does UX work prevent confusion or just explain errors? Where did cost justify compromise?

Current source: Andrey's confirmation in this chat, 2026-10-18. Historical evidence supports or bounds it; it need not prove a preference he has now stated explicitly.

| Value/default | Concrete evidence | Counterexample or limit |
|---|---|---|
| Own implementation by default | `jsonfix` preserves the standard decoder while adding a small owned layer; `sqlexpr` preserves normal Go/SQL control. [Libraries](31-small-libraries.md). | `sealer` uses established crypto/compression. [U6](53-ulysses-sources.tsv) explicitly favors libraries for specialist algorithms, platform quirks and maintained datasets. Dependencies need a reason, not a ban. |
| Think through small details | Maccel replaces input-source ordering assumptions with stable IDs (`09e99c46`). Happy Grid removes pointless forwarding and fixes first-party libraries at source (H2/H4). | These demonstrate concrete robustness/clarity, not a measured equal-cost elegance comparison. The stronger aesthetic tie-breaker comes from today's statement. |
| Avoid future minefields | Ulysses says not to defer error handling that changes the design (U1); stable public names survive internal renaming (B1). | The old router's middleware methods were unfinished; buddyd's SSO test was empty. These limit claims about historical execution, not the stated aspiration. |
| Prevent confusion | Bubblehouse fixes discount replacement timing so normal use does not produce “invalid code”; imported birthdays appear completed and eligibility is explicit. Sources below. | Fixes reveal that earlier behavior was confusing. They do not prove the entire product met the standard, or establish every original defect's author. |
| Speak the user's language | “Handle” becomes “Username”; inaccessible tabs receive a concrete explanation. Sources below. | Better wording alone does not establish that a user noticed, understood or could act on it. Today's value requires evaluating the whole flow. |
| Care within real costs | Voting queue simplified after mmap complexity; preserves room for a larger queue later (M3). Paid image optimization disabled to contain cost (`2bfd48465`). | Queue overflow discards events. Historical scope-specific compromise; no permission to lose durable user work. Cost saved is not proof every quality tradeoff was good. |
| Privacy by default | Prior public/private error separation (B9) limits accidental disclosure. | Sarekon removed analytics, but motive is unknown. Neither this nor logs establishes a historical privacy policy. Today's statement supplies the default. |
| No loss; brief hidden downtime | Backup/restore workflow and persisted job recovery (B4/B8) support recovery care. | Historical queue loss and single-server choices are not evidence of universal zero-loss/uptime guarantees. Define failure scenarios per project. |
| Native mobile now | Earlier native UI care: picker animation, cached content after refresh failure, larger touch targets. | LiveReload shared a Node model/controller runtime. That is an older tradeoff; today's native preference explicitly changes the decision under AI. No company-trend claim is needed. |

## New Bubblehouse sources
Repo `/Users/andreyvit/Developer/prairie/backend`. Each commit's author/date and relevant diff checked; all Andrey, before June 2025. Generated assets excluded.

- `74b8aed4cefff1706623d0446122e460b33efa0b` (2025-03-14): commit rationale; `fire/business/redemptions/pointredemption.go`, `shopify/extensions/checkout-rewards/src/Checkout.jsx`; delayed invalidation and serialized host operations. Regression scenario in `fire/apicheckoutandpos/api-checkoutext_test.go`.
- `7656132b12a728fc35a2f6277a9787dbf6517426` (2024-02-02): `fire/fireback/rewards-sources.go`, `rewards-vm.go`; imported birthday eligibility and completed presentation.
- `b3747a2d206ad47afa4a7f4ae66ec6e86f2bb15d` (2024-11-12): `fireback/bocommon-tabbedpage.go`; explain that no tabs are accessible.
- `1bdb6abb209793e769df83a73154fea075b6e70f` (2020-07-31): `templates/pages/admin_newprofile.html`, `admin_user.html`, `templates/partials/admin_user_table_header.html`; familiar user-facing term, internal field unchanged.

Earlier pointers: [Bubblehouse](23-bubblehouse-evidence.md), [Maccel](36-livereload-and-writing.md), [remaining code](60-other-code.md). These are historical examples, not a current runtime audit.

## LifeBase follow-up
- Mockko usability feedback records what users missed, expected elsewhere or misunderstood. Direct evidence for evaluating discovery and expectations.
- LiveReload critique follows real compilation/minification workflows before choosing defaults and UI. Care includes output paths and deployment consequences.
- LiveReload launch diary drops a website redesign when paid work consumes the day. A concrete limit on polishing.

[Findings and authorship limits](66-lifebase-expanded.md); exact sources L4–L6 in [source index](67-lifebase-sources.tsv).
