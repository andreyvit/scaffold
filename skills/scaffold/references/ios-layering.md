# iOS layering

Organizational preferences only. Modern iOS/macOS internal design is deferred pending research; do not treat historical mechanisms here as selected current defaults.

Organize by layer, then feature or screen. This structure has repeatedly proved convenient in Andrey's apps. For large apps, use layer → major feature → screen where useful.

| Layer | Responsibility |
|---|---|
| Application | Startup, lifecycle, app delegate and wiring |
| Cross-cutting concepts | Concerns shared across the app |
| Services | Non-visual controllers |
| Screens | Whole-screen presentation/controllers and screen-specific subcomponents |
| Components | UI reused across screens |
| Model | Domain data and behavior; may include persistence in Active Record style |
| Persistence, if separate | Storage mechanics when using a pure model layer |

These describe responsibilities, not a prescribed dependency order or a choice of UIKit over SwiftUI. Select modern mechanisms separately.

Typically implement layers as folders within one compilation module. Do not map every layer or feature to a Swift package. Consider separating app core from platform-specific code when useful.

Use package/module boundaries where their build-speed and dependency-enforcement benefits earn their setup/maintenance cost. Cheap packages can make allowed dependencies clear and prevent cycles; costly packaging can justify one module with folder boundaries. Verify current toolchain costs rather than treating historical Xcode friction as permanent.

Model/persistence separation is not yet a universal default. The historical combined model and a separate pure-model/storage design are both candidates.
