# Ulysses: engineering values

Read original-looking engineering drafts. Most relevant sheets have 2021–2022 content modification dates. Dates support historical origin; they do not establish that every quotation is Andrey’s. Preserve named quotations as quotations.

## Strong historical statements
- **Malleability:** ordinary changes should not cause jumps in complexity. Preserve this through small improvements, not periodic rescue projects. [U1,U7]
- **Obvious correctness:** understand a unit without mentally executing distant code. Neither giant files nor hundreds of empty abstractions help. [U2,U3]
- **Abstraction earns its cost** by making reasoning and changes easier. For trivial tasks, straightforward code may be better. [U3,U4]
- **Model / presentation separation is fundamental.** MVC/MVVM/MVP within presentation is a contextual choice, not the point. [U3]
- **Design failures early.** Do not defer error handling that changes the architecture. Domain models need a safety margin against invalid states. [U1,U5]
- **Dependency choice depends on capability and upkeep.** Options: use, copy a narrow part, implement, or drop the feature. Keep a library for difficult algorithms, platform quirks or maintained datasets. [U6]
- **Planning manages uncertainty.** Clarify, bound, prototype, defer deliberately, or compare likely outcomes. Invest according to business return. [U8]
- **Release safety is a system.** Small frequent releases, staged rollout, flags and recovery complement testing. [U9]
- **UX is everyone’s job.** Help users accomplish real tasks; visual prettiness alone is insufficient. [U10]

## Questions changed by this source
- Stop asking whether you value abstractions. Ask what concrete reasoning/change benefit earns one.
- Stop asking which MV* name you prefer. Ask where state and responsibilities belong.
- Stop asking “dependencies yes/no.” Ask which maintenance burden we should own.
- Stop asking whether to plan. Ask which uncertainty must be resolved before committing.
- Review overhead differs for trusted humans and AI. Older writing explicitly values pace; current AI workflow adds strong review. [U11]

## Limits
These are unfinished drafts. Placeholder headings are questions, not opinions. Old package, framework, OS and App Store claims need fresh research. No modern mobile or security defaults are approved by this pass.
