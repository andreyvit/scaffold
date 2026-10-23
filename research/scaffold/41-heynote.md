# Heynote

Source: iCloud Drive/Notes. Mixed scratchpads: authored prompts, copied answers, logs and unrelated notes. Treat each block separately.

## Original-looking instructions — confirm at interview
- **Five code values:** simplicity; local reasoning; architecture that fits in a head; future simple tasks stay easy and complex tasks stay possible; empathy for the machine. Product goal is separate: make clients happy. [N1]
- **Code mirrors the business task.** Separate algorithms, business rules and integration glue. Improve existing machinery before adding wrappers. A helper does not redeem a workaround. Explain unavoidable deviations. [N2]
- **Abstractions must stay easy to change.** Hide complexity fully; avoid long-range effects. Shared middleware is a deliberate exception. [N3]
- **Security should be evident.** One common enforcement point plus a clear local override is acceptable; scattered emergent security is not. [N4]
- **Tests prove behavior.** Coverage can be 100% and still miss the logic. Prefer real integrated actions over checking configuration. Repeating simple expected values can make tests clearer. [N3,N5]
- **Opinionated but malleable.** Shared types and interfaces can change. Old and new styles coexist; new work should use the current style. [N6]
- **Fast feedback matters.** Replace slow docs tooling with a fast edit/preview loop; validate cross-references early. Storage abstraction justified by test speed, not hypothetical engine choice. [N7]
- **Max terse means plain.** Simplicity, brevity, clarity, humanity; specific words. [N8]

## Tensions to resolve
- Foresight vs speculative abstraction: which future need is credible enough to design for?
- Refactor core machinery vs keep a production fix narrow: where is the boundary?
- Security vs friction: a note explicitly tolerates login enumeration. Is that product-specific or a default?
- Session note prefers random session IDs; permits signed tokens for concrete distributed verification needs. Its advice to handwrite token handling needs separate security review; not adopted as a recipe. [N9]

## Authorship limit
These blocks read as task instructions and personal drafts, not assistant summaries. That is stronger than repository author identity, but the scratchpad has no per-block author record. Keep this label until confirmed or matched to an original user message.

Excluded: assistant-style passages (“If you want, I can patch…”), copied review findings, logs, credentials, unrelated personal material. Duplicate text in `prior-prompts.txt` and `scratch.txt` counts once.
