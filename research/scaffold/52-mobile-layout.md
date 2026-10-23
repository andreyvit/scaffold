# Mobile layout: recovered draft

Source U12, “Structuring iOS Projects,” content dated 2021-09-19. A historical proposal. The [2026-10-20 interview](87-ios-layering.md) now confirms layering and clarifies current boundaries/packaging; it does not approve every old folder or sharing choice.

```text
Application   startup, lifecycle, app-wide wiring, config, logging, analytics
Security      separate only if substantial
Data          bundled non-design data; Media if substantial
Styling       shared appearance and formatting
Screens       presentation for a whole screen
Components    reusable product UI
Model         domain data and decisions
Subsystems    server access, authentication, caching, product engines
Utilities     small, self-contained, boring, maintained by us
Vendor        copied third-party code still maintained elsewhere
```

Folders communicate what the reader must understand. A cache or state engine is important architecture; do not hide it under Utilities. Product-specific UI belongs in Components. A small generic UI helper may be a utility.

The draft has empty Screens/Model/Subsystems sections. Recover their intent from code and interview; do not fill them as if written by Andrey.

## Other mobile decisions recovered
- Settings: local when simple; cloud sync when setup effort warrants it; own server for cross-platform/control. Consider supportability and what survives business shutdown. [U13]
- Authentication draft starts with **no visible account** as an option. Do not force login into every app. [U14]
- Native views plus shared core was acceptable in LiveReload; test modern choices against actual UX needs.

## Research questions
1. Which app classes need local-first work, background work, media, sharing or collaboration?
2. Which state must survive termination, reinstall, offline edits and account changes?
3. What is worth sharing across platforms: domain logic, storage, networking, UI?
4. What native interaction quality is non-negotiable?
5. Which failures must users resolve, and which should recover silently?
