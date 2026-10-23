# Zoo v1 and role models

Questions entering: what do the personas stand for? Which rules came from Andrey?

## Sources
- Zoo v1: `~/Developer/andreyvit/zoo`, `2aa5125`. Earlier snapshot: `aaf8b2a` (2025-08-22).
- Public account: `~/Developer/pub/tarantsov`, `b77039e:content/blog/2025-09-29-all-star-zoo.md`; later edits mainly copyediting/frontmatter.
- Matching scratch instruction: Heynote N10. Original Happy Grid chats independently name the same roles.

## Supported choices
- **Linus:** high-level judgment: right problem, right abstraction, complete work, honest tests. Scratch prompt and blog agree.
- **Don:** chosen to insist on correctness and quality; replaced the Joel persona as lead when it dismissed review feedback to ship sooner.
- **Joel:** retained for attention to detail and explicit implementation plans.
- **Rob:** chosen as implementer. Blog reports no immediately noticeable benefit; do not invent a measured effect.
- **Kent:** test engineer; **Kevlin:** ordinary code reviewer; **Knuth:** stop coding and think when stuck.

These are Andrey’s uses of personas, not factual claims about what the real people would decide.

## Authorship boundary
The blog explicitly says Claude wrote instructions and Andrey curated them. The agent files contain extensive persona elaboration and unattributed quotations. Their wording is NOT original-value evidence. Current `.zoo/` files also contain imported Bubblehouse rules; do not equate them with universal values.

`tests-and-helpers.md` has an explicit “I wrote” claim in the blog. Its walkthrough asks whether a helper earns its abstraction, belongs in a shared place, preserves the underlying API, or merely obscures an assertion. Strong corroboration, but still verify authorship of the AI-era blog at interview.

## Useful tension
2021 Ulysses writing favors trusted developers’ pace over mandatory peer review. Zoo uses heavy AI review. Likely different error rates and review costs; confirm. Do not turn the AI workflow into a universal human-team process.

## Ask later
1. Are these the intended values of each role model? Which are missing?
2. Where should speed beat refinement after correctness is established?
3. Which review gates are specifically compensation for AI weaknesses?
