# iOS layering and package costs

Direct interview source: Andrey, 2026-10-20. [Current scaffold guide](../../skills/scaffold/references/ios-layering.md). Supplements the [historical Ulysses layout](52-mobile-layout.md).

## Confirmed structure
- Application: app delegate/lifecycle and wiring.
- Cross-cutting concepts.
- Services: non-visual controllers.
- Screens: whole-screen controllers and their subcomponents.
- Components: reused across screens.
- Model: historically often includes persistence, Active Record style. If pure model/persistence are separate, use two layers.

Within a layer, feature often means screen. Large apps may need layer → major feature → screen. Do not invent one uniform tree depth.

Usually these are folders within one compilation module, not separate Swift packages. Consider app-core/platform separation where useful. This does not select shared iOS/Android code or a native UI framework.

## Why
Repeated experience found this layout convenient and alternatives inconvenient. Package boundaries are tools: when cheap/easy, use them for faster builds, clear allowed dependencies and avoiding circular package dependencies. If packaging is expensive/fussy, a single module is acceptable.

Historical Xcode friction is not a verified claim about today's toolchain. Current build/setup tradeoffs remain a research item; do not overpackage Swift by copying Go conventions.

## Deferred research
Andrey is not ready to select current iOS/macOS internal design based on historical experience. [Later research step](88-apple-design-research-plan.md): collect modern recommendations/arguments, group by approach, then consider each. Stop asking implementation-choice questions for Apple apps until that work.

## Still open
Pure model vs combined persistence default; exact modern native state/UI/storage mechanisms; justified app-core/platform split.

The pending Go error-handling question was not answered by this message.
