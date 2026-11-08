# Great Linux business, productivity and utility apps

Research date: **8 November 2026**. Desktop GUI apps; GNOME, KDE Plasma and cross-desktop workflows. Recommendations are research findings, not confirmed scaffold choices.

**Build a dependable work tool for an explicit Linux support matrix.** Choose a coherent desktop language; prove the risky integrations in a packaged build; make saving, sync and recovery understandable. Native appearance, downloads and a price tag each establish only part of greatness.

Read by task: [app examples](#app-examples-dimensions-of-great-and-limitations), [104 UI details](#specific-screens-and-components-104-practical-details), [visual directions](#visual-directions-directly-inspected), [business models](#payment-models-and-app-examples), [stacks](#stack-choices), [compatibility](#compatibility-four-distinct-promises), [113 tools](#named-ecosystem-catalog), [avoid/migrate](#named-avoid--migrate--qualify-list), [build order](#build-order-and-decisions-to-test).

## Scope and relation to existing guidance

Business includes document, finance and team-work clients; productivity includes notes, tasks, calendars, email and knowledge tools; utilities include file, backup, credential, capture and system tools. Games, server administration and specialist creative production are outside scope except useful comparisons. Linux does not have one desktop interaction contract. Distinguish GNOME recommendations, KDE recommendations, cross-desktop conventions and product exceptions.

Shared principles: [values](values.md), [offline sync](offline-sync.md), [data rights](data-rights.md). Server defaults in the [web recipe](app-web.md) do not select a Linux UI stack. Compare [Mac craft](playbook-macos-apps.md), [B2B workflows](playbook-b2b-saas-web-apps.md) and [tiny cross-platform tools](playbook-tiny-cross-platform-utilities.md); this report owns Linux desktop differences and broader work apps.

## How to judge greatness

Use separate outcomes. A utility can be loved, useful and easy to maintain while earning little. A large donated project can be financially viable without being an indie commercial model. A familiar-looking office suite can still fail the customer's document round trip. The cases in this report support different claims; none supplies a universal Linux app ranking.

| Meaning | Evidence worth collecting | Misleading substitute |
|---|---|---|
| User love | Specific repeated praise, voluntary return, recommendations, relief after recovery | Attractive launch screenshot or stars alone |
| Problem solving | A real document, transfer, backup or business operation completed correctly | Feature checklist |
| Downloads and retention | Successful first job; repeated useful work by cohort and package channel | Downloads including updates, or repository stars |
| Cash earned | Collected payments, refunds and plan mix | List price multiplied by downloads |
| Viable business | Maintainer compensation after support, distribution, hosting and acquisition | Gross donations or revenue without expenses |
| Maintainable code | Safe changes, supported dependencies, useful diagnostics, tested recovery | Small binary or fashionable language alone |
| Featured | Current curation criteria and an actual placement | Assuming toolkit choice guarantees editorial attention |

This is a proposed assessment framework. The report's primary financial disclosures and independent use accounts are evidence inputs, not controlled comparisons between apps.

## Strong and weak workflow choices

**Build around an identifiable job.** A focused backup app should make destination, last result and recovery legible. A document workbench should keep navigation, selection and inspection efficient. Do not copy the sparse screen of a one-action utility into a records application where users compare many rows. Pika, Dolphin, Zotero and the office reviews below illustrate these different demands.

**Native behavior is more than native appearance.** Focus, IME, file grants, window activation, notifications, accessible state and updates all affect daily work. A custom shell can succeed when it implements these; a stock GTK window can fail when it loses data or spins forever. These are engineering judgments supported by the platform contracts and failure cases, not a benchmark of frameworks.

**Choose a coherent desktop relationship.** GNOME's focused presentation, KDE's configurable workbench and a branded cross-platform client can each be appropriate. Arbitrary theming compatibility is not the same promise as respecting supported dark mode, font size and contrast. The theming disagreement below explains why “match every theme” is an expensive and contested requirement.

**Preserve user agency without outsourcing design.** Import, export, external editors, documented formats and sensible keyboard commands can make an app fit existing work. Eric Raymond's *The Art of Unix Programming* (2003), chapter 11, argues for familiar interfaces and delegating suitable tasks to tools users know. The accessible mirrored chapter was read directly after the author's site timed out. Treat it as historical design reasoning; its browser/Emacs examples do not override today's desktop shortcuts or justify a compulsory terminal. [Chapter excerpt](https://rus-linux.net/MyLDP/BOOKS/ArtProgr/ch11s01.html).

**Installation is part of the experience.** In a May 2025 Linux-switching diary, Tom's Hardware's Avram Piltch found FileZilla's archive download confusing and preferred Mission Center's separation of apps from processes. These are one user's task failures/preferences, not Linux prevalence estimates; his shell command examples are not installation instructions. Design implication: name the download format and next step, and group data around the user's intended action. [Diary](https://www.tomshardware.com/news/live/my-week-with-linux).

**Minimum window size is a workflow choice.** *LINUX Unplugged* episode 521 (2023), around 29:40–33:00, criticizes chat apps whose persistent chrome makes tiling impractical and tiny utilities expanded into mostly empty space. The transcript was read; audio was not independently checked. Its proposed GNOME Mosaic discussion was speculative, not a shipped platform requirement. The enduring test is useful composition at both narrow and large sizes. Current GNOME/KDE guidelines independently support adaptation. [Transcript](https://podscripts.co/podcasts/linux-unplugged/521-rethinking-gnome), [GNOME windows](https://developer.gnome.org/hig/patterns/containers/windows.html).

## App examples: dimensions of great and limitations

Community projects are reference products, not all sole-developer businesses. No sales, retention or profit ranking is supported by these pages.

| App | What to learn | Weakness, boundary, evidence type |
| --- | --- | --- |
| Pika Backup | A narrow, consequential task made legible: destination, last outcome, inclusion/exclusion lists, one backup action. Great rational value and GNOME polish. | Personal-file backup, not whole-system recovery. A real restoration matters more than setup screenshots: Jack Baty recovered an overwritten journal file in June 2026. One successful account is not a reliability rate. [App](https://apps.gnome.org/PikaBackup/), [user report](https://baty.net/notes/2026/06/pika-backup/). |
| Apostrophe | A writing canvas with restrained chrome, Markdown helpers, focus mode and export. Good example of emotional calm tied to a job. | Writing focus does not demonstrate reference management or enterprise document compatibility. Test exports with actual recipient files. Features are developer claims; screen directly inspected. [App](https://apps.gnome.org/Apostrophe/). |
| Resources | Overview-to-detail monitoring; separate apps/processes, labeled component graphs. The inspected CPU screen turns per-core detail into regular cards. | Joey Sneddon's 2023 critique favored glanceability over the old monitor's tiny graphs and warned that fast refresh consumes CPU. Historical review; current hardware support requires current checks. [App](https://apps.gnome.org/Resources/), [review](https://www.omgubuntu.co.uk/2023/10/resources-system-monitor-app-for-linux/amp). |
| Warp | Short human-shareable codes and a bounded send/receive flow; compatible with Magic Wormhole clients. Great focused problem solving. | Its official page says internet is required even though transfer can use the LAN. Do not sell it as fully offline LAN sharing. [App](https://apps.gnome.org/Warp/). |
| Obfuscate | A single-purpose image-redaction workflow avoids a full image editor's conceptual burden. | The inspected source describes redaction, not a security proof. A polished editor is no guarantee of irreversible export or metadata removal. Latest listed release is 0.0.10, March 2024; age alone does not prove abandonment. [App](https://apps.gnome.org/Obfuscate/). |
| Secrets | Uncluttered GNOME presentation over KeePass v4 databases; standards-based data can coexist with platform-specific UI. | Database compatibility alone does not prove feature parity, browser integration or sync safety. The product's simplicity is a scope choice. [App](https://apps.gnome.org/Secrets/). |
| Iotas | Offline notes, optional Nextcloud Notes sync, Shell search and partial loading of large collections. Markdown is optional. | Basic conflict detection; local storage is SQLite, not a directory of editable Markdown. Plain-file backup is CLI-based. Data ownership claims need exact storage/export semantics. [App](https://apps.gnome.org/Iotas/). |
| Planify | A richer GNOME task manager: inbox/today/schedule, projects, recurring tasks, multiple accounts and offline work with Todoist/CalDAV sync. Inspected dark screenshot has strong task hierarchy and colored navigation tiles. | Provider parity and conflicts require testing. Site's 424.6K downloads and 5.8K stars are developer-displayed counters, not retained users or revenue. Mobile uses provider apps. [Project](https://useplanify.com/). |
| Dolphin | Tabs, split panes and optional tools make repeated file operations efficient. Inspected screen retains compact menus, breadcrumb path, sidebar and large content region. | A 2026 How-To Geek review praises familiar paths and optional terminal; its claim that Dolphin became default in 2024 is wrong and was not used. Treat opinions separately from history. [App](https://apps.kde.org/dolphin/), [review](https://tech.yahoo.com/computing/articles/tried-every-major-file-manager-140013806.html). |
| Okular | Navigation, thumbnails, annotations and bookmarks support real document work across many formats. Good problem-solving and maintainable community reference. | Format support is not a promise of full PDF editing or every form/signature workflow. Validate the actual customer document. [App](https://apps.kde.org/okular/). |
| Kate | Multi-document work, splits, project context and optional power tools show how a focused editor can grow without becoming a mandatory IDE. | Rich features add choices and learning; not a pattern to copy into a one-action utility. [App](https://apps.kde.org/kate/). |
| KDE Itinerary | Organizes reservations and changing trip facts into useful travel context, including multiple travelers. Good example of turning imported data into an actionable timeline. | Listed as convergent/mobile-oriented; not every backend or transport operator provides equal real-time data. Do not claim worldwide data coverage. [App](https://apps.kde.org/itinerary/). |
| KeePassXC | Durable local password databases and specialist integration serve users who value control. | The FAQ’s X11-only claim is stale: 2.8.0 stable added Wayland Auto-Type on 2026-10-21. Required portals and remaining focus/title limitations still make desktop choice consequential. [Release](https://keepassxc.org/blog/2026-10-21-2.8.0-released/), [tagged guide](https://raw.githubusercontent.com/keepassxreboot/keepassxc/2.8.0/docs/topics/AutoType.adoc). |
| Joplin | Explicit conflict copies and note history preserve recovery paths in a cross-platform note workflow. | Its documented conflict process requires comparing versions; local is copied to Conflicts and remote replaces the working note. Recovery is safer than silent loss but still costly. Do not call sync frictionless. [Conflict guide](https://joplinapp.org/help/apps/conflict/). |
| Xournal++ | Pen pressure, layers, page previews, configurable tools and linked audio serve a genuine handwriting workflow. Great category fit beyond typed notes. | Requires device/input testing; a dense pen toolbar is not a model for a general todo app. No measured latency or palm-rejection claim made. [Project](https://xournalpp.github.io/). |
| Zotero | Collection/item/metadata panes plus saved searches, attachments and local snapshots support research retrieval. Items can appear in several collections without duplication. | A knowledge workbench demands learning; collection removal and library deletion must remain distinguishable. No adoption or revenue figure inferred. [Quick start](https://www.zotero.org/support/quick_start_guide). |
| LibreOffice | A long-term writer reports completing books in it; substantial work can succeed despite imperfect polish. | Same writer still finishes manuscripts in Word for publisher format requirements. Review of 24.2 criticizes numerous uneven UI layouts and style handling while praising improved visual integration. Scope/version matter. [Review](https://www.dedoimedo.com/computers/libreoffice-24-2-review.html). |
| ONLYOFFICE Desktop Editors | Familiar office composition and useful document features can ease migration for existing Office users. | 8.1 review found scaling, pale text, rigid style placement and cumbersome Open access. Reviewer opinion on KDE neon, 2024; not current regression proof. [Review](https://www.dedoimedo.com/computers/onlyoffice-desktop-editors-8-1.html). |

### A versioned feature matters more than a platform badge

**KeePassXC 2.8.0 shipped Wayland Auto-Type on 2026-10-21.** The dated stable announcement and GitHub release tag supersede the FAQ’s X11-only statement. Verified owning tagged source includes `src/autotype/wayland/AutoTypeWayland.cpp` and `docs/topics/AutoType.adoc`; this is released capability, not a development promise. [Stable announcement](https://keepassxc.org/blog/2026-10-21-2.8.0-released/), [release](https://github.com/keepassxreboot/keepassxc/releases/tag/2.8.0).

The guide requires RemoteDesktop and GlobalShortcuts portals. It lists support since Plasma 5.27/GNOME 48, with newer versions improving shortcut reconfiguration; older Plasma versions before 6.4 can repeatedly prompt. Wayland lacks title matching and active-window tracking here: users select entries, and focus changes during typing do not stop the sequence. IMEs can interfere. Permission persistence and keeping the remote-desktop session open are explicit settings. These are meaningful UX limits even after basic support ships. [2.8.0 tagged guide](https://raw.githubusercontent.com/keepassxreboot/keepassxc/2.8.0/docs/topics/AutoType.adoc). Do not recommend a blanket X11 workaround or call all compositor combinations equivalent.

## Data safety, work under strain and trust

**Saving is a product contract.** An editor should distinguish the live buffer, durable local save, remote acknowledgement and recoverable history. LibreOffice documents AutoRecovery and a previous-save backup separately; its `.BAK` can be overwritten by the next save. A 2026 user discussion asks for Google Docs-like continuous saving and reports confusion over these features. That is evidence of a mismatched expectation, not a measured LibreOffice failure rate. Choose explicit save or autosave per document workflow, then make its guarantees visible. [LibreOffice recovery](https://help.libreoffice.org/latest/en-GB/text/shared/guide/doc_autosave.html), [user discussion](https://www.reddit.com/r/libreoffice/comments/1qr40a4/can_libreoffice_autosave_every_step_of_my/).

**Sync success does not establish content correctness.** Joplin documents conflicting copies and manual reconciliation. In one April 2026 report, a user lost recent note text, found an older backup and questioned paying for sync; later comments left renewal undecided. The report cannot establish the cause, affected version, operating system or general reliability; this is a cross-platform workflow example. It does show why recoverable content and an understandable timeline matter to paid retention. [Conflict behavior](https://joplinapp.org/help/apps/conflict/), [user account](https://www.reddit.com/r/joplinapp/comments/1sgbapz/my_note_was_overwriitten_on_sync/).

**Local storage still needs failure design.** Use a transaction or safe whole-file replacement, check final commit errors and preserve the previous version. QSaveFile's direct-write fallback sacrifices the temporary-file protection; GIO can reject a save against a changed etag. These mechanisms address different risks: interrupted writes versus overwriting another editor's work. Test both. [QSaveFile](https://doc.qt.io/qt-6/qsavefile.html), [GIO replace](https://docs.gtk.org/gio/method.File.replace_contents.html).

**A live database is not an ordinary sync folder.** SQLite documents inconsistent copies, missing journals and broken network-filesystem locks as corruption causes. Use its backup API or another documented consistent snapshot, then sync the snapshot; do not promise that copying a busy database is safe. Keep recovery material paired with its database. This is a storage-specific constraint, not a rejection of user-controlled files. [SQLite corruption mechanisms](https://sqlite.org/howtocorrupt.html).

**Cross-device files need explicit limits.** Syncthing preserves competing versions and reports case conflicts; watcher notifications also need periodic reconciliation. A Linux app exchanging files with Windows or macOS must handle case collisions, external edits and delayed detection. Infer a product requirement: show unresolved conflicts and never silently choose a convenient spelling. [Syncthing synchronization](https://docs.syncthing.net/users/syncing.html).

**Permissions should explain the job.** File portals grant access to user-chosen files; a file filter is a convenience, not validation. Background and inhibition are separate capabilities. Request them for the task that needs them, handle denial, and end inhibition when work ends. Blanket home access or permanent sleep prevention obscures intent and adds support risk. [File chooser](https://flatpak.github.io/xdg-desktop-portal/docs/doc-org.freedesktop.portal.FileChooser.html), [background](https://flatpak.github.io/xdg-desktop-portal/docs/doc-org.freedesktop.portal.Background.html), [inhibit](https://flatpak.github.io/xdg-desktop-portal/docs/doc-org.freedesktop.portal.Inhibit.html).

The following are proposed acceptance scenarios, derived from those mechanisms and app cases—not claims of tests performed here:

| Scenario | Expected behavior | Consequence of a miss |
|---|---|---|
| Disk fills during Save | Keep dirty buffer and previous file; offer another destination; show failed save | False reassurance, then data loss on quit |
| USB/network mount disappears | Stop affected writes; preserve pending work; allow reconnect or Save Copy | Partial output or accidental creation under an empty mount point |
| App crashes during migration | Recover or roll back consistently; retain a usable backup and version metadata | App update makes years of records inaccessible |
| Two windows edit one object | Shared model or explicit revision conflict; avoid last-window-wins invisibly | One window overwrites the other's work |
| Offline for a week | Separate local availability, queued changes and remote state; reconcile on return | Duplicate sends, overwritten notes, false completion |
| Remote auth expires | Keep local reading/editing where valid; reconnect the affected account once | Login loop blocks unrelated work |
| Laptop sleeps mid-operation | Resume or report interruption; release stale UI state and revalidate network | Forever-running spinner or repeated external action |
| Huge import | Preview, cancellation boundary, bounded memory, skipped-row report, resumable work where useful | Freeze, out-of-memory kill or silent truncation |
| Hundreds of permission failures | Summarize by cause, with affected items and retry | Modal storm makes the app unusable |
| Battery saver / low memory | Throttle indexing and previews; retain edits before discarding caches | Utility costs more attention and energy than it saves |
| Stale shared folder or revoked grant | Explain scope and recovery; do not reinterpret missing as deleted | Mass deletion propagates to other devices |
| Uninstall and reinstall | State what remains local, what remains remote and how to restore | User expects erasure or recovery the app never supplied |

## Specific screens and components: 104 practical details

These are desktop recommendations unless labelled inference. GNOME and KDE conventions are distinguished; exceptions follow the job.

### Start and home

1. **Start with the job.** A small utility should expose its main action immediately. Avoid a preferences wizard before the first useful operation. Complex mandatory setup can justify a wizard; optional teaching must remain skippable. [KDE simple](https://develop.kde.org/hig/simple_by_default/).

2. **Choose devices sensibly.** Preselect the last relevant device; skip a picker when only one exists. Requiring confirmation on every scan or backup wastes attention. Keep selection visible when choosing the wrong device has consequences. [KDE simple](https://develop.kde.org/hig/simple_by_default/).

3. **Separate onboarding from empty results.** A first-run illustration may introduce an app; an empty search needs restrained status. Repeating celebratory onboarding art after every unsuccessful query misreads the situation. [GNOME placeholders](https://developer.gnome.org/hig/patterns/feedback/placeholders.html).

4. **Offer a next step.** Pair an empty-state heading with a relevant Add/Open action or short instruction. A large icon alone cannot explain how to begin. Do not manufacture an empty home when useful content can open directly. [GNOME placeholders](https://developer.gnome.org/hig/patterns/feedback/placeholders.html).

### Header and navigation

5. **Keep the GNOME header sparse.** Align primary actions at the leading edge, heading centrally and menus at the trailing edge. Packing every command into it reduces both recognition and narrow-window flexibility. [Header bars](https://developer.gnome.org/hig/patterns/containers/header-bars.html).

6. **Leave a drag region.** A header filled edge-to-edge with controls makes ordinary window movement awkward. Preserve blank space and tooltips for controls; do not make users discover a one-pixel drag target. [Header bars](https://developer.gnome.org/hig/patterns/containers/header-bars.html).

7. **Match header actions to content.** Change controls with the current view/mode. A document's actions should not linger over an unrelated home. GNOME favors mostly flat header controls; action-dialog buttons have different styling needs. [Header bars](https://developer.gnome.org/hig/patterns/containers/header-bars.html).

8. **Keep Back recognizable.** In left-to-right GNOME layouts, place Back top-left and update the heading on navigation. An unexplained close icon for ordinary history breaks recognition. Support navigation keys as well. [Browsing](https://developer.gnome.org/hig/patterns/nav/browsing.html).

9. **Distinguish destinations from documents.** Use a view switcher for a small fixed set; tabs for user-opened documents. Mixing permanent sections and disposable documents in one strip makes closing and persistence ambiguous. [View switchers](https://developer.gnome.org/hig/patterns/nav/view-switchers.html), [Tabs](https://developer.gnome.org/hig/patterns/nav/tabs.html).

10. **Name views as places.** Short nouns such as Archives or Schedule work better than command phrases. GNOME suggests about three to five views; beyond that, assess a sidebar. This is guidance, not a universal count limit. [View switchers](https://developer.gnome.org/hig/patterns/nav/view-switchers.html).

11. **Adapt the switcher.** Move a GNOME switcher to the bottom at narrow widths using the supplied components. Shrinking labels until unreadable preserves neither discoverability nor useful space. [View switchers](https://developer.gnome.org/hig/patterns/nav/view-switchers.html).

12. **Use sidebars for repeated switching.** Many or changing destinations justify a sidebar. A permanent navigation column is wasteful in immersive writing or viewing. Put controls for its list above that list. [Sidebars](https://developer.gnome.org/hig/patterns/nav/sidebars.html).

13. **Order for retrieval.** A changing conversation list may need recency; a fixed task hierarchy may need user order. Alphabetizing everything ignores the user's retrieval strategy. Keep each row's key information dominant. [Sidebars](https://developer.gnome.org/hig/patterns/nav/sidebars.html).

14. **Front-load tab identity.** Put the distinguishing document name before repeated suffixes. Long shared prefixes make ellipsized tabs indistinguishable. Show an icon only when it adds information. [Tabs](https://developer.gnome.org/hig/patterns/nav/tabs.html).

15. **Make tabs manageable.** Provide a tab context menu and standard close/switch shortcuts; offer Move to New Window when supported. Avoid direction-named commands that become wrong in right-to-left layouts. [Tabs](https://developer.gnome.org/hig/patterns/nav/tabs.html).

### Lists and detail

16. **Choose the right list.** Boxed lists suit modest, mostly static settings or recent-item groups. Large changing records need a list/column view. Rendering a business dataset as hundreds of individually assembled settings cards is the wrong model. [Boxed lists](https://developer.gnome.org/hig/patterns/containers/boxed-lists.html), [List views](https://developer.gnome.org/hig/patterns/containers/list-column-views.html).

17. **Keep rows regular.** Use a small, consistent set of fields; distinguish primary and secondary text. Every row with a different badge and action layout makes comparison slower. Dense professional tables can legitimately show more. [List views](https://developer.gnome.org/hig/patterns/containers/list-column-views.html).

18. **Expose sorting.** Show which column and direction determine the order. A clickable heading without a state marker makes repeated clicks a guessing game. Use the toolkit's convention rather than hand-drawing a reversed indicator. [List views](https://developer.gnome.org/hig/patterns/containers/list-column-views.html).

19. **Make a settings row one target.** Clicking the background should operate its control; keyboard focus should reach the control without a duplicate stop on the row. Avoid tiny switches embedded in otherwise inert slabs. [Boxed lists](https://developer.gnome.org/hig/patterns/containers/boxed-lists.html).

20. **Show navigation affordances.** A boxed row opening another page needs a trailing arrow. A switch row should look and act like a setting, not like a hidden drill-down. Usually keep one control per row. [Boxed lists](https://developer.gnome.org/hig/patterns/containers/boxed-lists.html).

21. **Make reorder accessible.** Drag handles help pointer users; include Move Up/Down alternatives. A drag-only list fails keyboard and assistive users even when its animation looks polished. [Boxed lists](https://developer.gnome.org/hig/patterns/containers/boxed-lists.html).

22. **Select in batches where batches matter.** GNOME selection mode fits intensive collection management with several actions. Adding a mode for one rarely used action adds friction. A permanent individual action may suffice. [Selection modes](https://developer.gnome.org/hig/patterns/containers/selection-mode.html).

23. **Expose selection state.** Show the selected count, a cancel route and actions for that selection. Changing click behavior without a visible mode boundary invites operations on unintended records. [Selection modes](https://developer.gnome.org/hig/patterns/containers/selection-mode.html).

24. **Do not hide the main edit task.** If editing defines the collection, keep editing controls available. An Edit gate suits a secondary restructuring task, not every interaction in a task manager. [Selection modes](https://developer.gnome.org/hig/patterns/containers/selection-mode.html).

### Search

25. **Search and Find differ.** Search filters a collection; Find locates text inside the current document. Name and scope them accordingly. Reusing one ambiguous field for both produces surprising results. [Search](https://developer.gnome.org/hig/patterns/nav/search.html).

26. **Make search reachable.** GNOME supports a search button, Ctrl+F and type-to-search where appropriate. A search-first app can keep its field visible. Do not intercept ordinary typing in an editor. [Search](https://developer.gnome.org/hig/patterns/nav/search.html); editor exception is inference.

27. **Show results promptly.** Prefer live, incremental results and a distinct no-results state. Waiting silently for a whole remote collection looks frozen. GNOME recommends global search; explicitly scoped professional tools need clear scope labels. [Search](https://developer.gnome.org/hig/patterns/nav/search.html); scope exception is inference.

28. **Support imperfect recall.** Match useful associated metadata and tolerate small errors. Exact-title-only lookup fails users who remember a client or place. Retain browsing because not everyone searches. [Search](https://developer.gnome.org/hig/patterns/nav/search.html).

### Menus and settings

29. **Separate app from item menus.** Preferences/About belong to the GNOME primary menu; document operations belong to a secondary one. Duplicating the full app menu everywhere confuses scope. [Menus](https://developer.gnome.org/hig/patterns/controls/menus.html).

30. **Group commands by task.** Use short logical groups and shallow menus. Nested cascades and mixed command/toggle groups increase scanning and pointer effort. GNOME suggests 3–12 menu items, not an arbitrary huge command warehouse. [Menus](https://developer.gnome.org/hig/patterns/controls/menus.html).

31. **Keep settings states stable.** Use checked/radio menu items for settings; reserve changing labels for obvious opposite actions such as Play/Pause. A setting whose label flips meaning is harder to inspect. [Menus](https://developer.gnome.org/hig/patterns/controls/menus.html).

32. **Name the menu accessibly.** GNOME calls its primary menu Main Menu, with Preferences, shortcuts/help where present, and About near the end. Do not rely on the visual hamburger alone to identify it. [Menus](https://developer.gnome.org/hig/patterns/controls/menus.html).

33. **Settings should represent valid workflows.** Add a choice when users need different supported behavior. Avoid a switch for every indecision or bug workaround. KDE explicitly treats indiscriminate customization as poor design. [KDE powerful](https://develop.kde.org/hig/powerful_when_needed/).

34. **Name the subject, not “Advanced.”** Put richer settings on a descriptive subpage or expandable section. “Advanced” says nothing about its contents and varies with the user's job. [KDE powerful](https://develop.kde.org/hig/powerful_when_needed/).

35. **Keep related preferences together.** Avoid controls on one GNOME preference view silently affecting another view. Hidden dependencies make settings hard to reason about; group the choice and its consequences. [View switchers](https://developer.gnome.org/hig/patterns/nav/view-switchers.html).

36. **Offer accelerators after discovery.** Shortcuts and context menus speed repeated work, but primary operations must also be visible. A keyboard-only “feature” is effectively absent for unfamiliar users. KDE encourages assignable shortcuts. [KDE powerful](https://develop.kde.org/hig/powerful_when_needed/).

### Visual precision

37. **Use a restrained type hierarchy.** Adopt system fonts and relative standard styles. Hard-coded sizes and many weights make scaling brittle and hierarchy noisy. Current GNOME names Adwaita Sans; do not hard-code yesterday's Cantarell assumption. [Typography](https://developer.gnome.org/hig/guidelines/typography.html).

38. **Keep text clear.** Avoid textured backgrounds, gratuitous all caps and decorative italics in interface labels. Use weight/size sparingly to distinguish meaning. Rich document content may legitimately have its own typography. [Typography](https://developer.gnome.org/hig/guidelines/typography.html).

39. **Judge density at real scale.** Test common fractional scaling with real documents. ONLYOFFICE 8.1's reviewer found 100% too small and 125% disproportionate on a 14-inch KDE laptop; screenshots alone concealed the discomfort. Historical case, not a claim about current releases. [Dedoimedo, 2024-07-26](https://www.dedoimedo.com/computers/onlyoffice-desktop-editors-8-1.html).

40. **Keep repeated tools stable.** A style picker should remain easy to revisit as document selection changes. A long-term LibreOffice user disliked its jumping style list and double-click application. This is a concrete expert complaint, not consensus or a verified current defect. [LibreOffice 24.2 review, 2024-07-08](https://www.dedoimedo.com/computers/libreoffice-24-2-review.html).


### Documents, saving and recovery

41. **Name the save state.** Use “Saved on this device” separately from sync state; do not label a queued upload “All changes saved.” Offline editors need a visible local guarantee. Recommendation from the recovery/sync distinction above; a purely local app needs only the local state. [LibreOffice recovery](https://help.libreoffice.org/latest/en-GB/text/shared/guide/doc_autosave.html).

42. **Keep failed saves editable.** Leave the document dirty and offer Save Copy after a write failure; do not close the buffer after an attempted save. QSaveFile reports failure at commit, so success UI belongs after that result. [QSaveFile](https://doc.qt.io/qt-6/qsavefile.html).

43. **Protect the old file.** Use safe replacement for whole documents; do not truncate the original before serialization succeeds. Direct-write fallback needs a deliberate tradeoff where directory permissions prevent a temporary file. [QSaveFile](https://doc.qt.io/qt-6/qsavefile.html).

44. **Detect external edits.** Compare a revision/etag before overwriting and offer reload, comparison or Save Copy. A watcher alone is not an overwrite guard. GIO exposes this check; immutable exports do not need it. [GIO replacement](https://docs.gtk.org/gio/method.File.replace_contents.html).

45. **Make history recover without destroying the present.** Preview a dated revision and restore a copy before replacement. Joplin restores into a separate notebook; copying that principle avoids a second mistaken overwrite. [Note history](https://joplinapp.org/help/apps/note_history/).

46. **Explain shared retention.** Show the effective history window across devices; a local “100 days” control must not imply 100 days if another device purges at 30. Joplin documents this exact minimum-across-devices behavior. [Note history](https://joplinapp.org/help/apps/note_history/).

47. **Separate cache from records.** Put rebuildable thumbnails in cache, durable records in data, and logs/session history in state. A “Clear cache” button must not delete the only working copy. Follow XDG locations; portable mode needs an explicit exception. [XDG base directories](https://specifications.freedesktop.org/basedir/latest/).

48. **Export a consistent snapshot.** Provide an export/backup operation that coordinates with the database. Do not tell users to copy a changing SQLite file with a file manager. Include attachments and schema version in the product's export design. [SQLite backup hazards](https://sqlite.org/howtocorrupt.html).

### Open, import, export and print

49. **Use the desktop file chooser.** Parent it to the initiating window and preserve cancellation as a normal outcome. A custom path textbox alone loses discoverability and sandbox grants; expert path entry can supplement the chooser. [FileChooser](https://flatpak.github.io/xdg-desktop-portal/docs/doc-org.freedesktop.portal.FileChooser.html).

50. **Validate selected content.** Check format after selection; do not trust extension filters to enforce it. Explain unsupported/corrupt content without blaming the user. Portal filters may permit non-matching files. [FileChooser](https://flatpak.github.io/xdg-desktop-portal/docs/doc-org.freedesktop.portal.FileChooser.html).

51. **Treat permission loss as recoverable.** Let users choose a file again when a stored grant or location stops working; do not replace their recent-document entry with an empty document. This is a recommendation derived from portal access, not a promise that every grant survives reinstall. [FileChooser](https://flatpak.github.io/xdg-desktop-portal/docs/doc-org.freedesktop.portal.FileChooser.html).

52. **Preview import interpretation.** Show encoding, separator, date and numeric interpretation on real rows before committing. GnuCash's CSV importer is a useful reference. Do not make an apparently successful import silently change amounts. [GnuCash import](https://code.gnucash.org/docs/C/gnucash-manual/trans-import.html).

53. **Show duplicate decisions.** Display new, matched and skipped records; allow correction of automatic matches. Importing the same bank file twice should not quietly double totals. Scope this to record imports, not arbitrary copied documents. [GnuCash import](https://code.gnucash.org/docs/C/gnucash-manual/trans-import.html).

54. **Keep source-to-destination mapping visible.** Ask which account or collection receives imported data; retain a reusable mapping only after confirmation. A guessed account is useful assistance, not authority. [GnuCash import](https://code.gnucash.org/docs/C/gnucash-manual/trans-import.html).

55. **State interchange limits.** Distinguish opening a DOCX/XLSX from faithful round-trip output and executable VBA compatibility. Give a specific loss warning where known, not an alarming generic dialog on every save. LibreOffice's ongoing OOXML fixes show why sample-file validation matters. [26.8.1 fixes](https://blog.documentfoundation.org/blog/2026/10/02/libreoffice-26-8-1/), [VBA limits](https://help.libreoffice.org/latest/en-GB/text/sbasic/shared/vbasupport.html).

56. **Print the selected scope.** Make current page, selection, range and all distinguishable; format using chosen paper/margins before sending. The Print portal separates preparation from printing; hard-coded A4 output breaks Letter users and labels. [Print portal](https://flatpak.github.io/xdg-desktop-portal/docs/doc-org.freedesktop.portal.Print.html).

57. **Keep print numbering human.** Display one-based page numbers and translate correctly to underlying ranges. The portal uses zero-based range values. Test the first, last and disjoint pages; a preview that disagrees with output wastes work. [Print portal](https://flatpak.github.io/xdg-desktop-portal/docs/doc-org.freedesktop.portal.Print.html).

### Offline, sync and accounts

58. **Show what is cached.** “Available offline” should cover the content users need, including attachments where promised. Evolution distinguishes downloaded headers from bodies and supports folder-specific caching; merely listing a title is insufficient. [Evolution offline](https://help.gnome.org/evolution/mail-working-offline.html).

59. **Scope Offline controls honestly.** If a switch pauses mail only, say so; do not imply calendars and contacts stop networking too. Evolution explicitly documents that boundary. A unified offline mode needs a unified implementation. [Evolution offline](https://help.gnome.org/evolution/mail-working-offline.html).

60. **Expose conflict copies near the original.** Offer compare/keep-both before users discard either version; do not bury conflicts among ordinary folders without a count. Joplin's documented manual merge burden motivates this recommendation. [Joplin conflicts](https://joplinapp.org/help/apps/conflict/).

61. **Make sync readiness visible before editing stale data.** Show pending download/reconciliation without blocking safe local reading. Requiring users to remember a manual sync ritual is fragile; Joplin documents that ritual as mitigation. [Joplin conflicts](https://joplinapp.org/help/apps/conflict/).

62. **Surface filename collisions.** Preserve both `Report` and `report` until the user chooses a portable name; do not lowercase silently. Cross-device sync can encounter case-insensitive targets even when Linux accepts both. [Syncthing case conflicts](https://docs.syncthing.net/users/syncing.html).

63. **Reconcile beyond filesystem events.** Refresh after reconnect and periodically check watched state; do not assume every external edit generated a delivered event. Use a bounded scan for large collections. [Syncthing scanning](https://docs.syncthing.net/users/syncing.html).

64. **Show the acting account.** Put the sender/workspace near a consequential action, with a predictable default and explicit override. Evolution's folder/recipient sender rules illustrate the value and complexity. Do not hide identity in Settings. [Send account overrides](https://help.gnome.org/evolution/mail-composer-send-account-overrides.html).

### Calendar, tasks and business forms

65. **Show appointment time zones.** Let global viewing zone and event zone differ; display a second zone when coordination is common. Changing the laptop zone must not silently reinterpret a fixed meeting time. [Evolution zones](https://help.gnome.org/evolution/calendar-timezones.html.oc).

66. **Preview recurrence as a sentence.** Show frequency, weekdays and end condition together; offer explicit exceptions. A scattered set of dropdowns can encode an unintended schedule. Evolution demonstrates sentence-like composition. [Recurrence](https://help.gnome.org/evolution/calendar-recurrence.html).

67. **Keep form labels after entry.** Use persistent labels when the value does not explain the field; placeholders alone disappear. GNOME permits placeholders for obvious fields, so do not turn every search box into a bulky form. [Text fields](https://developer.gnome.org/hig/patterns/controls/text-fields.html).

68. **Validate without fighting typing.** Preserve incomplete input and explain what must change before submission. Do not mark every intermediate keystroke as a failure. GNOME favors useful positive feedback; KDE documents inline invalid-state feedback. Apply timing to the field's semantics. [GNOME fields](https://developer.gnome.org/hig/patterns/controls/text-fields.html), [KDE input](https://develop.kde.org/hig/getting_input/).

69. **Use bounded controls where they help.** A spin control suits exact counts; a slider suits approximate adjustment; pair them when both matter. A percentage typed into an unlabeled free-text field invites ambiguity. [KDE input](https://develop.kde.org/hig/getting_input/).

70. **Keep switch state and readiness distinct.** A requested service may still be starting. Show pending or failed state rather than falsely indicating active service; disable unavailable actions with a reason. GTK switches support state/position distinction. [GNOME switches](https://developer.gnome.org/hig/patterns/controls/switches.html).

### Focus, text input and accessibility

71. **Respect composition.** Let the input method commit text before handling Enter as Send/Search. Raw key handlers can break CJK input and composed characters; use toolkit text controls or implement the full IM context. [GTK input methods](https://docs.gtk.org/gtk4/class.IMContext.html).

72. **Keep the candidate UI at the caret.** Report cursor location and focus changes in custom editors; do not treat text input as character callbacks alone. Test scrolling and multi-monitor movement during composition. [GTK input methods](https://docs.gtk.org/gtk4/class.IMContext.html).

73. **Provide meaningful accessible names.** A trash icon needs an action name and an item context where repeated. Stock controls help but do not explain a custom canvas automatically. Verify with the display off and Orca running. [GNOME accessibility](https://developer.gnome.org/hig/guidelines/accessibility.html).

74. **Distinguish focus from selection.** A selected row in an inactive pane must not look like keyboard focus. Test all primary tasks without a pointer; never put essential instructions only in hover tooltips. [KDE accessibility](https://develop.kde.org/hig/accessibility/).

75. **Reflow large text.** Test system large text and high contrast across populated forms, errors and dialogs. Do not certify accessibility from a normal-size empty window. Allow wrapping or expansion rather than hiding critical labels. [GNOME accessibility](https://developer.gnome.org/hig/guidelines/accessibility.html).

76. **Honor reduced motion.** Navigation still needs a clear destination when animations are disabled; loading needs a non-moving state indicator. KDE specifically asks for this test. Do not make motion the only evidence of work. [KDE accessibility](https://develop.kde.org/hig/accessibility/).

77. **Keep touch usable without hover.** Make controls reachable with touch and the on-screen keyboard; provide a non-drag route for important operations. This matters on convertible laptops even when phones are excluded. [GNOME accessibility](https://developer.gnome.org/hig/guidelines/accessibility.html), [KDE accessibility](https://develop.kde.org/hig/accessibility/).

78. **Mirror structure, preserve meaning.** Test RTL layout and directional icons; keep content-specific direction, such as code, appropriate to its meaning. Absolute pixel positioning makes this harder. Qt layouts support mirroring, but still require inspection. [KDE layout](https://develop.kde.org/hig/layout_and_nav/).

### Dialogs, progress and interruption

79. **Name the action in confirmations.** Use Delete/Replace/Disconnect rather than OK. Keep cancel predictable and do not make destructive actions the Enter default. GNOME specifies cancel before affirmative in reading order; use toolkit ordering across desktops. [GNOME dialogs](https://developer.gnome.org/hig/patterns/feedback/dialogs.html).

80. **Prefer recoverable removal.** Offer Undo for reversible deletion; reserve confirmation for consequences that cannot be undone. A habitual click-through dialog adds little protection. Sensitive final erasure needs a different contract from ordinary trash. [GNOME dialogs](https://developer.gnome.org/hig/patterns/feedback/dialogs.html).

81. **Parent and focus dialogs.** Open in response to the initiating action, attach to its window and put focus on the next useful control. Do not leave a hidden modal behind another window. [GNOME dialogs](https://developer.gnome.org/hig/patterns/feedback/dialogs.html).

82. **Keep work progress beside the work.** Show a useful count/size or honest estimate; do not animate an invented percentage. Use indeterminate progress while totals are unknown. Separate progress windows obscure cancellation semantics. [GNOME progress](https://developer.gnome.org/hig/patterns/feedback/progress-bars.html).

83. **Define Cancel's boundary.** Tell users whether completed items remain; show partial results after cancellation. Provide pause/cancel for expensive batches where feasible. A disappearing spinner must not imply every external effect was reversed. Recommendation extending [GNOME progress](https://developer.gnome.org/hig/patterns/feedback/progress-bars.html).

84. **Make errors actionable.** Show what failed, which work is safe and a recovery action; retain technical details behind Copy Details. Avoid raw D-Bus errors as the only explanation. KDE explicitly ranks actionable recovery above error descriptions alone. [KDE status](https://develop.kde.org/hig/status_changes/).

85. **Use notifications outside the active workflow.** Keep local confirmation in the app; use system notifications for relevant background events. Withdraw stale notices and leave equivalent information in the window, since notices may be missed. [GNOME notifications](https://developer.gnome.org/hig/patterns/feedback/notifications.html).

86. **Batch noisy events.** Summarize many incoming messages and let users reduce interruptions. Clicking should reach the relevant item, not an unrelated home screen; do not duplicate Open as both default action and button. [GNOME notifications](https://developer.gnome.org/hig/patterns/feedback/notifications.html).

### Lifecycle, security and desktop integration

87. **Separate close from quit deliberately.** Closing one document window should not close unrelated documents. Background-service tools need an explicit continuing-state explanation and a reliable way back. GNOME permits both single- and multi-window apps. [GNOME windows](https://developer.gnome.org/hig/patterns/containers/windows.html).

88. **Restore useful geometry.** Restore the last size when restoring content, but let users resize and tile. Avoid a huge blank utility window or a document window too small to read. Do not rely on exact absolute placement across compositors. [GNOME windows](https://developer.gnome.org/hig/patterns/containers/windows.html).

89. **Do not require a tray icon to recover the app.** Provide ordinary launcher activation and a main-window entry point. KDE's current HIG even treats tray use as a last resort; a background utility may justify it but should make it opt-in. [KDE status](https://develop.kde.org/hig/status_changes/).

90. **Ask for autostart in context.** Explain the recurring job and show whether permission was granted. Do not silently recreate an autostart entry after the user disables it. The Background portal treats startup and background permission as explicit results. [Background portal](https://flatpak.github.io/xdg-desktop-portal/docs/doc-org.freedesktop.portal.Background.html).

91. **Release sleep inhibition.** Inhibit only for work that needs it, with a readable reason; close the request on finish/cancel. A note app's open window should not keep a laptop awake all night. [Inhibit portal](https://flatpak.github.io/xdg-desktop-portal/docs/doc-org.freedesktop.portal.Inhibit.html).

92. **Show actual global shortcuts.** Display the accepted binding returned by the portal, not merely the requested combination. Registration can return a subset, including none; keep an in-window action available. [GlobalShortcuts](https://flatpak.github.io/xdg-desktop-portal/docs/doc-org.freedesktop.portal.GlobalShortcuts.html).

93. **Store secrets with a defined recovery story.** Use an available secret service/portal, handle locked or missing storage, and explain any need to sign in again. The Secret portal supplies a per-app opaque secret; it is not a portable backup of credentials. [Secret portal](https://flatpak.github.io/xdg-desktop-portal/docs/doc-org.freedesktop.portal.Secret.html).

94. **Treat external opening as data exposure.** An encrypted attachment opened in another app needs a temporary plaintext representation. Explain the boundary for sensitive workflows and avoid claiming encryption protects an already-open viewer. KeePassXC documents its extraction flow. [KeePassXC guide](https://keepassxc.org/docs/KeePassXC_UserGuide).

95. **Keep sensitive display optional.** Mask secrets, provide a deliberate reveal action and keep keyboard copy efficient. Do not assume screenshot protection documented for Windows/macOS also exists on Linux. Verify each platform capability separately. [KeePassXC guide](https://keepassxc.org/docs/KeePassXC_UserGuide).

96. **Accept launch arguments safely.** Handle filenames/URIs through the desktop entry contract and argument arrays. Do not concatenate a filename into shell code; spaces, quotes and percent sequences are normal data. [Desktop Exec specification](https://specifications.freedesktop.org/desktop-entry/latest/exec-variables.html).

### Discovery, purchase and support

97. **Show the shipped Linux UI.** Put populated, representative screens in the listing; avoid promotional overlays that conceal the workflow. Flathub quality checks distinguish promotion eligibility from basic publication. [Quality guidelines](https://docs.flathub.org/docs/for-app-authors/metainfo-guidelines/quality-guidelines).

98. **Explain publisher identity accurately.** Link the official package and support channel. A Flathub verified badge establishes authorized publishing, not an independent security audit or reliability guarantee. [Verification](https://docs.flathub.org/docs/for-app-authors/verification).

99. **Keep failure reports useful and private.** Offer a copyable version/package/backend summary and a redacted log preview. Do not require users to paste an entire home-directory path inventory into a public issue. This is a support-design recommendation extending KDE's actionable-error guidance. [KDE status](https://develop.kde.org/hig/status_changes/).

100. **Keep paid entitlement separate from data possession.** Explain trial expiry, offline allowance, updates and support terms before purchase; preserve a practical export route when service ends. The commercial cases below show different published arrangements, not one Linux pricing convention. This is a product recommendation, not a measured conversion claim.

### Further desktop conventions

101. **Keep clipboard contracts separate.** Normal Copy/Paste and primary selection are distinct toolkit channels. Test both when supporting selection-based paste; do not overwrite the explicit clipboard merely because text was selected. GDK can emulate primary selection locally where a backend lacks it, so do not promise cross-app behavior everywhere. [Primary clipboard](https://docs.gtk.org/gdk4/method.Display.get_primary_clipboard.html), [Clipboard](https://docs.gtk.org/gdk4/class.Clipboard.html).

102. **Show the drop consequence.** Distinguish copy, move and link; preview the destination and reject unsupported data visibly. Commit a move only after the destination accepts it. GTK exposes negotiated actions and an async target for larger transfers; do not block the UI while fetching dragged data. [GTK drag and drop](https://docs.gtk.org/gtk4/drag-and-drop.html).

103. **Use recognizable shortcuts.** GNOME's Ctrl+O/S/F, Ctrl+W and Ctrl+Q have separate meanings; Alt+Left navigates back. Keep system window-management combinations free. Terminal-like components may need their established copy/paste exceptions; document them rather than globally changing editing behavior. [Shortcut reference](https://developer.gnome.org/hig/reference/keyboard.html).

104. **Match preference controls to apply behavior.** KDE recommends switches for immediate effect and checkboxes for other cases; keep labels stable. Do not make an instant-looking switch silently wait for Apply. Follow the chosen desktop/component contract, not a universal claim that all Linux preferences autosave. [KDE input](https://develop.kde.org/hig/getting_input/).

## Visual directions, directly inspected

**Focused Adwaita utility.** Pika has a quiet pale surface, rounded grouped rows, subordinate explanatory text and a single accent action. Its tabs correspond to backup, archives and schedule. Resources adds a navigation sidebar and repeatable graph cards without changing the control language. Fits small tools and comprehensible status. Risk: too much card padding can hide the useful dataset. Keep actual operation state more prominent than decorative reassurance. These are observations of official screenshots, not live usability findings.

**Writing canvas.** Apostrophe presents a large uncluttered document, compact header, quiet bottom formatting tools and document statistics. The document's typography leads. Fits composition where chrome competes with thought. Risk: hiding every tool can make formatting/export discoveries difficult; retain menu/keyboard routes and optional helpers. Light, dark and sepia options are published features. Static inspection cannot establish caret movement, transition quality or distraction in daily use.

**Configurable desktop workbench.** Dolphin's screenshot shows a compact menubar/toolbar, editable-looking breadcrumb, places sidebar, file grid and status information. This preserves screen area for many objects; split/terminal features are available in official documentation. Fits frequent file/project work and users with established habits. Risk: every pane visible at once overwhelms novices. The design direction is purposeful density, not a requirement for tiny targets or obsolete colors.

**Branded productivity within native structure.** Planify's dark screenshot uses colored destination tiles, counts, icons and a dense project sidebar, paired with a restrained chronological task list and a conspicuous add button. Fits repeated capture and planning. Risks: color categories can overwhelm; brand colors must not become the only state cue. This is one live product's sensibility, not evidence of a Linux-wide trend.

Published screens inspected on 2026-11-08: [Pika](https://static.gnome.org/catalog/app-screenshot/org.gnome.World.PikaBackup/image-1_orig.png), [Apostrophe](https://static.gnome.org/catalog/app-screenshot/org.gnome.gitlab.somas.Apostrophe/image-1_orig.png), [Resources](https://static.gnome.org/catalog/app-screenshot/org.gnome.Resources/3.png), [Dolphin](https://cdn.kde.org/screenshots/dolphin/dolphin.png), [Planify](https://raw.githubusercontent.com/alainm23/planify/master/data/resources/screenshot/screenshot-04.png). Screenshot app versions are not supplied; do not call them a hands-on audit of current builds. Motion inspection is documented below.

### Disagreement and historical context

GNOME designers argue that arbitrary distribution stylesheets can break contrast, controls and documentation consistency. Tobias Bernard's 2018 essay shows concrete breakages, including an invisible Create button. The independent-app open letter also raises icon semantics and brand ownership. These are developer positions with examples, not a survey of all Linux users. KDE meanwhile treats system-level styling as a legitimate place for user preference. Separate supported light/dark/accent/font behavior from arbitrary stylesheet replacement. [Essay](https://blogs.gnome.org/tbernard/2018/10/15/restyling-apps-at-scale/), [letter](https://stopthemingmy.app/), [KDE powerful](https://develop.kde.org/hig/powerful_when_needed/).

Dedoimedo's office reviews value density, stable tool locations and readable scaling more than a fashionable silhouette. His anti-touch generalization is opinion, not universal evidence. The concrete regressions are useful test cases. Conversely, Resources' reviewer values larger, glanceable charts. Neither “denser” nor “more spacious” is universally better; identify what users must compare and how often.

## Design resources worth using

- **GNOME HIG and resources:** actual widget patterns, Icon Library, Typography, App Icon Preview, Symbolic Preview, palette, mockup/icon SVG templates, Adwaita Demo and GTK inspector. Good route from composition to implementable controls. GNOME warns that older design repository material may be outdated; a mockup is not shipped behavior. [Resources](https://developer.gnome.org/hig/resources.html).
- **Apps for GNOME:** curated shipped apps with screenshots and source/issue links; useful for narrowly scoped tools. Curation expresses GNOME philosophy, not market leadership. Read individual app licenses before copying code/assets. [Catalog](https://apps.gnome.org/).
- **KDE applications and HIG:** browse mature workbenches and newer convergent apps separately. The catalog is broad and is not a uniform quality endorsement. Kirigami Gallery and source apps let designers examine real component states rather than infer behavior from mockups. [Catalog](https://apps.kde.org/), [HIG](https://develop.kde.org/hig/), [Kirigami next steps](https://develop.kde.org/docs/getting-started/kirigami/introduction-next_steps/).
- **libadwaita style classes:** implementable suggested/destructive/flat styles and component-specific examples. The live main documentation read here identifies itself as 1.11.alpha; confirm against your supported stable runtime before adopting recent classes. [Reference](https://gnome.pages.gitlab.gnome.org/libadwaita/doc/main/style-classes.html).
- **Independent writing:** OMG! Ubuntu supplies detailed app/release screenshots; Dedoimedo supplies opinionated, longitudinal office/desktop critiques; Jack Baty's short use reports expose real recovery outcomes. None is a controlled UX laboratory. Keep dates and distinguish one user's preference from consensus.

- **Adwaita Sans / Mono:** GNOME's source provides an Inter-derived UI face and an Iosevka-derived monospace companion under SIL OFL 1.1. Useful for GNOME mockups; production UI should normally inherit system choices. Bundling requires the supplied notices/license; document text does not inherit the font license. [Source and lineage](https://github.com/GNOME/adwaita-fonts), [license](https://raw.githubusercontent.com/GNOME/adwaita-fonts/main/LICENSE).
- **Breeze icons:** coherent KDE actions/devices/status assets. The artwork's own COPYING-ICONS specifies LGPL-3.0-or-later and GUI-use clarification; do not rely on GitHub's aggregate license badge. Use semantic theme names where supported and package required assets deliberately. [Artwork license](https://raw.githubusercontent.com/KDE/breeze-icons/master/COPYING-ICONS).
- **GNOME symbolic icons:** start from the HIG's Icon Library/development kit. Adwaita's core icon repository explicitly describes itself as private and warns that it supplies no stable reuse API. Arbitrary names working on the developer's desktop are not a distribution contract. [Owning repository](https://github.com/GNOME/adwaita-icon-theme).

### Recorded motion and continuity

Inspected extracted chronological frames from three public GNOME clips embedded in the **2025-04-11 STF report**: Elastic’s adaptive About dialog (7.70 seconds, 2 frames/second), Shortwave’s bottom sheet (8.26 seconds, first 6.67 seconds at 3 frames/second), and its multi-layout demo (13.79 seconds, first 12 seconds at 1 frame/second). This is recorded-state inspection, not playback latency testing.

- **Elastic:** as its host narrows, the centered About card becomes an attached bottom sheet, retains its content/close control and returns to a centered card when widened. The same task survives a geometry change.
- **Shortwave bottom sheet:** the compact current-station row expands upward into a larger control surface; dragging down reveals the list behind it and returns to the compact row. Inference for productivity apps: preserve identity between a compact running-task summary and expanded controls. Do not add a sheet merely for fashion.
- **Shortwave multi-layout:** wide navigation/content becomes a narrow list with bottom controls. The demonstration also includes a playful tiny retro-radio layout; do not infer that every app needs this extreme mode.

[Report](https://blogs.gnome.org/tbernard/2025/04/11/gnome-stf-2024/), [Elastic clip](https://blogs.gnome.org/tbernard/files/2025/03/libadwaita-adaptive-dialog.webm), [bottom-sheet clip](https://blogs.gnome.org/tbernard/files/2025/03/libadwaita-bottomsheet.webm), [multi-layout clip](https://blogs.gnome.org/tbernard/files/2025/03/libadwaita-multilayout2.webm). The report dates adaptive dialogs to libadwaita 1.5 and bottom sheets/multi-layout to 1.6. Clips support continuity/composition claims, not universal delight or smoothness on weak hardware.

Elastic itself is a useful **motion-design resource**: adjust spring parameters, inspect curves, preview transformations and export code. Its 2023 introduction explains why physical parameters need visual tooling; this is a practical developer utility, not just a decorative demo. [Introduction](https://blogs.gnome.org/alicem/2023/02/24/introducing-elastic/), [current app page](https://apps.gnome.org/Elastic/).

## Payment models and app examples

**Insync: paid solution to missing cloud integration.** Observed desktop offer: $49.99 normal price, $39.99 temporary offer per cloud account; unlimited machines; seven-day trial; one year of Care included, then optional $19.99/year support renewal. Software continues without Care. Office showed $159.99/year for one machine and a separate 15-day trial. Two providers under one email count as two cloud accounts. These distinctions must be visible before checkout; “lifetime” without the support/account boundary would mislead. The vendor claims hundreds of thousands of users, without a Linux share, paying-user count or audited profit. [Pricing](https://www.insynchq.com/pricing). Its live terms page, dated July 31, 2019, says no refunds; report this as published vendor policy, not a legal conclusion about statutory rights. [Terms](https://www.insynchq.com/terms). A 2026 support article acknowledges confusion from several renamed legacy plans. [Pricing history](https://help.insynchq.com/en/articles/6768066-pricing-then-versus-now).

**Sublime Text: personal perpetual use with bounded updates; business subscription.** Current checkout showed $99 personal purchase, three years of updates, one key across the user's computers/OSes. Business seats start at $65/year for the first ten, with lower marginal tiers. Free evaluation is offered, but continued use requires purchase. This makes update entitlement distinct from continuing use and licenses the person rather than penalizing dual-boot users. [Current checkout](https://www.sublimehq.com/store/text). The old `/sales_faq` still discusses Text 3/4 major upgrades; it does not describe today's update policy. A price page proves a business offer, not its profitability. Revenue searches returned third-party estimates with unclear methodology; none establishes Linux-derived profit. Prefer no numerical claim over directory-estimate arithmetic.

**Obsidian: free local work, paid convenience and patronage.** Sync starts at $4/user/month billed annually or $5 monthly; Publish $8/site/month annual or $10 monthly. Optional Catalyst costs $25 once; Commercial $50/user/year. Sync/Publish offer seven-day refunds; patronage licenses and credit do not. Forty-percent education/nonprofit discounts are listed. [Pricing](https://obsidian.md/pricing). On February 20, 2025, it made commercial licensing optional because the old rules were confusing; it reported use in more than 10,000 organizations. This is a documented simplification and adoption claim, not a measured conversion gain. Local Markdown, no compulsory account and paid optional services let users trust the exit path while paying for recurring value. [Change announcement](https://obsidian.md/blog/free-for-work/). No inspected owner financial disclosure isolates Linux revenue or proves whether this change increased total revenue.

**Joplin: free open-source clients, paid hosted sync and business hosting rights.** Basic showed €2.99 monthly or €28.69/year, 2 GB storage and 10 MB per note/attachment; Pro €5.99 monthly/€57.48 yearly with larger limits. Teams separates administration, consolidated billing and permissions; self-hosted Server Business uses annual per-user tiers. Fourteen-day trial. The vendor explicitly says subscriptions fund client maintenance and security fixes. That is a clear value exchange; Joplin Server Business self-hosting still has a published per-user charge. Current comparison distinguishes accepting a shared notebook from creating shares. [Plans and comparison](https://joplinapp.org/plans/). Do not turn the vendor's faster-sync claim into a benchmark. Costs, subscriber counts, churn and Linux share were not disclosed here.

**Standard Notes: paid privacy product with larger-owner support.** In November 2024 the company reported tens of thousands of paying customers, remaining a distinct business after joining Proton, and infrastructure hardening that delayed visible new features. This supports paid demand and the cost of abuse prevention; not audited profit or Linux-specific demand. [Company update](https://standardnotes.com/blog/progress-with-proton). Its December 2025 update lists actual maintenance work and says its subscription remains separate from Proton. Users should not need to guess whether an acquisition bundles their license or changes the roadmap. [2025 update](https://standardnotes.com/blog/2025-update). This is now a larger-company comparison, not evidence for an independent solo business.

**Thunderbird: a large donation-funded project with an inherited audience.** The October 2025 report says 2024 donations reached $10.3M (+19%), from more than 335,000 donors and 539,000 transactions; 25% was recurring support. Median gift $16.66; 94% of gifts $35 or less. Staff ended 2024 at 43. Personnel dominated spending, then infrastructure and administration. These are company-reported cross-platform finances; total profit and Linux share are not supplied. Twenty years of distribution and community make this a poor revenue forecast for a new utility. [2024/25 report](https://blog.thunderbird.net/2025/10/state-of-the-bird-2024-25/). The prior report describes a usage upturn after Supernova following three declining years, but design, architecture and other changes shipped together; this is correlation, not a redesign experiment. [2023/24 report](https://blog.thunderbird.net/2024/10/thunderbird-annual-report-2023-2024/).

## Measured payment evidence and its limits

The inspected pricing pages, annual reports, founder retrospectives, store reports and user accounts yielded no Linux-only controlled conversion effect or auditable top-grossing/profit ranking. Private cohorts, acquisition costs and churn were not disclosed. These sources cannot supply a universal pricing benchmark; case figures below retain their scope.

**elementary AppCenter, February 2018: low paid conversion despite downloads.** Its founder reported ~$1,700 processed from 750+ charges since May 2017; roughly $2.30 per paid transaction. Harvey/Nimbus and Sequeler each had about 1% paying downloaders; Clipped/Torrential 0.75%. Individual developer payouts cited were $155–330. Users told the team they wanted to try first and could not easily return to pay. The store proposed a permanent funding button and an update-time request while preserving critical/security updates. These are developer-reported historical aggregates and qualitative feedback, not a randomized intervention or a current Linux benchmark. No follow-up effect size was established by this pass. Practical inference: let satisfied users pay later without reinstalling; measure actual payment completion. [About AppCenter payments](https://blog.elementary.io/about-appcenter-payments/).

**Current AppCenter economics.** Suggested prices remain pay-what-you-want, including zero. The documented split is 70% developer/30% elementary with a $0.50 minimum platform share; a $1 payment leaves $0.50 and a $10 payment $7. No enrollment/subscription publishing charge. Tiny tips therefore have different economics from larger payments. These are the store's terms, not evidence every app can cover its costs. [Monetization docs](https://docs.elementary.io/develop/appcenter/monetizing-your-app).

**Insomnia founder: support and identity can motivate payment.** Gregory Schier's December 2019 retrospective says dozens of $5/month Plus subscribers told him they paid to support the product; some donations exceeded $100. He credits direct customer conversations, a narrow market and open-sourcing as advantages. This is founder testimony with selection bias, no conversion denominator, and all-platform users. Treat as an idea to test: document decisions, answer real workflow problems, make the funding purpose plain. His 500 × $30/month example is illustrative arithmetic, not Insomnia's revenue. [Retrospective](https://schier.co/blog/indie-a-competitive-advantage).

## What hurts trust, retention and sales

**Paid activation must survive ordinary outages.** A February 2024 Insync buyer reported successful trial and payment but continued “trial expired,” failed license refresh and a server error; another commenter reported no problem. One anecdote, not a defect rate. Expected behavior: explain payment propagation, retain safe access, show the affected cloud account and provide a usable support route. A licensing outage must not look like lost payment or lost data. [User report](https://www.reddit.com/r/linuxquestions/comments/1aj6gpi/anyone_else_having_problems_with_insynchq_the/).

**Do not make existing local work unexpectedly depend on cloud adoption.** Insomnia 8.0's 2023 launch emphasized account-free Scratch Pad while adding collaboration. Version 8.3 restored fully local projects and made migration default to Local Vault to avoid sending employer data to the cloud unintentionally. This is the vendor's explicit reversal, not proof of quantified lost sales. Preserve storage/account choice during upgrades and explain any conversion. [8.0](https://konghq.com/blog/product-releases/insomnia-8-0), [8.3](https://konghq.com/blog/product-releases/insomnia-8-3). Current account docs should be consulted for current behavior; historical encryption claims are not today's default. [Current accounts](https://developer.konghq.com/insomnia/accounts/).

**A polished app can lose its sponsor's strategic priority.** Nylas Mail maintenance ended in 2017 as the company focused on APIs; its issue thread directs users to Mailspring and community forks. A 2026 archive timestamp must not be confused with the actual end of maintenance. [Maintainer notice](https://github.com/nylas/nylas-mail/issues/3564). Contemporary reviewer Joey Sneddon liked its appearance/features but preferred Thunderbird; he explicitly had not used Nylas full-time. His report corroborates discontinued support, not an audited reason for business failure. [Contemporary review](https://www.omgubuntu.co.uk/2017/06/nylas-mail-is-dead-jim). Lesson: account for export, transferable data and a funded maintenance owner; open code enables a fork but does not guarantee one will thrive.

**Sync is retention work, not a checklist item.** A 2022 Joplin user considered leaving over sync conflicts and clipping failures. Replies included happy long-term users and provider/large-attachment difficulties. This particular report was Mac+iPhone, so it informs the cross-device workflow of a Linux note app, not a Linux defect claim. It shows why every supported companion affects trust in the desktop app. [Discussion](https://www.reddit.com/r/joplinapp/comments/yk7zu5/sync_and_web_clipping_are_both_driving_me_away/).

**Slow visible progress can look like abandonment.** Standard Notes' own update explains its security/infrastructure phase; its subsequent maintenance list provides evidence of work. Users cannot observe backend investment. Publish substantive maintenance notes, explain roadmap boundaries and fix daily irritants alongside infrastructure work. This is an inference from the dated updates above, not measured churn causation.

## Distribution, featuring and market measurement

**Flathub curation rewards listing execution, not only framework choice.** For optional featured eligibility: maintain a supported runtime and author verification; supply contrasting light/dark brand colors, recognizable icons, short name and outcome-based summary; use real Linux window screenshots, defaults, native decorations and a strong first image. Do not supply Mac screenshots or promotional composites. Three to six screenshots suit medium-complexity apps. These are curation criteria, not mandatory general Linux UI rules. [Current quality guidelines](https://docs.flathub.org/docs/for-app-authors/metainfo-guidelines/quality-guidelines). Passing checks permits weekly/App-of-the-Day rotation and can improve discovery; neither a guaranteed placement nor measured paid uplift. [Maintenance](https://docs.flathub.org/docs/for-app-authors/maintenance).

**Curation has biases and real maintenance costs.** In November 2024 a Flathub volunteer said over 90% of apps passing the then-current checks used GNOME technologies; he explicitly wanted more non-GNOME apps and invited objections. Developers cited upstream icon control and niche app fit. Do not interpret this historical selection as all Linux users preferring GNOME or a ban on Qt. [Discussion](https://discourse.flathub.org/t/app-developer-feedback-about-quality-guidelines/8037). A May 29, 2026 GNOME Circle committee post announced temporarily closing new submissions to clear a long backlog. An October 7 reviewer update still described reopening as future work. Do not make launch success depend on timely acceptance. The public landing page still links to Apply; that does not prove the review queue reopened. [Committee update](https://blogs.gnome.org/sophieh/2026/05/29/updates-from-the-circle-committee/), [October reviewer update](https://blogs.gnome.org/psauberz/2026/10/07/fellowship-update-2026-10-07/).

**Payment policy is not proof of payment infrastructure.** Flathub's current requirements allow monetized apps with clear upfront benefits and access for reviewers; they reject manipulative design. [Requirements](https://docs.flathub.org/docs/for-app-authors/requirements). In June 2026 a GNOME board candidate said legal-entity work still blocked native payment processing, explicitly qualifying his knowledge. This is newer than 2023/24 launch plans but not definitive November status. No inspected current author payment setup docs established a launched merchant service or fee. Plan a working external purchase/donation route; recheck actual merchant onboarding before depending on built-in checkout. [June discussion](https://discourse.gnome.org/t/debate-fiscal-hosting/35467/2).

**Current AI submission restrictions affect delivery.** The requirements read on November 8 disallow AI-generated/assisted Flathub manifests and AI submission PRs/comments; other generated app material requires disclosure and discretionary review. Treat as a distribution constraint when choosing a process, not an app design principle. The report does not submit anything. The source also requires meaningful history/use/maintenance commitment; a new app is not guaranteed instant acceptance. [Requirements](https://docs.flathub.org/docs/for-app-authors/requirements).

**Downloads are not people, retention or revenue.** Flatpak's history records Flathub's 2025 438M downloads and 3,200+ apps; these platform totals do not give unique paying users or a target niche's size. Do not divide by app count for a business forecast. [Flatpak history](https://flatpak.org/about/). Direct channels, distro packages and mirrors further complicate counting. Product-specific activation, repeated completed jobs and paid cohorts are needed; privacy-sensitive apps should disclose any measurement and allow an appropriate opt-out.

## Economics and business scope

**Budget by support promise.** Perpetual local utility: payment/refund/chargeback fees, release packaging, signing infrastructure where used, mirrors/CDN, distro/runtime migrations, security updates, support and developer time. Hosted sync: add storage, bandwidth, backup/restore, abuse prevention, outages, tenant isolation and account recovery. Business tier: add invoicing, procurement, deployment documentation, permission administration and response-time commitments. A flat binary has low marginal hosting cost; it does not have zero continuing cost. Insync, Joplin and Standard Notes illustrate different boundaries, not published cost benchmarks.

**Model cash left after costs.** Illustrative budget, not a formal accounting margin: collected revenue − payment/platform fees − refunds/tax obligations − variable hosting/support − acquisition cost; then subtract fixed development, maintenance and administration. Keep unpaid founder/volunteer time visible. Lifetime-use promises should include a funded update horizon or an honest support boundary. No numerical CAC/LTV estimate is justified by the public sample.

**Segment before selecting a model.** A GNOME-only personal utility can optimize discovery and donations inside that community; a business client may need support on an organization's selected distro and a procurement-friendly invoice; a cross-platform knowledge tool sells continuity between desktop and phone. High-connectivity subscriptions cannot be assumed suitable for offline work, restricted payment regions or low-income audiences. Joplin/Obsidian publish education discounts, but those do not establish fair prices in every locale. Test local payment availability and language with the actual intended audience.


## Observed external payment costs

Stripe’s US-dollar standard pricing read November 8 showed 2.9% + $0.30 for domestic-card transactions, +1.5% international cards and +1% when currency conversion is required. Pay-as-you-go Billing adds 0.7% of Billing volume. Original processing/conversion fees are not returned on refunds. These are one market/payment-method schedule, not universal Linux fees or all-in merchant costs. At $1, domestic-card processing alone is about $0.33 (33%); at $10, $0.59 (5.9%)—illustrative arithmetic before other costs. [Stripe pricing](https://stripe.com/pricing).

GitHub Sponsors documents zero fees for sponsorships from personal accounts and up to 6% from organization accounts; supported payout regions restrict who can receive funds. This suits open-source patronage, not a general proprietary-software checkout. [GitHub Sponsors](https://docs.github.com/en/sponsors/getting-started-with-github-sponsors/about-github-sponsors).

## Stack choices

Some linked docs move independently of the selected release: libadwaita `main` identifies 1.11.alpha, Qt `/qt-6/` resolves to 6.12, and electron-builder describes unreleased v27. Pin the selected stable release and its docs; a moving API reference does not establish a release date.


**GTK 4 + libadwaita:** strongest direct fit for GNOME-style focused tools. Use platform controls, actions, async I/O and accessibility metadata; avoid recreating them in a canvas. C, Rust, Python and GJS are language options. Rust adds binding complexity; Python needs a packaged interpreter. gtk-rs lists Authenticator and Pika Backup; PyGObject lists Apostrophe, Blanket and BleachBit: concrete adoption, not market share. libadwaita supplies GNOME patterns and uses LGPL-2.1-or-later. Its look is a product choice, not a promise to match every desktop theme. [GNOME libraries](https://developer.gnome.org/documentation/introduction/overview/libraries.html), [gtk-rs](https://gtk-rs.org/), [PyGObject](https://pygobject.gnome.org/), [libadwaita](https://gnome.pages.gitlab.gnome.org/libadwaita/doc/main/).

**Qt 6 Widgets:** good starting point for dense business tools, multiple documents, established menu/toolbars and complex tables. **Qt Quick + Kirigami:** better fit for adaptive KDE-style interfaces; QML and native code form another boundary to maintain. Frameworks are modular; adopting one need not pull in the desktop. KDE's tier system exposes dependency cost. PySide6 gives official Python bindings; PyQt6 is another mature binding with different licensing. Confirm licenses module by module: Qt Graphs is GPLv3/commercial, not an interchangeable LGPL add-on. [KDE catalog](https://api.kde.org/), [Kirigami](https://api.kde.org/kirigami-index.html), [Qt for Python](https://doc.qt.io/qtforpython-6/), [PyQt](https://www.riverbankcomputing.com/software/pyqt/), [Qt Graphs](https://doc.qt.io/qt-6/qtgraphs-index.html).

**Electron:** defensible for existing web teams, rich editors and cross-platform business workflows; VS Code is concrete adoption. Bundled Chromium reduces browser-engine variation but makes the developer responsible for shipping its security updates. The project supports the newest three stable major lines and releases majors on an eight-week cadence. Budget package size, idle memory, startup and battery measurement; these sources do not establish a universal benchmark against native apps. Use isolated renderers and narrow validated IPC; untrusted web content must not inherit Node powers. [Repository/platform policy](https://github.com/electron/electron), [release policy](https://www.electronjs.org/docs/latest/tutorial/electron-timelines), [security](https://www.electronjs.org/docs/latest/tutorial/security).

**Tauri 2:** Rust core plus web UI and system WebKitGTK. Avoid equating a small executable with a small complete Linux installation: distribution may need WebKit libraries or bundle them. GTK/WebKit version, GPU driver, media plugins and the oldest target distro become product support obligations. Its app capability system is separate from Flatpak/Snap sandbox permissions. Test web content on actual WebKitGTK, not only Chrome. [Prerequisites](https://tauri.app/start/prerequisites/), [AppImage](https://v2.tauri.app/distribute/appimage/), [security model](https://v2.tauri.app/security/).

**Wails:** Go logic plus system webview is a good candidate when Go reuse is valuable. Current owning FAQ says v3.0.0 is stable for desktop; its default Linux stack is GTK4/WebKitGTK 6.0. Installation docs identify Ubuntu 24.04+/Debian 13+ for that stack. The GTK3/WebKit2GTK 4.1 build path supports older targets through v3.0.x, with removal planned for v3.1. Do not repeat old v2 installation advice. This is a documented support contract, not this survey's test result. [FAQ](https://wails.io/faq/), [installation](https://wails.io/quick-start/installation/).

**Flutter:** coherent custom UI shared with mobile, with Linux integration via Dart FFI and plugins. Desktop focus, menus, density and accessibility require deliberate work; mobile layouts do not become good desktop layouts by resizing. Shipping only the executable fails: include `lib` and `data`, then verify linked system libraries. Canonical's Linux plugin work is adoption/investment evidence, not proof every plugin covers every distro. [Linux build guidance](https://docs.flutter.dev/platform-integration/linux/building).

**Fyne / Gio:** reasonable Go-first candidates for owned utilities. Fyne provides a retained widget set, binding, packaging and GUI test helpers; Gio uses immediate-mode UI and has a public showcase including gotraceui. Neither a small dependency count nor a screenshot establishes complete screen-reader, IME or Wayland integration for the target app: prototype these before commitment. Native GTK/Qt can be cheaper when those behaviors dominate. [Fyne](https://docs.fyne.io/started/), [Gio](https://gioui.org/).

## Compatibility: four distinct promises

Specify separately: **installs** (ABI/package dependencies), **features work** (portal/hardware/service), **UI adapts** (layout/input/accessibility), **tested reliably** (named configurations and workflows). Linux has no single minimum OS version or platform-wide store deadline. Kernel version alone is almost never a useful desktop-app support contract. Framework build minimum, runtime libraries, package runtime and desktop services can differ.

| Axis | User-visible consequence; implementation and test cost | Useful support strategy / graceful failure | Evidence |
| --- | --- | --- | --- |
| Distro ABI / glibc | A binary built against newer libc may not launch on an older supported distro. Compiler, C++ runtime and linked plugins matter too. | Build on oldest supported baseline or reproducible runtime; test clean machines, not only dev containers. A source-build option is not a tested binary promise. | [Qt Linux](https://doc.qt.io/qt-6/linux.html) |
| Framework build vs runtime | Qt's page lists supported source configurations alongside separate binary glibc requirements. The observed page even has different installer-build and minimum tables; do not infer one universal glibc floor. | Inspect actual binaries and exact framework release. Record build image, runtime and architecture in release manifest. | [Qt Linux](https://doc.qt.io/qt-6/linux.html) |
| Flatpak runtime | Shared GNOME/KDE/freedesktop runtime reduces distro-library variation; app still bundles missing libraries and must migrate EOL runtimes. | Use an existing runtime; avoid maintaining a private runtime for an ordinary indie app. Test the installed sandbox. | [Dependencies](https://docs.flatpak.org/en/latest/dependencies.html) |
| Flatpak permissions | Host files, devices, processes and buses are restricted; raw path code can fail after working unpackaged. | Prefer file/print/URI portals; request only necessary static access. Permission denial is a recoverable state with a clear action. | [Sandbox permissions](https://docs.flatpak.org/en/latest/sandbox-permissions.html) |
| Snap confinement | Strict, classic and devmode have materially different guarantees. Classic review is required; devmode is not stable-channel production distribution. | Validate required interfaces early. Classic may fit tools that truly need host access, but does not give strict confinement's isolation. | [Snap confinement](https://snapcraft.io/docs/explanation/security/snap-confinement/) |
| AppImage launch | Executable bit and FUSE can block the very first run. The format is not proof of universal host compatibility. | Document executable permission and extraction fallback; test no-FUSE and clean baseline. Avoid presenting terminal fixes as ordinary onboarding. | [Quickstart](https://docs.appimage.org/introduction/quickstart.html), [FUSE troubleshooting](https://docs.appimage.org/user-guide/troubleshooting/fuse.html) |
| deb/rpm packages | Package manager integrates dependencies and updates; separate distro/version packaging adds work. | Choose audience-relevant formats, keep app IDs/data paths consistent, test upgrades and removal. More formats need separate release checks. | [Electron updater Linux guidance](https://www.electronjs.org/docs/latest/api/auto-updater) |
| Wayland vs X11 | Capture, global shortcuts and window control cannot be assumed to behave like old X11 code. | Use portal-backed APIs where available; discover interface versions/capabilities. Preserve ordinary in-app access when a global feature is absent. | [Portal architecture](https://flatpak.github.io/xdg-desktop-portal/docs/), [GlobalShortcuts](https://flatpak.github.io/xdg-desktop-portal/docs/doc-org.freedesktop.portal.GlobalShortcuts.html) |
| Desktop/portal backend | GNOME, KDE and other desktops implement portals through different backends. API existence in docs does not prove local backend support. | Test actual sessions, not just installed packages. Handle missing service, denied request and cancelled request distinctly. | [Portal docs](https://flatpak.github.io/xdg-desktop-portal/docs/) |
| Screen capture | User chooses source; app receives PipeWire streams. Persisted selection tokens can change. | Treat capture as a session; handle cancellation, monitor removal and restart. Query available source/cursor modes. | [ScreenCast](https://flatpak.github.io/xdg-desktop-portal/docs/doc-org.freedesktop.portal.ScreenCast.html) |
| Tray availability | Some desktops show no status icon. Closing a tray-only utility can make it undiscoverable. | Tray is supplementary; provide launcher/normal-window status and controls. | [Desktop integration](https://docs.flatpak.org/en/latest/desktop-integration.html) |
| Startup/background | Autostart and permission to continue running are separate outcomes. | User-visible reason, explicit opt-in, recoverable denied state; do not infer one result from the other. | [Background portal](https://flatpak.github.io/xdg-desktop-portal/docs/doc-org.freedesktop.portal.Background.html) |
| x86-64 / arm64 | Native modules, webviews and bundled helpers all need matching builds. Compiler success does not test drivers or plugin availability. | Start with audience-backed architectures. Qt documents limited ARM reference hardware; test ARM hardware for an ARM promise. | [Qt support](https://doc.qt.io/qt-6/supported-platforms.html), [Electron repository](https://github.com/electron/electron) |
| GPU / software rendering | Custom rendering can fail differently on Intel/AMD/NVIDIA, VM or remote sessions. | Measure actual app; retain supported fallback and useful diagnostics. Avoid global permanent debug-environment workarounds without scoped verification. | [GTK runtime/debug docs](https://docs.gtk.org/gtk4/running.html), [Tauri Linux graphics guide linked from distribution docs](https://v2.tauri.app/distribute/appimage/) |
| Mixed DPI / monitor changes | Raw pixel math produces tiny targets, blurry assets or misplaced windows. | Use toolkit logical coordinates; test 100%, 125/150%, 200%, moving between displays and unplugging a monitor. Test drawing code separately. | [Qt High DPI](https://doc.qt.io/qt-6/highdpi.html) |
| Keyboard / IME / locale | Text input is not raw key events. Missing modules, composition and translated label growth expose custom-control defects. | Prefer toolkit entries; test CJK composition, dead keys, RTL, keyboard-only use and locale changes. | [GTK input-module runtime guidance](https://docs.gtk.org/gtk4/running.html), [Pango](https://docs.gtk.org/Pango/) |
| Accessibility | Standard GTK controls expose semantics; custom widgets must supply roles, properties and implementations. | Test with Orca on supported desktop; include focus order, selected states, errors and live updates. A toolkit capability is not app certification. | [GTK accessibility](https://docs.gtk.org/gtk4/section-accessibility.html) |
| Secret-service availability | Keyring may be missing/locked. Electron's `basic_text` backend does not protect stored secrets. | Detect backend and failure; avoid silent downgrade to purported secure persistence. Offer nonpersistent session when appropriate. | [safeStorage](https://www.electronjs.org/docs/latest/api/safe-storage), [libsecret](https://gnome.pages.gitlab.gnome.org/libsecret/) |
| Network/shared storage | SQLite WAL cannot operate over network filesystems. Syncing open DB files is not a collaboration protocol. | Keep live DB local; export consistent snapshots or use app-level sync. Test network disconnect and external file mutation separately. | [SQLite WAL](https://www.sqlite.org/wal.html) |
| Updating / rollback | Electron's built-in autoUpdater does not support Linux. Distribution package updates can conflict with an app's private updater. | One owner per install channel; test migration, interrupted update and old-version behavior. | [autoUpdater](https://www.electronjs.org/docs/latest/api/auto-updater) |
| Remote / enterprise / immutable desktops | Admin policy, restricted install rights, proxy and host access can change otherwise working integration. | Select managed package strategy for actual customer fleet; portable package is not automatic policy compliance. Publish support boundaries. | Inference from package/permission contracts above; not measured fleet prevalence. |
| Small screens / touch / large data | Adaptive containers help width; long lists need models and bounded work. Desktop convergence is not a requirement for every utility. | Test minimum usable window and large text; make touch/handheld support explicit. | [Kirigami](https://api.kde.org/kirigami-index.html), [libadwaita](https://gnome.pages.gitlab.gnome.org/libadwaita/doc/main/) |
| WSL GUI | WSL 2 runs X11/Wayland apps integrated with the Windows desktop; host graphics and clipboard are another boundary. | Support it only after testing Windows/WSL/GPU versions, file paths, portal-dependent features and startup. Microsoft documents Windows 10 build 19044+ or Windows 11; this is WSL eligibility, not this app's tested promise. | [WSL GUI](https://learn.microsoft.com/en-us/windows/wsl/tutorials/gui-apps) |
| ChromeOS Linux environment | Debian environment is optional; school/work policy can disable it. Shared files/permissions apply across its Linux apps. | Treat as a separate target, including architecture, microphone grants and backup/restore. Do not promise all Chromebook hardware or ordinary GNOME session services. | [ChromeOS Linux](https://support.google.com/chromebook/answer/9145439?hl=en) |
| Corporate proxies | A client may open locally yet fail authentication, sync or updates behind proxy policy. | Test explicit/system proxy selection and failures for every network subsystem; do not bypass certificate validation as a fix. Qt exposes proxy factories but documents platform limits. | [Qt proxy selection](https://doc.qt.io/qt-6/qnetworkproxyfactory.html) |
| Clipboard and drag across apps | Data formats, ownership and copy/move/link differ from internal widget operations. | Test text, files and rich content across sandbox/toolkit boundaries, cancellation and source exit. Offer normal Open/Import/Paste alternatives. | [GDK clipboard](https://docs.gtk.org/gdk4/class.Clipboard.html), [GTK DND](https://docs.gtk.org/gtk4/drag-and-drop.html) |

Representative strategies, not universal recommendations: (1) GNOME-oriented independent utility: Flatpak/GNOME runtime, GNOME and KDE smoke tests, x86-64 first if audience supports it; add ARM after testing. (2) KDE document tool: Qt/KF6 plus KDE runtime, dense keyboard workflows, check non-Plasma portals and appearance. (3) Existing cross-platform SaaS client: Electron on a maintained release line, a small documented distro/package matrix, measured idle resource budgets. (4) Managed business workstation: customer distro versions and repository deployment first; stability and support contract may outweigh broad public distribution. (5) System utility: prove permissions and Wayland capabilities before picking sandbox/package; unsandboxed distribution may be necessary for specific host operations, not as a blanket shortcut.

## Named ecosystem catalog

This is a capability catalog, not a popularity ranking or required dependency list. **Platform** means maintained as part of the documented platform; **project** means a current owning project/doc was inspected. Specific app adoption is stated only where verified. Adjacent entries are alternatives unless their roles differ. LGPL/GPL/commercial differences can change distribution obligations; review each chosen version and bundled dependency. No private usage telemetry or comparative reliability test was available.

### UI and languages

1. **GTK 4** — platform widgets and integration; GNOME-first tools. Alternative: Qt. [Libraries](https://developer.gnome.org/documentation/introduction/overview/libraries.html).
2. **libadwaita** — GNOME adaptive patterns; LGPL-2.1+. Choose for its coherent appearance. Alternative: plain GTK/custom styling. [API](https://gnome.pages.gitlab.gnome.org/libadwaita/doc/main/).
3. **gtk-rs** — Rust GTK bindings; Authenticator/Pika Backup examples. Alternative: direct C/PyGObject. [Project](https://gtk-rs.org/).
4. **PyGObject** — Python/GObject runtime bindings; Apostrophe/Blanket adoption, LGPL-2.1+. Package typelib/native dependencies too. [Project](https://pygobject.gnome.org/).
5. **GJS** — JavaScript GTK bindings listed by GTK; useful GNOME-language choice, not a browser runtime. Alternative: Python/Rust. [Bindings](https://www.gtk.org/docs/language-bindings/).
6. **Vala** — GTK-supported language route; choose for GObject-oriented code and existing expertise. Alternative: C/Rust. [Bindings](https://www.gtk.org/docs/language-bindings/).
7. **gtkmm** — C++ GTK bindings; fit existing C++ without choosing Qt. Track GTK-major compatibility. [Bindings](https://www.gtk.org/docs/language-bindings/).
8. **Qt Widgets** — mature desktop controls; fit dense tools. Alternative: Qt Quick for adaptive/custom layouts. [Modules](https://doc.qt.io/qt-6/qtmodules.html).
9. **Qt Quick** — declarative custom/adaptive UI; renderer and QML integration cost. Alternative: Widgets. [Modules](https://doc.qt.io/qt-6/qtmodules.html).
10. **Qt Quick Controls** — QML controls; prefer over drawing ordinary buttons. [Modules](https://doc.qt.io/qt-6/qtmodules.html).
11. **Kirigami** — KDE adaptive QML components; desktop/mobile scope, not mandatory mobile support. [API](https://api.kde.org/kirigami-index.html).
12. **PySide6** — official Python Qt bindings; package Qt plugins/runtime. Alternative: PyQt6. [Qt for Python](https://doc.qt.io/qtforpython-6/).
13. **PyQt6** — independent Qt bindings; Linux Intel/ARM documented. GPLv3/commercial, no LGPL option; differs from PySide. [Riverbank](https://www.riverbankcomputing.com/software/pyqt/).
14. **Electron** — Chromium/Node desktop shell, MIT; VS Code adoption. Budget rapid upgrades. Alternative: system-webview shells. [Repository](https://github.com/electron/electron).
15. **Tauri 2** — Rust/web UI; WebKitGTK runtime on Linux. Alternative: Electron for bundled engine consistency. [Prerequisites](https://tauri.app/start/prerequisites/).
16. **Wails 3** — Go/web UI; current docs specify GTK4/WebKitGTK6. Alternative: Fyne/Gio for Go-drawn UI. [FAQ](https://wails.io/faq/).
17. **Flutter/Dart** — shared rendered UI with FFI/plugins. Verify desktop-specific APIs per plugin. [Linux](https://docs.flutter.dev/platform-integration/linux/building).
18. **Fyne** — Go widget/binding/testing toolkit. Prototype accessibility/IME for app requirements. Alternative: Gio or native bindings. [Docs](https://docs.fyne.io/started/).
19. **Gio** — Go immediate-mode UI; gotraceui showcase. More owned component behavior. Alternative: retained Fyne/GTK. [Project](https://gioui.org/).
20. **Relm4** — Elm-inspired application structure over gtk4-rs; extra abstraction for Rust teams wanting it. [gtk-rs ecosystem](https://gtk-rs.org/).

### Platform data, files and jobs

21. **GLib** — main loop, portable utilities and threads; default base for GTK. Avoid second event-loop framework without need. [API](https://docs.gtk.org/glib/).
22. **GObject** — object/signals/introspection base; use through language bindings when possible. [GLib related libraries](https://docs.gtk.org/glib/).
23. **GIO** — I/O, networking and IPC; fits GTK async operations. Alternative: language stdlib where integration is unnecessary. [GLib catalog](https://docs.gtk.org/glib/).
24. **GSettings** — schema-backed GNOME settings; suitable preferences, not document storage. [gtk-rs introductory book coverage](https://gtk-rs.org/).
25. **KConfig** — persistent/cascading settings and lockdown; useful managed KDE tools. Alternative: Qt settings for simpler needs. [API](https://api.kde.org/kconfig-index.html).
26. **KIO** — Qt/KDE local and remote resource access. Dependency cost exceeds a simple local-file API. [API](https://api.kde.org/kio-index.html).
27. **KArchive** — archive reading/writing for Qt; avoid shelling out with untrusted paths. Alternative: libarchive/language library after separate evaluation. [API](https://api.kde.org/karchive-index.html).
28. **Qt Core** — base containers/events/models; platform foundation. [Modules](https://doc.qt.io/qt-6/qtmodules.html).
29. **Qt Concurrent** — higher-level threading; appropriate bounded CPU work. [Modules](https://doc.qt.io/qt-6/qtmodules.html).
30. **Qt SQL** — database drivers/integration; include needed plugins. Alternative: direct SQLite binding. [Modules](https://doc.qt.io/qt-6/qtmodules.html).
31. **SQLite** — embedded local transactional data; no server administration. Alternative: file formats for very simple data. [Use cases](https://www.sqlite.org/whentouse.html).
32. **KCalendarCore** — calendar-data handling; preferable to inventing recurrence machinery in KDE tools. [API](https://api.kde.org/kcalendarcore-index.html).
33. **KContacts** — vCard parsing/data model for contact tools. Prefer over hand-written vCard handling; direct language-specific parser may fit a non-Qt app. Current KF6 C++/QML API is documented, not measured adoption. [Owning docs](https://api.kde.org/kcontacts-index.html).
34. **KDAV** — CalDAV/CardDAV/GroupDAV with KJobs for personal-information apps. More appropriate than rebuilding protocol behavior over Qt Network; server interoperability and auth still need tests. Current KF6 module. [Owning docs](https://api.kde.org/kdav-index.html).
35. **KItemModels** — Extra Qt model/view models; use when plain Qt proxies leave real gaps in filtering/grouping. Current KF6 C++/QML module; avoid adding it for a simple list already covered by Qt. [Owning docs](https://api.kde.org/kitemmodels-index.html).
36. **KJobWidgets** — Progress UI for asynchronous KDE jobs. Fits existing KJob architecture; ordinary toolkit progress controls suffice without it. Current KF6 API; does not supply the underlying durable job system. [Owning docs](https://api.kde.org/kjobwidgets-index.html).
37. **ThreadWeaver** — Dependency-aware job queue with bounded worker threads. Fits parallel import/indexing pipelines; Qt Concurrent is simpler for isolated tasks. Current KF6 docs warn circular job dependencies never run. [Owning docs](https://api.kde.org/threadweaver-index.html).
38. **KFileMetaData** — Extract file text/metadata for document search/catalogs. Current KF6 module; plain file attributes suffice when content indexing is unnecessary. Treat extraction of untrusted files as a security/performance boundary. [Owning docs](https://api.kde.org/kfilemetadata-index.html).

### Rendering, text and rich content

39. **Pango** — internationalized text layout; use toolkit text first. LGPL-2.1+. [API](https://docs.gtk.org/Pango/).
40. **HarfBuzz** — shaping; normally indirect through toolkit. [GNOME libraries](https://developer.gnome.org/documentation/introduction/overview/libraries.html).
41. **FreeType** — font rasterization; direct use mainly specialist typography. [GNOME libraries](https://developer.gnome.org/documentation/introduction/overview/libraries.html).
42. **Fontconfig** — system font discovery/matching; useful font tools. [GNOME libraries](https://developer.gnome.org/documentation/introduction/overview/libraries.html).
43. **Cairo** — 2D drawing/surfaces; text via Pango rather than hand-positioned glyphs. [GTK architecture links](https://www.gtk.org/docs/language-bindings/).
44. **librsvg** — SVG rendering for GTK/Cairo. [GNOME libraries](https://developer.gnome.org/documentation/introduction/overview/libraries.html).
45. **GdkPixbuf** — image pixel manipulation; ordinary display often needs only GTK. [GNOME libraries](https://developer.gnome.org/documentation/introduction/overview/libraries.html).
46. **glycin** — sandboxed image decoding/metadata into textures; relevant untrusted-image apps. [GNOME libraries](https://developer.gnome.org/documentation/introduction/overview/libraries.html).
47. **GtkSourceView 5** — editor-oriented GTK text component; LGPL-2.1+; fits code/config editing. [API](https://gnome.pages.gitlab.gnome.org/gtksourceview/gtksourceview5/).
48. **KTextEditor** — full embeddable editor with highlighting/indentation/scripting; avoid rebuilding these for a KDE tool. [API](https://api.kde.org/ktexteditor-index.html).
49. **KSyntaxHighlighting** — Structured-text/code coloring without embedding a full editor. Current KF6 C++/QML API; KTextEditor fits when editing commands, indentation and scripting are needed. [Owning docs](https://api.kde.org/ksyntaxhighlighting-index.html).
50. **Sonnet** — Qt spell-check framework with core/UI/QML APIs. Fits writing and business correspondence; avoid it for machine identifiers or code. Alternative: editor component with integrated spelling. Current KF6 module. [Owning docs](https://api.kde.org/sonnet-index.html).
51. **KTextTemplate** — Django-style text templates for generated reports; LGPL-2.1+. Current KF6 integration; plain formatting suffices for fixed short text. It introduces template syntax/localization/escaping work, not a full document editor. [Owning docs](https://api.kde.org/ktexttemplate-index.html).
52. **Qt Graphs** — accelerated 2D/3D charts; GPLv3/commercial. Check integration and license, not only appearance. [API](https://doc.qt.io/qt-6/qtgraphs-index.html).
53. **KQuickCharts** — Qt Quick charting with model-backed sources and GPU rendering for live/high-volume displays. Current KF6 docs; compare Qt Graphs for required graph types. Built-in convenience controls constrain appearance/data sources. [Owning docs](https://api.kde.org/kquickcharts-index.html).
54. **KPlotting** — QWidget plot component that handles data-to-screen conversion and axes. Fits simple scientific/utility plots in Widgets. Current KF6 API; KQuickCharts/Qt Graphs fit a QML surface better. [Owning docs](https://api.kde.org/kplotting-index.html).
55. **Qt SVG** — SVG subset support; test imported assets. [Modules](https://doc.qt.io/qt-6/qtmodules.html).
56. **Qt Multimedia** — audio/video/camera APIs; backend and codec tests remain necessary. [Modules](https://doc.qt.io/qt-6/qtmodules.html).
57. **GStreamer** — GTK/Rust multimedia ecosystem; plugin availability matters. [gtk-rs ecosystem](https://gtk-rs.org/).
58. **WebKitGTK** — embedded HTML/webview; host/runtime security updates matter. [GNOME libraries](https://developer.gnome.org/documentation/introduction/overview/libraries.html).
59. **Qt Quick MultiEffect** — combined common visual effects; prefer over stacked compatibility effects. [Migration guidance](https://doc.qt.io/qt-6/qtgraphicaleffects5-index.html).
60. **Prison** — Barcode rendering/scanning with current KF6 C++/QML APIs. Fits inventory and ticket utilities. A dedicated codec may suit non-Qt code; test real scanners/cameras instead of only generated images. [Owning docs](https://api.kde.org/prison-index.html).

### Integration, networking and security

61. **xdg-desktop-portal** — desktop-mediated APIs; backend availability is separate from API definition. [Docs](https://flatpak.github.io/xdg-desktop-portal/docs/).
62. **libportal** — convenient portal bindings; LGPL-3.0 repository license. Alternative: toolkit integration/direct D-Bus. [Repository](https://github.com/flatpak/libportal).
63. **Qt D-Bus** — Maintained Qt IPC module for desktop services; LGPLv3/GPLv2/commercial options. Use toolkit/portal wrappers when sufficient. Bus-name ownership and sandbox permissions still need explicit handling. [Owning docs](https://doc.qt.io/qt-6/qtdbus-index.html).
64. **Qt Network** — Maintained TCP/IP/HTTP/cookie APIs integrated with Qt. Prefer over a second networking stack when it fits. TLS backend deployment is part of packaging; alternatives include libsoup for GNOME apps. [Owning docs](https://doc.qt.io/qt-6/qtnetwork-index.html).
65. **libsoup 3** — GNOME HTTP client/server; use async sessions. Do not expose its basic server indiscriminately to untrusted clients. [API](https://libsoup.gnome.org/libsoup-3.0/).
66. **libsecret** — Secret Service client; LGPL-2.1+, handle locked/missing service. Alternative: toolkit wrapper. [API](https://gnome.pages.gitlab.gnome.org/libsecret/).
67. **Electron safeStorage** — OS-backed local protection; Linux backend must be checked. Not portable end-to-end encryption. [API](https://www.electronjs.org/docs/latest/api/safe-storage).
68. **KWallet** — KDE secret storage through current KF6 API. Fits a KDE app; libsecret/Secret Service can fit broader integration. Handle unavailable or locked storage; it is not an app-wide encryption or sync solution. [Owning docs](https://api.kde.org/kwallet-index.html).
69. **KNotifications** — cross-platform notifications; metadata/desktop ID must match for history/settings. [API](https://api.kde.org/knotifications-index.html).
70. **KStatusNotifierItem** — Current KF6 status-icon protocol implementation. Useful supplemental control/status for KDE utilities; normal window/launcher remains necessary on desktops without icons. Prefer it over inventing a tray protocol. [Owning docs](https://api.kde.org/kstatusnotifieritem-index.html).
71. **KGlobalAccel** — Current KF6 global-shortcut registration API. Fits KDE workspace integration; portable utilities should evaluate the GlobalShortcuts portal. Neither library name proves every compositor/backend supports the requested binding. [Owning docs](https://api.kde.org/kglobalaccel-index.html).
72. **KWindowSystem** — Current KF6 C++/QML window-system access. Fits KDE integrations beyond ordinary Qt windows; use Qt APIs when enough. Test backend-specific features rather than assuming X11 capabilities transfer to Wayland. [Owning docs](https://api.kde.org/kwindowsystem-index.html).
73. **Solid** — Current KF6 hardware-query/integration abstraction. Fits device-aware utilities; direct OS APIs may be smaller for one narrow Linux feature. Hardware permissions and actual-device tests remain app work. [Owning docs](https://api.kde.org/solid-index.html).
74. **KAuth** — Current KF6 privileged-action/helper framework using polkit on Linux. Fits admin utilities; ordinary apps need no privilege layer. Keep privileged helper small and validate its requests; do not elevate the whole GUI. [Owning docs](https://api.kde.org/kauth-index.html).
75. **KI18n** — gettext-based Qt internationalization and locale data. Alternative: Qt's own translation stack for simpler cross-platform code. [API](https://api.kde.org/ki18n-index.html).
76. **Qt Network Authorization** — OAuth helpers; GPLv3/commercial, unlike many Qt modules. [Licensing](https://doc.qt.io/qt-6/licensing.html).
77. **Qt WebSockets** — persistent bidirectional transport; reconnection/state semantics remain app work. [Modules](https://doc.qt.io/qt-6/qtmodules.html).
78. **Qt Print Support** — print APIs; test real output and portal route. [Modules](https://doc.qt.io/qt-6/qtmodules.html).

### Build, packaging, diagnostics and tests

79. **Meson** — native build system with GNOME/i18n modules and distro dependency integration. Alternative: CMake. [Project](https://mesonbuild.com/).
80. **CMake** — native build orchestration; direct Qt/KDE fit. Pin policies/toolchains. [Docs](https://cmake.org/cmake/help/latest/).
81. **Ninja** — generated build executor; usually chosen through CMake/Meson. [CMake introduction](https://cmake.org/cmake/help/latest/).
82. **CTest** — CMake test runner. [CMake docs](https://cmake.org/cmake/help/latest/).
83. **CPack** — packaging alongside CMake; still test generated packages. [CMake docs](https://cmake.org/cmake/help/latest/).
84. **ECM** — KDE extra CMake modules. [KDE catalog](https://api.kde.org/).
85. **Flatpak / flatpak-builder** — runtime/sandbox distribution and manifest builds; modern desktop app fit. [Dependencies/build docs](https://docs.flatpak.org/en/latest/dependencies.html).
86. **Snap / Snapcraft** — confined package and build workflow; audience/snapd support matters. [Confinement](https://snapcraft.io/docs/explanation/security/snap-confinement/).
87. **AppImage** — portable executable format; launch/FUSE/ABI costs remain. [Quickstart](https://docs.appimage.org/introduction/quickstart.html).
88. **Electron Forge** — integrated packaging/publishing with makers/plugins. Current docs require real `node_modules`; pnpm hoisting/Yarn node-modules settings matter. [Docs](https://www.electronforge.io/).
89. **electron-builder / electron-updater** — alternative package/update pipeline; root docs currently unreleased v27, pin stable docs. Do not confuse it with Electron core autoUpdater. [Project](https://www.electron.build/).
90. **Playwright Electron support** — automation of renderer/main process; explicitly experimental. Alternative: toolkit-native tests where applicable. [API](https://playwright.dev/docs/api/class-electron).
91. **Qt Test** — unit/component tests in Qt. [Modules](https://doc.qt.io/qt-6/qtmodules.html).
92. **Qt Quick Test** — QML UI tests. [Modules](https://doc.qt.io/qt-6/qtmodules.html).
93. **GTK Inspector** — widget/style/action inspection; catches UI structure defects before screenshots alone. [Runtime docs](https://docs.gtk.org/gtk4/running.html).
94. **KCrash** — Current KF6 crash-handling integration for KDE apps. Useful where matching desktop reporting infrastructure exists; alternative is app-specific crash capture. Handle privacy and useful symbols; a report endpoint alone does not diagnose crashes. [Owning docs](https://api.kde.org/kcrash-index.html).
95. **KUserFeedback** — Current KF6 telemetry and targeted-survey framework with core/widgets/QML APIs. Fits consent-based product learning; direct optional feedback may suffice. Do not collect raw documents or imply framework adoption proves retention. [Owning docs](https://api.kde.org/kuserfeedback-index.html).
96. **Fyne test helpers** — headless widget checks; not a replacement for real Linux integration testing. [Docs](https://docs.fyne.io/started/).


### Toolchains, data formats, measurement and verification

97. **Cargo** — official Rust dependency/build/publish tool for gtk-rs or Tauri code. Lock application dependencies and use the chosen runtime's native development libraries. Meson/CMake may still coordinate native parts; Cargo does not replace Linux packaging. [Cargo book](https://doc.rust-lang.org/cargo/).
98. **GCC** — established GNU native compiler/toolchain; its owning site publishes supported release branches. Fits distro-native C/C++ builds. Alternative: Clang; select versions compatible with target runtime rather than newest host alone. [GCC](https://gcc.gnu.org/).
99. **Clang/LLVM** — production C/C++ compiler and analysis infrastructure, with GCC-compatible driver. Owning site names Chrome/Firefox adoption. Alternative: GCC; compiler choice does not remove libc/libstdc++ ABI floors. LLVM Apache-2 licensing. [Clang](https://clang.llvm.org/).
100. **pkg-config / pkgconf** — discover compiler/linker flags from native-library metadata; pkgconf is a current alternative implementation, not bug-for-bug compatible. Fits GTK/WebKit builds. Prefer stable query flags over parsing debug output; CMake package configs are another route. [pkgconf repository](https://github.com/pkgconf/pkgconf).
101. **JSON-GLib** — GObject/GIO JSON parsing/generation, LGPL-2.1+. Fits C/GObject apps; Python/Rust/Go already have language-appropriate choices. Current owning API includes GObject serialization; validate schema and data limits yourself. [API](https://gnome.pages.gitlab.gnome.org/json-glib/).
102. **Serde / serde_json** — Rust typed serialization plus JSON format adapter. Suitable gtk-rs/Tauri data exchange; alternative is explicit/manual parsing for narrow protocols. Current owning docs distinguish format from data model; derive macros do not define migration policy. [Serde](https://serde.rs/).
103. **Qt JSON classes** — platform JSON parse/edit/write support within Qt Core. Usually enough before adding a C++ JSON library. Current API includes parse errors and value classes; preserve ID/decimal semantics explicitly rather than assuming every number is harmless. [Qt JSON](https://doc.qt.io/qt-6/json.html).
104. **SQLAlchemy** — established Python SQL toolkit/optional ORM, suitable richer local business data. Core can be used without ORM; Python sqlite3 is smaller for simple storage. Current docs expose separate release/maintenance branches; pin the branch rather than copying old tutorials. [Overview](https://docs.sqlalchemy.org/en/20/intro.html).
105. **Alembic** — versioned migrations for SQLAlchemy applications. Fits nontrivial evolving local schemas; small owned migrations may be enough without SQLAlchemy. Include migration scripts in package; test old user data and failure recovery. Owning tutorial documents upgrade/downgrade environment. [Tutorial](https://alembic.sqlalchemy.org/en/latest/tutorial.html).
106. **SQLite Online Backup API** — consistent incremental snapshots of live databases; fits export and recovery. Alternative: documented VACUUM INTO when its tradeoffs fit. Prefer either over copying a changing DB file; backup tooling does not replace restore tests. [SQLite](https://www.sqlite.org/backup.html).
107. **Sysprof** — GNOME/Linux sampling profiler for whole-system interactions, main-loop stalls and allocations. Prefer measured traces over stack stereotypes. Alternative: Valgrind tools for instrumented memory diagnoses. Current app page lists maintained release; include unwind/symbol data. [Developer guide](https://developer.gnome.org/documentation/tools/sysprof.html), [app](https://apps.gnome.org/Sysprof/).
108. **Valgrind Memcheck** — established C/C++ memory-error/leak detector. Fits native parsers/helpers; heavy instrumentation is for diagnosis, not representative latency benchmarks. Alternative: compiler sanitizers after separate toolchain setup. [Suite](https://valgrind.org/info/tools.html).
109. **Valgrind Massif / Callgrind** — heap history and call-cost diagnosis. Fits growth and CPU investigations; Sysprof has less intrusive sampling. Current suite documents substantial overhead; do not report instrumented timings as user performance. [Suite](https://valgrind.org/info/tools.html).
110. **Orca** — real screen-reader verification of names, focus, tables, forms and live content. Fits every app promising accessible Linux use. Accessibility-tree inspection complements it; neither screenshots nor keyboard-only tests substitute for spoken behavior. [Manual](https://help.gnome.org/orca/).
111. **dogtail** — Python AT-SPI workflow automation. Current master documents Xorg/GNOME Wayland, ponytail support and hermetic Mutter sessions; also notes incomplete 2.x docs and limited Qt support. Prefer toolkit-native tests for unsupported environments. Pin version and validate coordinates; this is no claim of universal Wayland automation. [Owning README](https://gitlab.com/dogtail/dogtail/-/raw/master/README.md).
112. **GtkIconTheme** — platform named-icon lookup and theme/scale fallback. Usually enough for GTK UI icons; raw file paths suit deliberately fixed illustrations. Current GTK4 API; install app icons into theme structure rather than hiding them only inside app resources. [API](https://docs.gtk.org/gtk4/class.IconTheme.html).
113. **KIconThemes** — KF6 icon chooser/effects/loading integration; fits customizable KDE tools. QIcon theme lookup alone may suffice. Use public APIs; owning docs warn internal classes are not for apps and explain standalone resource deployment. [API](https://api.kde.org/kiconthemes-index.html).

Catalog limits: current platform/module docs establish purpose and supported integration, not measured adoption or a full dependency audit. “Current KF6” means documented in the current owning API reference; it does not guarantee a fix SLA. Alternatives and fit judgments are research inferences. Do not call all entries widely used. License distinctions are flagged where consequential; inspect exact bundled licenses when selecting a release.

## Named avoid / migrate / qualify list

| Choice | Verified status or problem | Recommendation and exception |
| --- | --- | --- |
| Spectron | Owning repository labels deprecated; historical compatibility map stops at Electron 19. [Repo](https://github.com/electron-userland/spectron) | Avoid new tests; migrate to maintained automation such as Playwright's experimental Electron interface, with validation. Old frozen regression suite can remain while porting. |
| atom/node-keytar | Repository archived 2022-12-15. [Repo](https://github.com/atom/node-keytar) | Avoid new dependency on original package. Evaluate safeStorage or maintained Secret Service binding; migration must preserve decryptability/access to existing secrets. |
| andlabs/ui | Owning README explicitly says mid-alpha, incomplete and buggy on some platforms. [Repo](https://github.com/andlabs/ui) | Unsuitable default for polished broad desktop support without owning gaps. Small prototypes remain legitimate; no claim of formal abandonment. |
| therecipe/qt | Owning README's default installation uses `GO111MODULE=off` and historical tooling. [Repo](https://github.com/therecipe/qt) | High integration-risk candidate for new modern Go/Qt work; prove exact modern Go/Qt/build matrix first. This evidence does not establish archival or universal unusability. |
| Qt Charts | Deprecated since Qt 6.10; upstream recommends Qt Graphs. [Docs](https://doc.qt.io/qt-6/qtcharts-index.html) | Avoid new dependency if Graphs fits; existing Widgets app migration may be substantial. Both license and renderer differences matter. |
| Qt5Compat.GraphicalEffects | Compatibility module; stacking effects has performance constraints. [Docs](https://doc.qt.io/qt-6/qtgraphicaleffects5-index.html) | New work: MultiEffect or Effect Maker. Keep compatibility while migrating known Qt5 visuals. |
| GTK3 API for a new GNOME app | GTK4 breaks API/ABI; GTK3.24 is final GTK3 stable series. [Migration](https://docs.gtk.org/gtk4/migrating-3to4.html) | Prefer GTK4/libadwaita when target runtime permits. Maintaining a working GTK3 app is not itself a defect; account for custom-drawing/input port cost. |
| AdwLeaflet / AdwFlap | Deprecated since libadwaita1.4 in current API docs. [API](https://gnome.pages.gitlab.gnome.org/libadwaita/doc/main/) | Prefer navigation/split-view/breakpoint patterns for new code. Older runtime targets may justify legacy widgets. |
| AdwPreferencesWindow / AdwMessageDialog | Deprecated since1.6; adaptive dialog replacements exist. [API](https://gnome.pages.gitlab.gnome.org/libadwaita/doc/main/) | New compatible target: PreferencesDialog/AlertDialog. Do not adopt newer APIs without raising runtime minimum deliberately. |
| PyQt4 | Riverbank says no longer supported/no new releases. [Project](https://www.riverbankcomputing.com/software/pyqt/) | Avoid new work; migrate maintained apps to supported binding/toolkit after behavior tests. |
| Old Electron outside supported lines | Only newest three major stable lines supported. [Policy](https://www.electronjs.org/docs/latest/tutorial/electron-timelines) | Budget routine upgrades; no “set and forget” browser shell. Internal/offline deployment does not erase dependency risk. |
| Electron core autoUpdater for Linux | API has no built-in Linux support. [Docs](https://www.electronjs.org/docs/latest/api/auto-updater) | Use install-channel updater or separately evaluated updater. Not a reason to reject Electron itself. |
| Electron safeStorage `basic_text` | Hardcoded-password fallback gives no meaningful secret protection. [Docs](https://www.electronjs.org/docs/latest/api/safe-storage) | Detect and refuse silent secure-storage claim. Store no persistent secret or require suitable backend. |
| libsoup basic HTTP server exposed to hostile internet | Owning API recommends internal/mock/private IPC usage and warns about untrusted clients. [API](https://libsoup.gnome.org/libsoup-3.0/) | Suitable embedded test server; choose hardened server architecture for public exposure. |
| Wails GTK3 legacy path as long-term support plan | Owning installation docs say support only through v3.0.x, removal in v3.1. [Docs](https://wails.io/quick-start/installation/) | Plan GTK4/WebKitGTK6 minimum or separate maintained compatibility branch. Do not market old distro support as indefinite. |
| Broad Flatpak host/bus access “to make it work” | Defeats much of sandbox value and may break policy review. [Permissions](https://docs.flatpak.org/en/latest/sandbox-permissions.html), [Flathub requirements](https://docs.flathub.org/docs/for-app-authors/requirements) | Request exact necessary access; system utilities can justify broader scope with clear behavior. |
| New private Flatpak runtime | Upstream warns runtime maintenance is substantial and generally unnecessary for app authors. [Dependencies](https://docs.flatpak.org/en/latest/dependencies.html) | Use GNOME/KDE/freedesktop runtime; custom runtime only with concrete unsupported dependencies and maintenance capacity. |
| Toolkit debug env vars as permanent app configuration | GTK says these are not stable API and intended for debugging. [Runtime docs](https://docs.gtk.org/gtk4/running.html) | Scope temporary workaround and pursue supported API; do not prescribe global `GTK_PATH` or renderer hacks. |

## Build-first verification guidance

Before polishing: install the packaged app on a clean supported desktop; open/save through the real chooser; test denied permission, offline launch, keyring unavailable, keyboard/IME, Orca, mixed DPI, restart and update. For a capture/hotkey/tray utility, prove those capabilities on both intended GNOME and KDE sessions before stack selection. For a business document app, first prove import/export fidelity, crash recovery, migration and large-data responsiveness. This order is inference from the contracts above, not a measured conversion experiment.

No live app benchmarks, GPU/IME/device-lab tests, dependency CVE audit or licensed legal analysis was performed. No such outcomes are implied here.

## Runtime/release maintenance addendum

Flatpak runtime selection changes the recurring maintenance budget: the runtime overview states a two-year support period for freedesktop branches and usually one year for GNOME branches. A runtime SDK is the build environment; the matching platform is the user runtime. Neither removes host portal or driver variability. [Available runtimes](https://docs.flatpak.org/en/latest/available-runtimes.html).

Flathub expects maintainers to test PR builds before merging, update runtimes, respond to issues and mark nonfunctional/ceased apps EOL. The policy explicitly separates expectations from strict requirements and notes volunteer capacity. Store publication therefore does not outsource app maintenance. [Maintenance](https://docs.flathub.org/docs/for-app-authors/maintenance).

## Build order and decisions to test

These are research recommendations, not new scaffold defaults.

1. **Pick a job and support promise.** Name the desktop sessions, packaging channel, architecture, minimum runtime and core integrations. For an enterprise client, start with the customer's fleet. For a public utility, choose a small viable matrix and explain what is untested. Do not start by promising every distro.
2. **Prove the risky vertical slice.** Capture utility: choose a screen, capture, save, reopen after denial/restart. Notes: import real data, edit offline, sync a conflict, restore a revision. Business documents: import, calculate, print/export and reopen in the recipient's tool. Test the packaged artifact on the actual target desktop before polishing.
3. **Make persistence boring.** Test full disk, crashes, unavailable destinations, concurrent editing, upgrades and export. Give the user clear local/remote/recovery states. Data failure can negate every visual improvement.
4. **Choose one coherent visual language.** Use the matching toolkit's controls, spacing, text and action conventions as the starting point. Adapt density to the task; prototype realistic data, large text and narrow windows together.
5. **Complete everyday integration.** Launcher and file association, keyboard/IME, accessibility, window focus, file/print portals, secrets and update ownership. Add only the host permissions the job requires.
6. **Make support affordable.** Redacted diagnostics, named support versions, reproducible release artifacts, migration tests and a documented retirement path. Measure idle and active resource use on the weakest promised hardware.
7. **Earn discovery.** Accurate screenshots, short task-based description, clear publisher identity, working install path and dated maintenance notes. Curation is one channel; demonstrations to actual niche users and useful documentation are others.
8. **Test the commercial offer.** Observe first-task completion, return use, trial-to-payment, refunds, support minutes and paid retention separately. Test price/trial/pay-later messaging with the target audience. Historical payment rates and cross-platform finances do not predict a new app's optimum.

Useful differentiators: trustworthy restoration, excellent import/export, a good keyboard workflow, unusually clear background state, fast handling of a realistic large collection, and integration with the user's existing services. Each serves an observed failure or successful app pattern above.

Costly traps: supporting five package formats before one works well; custom controls that silently omit IME/accessibility; browser-engine upgrades with no maintenance budget; generic “works on Linux” claims for Wayland-sensitive features; cloud/account changes imposed on existing local data; and selling indefinite maintenance without a funding model.

A practical pilot should include both a novice to the app and a domain expert. Have them complete a real task, recover from one failure, find an uncommon command and move their data out. Keep the results separate from this literature review: none of those user tests was performed here.

## Sources and reading method

Sources were read on 8 November 2026 unless a historical date is stated. Links beside claims are the source record; citations distinguish documented behavior, developer claims, reviewer judgments, individual reports and research recommendations. Repeated reporting of one announcement was not treated as independent confirmation.

| Source family | Best use in this report | Limits |
|---|---|---|
| [GNOME HIG](https://developer.gnome.org/hig/), [KDE HIG](https://develop.kde.org/hig/) | Screen/control conventions and desktop-specific tradeoffs | Vendor/community recommendations; not measured preference for every Linux user |
| [XDG portals](https://flatpak.github.io/xdg-desktop-portal/docs/), toolkit APIs and tagged releases | Mechanisms, version boundaries, permissions and migration status | API existence does not prove a given compositor/backend works |
| App manuals, source and published screens | Workflows, supported scope, visual composition | Screenshots show appearance; releases show shipped intent; neither measures long-term reliability |
| Dedoimedo, OMG! Ubuntu, Tom's Hardware, Baty and user discussions | Concrete friction, expert habits and recovery experiences | Selected experiences; preserve versions and contradictory experiences |
| Raymond chapter excerpt, Linux Unplugged transcript, GNOME recorded demos | Historical reasoning, workflow critique and visible transitions | Excerpt/transcript/frame inspection, not entire-book review or live performance testing |
| Pricing pages, elementary payment report, Thunderbird reports and founder accounts | Actual offers, historical payments and maintenance economics | Mostly self-reported; private Linux cohorts, profitability and causality are not disclosed |
| Flathub, elementary and payment-provider documentation | Distribution, curation, maintenance and observed fees | Time-sensitive; eligibility and documented plans do not prove merchant onboarding or editorial acceptance |

The report includes 104 paired UI details, four inspected visual directions, 18 main app profiles, 26 compatibility axes, 113 named ecosystem entries and 18 avoid/migrate/qualify cases. Additional commercial cases and historical failures broaden those profiles. Published screenshots and sampled recorded motion were inspected; no installed-app benchmark, user study, device-lab test, dependency security audit or private financial audit was performed. Public-evidence limits remain beside the affected claims. This is a research reference for choosing and testing a product, not certification of any listed app or package.
