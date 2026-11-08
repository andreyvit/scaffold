# Great macOS productivity and utility apps

Scope confirmed 2026-11-07: productivity and utilities. Particular emphasis: the minute appearance and interaction details that make a Mac app feel excellent. Other categories appear only as labelled comparisons. Research recommendations do not change scaffold defaults.

**Great Mac apps preserve the user's control:** fast access, familiar commands, precise editing, stable context and trustworthy data. Distinctive visuals work best when they reinforce that behavior. A small utility can earn lasting loyalty by removing one repeated annoyance; polish alone does not prove a viable business.

This report covers **162 paired UI details**, concrete screen compositions, five visual families, **114 named ecosystem entries**, compatibility strategies, business measurements and failure lessons. Good and bad choices appear together. Research checked 7 November 2026; historical evidence is labelled.

### Reading paths

- **Design:** [visual directions](#visual-directions-choose-a-coherent-whole), [visual/workflow details](#visual-and-workflow-details), [screen compositions](#assemble-screens-around-the-work), [Mac components](#mac-command-and-component-reference).
- **Quality:** [reliability scenarios](#reliability-is-part-of-the-interface), [app exemplars](#strong-exemplars-with-limits), [long-term use](#long-term-use-and-contrary-experience).
- **Business:** [pricing](#pricing-models-coexist), [failure lessons](#failure-trust-and-switching), [economics](#full-economics), [measurements](#business-measurements-and-storefront-evidence).
- **Engineering:** [stacks](#technology-stacks-and-development-tradeoffs), [compatibility](#compatibility-is-four-promises), [ecosystem](#named-ecosystem-catalog), [avoid/migrate decisions](#named-technologies-to-avoid-migrate-or-constrain).
- **Execution:** [what to build first](#what-to-build-first), [sources and method](#sources-and-reading-method).

## Scope and evidence

A productivity app holds sustained work: notes, plans, calendars, documents, reference collections. A utility briefly intervenes: launch, capture, paste, rename, route audio, arrange windows. Their shared standard is **control without friction**; their appropriate size, density and persistence differ. A utility should return focus promptly. A workspace should preserve context for hours. Do not make either behave like a mobile onboarding funnel.

This report separates **Apple guidance**, **documented product behavior**, **reviewer/user judgment**, **developer business claims**, and **research recommendations**. “Great” is not a revenue ranking. Delight, usefulness, adoption, retention, revenue, profit, maintainability and editorial recognition require different evidence. Public screenshots establish appearance; support pages establish promised behavior; neither establishes measured speed or reliability. No hands-on installed-app benchmark is claimed.

Research date: **7 November 2026**. Treat versions carefully: historical Things 3 launch screenshots remain instructive but do not establish today's chrome. Current Apple macOS guidance was changed on 28 October 2026 to include touch input. Its advice retains pointer/keyboard density while accommodating brief touch interactions. Do not transfer iPhone layouts or assume all Macs have identical inputs. [Apple: designing for macOS](https://developer.apple.com/design/human-interface-guidelines/designing-for-macos/)

## Visual directions: choose a coherent whole

These are useful design families inferred from actual examples, not measured market trends. Combine compatible traits deliberately; do not average them into one generic dashboard.

### Quiet, document-centered craft — Things and Bear

Things' published project screen uses a white field, a strong project title, blue section headings, fine dividers and light metadata. Checkboxes form a stable left edge. Dates, tags and notes receive less emphasis than task names. Its expanded task is a local editing surface; it need not replace the whole workspace. The generous spacing makes a short plan inviting; copying it indiscriminately into a 10,000-row utility would waste space. The example inspected is a **historical 2017 asset still published on the features page**, not proof of current window styling. [Things features](https://culturedcode.com/things/features/)

Bear's current published Mac hero has three distinct zones: dark navigation, a pale note list, and a white editor. A restrained red accent marks selection and links; note previews contain meaningful images and text. Large document headings coexist with smaller navigation labels. This is branded typography within a recognizable Mac workspace. The editor permits separate fonts, line height, line width, paragraph spacing and indentation. Those controls serve long reading/writing sessions; they need not become global UI typography controls. [Bear](https://bear.app/), [typography settings](https://bear.app/faq/typography-options/)

**Build:** establish a readable text measure; give the document the strongest hierarchy; keep chrome quiet; put rich metadata behind disclosure. **Cost:** careful editor behavior, selection, attachments, undo and text input matter more than a beautiful empty page. **Failure:** pale metadata that cannot be read, oversized headings that leave three rows visible, or bespoke controls whose meanings disappear outside the designer's favorite theme.

### Compact instrument — SoundSource

The directly inspected SoundSource 6 screenshot shows aligned columns for app/device identity, volume, boost, route and effects. Green highlights communicate activity while numeric percentages add precision. White groups on a neutral surface separate system audio from individual apps. This is a small instrument panel, not a stack of unrelated cards.

Its designer documents rejecting a chunky slider because mute and slider hit areas collided at low volume. More complex device configuration moved into separate windows. Concentric corners were adopted; low-legibility glass was rejected. The lesson is selective platform fidelity: preserve hierarchy and recognizable controls while judging each visual fashion against the task. This is the developer's account, not a controlled usability study. [SoundSource 6 design stories, May 2026](https://weblog.rogueamoeba.com/2026/05/07/soundsource-6-design-stories/)

**Build:** align repeated measurements, keep labels near controls, show state at a glance, expose advanced configuration without enlarging every routine interaction. **Cost:** custom controls must preserve keyboard, accessibility, tooltips and clear hit targets. **Failure:** nesting every row in another rounded card, hiding slider handles until hover, or placing mute inside the drag target.

### Command-centered utility — Alfred and Raycast

Alfred's published search screenshot uses one dominant query, a strong selected row, recognizable result icons, secondary paths, and visible keyboard hints. It is intentionally transient: choose an action and return to work. Themes can change its surface while the result grammar remains stable. Its workflows add a separate authoring environment; the launcher does not try to expose that complexity in every result. [Alfred](https://www.alfredapp.com/)

Raycast emphasizes a common command interface across many integrations. This creates a useful constraint for extension authors: consistent list rows, details and actions reduce relearning. Its marketing claims about speed and crash-free rate are developer claims; no comparative performance test was conducted here. [Raycast](https://www.raycast.com/)

**Build:** predictable invocation, immediate query focus, stable selection, direct completion, visible alternate actions, clean escape back to the previous app. **Cost:** global shortcuts, focus restoration, extension isolation, async result races and permissions. **Failure:** treating a command launcher as a miniature website, changing the selected result under Return, or letting network-backed search block local results.

### Familiar multi-pane workspace — file and information utilities

Transmit demonstrates the usefulness of a familiar dual-pane file model with an activity view, inspector and batch rename. Its value lies in exposing source, destination and operation status together. Use this family for file tools, mail, reference libraries and substantial collections. It is appropriate when users compare or move objects across contexts. A split view should earn its width; a tiny single-purpose timer does not need a sidebar. Product behavior was read; the screenshot download was blocked, so no direct Transmit visual inspection is claimed. [Transmit](https://panic.com/transmit/)

**Build:** distinguish navigation, collection, detail and inspector; retain selection while changing a view; let panes resize or collapse. **Cost:** selection ownership, multiwindow state, toolbar scope and compact-width behavior. **Failure:** a web-style left rail plus another sidebar plus cards plus an inspector, all permanently visible.

### System-led material and restrained personality

Apple places Liquid Glass in the functional layer for controls/navigation and standard materials within content. It explicitly warns against overuse. Prefer semantic materials and colors, not a sampled blur/color from a screenshot. Test the window over real content and wallpapers, inactive, in both appearances, with reduced transparency and increased contrast. A clean screenshot on one wallpaper proves little. [Apple materials](https://developer.apple.com/design/human-interface-guidelines/materials/)

The disagreement is substantive. Rogue Amoeba rejects blurry surfaces but accepts selected geometry. Jim Nielsen objected to Tahoe's indiscriminate menu icons and uneven alignment while praising spatial window-arrangement icons that communicate more quickly than words. These are reasoned critiques, not evidence that every user rejects the new appearance. Current menu guidance must be checked separately from the 2025 controversy. [Nielsen, December 2025](https://blog.jim-nielsen.com/2025/icons-in-menus/)

**Build:** use stock controls as the baseline; put personality in the app icon, content, illustration, a restrained accent and a few purposeful transitions. **Cost:** new SDKs can change appearance; inspect every supported OS. **Failure:** freezing an imitation of one OS release, or replacing useful contrast with glass because a marketing mockup looked fashionable.

### Motion: continuity before spectacle

Keep an expanding row anchored to its original position; show where inserted, moved and removed items went. Let repeated keyboard actions interrupt transitions. Keep a stable final state when Reduce Motion is enabled. A spring is a choice of character, not proof of quality. Apple's current motion guidance asks for brief, purposeful, cancelable motion and warns against adding delay to frequent operations. [Apple motion](https://developer.apple.com/design/human-interface-guidelines/motion/)

Design Spells catalogs Things' minimum-window-size rubberbanding and progress animation. These identify concrete behaviors worth studying, but its textual catalog alone does not establish timing, interruptibility or accessibility. Treat a clip as a prompt to prototype and test, not as a prescribed animation curve. [Things details catalog](https://designspells.com/apps/things)

A separate Things Mac demo was directly inspected through sampled frames: the task card grows downward as a checklist gains rows; title and note remain anchored above, while scheduling controls move with the lower edge. This is a concrete continuity pattern. The published asset is from 2017; sampled frames establish geometry and sequence, not current timing or interruptibility. The Design Spells media route returned HTTP 429, so this first-party demo supplied an accessible alternative. [Things Mac demonstration](https://static.culturedcode.com/things/videos/2017-05-18-website-videos/1-design-hotels-3-mac-2.mp4)

## Practical design resources

| Resource | Useful work | Limits and fit |
|---|---|---|
| [Apple Design Resources](https://developer.apple.com/design/resources/) | Current windows, controls, typography, materials and icon templates; start a coherent Mac mockup | Match the kit version to the deployed OS. Design assets are not production components; Apple license terms apply. |
| [SF Symbols](https://developer.apple.com/sf-symbols/) | Match symbol weight, scale and rendering to nearby text; inspect availability and localization | Check OS availability and restricted symbols. Do not assume export gives an unrestricted cross-platform icon license. |
| [Apple fonts](https://developer.apple.com/fonts/) | System type, optical behavior and language coverage | Use runtime font APIs. Downloaded fonts carry Apple-specific license terms; do not extract another app's font. |
| [Bear typography](https://bear.app/faq/typography-options/) | Study user control over sustained reading/writing | Editor settings are not a prescription to theme all chrome. No license to copy proprietary assets. |
| [Rogue Amoeba design essays](https://weblog.rogueamoeba.com/category/news/the-design-of/) | Real iterations, rejected controls, inspector/popover tradeoffs | First-party intent; shipped and rejected mockups are explicitly distinguished. Some examples are audio/creative tools. |
| [Design Spells](https://designspells.com/apps/things) | Small interaction references, including actual desktop examples | Mixed platforms; record the platform and date. A short clip is not long-term-use evidence or reusable licensed code. |
| [before.click](https://before.click/) | Mac-filtered App Store screenshots, onboarding/paywall copy and icon references | Marketing assets, not a complete in-app flow library. Public browsing was available; popularity and curation do not prove conversion. |
| [Butterick's Practical Typography](https://practicaltypography.com/typography-in-ten-minutes.html) | Accessible book text on body text, measure, spacing and hierarchy | Document typography. Do not transplant web pixel sizes or its preference for purchased fonts into Mac control labels. |
| [Nielsen's menu critique](https://blog.jim-nielsen.com/2025/icons-in-menus/) | Learn to question icon meaning, alignment and cognitive cost | Historical Tahoe critique; examples support reasoning, not a representative user survey. |

Direct visual inspection covered published SoundSource 6, Bear Mac, Things project and Alfred search images, plus sampled frames from a Things Mac demonstration. Asset age is stated where identifiable. Product pages and written descriptions were inspected for other examples. No installed-app interaction, timing measurement or exhaustive accessibility verification follows from these assets.

## Visual and workflow details

The entries below are research recommendations derived from the cited convention or example. Exceptions depend on the operation; “native” does not mean blindly copying every Apple app. The component catalog later supplies more keyboard, window and control details.

### Composition, type and surfaces

**D001 — Stable alignment.** Align titles and controls on stable columns. Avoid centering each row independently. Adjust asymmetric icons optically without moving the label column. [Layout](https://developer.apple.com/design/human-interface-guidelines/layout/)

**D002 — Group with space first.** Keep related controls close. Add separators where space alone is insufficient; avoid a card around every label. [Layout](https://developer.apple.com/design/human-interface-guidelines/layout/)

**D003 — Hierarchy without faint text.** Distinguish title, value and supporting text through weight, size and placement before reducing contrast. Avoid thin gray type as the sole sign of refinement. Secondary information can be quieter, but must remain legible on the actual material. [Typography](https://developer.apple.com/design/human-interface-guidelines/typography/)

**D004 — Content size differs from control size.** Provide useful reading enlargement in editors and lists while preserving navigation hierarchy. Do not force a giant document heading into every toolbar or treat the minimum legible size as a design target. Apple lists 13 pt as the Mac default and 10 pt as the minimum in its accessibility guidance; these are guidance, not a universal size for every text role. [Accessibility](https://developer.apple.com/design/human-interface-guidelines/accessibility/)

**D005 — Correct system font roles.** Use dynamic system variants for labels, menus and controls rather than hardcoding one SF face and size everywhere. Custom brand fonts fit content if readable and licensed. A close imitation can still differ in baseline, weight and optical spacing. [Typography](https://developer.apple.com/design/human-interface-guidelines/typography/)

**D006 — Reading measure.** Limit prose width even when the window is wide; let a user choose comfortable width and leading. Stretching a note edge-to-edge makes line return harder. Tables and code may need a wider or independently scrolling area. [Bear typography](https://bear.app/faq/typography-options/), [Practical Typography](https://practicaltypography.com/typography-in-ten-minutes.html)

**D007 — Stable numerals.** For changing durations, file sizes and measurements, consider tabular numerals and a stable unit column. Avoid values that make adjacent controls jump on each tick. This is a layout recommendation for instruments, not a rule for ordinary prose. [Layout](https://developer.apple.com/design/human-interface-guidelines/layout/)

**D008 — Semantic colors.** Use system label, selection and background roles; test custom accents in light/dark and high-contrast modes. Hardcoded white, black and translucent gray often fail when the window becomes inactive or its background changes. [Color](https://developer.apple.com/design/human-interface-guidelines/color/)

**D009 — Color is supplementary.** Distinguish warning, completion, synchronization and selection through words, shape or state as well as hue. A red/green dot alone hides meaning from some users; decorative color is fine when it carries no required information. [Accessibility](https://developer.apple.com/design/human-interface-guidelines/accessibility/)

**D010 — Material has a job.** Use a material to establish a functional layer, not merely to blur content. Avoid translucent reading surfaces over busy text. Prefer the regular glass variant for substantial text; the clear variant has narrower media-oriented use. [Materials](https://developer.apple.com/design/human-interface-guidelines/materials/)

**D011 — Resize is a designed state.** Set a useful minimum, let content gain space, and collapse optional panes intentionally. Do not enlarge every gap proportionally or leave clipped controls at the minimum width. Preserve access to functions even when their presentation changes. [Layout](https://developer.apple.com/design/human-interface-guidelines/layout/)

### First launch, settings and permissions

**D012 — Start with the useful action.** Present an empty working surface with one clear next step, or a usable example. Avoid compulsory tours of ordinary Mac conventions. Complex utilities may need a short prerequisite flow before they can function. [Onboarding](https://developer.apple.com/design/human-interface-guidelines/onboarding/)

**D013 — Teach in context.** Show a tip beside the relevant control after the user reaches it. Avoid a first-launch carousel requiring memorization of five future tasks. Let skipped tutorials remain available in Help without reopening on every launch. [Onboarding](https://developer.apple.com/design/human-interface-guidelines/onboarding/)

**D014 — Ask for a permission at its reason.** Explain screen capture when starting capture, or microphone access when recording. A utility whose sole function requires permission can explain it during setup. Do not request all conceivable permissions before showing value. [Onboarding](https://developer.apple.com/design/human-interface-guidelines/onboarding/)

**D015 — Denied permission is a real state.** Preserve the pending task and explain which feature is unavailable and how to restore access. Repeatedly invoking the same denied prompt is not recovery. Unrelated features should keep working. [Privacy](https://developer.apple.com/design/human-interface-guidelines/privacy/)

**D016 — Sensible defaults reduce setup.** Detect appearance and hardware where possible; do not ask users to configure what the system already knows. Product-specific overrides can be useful, but should clearly state their scope. [Settings](https://developer.apple.com/design/human-interface-guidelines/settings/)

**D017 — Advanced controls need space.** Put extensive device/account configuration in a real pane or window when a popover becomes a maze. Avoid hiding three layers of navigation inside a tiny transient surface merely to preserve a clean main screenshot. [SoundSource design](https://weblog.rogueamoeba.com/2026/05/07/soundsource-6-design-stories/)

### Search, lists and ongoing work

**D018 — Search privacy.** Let users clear recent queries; avoid unexpectedly exposing sensitive history during screen sharing. History improves recall only when its visibility is acceptable. [Searching](https://developer.apple.com/design/human-interface-guidelines/searching/)

**D019 — Separate “empty” from “no match.”** An empty collection suggests creating/importing; no match suggests editing the query or removing a filter. A connection failure needs retry and saved context. Do not use the same cheerful illustration for all three. This follows the requirement to communicate scope and operation state. [Searching](https://developer.apple.com/design/human-interface-guidelines/searching/), [Progress](https://developer.apple.com/design/human-interface-guidelines/progress-indicators/)

**D020 — Search should not steal the next action.** Maintain query focus and stable keyboard selection as asynchronous results arrive. Cancel obsolete requests; do not execute a different result because ranking changed under Return. This is an implementation consequence of a keyboard-first launcher, not a documented benchmark result. [Alfred](https://www.alfredapp.com/)

**D021 — Keep pending work visible.** Retain content during background refresh; use a local status indicator. Replacing an entire populated window with a spinner destroys orientation. A blocking state is justified only when the operation truly prevents further safe work. [Progress indicators](https://developer.apple.com/design/human-interface-guidelines/progress-indicators/)

**D022 — Honest progress.** Show measurable progress when available; distinguish preparation, transfer and finalization. Do not sit at a fictitious 99% indefinitely. An indeterminate indicator is better than an invented estimate. [Progress indicators](https://developer.apple.com/design/human-interface-guidelines/progress-indicators/)

**D023 — Cancel has semantics.** State whether canceling keeps completed files, loses partial progress or stops only future jobs. Offer pause when useful. Do not label a button Cancel if it merely hides the window while work continues. [Progress indicators](https://developer.apple.com/design/human-interface-guidelines/progress-indicators/)

**D024 — Background notices stay in the background.** A routine available update should not interrupt typing with a frontmost dialog. Loopback's April 2026 release replaced that behavior with a title-bar indicator; urgent incompatibility or security action may warrant greater prominence. [Loopback release notes](https://rogueamoeba.com/support/releasenotes/?product=Loopback)

**D025 — Actionable notifications.** Open the affected item and offer useful, safe actions. Do not add an “Open app” button duplicating the notification's default action. Completion notices should reflect user value, not every internal job. [Notifications](https://developer.apple.com/design/human-interface-guidelines/notifications/)

**D026 — Quiet and private notifications.** Respect disabled notifications and Focus; keep private note titles or clipboard content out of previews where inappropriate. Essential status must also be discoverable inside the app. [Notifications](https://developer.apple.com/design/human-interface-guidelines/notifications/)

### Documents, undo and cross-app work

**D027 — Save without anxiety.** Preserve edits automatically where the document model supports it; still make name, format and destination explicit. Respect the user's ask-to-keep-changes setting. A silent failed save is worse than an explicit failure with recovery. [File management](https://developer.apple.com/design/human-interface-guidelines/file-management/)

**D028 — Edited means something.** Keep dirty indicators consistent with the actual autosave state. Do not imply saved content is safe remotely merely because a local save completed. The second distinction is a research recommendation for sync apps. [File management](https://developer.apple.com/design/human-interface-guidelines/file-management/)

**D029 — Use the system file panel.** Preserve familiar navigation, search and access behavior. Add relevant format/options as an accessory rather than rebuilding a poorer Finder. Custom library browsers can coexist with normal file import/export. [File management](https://developer.apple.com/design/human-interface-guidelines/file-management/)

**D030 — Preview unknown attachments.** Offer Quick Look for supported previews even if the app cannot edit that type; supply previews for your own custom format. Do not force an external app launch merely to identify a document. [File management](https://developer.apple.com/design/human-interface-guidelines/file-management/)

**D031 — Capture remains portable.** A capture utility should offer copy, save and drag into another app, with cloud sharing as an explicit route. Avoid making a web account the only exit for a local image. CleanShot documents these direct paths; this does not establish its measured speed. [CleanShot](https://cleanshot.com/)

**D032 — Export is usable outside the app.** Include meaningful names, attachments and documented formats. A backup blob is not equivalent to readable export. Choose formats around the content and round-trip needs; do not promise perfect fidelity across all Markdown implementations. [Bear Markdown notes](https://bear.app/faq/how-to-use-markdown-in-bear/)

### Accessibility and sustained use

**D033 — Test meaningful text enlargement.** Check long titles, lists, editor text and inspector values at larger sizes. Enlarged prose with clipped controls is incomplete. Use platform-supported mechanisms and explicit app controls where needed; do not assume every iOS Dynamic Type behavior exists on every Mac target. [Accessibility](https://developer.apple.com/design/human-interface-guidelines/accessibility/)

**D034 — Hit areas must not conflict.** A large invisible target is harmful if it overlaps its neighbor. Keep small utility controls distinguishable and provide keyboard alternatives. Touch adaptation should not inflate the permanent pointer layout indiscriminately. [Designing for macOS](https://developer.apple.com/design/human-interface-guidelines/designing-for-macos/)

**D035 — Motion is interruptible.** Immediate next input should win over a decorative transition. Do not queue a series of animations behind rapid typing or navigation. Reduce Motion must leave a clear final state and equivalent feedback. [Motion](https://developer.apple.com/design/human-interface-guidelines/motion/)

**D036 — Feedback has alternatives.** Pair a completion chime with visible state. Do not assume every Mac input device supports haptics. [Accessibility](https://developer.apple.com/design/human-interface-guidelines/accessibility/)

**D037 — Expose control meaning.** Icons need accessible names; stateful controls need accessible values. Hide purely decorative images from screen-reader navigation. [Accessibility](https://developer.apple.com/design/human-interface-guidelines/accessibility/)

**D038 — Preserve hierarchy while adapting.** Keep primary content early as panes collapse. Avoid unpredictable action reordering or blindly mirrored directional content. [Layout](https://developer.apple.com/design/human-interface-guidelines/layout/)

### Purchase and account surfaces

**D039 — Show the actual bill.** State total price, billing period and trial terms together; do not replace an annual bill with only a monthly equivalent. [Purchase guidance](https://developer.apple.com/design/human-interface-guidelines/apple-in-app-purchase/)

**D040 — Keep the purchase surface familiar.** Use the app's typography and hierarchy; retain Apple's confirmation sheet. A branded paywall must not imitate a system authorization prompt. [Purchase guidance](https://developer.apple.com/design/human-interface-guidelines/apple-in-app-purchase/)

**D041 — Explain purchase unavailability.** Restricted payments need a useful state, not a dead Buy button. Preserve free work and provide purchase help. [Purchase guidance](https://developer.apple.com/design/human-interface-guidelines/apple-in-app-purchase/)

**D042 — Make ownership recoverable.** Expose restore/redeem/help where applicable. Direct licenses need their own clear recovery route; StoreKit terminology alone does not solve direct-sale licensing. [Purchase guidance](https://developer.apple.com/design/human-interface-guidelines/apple-in-app-purchase/)

**D043 — Show subscription state.** Put renewal date and management near the plan. Cancellation should be recognizable and easy, not hidden behind support contact. [Purchase guidance](https://developer.apple.com/design/human-interface-guidelines/apple-in-app-purchase/)

**D044 — Require an account only for a reason.** Local utility work need not wait for registration. Explain what an account enables when sync or collaboration requires one. [Managing accounts](https://developer.apple.com/design/human-interface-guidelines/managing-accounts/)

**D045 — Name available authentication correctly.** Offer the method supported by this Mac and context; do not show Face ID branding on unsupported hardware or call an account password a device passcode. [Managing accounts](https://developer.apple.com/design/human-interface-guidelines/managing-accounts/)

**D046 — Distinguish deletion, sign-out and cancellation.** Explain data removal and completion timing. Account deletion may not stop store subscription billing; provide the relevant management route. Deactivation is not deletion. [Managing accounts](https://developer.apple.com/design/human-interface-guidelines/managing-accounts/)


## Reliability is part of the interface

A beautiful normal state earns little trust if work disappears during an interruption. The following are **derived acceptance scenarios**, not claims that every named app passes them. Test the smallest supported machine and OS, real user-sized data and a mixed-input setup; record latency, memory and failure recovery rather than inventing a universal “fast enough” number.

| Scenario | Expected behavior and what to test | Consequence of getting it wrong |
|---|---|---|
| Offline capture and editing | Save locally; distinguish saved from uploaded; reconnect without discarding or duplicating work | The user stops trusting the app as a place to think |
| Two devices edit one item | Preserve conflicting versions or merge with a clear model; expose recovery without requiring database surgery | Silent last-writer loss can destroy hours of work |
| Large first import | Show phases and counts; keep the UI responsive; allow safe interruption and resumption | A legitimate long import looks like a frozen app |
| Full disk, quota or read-only destination | Keep the unsaved content and identify the failing destination; offer a safe alternate save/export | “Saved” becomes a false promise |
| External drive disconnect or moved file | Preserve identity where possible; explain unavailable content and offer relocation | The app mistakes unavailable data for deleted data |
| Sleep/wake and network change | Revalidate connections and elapsed-time state; do not run stale work twice | Timers drift, jobs duplicate and auth loops appear |
| Time-zone/DST change | Distinguish a floating all-day task, a local recurring time and an absolute instant; test skipped/repeated hours | Deadlines or reminders move to the wrong day |
| Huge clipboard image/text | Bound history and decoding work; keep invoke/paste responsive; expose exclusion behavior | A tiny helper consumes the machine or silently omits expected clips |
| Secret or remote clipboard content | Respect concealed/transient markers; make retention, exclusions and clearing understandable | A convenience tool becomes a long-lived secret archive |
| Permission revoked after upgrade | Detect the missing capability and preserve work; give a precise repair path | Users reinstall or delete data to fix an unrelated permission |
| Fast user switching | Scope background behavior, credentials and notifications to the right user | Sensitive information appears in another session |
| Monitor removed, scaling changed | Restore an accessible window; retain useful pane sizes without offscreen dialogs | The app seems to have disappeared |
| Keyboard layout or IME changed | Preserve composition; allow shortcut remapping; test Return, Tab, Escape and dead keys | Ordinary input executes a command or destroys text |
| Screen reader or Voice Control | Expose role, name, value, selection and actions; complete full workflows | A visually complete feature is functionally absent |
| Increased contrast/reduced transparency | Retain state and hierarchy; do not rely on a subtle blur or tint | Controls vanish under the user's chosen accommodation |
| Low power or thermal pressure | Reduce discretionary indexing, effects and polling; preserve core interaction | A utility becomes a battery/fan problem |
| Interrupted update or migration | Preserve a recoverable copy; distinguish unsupported schema from corruption; test update paths | Routine maintenance becomes data loss |
| Extension or external service failure | Bound execution, cancel safely, retain local functions and explain the failing integration | One optional plugin breaks the whole app |
| Account expiry/sign-out/deletion | Explain what remains local, what stops syncing, and how to export or delete | Users discover lockout only after committing their data |
| Support diagnostics | Preview/redact sensitive content; make logs available without shell commands | Support requests unintentionally disclose private documents |

These scenarios combine source evidence and engineering consequences. Bear explicitly retains conflicting notes rather than dropping a version. Its sync help distinguishes offline and other sync failures, documents large initial-import delays, attachment/text limits, and warns that diagnostic logs may contain note text. That supports visible state, recoverable conflicts and careful diagnostics; it does not prove a failure rate. [Bear conflicts](https://bear.app/faq/how-bear-pro-handles-conflicted-notes/), [sync troubleshooting](https://bear.app/faq/sync-troubleshooting/)

Alfred disables clipboard history initially, offers retention and clearing controls, ignores selected password apps/concealed data, and lets users limit clip size. These are useful product choices, not a guarantee that unmarked secrets cannot be captured. Maccy's owning repository is a better technical reference than similarly named third-party sites; it also warns of impersonators. Use links from the owner when studying or recommending a security-sensitive utility. [Alfred clipboard](https://www.alfredapp.com/help/features/clipboard/), [Maccy source](https://github.com/p0deje/Maccy)

Apple's energy guide explains the user-visible result of thermal pressure—fans, battery loss and reduced responsiveness—and recommends reducing CPU/GPU/I/O work as conditions worsen. The guide is archival; its old code syntax is not a current implementation template. Use current API availability for the supported targets. A menu-bar helper should normally be idle when nothing needs doing; measure wakeups and background work as well as peak throughput. [Energy guide](https://developer.apple.com/library/archive/documentation/Performance/Conceptual/power_efficiency_guidelines_osx/RespondToThermalStateChanges.html)

For locales, test German-length labels, Arabic/Hebrew layout, mixed-script content, CJK composition, locale-specific decimal separators, 12/24-hour time, calendar conventions and non-ASCII filenames. RTL adaptation is semantic: mirror navigation and reading-order layout, not logos, photographs, digits within a number or an arrow meaning physical right. These are supported-target obligations, not a demand to translate into every language at launch. [Apple RTL guidance](https://developer.apple.com/design/human-interface-guidelines/right-to-left/)

## Assemble screens around the work

These are **design recommendations**, assembled from the component evidence rather than universal templates.

| Screen or task | Strong starting composition | Tempting mistake and test |
|---|---|---|
| Task or notes workspace | Sidebar for durable collections; list with clear selection; editor/detail; contextual toolbar and menu commands | Dashboard cards before actual work. Test quick capture, bulk edits, empty/filter states and two windows on the same item. |
| File utility | Source/destination or list/detail; visible path; operation status; preview/inspector when needed | Ambiguous active pane or silent destructive overwrite. Test keyboard-only copy/move, collisions, disconnection and rollback. |
| Quick capture | Small focused panel, immediate insertion point, explicit destination, predictable save/dismiss, restoration of prior focus | A modal setup wizard on each use. Test invocation while another app has a sheet, while fullscreen, and during IME composition. |
| Search/launcher | One query, stable result grammar, selected action, alternate actions, clear scope | Huge result cards and shifting ranking. Test rapid typing followed immediately by Return, with slow remote providers. |
| Rule/automation editor | Trigger → conditions → actions, readable summary, example input and safe preview; separate run history | Powerful rules whose effect cannot be predicted. Test a mistaken rule against a copy of real files, partial failures and duplicate triggers. |
| Settings | Stable grouped navigation, labels tied to controls, immediate reversible previews, explicit apply only where the transaction requires it | “Save all settings” on trivial toggles, or silently applying an irreversible operation. Test keyboard traversal and reopening. |
| Inspector | Name the selected object/scope; group related attributes; show mixed values for multiple selection | Changing the whole document because no selection looked identical to a selected row. Test no/single/multiple selection. |
| Import/export | Format, destination and meaningful options; preview mapping; counts/progress; result and recovery | A file picker followed by an unexplained spinner. Test malformed data, duplicates, unsupported fields and canceled runs. |
| Purchase/account | Clear entitlements, price/period, trial/expiry behavior, recovery, export/deletion and billing management | A high-converting-looking paywall that hides ownership or data consequences. Test failed payment, restore, offline use and expiry. |

OmniOutliner 6's manual gives a useful inspector example: selection properties and whole-document properties are distinct groups, with a preview identifying the target. It also documents a consequential default: with no selection, some style changes apply to the whole document. Study and communicate that scope; do not copy it invisibly. [OmniOutliner inspectors](https://support.omnigroup.com/documentation/omnioutliner/universal/6.4/en/inspectors/)

For implementation, Apple's WWDC25 AppKit transcript explains why static mockup metrics are insufficient: control heights changed, compact metrics remain available for dense layouts, and toolbar informational text should not receive a button-like glass background. Auto Layout and semantic grouping let controls evolve. This is **Tahoe-era technical guidance**; the current menu-icon policy supersedes its more expansive icon encouragement. [WWDC25 transcript](https://developer.apple.com/videos/play/wwdc2025/310/)

## Mac command and component reference

### Menu bar and command vocabulary

**D047 — Keep the menu map stable.** Retain standard menu ordering; disable unavailable main-menu commands instead of removing them. A changing map prevents learning. This rule differs from context menus. [Menu bar](https://developer.apple.com/design/human-interface-guidelines/the-menu-bar).

**D048 — Expose commands beyond the visible toolbar.** Include app-specific actions in menus, including advanced ones. Hiding commands behind gestures or an overflow-only interface obstructs discovery and keyboard access. [Menu bar](https://developer.apple.com/design/human-interface-guidelines/the-menu-bar).

**D049 — Provide Window even for one window.** Keep Minimize and Zoom accessible from the keyboard. “Only one window” does not remove window-management needs. [Menu bar](https://developer.apple.com/design/human-interface-guidelines/the-menu-bar).

**D050 — Use Option alternates as accelerators.** A hidden alternate must not be the sole route to a feature. Require at most one modifier to reveal it; avoid modifier puzzles. [Menu bar](https://developer.apple.com/design/human-interface-guidelines/the-menu-bar).

**D051 — Write action labels.** Prefer “Export…” over ambiguous nouns. An ellipsis means further input is required, not merely that another view opens. Use clear, short, title-case English labels. [Menus](https://developer.apple.com/design/human-interface-guidelines/menus).

**D052 — Keep related commands together.** Keep Paste and Match Style beside Paste even if rarely used; group with separators. Do not sort all actions by usage and destroy learned relationships. [Menus](https://developer.apple.com/design/human-interface-guidelines/menus).

**D053 — Distinguish state from action.** “Show Sidebar” changes to “Hide Sidebar”; a checkmark indicates an applied attribute. Ambiguous “Sidebar On” leaves readers guessing whether it describes state or action. [Menus](https://developer.apple.com/design/human-interface-guidelines/menus).

**D054 — Keep submenus shallow.** Prefer one level and short groups. Repeated parent concepts can justify a submenu; deep navigation taxes pointer precision and hides commands. [Menus](https://developer.apple.com/design/human-interface-guidelines/menus).

**D055 — Use menu icons deliberately.** Current Apple guidance says sparingly, with a clear metaphor, and consistent treatment within each group. Do not fill arbitrary icon slots. Guidance changed June 8, 2026. [Menus](https://developer.apple.com/design/human-interface-guidelines/menus).

**D056 — Preserve a readable text edge.** Nielsen’s December 2025 critique documents mixed icon/checkmark indentation in Tahoe menus. Treat aligned labels and distinct state marks as design checks; the critique is not a measured usability experiment. [Nielsen](https://blog.jim-nielsen.com/2025/icons-in-menus/).

**D057 — Use one metaphor consistently.** Prokopov documents different symbols for the same action and identical symbols for different actions in macOS 26.1/26.2. Reuse the same command symbol in menu and toolbar; tiny stroke differences cannot carry essential meaning. [Prokopov, January 2026](https://tonsky.me/blog/tahoe-icons/).

**D058 — Make opposites look related.** Paired rotate directions can benefit from diagrams; unrelated actions should not become mirror-image twins. Prokopov’s critique supports this distinction, not a blanket ban on icons. [Prokopov](https://tonsky.me/blog/tahoe-icons/).

**D059 — Use special marks for special meaning.** Gruber cites BBEdit’s trial stars: they identify paid commands, then disappear after licensing. A meaningful mark can teach entitlement; decorating every row erases that signal. [Gruber, March 2026](https://daringfireball.net/2026/03/what_to_do_about_those_menu_item_icons_in_macos_26_tahoe).

### Context menus and toolbars

**D060 — Make context menus contextual.** Offer a small set of likely actions on the current content. Do not use them as a landfill for every advanced feature. Keep equivalent commands in the main interface. [Context menus](https://developer.apple.com/design/human-interface-guidelines/context-menus).

**D061 — Hide irrelevant context actions.** Unlike main menus, omit unavailable contextual actions; Apple permits disabled Cut, Copy and Paste on Mac. Applying one availability rule everywhere loses either relevance or discoverability. [Context menus](https://developer.apple.com/design/human-interface-guidelines/context-menus).

**D062 — Avoid shortcut clutter in context menus.** Apple recommends displaying shortcuts in main menus. Context menus already shorten access; repeated shortcut glyphs widen a transient list without adding its primary value. [Context menus](https://developer.apple.com/design/human-interface-guidelines/context-menus).

**D063 — Keep toolbar commands in menus.** Users can hide or customize toolbars. Do not make a toolbar the only route to an action; the converse is unnecessary—every menu action need not get a button. [Toolbars](https://developer.apple.com/design/human-interface-guidelines/toolbars).

**D064 — Design the narrow toolbar.** Set sensible overflow priorities and preserve critical actions. Testing only the wide marketing screenshot produces disappearing controls in ordinary side-by-side work. [Toolbars](https://developer.apple.com/design/human-interface-guidelines/toolbars).

**D065 — Offer customization when workloads differ.** Long-lived, capable productivity apps benefit from user-selected frequent tools. Keep a useful default; a forced setup exercise is no substitute for designing it. [Toolbars](https://developer.apple.com/design/human-interface-guidelines/toolbars).

**D066 — Separate toolbar groups without fragmentation.** Group by task and importance; avoid many small islands. Separate text buttons from adjacent icons so they do not read as one combined control. [Toolbars](https://developer.apple.com/design/human-interface-guidelines/toolbars).

**D067 — Title the content, not the brand.** Differentiate multiple open windows with document or item names. Repeating the app name wastes the title’s orientation function; redundant titles can be omitted. [Toolbars](https://developer.apple.com/design/human-interface-guidelines/toolbars).

### Windows and sheets

**D068 — Use system window frames and controls.** Homemade traffic lights must recreate behavior as well as shape. Standard frames carry learned interactions and evolving OS treatment. [Windows](https://developer.apple.com/design/human-interface-guidelines/windows).

**D069 — Distinguish key, main and inactive states.** A floating panel can receive input while the document remains main. Custom chrome must reflect these states; identical active/inactive styling hides where keystrokes go. [Windows](https://developer.apple.com/design/human-interface-guidelines/windows).

**D070 — Offer another window when comparison helps.** Let users open a task or item separately without forcing every navigation to spawn a window. Mail’s compose window is Apple’s example of preserving context. [Windows](https://developer.apple.com/design/human-interface-guidelines/windows).

**D071 — Adapt while resizing.** Main content must remain usable across real multitasking sizes. A fixed presentation that merely crops is insufficient; choose a sensible minimum rather than assuming fullscreen. [Windows](https://developer.apple.com/design/human-interface-guidelines/windows).

**D072 — Do not strand essential actions at the bottom.** Mac users can move a window partly below the display. Bottom status summaries are suitable; the sole completion control is not. [Windows](https://developer.apple.com/design/human-interface-guidelines/windows).

**D073 — Scope sheets to their parent.** Permit work in other app windows while a sheet is open. Blocking the entire app for one document’s choice defeats Mac multitasking. [Sheets](https://developer.apple.com/design/human-interface-guidelines/sheets).

**D074 — Avoid sheet towers.** Dismissing a sheet should return to its parent, not reveal another sheet. Move long, self-contained work into its own window; use a panel for repeated adjustments with visible results. [Sheets](https://developer.apple.com/design/human-interface-guidelines/sheets).

**D075 — Give sheets a real exit.** Pair Done with Cancel or an appropriate Back route. Size for actual content; permit resizing when it helps inspect a large payload. A clipped, compulsory workflow is not polish. [Sheets](https://developer.apple.com/design/human-interface-guidelines/sheets).

### Keyboard and text

**D076 — Preserve established shortcuts.** Do not steal Command-Z or Command-Q for product features. App-specific shortcuts need a reason; a standard shortcut can be repurposed only when its usual operation is irrelevant. [Keyboards](https://developer.apple.com/design/human-interface-guidelines/keyboards).

**D077 — Test Full Keyboard Access.** “Has shortcuts” is weaker than “every control can be reached and operated.” Enable the system feature and complete the task without a pointer. [Keyboards](https://developer.apple.com/design/human-interface-guidelines/keyboards).

**D078 — Let the system present shortcuts.** Preserve modifier order Control–Option–Shift–Command, keyboard-layout localization and relevant RTL mirroring. Handwritten shortcut strings easily diverge from the actual binding. [Keyboards](https://developer.apple.com/design/human-interface-guidelines/keyboards).

**D079 — Keep word and line editing.** Support Option-arrow word movement, Command-arrow line boundaries, Shift extension and Option-Delete. A custom editor that handles only letters and Backspace breaks routine editing. Apps may have specialized modes. [Apple shortcuts](https://support.apple.com/en-us/102650).

**D080 — Separate scrolling from caret movement.** Home/End scroll the document; Command-Up/Down move the insertion point. Blindly importing another platform’s behavior can unexpectedly alter selection. [Apple shortcuts](https://support.apple.com/en-us/102650).

**D081 — Preserve text-system conveniences.** Control-A/E, forward delete, spelling, dictionary lookup and Paste and Match Style matter to practiced users. Validate relevant commands in custom editors; not every document type supports formatting. [Apple shortcuts](https://support.apple.com/en-us/102650).

**D082 — Do not conflate Close and Quit.** Command-W closes a window; Command-Q quits. Keep Hide and Minimize distinct too. A cross-platform event handler must not collapse these operations. [Apple shortcuts](https://support.apple.com/en-us/102650).

**D083 — Use a field for short input, a view for editing.** Single-line fields are poor long-form editors. Preserve full text-view behaviors when notes, descriptions or documents become substantial. [Text views](https://developer.apple.com/design/human-interface-guidelines/text-views).

**D084 — Let users copy useful output.** Errors, identifiers and addresses should be selectable where useful. Treating everything outside an input as decoration forces retyping and makes support harder. [Text views](https://developer.apple.com/design/human-interface-guidelines/text-views).

**D085 — Keep a label after typing.** Placeholders disappear. Use persistent labels where a completed form would otherwise lose meaning; do not use placeholders as the sole explanation for ambiguous fields. [Text fields](https://developer.apple.com/design/human-interface-guidelines/text-fields).

**D086 — Align fields and their labels.** Use consistent widths and spacing within related groups; size fields to expected input. Random widths and excessive label gaps make field ownership hard to scan. [Text fields](https://developer.apple.com/design/human-interface-guidelines/text-fields).

**D087 — Make Tab order logical.** Traverse fields in reading/task order, including Shift-Tab backwards. A visually reordered layout with stale focus order feels broken even when every field works. [Text fields](https://developer.apple.com/design/human-interface-guidelines/text-fields).

**D088 — Validate at a useful moment.** Do not call a half-entered email invalid on every keystroke. Choose timing by field, preserve the entry, and use locale-aware numeric formatting. [Text fields](https://developer.apple.com/design/human-interface-guidelines/text-fields).

### Lists, tables, outlines and scrolling

**D089 — Make sorting reversible and visible.** Clicking a sorted column again reverses its direction. Avoid a cosmetic header that looks interactive but does nothing when sorting is useful. [Lists and tables](https://developer.apple.com/design/human-interface-guidelines/lists-and-tables).

**D090 — Allow column resizing.** Names and other data do not have fixed widths. Let users reveal detail and redistribute space; permanent truncation is not a density strategy. [Lists and tables](https://developer.apple.com/design/human-interface-guidelines/lists-and-tables).

**D091 — Use row structure to aid scanning.** Succinct labels, descriptive column headings and optional alternating backgrounds help wide tables. Overlarge prose rows obscure comparisons; use detail views when needed. [Lists and tables](https://developer.apple.com/design/human-interface-guidelines/lists-and-tables).

**D092 — Highlight the selected navigation row persistently.** It explains which detail is displayed. Momentary feedback suits a choice that receives a checkmark; navigation and toggling need different feedback. [Lists and tables](https://developer.apple.com/design/human-interface-guidelines/lists-and-tables).

**D093 — Represent hierarchy in the first column.** Use outline disclosure, not ornamental indentation in an ordinary flat table. Other columns describe the same item without creating competing hierarchies. [Outline views](https://developer.apple.com/design/human-interface-guidelines/outline-views).

**D094 — Remember expansion state.** Reopening the view should not make users retraverse folders they expanded. Support efficient nested expansion; Finder’s Option-disclosure expands descendants. [Outline views](https://developer.apple.com/design/human-interface-guidelines/outline-views).

**D095 — Sort within hierarchy levels.** Sorting a tree must retain containment. Do not flatten children away from their parents merely to produce a global alphabetical list. [Outline views](https://developer.apple.com/design/human-interface-guidelines/outline-views).

**D096 — Keep distinguishing text visible.** Middle truncation can preserve filename beginnings and extensions. Choose deliberately; blindly clipping every right edge hides meaningful differences. [Outline views](https://developer.apple.com/design/human-interface-guidelines/outline-views).

**D097 — Preserve system scrolling.** Respect gestures, keys and indicator behavior. Avoid same-axis nested scroll views; they leave users unsure which region will move. [Scroll views](https://developer.apple.com/design/human-interface-guidelines/scroll-views).

**D098 — Signal hidden content.** Indicators may be hidden by system preference; partial content can reveal more below. For page scrolling, slight overlap preserves context instead of making users hunt for their previous line. [Scroll views](https://developer.apple.com/design/human-interface-guidelines/scroll-views).

**D099 — Keep scrolled content distinct from controls.** Use appropriate system scroll-edge treatment, not decorative gradients everywhere. In split views, keep edge heights aligned; test contrast over varied underlying content. [Scroll views](https://developer.apple.com/design/human-interface-guidelines/scroll-views).

### Dragging and undo

**D100 — Support dragging plus alternatives.** Accept useful content across the app, but offer commands for people who cannot drag. Multi-item operations should not require repeating the same drag for each item. [Drag and drop](https://developer.apple.com/design/human-interface-guidelines/drag-and-drop).

**D101 — Show valid destinations precisely.** Highlight the actual target or insertion point only while hovered; show rejection on failed drops. Silent disappearance falsely signals success. [Drag and drop](https://developer.apple.com/design/human-interface-guidelines/drag-and-drop).

**D102 — Check modifiers at drop time.** Option can change an internal move into a copy; users may release it mid-drag. Preview and final operation must agree. [Drag and drop](https://developer.apple.com/design/human-interface-guidelines/drag-and-drop).

**D103 — Allow background dragging.** A selected item in an inactive window should drag without activating it first. Where possible, dragging an unselected background item should preserve that window’s existing selection. [Drag and drop](https://developer.apple.com/design/human-interface-guidelines/drag-and-drop).

**D104 — Support file interchange, not only internal rearranging.** Where useful, dragging to Finder should produce a reopenable file; Calendar’s `.ics` export illustrates this. Offer rich and fallback representations for other destinations. [Drag and drop](https://developer.apple.com/design/human-interface-guidelines/drag-and-drop).

**D105 — Make undo descriptive.** “Undo Rename” teaches the pending result. Preserve multiple undo steps, and group a continuous adjustment sensibly instead of requiring hundreds of reversals. [Undo and redo](https://developer.apple.com/design/human-interface-guidelines/undo-and-redo).

**D106 — Show the undone result.** Reveal affected content when it is offscreen. Invisible success encourages repeated undo and unintended changes. Preserve standard Edit-menu commands and Command-Z/Shift-Command-Z. [Undo and redo](https://developer.apple.com/design/human-interface-guidelines/undo-and-redo).

### Settings, alerts, search and capture

**D107 — Keep settings in the app menu.** Support Command-comma. Frequent per-view choices belong near their content; a gear in prime toolbar space should not substitute for standard Settings access. [Settings](https://developer.apple.com/design/human-interface-guidelines/settings).

**D108 — Make settings navigation stable.** Keep the current pane visibly selected, title it usefully and restore the last pane. Apple describes a noncustomizable toolbar; huge settings systems can warrant other navigation rather than forced tiny tabs. [Settings](https://developer.apple.com/design/human-interface-guidelines/settings).

**D109 — Respect system preferences.** Do not independently reinvent global scrolling or accessibility controls. Good defaults reduce setup; product-specific settings should solve a real variation in work. [Settings](https://developer.apple.com/design/human-interface-guidelines/settings).

**D110 — Use the right choice control.** A pop-up button chooses one state and displays it; a pull-down offers commands. Confusing them hides the current value or makes an action look like a setting. [Pop-up buttons](https://developer.apple.com/design/human-interface-guidelines/pop-up-buttons).

**D111 — Keep segments coherent.** Use closely related choices with consistent sizing and treatment. Do not mix assorted icon and text buttons into a pseudo-tab row; use an actual tab view for main-content switching. [Segmented controls](https://developer.apple.com/design/human-interface-guidelines/segmented-controls).

**D112 — Reserve alerts for interruption-worthy decisions.** Avoid modal success notices, startup networking complaints and confirmation of ordinary undoable deletions. Inline status preserves work; uncommon irreversible actions merit confirmation. [Alerts](https://developer.apple.com/design/human-interface-guidelines/alerts).

**D113 — Name the result on alert buttons.** “Delete” or “Convert” is clearer than “OK.” Offer Cancel and keyboard cancellation. Do not automatically make Cancel the default; Apple recommends no default when deliberate reading is essential. [Alerts](https://developer.apple.com/design/human-interface-guidelines/alerts).

**D114 — Distinguish intended deletion from surprise loss.** Apple’s alert guidance does not require red styling for every deliberate destructive command. Reserve warning treatment for unexpected risk; repeated caution icons lose force. [Alerts](https://developer.apple.com/design/human-interface-guidelines/alerts).

**D115 — Make search scope legible.** Put cross-column search in the toolbar; filtering a sidebar can belong above it. Clarify scope with a placeholder and visible filters. Do not silently search only an unexpected subset. [Search fields](https://developer.apple.com/design/human-interface-guidelines/search-fields).

**D116 — Help users refine while typing.** Prompt results and useful suggestions shorten finding. Use tokens for meaningful structured filters, not decoration; suggestions teach available tokens. Preserve sensible behavior as the window narrows. [Search fields](https://developer.apple.com/design/human-interface-guidelines/search-fields).

**D117 — Capture without losing the original task.** Things’ Quick Entry can save a task from another app and reuse main-window shortcuts. This is a product pattern, not a requirement for every utility. [Things support](https://culturedcode.com/things/support/articles/2249437/).

**D118 — Make global shortcuts configurable.** Things documents conflict avoidance. Its default Control-Space overlaps input-source switching; multilingual users need an escape from that conflict rather than instructions to abandon their system shortcut. [Things support](https://culturedcode.com/things/support/articles/2249437/), [Apple shortcuts](https://support.apple.com/en-us/102650).

**D119 — Specify capture dismissal semantics.** Things documents Escape saving collapsed main-window edits but discarding Quick Entry input; Command-Return saves the latter. This difference deserves explicit product testing, not blind imitation. [Things support](https://culturedcode.com/things/support/articles/2249437/).

**D120 — Keep menu-bar utilities recoverable.** Do not depend solely on a status item that may be hidden. Offer another route to the app; simple actions fit a menu, while complex functionality can justify a popover. [Menu bar](https://developer.apple.com/design/human-interface-guidelines/the-menu-bar).


### Shipped regression evidence: compact case study

Things 3.23–3.24.2 release notes (August–November 2026) expose what polish costs: correct selection after collapsing an edited task; usable final blank text lines; larger-font selection highlights; narrow-window toolbar sizing; commands remaining available in other windows while one shows a dialog; correct text deletion; and Tab/Escape behavior with international input methods. These are developer-reported fixes, not independently reproduced results. Derived test: repeat every important operation while editing, filtered, resized, backgrounded and using an IME—not only in a pristine list. The changelog cannot establish failure frequency or prove all variants are fixed. [Things Mac release notes](https://culturedcode.com/things/support/articles/1100684/).

### Additional details: selection, focus, input and files

**D121 — Command-click changes membership.** Add nonadjacent items, and remove an already-selected item without clearing the rest. A multi-select list that requires one-at-a-time checkboxes discards a learned Mac technique. [Apple selection guide](https://support.apple.com/guide/mac-help/select-items-mchlp1378/mac).

**D122 — Shift-click selects a range.** In an ordered list, retain an anchor and include intervening items. Do not substitute Command-style toggling. Geometric icon layouts may need different selection models; test them separately. [Apple selection guide](https://support.apple.com/guide/mac-help/select-items-mchlp1378/mac).

**D123 — Text selection has granularity.** Double-click selects a word; triple-click selects a paragraph in standard Mac text. Preserve these in custom note editors; a visual highlight alone does not implement selection behavior. [Apple selection guide](https://support.apple.com/guide/mac-help/select-items-mchlp1378/mac).

**D124 — Click-through is control-specific.** AppKit views normally activate an inactive window without acting; many buttons and sliders accept the first click. Do not impose “everything activates” or “everything requires two clicks.” Check accidental-action risks explicitly. [NSView acceptsFirstMouse](https://developer.apple.com/documentation/appkit/nsview/acceptsfirstmouse(for:)).

**D125 — Honor the double-click interval.** Use system recognition rather than a hardcoded fast timeout. Apple exposes this user setting through `NSEvent.doubleClickInterval`; custom detection must not exclude people who deliberately slow it. [NSEvent](https://developer.apple.com/documentation/appkit/nsevent/doubleclickinterval).

**D126 — Double-click extends the first click.** Selection then opening is coherent; unrelated first- and second-click actions force delay or cause side effects. Keep another route. This is a useful historical principle, stated in Apple’s 1986 draft—not a modern API requirement. [1986 HIG draft, printed pp. 19–20](https://daringfireball.net/thetalkshow/428/HumanInterfaceGuidelines-1986.pdf).

**D127 — Commands target the focused context.** Copy should operate on the editor or selected objects that currently own focus, not a stale global selection. Apple’s Shortcuts example connects a SwiftUI editor to AppKit menu commands through the responder chain. [WWDC22 transcript](https://developer.apple.com/videos/play/wwdc2022/10075/).

**D128 — Restore usable focus, not merely a focus flag.** After transient UI closes, return input to an eligible control. `makeFirstResponder` can fail when the old responder refuses resignation; even success can mean the window received focus because the requested view refused. Test actual typing. [NSWindow](https://developer.apple.com/documentation/appkit/nswindow/makefirstresponder(_:)).

**D129 — Reopening a running app should do something useful.** Handle Dock/Finder reactivation when all main windows are closed. Default AppKit document behavior can create an untitled document; an app with one workspace may instead reopen it. Minimized windows count as visible for this callback. [Reopen handling](https://developer.apple.com/documentation/appkit/nsapplicationdelegate/applicationshouldhandlereopen(_:hasvisiblewindows:)).

**D130 — Composition is not committed text.** Preserve marked text while an input method constructs a character or phrase. Do not submit a form or replace its contents indiscriminately on each raw key event. Use `NSTextView` or correctly implement `NSTextInputClient`. [Text-input protocol](https://developer.apple.com/documentation/appkit/nstextinputclient), [Text editing guide](https://developer.apple.com/library/archive/documentation/TextFonts/Conceptual/CocoaTextArchitecture/TextEditing/TextEditing.html).

**D131 — Candidate UI needs real text geometry.** Custom editors must provide character rectangles, selection and marked ranges to the input system. After scrolling or moving windows, test that candidate UI still follows the insertion point. This test is derived from the protocol’s coordinate contract. [Text-input protocol](https://developer.apple.com/documentation/appkit/nstextinputclient).

**D132 — Return depends on the editor.** Standard field editing commits; a normal text editor inserts a newline. Custom “Return saves” behavior must preserve composition and a discoverable way to enter multiline content. Do not infer identical semantics from identical keys. [Text editing guide](https://developer.apple.com/library/archive/documentation/TextFonts/Conceptual/CocoaTextArchitecture/TextEditing/TextEditing.html).

**D133 — Paste the richest supported representation.** A copied object can contain rich text, plain text, images and a native type. Publish useful fallbacks; consume the best valid type. Copying only an internal identifier makes cross-app paste useless. [Pasteboard concepts, archived 2010](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/PasteboardGuide106/Articles/pbConcepts.html).

**D134 — Generate expensive paste formats on demand.** Promised data avoids preparing every large image encoding on Copy. Test paste after the source document closes; deferred representations need a valid producer or retained data. [Pasteboard concepts](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/PasteboardGuide106/Articles/pbConcepts.html).

**D135 — Do not overwrite the clipboard for unrelated UI.** Find has a separate system pasteboard; dragging and Services also have pasteboard roles. Use the proper channel instead of stealing the user’s ordinary copied content for an internal transfer. [Pasteboard concepts](https://developer.apple.com/library/archive/documentation/Cocoa/Conceptual/PasteboardGuide106/Articles/pbConcepts.html).

**D136 — Remember file permission, not just its path.** A sandboxed app reopening a user-chosen folder needs appropriate security-scoped bookmarks. Handle stale bookmarks by recreating them; request access again when necessary rather than falsely reporting an empty folder. [Sandbox file access](https://developer.apple.com/documentation/security/accessing-files-from-the-macos-app-sandbox).

**D137 — Distinguish permission failures.** A valid sandbox grant does not override POSIX permissions, access-control lists or other macOS restrictions. Explain the failed operation accurately; repeatedly showing the same picker may not fix it. [Sandbox file access](https://developer.apple.com/documentation/security/accessing-files-from-the-macos-app-sandbox).

**D138 — Balance security-scoped resource access.** Release access after use; leaking grants can eventually prevent opening new user files until relaunch. A file utility that works initially but fails after sustained use is not reliable. [Security-scoped URL access](https://developer.apple.com/documentation/foundation/nsurl/startaccessingsecurityscopedresource()).

**D139 — Mixed checkboxes mean mixed values.** When selected items or subordinate options disagree, show the dash state rather than falsely choosing on or off. Do not use an ordinary checkbox to claim a uniform value that does not exist. [Toggles](https://developer.apple.com/design/human-interface-guidelines/toggles).

**D140 — Radio groups mean one choice.** Use checkboxes for multiple independent options. A lone radio button is a poor on/off control; many exclusive choices may fit a pop-up better than a wall of circles. [Toggles](https://developer.apple.com/design/human-interface-guidelines/toggles).

**D141 — Choose switch weight deliberately.** A switch emphasizes a substantial setting or group; compact checkbox hierarchies communicate dependencies. Do not mechanically replace every Mac checkbox with a mobile-looking switch. Apple also supports mini switches in grouped forms. [Toggles](https://developer.apple.com/design/human-interface-guidelines/toggles).

**D142 — Align checkbox groups precisely.** Align a group’s introductory label baseline with its first checkbox; align subordinate boxes and indent dependencies. This communicates structure without extra panels or explanatory prose. [Toggles](https://developer.apple.com/design/human-interface-guidelines/toggles).

**D143 — A dismissed save panel is not a saved file.** Check its OK/Cancel result before writing. Completion can run while the panel remains onscreen; remove it before presenting another alert. Preserve the document after cancellation. [NSSavePanel](https://developer.apple.com/documentation/appkit/nssavepanel/beginsheetmodal(for:completionhandler:)).

**D144 — Commit the active edit before reporting success.** A field’s displayed string may not yet be in the model. `commitEditing()` can fail validation; do not close and claim Save succeeded anyway. [NSViewController](https://developer.apple.com/documentation/appkit/nsviewcontroller/commitediting()).

**D145 — Inspector and Info windows differ.** An inspector follows selection; an Info window stays attached to the original object. Switching objects must not silently change the subject of a supposedly pinned Info window. [Panels](https://developer.apple.com/design/human-interface-guidelines/panels).

**D146 — Restore the task, not only the rectangle.** Preserve selected item, tabs and in-progress UI across normal relaunches. Restore each window independently. Apple’s sample distinguishes normal quit from force quit, which discards saved state. [AppKit restoration sample](https://developer.apple.com/documentation/appkit/restoring-your-app-s-state-with-appkit).

**D147 — Do not block shutdown for trivial UI.** Sheets that need no intervention should permit termination; unsaved data still needs protection. Apple’s 2026 session points to `preventsApplicationTerminationWhenModal`. [WWDC26 transcript, 9:08](https://developer.apple.com/videos/play/wwdc2026/289/).

**D148 — Keep Tab order correct after changes.** Dynamic panes can add or remove focusable controls. Use AppKit’s key-view-loop recalculation or maintain it explicitly; an initially correct loop is insufficient. [WWDC26 transcript, 5:51](https://developer.apple.com/videos/play/wwdc2026/289/).

**D149 — Menu-bar popovers need a focus lifecycle.** Custom status-item UI must cooperate when keyboard focus enters and leaves. AppKit’s expanded-interface session coordinates display and dismissal; test both keyboard and pointer entry. [WWDC26 transcript, 5:51](https://developer.apple.com/videos/play/wwdc2026/289/).

**D150 — Do not rebuild selection from raw mouse tracking.** Current AppKit offers selection delegates and, in macOS 27, `NSTextSelectionManager` for custom text views. Prefer these behaviors where applicable; older targets need their supported path. [WWDC26 transcript, 2:25–4:26](https://developer.apple.com/videos/play/wwdc2026/289/).

### Filename edge case and source-method additions

For file utilities, test canonically equivalent Unicode filenames, case-only differences, case-sensitive volumes and remote shares. Preserve actual URLs and avoid inventing identity by lowercasing names. Apple’s retired APFS FAQ explicitly distinguishes preserving name representation from comparing normalization-insensitively; do not claim all Mac filenames are physically converted to NFD. Its 2018 filesystem/version detail is historical, while the current Foundation guide still recommends high-level APIs. This is a derived compatibility test matrix, not a claim that every mounted volume behaves like APFS. [APFS FAQ](https://developer.apple.com/library/archive/documentation/FileManagement/Conceptual/APFS_Guide/FAQ/FAQ.html), [current Foundation guide](https://developer.apple.com/documentation/foundation/about-apple-file-system).

Read direct primary long-form material: Apple’s *Human Interface Guidelines*, second beta draft, July 22, 1986, especially printed pp. 18–20, 54–56 and 79–80; and transcripts of WWDC22 *Use SwiftUI with AppKit* and WWDC26 *Modernize your AppKit app*. The historical draft helps explain interaction reasoning, not current metrics or visual styling. It also contains obsolete advice, including old button ordering; current guidance takes precedence. Transcripts were read, not watched as motion demonstrations.

### Help, precision and finishing details

**D151 — Tooltips explain the action.** Describe what an icon does, not its shape; change the text when state changes. Avoid repeating a clear label or hiding essential instructions only in hover text. [Offering help](https://developer.apple.com/design/human-interface-guidelines/offering-help/)

**D152 — Keep tooltip copy short.** Apple suggests roughly 60–75 characters, allowing for localization. A paragraph usually signals a control or help-design problem; use contextual help for multi-step work. [Offering help](https://developer.apple.com/design/human-interface-guidelines/offering-help/)

**D153 — Help opens the relevant topic.** A Rules pane's help should explain rules, not send users to a marketing homepage. Use the recognizable system help button where appropriate. [Buttons](https://developer.apple.com/design/human-interface-guidelines/buttons/)

**D154 — Button height follows content.** Use standard sizes for ordinary labels and flexible height for genuinely tall content. Do not stretch every button to a mobile-sized slab or clip localized labels into a fixed custom height. [Buttons](https://developer.apple.com/design/human-interface-guidelines/buttons/)

**D155 — Spring loading extends a drag.** Where useful, let supported controls activate during a held drag so users can reach a destination without dropping. Keep a conventional command route for hardware without force interaction. [Buttons](https://developer.apple.com/design/human-interface-guidelines/buttons/)

**D156 — Sliders show their result live.** Preview safe changes while dragging. For expensive/destructive work, explain a separate apply step instead of implying the preview committed. [Sliders](https://developer.apple.com/design/human-interface-guidelines/sliders/)

**D157 — Sliders communicate their scale.** Label useful endpoints/ticks, especially nonlinear ranges; show a precise current value when it matters. Use circular controls for cyclic values, not merely visual novelty. [Sliders](https://developer.apple.com/design/human-interface-guidelines/sliders/)

**D158 — Sidebar size respects the user.** Standard sidebar row, text and glyph sizes respond to the system's sidebar size preference. A custom sidebar should not freeze the designer's preferred density while the rest of the Mac adapts. [Sidebars](https://developer.apple.com/design/human-interface-guidelines/sidebars/)

**D159 — Tabs contain self-contained peers.** Controls in one pane should not secretly alter another. Use short descriptive labels; excessive tabs need another navigation structure, not microscopic titles. [Tab views](https://developer.apple.com/design/human-interface-guidelines/tab-views/)

**D160 — Gestures retain system meaning.** Do not steal Mission Control or workspace gestures for app features. Provide equivalent routes for mouse and keyboard users; a trackpad gesture cannot be the only way to navigate. [Pointing devices](https://developer.apple.com/design/human-interface-guidelines/pointing-devices/)

**D161 — Touch reveals hidden controls without losing selection.** Current Mac guidance distinguishes reveal from activation. If an action acts on selected items, revealing it must preserve those items. Retain context-menu access; do not expose every hover-only control permanently. [Pointing devices](https://developer.apple.com/design/human-interface-guidelines/pointing-devices/)

**D162 — Precision feedback earns its pixels.** During resize or measured editing, show useful dimensions/coordinates. Avoid decorative cursor changes or instructional paragraphs attached to the pointer; feedback should clarify the operation. [Pointing devices](https://developer.apple.com/design/human-interface-guidelines/pointing-devices/)

## Strong exemplars, with limits

| App | What to study | Cost, weakness or scope limit | Meaning of great supported |
| --- | --- | --- | --- |
| **Things 3** | Clear distinction between start date and deadline; headings within projects; readable task cards; fast Type Travel search on Mac. MacStories praised hierarchy, typography, restrained color and enjoyment. | The 2017 review spans platforms; Magic Plus and swipe examples are iOS, not Mac conventions. Reviewer found some bulk entry slower than alternatives. Current support confirms no collaborative lists or browser client. | Reviewer-observed emotional appeal and personal-task value; no public profit proof. |
| **Alfred** | One keyboard entry point scales from search to clipboard history, snippets, file actions and workflows. Community extensions let advanced users extend a small interaction vocabulary. | Workflow creation and third-party integrations add configuration and maintenance work. This is an inferred tradeoff, not a measured usability finding. | Practical capability; independent team and maintained commercial offer. |
| **Keyboard Maestro** | Triggers, conditions and actions compose reusable automation; macro wizard helps entry; dedicated security pane shows permission status. | Breadth creates learning and debugging work. Automating other interfaces inherits their changes. | Rational time-saving value; concrete long-lived paid-upgrade model. |
| **Hazel** | Folder rules automate naming, tagging, moving and archiving; uses Spotlight, Shortcuts, AppleScript and Automator. | Rules can act on files without a foreground screen: preview, audit and recovery deserve higher priority than visual novelty. Inference from automation scope. | Focused value and platform integration; commercial success not quantified. |
| **Maccy** | Search clipboard history by typing, keep records locally, honor password-manager clipboard removal; a small utility stays small. | Local clipboard history still contains sensitive data; “local” is not a blanket security guarantee. Site’s performance adjectives are developer claims, not measurements. | Focus, keyboard workflow and inspectable MIT source. |
| **Rectangle** | Repeat a shortcut to cycle sizes; snap zones support portrait displays; offer Spectacle’s old shortcuts at first launch. | OS window management competes with the core task; paid differentiation needs more than familiar basic tiling. Inference. | Low-friction migration and clear free/Pro separation. |
| **Little Snitch** | Explain outgoing network activity; offer hierarchy, search and traffic views; Silent Mode postpones interruptions while learning connections. | Blocking prompts impose decisions users may not understand; silent allowance trades prevention for fewer interruptions. Neither mode is universally best. | Deep utility, inspectability and explicit control. |
| **Default Folder X** | Improve repeated Open/Save work: recent/favorite folders, larger filename field, choose an already-open Finder folder, keyboard search. | Cross-app integration creates an OS-compatibility maintenance obligation. Exact mechanisms not inspected here. | Small friction removed across many daily tasks. |
| **DEVONthink 4** | Document collection, tags, smart groups, cross-links, automation, automatic versions and recovery. | A knowledge repository has onboarding, migration and backup obligations; complexity may exceed a small notes utility’s needs. AI is optional product direction, not evidence every organizer needs AI. | Serious information-management capability; no profitability claim. |
| **Hookmark** | “Copy Link” across files, mail and tasks; return directly to context instead of searching again; free basic tier and 30-day Pro trial without card. | Value depends on supported app integrations and durable links. Broad marketing wording is not proof every item in every app works. | Cross-app continuity and reduced navigation. |
| **BBEdit** — adjacent text/professional-tool comparison | Full 30-day trial falls back to a usable free mode, with no nag screens; pay to restore advanced features. | Professional editing complexity is not a template for a tiny utility. Free mode and paid capabilities must be explained clearly. | Respectful purchase transition and durable editing utility. |
| **Nova** — adjacent developer-tool comparison | Native Mac workflow, integrated editor/terminal/transfers; 2020 license retained the purchased version while charging optionally for another year of updates. | Not Mac App Store distributed at announcement because arbitrary executables/extensions conflict with sandboxing. 2020 price is historical, not today’s quote. | Coherent workflow and an alternative to subscription lockout. |

Sources: [Things review, Ryan Christoffel, launch-era 2017](https://www.macstories.net/reviews/things-3-beauty-and-delight-in-a-task-manager/); [Things current purchasing/support](https://culturedcode.com/things/support/articles/2803552/); [Alfred Powerpack](https://www.alfredapp.com/powerpack/); [Keyboard Maestro 11](https://www.keyboardmaestro.com/main/); [Hazel](https://www.noodlesoft.com/); [Maccy](https://maccy.app/); [Rectangle](https://rectangleapp.com/); [Little Snitch](https://www.obdev.at/products/littlesnitch/index.html); [Default Folder X](https://www.stclairsoft.com/DefaultFolderX/); [DEVONthink](https://www.devontechnologies.com/apps/devonthink); [Hookmark](https://hookproductivity.com/); [BBEdit](https://www.barebones.com/products/bbedit/); [Nova launch, October 2020](https://blog.panic.com/nova-is-here/); [Nova distribution rationale, July 2019](https://blog.panic.com/nova-our-next-big-thing/).

These are exemplars for particular qualities, not an audited ranking. Revenue, profit and retention are generally private. Longevity and active sales show continuation, not financial health.

## Pricing models coexist

**One-time, per platform:** Things offers a Mac trial for 15 days, sells through Apple’s stores, includes cloud sync and charges separately by platform. Buyers should see the full multi-device cost. Store purchases constrain direct refund handling and discount flexibility; support routes refunds to Apple. This proves such a model exists, not that a new unknown app can fund indefinite hosting from the same terms. [Current Things support](https://culturedcode.com/things/support/articles/2803552/).

**Paid major upgrades:** Keyboard Maestro 11 is listed at US$36 plus tax; upgrades US$25, with recent purchases grandfathered. Version 11 remains usable indefinitely. A concrete alternative to recurring access fees; continued compatibility of old versions is a separate promise. [Keyboard Maestro](https://www.keyboardmaestro.com/main/).

**Lifetime upgrades:** Alfred lists £34 for its v5 license and £59 for Mega Supporter with free lifetime upgrades, with a stated v6 upgrade offer. These are observed offers, not a recommendation to promise unlimited future labor. [Alfred](https://www.alfredapp.com/powerpack/).

**Optional update renewal:** Nova’s 2020 launch offered US$99 ownership, one year of updates, then optional US$49 update years without a late-renewal penalty. This separates continued use from continued maintenance. Price and release date must remain attached. [Panic](https://blog.panic.com/nova-is-here/).

**Subscriptions plus a perpetual option:** Ulysses’ 2017 rationale describes new-user dependence and release-driven sales spikes; developers wanted recurring funding for continuous improvements. That is the maker’s economic account, not a universal law. The current support page now offers monthly/yearly subscriptions, a perpetual license, educational terms, Setapp and business volume licensing. Regular subscriptions have a seven-day trial; trial enrollment requires subscription authorization. Do not describe Ulysses as currently subscription-only. [2017 rationale](https://blog.ulysses.app/why-were-switching-ulysses-to-subscription/), [current options](https://help.ulysses.app/subscription-options-).

**Free core with paid power:** BBEdit leaves a useful editor after the trial; Rectangle separates a free open-source app from Pro; Hookmark offers basic linking without a card. This can let users prove value before paying. None of these pages supplies controlled conversion data; do not claim a numerical lift. [BBEdit](https://www.barebones.com/products/bbedit/), [Rectangle](https://rectangleapp.com/), [Hookmark](https://hookproductivity.com/).

## Conversion and distribution: what the numbers actually show

**Type, six months after launch:** Nicolas Bichon reported 653 sales and US$2.68K sales revenue for a US$3.99 paid-upfront Mac note utility, launched November 29, 2023. About US$1,000 arrived during three launch days, another US$550 during five days around Lifehacker coverage; otherwise typically 0–2 sales/day. Website traffic attribution was 60%, store search/browse 40%. His article’s title says $2,800; use the more precise body figure and call it reported sales, not profit. He planned a trial and price rise: neither outcome was measured in this article. Native review prompts reportedly increased five-star ratings, without a numerical controlled comparison. Press, launch, timing and an audience changed together; this does not establish causality for one UI change. Lesson: distribution and repeatable discovery can dominate polish’s effect on income. [June 3, 2024 report](https://nicolasbichon.com/articles/type-6-months-later).

**Do not import mobile funnel benchmarks.** Trial-to-paid, install-to-paid, product-page-to-download and retained payer rates have different denominators. The search surfaced RevenueCat’s iOS/Android comparisons, not a verified representative native-Mac cohort. No controlled Mac-specific paywall experiment was established in this pass. The Mac-specific cohorts below supply better context, but do not establish controlled causal effects or universal conversion targets. [Apple metric definitions](https://developer.apple.com/help/app-store-connect-analytics/reference/metrics-definitions/).

**Featuring:** Apple names cohesive useful UX, UI quality, innovation, uniqueness, accessibility, localization and a compelling product page. Featuring is regional and editorial; criteria are not a guarantee. Submit a nomination at least two weeks ahead; Apple recommends up to three months for wider consideration. A genuinely useful new capability or story supplies a pitch; cosmetic OS adoption alone does not establish demand or revenue. [Apple’s current featuring guidance](https://developer.apple.com/app-store/getting-featured/).

## Failure, trust and switching

**MacUpdater: useful software can fail economically.** CoreCode’s April 30, 2025 release announced development would end January 1, 2026, citing unsustainable monetization under its non-subscription model despite tens of thousands of users and coverage of 6,700+ apps. Those scale claims come from the vendor, not audited accounts. Current FAQ confirms discontinuation, final free 3.5 and declining usefulness without daily maintenance; database servers remain running during 2026. Its problem is a continuously maintained service beneath a purchased utility. Inference: count ongoing catalog verification and support before promising indefinite functionality. The press release gives a cause, not detailed profit/loss evidence. [Owner’s press release](https://www.corecode.io/macupdater/press_release_discontinuation.pdf), [current FAQ](https://www.corecode.io/macupdater/faq.html).

**TextExpander: reprice the right audience.** In 2016, a subscription and vendor-hosted sync accompanied team sharing. Macworld criticized value for individuals and reported snippets disappearing when a subscription lapsed; export remained available from the Mac app. Brett Terpstra argued the launch failed to explain benefits relevant to individual customers; he disclosed Smile sponsorship. Pricing was subsequently adjusted. This documents a trust and positioning failure, not proof subscriptions fail. Current TextExpander has a free tier, so do not repeat the 2016 expiry behavior as present fact. [Macworld review, April 7, 2016](https://www.macworld.com/article/227761/textexpander-6-review-a-snippets-subscription-service-thats-priced-too-high.html), [Terpstra’s disclosed perspective](https://brettterpstra.com/2016/04/12/the-textexpander-subscription-snafu/), [current pricing/free-tier policy](https://textexpander.com/pricing).

**Bartender: permissions amplify ownership trust.** June 2024 reporting describes users discovering an ownership transfer through a signing-certificate change and MacUpdater warning. New permission prompts preceded adequate explanation. Do not equate this with proven malware. The lesson is concrete: disclose transfer, signer and data-policy changes before asking customers to renew sensitive permissions. Public objections establish a trust event; they do not quantify churn or prove today’s app unsafe. [MacRumors report and update](https://www.macrumors.com/2024/06/04/bartender-mac-app-new-owner/).

**Transmit: integrations carry external business risk.** Panic explained in October 2024 that Google Drive’s annual security-assessment burden made continuing the integration unreasonable. Other transfer protocols remained supported. Feature withdrawal need not reflect bad code or lack of user demand: integration review costs can exceed its value to a small team. Preserve portable core workflows and explain deprecation early. [Panic’s account](https://blog.panic.com/end-of-the-road-for-google-drive-and-transmit/).

**Beautiful features do not settle scope.** Things’ lack of collaboration is confirmed in support; one household may need shared lists more than elegant personal organization. Conversely, adding collaboration brings identity, conflict and notification costs. Treat missing features as a target-audience fit question before classifying them as defects. [Things support](https://culturedcode.com/things/support/articles/2803552/).

## Full economics

**Distribution costs:** Eligible enrolled Small Business Program developers pay Apple 15% commission, with a US$1 million proceeds threshold and associated-account rules. Do not reduce eligibility to gross revenue from one app. Direct sales may use a merchant of record: Paddle advertises 5% + US$0.50 per checkout, including tax/compliance and payment support; under-US$10 products can request custom terms. These fee schedules cover different services and constraints. On a hypothetical US$5 transaction, the fixed fifty cents makes the stated Paddle fee 15%, before tax/refund details; on US$50 it is 6%. This arithmetic illustrates why headline percentages mislead, not an all-in profitability comparison. [Apple](https://developer.apple.com/app-store/small-business-program/), [Paddle](https://www.paddle.com/pricing).

**Setapp is not a fixed per-install payment:** Membership allocates 70% of each subscriber’s revenue among used apps, weighted by price tiers. Eligible referrals add 20%; unused apps receive no usage share for that period. Free-trial use creates no revenue; new-user allocation can lag roughly 2–2.5 months. Model cash timing, usage mix and direct-sale cannibalization separately. These are vendor terms, not proof the channel increases total profit for every app. [Setapp revenue documentation](https://docs.setapp.com/docs/setapp-membership-revenue).

**Budget the hidden work:** OS beta testing; Accessibility and screen-recording permission support; security/signing and updater repair; billing and license recovery; refunds and chargebacks; customer support; docs/localization; storage, sync and backups; external API reviews; incident response; owner salary and replacement capacity. MacUpdater and Panic show two real ongoing costs that a “finished desktop binary” story can conceal. A subscription can fund these; so can sufficient new sales, upgrades or paid support. Choose with actual cohorts and costs, not ideological labels.

**Track the full chain:** qualified visit → download → successful launch → permission completion → first useful action → repeat use → purchase → retained payer → contribution after fees, refunds, service use and support. Segment by source, locale, OS and app version. Test trial start timing, trial duration, purchase explanation and feature packaging independently where sample size permits. Low-volume indie data may not support meaningful A/B conclusions; qualitative observation and staged cohorts are more honest than invented certainty.

## Business measurements and storefront evidence

The following are primary cohort and cost disclosures. None is a randomized experiment or an independently audited account.

**A real studio cost account:** Alin Panaitiu’s December 24, 2023 account covers rcmd, Grila and Gamma Dimmer on the App Store, mainly Lunar plus new Clop through Paddle. Reported customer payments totaled US$108,400; proceeds after platform fees/tax/FX deductions US$84,800. His final US$69,960 figure subtracts Romanian taxes, US$600 hosting, US$140 IPStack, US$100 developer membership and US$1,000 further currency costs. He calls it net profit but describes it as his salary equivalent: owner labor is not charged at a replacement wage, and nonrecurring test hardware is excluded. He also reports support consuming much of his day and choosing autonomy over better-paid consulting. This is a concrete livelihood account, not an audited margin benchmark or current tax guide. Do not repeat his tax interpretation as advice. [Original account](https://notes.alinpanaitiu.com/Costs-of-running-a-macOS-app-studio-business).

**Mac-specific conversion evidence, with confounding:** Tyler Hall’s December 9, 2020 portfolio report gives Rebudget conversion of 2.1% direct versus 8% Mac App Store, but direct had 13 times as many active users. Different source populations prevent crediting store checkout alone. CommandQ’s two-week trial/US$9.99 purchase converted 6%; Ears’ unrestricted shareware/nag model was estimated at 7%, with US$2.78 average sale. VirtualHostX’s annual plan accounted for 91% of subscribers; reported 8% churn covered only the first week of annual renewals. Different apps, audiences, funnels and small/unstated sample sizes make these observations, not controlled model comparisons. Historical prices are attached to 2020. [One Year of App Pricing Experiments](https://tyler.io/2020/12/09/one-year-of-app-pricing-experiments/).

**Type’s follow-up proves purchase reliability matters:** On January 2, 2025, Bichon described macOS 15.2’s new production payment sheet appearing below the menu-bar icon without a purchase button. About 100 users encountered it during three days of 9to5Mac attention; 29 contacted support. He reported 138 trials and 60 lifetime purchases (~43%) and estimated US$240 lost, extrapolating that rate to unreachable affected users. Lost revenue is modeled, not observed; the ratio is not a universal Mac conversion target. Two expedited submissions and a user workaround consumed the launch opportunity. Recommendation: test real release purchase presentation and window activation after OS updates, instrument failures, and provide support recovery. [Developer incident account](https://nicolasbichon.com/articles/being-featured-and-having-a-huge-crash-at-the-same-time).

**Type’s later scale:** His portfolio, read November 7, 2026, says US$8.5K revenue and 5K users. It does not date the measurement, define users or disclose costs; do not compute paid conversion from those totals. The earlier trial/price plans therefore did progress to a shipping trial by January 2025, but the sources do not isolate the change’s incremental effect. [Developer portfolio](https://nicolasbichon.com/).

**Storefront snapshot, not a quality ranking:** Apple’s US Mac Productivity paid chart, opened November 7, 2026, showed: 1 Magnet; 2 Dark Reader for Safari; 3 Scrivener 3; 4 Cyberduck; 5 LibreOffice; 6 Tampermonkey; 7 Things 3; 8 Parall; 9 LosslessCut; 10 Maccy. Search-cache order differed from the opened page; these ranks describe that retrieved snapshot only. Paid rank gives no unit count, revenue, retention, profit or direct-sales coverage. The mixture shows repeated narrow jobs alongside full document tools; it does not establish every listed publisher as indie or every listing as the canonical open-source distribution. [Apple US Mac Productivity, paid](https://apps.apple.com/us/mac/charts/6007?chart=top-paid).

**Utilities snapshot:** Same date/storefront: 1 Shadowrocket; 2 Wipr 2; 3 Keka; 4 Noir; 5 DaisyDisk; 6 MediaInfo; 7 RAR Extractor – Unarchiver Pro; 8 GrandPerspective; 9 Quantumult X; 10 Parachute. This is a discovery sample, not security endorsement or a revenue estimate. [Apple US Mac Utilities, paid](https://apps.apple.com/us/mac/charts/6002?chart=top-paid).

**Grossing evidence limit:** Apple’s opened web charts exposed Free/Paid only. A direct request to the legacy US `topgrossingmacapps` JSON feed on November 7, 2026 returned HTTP 200 and zero entries, with feed timestamp `2026-11-07T03:46:26-07:00`. The web grossing variant was inaccessible. Independent State of Mac methodology also reports empty paid/grossing legacy feeds; its paid-feed limitation must not be mistaken for absence of the working paid web chart. Thus this report cannot responsibly supply a current Mac grossing ranking from those public routes. Private direct-sale and subscription receipts prevent reconstructing total-business rankings from paid download rank. Use disclosed business accounts above instead. [Apple grossing feed](https://itunes.apple.com/us/rss/topgrossingmacapps/limit=25/json), [methodology corroboration](https://stateofmac.com/methodology/).


## Long-term use and contrary experience

**Default Folder X’s useful details compound:** Dan Frakes’ 2013 account describes decades of use and daily benefit from per-app default/recent folders and selecting an already-open Finder window as a save destination. Glenn Fleishman’s 2021 review of v5.6 records 21,764 uses across nearly six years; he specifically values the current document’s folder as the next save destination, remembered selection and keyboard navigation among recent folders. That counter is one user’s usage, not measured hours saved or population retention. These accounts support designing for repeated, low-friction transitions; they cannot verify current OS reliability. [Frakes, February 5, 2013](https://www.macworld.com/article/220335/apps-we-cant-live-without-default-folder-x.html), [Fleishman, October 22, 2021](https://www.macworld.com/article/544310/mac-gems-default-folder-x-review.html).

**Same utility, different value:** In a 2021–2023 Mac Power Users discussion, some long-term owners rarely used Default Folder X or felt Finder/Alfred/Hazel covered their needs; others described particular value across server volumes, file-type routing and recent project folders. One user suspected slow file dialogs; no controlled performance evidence accompanies it. The disagreement is informative: validate the frequency and complexity of the target workflow before adding an always-running helper. Teach concrete recipes, since several owners did not understand the feature that would help them. This is a self-selected forum, not a satisfaction survey. [MPU discussion](https://talk.macpowerusers.com/t/default-folder-x-why-the-love/24496).

**Hazel remains useful without fashionable features:** David Sparks confirmed continued Hazel use on September 6, 2026, emphasizing on-device file management without AI-token costs or remote data processing. It is a current practitioner endorsement, not a comparative benchmark; Sparks sells a Hazel training course and promoted its discount in the same post. That commercial interest belongs beside the praise. [Hazel Turns 20](https://www.macsparky.com/blog/2026/09/hazel-turns-20/).

**MacUpdater’s labor, quantified by its maker:** Its FAQ attributes roughly 80% of work to unseen daily maintenance, involving manual curation and checks despite extensive automation. Treat that share as a developer estimate. The resulting lesson is specific: maintenance-heavy catalogs need ongoing economics even if the visible UI rarely changes. The source contains historical sections alongside the discontinuation notice; use the notice for current status. [MacUpdater FAQ](https://www.corecode.io/macupdater/faq.html).
## Podcast: product timing and critique

**Mac Power Users 863, August 23, 2026; transcript inspected, audio not heard.** At **03:22**, Werner Jainek connects Things’ origin with rising interest in personal task management; at **03:46**, he describes bringing iGTD users over with an importer. Lesson: market timing and migration help explain adoption alongside polish. At **08:56**, he describes actively accepting criticism even after investing in a design. That supports review culture, not a measured business effect. These are the developer’s recollections. [Podscan transcript](https://podscan.fm/podcasts/mac-power-users/episodes/863-20-years-of-things-with-werner-jainek).

The [primary episode](https://relay.fm/mpu/863) and RSS returned 403. Tapesearch required login beyond its opening; Snipd exposed AI summaries, not the relevant full transcript. Podscan’s **06:50–07:57** text is visibly corrupt and excluded. Do not use its missing sections to assert animation internals, team process or financial results.

## Technology stacks and development tradeoffs

**Mac-first productivity:** Swift + SwiftUI, with AppKit where the interaction needs it, is a defensible starting point. SwiftUI declares scenes/state; AppKit supplies mature documents, text, tables, menus and desktop integrations. A hybrid is an intentional architecture: use `NSViewRepresentable`/`NSViewControllerRepresentable` or host SwiftUI in AppKit. Keep command/state ownership explicit across bridges; SwiftUI owns represented-view layout, and delegate events need a coordinator. Neither framework guarantees correct behavior without product-specific testing. [SwiftUI](https://developer.apple.com/documentation/swiftui), [AppKit](https://developer.apple.com/documentation/appkit), [bridge contract](https://developer.apple.com/documentation/swiftui/nsviewrepresentable).

Omni's 2026 roadmap gives a concrete developer rationale: use SwiftUI to share inspector/settings code while designing and testing the Mac experience first. This is a reported strategy and plan, not proof every planned feature shipped or that sharing all UI is optimal. [Omni roadmap](https://www.omnigroup.com/blog/omni-roadmap-2026)

**Text/document-heavy utility:** start by proving the hardest editor, file coordination, undo and large-file path with `NSTextView`/TextKit and `NSDocument`. A custom renderer or third-party editor can be justified, but must recover native text behaviors deliberately. CodeEditTextView itself warns it is for line-oriented text and lacks full system parity/RTL; STTextView documents real TextKit defects and now has GPLv3/commercial licensing. Choosing a fashionable UI framework before this spike reverses the risk order. [NSDocument](https://developer.apple.com/documentation/appkit/nsdocument), [NSTextView](https://developer.apple.com/documentation/appkit/nstextview), [CodeEditTextView](https://github.com/CodeEditApp/CodeEditTextView), [STTextView](https://github.com/krzyzanowskim/STTextView).

**Small menu utility:** `MenuBarExtra` + a Settings scene + `SMAppService` may cover nearly everything. Add KeyboardShortcuts only if global activation matters; use `NSStatusItem`/`NSPanel` when SwiftUI’s scene behavior is too restrictive. A menu-only SwiftUI app terminates if its extra is removed; plan recovery/relaunch intentionally. `LSUIElement` controls Dock/app-switcher presence. [MenuBarExtra](https://developer.apple.com/documentation/swiftui/menubarextra), [SMAppService](https://developer.apple.com/documentation/servicemanagement/smappservice).

**Cross-platform workflow:** Electron, Tauri, Flutter and Qt are viable conditional choices, not synonymous with bad UX. Electron bundles Chromium/Node; its team must ship engine security updates. Tauri uses the system WKWebView, trading bundled-engine size for OS-dependent web behavior. Flutter’s native binary does not imply AppKit controls or complete Mac interaction parity. Qt fits existing C++ desktop products but brings module/license/deployment choices. Evaluate the actual commands, text, accessibility, file access, memory, idle energy and packaging path—not a blank-window benchmark. [Electron security](https://www.electronjs.org/docs/latest/tutorial/security), [Tauri engines](https://v2.tauri.app/reference/webview-versions/), [Flutter desktop](https://docs.flutter.dev/platform-integration/desktop), [Qt macOS](https://doc.qt.io/qt-6/macos.html).

**Data:** choose one authoritative store. Core Data fits managed object graphs and established Apple integration; SwiftData fits modern Swift models if its OS floor and migration behavior meet the product; GRDB fits explicit SQL, migrations, observation and full-text search. CloudKit is transfer/storage infrastructure with limited offline caching, not a replacement for an app’s local model. Do not make “uses iCloud” stand in for conflict, offline and account-change design. [Core Data](https://developer.apple.com/documentation/coredata), [SwiftData](https://developer.apple.com/documentation/swiftdata), [GRDB](https://github.com/groue/GRDB.swift), [CloudKit](https://developer.apple.com/documentation/cloudkit).

## Compatibility is four promises

1. **Installable:** CPU slices, deployment target, signing and dependency floor allow launch.
2. **Feature-supported:** a capability exists, permission can be granted, and required service/account is available.
3. **Adapted:** windows, controls, text, density, appearance and input work for that environment.
4. **Tested:** named releases/configurations have passed relevant workflows. “Compiles for macOS 13” proves none of the later promises.

These distinctions are a research framework, not Apple terminology. Apple’s Xcode table independently lists host OS, SDKs, deployment targets and compiler/language modes. The current fetched table lists Xcode 27.2 and 27.3 beta, with macOS 12–27 deployment targets; use the selected release row when configuring a real project. A newer SDK can change framework behavior even when the deployment target stays unchanged. [Xcode requirements](https://developer.apple.com/xcode/system-requirements/), [Qt explanation of SDK-linked behavior](https://doc.qt.io/qt-6/macos.html).

| Axis | What users experience; implementation and support cost |
| --- | --- |
| Minimum OS vs SDK | Build SDK is the API surface compiled against; deployment target is oldest intended runtime. Guard newer APIs and provide an honest fallback, not a launch-time crash. Verify every package and embedded helper, not only the app target. New build tools need not force users onto the build machine’s OS. [Xcode](https://developer.apple.com/xcode/system-requirements/) |
| Meaningful API floors | macOS 13 brings `MenuBarExtra`, Swift Charts and `SMAppService`; macOS 14 brings SwiftData and Observation. ScreenCaptureKit starts at 12.3; individual newer methods require later systems. Support below a feature’s floor means an older implementation, reduced feature set, or higher minimum—not a cosmetic checkbox. [MenuBarExtra](https://developer.apple.com/documentation/swiftui/menubarextra), [Charts](https://developer.apple.com/documentation/charts), [SwiftData](https://developer.apple.com/documentation/swiftdata), [Observation](https://developer.apple.com/documentation/observation), [ScreenCaptureKit](https://developer.apple.com/documentation/screencapturekit) |
| Intel/Apple silicon | Universal binaries contain both architectures. All frameworks, plugins, CLIs and helpers must match the promised architecture; an ARM app with an Intel-only helper is not wholly native. Test actual Intel where supported: Rosetta on ARM cannot reproduce every hardware/driver condition. ARM-only saves testing/support if audience allows; universal retains older hardware. No audience prevalence estimate established. [Apple universal binaries](https://developer.apple.com/documentation/apple-silicon/building-a-universal-macos-binary) |
| Resource tiers | A low-memory laptop, battery mode and large library expose synchronous indexing, unbounded thumbnails and permanent polling. Set measured startup/idle/import/search budgets on the weakest supported machine. GPU/ML availability is capability-specific; offer CPU/basic fallback or document the requirement. Minimum RAM is product evidence, not inferable from “Mac native.” [Accelerate](https://developer.apple.com/documentation/accelerate), [Metal feature tables](https://developer.apple.com/metal/availability/) |
| Store/direct | Mac App Store requires App Sandbox. Direct distribution still needs credible Developer ID signing/notarization and an update path; it does not erase privacy permissions. Dual channels add receipt/licensing, updater, entitlements, support and migration variants. Sandbox proves containment, not that every file is accessible. [Sandbox](https://developer.apple.com/documentation/security/app-sandbox), [notarization](https://developer.apple.com/documentation/security/notarizing-macos-software-before-distribution) |
| Sandboxed files | User-selected files, security-scoped bookmarks, related files and app groups require deliberate access design. POSIX/ACL/privacy restrictions can still deny operations sandbox entitlements permit. Handle revoked/stale access, moved volumes and missing files; provide a user-driven reselect action. [Apple file access](https://developer.apple.com/documentation/security/accessing-files-from-the-macos-app-sandbox) |
| Login/background helpers | On 13+, `SMAppService` registers bundled login items/agents/daemons subject to approval; older releases need older mechanisms. Reflect actual registration/approval state rather than a saved Boolean. Test uninstall/reinstall, duplicate copies and moves out of Downloads. [SMAppService](https://developer.apple.com/documentation/servicemanagement/smappservice), [LaunchAtLogin caveats](https://github.com/sindresorhus/LaunchAtLogin) |
| Screens/windows | A minimum-size window, split layout, full screen, Stage Manager, external display removal and mixed scaling are separate tests. Preserve reachable window positions; let toolbars contract and tables scroll. A screenshot on one Retina display gives no support evidence. Concrete shipped fixes: Things 3.24.2 fixes narrow-window toolbar shrinking. [Things release notes](https://culturedcode.com/things/support/articles/1100684/), [split controller](https://developer.apple.com/documentation/appkit/nssplitviewcontroller) |
| Input/accessibility | Keyboard-only, mouse, trackpad, IME/marked text, RTL, VoiceOver and larger text affect editing and focus—not just labels. Include touch-capable Mac guidance where applicable to current targets; do not assume all future Mac input remains pointer-only. Use current HIG and actual hardware capability. [NSTextView](https://developer.apple.com/documentation/appkit/nstextview), [accessibility protocol](https://developer.apple.com/documentation/appkit/nsaccessibilityprotocol), [Mac design](https://developer.apple.com/design/human-interface-guidelines/designing-for-macos) |
| Services/accounts | iCloud unavailable, signed out, storage-full or changed accounts must not destroy local work. Calendar/contacts permissions can be denied or changed; screen capture selection is revocable. Keep unrelated functions available. No automatic claim that an Apple API works in every locale/account. [CloudKit](https://developer.apple.com/documentation/cloudkit), [EventKit](https://developer.apple.com/documentation/eventkit), [ScreenCaptureKit](https://developer.apple.com/documentation/screencapturekit) |
| Language/region | Localize strings and format dates/numbers with Foundation; test long labels, plural forms, different calendars/time zones and non-Latin filenames. Persist semantic dates correctly for the task. A translated website does not establish localized app/support quality. [Foundation](https://developer.apple.com/documentation/foundation) |
| Web runtime | Electron’s current README floor is Ventura; current Tauri README says 10.15+, but actual WebKit features depend on OS. Current Qt 6.12 docs list macOS 14.4+. These are framework-specific floors, not native-platform requirements; plugin/package floors may be higher. [Electron](https://github.com/electron/electron), [Tauri](https://github.com/tauri-apps/tauri), [Qt](https://doc.qt.io/qt-6/macos.html) |
| Extensions/plugins | A parent app working does not establish Finder, Quick Look, Share, Spotlight or helper reliability. Test extension lifecycle and signed distribution; host/plugin CPU, library validation and entitlements can block loading. [notarization/plugin guidance](https://developer.apple.com/documentation/security/notarizing-macos-software-before-distribution) |
| Cross-device | Universal purchase, an iPad binary on Apple silicon, Catalyst and a native Mac target are different product decisions. Shared data should preserve IDs, edits and conflict rules; shared code must not impose touch navigation on desktop. No assumption that shipping an iPhone app supplies a finished Mac app. [SwiftUI](https://developer.apple.com/documentation/swiftui), [AppKit](https://developer.apple.com/documentation/appkit) |

### Real small-team support strategies

- **Current+previous as promise; older where practical:** Panic says each major update supports current and previous macOS. Its actual table can cover more: Nova 14 spans 15/26/27; Transmit 5.11 spans 14/15/26/27. It also supplies older downloadable versions. Treat the promise as a floor of coverage, not an assertion that every app drops N−2. [Panic compatibility](https://help.panic.com/general/os-compatibility/).
- **Broad support, then deliberate floor increase:** Things 3.22.14 still required 10.15 on 2026-08-14; 3.23 raised the minimum to 13.3 on August 21, with 3.24.2 retaining that floor. Old purchasers can use their last compatible version without new updates. This shows an actual support transition, not its private revenue rationale. [release notes](https://culturedcode.com/things/support/articles/1100684/), [minimum requirements policy](https://culturedcode.com/things/support/articles/5571307/).
- **Version matrix plus legacy downloads:** Bare Bones maps each OS to a recommended BBEdit release, including old releases for old systems, and calls out specific OS patch-level defects. Its compatibility page and download/FAQ pages can lag one another on app version; prefer the release-specific requirements at purchase/build time. [Bare Bones matrix](https://faq.barebones.com/support/new-os.html), [BBEdit FAQ](https://barebones.com/support/bbedit/faqs.html).

**Small-team inference:** select the oldest OS and hardware from reachable customers and core APIs, then budget real test machines/VMs, migration fixtures and beta testing. A deep system utility needs more OS-specific testing than a local timer; an enterprise deployment may justify older systems; an AI utility may require recent silicon. Do not recommend one universal minimum from these three examples. Geographic hardware age, payment access and service availability need actual audience evidence; public app support matrices do not supply it.

Store submission deadlines govern accepted builds, not every user’s runtime. The current requirements page changes and contains platform-specific notices; do not copy an iOS SDK deadline into a Mac minimum. [Apple upcoming requirements](https://developer.apple.com/news/upcoming-requirements/).

## Named ecosystem catalog

Each row states purpose, fit and an alternative or boundary. Apple rows are first-party API evidence. Repository links support declared capability/requirements; absent a named shipped consumer, adoption breadth is **not measured**. Pin released versions, not `main`: Nuke and Sentry explicitly distinguish development branches from released series. Licensing claims below come from inspected READMEs where stated; verify the exact dependency tag and transitive notices before distribution.

### Language, build and packages

| # | Tool | Fit, alternative, constraint |
| --- | --- | --- |
| 1 | [Swift](https://www.swift.org/documentation/) | Native language and concurrency model; share pure packages across Apple apps. Compiler version, language mode and deployment target differ. Objective-C remains relevant for existing AppKit code and C interop. |
| 2 | [Xcode](https://developer.apple.com/xcode/system-requirements/) | Apple SDK, signing, debugger, tests, Instruments. Pin CI Xcode; newer IDE host requirements do not equal app runtime floor. |
| 3 | [Swift Package Manager](https://www.swift.org/documentation/package-manager/) | Default candidate for Swift dependencies/modules; prefer local packages for simple decomposition. Binary artifacts/plugins add build and trust costs. |
| 4 | [XcodeGen](https://github.com/yonaskolb/XcodeGen) | Generate `.xcodeproj` from a readable specification; useful where project merges churn. Extra generation tool versus a small checked-in Xcode project. |
| 5 | [Tuist](https://github.com/tuist/tuist) | Project generation, caching, selective tests and build insights. More useful at multi-module/team scale; hosted features introduce service/pricing choices. Named companies are vendor-reported adoption, not Mac-indie prevalence. |
| 6 | [SwiftLint](https://github.com/realm/SwiftLint) | Configurable static style/convention checks; MIT per README. Keep a small useful rule set; lint is not correctness testing. SwiftSyntax/SourceKit compatibility matters. |
| 7 | [SwiftFormat](https://github.com/nicklockwood/SwiftFormat) | Nick Lockwood’s formatter, distinct from `swift-format`; configure Swift version/language mode. Choose one formatter to avoid churn. |
| 8 | [swift-format](https://github.com/swiftlang/swift-format) | Swift project formatter used by SourceKit-LSP; match toolchain. Its defaults are not an official universal Swift style mandate. |
| 9 | [SwiftGen](https://github.com/SwiftGen/SwiftGen) | Generate typed resources/localization/assets; useful beyond SDK-generated accessors. Adds generation/templates; avoid duplicate mechanisms for the same asset. Older README badges do not establish abandonment. |
| 10 | [SwiftSyntax](https://github.com/swiftlang/swift-syntax) | Swift parsing/macros/source tools; release alignment with compiler is consequential. Avoid adding macro complexity for trivial code generation. |
| 11 | [Swift Argument Parser](https://github.com/apple/swift-argument-parser) | Companion CLI arguments/help/validation; preferable to hand-parsing complex commands. Not needed for an app without a CLI. |
| 12 | [Swift Collections](https://github.com/apple/swift-collections) | Ordered sets/dictionaries, deques and specialized structures. Use when standard arrays/dictionaries do not fit; current README flags Swift 6.2 backdeployment-library packaging for standalone binaries. |
| 13 | [Swift Algorithms](https://github.com/apple/swift-algorithms) | Reusable sequence algorithms; reduce bespoke combinator code. Plain standard-library operations suffice for simple paths. |
| 14 | [Swift Async Algorithms](https://github.com/apple/swift-async-algorithms) | Debounce/throttle/merge/combine asynchronous streams. Alternative to equivalent Combine pipelines; cancellation/lifetime still need design. |

### UI, state and Mac controls

| # | Tool | Fit, alternative, constraint |
| --- | --- | --- |
| 15 | [SwiftUI](https://developer.apple.com/documentation/swiftui) | Declarative scenes, forms and state-driven presentation. Native defaults help; per-OS behavior and complex focus/window cases still need tests. |
| 16 | [AppKit](https://developer.apple.com/documentation/appkit) | Mature Mac windows, menus, text, events and document behavior. More explicit management; useful host or bridge rather than an all-or-nothing rewrite. |
| 17 | [NSViewRepresentable](https://developer.apple.com/documentation/swiftui/nsviewrepresentable) | Bridge AppKit components into SwiftUI; coordinator handles delegate/action feedback. SwiftUI owns represented view geometry. |
| 18 | [Observation](https://developer.apple.com/documentation/observation) | Property-read-based change tracking; macOS 14+ base framework. Combine/ObservableObject or Perception for older requirements. |
| 19 | [Combine](https://developer.apple.com/documentation/combine) | Publisher pipelines and existing integration; still documented, not automatically deprecated by async/await. Async sequences can simplify new one-shot/stream code. |
| 20 | [The Composable Architecture](https://github.com/pointfreeco/swift-composable-architecture) | Explicit state/actions/effects and testability; MIT. Fit for teams valuing one architecture; coupling, learning and migrations outweigh value for some tiny utilities. |
| 21 | [Swift Dependencies](https://github.com/pointfreeco/swift-dependencies) | Controlled dependency overrides for tests/previews; MIT. Plain initializer injection remains sufficient in small models. |
| 22 | [Swift Navigation](https://github.com/pointfreeco/swift-navigation) | State-driven navigation tools; avoid importing mobile navigation assumptions. Native scene/window commands may be enough for Mac. |
| 23 | [Swift Sharing](https://github.com/pointfreeco/swift-sharing) | Shared state across features and persistence; MIT. Does not make distributed sync/conflicts disappear. |
| 24 | [Perception](https://github.com/pointfreeco/swift-perception) | Observation-style backport to macOS 10.15; MIT. Only pay compatibility integration cost if supporting below native Observation. |
| 25 | [SwiftUI Introspect](https://github.com/siteline/swiftui-introspect) | Public-API traversal to underlying AppKit controls. Explicit opt-in per OS generation; use a native API or owned bridge when available. Missing expected view becomes a no-op, so test the customization actually occurred. |
| 26 | [NSTableView](https://developer.apple.com/documentation/appkit/nstableview) | Dense sortable/selectable records and mature desktop behavior. SwiftUI Table for simpler needs; large-data responsiveness must be measured. |
| 27 | [NSOutlineView](https://developer.apple.com/documentation/appkit/nsoutlineview) | Hierarchical file/tree data; model expansion and selection separately. Avoid building a tree from nested arbitrary buttons when semantics matter. |
| 28 | [NSCollectionView](https://developer.apple.com/documentation/appkit/nscollectionview) | Reusable items/custom layouts for libraries; a simple SwiftUI grid may suffice. |
| 29 | [NSSplitViewController](https://developer.apple.com/documentation/appkit/nssplitviewcontroller) | Resizable/collapsible panes and lazy child views; Auto Layout required. Alternative: NavigationSplitView for compatible flows. |
| 30 | [NSGridView](https://developer.apple.com/documentation/appkit/nsgridview) | Aligned label/control grids; useful for Mac settings. Flexible layout beats hardcoded label widths. |
| 31 | [Settings](https://github.com/sindresorhus/Settings) | AppKit settings-window/pane wrapper with SwiftUI support; supports 10.13+. SwiftUI Settings scene suffices for many modern apps. Repository explicitly handles Preferences→Settings naming by OS. |
| 32 | [MenuBarExtra](https://developer.apple.com/documentation/swiftui/menubarextra) | Menu/window style menu utilities on macOS 13+. Removal/lifecycle semantics matter; NSStatusItem for greater control. |
| 33 | [NSStatusItem](https://developer.apple.com/documentation/appkit/nsstatusitem) | AppKit status bar item and menu/button behavior. Do not implement a fake menu bar as an always-on-top window. |
| 34 | [NSPanel](https://developer.apple.com/documentation/appkit/nspanel) | Auxiliary palettes/inspectors; app/window activation behavior differs from ordinary windows. Use only when utility semantics fit. |
| 35 | [KeyboardShortcuts](https://github.com/sindresorhus/KeyboardShortcuts) | User-recorded global hotkeys, conflict warnings, App Store-compatible; 10.15+. Developer names Dato/Jiffy/Plash/Lungo as production consumers. Not needed for local menu shortcuts. |
| 36 | [DockProgress](https://github.com/sindresorhus/DockProgress) | Dock task progress, macOS 12+; progress APIs called on main actor. Inline progress remains primary; avoid needless Dock noise. |
| 37 | [NSAccessibilityProtocol](https://developer.apple.com/documentation/appkit/nsaccessibilityprotocol) | Modern method-based roles, values, actions, notifications. Standard controls provide much automatically; custom controls must expose real semantics. |

### Documents, storage and sync

| # | Tool | Fit, alternative, constraint |
| --- | --- | --- |
| 38 | [NSDocument](https://developer.apple.com/documentation/appkit/nsdocument) | File-backed document lifecycle, save/revert/print/window integration. SwiftUI document APIs may suffice; an internal database app need not pretend to be document-based. |
| 39 | [UndoManager](https://developer.apple.com/documentation/foundation/undomanager) | Named reversible operations/redo; group user intentions, not arbitrary implementation calls. Persistent history is separate. |
| 40 | [NSFileCoordinator](https://developer.apple.com/documentation/foundation/nsfilecoordinator) | Coordinate shared file operations across presenters/processes; useful for documents touched elsewhere. Not a substitute for DB transaction protocols. |
| 41 | [NSFilePresenter](https://developer.apple.com/documentation/foundation/nsfilepresenter) | Receive coordinated external file changes; pair with coordinator. Avoid stale editors silently overwriting moved/updated documents. |
| 42 | [Uniform Type Identifiers](https://developer.apple.com/documentation/uniformtypeidentifiers) | Declare content type/conformance for import/export/dragging. File-extension string guesses miss packages and alternative representations. |
| 43 | [Core Data](https://developer.apple.com/documentation/coredata) | Established graph persistence, undo and CloudKit mirroring; test schema evolution and merge behavior. GRDB for explicit relational control. |
| 44 | [SwiftData](https://developer.apple.com/documentation/swiftdata) | Model macros/SwiftUI integration, macOS 14+. Prototype complex migrations and concurrency on oldest supported OS; availability alone is insufficient. |
| 45 | [GRDB](https://github.com/groue/GRDB.swift) | SQLite queries/migrations/observation/WAL concurrency. README: 7.12.0 released Nov 1 2026, macOS 10.15+, Swift 6.1+. Strong concrete maintenance signal, not a market-share claim. |
| 46 | [SQLite.swift](https://github.com/stephencelis/SQLite.swift) | Type-safe SQL expression layer; MIT. Compare needed migration/observation features with GRDB before choosing. |
| 47 | [SQLCipher](https://github.com/sqlcipher/sqlcipher) | Encrypted SQLite, with distinct community/commercial offerings. Adds key recovery and binary/build integration; never promise encryption compensates for lost keys. |
| 48 | [GRDBQuery](https://github.com/groue/GRDBQuery) | SwiftUI query observation over GRDB; README 0.11.0, macOS 11+, Swift 6. Direct observation is an alternative; version-age alone proves no abandonment. |
| 49 | [UserDefaults / Defaults](https://github.com/sindresorhus/Defaults) | Defaults adds typed keys, Codable, observation and iCloud convenience over UserDefaults; macOS 11+. Developer reports own-app use. Use for preferences, not large authoritative document collections. |
| 50 | [CloudKit](https://developer.apple.com/documentation/cloudkit) | Apple-account cloud storage/transfer. Local authoritative model and sync policy remain necessary; custom backend when cross-platform/accounts demand it. |
| 51 | [File Provider](https://developer.apple.com/documentation/fileprovider) | Remote document storage surfaced through system file workflows; a serious sync extension, not a generic export feature. Local sharing may need no provider. |
| 52 | [Finder Sync](https://developer.apple.com/documentation/findersync) | Finder badges/context controls for sync folders; not interchangeable with File Provider’s storage model. |
| 53 | [ZIPFoundation](https://github.com/weichsel/ZIPFoundation) | ZIP read/create/edit for exports/imports; macOS 10.11+. Handle untrusted paths/size limits; archives are not backups until restoration is tested. |
| 54 | [Yams](https://github.com/jpsim/Yams) | YAML via libYAML; both MIT. Good for developer-facing config; Codable JSON suffices if YAML’s human editing is unnecessary. |

### Networking, security and accounts

| # | Tool | Fit, alternative, constraint |
| --- | --- | --- |
| 55 | [URLSession](https://developer.apple.com/documentation/foundation/urlsession) | HTTP transfer, authentication, redirects/background transfers. Usually enough before adding a networking abstraction. |
| 56 | [Network](https://developer.apple.com/documentation/network) | TCP/UDP/TLS/custom protocols. Apple says continue URLSession for HTTP/URL resources. |
| 57 | [Alamofire](https://github.com/Alamofire/Alamofire) | HTTP request/response conveniences; MIT; current README supports Swift 6 and old macOS floor. Choose when its features remove real code, not just to wrap one request. |
| 58 | [Keychain Services](https://developer.apple.com/documentation/security/keychain-services) | Small secrets/credentials. Not general document storage; handle locked/missing items and app-signing/access-group changes. |
| 59 | [CryptoKit](https://developer.apple.com/documentation/cryptokit) | System hashing, signatures, key agreement and authenticated encryption; Apple recommends it over lower-level interfaces for supported operations. |
| 60 | [CryptoSwift](https://github.com/krzyzanowskim/CryptoSwift) | Additional pure-Swift algorithms/interoperability. Prefer CryptoKit where adequate; algorithm availability is not protocol/security review. |
| 61 | [LocalAuthentication](https://developer.apple.com/documentation/localauthentication) | Touch ID/system authentication with fallback. Hardware and policy vary; app account ownership is a separate concern. |
| 62 | [AuthenticationServices](https://developer.apple.com/documentation/authenticationservices) | Passkeys, Apple sign-in and web authentication sessions. Prefer system auth to capturing passwords in embedded custom forms. |
| 63 | [SwiftSoup](https://github.com/scinfu/SwiftSoup) | HTML DOM parsing/CSS queries for clippers/importers; MIT. Parser correctness does not grant permission to fetch or safely execute content. |

### Text, media and useful integrations

| # | Tool | Fit, alternative, constraint |
| --- | --- | --- |
| 64 | [NSTextView / TextKit](https://developer.apple.com/documentation/appkit/nstextview) | Rich editing, selection, marked text, key bindings and attachments. Test TextKit mode and real IMEs; avoid replacing all this for cosmetic styling. |
| 65 | [NSTextFinder](https://developer.apple.com/documentation/appkit/nstextfinder) | Standard find bar and responder-chain commands. Custom content can implement its client protocol. |
| 66 | [Swift Markdown](https://github.com/swiftlang/swift-markdown) | cmark-gfm-based parse/edit/analyze tree; renderer is separate. Useful for structured Markdown transformations. |
| 67 | [MarkdownUI](https://github.com/gonzalezreal/swift-markdown-ui) | SwiftUI Markdown renderer, now maintenance mode; see avoid/context section. Existing apps need not rewrite automatically. |
| 68 | [STTextView](https://github.com/krzyzanowskim/STTextView) | TextKit 2-based editor, used for Swift Studio; macOS 14+. GPLv3 or commercial license is consequential. |
| 69 | [CodeEditTextView](https://github.com/CodeEditApp/CodeEditTextView) | MIT, line-oriented editor component for specific cases. Owner warns against treating it as full RTL/system-text replacement; source editing features belong in parent CodeEditSourceEditor. |
| 70 | [Splash](https://github.com/JohnSundell/Splash) | Swift syntax highlighting, with shipped usage in Swift by Sundell articles. Not a general multi-language editor engine. |
| 71 | [WebKit / WKWebView](https://developer.apple.com/documentation/webkit) | Rich web previews/integration. Keep navigation/auth and trusted JS bridges explicit; native shell does not make untrusted HTML safe. |
| 72 | [Nuke](https://github.com/kean/Nuke) | Image pipeline/cache/processing/coalescing; MIT. README says 13 released, 14 in development; 13 needs macOS 12/Swift 6.2. Simple local icons do not need it. |
| 73 | [Kingfisher](https://github.com/onevcat/Kingfisher) | Alternative image downloader/cache with AppKit/SwiftUI integrations; MIT. Version-series compiler/OS requirements differ; pin and check. |
| 74 | [Image I/O](https://developer.apple.com/documentation/imageio) | Efficient image formats/metadata/color management; use thumbnail decode rather than loading giant originals for rows. |
| 75 | [Core Image](https://developer.apple.com/documentation/coreimage) | System image processing/filter pipelines; less engine ownership than custom GPU code. |
| 76 | [PDFKit](https://developer.apple.com/documentation/pdfkit) | PDF display/manipulation. Specialized full PDF editing may exceed it; validate damaged/large documents. |
| 77 | [Vision](https://developer.apple.com/documentation/vision) | OCR and image analysis for document utilities; language/revision/hardware availability is feature-specific. |
| 78 | [Natural Language](https://developer.apple.com/documentation/naturallanguage) | Language identification/tokenization/tagging; useful before introducing a remote AI dependency for simple text tasks. |
| 79 | [Swift Charts](https://developer.apple.com/documentation/charts) | Native charts with accessibility/localization, macOS 13+. Rendering a chart is not choosing honest axes or readable density. |
| 80 | [AVFoundation](https://developer.apple.com/documentation/avfoundation) | Playback/capture/audio-video processing for focused utilities. Permission/device interruption handling remains product work. |
| 81 | [ScreenCaptureKit](https://developer.apple.com/documentation/screencapturekit) | Screen/audio streams, 12.3+; current docs recommend system content picker. Older/newer method floors differ. |
| 82 | [Accelerate](https://developer.apple.com/documentation/accelerate) | Optimized CPU math/image work; good alternative to handwritten SIMD or premature GPU kernels. |
| 83 | [Metal](https://developer.apple.com/documentation/metal) | GPU compute/rendering for justified workloads. Usually excessive for ordinary lists/forms; capability tests and GPU-family differences matter. |
| 84 | [NSPasteboard](https://developer.apple.com/documentation/appkit/nspasteboard) | Rich multi-representation copy/paste, drag and Services. Preserve interoperable plain text/file types alongside app formats. |
| 85 | [NSFilePromiseReceiver](https://developer.apple.com/documentation/appkit/nsfilepromisereceiver) | Receive lazily produced dragged files. Test Mail/Finder/browser drags rather than accepting only existing local URLs. |
| 86 | [NSWorkspace](https://developer.apple.com/documentation/appkit/nsworkspace) | Open/reveal files and track workspace/device changes. Use system routing rather than hardcoded application paths. |
| 87 | [Quick Look](https://developer.apple.com/documentation/quicklook) | Common-file previews; platform-specific preview APIs/extensions differ. Custom document types may need extension work. |
| 88 | [Core Spotlight](https://developer.apple.com/documentation/corespotlight) | Index app content for system discovery; update/deletion/privacy policy matters as much as indexing. |
| 89 | [App Intents](https://developer.apple.com/documentation/appintents) | Expose meaningful actions/entities to Shortcuts/Siri/Spotlight; base macOS 13+. Individual integrations have newer floors. |
| 90 | [WidgetKit](https://developer.apple.com/documentation/widgetkit) | Glanceable system surfaces; choose timely small content, not a miniature app. Update budgets and family availability vary. |
| 91 | [EventKit](https://developer.apple.com/documentation/eventkit) | Calendar/reminder data and changes. EventKitUI examples are iOS-specific; Mac UI still needs design. |
| 92 | [Contacts](https://developer.apple.com/documentation/contacts) | Permissioned localized contact data; replaces Address Book framework. Avoid copying whole address books for one selected person. |
| 93 | [UserNotifications](https://developer.apple.com/documentation/usernotifications) | Local/push notifications and actions. Permission and Focus affect delivery; no guarantee of precise visible interruption. |
| 94 | [NSPrintOperation](https://developer.apple.com/documentation/appkit/nsprintoperation) | System print/PDF workflows. Useful in document/productivity apps; web-style custom print UI is often unnecessary. |

### Diagnostics, testing and release

| # | Tool | Fit, alternative, constraint |
| --- | --- | --- |
| 95 | [Logger](https://developer.apple.com/documentation/os/logger) | Unified logging by subsystem/category/level. Redact sensitive text; logs do not replace user-visible recovery. |
| 96 | [OSSignposter](https://developer.apple.com/documentation/os/ossignposter) | Named timed intervals in Instruments. Measure import/search/launch where users wait; wall-clock unit-test assertions alone are noisy. |
| 97 | [Pulse](https://github.com/kean/Pulse) | Local logs/network inspection; MIT framework, separate Pulse Pro Mac app. Useful support export; scrub credentials/content before sharing. |
| 98 | [Sentry Cocoa](https://github.com/getsentry/sentry-cocoa) | Crash/performance reporting SDK; hosted service cost/privacy and debug-symbol delivery are separate from SDK availability. README main is v9 development, v8 release branch. |
| 99 | [PLCrashReporter](https://github.com/microsoft/plcrashreporter) | In-process crash report generation; macOS 11.5+ in current README. Collector, delivery, consent and symbolication still needed. App Center retirement does not itself prove this library retired. |
| 100 | [Swift Testing](https://developer.apple.com/documentation/testing) | Modern parameterized/unit tests in Swift packages/Xcode. XCTest/XCUIAutomation still needed for UI workflows. |
| 101 | [XCTest / XCUIAutomation](https://developer.apple.com/documentation/xctest) | UI/performance and existing unit suites. Test menus, keyboard, multiwindow and permission/relaunch paths, not only model code. |
| 102 | [SnapshotTesting](https://github.com/pointfreeco/swift-snapshot-testing) | Image/value snapshots; MIT. Freeze relevant OS/font/render settings; snapshots do not establish interaction or accessibility. |
| 103 | [Quick / Nimble](https://github.com/Quick/Quick) | BDD organization/expectation style; Quick Apache 2.0. Existing suites can retain them; Swift Testing/XCTest often avoid an extra DSL for new work. [Nimble](https://github.com/Quick/Nimble) |
| 104 | [Swift Clocks](https://github.com/pointfreeco/swift-clocks) | Controllable time for debounce/retry/timer tests; MIT. Better than real sleeps when behavior depends on time. |
| 105 | [SMAppService / LaunchAtLogin-Modern](https://github.com/sindresorhus/LaunchAtLogin-Modern) | Native service management or tiny SwiftUI wrapper, macOS 13+. Legacy wrapper only for older support needs. |
| 106 | [StoreKit](https://developer.apple.com/documentation/storekit) | Apple purchases/transactions/restoration. Direct licenses need their own model; do not equate a successful payment UI with persistent entitlement correctness. |
| 107 | [Sparkle 2](https://sparkle-project.github.io/) | Direct-distribution updates, MIT; current site macOS 12+. EdDSA plus Apple signing; named consumers include Things, Nova, DaisyDisk and NetNewsWire. Store distribution uses store updates. |
| 108 | [notarytool / stapler](https://developer.apple.com/documentation/security/notarizing-macos-software-before-distribution) | Apple direct-distribution notarization/ticket tools; integrate final signed artifacts and inspect logs. Not an App Review substitute. |
| 109 | [create-dmg](https://github.com/sindresorhus/create-dmg) | Opinionated DMG generation. Packaging polish is useful; installer image does not provide signing/update security. Distinguish this project from similarly named scripts. |
| 110 | [fastlane](https://github.com/fastlane/fastlane) | Release/signing/store automation, MIT. Ruby/tool-version ownership; shell+xcodebuild/notarytool may be simpler for one direct-distribution utility. |
| 111 | [Electron](https://github.com/electron/electron) | MIT framework, documented VS Code use; bundled Chromium/Node and regular security updates. Current README macOS Ventura+. Native menus/dialogs still need deliberate implementation. |
| 112 | [Tauri](https://github.com/tauri-apps/tauri) | Rust+system webview, MIT/Apache 2.0; current README macOS 10.15+. Smaller runtime strategy, more WebKit-version variability and native plugin work. |
| 113 | [Flutter desktop](https://docs.flutter.dev/platform-integration/desktop) | Shared Dart/rendering stack; verify every plugin supports macOS. Native executable is not native-control parity. |
| 114 | [Qt](https://doc.qt.io/qt-6/macos.html) | Mature C++ cross-platform desktop toolkit; LGPLv3/commercial, with some GPLv3-only open-source modules; inspect exact modules. Current Qt 6.12 runtime floor 14.4; older branches differ. [License map](https://doc.qt.io/qt-6/licensing.html) |

## Named technologies to avoid, migrate or constrain

Statuses checked 2026-11-07. “Avoid” below always has scope; none is a claim that every existing use must be rewritten immediately.

| Choice | Status, failure mode, replacement, exception |
| --- | --- |
| AFNetworking | **Avoid new work; plan legacy ownership.** Owner deprecated it Jan 17 2023, no further releases. URLSession or Alamofire; Objective-C legacy may vendor/fork under its license while testing/security ownership remains explicit. [owner README](https://github.com/AFNetworking/AFNetworking) |
| Atlas Device Sync / Atlas Device SDK backend integration | **Migrate.** Owner says SDK EOL/removal Sep 30 2025; Sync/auth-related services affected. Choose another sync/auth design. Local Realm is a distinct case: open-source database continues; Swift README points to v20/community without Sync. Do not call all Realm unusable. [MongoDB deprecation](https://www.mongodb.com/docs/atlas/device-sdks/deprecation/), [Realm Swift](https://github.com/realm/realm-swift) |
| New CocoaPods Trunk dependence | **Avoid for new work when SPM/manual alternative exists.** Owner plan: Nov 2–6 2026 read-only test, permanent Dec 2 2026; dates explicitly revisable. Existing resolution remains, private specs/vendored dependencies differ. Do not claim permanent freeze already happened on Nov 7. [plan](https://blog.cocoapods.org/CocoaPods-Specs-Repo/) |
| `altool` notarization | **Replace.** Notary service stopped accepting it Nov 1 2023. Use `notarytool` or supported Xcode. This is notarization-specific; do not generalize to every similarly named upload flow. [Apple](https://developer.apple.com/documentation/security/notarizing-macos-software-before-distribution) |
| OpenGL for new Mac rendering | **Avoid new platform-specific renderer.** Deprecated since 10.14; choose Metal or a maintained abstraction. Existing cross-platform rendering can retain it temporarily with tested constraints; deprecation is not proof of removal. [Apple archived guide](https://developer.apple.com/library/archive/documentation/GraphicsImaging/Conceptual/OpenGL-MacProgGuide/opengl_intro/opengl_intro.html) |
| `NSUserNotification` | **Avoid new use.** Apple marks deprecated and directs to User Notifications. Existing older-target code may retain a bounded compatibility path. [Apple](https://developer.apple.com/documentation/foundation/nsusernotification) |
| Legacy key-based `NSAccessibility` | **Avoid as new default.** Apple recommends method-based `NSAccessibilityProtocol`; a few old methods remain relevant and can coexist. [Apple](https://developer.apple.com/documentation/appkit/nsaccessibility) |
| Legacy LaunchAtLogin helper when minimum is 13+ | **Unnecessary compatibility burden.** Owner recommends modern version; old package remains legitimate for 10.13–12 and already switches to SMAppService on 13+. [old package](https://github.com/sindresorhus/LaunchAtLogin), [modern](https://github.com/sindresorhus/LaunchAtLogin-Modern) |
| App Center as new infrastructure | **Avoid new commitment; migrate by feature.** Build/test/distribution retirement March31 2025. Apr15 2026 owner update extends Analytics/Diagnostics to March31 2027. Alternatives: own CI/Xcode tooling, supported telemetry service or Microsoft’s stated migration path; validate Mac coverage rather than assuming mobile support. [Microsoft](https://learn.microsoft.com/en-us/appcenter/retirement) |
| MarkdownUI as assumed active new-feature engine | **Context-dependent.** README now says maintenance mode, development moved to Textual. Textual is MIT and its current manifest requires macOS 15/Swift tools 6.0; it is not a drop-in lower-OS replacement. Stable existing rendering does not require a cosmetic rewrite. [owner](https://github.com/gonzalezreal/swift-markdown-ui), [Textual](https://github.com/gonzalezreal/textual), [manifest](https://github.com/gonzalezreal/textual/blob/main/Package.swift) |
| NukeExtensions for new image-view integration | **Superseded within a viable project.** Owner calls it soft-deprecated; use NukeUI `ImageLoader`. Nuke itself remains active, with released/dev requirements separated. [owner](https://github.com/kean/Nuke) |
| STTextView assumed to be permissive | **License mismatch risk, not bad software.** Current README GPLv3 or commercial. Closed-source product must select a compatible license/design; `NSTextView` or a suitable permissive editor is an alternative. [owner](https://github.com/krzyzanowskim/STTextView) |
| CodeEditTextView as universal text editor | **Wrong fit for full text-system parity/RTL.** Owner explicitly narrows use to line-oriented cases; `NSTextView` or evaluated STTextView for those needs. [owner](https://github.com/CodeEditApp/CodeEditTextView) |
| Unbounded SwiftUI introspection | **Fragile usage, viable library.** Explicit OS opt-in exists because underlying types may change. Prefer native APIs; isolate and test introspection on each OS instead of globally traversing internal view hierarchies. [owner](https://github.com/siteline/swiftui-introspect) |
| Old Electron frozen to preserve an OS floor | **Security/support trap.** Framework/Chromium/Node updates are app-owner responsibility. Retire old OS with a clear policy or fund backports; do not silently freeze internet-facing code. Electron remains viable when maintained. [security guide](https://www.electronjs.org/docs/latest/tutorial/security) |
| Electron with Node integration in untrusted content | **Unsafe architecture.** Keep remote/untrusted content away from privileged Node APIs; use sandbox/context isolation and narrow IPC. Native shell does not provide browser-level safety automatically. [security guide](https://www.electronjs.org/docs/latest/tutorial/security) |
| Tauri assuming one modern WebKit everywhere | **Compatibility trap.** System webview differs across supported OS versions; test feature support/fallbacks. Tauri remains viable for teams accepting that matrix. [engine reference](https://v2.tauri.app/reference/webview-versions/) |
| SwiftData merely because it is newest | **Requirement mismatch, not deprecated.** Minimum 14; prove schema evolution, recovery and concurrency on supported versions. Core Data/GRDB may better fit older targets or explicit SQL. [SwiftData](https://developer.apple.com/documentation/swiftdata), [GRDB](https://github.com/groue/GRDB.swift) |
| Calling all Carbon use obsolete | **Incorrect blanket rule.** KeyboardShortcuts explains its remaining Carbon global-hotkey use; do not replace working shortcut registration with permission-heavy event taps solely because of framework age. Verify the specific symbol’s status. [owner rationale](https://github.com/sindresorhus/KeyboardShortcuts) |
| Old release date as abandonment proof | **Invalid selection heuristic.** Look for owner notices, compiler compatibility, security issues, consumer needs and reproducible builds. GRDBQuery/SwiftGen may have older releases yet useful maintained scope; this survey did not establish their entire issue health. [GRDBQuery](https://github.com/groue/GRDBQuery), [SwiftGen](https://github.com/SwiftGen/SwiftGen) |

## Integration recommendations and limits

Prioritize proving the data/editor path, then native commands/focus/undo, then OS/architecture/distribution matrix. Add libraries for concrete missing behavior. A dependency’s minimum OS, Swift compiler, macro/build-plugin requirements, binary CPU slices, license and privacy manifest can each independently break an otherwise valid app target. Runtime feature detection and compile-time availability solve different problems.

No public evidence inspected here establishes a statistically representative “most used Mac indie libraries” ranking, aggregate OS install base, or an optimal universal deployment floor. Repository ownership/docs, named consumer examples and real app compatibility policies support selection and cost analysis, not market-share rankings. No package was compiled or benchmarked in this research; validate the actual pinned dependency graph for a product before calling it supported.


## What to build first

These are research recommendations. Product scope, architecture defaults and rollout choices still belong to the product's requirements.

1. **Prove one repeated job.** Observe how the intended users do it now. Measure completion and return use, not merely launch-day downloads. Default Folder X's long-term accounts show how a small repeated improvement can matter; the contrary accounts show why it is not valuable to everyone.
2. **Choose the app's posture.** A persistent notes workspace needs different navigation from a transient launcher or background rule engine. Sketch the normal task, quick interruption and failure state before choosing chrome. Use the visual families above as coherent starting points.
3. **Prove the risky native interaction.** Build the editor/IME path, selection model, file access, capture permission or focus lifecycle first. If that is unreliable, adding branded animation only increases the eventual rewrite. Choose AppKit/SwiftUI boundaries from this evidence.
4. **Protect the work.** Establish local persistence, undo, import/export, migration and recovery before broad sync or automation. Explicitly distinguish local save, remote sync, backup and export. A green cloud is not evidence of all four.
5. **Finish the normal Mac vocabulary.** Menus, keyboard commands, selection, text editing, drag/drop, windows, settings and accessibility are expected basics. Use the component reference as task-based acceptance criteria. Test with real data and interruptions, not only clean screenshots.
6. **Add a few earned differentiators.** Quick capture, durable deep links, Spotlight, Shortcuts, rule previews, cross-app paste or an excellent inspector can compound daily value. Choose the ones users repeat. Each extra service integration creates permission, support and compatibility work.
7. **Make buying and updating dependable.** Explain trial/ownership/renewal, test purchase presentation on supported OS releases, restore entitlements and preserve data at expiry. Type's payment-sheet incident shows how a distribution opportunity can be lost to presentation failure.
8. **Fund maintenance and measure sustainability.** Track net receipts, refunds, support time, ongoing services and owner labor. MacUpdater demonstrates the cost of maintaining a useful catalog; Panaitiu's account distinguishes customer payments from livelihood. Test pricing against the actual audience, with uncertainty when cohorts are small.

### Expected basics, differentiators and traps

| Priority | Build or investigate | Evidence and boundary |
|---|---|---|
| Expected | Fast invocation, correct editing/selection, responsive resize, clear errors, accessible controls, recoverable data | HIG conventions plus Things' shipped regression fixes; no universal millisecond budget inferred |
| Expected | Honest support matrix, signed release, reliable updates and permission recovery | Owning platform docs and real compatibility policies; direct/MAS variants differ |
| Useful differentiator | Capture from another app, meaningful automation, durable object links | Things, Alfred, Hookmark and Omni; valuable only for repeated workflows |
| Useful differentiator | Purposeful detail and restrained motion | Direct visual examples and documented designer choices; neither proves retention lift |
| Costly trap | Recreating the Mac text system for appearance alone | IME, selection, responder, pasteboard and accessibility obligations recur throughout this report |
| Costly trap | A cloud service, app catalog or external integration priced as zero future work | MacUpdater and Transmit Google Drive cases; ongoing work is product-specific |
| Costly trap | Perpetual maintenance promise without capacity planning | Lifetime updates can be a viable offer, but public examples do not disclose its economics for a new app |
| Test | Trial length/start, free mode, direct/store channel, purchase explanation | Hall and Type provide cohort observations; randomized causal evidence remains unavailable here |
| Test | More density, personalization, richer metadata, new panels | Observe representative work and accessibility settings; do not optimize only a pristine screenshot |

### A small-team quality gate

Complete a representative task with keyboard only, a mouse and a trackpad; compose non-Latin text; use VoiceOver; resize to the supported minimum; move between displays; switch appearance and accessibility settings; interrupt network and disk access; reopen after quitting; upgrade an old real document/library; restore a purchase; export data and reopen it elsewhere. Add category-specific tests for screen capture, background rules, calendars or extensions. Automate high-risk repeatable paths; inspect visual and physical-input behavior on actual supported configurations.

This is a proposed product verification plan, not tests run during research. It turns the report's concrete conventions and failure evidence into acceptance work without claiming every library or app was audited.

## Sources and reading method

Citations beside each claim are the source record. The main source groups serve different purposes:

- **Current platform contract:** Apple's HIG, AppKit/SwiftUI/Foundation documentation, Xcode requirements and distribution guidance. Markdown endpoints were read directly when the HTML reader exposed only a JavaScript shell. Per-platform sections take precedence over nearby iOS examples.
- **Long-form platform reasoning:** selected pages of Apple's 1986 second-beta HIG draft; WWDC22, WWDC25 and WWDC26 transcripts. Historical conventions explain intent; current APIs, sizing and button order supersede obsolete details.
- **Independent assessment:** MacStories' Things review, Macworld's Default Folder X/TextExpander coverage, Nielsen, Prokopov and Gruber's menu critiques, and the MPU user discussion. Dates, sponsorship and self-selection limits remain beside their conclusions.
- **Maker evidence:** Cultured Code, Rogue Amoeba, Panic, Bear, Alfred, Omni, CoreCode, Bichon, Hall and Panaitiu. Product behavior, design intent and self-reported finances are labelled; they are not independent experiments or audited accounts.
- **Visual inspection:** four developer-published Mac screen images and sampled frames of a Things Mac demonstration. No current installed-app usability benchmark or measured animation timing was performed. An inaccessible secondary motion asset was replaced with an accessible first-party demo.
- **Market evidence:** dated US paid-chart snapshots plus public developer accounts. Paid rank is not gross revenue; empty/inaccessible public grossing routes and private direct-sale receipts prevent a defensible complete grossing ranking.
- **Technology evidence:** owning documentation, repository READMEs/manifests and explicit deprecation notices. Catalog entries describe fit and documented maintenance, not measured prevalence or a compiled dependency audit.

No general causal conversion law, private profitability ranking, universal OS floor or universal visual style can be extracted from these sources. The report instead supplies observed behavior, specific tradeoffs and testable recommendations; limitations remain beside the affected claims.
