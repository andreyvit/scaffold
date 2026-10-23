# Coverage and limits

2026-10-18. **163 checkout entries screened; 44 library source rows.** Counts are inventory, not 163 independent deep reviews. [Repository detail](02-repositories.tsv), [libraries](32-library-sources.tsv).

## Substantive passes
| Source | What was examined | Output |
|---|---|---|
| Happy Grid | 43 root chats; original user messages; selected docs/history | [Findings](10-happy-grid.md) |
| Bubblehouse | Historical backend docs; own jobs/auth/metrics/testing/integration code; early legacy commits | [Backend](21-bubblehouse.md) |
| Bubblehouse iOS | Archived Git history; selected Andrey state/animation/offline commits | [Mobile](22-bubblehouse-mobile.md) |
| Personal code | Native apps, libraries, LiveReload rationale; selected own implementations/corrections | [Libraries](31-small-libraries.md), files 33–36, 60–63 |
| Heynote | Relevant original-looking instruction blocks in mixed synced scratchpads | [Findings](41-heynote.md) |
| Zoo | v1 personas, source prompts, public account, tests/helpers essay, terse skill | [Findings](43-zoo.md) |
| LifeBase | Writing, Core, hiring, raw dictations, selected Daily/Diary, Past and older Inbox product drafts; topic screening then relevant reads | [Expanded findings](66-lifebase-expanded.md), [22 source pointers](67-lifebase-sources.tsv) |
| Principal hiring | Current and historical postings; manual-edit clue; scenario questions; derived guides excluded as evidence | [Findings](65-hiring.md) |
| Ulysses | 514 non-trash sheets indexed; relevant engineering drafts selected and read | [Values](51-ulysses.md), [layout](52-mobile-layout.md) |
| Other writing | Older public essays, mvpalliance drafts, teaching material | [Findings](62-more-writing.md) |

## Deduplication
- Bubblehouse backend/back2–10/clone/worktree share history; count once as evidence.
- Happy Grid checkouts share project context; messages count once.
- LiveReload 2/3/old overlap; compiler/library copies overlap. Alternate-object path repaired only through a temporary read-only environment override.
- Sarekon nested native checkouts duplicate sibling apps. Maccel/MacAccelerator share history.
- Copied note/prompt text is one source, not independent corroboration.

## Excluded or shallow
- Other authors’ code; imported libraries; generated boilerplate; explicit AI text, even before June 2025.
- Current AI-era implementations unless an original user decision was recovered.
- Small experiments, site/config repositories and stubs: tree/README screening; targeted code only where useful. No whole-app values inferred from their mere existence.
- Bubblehouse Android has no eligible Andrey commits in the checked history. Sarekon Android and Bubblehouse web contribute selected own changes only.
- Mixed wiki/infra material is not universal Andrey guidance. Credentials and unrelated private records are excluded from outputs.

## Open evidence gaps
- Exact authorship of Happy Grid README philosophy, public principles, parts of the edited LifeBase essay, hiring expansions and Zoo blog wording. LifeBase raw dictation now recovered for part of the architecture essay.
- Heynote has no per-block author metadata; original-looking prompts need confirmation where not independently matched.
- Ulysses content mtimes support age, not exact creation/authorship. Unfinished headings are not positions.
- No exhaustive line-by-line audit of thousands of commits; targeted history answered the evolving value questions.
- No blanket search of unrelated personal documents, deleted Ulysses sheets or inaccessible remote repositories. No evidence from those is claimed.
- Current mobile choices have only an official-source scan; executable comparisons follow selected requirements.

## Where further digging would help
Recover an original transcript for an uncertain statement **if its wording changes a decision**. Otherwise ask Andrey. Deepen code history for a specific tradeoff or counterexample; avoid repeating the whole survey.
