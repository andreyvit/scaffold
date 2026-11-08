# Great Windows business, productivity and utility apps

Research completed 8 November 2026. Scope: Windows desktop apps for individual professionals and small teams, including business workflows, document/data tools, notes/tasks, launchers and system utilities. Enterprise deployment matters where customers require it. Games, server software and specialist creative suites are outside the main scope; relevant lessons are labelled comparisons.

Research recommendations do not change confirmed scaffold choices. Existing [values](../skills/scaffold/references/values.md), [changes and undo](../skills/scaffold/references/changes.md), [optional offline sync](../skills/scaffold/references/offline-sync.md) and [configuration](../skills/scaffold/references/app-config.md) provide shared reasoning, not a Windows framework mandate. Compare [macOS](macos-apps.md), [B2B web](b2b-saas-web-apps.md) and [tiny cross-platform utilities](tiny-cross-platform-utilities.md); this report owns Windows conventions and deployment tradeoffs.


## Read by decision

- [Quality and audience](#what-great-means-here), [working posture](#choose-the-working-posture-before-the-style), [good and poor UX](#great-and-poor-ux-evidence-and-disagreements).
- [App examples](#app-examples-strengths-costs-and-meanings-of-great), [free tools and maintenance](#free-utilities-and-maintenance-economics).
- [Visual directions](#visual-design-directions-and-resources), [screen compositions](#screen-and-task-compositions), [120 practical details](#specific-screens-and-components-120-paired-details).
- [Reliability](#reliability-trust-and-windows-citizenship), [business work under strain](#business-work-under-strain).
- [Conversion and pricing](#commercial-success-measurements-pricing-and-conversion), [distribution and economics](#distribution-and-full-economics), [failures](#failures-switching-and-continuity), [featuring](#being-featured-is-a-separate-outcome).
- [Stack fit](#technology-choices-and-stack-fit), [compatibility](#compatibility-and-supported-targets), [library catalog](#common-libraries-and-components), [avoid/migrate guidance](#named-technologies-to-avoid-migrate-or-constrain).
- [Build priorities and tests](#prioritized-build-guidance), [sources and limits](#sources-and-inspection-scope).

## What “great” means here

A great Windows work app makes a recurring job easier while preserving the user's control over files, windows, input and deployment. A polished surface matters, but users also experience startup, updates, slow shares, printer failures and years of accumulated configuration.

| Meaning | Evidence that supports it | Examples and limits |
|---|---|---|
| User love | Long-term accounts, voluntary recommendations/donations, relief from recurring friction | Everything's decade-long user account; selected reviews cannot establish representative satisfaction |
| Problem solving | A complete real workflow with less effort or fewer errors | Beyond Compare comparison/merge; NAPS2 scanning/OCR; PerfectTablePlan seating/printing |
| Downloads and retention | Acquisition plus repeat-use cohorts, separately measured | ShareX reports large cumulative downloads; they are not active-user counts or retention |
| Cash earned | Paid receipts, order value, edition/upgrade mix | PerfectTablePlan's edition and upgrade accounts; before/after results are not controlled causal estimates |
| Viable business | Revenue minus delivery/support/maintenance costs over time | PerfectTablePlan's claimed annual profitability; private costs and Windows-only margins are not audited |
| Maintainable code | Clear boundaries, small failure surfaces, serviced dependencies, tested migrations | Native and shared-UI stacks can both work; a framework name alone proves none of these |
| Featuring | A named award/editorial placement and its criteria/date | Store awards demonstrate recognition; changing editorial priorities differ from user or founder outcomes |

Evidence appears in the app, business and technology sections below. These meanings overlap but cannot be substituted for one another.

**Windows-specific constraints.** Desktop files and other applications are part of the workflow. Users may have precise mouse/keyboard habits, dense tables, snapped windows, mixed-DPI displays and managed work computers. Store distribution is one channel; direct installers and enterprise deployment remain relevant. Modern Fluent controls coexist with mature Win32/WPF tools. Support the chosen audience's actual environment rather than treating a Windows app as a web page with a close button.

**Audience boundaries.** For individual utilities, invocation speed and low idle cost may dominate. For daily business tools, data entry, bulk review, recovery and procurement can dominate. For team clients, identity, permissions and synchronization add costs. Creative apps appear only where capture/annotation or document workflows teach a relevant lesson. Mobile/web companions are compatibility/business tradeoffs, not a mandate to share UI.

## Choose the working posture before the style

A business workspace used for hours, a file-search window used for seconds and a background monitor need different defaults. *About Face 2.0* distinguishes sustained, transient, background and auxiliary desktop roles. Its enduring contribution is matching interaction cost to duration/frequency. Its maximized-window assumptions and tiny mouse-target advice reflect older desktops; do not copy those into touch, accessible or multi-monitor layouts. This report directly read the posture chapter, not the whole book. [Accessible chapter](https://flylib.com/books/en/2.153.1.43/1/).

Joel Spolsky's author-hosted *User Interface Design for Programmers* excerpt connects small surprises to loss of control. Use that as an inspection method: watch where an experienced Windows user presses a familiar key and gets an unexpected result. The 2001 Mac/Windows examples are historical; current behavior must come from current APIs and testing. [Book excerpt](https://www.joelonsoftware.com/2001/10/24/user-interface-design-for-programmers/).

Jeff Atwood's 2007 review praised *About Face* while explicitly describing earlier Windows-era examples as aging. This is useful evidence against treating a classic book as a current control specification. Read books for interaction reasoning, current platform docs for contracts, and shipped apps plus user reports for the costs of applying both. [Independent book critique](https://blog.codinghorror.com/the-three-faces-of-about-face/).

| Product posture | Build first | Tempting mistake | Success evidence to seek |
|---|---|---|---|
| Daily business workspace | Stable list/detail navigation, keyboard work, bulk actions, durable edits, import/export | Dashboard cards that consume the space needed for records | Completed real workflows, fewer corrective edits, repeat use by role |
| Document tool | Open/save identity, recovery, search, side-by-side comparison, print/export fidelity | Beautiful canvas with uncertain save state or proprietary lock-in | Successful round trips and restored work under interruption |
| Quick utility | Fast invocation, clear current target, one useful result, easy dismissal | Account/setup before first result; always-on resource cost hidden from users | Time from invoke to correct result, failed invocation rate, idle resource use |
| Background monitor/automation | Trustworthy state, pause/quit, bounded work, recovery after sleep | Notifications as the only status UI; silent privilege failures | Correct transitions after outages/reboots; explainable logs |
| Team client | Identity/workspace clarity, stale/offline states, permission changes, deployment | Local-looking edits that disappear when a token expires | Recovery from session expiry, policy denial and concurrent changes |

These are research-derived design starting points. They do not authorize every feature for every product.

## Great and poor UX: evidence and disagreements

Windows quality has several valid appearances. Files supplies rounded Fluent surfaces; Directory Opus supplies a dense configurable workbench; Everything supplies an almost bare search table; EarTrumpet fits a tiny system flyout. Choose according to the job. A large blank margin is neither inherently polished nor inherently wasteful. Inspect comparison-heavy work at realistic data volume.

The sharpest independent disagreement is aesthetic modernization versus repeated-use friction. Andrew Cunningham's 5 October 2021 Ars review welcomed cleaner Explorer commands but warned that unlabeled icons reduce recognition and hiding old extensions adds steps. This describes the Windows 11 launch, not today's exact shell. [Ars review](https://arstechnica.com/gadgets/2021/10/windows-11-the-ars-technica-review/)

A 2025 Files discussion contains reports of lag, failed copies, unexpected navigation and users uninstalling after trying the app. Several commenters praise appearance while rejecting operation speed or reliability; one reports two months of use. These are selected, unverified reports, not a defect-rate study or proof those bugs remain. They justify repeatable tests with large folders, previews, copy failures and restart, rather than declaring Files universally poor. [User discussion](https://www.reddit.com/r/Windows11/comments/1kfvq86/what_do_you_think_of_the_files_app_windows/)

Files v3's own 8 November 2023 announcement says commands stayed in familiar places during redesign; it added a speed graph and a background-residency option to improve startup, explicitly costing resources. This makes the tradeoff concrete: disclose warm-start helpers; benchmark cold and warm launches separately. Do not infer an inevitable WinUI performance problem. [Files v3](https://www.files.community/blog/posts/v3)

Scott Hanselman's December 2020 tools essay describes utilities used repeatedly, portable tools in a shared PATH, and dislike of tray clutter. Historical expert practice supports fast access and low interruption; it supplies no present-day adoption percentages. [Long-form tools essay](https://www.hanselman.com/blog/scott-hanselmans-2021-ultimate-developer-and-power-users-tool-list-for-windows)

Paul Thurrott's *Hands-On Windows 173* (22 January 2026) describes keyboard fluency as a way to reduce visible chrome and discusses shortcut collisions. This is an AI-generated published transcript, not verified verbatim audio; use as expert commentary. Its suggestion to use Win+Space conflicts with multilingual input-switching use, so do not turn that personal shortcut into a recommendation. [Transcript](https://twit.tv/posts/transcripts/hands-windows-173-transcript)

### Concrete regressions to test for

**Configuration loss can feel like a removed feature.** A ShareX user who reported using it since 2015 complained in 2024 that recent screenshots no longer appeared in the main window after reinstall, requiring a second history window. Replies found a setting. This supports testing reinstall/default migrations and discoverability; it does not prove a permanent removal or establish prevalence. [User discussion](https://www.reddit.com/r/sharex/comments/1ejd13d/sharex_no_longer_shows_recent_screenshots_each/).

**A privilege selector must match the launched process.** PowerToys issue #46669 reports version 0.98.1 launching a shortcut target elevated despite choosing Normal when PowerToys itself runs elevated. The issue was open and untriaged when read; this is a reproducible report to investigate, not a confirmed defect in every current release. Test child-process identity independently from the parent process and label the result accurately. [Issue, 31 March 2026](https://github.com/microsoft/powertoys/issues/46669).

**Modern visuals do not settle startup quality.** Files Preview 4.2.11's August 2026 release note still identifies startup optimization as ongoing. That demonstrates maintenance attention, not a measured speed comparison. Benchmark cold start, warm start and background residency separately before choosing a shell. [Release note](https://www.files.community/blog/posts/v4-2-11).

**A lightweight edition can remove essential access.** Everything's FAQ says Lite removes IPC, SDK/CLI integration and screen-reader support. Its name/content searches also differ: content search is not indexed and is slower. Treat these as product/edition boundaries, not a blanket accessibility or performance judgment about all Everything versions. [Developer FAQ](https://www.voidtools.com/faq/).


## App examples: strengths, costs and meanings of great

These are exemplars, not a financial ranking. Developer claims establish offered behavior; inspected screenshots establish appearance; independent accounts establish particular experiences. None proves profitability or retention.

- **Everything:** a query field above a dense result table, with paths, sizes, dates and count/status. Official documentation says filename search is indexed, offline and telemetry-free. Great at rational value and low interaction cost; conventional appearance may look old. Name search is not equivalent to indexed document-content search. [Product documentation](https://www.voidtools.com/support/everything/)
- **Directory Opus:** dual panes, tabs, viewer/metadata panels, queued copies, batch rename and extensive command customization. Great for repeated professional file work; configuration and dense surfaces impose learning cost. That cost is an inference from breadth, not a measured onboarding failure. Homepage currently explicitly excludes ARM support. [Developer](https://www.gpsoft.com.au/)
- **Files:** Fluent hierarchy, tabs, command palette and operation feedback. Strong appearance and command discoverability examples; selected reports above challenge repeated-use performance. Developer's background-process option shows the resource cost of hiding cold launch. [v3 announcement](https://www.files.community/blog/posts/v3)
- **OneCommander:** Miller columns, dual panes, previews, persistent tabs and batch tools create an alternative navigation model. Useful when deep hierarchies dominate. Its website recommends high-PPI displays; do not assume low-resolution usability from polished screenshots. Website claims performance; no benchmark performed here. [Developer](https://www.onecommander.com/)
- **ShareX:** capture → edit → copy/save/upload workflows, configurable after-capture actions and many destinations. Strong rational value and automation; configuration and automatic publishing need care. Its 34-million-download figure is a developer claim, not active users or revenue. [Developer](https://getsharex.com/)
- **EarTrumpet:** per-app volume, moving apps among playback devices, theme/accent support and configurable hotkeys. Strong example of a narrow utility fitting Windows. Source lists a 2022 Store award; see the featuring section. It is WPF: polished Windows behavior is not confined to WinUI. [Repository](https://github.com/File-New-Project/EarTrumpet)
- **Notepads:** Fluent tabs, Markdown/diff previews, CLI entry, session snapshots. Shows how a small editor can have distinctive polish. README explicitly warns of UWP system-folder/file-association restrictions and a 1 MB file limit. Treat those as documented product constraints, not a statement that all UWP editors share the limit. [Repository](https://github.com/0x7c13/Notepads)
- **Obsidian:** locally stored notes, themes/plugins, command discovery and named layouts. Great for user ownership and personal workflows. Plugin/setup choice can become work; that is a design risk rather than measured dissatisfaction. Its Ctrl+P command palette is a product-specific exception to conventional Print; do not copy blindly into business document apps. [Product](https://obsidian.md/), [palette](https://obsidian.md/help/Plugins/Command%2Bpalette), [workspaces](https://obsidian.md/help/plugins/workspaces)

- **PerfectTablePlan:** domain-specific inputs, seating optimization, offline execution, print output, one-off and professional editions. Strong evidence of sustainable owner business; limited collaboration compared with browser-first competitors; longevity is not proof that a new clone can buy traffic at historic prices.
- **Beyond Compare:** compare/merge/sync across text, folders, images and tables. Strong rational repeat-use value; independent reseller reviews include a 20-year user praising filters/integrations and another finding possibilities hard to discover. Neither the vendor's “popular” label nor 29 reseller reviews establishes market share. [Product](https://www.scootersoftware.com/), [reviews](https://www.componentsource.com/product/beyond-compare/reviews/).
- **Fences:** organizing a Windows desktop into groups/tabs and folder portals; business deployment offers value beyond cosmetic personalization. OS integration creates ongoing compatibility responsibility; users who rarely see the desktop have little reason to pay.
- **Paint.NET:** focused image editing and voluntary paid Store convenience. Excellent example of distribution-specific monetization; no verified private revenue here.
- **Snagit:** annotate-and-share workflow provides professional support/documentation value. Historical support practitioner explicitly used it; subscription policy attracts mixed long-term reactions. Bigger independent vendor, not a solo baseline.
- **Snipboard, September 2026 preview:** Windows Central's one-day hands-on liked paste transformations and per-app exclusions/temporary sync mode; wanted drag/drop supported by Edge Drop. Useful concrete polish comparison, not long-term reliability evidence. [Hands-on](https://www.windowscentral.com/software-apps/i-just-spent-a-day-with-stardocks-snipboard-a-promising-replacement-for-the-windows-11-clipboard).

## Business niches and document workflows

**Moon Invoice — recurring business records.** The Windows product covers estimates, invoices, receipts, expenses, purchase orders, credit notes, time tracking and reports; local offline storage reconnects through MoonSync. Its recurrence help, dated 4 April 2025, documents editable intervals and an end date, plus explicit disabling. Unlike a launcher, success requires correct durable records and repeat workflows. Product-specific design implications: distinguish draft/sent/paid states, show customer and currency, preview totals, expose next/last recurrence and prevent duplicate creation on retries. Those are research inferences, not observed bugs. Regional tax/legal requirements need separate verification. Vendor testimonials and support promises establish positioning, not measured satisfaction or independent outcomes. [Windows product](https://www.mooninvoice.com/online-windows-invoicing-software), [recurring-invoice instructions](https://help.mooninvoice.com/hc/en-us/articles/360001222166-How-to-set-up-a-recurring-Invoice-through-the-application).

**Easy Data Transform — repeatable reporting preparation.** Visual transformations, intermediate results and reusable batch workflows target people repeatedly cleaning spreadsheet/CSV data without scripting. Local processing matters for private datasets; show changed row counts, parsing errors and output paths rather than only a success toast. Its primary site advertises a one-time price from $99 and 60-day refund. The trial counts **seven days of use, which need not be consecutive**; afterward save/export is blocked. Indefinite named-user license covers up to three PCs/Macs for that user's use; organizational transferable licenses require a quote. Future major upgrades have a 90-day grace and stated 60% discount. The FAQ supports Unicode and local number/date formats. Vendor tests and testimonials do not establish independent performance or retention. [Product](https://www.easydatatransform.com/), [FAQ](https://www.easydatatransform.com/faq.html).

**PDF-XChange — document work and entitlement clarity.** The vendor distinguishes perpetual use from optional maintenance and per-user licensing from concurrent use. Free functions permit commercial use; using licensed functions without a valid key applies watermarks. Do not misstate this as every free export being watermarked. This is a case for clearly marking paid commands before users alter valuable documents, showing a preview, and preserving originals. [Licensing](https://www.pdf-xchange.com/licensing), [administrator licensing guide](https://help.pdf-xchange.com/sysadmin/licensing.html).

**A concrete perpetual-license recovery trap.** PDF-XChange's KB, updated **22 October 2026**, says prior-version installers remain downloadable for only **90 days after maintenance expires**. Existing keys remain valid for entitled older versions; a newer installation can produce watermarks. Staff explained the archive policy in December 2025, citing security and advising users to retain installers. Thus a perpetual entitlement is not a promise of perpetual installer availability. Explain use, update, support and recovery rights separately; retain a recovery path. A January 2026 user complaint called licenses self-destructing, but the primary evidence supports an installer-access restriction, not license expiration. [Current KB](https://www.pdf-xchange.com/knowledgebase/447-How-do-I-determine-what-version-I-should-installhow-can-I-retrieve-my-serial-key), [staff explanation](https://forum.pdf-xchange.com/viewtopic.php?t=41277), [complaint](https://www.reddit.com/r/pdf/comments/1qjszmv/pdfxchange_editor_is_selling_perpetual_licenses/).

**Love versus retention.** A separate PDF-XChange discussion includes claimed 20-year use and repeated weekly PDF-Tools use, with Explorer right-click scanning/rotation automation praised. Everything's decade-long user account, Beyond Compare's long-term reseller reviews and these concrete workflow accounts explain why users return. They do not provide denominators, inactive users or churn cohorts. PerfectTablePlan's upgrade percentages measure purchase behavior among eligible license holders, not daily active retention; a satisfied perpetual user may never upgrade. Do not rank user love by revenue, stars or anecdote count. [PDF-XChange users](https://www.reddit.com/r/pdf/comments/1uf7mtm/pdfxchange_editor_is_so_awesome/).

### Current Store policy check

Owning policy **version 7.20**, published 15 September 2026, effective **22 October 2026**, checked 8 November. Sections 10.8.1/10.8.6 permit secure third-party purchase/subscription APIs for non-game PC products. Third-party commerce has disclosure, authentication and confirmation requirements; it is not an exemption from Store review. Section 10.8.4 requires advance disclosure if a trial restricts access to user-created content. Sections 10.8.3/10.14 require a company account for primary functionality requiring financial information and for business-entity presentation. This particularly affects invoicing/accounting products compared with simple utilities. Section 10.8.2 has separate donation wording; do not extrapolate ordinary app purchases into a blanket rule for paid-benefit donations. Free company registration does not remove identity verification. [Current Store policies](https://learn.microsoft.com/en-us/windows/apps/publish/store-policies).

## Free utilities and maintenance economics

**Everything — daily usefulness and attachment, not proven commercial scale.** Its official documentation promises fast filename search, offline operation and no telemetry. John Seiffer's January 2023 Cool Tools review describes ten years' use, file operations directly from results and periodic donations; content search is slower than filename lookup. This is a concrete long-term account, not a benchmark. Donation history contains recurring appreciation and support payments but does not expose total expenses or a salary. Label Everything freeware rather than assuming open-source status. [Documentation](https://www.voidtools.com/support/everything/), [independent long-term review](https://kk.org/cooltools/everything/), [funding page](https://www.voidtools.com/donate/).

**ShareX — power-user workflows and community distribution.** The project offers capture, annotation, recording, OCR, custom upload destinations and configurable after-capture/after-upload tasks. It reports 34m downloads and 18 years' development. Its funding page says donations are its only income and it contains no ads. That shows a sustained project and a funding mechanism, not full-time wages or profitable company economics. Rich automation raises setup and accidental-upload risks: teach the active destination and outcome of each hotkey. No claim that a specific insecure default was observed. [Product](https://getsharex.com/), [funding](https://getsharex.com/donate).

**Ditto — narrow recoverable value.** The GPL-3.0 project saves clipboard text, images, HTML and custom formats to a database; a hotkey opens history and Enter pastes into the prior window. It explicitly promises no login/cloud/telemetry and credits free signing from SignPath Foundation. Value is fewer lost copies and less task switching. Retained clipboard content creates privacy/retention responsibilities; no private earnings available. Demonstrates one concrete way OSS can reduce Windows signing cost, not a service-level guarantee for all applicants. [Owning repository/readme](https://github.com/sabrogden/Ditto).

**Flow Launcher — keyboard continuity and extensibility.** The Windows 10+ project documents app/file/web/bookmark search, calculation and commands, with plugins and user-adjustable invocation hotkey. It can use Everything or Windows Search. Free/open-source distribution includes an explicit sponsorship route. Plugin breadth is useful for users with repeated workflows, but introduces configuration, hotkey collisions and third-party-code trust; these are integration costs, not a measured failure rate. Do not read sponsor logos or GitHub stars as sustainable income. [Product and sponsor route](https://www.flowlauncher.com/).

**Joplin — open-source notes plus paid operation.** The project supports local notes, rich text/Markdown, attachments, plugins and choice of sync services; paid Cloud adds managed synchronization/sharing, and Server Business offers a self-hosted business route. Its donation page explicitly names signing certificates, hosting, development/testing hardware and developer time as expenses. This is stronger cost evidence than the claim that open-source is free to maintain. Privacy-sensitive business buyers can value operating control, but self-hosting transfers operations to them. Do not treat server source availability as unrestricted licensing or assume encryption is configured solely from marketing copy. [Product](https://joplinapp.org/), [plans](https://joplinapp.org/plans/), [maintenance costs](https://joplinapp.org/donate/).

**NAPS2 — practical business/PDF utility.** Free, open-source scanning to PDF and image formats, OCR, page reorder/deskew, WIA/TWAIN choices and duplex/ADF support solve a concrete office job. This is a scanner workflow, not a complete Acrobat replacement. MSI deployment, preset profiles and manually deployed OCR languages make it useful on managed/offline PCs. Driver/scanner variation remains real support work. Its organization docs distinguish default settings from locked policy; the MSI disables donation prompts by default, while retaining an optional Donate button. That is unusually concrete corporate citizenship without withholding the basic workflow. [Product](https://www.naps2.com/), [organization deployment](https://www.naps2.com/doc/org-use).



**OSS economic lesson (inference from above).** Free distribution can create love, distribution and a useful public resource while leaving paid maintenance uncertain. Give donation/sponsorship an honest place; avoid obstructive prompts, especially on centrally managed workstations. Paid hosting, support, enterprise deployment and optional convenience are different revenue experiments; none is automatically available to a tiny utility with no recurring service need. Track maintainer time and dependency/update obligations even if infrastructure bills are low. A user can choose a brilliant free tool while the founder should choose a different commercial model.

## Visual design directions and resources

Published screenshots were directly inspected. Screens are publisher-selected, dates/version vary, and no live interaction performance was tested.

### 1. Fluent shell companion

**Inspected:** Files v3 sidebar image from its 2023 announcement. Pale wallpaper-tinted shell, separate near-white rounded content surface, thin outline icons, colored folder/file art, generous rows, a short colored active-location marker and tab-strip continuity. Bold section labels separate locations; small pin icons carry state. This direction fits approachable Windows utilities and settings-heavy apps. Risks: too much padding on business tables; low-opacity layers reducing contrast; unlabeled toolbar icons; mixing arbitrary radii with native menus. Preserve system contrast and solid-material fallbacks. [Inspected Files image](https://www.files.community/blog-resources/v3/Sidebar.webp)

Mica is a window backdrop, not live blurred content. Microsoft's implementation supplies solid fallbacks for contrast settings, battery saver, hardware and older Windows. A portable or cross-platform rendering stack should not promise identical translucency everywhere. [Mica](https://learn.microsoft.com/en-us/windows/apps/design/style/mica)

### 2. Dense professional workbench

**Inspected:** Directory Opus homepage image: narrow folder tree, detailed file list, preview above an editable metadata panel, two compact toolbar rows, visible menus, status information and small colored icons. It allocates pixels to simultaneous comparison and action. This direction fits file management, accounting, developer tools and substantial datasets. Costs: more hierarchy work, keyboard paths and configurable columns; novice users need a strong default. Do not ship every command visible merely because power users can hide it. The inspected promotional image's version is unspecified; use it as layout evidence, not proof of current default styling. [Inspected Opus image](https://www.gpsoft.com.au/assets/img/advanced-feature-1.jpg)

### 3. Minimal instrument

**Inspected:** Everything support screenshot: standard caption buttons, menu bar, one full-width search field, four compact sortable columns, blue selected row and a count/path status strip. It avoids a dashboard and illustrations. This direction fits search, conversion, inspection and single-job tools. Brand can live in icon, naming and precise feedback. Costs: a generic appearance and an easy temptation to undersize text. Preserve scaling and accessible contrast. The screenshot proves compactness, not speed. [Inspected Everything image](https://www.voidtools.com/support/everything/Everything.Search.Window.png)

### 4. Focused system flyout

EarTrumpet's documented model concentrates on the app/audio-device relationship rather than a large home screen: levels, devices and direct routing. Fit: quick adjustment beside other work. Use system theme/accent, a small predictable entry point and a clear path to more options. Cost: focus, dismissal, keyboard operation and tray overflow must work; a tiny flyout must not become a second settings application. This direction is based on repository feature descriptions, not direct flyout image inspection. [EarTrumpet](https://github.com/File-New-Project/EarTrumpet)

### Practical design resources

- [WinUI Gallery](https://github.com/microsoft/WinUI-Gallery): executable controls/states plus source; inspect keyboard, focus, disabled and narrow-window behavior before drawing a custom replacement. Windows-specific; a gallery is not a complete information architecture.
- [Windows typography](https://learn.microsoft.com/en-us/windows/apps/design/signature-experiences/typography): Segoe UI Variable, optical sizing, text hierarchy and casing. Use system fonts under their distribution terms; do not assume a Windows font can be bundled on every platform.
- [Fluent System Icons](https://github.com/microsoft/fluentui-system-icons): MIT repository; regular/filled families and size variants. Match stroke, optical size and state; an icon font without accessible names is insufficient.
- [Windows layering](https://learn.microsoft.com/en-us/windows/apps/design/signature-experiences/layering): distinguish navigation base, content and temporary surfaces. Useful design grammar; not a requirement to put every field in a card.
- [Windows motion](https://learn.microsoft.com/en-us/windows/apps/design/signature-experiences/motion): continuity, consistent entry/exit and input response. Read text and sampled the official motion GIF as described below. Test interruption and animation-disabled settings before claiming polish.
- [Legacy UXGuide](https://learn.microsoft.com/en-us/windows/win32/uxguide/vis-layout): rich good/bad layout and control examples, explicitly Windows 7-era. Useful for semantics and alignment; stale for Windows 11 dimensions, visual assets and materials.
- Files, EarTrumpet and Notepads repositories give shipped-app source and issue discussions. Their licenses and dependency obligations still need checking before reuse; studying a screenshot grants no asset license.
- Independent critiques above supply disagreement missing from official galleries. Generic Dribbble/Mobbin-style web galleries are weak evidence for Windows keyboard, shell or lifetime behavior; no paid catalog was inspected here.

### Recorded motion inspection

Downloaded Microsoft’s [consistency GIF](https://learn.microsoft.com/en-us/windows/apps/design/signature-experiences/images/motion-consistent.gif), inspected 13 evenly spaced frames of its 400-frame animation. Start, search, task view and input flyouts appear above their taskbar entry points; intermediate frames show surfaces emerging from or returning toward that edge. This illustrates spatial consistency, not a fresh recording of current Windows or a frame-time benchmark. Frame sampling cannot establish perceived smoothness. The recording shows an older Windows 11 shell; apply the motion relationship, not every pictured control.

## Screen and task compositions

These are proposed compositions derived from the evidence above, not screenshots of a new product or confirmed recipes. Details below supply the control-level rules.

**First useful session.** Open the relevant working surface: a file picker/recent documents for an editor, focused search for a launcher, or a short import/create choice for a business tool. Explain only the capability needed now. Keep sample data visibly separate from real data. A local utility need not block on an account; cloud collaboration may legitimately require identity. Do not show a decorative dashboard before users can do the advertised job. This applies Spolsky's task/default argument and Everything's single-purpose entry.

**List → inspect → act.** Place locations/filters at left, a sortable data list centrally, and an optional detail/preview pane at right. Show scope and selection count near batch commands. Preserve selection while users inspect details. On narrow windows, make the detail view replace the list with an obvious return path; restore its selection/scroll state. Tables suit comparison; thumbnails suit visual recognition. Directory Opus and Everything illustrate different ends of this density choice.

**Document work.** Use document tabs for independent files, stable editing commands, visible save/failure state and a quiet status line for relevant facts. Reserve the main canvas for content. Search/replace and preview should allow repeated document interaction. Explicit export differs from saving the source document. Obsidian workspaces illustrate saved arrangements; Notepads shows small-editor preview/diff capability alongside explicit file limits.

**Configure a utility.** Group settings by user job, with descriptions only where consequence is unclear. Use immediate switches for ordinary reversible preferences, transactional forms for coupled changes, and a separate diagnostics/About area with version and support links. Show running/background state and which shortcuts are assigned. Advanced capability can justify many settings; Microsoft's suggestion of very few settings is not a useful literal cap for professional tools.

**Long batch operation.** Keep an operation center beside useful work: queued/running/failed items, actual progress, destination, pause/stop where safe, and a durable result summary. Confirm overwrite consequences before bulk replacement. Display partial completion honestly; distinguish retrying failures from repeating already-successful work. File-manager complaints make this a reliability task, not merely a progress-animation exercise.

**Buy, recover and leave.** A license screen should state edition, seat/device scope, whether current-version use survives cancellation, update entitlement and recovery route. Show trial limitations before the user invests work. Keep export and local data access intelligible when billing changes. These are product-design inferences from the Beyond Compare, Fences, Snagit and shutdown cases below; exact refund/billing terms belong to that evidence, not universal policy.

## Specific screens and components: 120 paired details

Evidence labels identify each group’s source basis: **M** current Microsoft guidance; **H** historical Windows guidance retained for behavior, not styling; **E** shipped-app example; **I** research inference. The paired failure consequences and implementation advice are research synthesis unless explicitly attributed; a group marked M does not mean Microsoft stated every sentence. These are scoped choices, not a requirement to put every component into every app.

### Window chrome — M

Source for 1–5: [Title bar design](https://learn.microsoft.com/en-us/windows/apps/design/basics/titlebar-design).

1. **Drag space.** Leave empty title-bar regions draggable. A full-width custom toolbar can accidentally make moving the window difficult; interactive controls must remain clickable.
2. **Caption controls.** Keep minimize, maximize and close visible at narrow widths. Truncate document titles before hiding window controls.
3. **System gestures.** Preserve title-bar double-click maximize/restore and right-click system menu. A custom painted header should not erase learned window handling.
4. **Inactive windows.** Distinguish active/inactive chrome without dimming readable content into illegibility. Users compare multiple windows; focus must remain apparent.
5. **Title-bar search.** Reserve sufficient height and responsive width for integrated search. Do not squeeze it between caption buttons until text or drag space disappears.

### Keyboard and focus — M

Source for 6–10: [Keyboard interactions](https://learn.microsoft.com/en-us/windows/apps/develop/input/keyboard-interactions).

6. **Tab order.** Follow reading/task order. Avoid focus jumping across columns because visual rearrangement and logical order diverged.
7. **Groups.** Use Tab between familiar lists/radio groups and arrows within them. Retain individual button tab stops where assistive conventions expect them.
8. **Initial focus.** Start on the useful first action, such as search or document content. A focused Help link wastes the first keystroke.
9. **Focus visibility.** Retain a visible keyboard focus indicator. Selection and focus are distinct; a selected row alone may not identify the active control.
10. **Two shortcut paths.** Provide accelerators for frequent commands and discoverable access keys/navigation. Shortcuts alone do not make the entire UI keyboard-operable.

### Navigation and tabs — M

Sources: [NavigationView](https://learn.microsoft.com/en-us/windows/apps/develop/ui/controls/navigationview), [TabView](https://learn.microsoft.com/en-us/windows/apps/develop/ui/controls/tab-view).

11. **Few destinations.** Top navigation can suit a handful of equal destinations. Avoid an icon-only left rail when category labels carry the meaning.
12. **Many destinations.** A left pane accommodates more categories. Collapse adaptively in narrow windows; do not force phone navigation on a wide desktop.
13. **Stable destinations.** Keep top-level navigation distinct from commands on current content. A Delete action disguised as a destination makes navigation hazardous. (inference)
14. **Document tabs.** Use closable/reorderable tabs for user-opened documents. Fixed settings categories should not pretend to be disposable documents.
15. **Closing tabs.** Select another tab after closing or detaching the active one. A blank content area with remaining tabs breaks continuity.

### Menus and commands — H

Source for 16–20: [Windows 7 menus](https://learn.microsoft.com/en-us/windows/win32/uxguide/cmd-menus). Retain semantics; modern WinUI controls may differ visually.

16. **Command labels.** Use specific verbs and familiar names. A novel word for Copy or Rename costs recognition without adding capability.
17. **Menu icons.** Use familiar icons where they speed recognition. Filling every menu row with a cryptic pictogram adds clutter rather than meaning.
18. **Context.** Put object-specific commands in its context menu. Avoid a giant repeated application menu unrelated to the clicked item.
19. **Submenus.** Group genuinely related commands. Deep cascading paths trade clutter for pointer precision and search effort.
20. **Disabled commands.** Preserve temporarily unavailable menu-bar items. Context menus may omit irrelevant commands; keep expected standard commands so their absence does not confuse.

### Layout and grouping — H

Source for 21–25: [Layout](https://learn.microsoft.com/en-us/windows/win32/uxguide/vis-layout).

21. **Aligned labels.** Align comparable labels and input edges. Arbitrary offsets force repeated eye movements and make equal fields look unrelated.
22. **Proximity.** Put related controls closer than unrelated groups. Decorative group boxes cannot repair contradictory spacing.
23. **Baseline.** Align text baselines across a row. Aligning rectangles alone can leave captions visibly uneven.
24. **Resize purpose.** Give additional space to lists, editors and previews. Stretching every button creates emptiness without exposing more useful data.
25. **Localization.** Size by content and layout rules, not English screenshots. Longer labels and larger fonts must not collide with controls.

### Tables and selection — H

Source for 26–30: [List views](https://learn.microsoft.com/en-us/windows/win32/uxguide/ctrl-list-views).

26. **Sort correctly.** Sort numbers numerically and dates chronologically. Lexical ordering makes business data misleading.
27. **Saved columns.** Persist useful per-user column order, widths and sorting per view. Reverting daily setup makes customization hollow.
28. **Selection visibility.** Keep selected rows recognizable when focus moves to details. Otherwise users lose the object being inspected.
29. **Multi-selection.** Support Ctrl/Shift conventions; add checkboxes when selection stability or discoverability matters. One stray click should not casually erase expensive selection work.
30. **Activation.** Single-click selects; double-click invokes the default command where appropriate. Keep another visible or menu route so double-click is never the sole access path.

### Text and forms — H

Source for 31–35: [Text boxes](https://learn.microsoft.com/en-us/windows/win32/uxguide/ctrl-text-boxes).

31. **Copyable output.** Use selectable output for paths, IDs and diagnostics. Read-only need not mean impossible to copy.
32. **Pasting.** Keep long tokens and addresses pasteable as a whole. Splitting a license key into tiny fields can obstruct the likely input method.
33. **Flexible formats.** Accept plausible spaces/punctuation where safe. Arbitrary US-only constraints exclude valid international input.
34. **Selection intent.** Select all when replacement is likely; preserve useful caret placement for editing. One rule does not suit passwords and appended notes alike.
35. **Input width.** Give expected content enough room. A wide window with a tiny path field wastes space and hides mistakes.

### Checkbox and switch semantics — H/M

Sources: [Checkboxes](https://learn.microsoft.com/en-us/windows/win32/uxguide/ctrl-check-boxes), [Toggle switches](https://learn.microsoft.com/en-us/windows/apps/develop/ui/controls/toggles).

36. **Independent choices.** Checkboxes select zero or more independent options. Mutually exclusive alternatives need radios or a single-choice list.
37. **Clear opposite.** A checkbox label must make the unchecked state obvious. “Landscape” hides “Portrait”; name both alternatives when ambiguity matters.
38. **Mixed value.** Indeterminate means selected objects disagree. Do not use it as an unexplained third state such as “service missing.”
39. **Immediate switch.** A switch should take effect when changed. A switch that silently waits for Save contradicts its physical-switch meaning.
40. **Committed selection.** Prefer checkboxes for options applied by Submit/Next. Preserve transactional forms even though ordinary preference switches can save immediately.

### Settings — M

Source for 41–45: [App settings](https://learn.microsoft.com/en-us/windows/apps/design/app-settings/guidelines-for-app-settings).

41. **Stable entry.** Put settings at the bottom of NavigationView or a predictable toolbar/overflow location. Do not scatter global preferences across unrelated screens.
42. **Workflow commands.** Keep frequently adjusted working controls beside the task. Burying brush size or active filters in Settings adds repeated travel.
43. **Immediate feedback.** Apply ordinary preferences immediately. If a change requires restart or validation, communicate that exception rather than implying it already worked.
44. **Theme choice.** Offer system, light and dark when overriding appearance is useful. Hardcoded dark mode ignores the user's environment.
45. **Grouped cards.** Use concise headers, descriptions and aligned action controls. Avoid deeply nested expanders; a long professional settings area also needs navigable structure.

### Search and command discovery — M/E

Sources: [AutoSuggestBox](https://learn.microsoft.com/en-us/windows/apps/develop/ui/controls/auto-suggest-box), [Obsidian palette](https://obsidian.md/help/Plugins/Command%2Bpalette).

46. **No result.** State when a submitted suggestion search finds nothing. An empty popup can look like a broken or unfinished request.
47. **Suggestion versus execution.** Distinguish text changes, suggestion choice and query submission. Highlighting a suggestion should not accidentally execute a destructive operation. (inference)
48. **Keyboard suggestions.** Keep displayed suggestion text and accepted text consistent. Arrow-key browsing should not produce a surprising replacement.
49. **Fuzzy command search.** Match likely abbreviations where command discovery benefits. Keep exact labels and keyboard hints visible rather than requiring memorized magic strings. (inference)
50. **Pinned commands.** Let repeated users pin or quickly recall actions. Personal ordering should supplement search, not silently move dangerous actions under familiar keys. (inference)

### Dialog choices — M

Source for 51–55: [Dialog controls](https://learn.microsoft.com/en-us/windows/apps/develop/ui/controls/dialogs-and-flyouts/dialogs).

51. **Concrete question.** State the decision in the first line. A generic “Warning” title and technical paragraph slow recognition.
52. **Action buttons.** Prefer “Replace” and “Keep both” to ambiguous Yes/No. Buttons should answer the actual question without rereading prose.
53. **Safe exit.** Provide a nondestructive Close/Cancel action. A confirmation that offers only irreversible choices is not meaningful control.
54. **Windows ordering.** Current ContentDialog guidance puts action buttons left and the safe close action right. Do not copy macOS button order by habit.
55. **Inline validation.** Show field errors beside their input. A modal error for every malformed field interrupts correction and separates cause from remedy.

### Dialog lifetime — H

Source for 56–60: [Dialog boxes](https://learn.microsoft.com/en-us/windows/win32/uxguide/win-dialog-box).

56. **Owner relationship.** Initially place a dialog over its owner and keep it on a visible monitor. A hidden dialog makes the app seem frozen.
57. **Close semantics.** X closes/cancels rather than invoking OK. In modeless settings, closing does not undo changes already applied; make that distinction clear.
58. **Modality.** Use modeless tools for repeated inspection and modal dialogs for decisions that must finish first. A modal Find window obstructs document work.
59. **Stop versus Cancel.** Say Stop if partial results remain; Cancel implies rollback. Bulk operations need honest labels and a result summary.
60. **Focus stealing.** Background-triggered dialogs should not capture another app's typing. Signal attention and let the user activate the window.

### Loading and progress — M

Source for 61–65: [Progress controls](https://learn.microsoft.com/en-us/windows/apps/develop/ui/controls/progress-controls).

61. **Known progress.** Show determinate progress when completed work can be measured. An endless spinner hides useful information.
62. **Unknown progress.** Use indeterminate feedback when completion is unknown. Fabricated percentages create false confidence and sticky “99%” endings.
63. **Local blocking.** Keep unaffected work usable while background work proceeds. A whole-window overlay for one small panel wastes concurrency.
64. **Explain activity.** Name the current operation when animation alone is ambiguous. “Connecting” and “Importing” imply different remedies.
65. **Quiet background work.** Do not animate every invisible maintenance task. Feedback must earn attention; visible user-triggered waits need acknowledgment.

### Persistent status and errors — M

Source for 66–70: [InfoBar](https://learn.microsoft.com/en-us/windows/apps/develop/ui/controls/infobar).

66. **Persistent failure.** Keep offline or autosave-failure status visible until resolved or acknowledged. A fleeting toast can hide continued data risk.
67. **Recovery action.** Put a relevant retry/sign-in action beside changed app state. A warning without a next step leaves users stranded.
68. **Avoid flashing.** Debounce rapid connectivity changes. Banners that repeatedly enter and leave cause distraction and layout jumps.
69. **Accessible update.** Ensure changed status is announced to screen readers. Updating visible message text alone may not emit the expected event.
70. **Reserve banners.** Do not use permanent app-wide banners for trivial successful clicks. Persistent importance loses meaning when every event receives it.

### Notifications — M

Source for 71–75: [Notification UX](https://learn.microsoft.com/en-us/windows/apps/develop/notifications/app-notifications/app-notifications-ux-guidance).

71. **Contextual opening.** A notification should open its referenced task/document. Landing on Home makes users search again.
72. **Background action.** A quick reply should complete without unnecessarily opening the app. Respect the intended interruption size.
73. **Focus respect.** Suppress or quiet low-value alerts during focused work. Notification volume can cause users to disable the channel entirely.
74. **Clear stale notices.** Remove resolved/read items, including when handled elsewhere. A notification center full of obsolete tasks undermines trust.
75. **Useful content.** Include the event and a useful action, not promotional noise. A notification should save work rather than create it.

### Accessibility — M

Source for 76–80: [Accessibility overview](https://learn.microsoft.com/en-us/windows/apps/design/accessibility/accessibility-overview).

76. **Semantic controls.** Expose names, roles, values and actions through UI Automation. Custom-painted controls need equivalent accessibility providers; XAML controls use automation peers.
77. **Screen reader path.** Test whole tasks with Narrator, not only a startup announcement. Labels alone do not prove selection or errors are usable.
78. **Text and zoom.** Preserve content and operations when users enlarge text. Fixed-height rows that clip are functional failures.
79. **Contrast adaptation.** Follow system high-contrast colors. A hardcoded branded background can erase focus, text or state.
80. **Equivalent input.** Ensure keyboard/assistive access to pointer interactions. Dragging cannot be the only route to an essential operation.

### Type and color — M

Sources: [Typography](https://learn.microsoft.com/en-us/windows/apps/design/signature-experiences/typography), [Color](https://learn.microsoft.com/en-us/windows/apps/design/signature-experiences/color).

81. **Type hierarchy.** Use a restrained size/weight hierarchy, with readable regular body text. Many unrelated type styles fragment the screen.
82. **Casing.** Prefer sentence case for Windows UI. All-caps controls create visual noise and weaken ordinary reading shapes.
83. **Truncation.** Signal shortened text with ellipses where appropriate. Silent clipping makes names and labels look incorrectly stored.
84. **Accent restraint.** Use accent for meaningful interaction/state. Coloring every card equally erases priority.
85. **Theme contrast.** Check contrast across both modes and accent choices. A beautiful dark screenshot does not validate light mode or bright-room use.

### Surface and motion — M

Sources: [Layering](https://learn.microsoft.com/en-us/windows/apps/design/signature-experiences/layering), [Mica](https://learn.microsoft.com/en-us/windows/apps/design/style/mica), [Motion](https://learn.microsoft.com/en-us/windows/apps/design/signature-experiences/motion).

86. **Layer meaning.** Separate navigation base from content. Random card nesting adds decoration without communicating structure.
87. **Temporary surfaces.** Give menus/dialogs clear elevation relative to content. Identical flat backgrounds can obscure what dismisses independently.
88. **Fallback appearance.** Design solid-color states alongside Mica. Battery saver or contrast mode must not produce an unfinished screen.
89. **Transition continuity.** Preserve object identity as layout changes. Unrelated jumps during resize or navigation make users reorient.
90. **Consistent motion.** Surfaces sharing an entry point should enter/dismiss consistently. Decorative animation should not make repeated commands feel slower. (inference)

### Task-specific desktop leverage — E/I

Sources vary by item; these are examples to adapt, not universal Windows conventions.

91. **Bulk work.** Queue file copies and show operation state when users manage many jobs. Separate untracked dialogs scale badly. [Directory Opus](https://www.gpsoft.com.au/)
92. **Adjacent preview.** Show preview and metadata beside the file list for inspection-heavy work. Reopening a separate app for every item adds context switching. [Directory Opus](https://www.gpsoft.com.au/)
93. **Path visibility.** Include full paths where equal filenames occur. A pretty name-only result grid can make the wrong file look correct. [Inspected Everything screen](https://www.voidtools.com/support/everything/Everything.Search.Window.png)
94. **Operation graph.** A speed graph helps explain variable file-transfer behavior. It supplements actual completion/error state; smooth animation alone is no guarantee. [Files v3](https://www.files.community/blog/posts/v3)
95. **Workflow handoff.** Offer copy, save and upload as explicit capture outcomes. Automatic publishing needs a visible, reversible configuration choice. [ShareX](https://getsharex.com/)
96. **Restore workspaces.** Save pane visibility, widths and open documents for recurring modes. Rebuilding a research/writing layout every session is needless setup. [Obsidian workspaces](https://obsidian.md/help/plugins/workspaces)
97. **Reveal capability limits.** Explain file-size and protected-folder limits before failure. A lightweight editor cannot imply unrestricted replacement behavior. [Notepads](https://github.com/0x7c13/Notepads)
98. **Device routing.** Show which application uses which output device. A global volume slider alone cannot explain one silent app. [EarTrumpet](https://github.com/File-New-Project/EarTrumpet)
99. **Learned locations.** Preserve familiar command locations during a visual refresh when they still fit. A restyle need not require relearning routine work. [Files v3](https://www.files.community/blog/posts/v3)
100. **Purposeful defaults.** Start with the likely job and allow advanced adjustment later. Setup questions should not merely defer obvious design decisions. [Spolsky book text](https://www.joelonsoftware.com/2001/10/24/user-interface-design-for-programmers/)
101. **Optional residence.** Explain “keep running in background” and provide exit/control. Faster warm launch spends memory and energy users may value differently. [Files v3](https://www.files.community/blog/posts/v3)
102. **Hotkey conflicts.** Make a global shortcut changeable and show conflicts. Do not adopt a reviewer's Win+Space preference as a universal default. [Thurrott transcript](https://twit.tv/posts/transcripts/hands-windows-173-transcript)
103. **Power without tray clutter.** Give occasional tools fast launch without persistent icons when no ongoing function needs them. Constant presence must earn its cost. [Hanselman](https://www.hanselman.com/blog/scott-hanselmans-2021-ultimate-developer-and-power-users-tool-list-for-windows)
104. **Preview under strain.** Test repeated preview/rename operations on realistic large folders. Smooth demo navigation does not establish long-session reliability. [Files user reports](https://www.reddit.com/r/Windows11/comments/1kfvq86/what_do_you_think_of_the_files_app_windows/)
105. **Selectable interaction density.** Consider compact modes for comparison-heavy work while preserving scaling/accessibility. Neither one angry comment nor one spacious screenshot establishes everyone's ideal row height. [Files discussion](https://www.reddit.com/r/Windows11/comments/1kfvq86/what_do_you_think_of_the_files_app_windows/)

### More keyboard paths — M/I

[Keyboard guidance](https://learn.microsoft.com/en-us/windows/apps/develop/input/keyboard-interactions) supplies the conventions; preserve task-appropriate exceptions.

106. **Escape.** Dismiss transient UI safely; do not make Escape unexpectedly navigate backward or close the main workspace. A deliberate full-screen mode may use it to leave that mode.
107. **Pane navigation.** Support F6/Shift+F6 between major panes. Repeated Tab traversal through every control makes large workspaces exhausting.
108. **Familiar accelerators.** Preserve Ctrl+S/F/P/Z and standard clipboard shortcuts where their tasks exist. Do not override text-entry behavior merely to make a global command shorter.

### Onboarding, money and data — E/I

These are product-design inferences from the cited workflows/policies, not universal Windows control rules.

109. **First useful result.** Start a local utility with its core task; defer optional accounts and customization. A team client may need identity first. Explain the dependency instead of pretending every app can skip setup. [Obsidian's optional account/service model](https://obsidian.md/blog/free-for-work/).
110. **Empty workspace.** Offer a small sample, import or create action matching the job. Distinguish “no records yet” from filtered results or a failed load; an empty table cannot communicate all three. This is a synthesis of the list/detail and reporting workflows above.
111. **Import preview.** Show delimiter, encoding, date/number interpretation and rejected rows before committing a business import. Preserve original files and reusable mappings; a silent locale guess can change values. [Easy Data Transform FAQ](https://www.easydatatransform.com/faq.html).
112. **Recurrence review.** Show interval, next run, end condition and disable action near the recurring record. Hiding this in global settings makes accidental future invoices hard to detect. [Moon Invoice recurrence](https://help.mooninvoice.com/hc/en-us/articles/360001222166-How-to-set-up-a-recurring-Invoice-through-the-application).
113. **Paid command boundary.** Mark a premium operation before it changes or exports a document. Explain watermark or save restrictions up front; do not let a user discover them in a delivered file. [PDF-XChange licensing](https://help.pdf-xchange.com/sysadmin/licensing.html).
114. **Trial clock.** State whether days mean calendar days or days actually used, and what happens at expiry. “Seven-day trial” alone cannot convey Easy Data Transform's nonconsecutive-day model. [Trial FAQ](https://www.easydatatransform.com/faq.html).
115. **License identity.** Display the licensed user/organization and seat/device scope; provide key recovery or account lookup. Avoid ambiguous “Activated” status when several workplace identities exist. [Beyond Compare sales terms](https://www.scootersoftware.com/kb/sales_faq).
116. **Renewal versus use.** Put continued-use rights beside update/support expiry. A red “Expired” label can falsely suggest that a perpetual version is unusable. [Opus update entitlement](https://resource.dopus.com/t/upgrade-subscriptions/58445).
117. **Recovery download.** Link the installer/version a license permits and explain any archive deadline. A valid key without a recoverable installer can strand a replacement PC. [PDF-XChange recovery policy](https://www.pdf-xchange.com/knowledgebase/447-How-do-I-determine-what-version-I-should-installhow-can-I-retrieve-my-serial-key).
118. **Export scope.** Identify which records, attachments and settings an export contains and where it was written. Test reopening it; a success banner without a usable artifact is insufficient. Keep export separate from a restorable database backup. [Backup distinction](https://www.sqlite.org/backup.html).
119. **Account and workspace context.** Show the active organization beside actions that affect shared data; distinguish access denial from an empty result. This is a product inference for team clients, not an instruction to add organizations to personal tools. Test revoked permissions and stale drafts before offering bulk actions.
120. **Delete, sign out and uninstall.** Explain separately what each removes locally and remotely. Preserve a clear export/recovery path where promised; never imply uninstall is account erasure. [Windows app-data lifetime](https://learn.microsoft.com/en-us/windows/apps/develop/data/store-and-retrieve-app-data), [shutdown/export case](https://skiff.com/data-migration).

## Reliability, trust and Windows citizenship

These are engineering recommendations derived from documented failure modes; they are not measured conversion claims.

**Recover work before recovery is needed.** Save drafts/checkpoints during normal work; preserve the last good document when saving fails. Windows Error Reporting can call a recovery callback after a crash/hang, but callbacks need progress pings and cannot replace normal persistence. Handle update/shutdown messages promptly; Microsoft's example gives five seconds per GUI shutdown message. Test restart with unsaved edits and interrupted operations, not merely a blank window. [Application recovery](https://learn.microsoft.com/en-gb/windows/win32/recovery/registering-for-application-recovery).

**A path is not necessarily a local, ready file.** Windows cloud placeholders may hydrate on access; full files can later dehydrate, while explicitly pinned files are intended for offline availability. Recommendation: keep file opening cancellable, distinguish unavailable content from an empty document, and avoid recursive background scans that download a user's entire cloud drive. A sync-provider implementation needs the Cloud Files APIs; an ordinary editor usually needs correct asynchronous I/O and error handling. [Cloud Files model](https://learn.microsoft.com/en-us/windows/win32/cfapi/build-a-cloud-file-sync-engine).

**Validate the destination's rules.** Windows names include reserved device names even with extensions; trailing dots/spaces and case assumptions create portability problems. Preserve the user's original name when offering a valid alternative. Test UNC shares, removable volumes, Unicode, junctions and rename collisions. Do not silently sanitize two different names into one overwrite. [Naming rules](https://learn.microsoft.com/en-us/windows/win32/fileio/naming-a-file).

**Long-path support is end to end.** Many Win32 APIs support long paths when both policy and the app manifest opt in; shell tools may still differ. Test picker, import, archive extraction, save, export and updater paths separately. A global setting alone does not retrofit every dependency. Give an actionable path error without discarding the user's work. [Long paths](https://learn.microsoft.com/en-ca/windows/win32/fileio/maximum-file-path-limitation).

**A denied save may be security policy.** Controlled Folder Access can reject writes by apps it does not trust. Keep edits recoverable; offer another destination and useful diagnostics. Do not instruct users to disable antivirus as the normal fix. Test managed-device policy separately from file ACLs and disk-full errors. [Controlled Folder Access](https://learn.microsoft.com/en-us/defender-endpoint/controlled-folder-access-overview).

**Keep secrets out of portable settings.** DPAPI normally binds encrypted data to the user and machine; machine scope permits other users on that machine to decrypt it. Design migration/re-login accordingly. This protects stored material under defined account assumptions, not against arbitrary code running as the same user. The prompt-based DPAPI flow is deprecated for removal in April 2027; this does not deprecate non-interactive DPAPI. [CryptProtectData](https://learn.microsoft.com/en-us/windows/win32/api/dpapi/nf-dpapi-cryptprotectdata).

**Back up databases through a consistent snapshot.** SQLite's backup API can copy a live database incrementally; VACUUM INTO is another documented option. A file copied while being mutated is not a tested restore. Keep exports separate from backups, verify opening restored data, and test interrupted migration/low-disk recovery before claiming durability. [SQLite backup](https://www.sqlite.org/backup.html).

**Do not promise shared-folder database collaboration.** SQLite WAL requires same-host coordination and does not work over network filesystems; it can still return busy errors locally. Keep an active local database outside naive shared-file synchronization, or design an explicit protocol. Inspect the actual SQLite binary shipped by bindings: the rare concurrent WAL-reset corruption bug was fixed in 3.51.3, with 3.44.6 and 3.50.7 backports. This is a targeted upgrade requirement, not a reason to reject SQLite. [WAL constraints and fix](https://www.sqlite.org/wal.html).

**Shortcuts are negotiated resources.** RegisterHotKey can fail when another app owns a chord. Show the conflict and offer rebinding; unregister old bindings. Avoid Windows-reserved combinations and F12. An accelerator that works only while your own window has focus is not a system-wide shortcut. [RegisterHotKey](https://learn.microsoft.com/en-us/windows/win32/api/winuser/nf-winuser-registerhotkey).

**Automation has privilege boundaries.** SendInput cannot inject into higher-integrity applications, and its error does not identify UIPI as the cause. Text expanders and launchers should explain elevated-target limitations and preserve the original text on failure. Test held modifiers, touch-keyboard Unicode and focus changes. Do not elevate the whole app merely to hide a limitation. [SendInput](https://learn.microsoft.com/en-us/windows/win32/api/winuser/nf-winuser-sendinput).

**Tray presence needs an escape route.** Keep a discoverable way to reopen the window and quit; support crisp icons, keyboard interaction and ordinary context menus. Anchor popups near the tray icon. Microsoft's Win32 guidance discourages critical, immediately actionable information in this area; its Windows 7-era balloon examples are historical, not a current visual specification. A reminder that cannot be missed needs an in-app pending state, not faith that a notification appeared. [Tray API and historical guidance](https://learn.microsoft.com/en-us/windows/win32/shell/notification-area).

## Business work under strain



**Printing is a workflow, not a button.** StartDocPrinter can block on network, driver and print-server conditions. Keep this off the UI thread. Recommended invoice/report flow: preview the actual page layout, choose paper/orientation/range, submit once, show the job state and offer export if the printer is unavailable. Do not equate spool acceptance with paper delivered or automatically resubmit an invoice after an ambiguous timeout. Test unavailable default printers, non-Latin fonts and large reports. [Print API behavior](https://learn.microsoft.com/en-us/windows/win32/printdocs/startdocprinter).

**Resume means rechecking reality.** Windows distinguishes suspend, automatic resume, user-triggered resume and power-setting changes. On wake, revalidate device/share availability and stale requests; coalesce missed polling work rather than replaying a burst. A timer must define whether sleep counts. Measure durations with a suitable elapsed-time source; QPC/Stopwatch is distinct from UTC timestamps. These are derived test requirements, not claims that every app needs a background service. [Power events](https://learn.microsoft.com/en-us/windows/win32/power/wm-powerbroadcast), [time measurement](https://learn.microsoft.com/en-us/windows/win32/sysinfo/acquiring-high-resolution-time-stamps).

**International input precedes translation.** IMEs compose characters; editors, search boxes and keyboard shortcuts must leave composition intact. Test candidate-window placement, Enter during composition and switching layouts mid-form. Right-to-left layouts also need mixed-direction text: paths, IDs, prices and names cannot all be mirrored indiscriminately. Prefer platform text controls before writing custom text interaction. [IME model](https://learn.microsoft.com/en-us/windows/win32/intl/input-method-manager), [bidirectional design](https://learn.microsoft.com/en-us/windows/apps/design/globalizing/design-for-bidi-text).

**File notifications are hints, not a ledger.** ReadDirectoryChangesW can lose detailed events on buffer overflow; recover by enumerating current state. A monitor or document browser should survive bulk extracts, renames and reconnects without permanent stale entries. Keep a rescan bounded and cancellable; distinguish a missing folder from temporary share failure. [Directory notification contract](https://learn.microsoft.com/en-us/windows/win32/api/winbase/nf-winbase-readdirectorychangesw).

**Clipboard interoperability and privacy travel together.** Supply useful standard formats alongside rich formats so copying into Excel, mail or a plain editor works. Windows offers formats controlling inclusion in clipboard history and cloud clipboard. Use them for secrets, but do not claim they prevent all third-party capture. A clipboard utility needs exclusions, bounded retention and a visible clear/pause control. [Clipboard formats](https://learn.microsoft.com/en-us/windows/win32/dataxchg/clipboard-formats).

**Dropping is not always importing.** Drag sources advertise copy/move/link and formats; targets report the performed operation. Show the effect before release and preserve source data until successful completion. Pair drag with Open/Import/Paste for keyboard access. Validate drops from Explorer, Outlook-like virtual attachments and other app windows; reject unsupported formats with a useful explanation. The virtual-attachment cases require stack-specific implementation/testing beyond the basic XAML sample. [Drag-and-drop contract](https://learn.microsoft.com/en-us/windows/apps/develop/data/drag-and-drop).

**Uninstall must not be the first discovery of data ownership.** Microsoft distinguishes replaceable app state from valuable user data; packaged app-data lifetime follows the app. Put export/backup and storage-location explanations where users can find them. Do not assume historical roaming settings provide cross-device sync on Windows 11. Test uninstall/reinstall, identity changes and package migration using the actual deployment format. [App-data lifetime](https://learn.microsoft.com/en-us/windows/apps/develop/data/store-and-retrieve-app-data).

## Commercial success: measurements, pricing and conversion

Windows desktop software can support a durable small business when a narrow, valuable job benefits from local execution, privacy, files or system integration. It can also remain a modest side income despite years of polish. Installation, licensing, updating and support are part of conversion economics. Neither an attractive UI nor Store reach establishes profitable demand. Separate consumer convenience, professional repeat use and managed business deployment.

### Measured outcomes and their limits

| Case | Observed result | What it supports; what it does not |
|---|---|---|
| PerfectTablePlan, 20-year account, February 2025 | Developer reports profitability every year since 2005; initially Windows, later Mac; largely owner-operated with spouse/contractors. Pandemic sales nearly disappeared. | Longevity and claimed profitability, plus sector risk. No audited margin, owner hourly wage, Windows-only revenue or counterfactual web profitability. Local computation/privacy helped justify staying desktop; inherited implementation skill also mattered. [20-year account](https://successfulsoftware.net/2025/02/21/20-years-working-on-the-same-software-product/). |
| PerfectTablePlan editions, change in September 2009; written February 2013 | Moving from one £19.95 edition to £19.95/£49.95/£199.95 editions coincided with 50% higher revenue in following 12 months. Pro features served frequent planners. Existing features stayed in Home. | Revenue, not a 50% conversion lift or controlled experiment. More product work and higher order value mattered; author thought visit-to-sale fell slightly. Match prices to different jobs/value, retain purchased features, permit in-app edition upgrade without reinstall. [Edition account](https://successfulsoftware.net/2013/02/28/how-i-increased-sales-by-adding-extra-price-points/). |
| PerfectTablePlan upgrades, August 2025 | Across v5→v6, 12% Home, 31% Advanced, 45% Professional customers upgraded. Half the observed upgrades took 23 weeks; 75% took 74 weeks. Major upgrades discounted 60%. | Professional repeat use changes lifetime value. Upgrade receipts have a long tail; launch-week sales understate demand. License-count share is not revenue share. One product and its existing audience, not general subscription superiority. [License-database analysis](https://successfulsoftware.net/2025/08/21/software-upgrade-economics-some-real-numbers/). |
| SQL Pretty Printer, 2011 | Developer told consultant that showing licensee name prominently accompanied increase from 1.34 to 2.65 licenses per order. | Historical before/after seats/order, not doubled unique customers or a randomized trial. Test clear per-user entitlement before intrusive DRM. Source discussion notes hardware transfer/dependency costs; activation vendor argues the other side. [Account and discussion](https://successfulsoftware.net/2011/06/26/a-simple-change-that-doubled-sales/). |
| Bingo Card Creator, September 2009 | Same best AdWords campaign: downloaded trial→purchase 1.35%; web 2.32%. Reported AdWords acquisition cost per sale $20 vs $9; requests among last 50 customers 15 desktop vs 3 web. | Installation, lost keys and stale installers can erase margin. Historical cross-platform Java/Swing teacher tool, nonrandom time comparison; not a verdict on modern Windows native utilities. Desktop earns its installation burden only when its advantages matter. [Developer report](https://www.kalzumeus.com/2009/09/05/desktop-aps-versus-web-apps/). |
| Downloadable-software survey, April 2009 | 92 self-selected, anonymous vendor responses; mean sales/visits 0.99% after one outlier excluded; middle half 0.28–1.39%. | Evidence against a universal conversion target. Unverifiable submissions, old acquisition channels, small platform subsamples; do not reuse its Windows/Mac ratio as a current market fact. [Survey, method and downloadable data](https://successfulsoftware.net/2009/04/23/the-truth-about-conversion-ratios-for-software/). |
| backiee and HUXSoft, Microsoft announcement September 2025 | Good2Create claims backiee DAU 10k→40k year-over-year, revenue ×6, 7m downloads; HUXSoft claims daily new Store installs ×10. | Publisher claims selected by a distribution vendor, not controlled results or independent corroboration. Downloads, active users and revenue differ; no profit/CAC/retention cohorts. [Microsoft announcement](https://blogs.windows.com/windowsdeveloper/2025/09/10/free-developer-registration-for-individual-developers-on-microsoft-store/). |
| OneCommander developer comment, July 2025 | Self-identified developer says ten years' work brings income but still needs full-time NYC job; Store income is 15% of direct PayPal/Stripe receipts. | Useful counterweight to Store success stories. Identity and accounts not independently audited; no representative channel share or demographic inference. [Discussion](https://www.reddit.com/r/dotnet/comments/1lxf0sk/is_anybody_earning_anything_by_creating_windows/). |
| PerfectTablePlan acquisition test, August 2026 | Developer reports £289.52 spend, 2,988 clicks, 14 installs, £20.68/install. Click→install 0.46% vs 5.3% Google ads and 4.2% unpaid ChatGPT referrals in same period. | Channel targeting and real activation matter more than cheap clicks. Small observational comparison, no paid-sales counts or randomization; cannot isolate why traffic differed. [Direct account](https://successfulsoftware.net/2026/09/02/chatgpt-ad-targeting-is-garbage/). |

No inspected source provides an audited current ranking of indie Windows app profit. Store awards, Steam revenue estimators, vendor downloads, reviews and cross-platform SaaS revenue cannot substitute. Public primary developer accounts and commerce policies give useful cases, not a market-wide expected return. Current Windows-only retention, refund and CAC distributions remain unavailable from these private businesses; these sources cannot support a profit ranking.

### Commercial models and their user-facing consequences

- **Paid version, optional major upgrades.** Beyond Compare promises perpetual use of the bought major version and free maintenance releases; Standard→Pro costs the difference. This is understandable for a stable professional local tool. Its license system cannot simply add seats to an existing key, and all seats in a multiuser license must move together for major upgrades: operational details can dominate purchase friction. [Sales FAQ](https://www.scootersoftware.com/kb/sales_faq).
- **Lifetime including future versions.** DisplayFusion explicitly promises future versions in its lifetime Standard license, currently $34/machine. OneCommander advertises $30 lifetime Pro for commercial use, including future updates; home use free. These are real alternatives to annual rent, not proof that unlimited maintenance is safe for a new business. Model future OS fixes/support before making an irreversible promise. [DisplayFusion](https://www.displayfusion.com/Purchase/), [OneCommander](https://www.onecommander.com/).
- **Free core, paid distribution convenience/support.** Paint.NET's Classic download is free; paid Store build has the same functionality plus fully automatic updating. Commercial use is allowed. This is a voluntary-support/convenience model; do not call the app open source or assume a paid Store listing means exclusive features. [License FAQ](https://paint.net/license.html).
- **Free local core, optional hosted services.** Obsidian removed mandatory commercial-use licensing on 20 February 2025, citing confusing terms. It claims use in 10,000+ organizations and funds itself through optional support licenses, Sync and Publish. Plain files and no required account reduce lock-in; optional recurring services fund real ongoing work. No evidence here establishes the change's net revenue effect or Windows-only viability. [Announcement](https://obsidian.md/blog/free-for-work/).
- **Subscription or permanent choice.** Fences 6 currently exposes both annual subscription and a separate permanent-license link, plus business deployment and suite choices. Its publisher reports 20m downloads and thousands of business customers, not that many paid users. A 2025 user discussion contains confusion over whether perpetual purchase exists, upgrade value and older versions remaining sufficient. Put duration, future-version entitlement, supported OS and cancellation effects side by side. [Current page](https://www.stardock.com/products/fences/), [May 2025 release](https://www.stardock.com/news/535945/stardock-releases-fences-6), [user discussion](https://www.reddit.com/r/Stardock/comments/1jwyzeq/qualms_about_fences_6_cost/).
- **Subscription-only transition.** TechSmith says Snagit/Camtasia 2025 shifted to annual subscriptions; current use ends after the paid term if canceled. The Snagit discussion contains long-term customers objecting to paying continuously for an already-sufficient tool, alongside vendor arguments about continuing value and legacy rates. This is evidence of a tradeoff and individual frustration, not measured churn. Distinguish old perpetual rights from new subscription rights; never silently revoke purchased use. [Policy](https://support.techsmith.com/hc/en-us/articles/360025504451-Is-This-a-One-Time-Fee), [discussion](https://www.reddit.com/r/SnagIt/comments/1d7yltt/snagit_2025_and_later_will_be_subscriptiononly/).

### Trials, refunds and business buyers

PerfectTablePlan offers a trial, offline work, human support and 14-day money-back guarantee, with consumer pricing from $29.95 plus tax. Beyond Compare instead offers a fully functional 30-day trial and ordinarily refuses returns, with discretionary technical-incompatibility exceptions. These different policies coexist; no source proves one converts better. Make terms visible before purchase; do not describe a no-return product as risk-free. [PerfectTablePlan](https://www.perfecttableplan.com/), [Beyond Compare return policy](https://www.scootersoftware.com/kb/returnpolicy).

Beyond Compare supports credit cards, qualifying bank transfers, constrained Net-30 purchase orders in US/Canada and resellers elsewhere. For work tools, a proforma invoice, organization name, documented seat entitlement and license recovery can unlock sales that a perfect consumer checkout cannot. Support purchase order workflows only where target deal sizes justify administration. The source's exact geographic/amount rules describe that vendor, not general law. [Sales FAQ](https://www.scootersoftware.com/kb/sales_faq).

Support is recurring cost even for offline software. In 2012 Brice reported roughly 40 support emails/week despite rising sales, favored email for a solo business and described collecting version/OS/license information in contact requests. Treat response times, documentation, reproducible diagnostics and repeated-error fixes as product work. His holiday support schedule is a personal choice, not a healthy universal requirement. [Support account](https://successfulsoftware.net/2012/08/21/tips-for-great-software-technical-support/).

## Distribution and full economics

**Current Store fees.** Individual registration became free globally in September 2025; company registration also became free in May 2026. The old $19/$99 figures are stale. Microsoft's commerce fee for non-game apps is 15%; eligible non-game apps may use their own in-app commerce without Microsoft's revenue cut. “Keep 100%” excludes payment-provider, tax, refund, support and infrastructure costs. Store MSIX distribution includes hosting, signing and automatic updates; direct installers remain a separate cost/support decision. [Company change](https://blogs.windows.com/windowsdeveloper/2026/05/07/publish-to-microsoft-store-as-a-company-now-with-free-registration-and-faster-onboarding/), [Store commerce](https://learn.microsoft.com/en-us/windows/apps/publish/publish-your-app/why-distribute-through-store).

**Direct checkout.** Paddle's published merchant-of-record rate is 5%+$0.50 per checkout, with tailored pricing available for products below $10. It covers billing/tax functions described on its page; eligibility, payout, refund treatment and contract still matter. At a hypothetical $30 sale, headline fee is $2 versus Store's $4.50; the $2.50 difference is not profit until the extra direct-distribution and support work is counted. At $5, the same headline fee is $0.75, or 15%. These are arithmetic illustrations, not provider recommendations or actual app margins. [Paddle pricing](https://www.paddle.com/pricing).

**Operating model for a new app (research inference).** Track net receipts after discounts, taxes collected for others, refunds, chargebacks, fees and FX; then deduct acquisition, license/support staff time, Windows release testing, signing, distribution, crash/support infrastructure and any sync/AI usage. Allocate founder maintenance time; do not hide it as “free.” For subscriptions, use cohort gross margin and retention, not headline MRR. For perpetual licenses, model years of compatibility obligations and paid-upgrade timing. Test whether users reach their first useful result on their actual locked-down work PC. Count successful installs and active licensed seats, not download-button clicks.

**Audience/geography.** Local-only desktop helps private data and offline venues but complicates phone/browser collaboration. Buyers with corporate deployment policies need install documentation and procurement routes; consumers may choose the Store for trust and updates. Language-specific support, payment methods and currency presentation can change service cost. None of the small samples above estimates geography-wide willingness to pay. Avoid a generic “Windows users will not pay” conclusion.

## Directory Opus: paid updates versus continued use

FAQ dated 22 January 2024; checked 8 November 2026. The update subscription is **not rental**: expiration stops access to newer releases, not use of the entitled version. Users can reinstall that version on a replacement PC. New purchases include at least one year of updates; no automatic charging, and no cancellation action required. Rejoining directly after the 14-day grace period charges missed time capped at one year plus at least a year ahead. Dealer-token rules differ. Keep installers/entitlement lookup accessible and avoid update prompts for unusable releases. Version-number changes do not themselves trigger a second purchase while updates are covered. Exact account-specific price remains on the renewal page; FAQ gives AUD examples, not a universal price. [Upgrade FAQ](https://resource.dopus.com/t/upgrade-subscriptions/58445).

## Failures, switching and continuity

**DRAMA and CleanChief (historical first-person failures).** DRAMA's sponsors liked retaining engineering rationale but end users bore extra work and integration friction; it never gained real adoption. CleanChief spent over two years building cleaning-company software without adequate domain/customer feedback and stopped near first sales. Treat owner enthusiasm, funding and plausible features separately from demonstrated repeated use. These self-selected 2010 accounts reveal mechanisms, not failure-rate estimates. [Original accounts](https://successfulsoftware.net/2010/05/27/learning-lessons-from-13-failed-software-products/).

**Skiff (adjacent cross-platform productivity service).** Its official migration notice confirms Mail, Pages, Calendar and Drive ended 9 August 2024 after acquisition; forwarding ended 9 February 2025. Acquisition did not mean continuity. Ars criticized burying the shutdown beneath acquisition messaging. For a Windows app depending on hosted accounts/sync, design a usable export and explicit notice, not just a celebratory acquisition banner. No evidence here proves the shutdown resulted from bad app UX or unprofitability. [Final notice](https://skiff.com/data-migration), [independent critique](https://arstechnica.com/gadgets/2024/02/encrypted-email-service-skiff-gets-acquired-will-shut-down-in-six-months/).

**Wunderlist.** Microsoft's lifecycle record confirms support ended in May 2020 and points to migration. Use as a second continuity example, without inventing the exact economics or claiming all migrations preserved all features. [Lifecycle record](https://learn.microsoft.com/en-us/lifecycle/products/wunderlist).

**Feature sufficiency.** Fences and Snagit comments show some long-term users do not need each year's new features. Distinguish active happy users from upgrade buyers. Offer clear migration/value explanations; do not manufacture daily friction merely to provoke renewal. Complaints are self-selected and cannot establish population sentiment.

## Being featured is a separate outcome

Microsoft's December 2025 Store awards recognized business/productivity products including Moon Invoice and Notion, alongside AI-focused categories. That documents editorial recognition, not indie profitability or a UX ranking. [Official winners](https://blogs.windows.com/windowsdeveloper/2025/12/03/announcing-the-microsoft-store-awards-2025-winners/).

Windows Central reviewer Sean Endicott criticized the AI emphasis and lack of community nominations. His article is one experienced reviewer's judgment, not a representative user survey. Build a product that earns repeat use; treat award alignment as a distribution opportunity with changing criteria. [Independent critique, 5 December 2025](https://www.windowscentral.com/software-apps/microsoft-store-awards-2025-lean-heavily-on-ai-and-community-voting-ditched).



Microsoft's 2024 awards included Diarium, Todoist, f.lux and Oh My Posh, alongside much larger companies. Awards can recognize daily usefulness, cross-device experience and ecosystem fit; they are neither an indie ranking nor a profit ranking. Read categories and date. Vendor editorial strategy can change; do not copy AI features solely to chase a badge. [2024 winners](https://blogs.windows.com/windowsdeveloper/2024/11/01/announcing-the-microsoft-store-awards-2024-winners/).

## Technology choices and stack fit

Windows has several viable UI stacks. Microsoft recommends WinUI for new Windows UI, but also explicitly supports adding modern capabilities to WPF, WinForms and Win32 without rebuilding the UI. A mature grid/editor, existing code and proven accessibility can outweigh default Fluent styling. Compare the hardest real screen, shell integration and installer before selecting a framework. [Windows platform](https://learn.microsoft.com/en-us/windows/apps/), [modernization paths](https://learn.microsoft.com/en-us/windows/apps/windows-app-sdk/migrate-to-windows-app-sdk/).

Separate **build API level**, **runtime minimum**, **serviced OS**, **package identity**, **installer**, **distribution channel**, **runtime deployment**, and **tested hardware**. “Windows 10 compatible” answers almost none of these alone. A Windows-specific .NET TFM chooses compile-time reference APIs; `SupportedOSPlatformVersion` expresses the supported lower OS boundary and enables analyzers. Guard newer API calls. [TFMs and WinRT](https://learn.microsoft.com/en-us/windows/apps/desktop/modernize/winrt-apis-desktop-apps).

Do not freeze a 2024 framework recommendation into a 2026 recipe. The inspected .NET policy lists .NET 10 LTS through 14 November 2028; .NET 8 and 9 end support on 10 November 2026. SDK and OS servicing have separate dates. Current Windows App SDK release page lists stable 2.6.5, released 2 November 2026, under the 2.0 servicing line ending 29 April 2027. These are source snapshots, not independently tested release guarantees. [.NET policy](https://dotnet.microsoft.com/en-us/platform/support/policy/dotnet-core), [Windows App SDK channels](https://learn.microsoft.com/en-us/windows/apps/windows-app-sdk/release-channels), [2.0 release notes](https://learn.microsoft.com/en-us/windows/apps/windows-app-sdk/release-notes/windows-app-sdk-2-0?pivots=stable).

| Shape | Best fit | Main cost / rejection test |
|---|---|---|
| C# + WinUI + Windows App SDK | New Windows-first app wanting current controls, accessibility infrastructure and shell capabilities | Prototype grids, rich editing, printing, multi-window behavior and deployment. Default controls do not prove the whole app accessible. |
| C# + WPF on supported .NET | Dense business tools, editors, mature third-party controls, substantial existing code | Verify per-monitor scaling, theme contrast and Win32 interop. Fluent styling can modernize appearance without a UI rewrite. |
| C# + WinForms | Internal CRUD/admin tools, designer productivity, existing controls | Dense forms are a strength; fixed pixel layouts and custom painting create DPI/accessibility work. Designer migration can differ from runtime compatibility. |
| C++ + Win32/WinUI | Deep shell/peripheral integration, startup/resource constraints, existing native core | More lifetime, ABI and threading responsibility. WIL and C++/WinRT reduce boilerplate; do not make unsafe ownership disappear. |
| C# + Avalonia | Cross-platform desktop, XAML team, custom brand and complex documents | Drawn UI requires platform-specific input, accessibility and rendering validation. WPF compatibility is conceptual, not source identity; commercial XPF is separate. |
| C# + Uno | WinUI-shaped API knowledge and shared UI across desktop/mobile/web | Current README describes Skia desktop rendering; do not assume every Windows Uno head is native WinUI. Choose the head and validate actual APIs. |
| Electron | Existing web UI/team, complex editor ecosystem, uniform Chromium behavior | Bundled engine size, background processes and continuous browser security updates. Keep privileged IPC narrow. Renderer sandboxing defaults on since Electron 20; privileged main-process code and IPC still need protection. |
| Tauri | Web UI plus Rust core; system WebView preferred | Runtime provisioning, webview variation and capability design. Small installer does not imply low end-to-end RAM or maintenance cost. |
| Wails | Go core with web UI | Windows WebView2 lifecycle and bridge security still matter. Do not presume the Go binary eliminates frontend packaging or native integrations. |
| Qt Widgets / Qt Quick | Native C++ core, cross-platform business/scientific UI; Widgets for dense forms, Quick for custom motion | Deployment/plugin/ABI work; module-specific LGPL/GPL/commercial terms. Do not call all Qt modules LGPL. |
| Flutter | Shared Dart UI with mobile companions, strongly branded interface | Desktop menus, focus, IME, windowing and plugin coverage deserve explicit tests; a mobile layout enlarged to desktop is insufficient. |
| Fyne | Small Go tools needing one toolkit | Custom-rendered UI and desktop integration fit must be demonstrated. Prefer a focused prototype over assuming Windows conventions from cross-platform support. |

Owning sources: [WinUI](https://github.com/microsoft/microsoft-ui-xaml), [WPF](https://github.com/dotnet/wpf), [WinForms](https://github.com/dotnet/winforms), [WIL](https://github.com/microsoft/wil), [Avalonia](https://github.com/AvaloniaUI/Avalonia), [Uno](https://github.com/unoplatform/uno), [Electron security](https://www.electronjs.org/docs/latest/tutorial/security), [Tauri webviews](https://v2.tauri.app/reference/webview-versions/), [Wails](https://github.com/wailsapp/wails), [Qt licensing](https://doc.qt.io/qt-6/licensing.html), [Flutter](https://github.com/flutter/flutter), [Fyne](https://github.com/fyne-io/fyne). README performance/production claims are author claims; no comparative measurements made here.

## Compatibility and supported targets

1. **Windows release and edition.** Windows App SDK reaches Windows 10 1809, but installation reach is not an OS-support promise. Windows 10 Home/Pro general support ended 14 October 2025; LTSC and paid/extended arrangements differ. Retaining old-business fleets needs a named edition/build contract, security policy and test image. A consumer app can choose currently serviced Windows 11 instead; do not infer market share from this choice. [OS lifecycle](https://learn.microsoft.com/en-us/lifecycle/products/windows-10-home-and-pro), [SDK/OS matrix](https://learn.microsoft.com/en-us/windows/apps/windows-app-sdk/support).

2. **x64, ARM64 and x86.** Ship native ARM64 when dependencies permit; test the complete installer, native DLLs, codecs, plug-ins and shell helpers. Windows 11 Arm emulates x86 and x64; Windows 10 Arm only x86. Kernel drivers must be ARM64. Emulation success for the main window says nothing about a scanner driver or injected extension. Keep x86 only for an identified customer/in-process dependency, with its own address-space and interoperability tests. [Arm emulation](https://learn.microsoft.com/en-us/windows/arm/apps-on-arm-x86-emulation).

3. **SDK target versus minimum.** Compile against newer APIs while declaring a lower minimum only if guarded paths and fallback behavior work. Test old minimum and current release. An app manifest minimum and .NET analyzer settings serve different roles; warnings are useful evidence, not runtime tests. [WinRT targeting](https://learn.microsoft.com/en-us/windows/apps/desktop/modernize/winrt-apis-desktop-apps).

4. **Managed and native runtime delivery.** Framework-dependent installation shares runtime servicing; self-contained delivery controls availability but makes the publisher responsible for shipping runtime patches. Inventory .NET, Windows App SDK, VC runtime and WebView independently. Offline installation must include every required payload. [Deployment choices](https://learn.microsoft.com/en-us/windows/apps/package-and-deploy/).

5. **MSIX, external-location identity and unpackaged apps.** MSIX gives managed installation/update identity; external-location packaging can add identity while retaining an existing installer; unpackaged remains legitimate. Identity affects share targets, declared extensions and some notification/background paths. Test upgrades from each historically shipped form; storage/identity changes can strand settings or taskbar pins. [Packaging/process](https://learn.microsoft.com/en-us/windows/apps/get-started/intro-pack-dep-proc), [external location](https://learn.microsoft.com/en-us/windows/apps/desktop/modernize/grant-identity-to-nonpackaged-apps).

6. **Store versus direct versus managed enterprise.** Packaging and channel are distinct choices. A direct download needs a trustworthy installer, updater and repair path; enterprise buyers may require silent install, detection rules, controlled version rollout and no self-update. Test a standard user and a locked-down machine, not only the developer's admin session. [Distribution overview](https://learn.microsoft.com/en-us/windows/apps/package-and-deploy/).

7. **WebView2 presence and servicing.** Check runtime availability even on recent Windows. Evergreen shares a patched runtime; fixed deployment gives version control at a disk/security-servicing cost. Include offline installers for disconnected customers; test upcoming Evergreen versions and feature detection. The installed Edge browser is not the production backing runtime. [WebView2 distribution](https://learn.microsoft.com/en-us/microsoft-edge/webview2/concepts/distribution).

8. **Mixed DPI, docking and RDP.** A 4K laptop docked to 1080p changes scale while running. Test 100/125/150/200%, moving windows, undocking, RDP reconnect and saved offscreen bounds. PMv2 handles important non-client behavior, but custom content still needs correct response to DPI changes. Raster icons, hit targets and pop-up position often fail before main text does. [DPI](https://learn.microsoft.com/en-us/windows/win32/hidpi/high-dpi-desktop-application-development-on-windows).

9. **Window size versus monitor size.** Test snapped narrow windows and enlarged text on a large monitor. Responsive layouts must preserve the main task, scroll access and command labels. Define a justified minimum window size; do not assume every business user maximizes. Keyboard and assistive-technology access must survive overflow. [Accessibility](https://learn.microsoft.com/en-us/windows/apps/design/accessibility/accessibility-overview).

10. **Mouse, keyboard, touch, pen and speech.** Windows unifies much pointer input, but precision, hover and text entry differ. Provide keyboard paths for all core actions; distinguish Tab between groups and arrows within composites. Test IME composition and touch keyboard occlusion where text entry matters. Pen-specific pressure/eraser behavior belongs only in annotation products. [Input model](https://learn.microsoft.com/en-us/windows/apps/develop/input/input-primer), [keyboard](https://learn.microsoft.com/en-us/windows/apps/develop/input/keyboard-interactions).

11. **Contrast, font scaling and Narrator.** Dark mode is not a contrast theme. Use semantic system colors and automation names/patterns, including custom grids and canvas content. Test selected/disabled/error states in customized contrast palettes. UI Automation supports both assistive technology and automation; a screenshot or successful mouse test cannot establish accessibility. [Contrast](https://learn.microsoft.com/en-us/windows/apps/design/accessibility/high-contrast-themes), [UI Automation](https://learn.microsoft.com/en-us/windows/win32/winauto/entry-uiauto-win32).

12. **GPU, virtual machines and remote sessions.** Rendering can fall back to software; acceptable output may become expensive. Test low-end integrated graphics, disabled acceleration and remote sessions; reduce continuous animation and avoid assuming GPU-backed effects. WARP supplies Direct3D software rendering, not free performance. [WARP](https://learn.microsoft.com/en-us/windows/win32/direct3darticles/directx-warp).

13. **Locale, writing system and business data.** Separate UI language from number/date conventions, timezone and persisted machine formats. Test long translations, RTL, sorting, non-Latin paths and decimal separators. Financial CSV import/export needs an explicit format contract; locale-sensitive human display must not change identifiers or serialized numbers. [Globalization](https://learn.microsoft.com/en-us/windows/apps/design/globalizing/globalizing-portal).

14. **Notifications and activation.** Modern `AppNotificationManager` can serve WinUI, WPF, WinForms and unpackaged Win32. Push/background delivery has additional identity/registration conditions. Test cold launch, already running, closed document, expired session and disabled notifications. Preserve an in-app record for important results. Do not copy UWP toast snippets without checking the app model. [Notification API comparison](https://learn.microsoft.com/en-us/windows/apps/develop/notifications/).

15. **Shell and peripheral extensions.** Test file associations, protocol activation and declared context commands in packaged and direct forms. Drivers and in-process extensions have architecture and deployment requirements beyond the UI framework. The old MSIX preparation page broadly says extensions are unsupported; newer packaging documentation describes supported declared extensions. Scope each extension instead of repeating either as a universal rule. [Older preparation guidance](https://learn.microsoft.com/en-us/windows/msix/desktop/desktop-to-uwp-prepare), [current extensions](https://learn.microsoft.com/en-us/windows/apps/desktop/modernize/desktop-to-uwp-extensions).

16. **Network and authentication environment.** Test corporate proxy, offline launch, DNS change, timeouts and cancellation. Reuse/pool HTTP connections; keep DNS refresh behavior deliberate. Preserve local edits when a request fails. Enterprise SSO and broker requirements are a separate feature decision, not implied by “business app.” [HttpClient](https://learn.microsoft.com/en-us/dotnet/fundamentals/networking/http/httpclient-guidelines).

17. **Large datasets and limited memory.** Virtualize visible records, bound background queues and cancel stale searches. Measure cold start, first useful action, idle CPU, working set, bulk import and recovery on an inexpensive device. A small download or fast microbenchmark is not user-visible responsiveness. [Channels](https://learn.microsoft.com/en-us/dotnet/core/extensions/channels), [Windows Performance Toolkit](https://learn.microsoft.com/en-us/windows-hardware/test/wpt/).

18. **Data, updates and shutdown.** See [reliability](#reliability-trust-and-windows-citizenship). Compatibility includes old databases and interrupted migrations, not merely old Windows. Keep document data outside replaceable installation files; validate backup/restore and downgrade policy before automatic updates. Runtime and app versions should be recorded in diagnostics.

### Representative support strategies — proposals, not prevalence claims

- **Windows-first solo product:** currently serviced Windows 11, x64 plus ARM64 if the dependency chain works, stable .NET/Windows App SDK, one installer and one update path. Add Windows 10 only for evidenced users/revenue; keep graceful fallback for newer optional effects.
- **Business fleet tool:** contract by OS edition/build, x64 and required legacy integrations, offline deployment, silent installation, proxy and RDP tests, supported rollback and managed-update controls. Budget for IT deployment support as a product cost.
- **Cross-platform editor:** share document logic and much UI, but maintain Windows-specific shell/input/accessibility tests. Use native ARM64 once all editor/rendering plug-ins support it; keep emulation as a tested temporary path.
- **Tiny system utility:** prioritize idle resource use, activation reliability, standard-user operation and correct privileged helper boundaries. A driver's hardware support can set a stricter floor than the UI toolkit.

Real source projects illustrating choices: WPF's README describes Windows-only vector UI; WinForms explicitly targets complex line-of-business workflows and visual-designer productivity; Avalonia's README names JetBrains and Schneider Electric use (vendor-reported adoption); Uno names Toyota, Microsoft and Kahua (vendor claims); ScreenToGif exposes a long-lived Windows utility source; PowerToys exposes the cost of many shell integrations. These are existence examples, not measured framework market share. [WPF](https://github.com/dotnet/wpf), [WinForms](https://github.com/dotnet/winforms), [Avalonia](https://github.com/AvaloniaUI/Avalonia), [Uno](https://github.com/unoplatform/uno), [ScreenToGif](https://github.com/NickeManarin/ScreenToGif), [PowerToys](https://github.com/microsoft/PowerToys).

### Business controls, deployment trust and architecture boundaries

**Buying a business component suite.** Evaluate the full workflow: editable grid with validation, frozen/reordered columns, grouped/filtered totals, keyboard selection, copy/export, printing, localization, accessible error recovery and restored workspace layout. A polished screenshot omits the expensive parts. Paid support and a consistent suite may reduce integration cost; this is an engineering inference, not a measured ROI claim. Use real data and a 30-day trial where offered. Keep the app's data model and document formats independent enough to replace a control later.

**License eligibility is part of stack fit.** Syncfusion currently limits community eligibility to under $1M annual gross revenue, at most five developers and ten employees, plus an outside-capital ceiling of $3M; consulting/IP ownership and government cases add conditions. Do not equate “indie” with eligibility. DevExpress says each developer needs a license; renewals buy updates/support. These are dated vendor terms, not a legal opinion. [Syncfusion terms](https://www.syncfusion.com/products/communitylicense), [DevExpress licensing summary](https://www.devexpress.com/products/net/controls/wpf/).

**Virtualization must include automation.** Unrendered rows do not appear as full UI Automation elements. Implement/test `ItemContainer` and `VirtualizedItem`; clients may need to find a placeholder, realize it, then inspect or act. Test screen-reader navigation to offscreen rows, retained selection during recycling, column headers and cell errors. Loading every row to satisfy a test defeats virtualization; exposing only visible rows defeats accessibility. [Microsoft virtualization patterns](https://learn.microsoft.com/en-us/windows/win32/winauto/uiauto-workingwithvirtualizeditems).

**Signing and installation trust.** Store MSIX packages are re-signed by Microsoft; Store MSI/EXE submissions still require publisher Authenticode signing. Direct distribution needs a trusted signing path and consistent identity. Current Microsoft docs call Azure's service Artifact Signing (formerly Trusted Signing), with identity/geography limits. Treat eligibility and validation lead time as release prerequisites. [Signing paths](https://learn.microsoft.com/en-us/windows/apps/package-and-deploy/code-signing-options).

**SmartScreen is separate from a valid signature.** New signed files can still warn; do not buy EV solely expecting instant bypass. Publisher and file reputation contribute; enterprise policy may prevent a user from proceeding. Smart App Control has a different execution scope. Test a clean public download on a fresh standard-user machine, not an already-trusted development workstation. Avoid instructions that normalize disabling protection. [SmartScreen](https://learn.microsoft.com/en-us/windows/apps/package-and-deploy/smartscreen-reputation).

**Driver signing is a separate product cost.** Hardware Dashboard attestation/WHCP submission requires an associated valid EV certificate; this remains true even though EV no longer buys SmartScreen bypass for ordinary apps. Architecture, driver certification and servicing belong in the utility's support matrix. [Driver signing](https://learn.microsoft.com/en-us/windows-hardware/drivers/dashboard/code-signing-reqs).

**WinGet release hygiene.** Keep manifest version, architecture, installer URL/hash, install scope and silent switches accurate; test upgrade from prior versions and coexistence with Store/direct installation. Package-manager presence helps admin automation, but cannot guarantee eligibility on a locked-down or offline fleet. [Publisher submission](https://learn.microsoft.com/en-us/windows/package-manager/package/).

**React Native migration boundary.** Owning v0.85 docs say old architecture targets UWP; new targets Windows App SDK/Win32 and uses Composition host components. Migration reinitializes the native project; not a switch. Native UI modules may need rewriting; C# support and XAML embedding are not yet production-ready in that architecture. New architecture became the new-project default in 0.80; old architecture deprecated with 0.82, yet legacy templates remain available. This makes dependency inspection more consequential than the promise of shared JavaScript. [Architecture guide](https://microsoft.github.io/react-native-windows/docs/new-architecture/).

## Common libraries and components

This is a choice catalog, not an install list or popularity ranking. **Platform** means an owning platform doc or supported framework; **repo** means an inspected owning README, not measured adoption; **example** names an actual declared user. Licensing notes flag material conditions, not a legal audit. Pin versions and inspect transitive/native assets before shipment. Small apps often need standard controls, plain state and platform libraries only.

### Languages, frameworks and build

| # | Tool / source | Purpose, fit and alternative | Evidence / material limit |
|---|---|---|---|
| 1 | [C# / supported .NET](https://dotnet.microsoft.com/en-us/platform/support/policy/dotnet-core) | Managed Windows core; compare C++ for deep native integration or existing Go/Rust cores. | Platform lifecycle; choose a serviced runtime and patch self-contained builds. |
| 2 | [WinUI](https://github.com/microsoft/microsoft-ui-xaml) | Current Windows controls/XAML; compare WPF for existing rich desktop controls. | Microsoft repository; benchmark the hardest screen rather than trusting framework branding. |
| 3 | [Windows App SDK](https://github.com/microsoft/WindowsAppSDK) | Windowing, lifecycle, resources and modern Windows APIs across UI frameworks. | Microsoft repo; does not require replacing WPF/WinForms or necessarily adopting MSIX. |
| 4 | [WPF](https://github.com/dotnet/wpf) | Windows XAML, binding, vector graphics and documents. | Microsoft repo; Windows-only, mature ecosystem; not abandoned merely because WinUI is recommended. |
| 5 | [WinForms](https://github.com/dotnet/winforms) | Designer-led forms and business workflows; compare WPF for richer composition. | Microsoft repo explicitly describes line-of-business fit; designer migration has separate costs. |
| 6 | [C++/WinRT](https://github.com/microsoft/cppwinrt) | Standard C++17 projection of WinRT APIs; compare C# projection. | Microsoft repo; consume published tooling instead of building its compiler unnecessarily. |
| 7 | [WIL](https://github.com/microsoft/wil) | C++ RAII wrappers for handles and Windows patterns. | Microsoft repo; reduces native lifetime boilerplate, not a UI framework. |
| 8 | [CsWin32](https://github.com/microsoft/CsWin32) | Generated C# P/Invoke/COM bindings; compare hand-written narrowly scoped interop. | Microsoft repo; metadata/version and generated-code review still matter. |
| 9 | [Avalonia](https://github.com/AvaloniaUI/Avalonia) | Cross-platform C#/XAML UI; compare WPF for Windows-only native ecosystem. | Vendor names JetBrains/Schneider Electric use; not market share. Commercial XPF is a separate product. |
| 10 | [Uno Platform](https://github.com/unoplatform/uno) | WinUI API-shaped shared UI; compare Avalonia or native heads. | Apache-2.0 foundation; vendor adoption claims; current desktop README describes Skia rendering. |
| 11 | [.NET MAUI](https://learn.microsoft.com/en-us/dotnet/maui/supported-platforms) | Shared mobile/desktop C# UI; compare WinUI when Windows desktop is the product. | Platform docs: Windows uses WinUI 3; mobile support does not prove desktop interaction quality. |
| 12 | [Electron](https://www.electronjs.org/docs/latest/tutorial/security) | Bundled Chromium/Node desktop shell; compare system-webview shells. | Owning security guide names VS Code/Slack; continuous dependency/security servicing required. |
| 13 | [Tauri](https://v2.tauri.app/reference/webview-versions/) | Rust + web frontend with WebView2 on Windows. | Owning docs; runtime and privileged bridge need explicit testing. |
| 14 | [Wails](https://github.com/wailsapp/wails) | Go core and web frontend; compare Fyne or Tauri. | Owning repo; choose version-specific desktop APIs and deployment path. |
| 15 | [Fyne](https://github.com/fyne-io/fyne) | Go UI toolkit; narrow tools and shared Go teams. | Owning repo; development also needs C compiler/system tools. |
| 16 | [Flutter](https://github.com/flutter/flutter) | Dart shared rendered UI; compare native WinUI for Windows-specific workflows. | Google repo; audit desktop plugins, input and accessibility per release. |
| 17 | [Qt](https://doc.qt.io/qt-6/licensing.html) | C++ Widgets/Quick and cross-platform APIs. | Mature commercial/OSS platform; some modules are GPL-only under open terms, others LGPL; commercial option. |
| 18 | [MSBuild](https://learn.microsoft.com/en-us/visualstudio/msbuild/msbuild) | Build graph/project orchestration for .NET/native Windows projects. | Microsoft platform; CI need not launch Visual Studio. Keep custom targets comprehensible. |
| 19 | [NuGet Central Package Management](https://learn.microsoft.com/en-us/nuget/consume-packages/central-package-management) | Shared versions in multi-project .NET solutions. | Platform feature for PackageReference; avoid version drift, not a substitute for update review. |
| 20 | [CMake](https://cmake.org/cmake/help/latest/manual/cmake.1.html) | Cross-platform native build generation/presets. | Owning manual; avoid adding it to a simple C# build without native needs. |
| 21 | [vcpkg](https://github.com/microsoft/vcpkg) | C/C++ dependency builds; alternative to vendoring each native library. | Microsoft-maintained MIT tool; ports retain their own licenses and target-triplet costs. |

### Controls, state and composition

| # | Tool / source | Purpose, fit and alternative | Evidence / material limit |
|---|---|---|---|
| 22 | [Windows Community Toolkit](https://learn.microsoft.com/en-us/dotnet/communitytoolkit/windows/) | Extra WinUI/Uno controls and helpers; prefer platform controls when sufficient. | .NET Foundation project; majority MIT, verify individual packages and WinUI generation. |
| 23 | [CommunityToolkit.Mvvm](https://github.com/CommunityToolkit/dotnet) | Observable properties, commands, messaging; compare plain state for tiny UIs. | Microsoft-maintained; repo reports use in Microsoft Store. Avoid needless messaging indirection. |
| 24 | [CommunityToolkit.Diagnostics](https://github.com/CommunityToolkit/dotnet) | Guards/throw helpers; compare ordinary argument checks. | Same toolkit; small helper, not a logging backend. |
| 25 | [CommunityToolkit.HighPerformance](https://github.com/CommunityToolkit/dotnet) | Pooled memory and specialized buffers. | Same toolkit; use after profiling, not as a universal “fast” dependency. |
| 26 | [WPF UI](https://github.com/lepoco/wpfui) | Fluent controls, navigation and themes over WPF. | Owning repo and Store gallery; custom styling still needs contrast/input tests. |
| 27 | [MahApps.Metro](https://github.com/MahApps/MahApps.Metro) | Restyled WPF controls, chrome, dialogs and flyouts. | MIT, .NET Foundation; longstanding project. Metro styling is a coherent choice, not current stock WinUI. |
| 28 | [Material Design in XAML](https://github.com/MaterialDesignInXAML/MaterialDesignInXamlToolkit) | Material-themed WPF controls/icons. | Owning repo; useful brand direction, deliberately different from Windows visual conventions. |
| 29 | [ModernWpf](https://github.com/Kinnara/ModernWpf) | Fluent-inspired WPF styles and controls. | MIT community project; not WinUI and does not replace WPF runtime. |
| 30 | [Krypton Toolkit](https://github.com/Krypton-Suite/Standard-Toolkit) | Styled WinForms controls for richer classic forms. | Owning repo with 2026 release notes; test designer/runtime compatibility against chosen .NET. |
| 31 | [ReactiveUI](https://github.com/reactiveui/ReactiveUI) | Reactive MVVM and bindings; useful for interdependent live state. | Owning repo; alternative to Toolkit.Mvvm, with Rx/disposal/learning costs. |
| 32 | [System.Reactive](https://github.com/dotnet/reactive) | Compose event streams, throttling and asynchronous UI inputs. | Owning repo; ReactiveUI is a declared user. Plain async suffices for linear workflows. |
| 33 | [DynamicData](https://github.com/reactivemarbles/DynamicData) | Reactive collection filtering/sorting/change sets. | Owning repo; useful for live lists, unnecessary for a small static collection. |
| 34 | [Prism](https://github.com/PrismLibrary/Prism) | Modular XAML apps, navigation, events and DI. | v9 dual community/commercial license; heavier structure may not earn its cost in a small app. |
| 35 | [Microsoft.Extensions.DependencyInjection](https://learn.microsoft.com/en-us/dotnet/core/extensions/dependency-injection/overview) | Standard service construction/lifetimes. | Platform; constructor composition without a container remains valid for small apps. |
| 36 | [Microsoft.Extensions.Configuration](https://learn.microsoft.com/en-us/dotnet/core/extensions/configuration) | Read config from layered providers. | Platform; `IConfiguration` is read-only and not a writable settings persistence system. |
| 37 | [Task Parallel Library](https://learn.microsoft.com/en-us/dotnet/standard/parallel-programming/task-based-asynchronous-programming) | Task scheduling and async work. | Platform; preserve UI thread ownership; a task is not a durability queue. |
| 38 | [System.Threading.Channels](https://learn.microsoft.com/en-us/dotnet/core/extensions/channels) | Bounded producer/consumer pipelines. | Platform; specify capacity/drop/wait behavior to control memory under load. |

### Storage, network and serialization

| # | Tool / source | Purpose, fit and alternative | Evidence / material limit |
|---|---|---|---|
| 39 | [SQLite](https://sqlite.org/) | Embedded relational documents/cache. | Primary engine; see the reliability section for WAL/network/backup rules and 2026 fix. |
| 40 | [Microsoft.Data.Sqlite](https://learn.microsoft.com/en-us/dotnet/standard/data/sqlite/) | Thin ADO.NET SQLite access. | Microsoft provider underlying EF's SQLite integration; use directly when ORM adds little. |
| 41 | [EF Core](https://github.com/dotnet/efcore) | LINQ, tracking and migrations. | Microsoft MIT repo; convenience trades explicit SQL for mapping/runtime complexity. |
| 42 | [EF Core SQLite provider](https://learn.microsoft.com/en-us/ef/core/providers/sqlite/limitations) | EF with local SQLite. | Platform docs enumerate schema/type/migration limits; do not assume SQL Server semantics. |
| 43 | [Dapper](https://github.com/DapperLib/Dapper) | SQL-to-object mapping; between raw readers and full ORM. | Owning repo; SQL and migrations remain application responsibilities. |
| 44 | [LiteDB](https://github.com/mbdavid/LiteDB) | Managed embedded document database. | Owning README explicitly warns its encryption is insecure. Choose SQLite/other protected storage where confidentiality matters. |
| 45 | [HttpClient](https://learn.microsoft.com/en-us/dotnet/fundamentals/networking/http/httpclient-guidelines) | HTTP with pooled connections/cancellation. | Platform; usually enough; deliberate client lifetime and DNS refresh. |
| 46 | [Refit](https://github.com/reactiveui/refit) | Generated HTTP clients from C# interfaces. | Owning repo; retains HttpClient/cancellation control; compare explicit client methods. |
| 47 | [RestSharp](https://github.com/restsharp/RestSharp) | Convenience HTTP request/serialization wrapper. | Owning repo calls itself a HttpClient wrapper; v107 introduced substantial migration changes. |
| 48 | [Polly](https://github.com/App-vNext/Polly) | Retry, timeout, circuit breaker and related policies. | Owning repo; cancellation must cooperate. Upcoming maintenance-fee terms are version-specific; see caveats. |
| 49 | [System.Text.Json](https://learn.microsoft.com/en-us/dotnet/standard/serialization/system-text-json/overview) | Platform JSON; default candidate for ordinary DTOs/files. | Platform; source generation can suit trimming/AOT; test schema evolution. |
| 50 | [Newtonsoft.Json](https://github.com/JamesNK/Newtonsoft.Json) | Mature alternate JSON ecosystem and legacy compatibility. | Owning repo; keep where behavior/features require it, not automatically obsolete. |
| 51 | [MessagePack-CSharp](https://github.com/MessagePack-CSharp/MessagePack-CSharp) | Compact binary serialization. | Owning repo distinguishes stable v3 from preview v4; claimed benchmark speed is not app evidence. |
| 52 | [SSH.NET](https://github.com/sshnet/SSH.NET) | SSH/SFTP and remote commands in .NET. | Owning repo; explicit host-key verification and remote failure semantics required. |
| 53 | [LibGit2Sharp](https://github.com/libgit2/libgit2sharp) | Managed Git over native libgit2. | MIT wrapper; native binaries/architectures and Git feature fit matter; shelling out is an alternative. |
| 54 | [System.CommandLine](https://learn.microsoft.com/en-us/dotnet/standard/commandline/) | CLI parsing/help for automation companion. | Platform docs name .NET CLI use; trim-friendly; avoid hand parsing complex commands. |
| 55 | [jq](https://github.com/jqlang/jq) | JSON processing for admin/export tooling. | MIT portable C, no runtime dependencies; a CLI companion, not required in-app library. |

### Editors, charts, graphics, media and documents

| # | Tool / source | Purpose, fit and alternative | Evidence / material limit |
|---|---|---|---|
| 56 | [AvalonEdit](https://github.com/icsharpcode/AvalonEdit) | WPF code/text editor. | MIT; README names SharpDevelop and ILSpy; use before writing an editor engine. |
| 57 | [AvaloniaEdit](https://github.com/AvaloniaUI/AvaloniaEdit) | AvalonEdit-derived editor for Avalonia. | Owning repo; TextMate integration available; not a drop-in WPF control. |
| 58 | [Monaco Editor](https://github.com/microsoft/monaco-editor) | Web code editor derived from VS Code. | MIT; appropriate inside webviews; VS Code extensions are not automatically portable. AMD build deprecated. |
| 59 | [xterm.js](https://github.com/xtermjs/xterm.js) | Terminal frontend for web UI. | MIT; repo names VS Code, Tabby and Hyper. Requires separate PTY/process backend. |
| 60 | [LiveCharts2](https://github.com/Live-Charts/LiveCharts2) | Interactive cross-platform .NET charts. | Owning repo says v2 fixes v0 architectural constraints; evaluate data scale and framework adapter. |
| 61 | [ScottPlot](https://github.com/ScottPlot/ScottPlot) | Interactive large-dataset plots. | MIT repo; cookbook/demo available. Current contribution policy limits anonymous code contributions; not proof of abandonment. |
| 62 | [OxyPlot](https://github.com/oxyplot/oxyplot) | Plot model and framework views. | Owning repo; choose exact adapter/package; compare ScottPlot for target interaction. |
| 63 | [SkiaSharp](https://github.com/mono/SkiaSharp) | Cross-platform 2D drawing/image rendering. | .NET binding around native Skia; ship matching native assets. Custom drawing needs accessibility alternatives. |
| 64 | [Win2D](https://github.com/microsoft/Win2D) | Windows immediate-mode GPU 2D drawing. | Microsoft repo flags partial Windows App SDK/WinUI3 feature coverage, including animated control. Prototype required feature. |
| 65 | [ImageSharp](https://github.com/SixLabors/ImageSharp) | Managed image processing. | Six Labors split license; inspect commercial conditions. Compare SkiaSharp/platform imaging, not just API style. |
| 66 | [Fluent UI System Icons](https://github.com/microsoft/fluentui-system-icons) | Consistent Windows-compatible icon family. | Microsoft source includes directional metadata; respect RTL-specific variants and icon licenses. |
| 67 | [NAudio](https://github.com/naudio/NAudio) | Audio capture/playback and Windows audio APIs. | MIT; current modular packages separate core/WASAPI/ASIO paths. Test device switching and architecture. |
| 68 | [LibVLCSharp](https://github.com/videolan/libvlcsharp) | Broad audio/video playback/streaming. | LGPLv2.1 or commercial wrapper; native LibVLC/assets/codecs add deployment obligations. |
| 69 | [Mapsui](https://github.com/Mapsui/Mapsui) | Maps across WPF/WinUI/Avalonia and other .NET UIs. | Owning repo lists adapters; tile/data licensing and offline caching are separate. |
| 70 | [ONNX Runtime](https://github.com/microsoft/onnxruntime) | Local model inference across CPU/accelerators. | Microsoft repo; hardware/driver execution provider and model-license checks remain necessary. |
| 71 | [QuestPDF](https://github.com/QuestPDF/QuestPDF) | Code-defined PDF invoices/reports. | Free eligibility includes organizations below stated $1M annual gross revenue; other commercial users need terms review. |
| 72 | [Open XML SDK](https://github.com/dotnet/Open-XML-SDK) | Low-level Office document/package generation. | Owning repo explicitly does not promise high-level productivity abstractions; not an Office rendering engine. |
| 73 | [ClosedXML](https://github.com/ClosedXML/ClosedXML) | Higher-level XLSX/XLSM manipulation over Open XML. | Owning repo; compare raw SDK for streaming/control; test spreadsheet correctness in actual readers. |
| 74 | [EPPlus](https://github.com/EPPlusSoftware/EPPlus) | Rich spreadsheet generation/editing. | v8 community license is noncommercial; commercial-business use needs commercial license. |
| 75 | [CsvHelper](https://github.com/JoshClose/CsvHelper) | CSV parsing/writing and mappings. | MS-PL or Apache-2.0; current v34 rewrite needs migration review. Test locale, quoting and malformed rows. |

### Diagnostics and tests

| # | Tool / source | Purpose, fit and alternative | Evidence / material limit |
|---|---|---|---|
| 76 | [Microsoft.Extensions.Logging](https://learn.microsoft.com/en-us/dotnet/core/extensions/logging/overview) | Standard structured logging API/providers. | Platform; often enough before a separate logging abstraction. Redact private document data. |
| 77 | [Serilog](https://github.com/serilog/serilog) | Structured events and sinks. | Owning repo; retention/backpressure/privacy remain app responsibilities. |
| 78 | [NLog](https://github.com/NLog/NLog) | Routing, formatting and structured logs. | Owning repo; mature alternative to Serilog, not a reason to install both. |
| 79 | [Sentry .NET](https://github.com/getsentry/sentry-dotnet) | Crash/error reporting integrations. | Owning SDK repo; hosted costs, consent, PII and offline buffering need review. |
| 80 | [OpenTelemetry .NET](https://github.com/open-telemetry/opentelemetry-dotnet) | Interoperable traces/metrics/logs. | Owning implementation; a contextual ecosystem option, not a reversal of scaffold telemetry preferences. |
| 81 | [Windows Performance Recorder / Analyzer](https://learn.microsoft.com/en-us/windows-hardware/test/wpt/) | OS-level traces and analysis of startup/CPU/I/O. | Microsoft toolkit; separate capture and analysis roles; better evidence than Task Manager alone. |
| 82 | [Process Monitor](https://learn.microsoft.com/en-us/sysinternals/downloads/procmon) | Filesystem, registry and process activity. | Microsoft Sysinternals; useful for installer/permission loops; captures can contain sensitive paths. |
| 83 | [ProcDump](https://learn.microsoft.com/en-us/sysinternals/downloads/procdump) | Hangs, exception and CPU-triggered dumps. | Microsoft Sysinternals; dumps may contain document/credential memory. |
| 84 | [BenchmarkDotNet](https://github.com/dotnet/BenchmarkDotNet) | Controlled .NET microbenchmarks. | MIT repository; complements rather than replaces end-to-end startup/input/idle measurements. |
| 85 | [FlaUI](https://github.com/FlaUI/FlaUI) | UIA2/UIA3 automation of Windows desktop apps. | Owning repo lists Win32/WPF/WinForms/Store apps; choose UIA backend and stabilize automation IDs. |
| 86 | [Accessibility Insights for Windows](https://accessibilityinsights.io/docs/windows/overview/) | Inspect automation tree, events, tab stops and automated findings. | Microsoft tool; combine with Narrator/manual tasks; automated checks are incomplete. |
| 87 | [Playwright Electron support](https://playwright.dev/docs/api/class-electron) | Electron process and renderer integration tests. | Owning API is experimental; not a generic native-Windows control driver. |
| 88 | [xUnit.net](https://github.com/xunit/xunit) | .NET unit/integration tests. | v3 targets .NET8+ or Framework4.7.2+, Apache-2.0; runner compatibility matters. |
| 89 | [NUnit](https://github.com/nunit/nunit) | Flexible .NET tests and assertions. | Owning repo documents major-version migrations; retain existing productive suite when viable. |
| 90 | [MSTest / Microsoft.Testing.Platform](https://github.com/microsoft/testfx) | Microsoft test framework and runner platform. | Supported OSS; separate framework, runner and IDE adapters. |
| 91 | [FsCheck](https://github.com/fscheck/FsCheck) | Property-based tests and shrinking counterexamples. | Owning repo; strong fit for parsing, migrations, sorting and undo invariants. |
| 92 | [Verify](https://github.com/VerifyTests/Verify) | Snapshot tests for structured data/documents. | Owning README adds fee on releases after 1 September 2026 for qualifying organizations; review terms. Avoid blind snapshot approval. |
| 93 | [Fluent Assertions](https://github.com/fluentassertions/fluentassertions) | Readable .NET assertions. | v8+ commercial use requires paid license; native framework assertions are a straightforward alternative. |

### Packaging, release and maintenance

| # | Tool / source | Purpose, fit and alternative | Evidence / material limit |
|---|---|---|---|
| 94 | [MSIX](https://learn.microsoft.com/en-us/windows/apps/package-and-deploy/) | Package identity, managed installation/update. | Platform; assess shell/service/driver constraints and data migration before conversion. |
| 95 | [Velopack](https://github.com/velopack/velopack) | Cross-platform install/update and delta packages. | Owning repo offers Squirrel migration; language-agnostic, not necessarily ideal for managed enterprise updates. |
| 96 | [WiX Toolset](https://github.com/wixtoolset/wix) | Windows Installer/MSI and bootstrapper authoring. | Powerful enterprise fit; current project requires maintenance-fee compliance for revenue-generating use. |
| 97 | [Inno Setup](https://jrsoftware.org/isinfo.php) | Scriptable Windows installer. | Longstanding owner project; commercial licenses requested, explicitly not strictly required. See [purchase FAQ](https://jrsoftware.org/isorder.php); do not call this a mandatory fee. |
| 98 | [NSIS](https://nsis.sourceforge.io/Main_Page) | Flexible script-based Windows installer. | Owning site lists 3.13 on 27 September 2026; own update/repair complexity and audit plugins. |
| 99 | [Electron Forge](https://github.com/electron/forge) | Unified Electron build/package workflow. | Owning project; compare electron-builder according to required makers/signing/update path. |
| 100 | [electron-builder](https://github.com/electron-userland/electron-builder) | Electron packaging and auto-update integration. | Owning repo; maintain native-module architecture builds, signing and staged update testing. |

### Commercial controls and additional platform tools

| # | Tool / source | Purpose, fit and alternative | Evidence / material limit |
|---|---|---|---|
| 101 | [DevExpress WPF](https://www.devexpress.com/products/net/controls/wpf/) | Data/pivot grids, rich text, spreadsheets, scheduler, docking, printing and report designer. | Vendor v26.1 page; paid per-developer subscription. Broad integration can beat assembling many small components. Audit control-specific accessibility and support versions. |
| 102 | [Telerik UI for WPF](https://www.telerik.com/products/wpf/overview.aspx) | MVVM-oriented grid, charts, schedule, PDF and document tools. | Commercial vendor advertises virtualization, editing/validation, export and touch/keyboard access; measure your data and tasks, not marketing superlatives. |
| 103 | [Syncfusion WPF](https://www.syncfusion.com/wpf-controls) | Grids/charts/documents and broad themed controls; [DockingManager](https://help.syncfusion.com/wpf/docking/getting-started) supports IDE-like layouts. | Commercial suite with conditional community eligibility; installation/licensing/version updates remain work. Demos provide source, not independent reliability proof. |
| 104 | [ComponentOne WPF](https://developer.mescius.com/componentone/wpf-ui-controls) | FlexGrid/FlexChart/FlexDiagram/FlexReport for data-heavy Windows apps. | MESCIUS commercial suite; page shows 2026 v2. Its extreme-row-count claim is vendor evidence, not measured app performance. |
| 105 | [WinGet](https://learn.microsoft.com/en-us/windows/package-manager/package/) | Scriptable discovery/install/upgrade distribution. | Microsoft channel accepts YAML manifests into public repository. It distributes an installer; it does not replace installer quality, entitlement handling or support. |
| 106 | [Azure Artifact Signing](https://learn.microsoft.com/en-us/windows/apps/package-and-deploy/code-signing-options) | Managed Authenticode signing, formerly Trusted Signing. | Identity and geography eligibility; CI integration without a physical token. Signing establishes publisher identity, not instant SmartScreen reputation. |
| 107 | [React Native for Windows](https://microsoft.github.io/react-native-windows/docs/new-architecture/) | Shared React Native UI with Windows App SDK/Win32 host. | v0.85 docs: New Architecture default for new projects since 0.80; Composition-based rather than WinUI-control-based. Validate native module parity. |

## Named technologies to avoid, migrate or constrain

Checked 8 November 2026. A paid license or large dependency is not itself a defect. These boundaries prevent selecting tools on obsolete assumptions.

| Choice | Classification, verified reason and date | Replacement / legitimate exception |
|---|---|---|
| Silverlight | Avoid new work; Microsoft support ended 12 October 2021. [Lifecycle](https://learn.microsoft.com/en-us/lifecycle/announcements/silverlight-end-of-support). | Supported desktop/web stack. Isolated legacy migration work is different from adopting it. |
| BinaryFormatter | Migrate existing use; .NET9+ built-in implementation throws and unsupported compatibility package retains security risks. [Migration](https://learn.microsoft.com/en-us/dotnet/standard/serialization/binaryformatter-migration-guide/). | Explicit safe formats and controlled legacy conversion; do not deserialize untrusted old blobs. |
| .NET6/7 and older modern .NET | Out of support; .NET8/9 also near end on 10 November 2026. [Policy](https://dotnet.microsoft.com/en-us/platform/support/policy/dotnet-core). | Supported LTS and scheduled servicing. .NET Framework has its own lifecycle; do not conflate it with .NET Core. |
| Windows App SDK preview/experimental in routine production | Avoid by default: owning channel page marks these unsupported; APIs can change/disappear. [Channels](https://learn.microsoft.com/en-us/windows/apps/windows-app-sdk/release-channels). | Stable serviced release; isolated experiment or deliberate preview dependency with contingency. |
| UWP as automatic default for a new general desktop tool | Usually avoid new work requiring desktop capabilities; current Microsoft direction is WinUI/Windows App SDK. This is not a claim all UWP apps stopped working. [Modernization](https://learn.microsoft.com/en-us/windows/apps/windows-app-sdk/migrate-to-windows-app-sdk/). | Retain supported existing UWP where cost/requirements justify it; map lifecycle/API differences before migration. |
| Old Electron retained for Windows7/8/8.1 | Avoid insecure support strategy: Electron23 dropped these OSes. [Owner announcement](https://www.electronjs.org/blog/windows-7-to-8-1-deprecation-notice). | Supported OS/runtime baseline or a separately maintained legacy product with explicit limitations. |
| Electron with Node enabled for remote untrusted pages / unrestricted IPC | Avoid insecure architecture; rendering content can cross into machine privileges. [Security](https://www.electronjs.org/docs/latest/tutorial/security). | Sandbox/context isolation, validated narrow IPC, allowlisted navigation and prompt patching. |
| Treating Tauri's Windows7 WebView statement as maintained-runtime assurance | Avoid stale inference: its webview page says Windows7+, while current runtime servicing must come from Microsoft. [Tauri](https://v2.tauri.app/reference/webview-versions/), [Microsoft delivery](https://learn.microsoft.com/en-us/microsoft-edge/webview2/concepts/distribution). | Verify current runtime support and test target; historic ability to install is not ongoing security support. |
| LiteDB built-in encryption | Avoid affected feature now: owning README explicitly says its implementation is not secure. [README](https://github.com/mbdavid/LiteDB). | Reviewed encryption/storage approach. This does not prove all unencrypted LiteDB uses unsafe. |
| SQLite WAL before fixed engine versions | Upgrade affected runtime, not merely managed wrapper: rare concurrent writer/checkpoint corruption fixed in 3.51.3; backports 3.44.6/3.50.7. See the reliability section. [WAL §11](https://sqlite.org/wal.html). | Verify actually loaded engine. SQLite remains a strong local-storage option. |
| Visual Studio App Center for a new release pipeline | Avoid new adoption; most features retired 31 March2025. Analytics/Diagnostics extension now runs to end March2027, superseding June2026 date. [Retirement](https://learn.microsoft.com/en-us/appcenter/retirement). | Own CI/distribution, Store package flights, appropriate maintained diagnostics. Do not describe all services as already gone. |
| Spectron | Avoid new work; owner marks deprecated and repository archived. [Repository](https://github.com/electron-userland/spectron). | Playwright Electron or other maintained testing route; check its experimental API limits. |
| WinAppDriver as an unquestioned new default | Caution, not proven formally retired: inspected README remains Windows10/Selenium-service focused; no current maintenance guarantee established here. [Owner](https://github.com/microsoft/WinAppDriver). | Evaluate FlaUI/UIA or maintained commercial automation against real controls; existing stable suites need no automatic rewrite. |
| Squirrel.Windows as an unquestioned new updater | Caution: owning README requests maintainer help. Not enough evidence to call it unsupported universally. [Repository](https://github.com/Squirrel/Squirrel.Windows). | Evaluate Velopack/MSIX; test migration of identity, shortcuts, data and rollback rather than swapping packages blindly. |
| LiveCharts v0 for new cross-platform charts | Prefer successor; v2 author explains v0's WPF-bound design limitations. [LiveCharts2](https://github.com/Live-Charts/LiveCharts2). | v2/ScottPlot/OxyPlot according to task; a working legacy v0 chart does not demand a rewrite alone. |
| Monaco AMD integration | Migrate new integration to supported module route; README marks AMD deprecated. [Monaco](https://github.com/microsoft/monaco-editor). | ESM build with correct workers/assets; old host may need staged migration. |
| Win2D APIs assumed equal across UWP and WinUI3 | Constrain: owner flags partial/missing features such as CanvasAnimatedControl. [Win2D](https://github.com/microsoft/Win2D). | Prototype exact control/API; SkiaSharp or lower-level Direct2D where justified. |
| Prism9, FluentAssertions8+, EPPlus8 treated as unconditional free commercial dependencies | Avoid licensing assumption, not these tools. Owning docs specify community/commercial distinctions. [Prism](https://github.com/PrismLibrary/Prism), [FluentAssertions](https://github.com/fluentassertions/fluentassertions), [EPPlus](https://github.com/EPPlusSoftware/EPPlus). | Budget eligible licenses or Toolkit.Mvvm/plain code, test-framework assertions, ClosedXML/Open XML. |
| QuestPDF/ImageSharp treated as universally permissive | Constrain by actual company/use/version eligibility. [QuestPDF](https://github.com/QuestPDF/QuestPDF), [ImageSharp](https://github.com/SixLabors/ImageSharp). | Paid licenses can be excellent value; evaluate alternatives against document/image requirements. |
| WiX/Verify/Polly upgrades without fee review | Current owning READMEs have maintenance-fee programs. Polly's announced 16 Nov2026 change applies to next major after that date, direct dependencies, and specified revenue threshold; existing versions are excluded. [WiX](https://github.com/wixtoolset/wix), [Verify](https://github.com/VerifyTests/Verify), [Polly](https://github.com/App-vNext/Polly). | Check release-specific terms; do not retroactively claim every installed version incurs a fee. |
| AutoMapper/MediatR added merely for architectural fashion | Contextual avoid: current READMEs include licensing-key systems; mappings/dispatch add indirection. No universal license conclusion inferred from presence of a key. [AutoMapper](https://github.com/AutoMapper/AutoMapper), [MediatR](https://github.com/LuckyPennySoftware/MediatR). | Plain mapping/functions suffice for small apps; established complex use can justify licensing and structure. |
| WPF/WinForms called “dead” | Reject unsupported avoidance: current owning repos and modernization docs support them. [WPF](https://github.com/dotnet/wpf), [WinForms](https://github.com/dotnet/winforms). | Select by real screen/integration/support costs. Rewrite only for a demonstrated product benefit. |

## Prioritized build guidance

This ordering is a research synthesis. Adapt it to the product's core promise; it is not a universal feature checklist.

1. **Prove a paid or repeated job.** Watch target users complete one real task with their own files/data. For business software, include the operator and the buyer; the person approving a purchase may not bear daily entry work. Record existing alternatives, frequency, errors and switching cost. The failed-product cases and PerfectTablePlan's professional editions support segmenting by actual work rather than decorative feature tiers.
2. **Choose the Windows support contract.** Name supported OS editions/builds, architectures, installation channels, offline requirements and required peripherals. Prototype the hardest grid/editor, IME/Narrator flow, shell hook and deployment path. Framework choice follows these results.
3. **Deliver one complete reliable loop.** Open/import → find/edit → save/export/print → reopen/recover. For a utility: invoke → identify target → act → verify → dismiss. Preserve work across errors and explain what actually completed. Do this before adding automation, sync or AI around an unreliable operation.
4. **Make familiar interaction work.** Keyboard navigation, selection, ordinary menus, text editing, resize/snap, contrast themes and predictable focus are baseline work. Apply a coherent visual direction after task hierarchy and density are clear. Use the detailed reference below as implementation guidance, not a demand to show 100 features.
5. **Ship installation and updating as product flows.** Standard-user install, signing, runtime provisioning, old-version migration, settings persistence and clean removal need real tests. Managed buyers may need a separate rollout policy. A trial that never installs has no opportunity to convert.
6. **Expose the paid value without trapping data.** State license scope, update rights, recurring terms and refund limits. Preserve export and explain cancellation effects. Model support and compatibility work before offering lifetime updates. Trial duration and edition count are hypotheses; the historical cases do not yield a universal optimum.
7. **Add the differentiator that compounds daily value.** Examples: Everything-like retrieval focus, Beyond Compare-like review before applying changes, reusable business templates, safe batch actions, portable documents or a workflow-specific shortcut. Benchmark the advantage on real tasks against the user's current tool.
8. **Add expensive capabilities when the evidence earns them.** Cross-device sync, plugins, shell extensions, scripting, multi-user authorization and AI each create new failure/support surfaces. Define the need, security boundary, degraded behavior and operating cost before implementation.

### Useful experiments

| Hypothesis | Observe | Guardrail |
|---|---|---|
| A compact list helps expert users | Task completion, mistaken row/action, keyboard use; test comfortable and compact density | Include enlarged text and low-precision input; do not optimize only a designer's monitor |
| First-use setup delays value | Successful install → first useful result → second useful session, split by source and audience | Preserve required privacy/permission explanations; no forced telemetry assumption |
| A Pro edition matches repeat use | Net revenue per visitor/account, upgrade mix, support time and refunds | Keep existing entitlements; distinguish a price test from new features/traffic changes |
| Background residency makes invocation worth it | Cold/warm invocation, idle CPU/RAM, wakeups and disabled-autostart rate | Show the choice; don't hide cold-start cost behind unsolicited login startup |
| An AI assistant improves a business task | Correct outputs accepted, corrections, time saved, marginal cost and sensitive-data exposure | Human review before consequential writes; keep a non-AI path where practical |
| A Store listing earns its fee | Source-attributed activation and net receipts after channel support | Do not compare downloads to paid sales; avoid double-counting direct and Store users |
| Paid upgrades fund maintenance | Cohort upgrade receipts over months/years, maintenance hours and continuing use | A launch-week spike misses the long upgrade tail documented by PerfectTablePlan |

No experiment here supplies an effect size in advance. Treat testimonials, award badges, review scores and downloads as different evidence from retention or profit.

### Release acceptance scenarios

Use the actual supported versions and hardware, not a theoretical framework matrix. These are proposed checks derived from the documented failure modes above and the compatibility section.

| Scenario | Expected outcome | Failure cost |
|---|---|---|
| Crash during edit or update | Last durable content opens; recoverable draft identified; no silently empty replacement | Lost work and distrust |
| Disk full, read-only destination or security-policy denial | Edits remain available; clear retry/Save As path | Data loss hidden behind a generic error |
| Offline cloud placeholder or disconnected share | Cancellable wait; clear unavailable state; no overwrite with empty content | Frozen UI or destroyed remote document |
| Expired login during a bulk action | Clear completed/pending results; safe retry; local draft retained | Duplicate invoices/actions or missing edits |
| Dock removal and RDP reconnect | Windows/dialogs remain reachable; scale and focus update | App appears lost or unusable |
| Narrator, contrast theme and enlarged text | Core task and errors remain perceivable/operable | Excluded users and support burden |
| IME composition and mixed-direction content | Composition, caret, selection and displayed identifiers remain correct | Wrong search or corrupted business text |
| Sleep/wake during a timer or transfer | Defined timer semantics; reconciliation; no burst of stale actions | Incorrect reporting or repeated side effects |
| Multi-million-entry search/import | Progressive bounded work, cancellation, responsive navigation | Memory exhaustion and abandoned trial |
| Upgrade/reinstall/uninstall | Document ownership and settings behavior match published promise | Lost records, keys and configurations |
| Standard user and managed policy | Supported features work or explain the precise blocked capability | Failed business rollout |
| Print server unavailable | Main UI stays responsive; job acceptance distinguished from completion | Duplicate output and stalled operations |

These are not test results. This research did not run Windows devices or install the surveyed apps.

## Sources and inspection scope

Research checked 8 November 2026. Near-claim links are the source record; dates and versions identify historical examples where material. Sources were read beyond search snippets. Repository entries use owning documentation/README text; a maintained repository is evidence of an available implementation, not representative adoption or independently verified quality.

- **Platform contracts:** Microsoft Learn pages for current controls, accessibility, deployment, lifecycle, Windows APIs and tooling. Windows 7 UXGuide pages are explicitly historical; retain useful semantics, not their visual dimensions or unsupported OS assumptions. Where old and current docs differ, the affected section states the distinction.
- **Shipped product evidence:** developer documentation, licensing/refund policies, release notes and source projects for the named apps. These establish offered behavior and publisher claims; they do not establish satisfaction, profit or comparative performance.
- **Independent use and critique:** Ars' Windows 11 review, Windows Central hands-on/editorial coverage, Hanselman's tools essay, Cool Tools' long-term Everything account, Beyond Compare user reviews and bounded user discussions. Selected reports supply failure scenarios and disagreement, not defect rates or consensus.
- **Commercial evidence:** Andy Brice's firsthand business accounts, Patrick McKenzie's historical desktop/web comparison, publisher Store case studies, current commerce policies and product purchase terms. Before/after results remain observational; cross-platform accounts are not Windows-only financial results. Public founder accounts, pricing, policy pages, case studies and reviews did not expose audited current Windows-only profit/retention distributions; no ranking or expected return is inferred.
- **Books and long-form commentary:** directly read Spolsky's author-hosted chapter and the *About Face 2.0* desktop-posture chapter; read Atwood's critique. These are excerpts, not a claim to have read each complete book. Thurrott's published *Hands-On Windows 173* transcript is AI-generated and used as expert commentary, not a verbatim audio record.
- **Visuals:** directly inspected publisher screenshots for Files, Directory Opus and Everything; sampled 13 frames of Microsoft's 400-frame consistency animation. EarTrumpet's flyout direction is based on documented behavior. Promotional screenshots and sampled frames cannot establish live responsiveness, gesture timing or long-term reliability.

No app installation, Windows device-lab run, private financial audit, dependency build, accessibility certification or comparative performance benchmark was performed. The release scenarios specify what a product team should test; they do not claim those tests passed. Sources unavailable through one route were pursued through primary alternatives; conclusions use accessible evidence and retain the specific limits beside affected claims.
