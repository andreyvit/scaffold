# Great B2B SaaS web apps

Research date: 2026-11-07. Browser-based business software for independent developers and small teams; larger products are labelled references. No single industry, locale, price tier or frontend stack is assumed. This report supplies research and proposals, not new scaffold decisions.

The strongest pattern is **less effort to finish consequential work**: a recognizable queue, dependable edits, understandable permissions and billing, and a way to recover when something fails. Visual restraint helps only while controls remain obvious. Revenue needs separate evidence: distribution, pricing fit, operating costs and retention cannot be inferred from polish.

Read by task: [app comparisons](#standout-apps-and-what-to-learn-from-them) · [100 UI details](#100-screencomponent-details) · [visual directions](#visual-design-directions-and-resources) · [compatibility](#compatibility-and-platform-citizenship) · [conversion](#conversion-retention-and-distribution) · [economics](#small-company-economics-and-product-choices) · [stacks](#stack-choices) · [115 tools](#named-ecosystem-catalog) · [avoid/migrate](#verified-avoid--migrate--context-list) · [build priorities](#what-to-build-first).

## Scope and meanings of great

Business software carries shared records across people, roles, sessions and integrations. The buyer, administrator and daily operator may be different people. Work can wait for another department, continue in email or spreadsheets, and resume weeks later. A fast signup is useful, but the unit of value may be a correctly completed team workflow. These distinctions are a working synthesis of the cases below, not claims that every SaaS requires enterprise features.

| Meaning of great | Useful evidence | Misleading substitute |
| --- | --- | --- |
| User love | Detailed repeat-use accounts; unsolicited advocacy; relief from a recurring frustration | A sleek launch page or one angry/praising comment |
| Solves the problem | Task completion, accuracy, time saved, successful handoffs | Feature count, time spent in the app |
| Builds an audience | Activated and retained accounts, repeat use at the job's natural cadence | Cumulative registrations or launch votes |
| Earns cash | Collected revenue after refunds and payment failures | ARR presented as cash or profit |
| Sustains the company | Owner wages, margin, reserves, support capacity, renewals | Unpaid founder work hidden behind low hosting bills |
| Stays maintainable | Safe changes, reproducible recovery, modest integration load | Framework fashion or small line count alone |
| Gets featured | A platform's actual review/distribution criteria | Assuming editorial attention predicts retention |

For workflow measurement, GOV.UK defines completion against genuine starts and matches saved work to later completion. That method transfers usefully to long B2B workflows; its government-specific requirement to funnel users through one start page does not. Define success at the actual business boundary, include assisted completion and separate it from purchase conversion. [Measurement guidance](https://www.gov.uk/service-manual/measuring-success/measuring-completion-rate)

**Evidence standard.** Product docs establish intended behavior; screenshots establish visible appearance; founder accounts establish what founders report. Reviews and complaints supply hypotheses and concrete failure examples, not representative sentiment. Experiments, observational cohorts and commercial disclosures remain labelled. Public evidence cannot produce an audited “top-grossing indie SaaS” ranking: the inspected founder reports use different dates and accounting units, while third-party estimates conflict. The comparison below therefore identifies strong examples by job and evidence, not a universal winner.

## Standout apps and what to learn from them

Read each row with the detailed cases and reviews below. “Great” describes the supported dimension, not a blanket endorsement of every feature, plan or current release.

| App / scope | Strongest lesson | Cost, weakness or boundary | Supported meaning |
| --- | --- | --- | --- |
| Plausible / small-team analytics | Focused questions and readable reporting | Pricing and Cloud/CE differences can drive switching | Problem solving, user affection, disclosed historical business success |
| Fathom / small-team analytics | Understandable data and explicit sustainable spending | Price/workload fit differs; API needs may outgrow the service | Individual user love; founder-defined viability |
| Tally / small-team forms | Familiar authoring plus public-form distribution | Free users still cost money; embeds, payments and trust need care | Audience growth and founder-reported revenue |
| Buttondown / business newsletters, creator crossover | Narrow product with human support and owned engineering | Paid expert features and finite support hours | Maintainability and claimed profitability |
| Balsamiq / professional wireframing | Focused artifact and teach-by-example onboarding | Historical selection/prototyping limits; revenue decline | Rational value and long-lived business |
| Transistor / podcast businesses and teams | Multi-show value supported by a coherent cost model | Media costs and pre-existing founder audience affect comparisons | Claimed sustainability; documented distribution preparation |
| Basecamp / mature collaboration reference | Organize communication around projects | First-use complexity and historical file-editing friction | Coherent workflow and distinctive visual character |
| Linear / funded, larger reference | Consistent expert work surface and opinionated workflow | Rich sync and permissions require substantial engineering | Craft/process and technical reference; no indie-profit claim |
| Buffer / larger financial reference | Distinguishes recurring revenue, cash, usage and income | Staffing and margins are not a bootstrap template | Concrete dated commercial disclosure |

## Good and poor daily UX

- **Daily work beats screenshot simplicity.** NN/g's workplace-table analysis distinguishes finding, comparing, editing and acting. Cards make cross-record comparison harder because values move between locations. Use the task to choose representation; a spacious card layout is not automatically better. [NN/g tables][tables]
- **An empty screen can lie.** NN/g documents employee software briefly claiming there were no records while loading. Users may leave before the records appear. Distinguish loading, zero matches, no content, inaccessible content and failed retrieval. [Empty states][empty]
- **Polish needs maintenance.** Linear acknowledges layout drift after earlier redesigns. Its refresh is vendor rationale, not measured delight. A mixed LinkedIn discussion includes concern about reduced borders; use it as a contrast-test prompt, not consensus. [Linear refresh][refresh]; [discussion](https://www.linkedin.com/posts/linearapp_linear-interface-refresh-a-visual-update-activity-7437912086438932483-9A5Z)

- **Billing is collaboration UX.** Notion's documentation explicitly warns that adding a member incurs charges, while a guest invitation has different access and cost. Its instructions even ask people to inspect the invitation identity and skip the upgrade prompt. A long-term user reports unexpected seats, a difficult support dispute and temporary inability to reach business data; the update says access and refunds were restored, but trust was not. Other commenters dispute whether cancellation was completed. Do not repeat their alleged one-year lockout as product policy. The supported lesson is to preview cost and access before invitation, expose billing state, and make export findable. [Billing][notionbill]; [first-person thread][complaint]
- **Permission complexity is real work.** A contractor-oriented Notion user reports that viewing restrictions did not support guest creation and attribution as expected. Current docs describe broadest-grant precedence and inherited permissions, with exceptions when moving pages private. The complaint is dated behavior, not proof that every limitation persists. Test read, create, modify, share and export separately for each role. [Complaint][permissioncomplaint]; [current permissions][permissions]
- **Product opinions differ from evidence.** Karri Saarinen's 2023 Lenny interview describes craft, focus and an opinionated workflow, rather than metric-driven goals or routine A/B tests. Read an accessible third-party transcript (with transcription errors), anchored to the original episode date. This is the founder's process account, not proof that experimentation hurts products. [Episode](https://www.lennysnewsletter.com/p/inside-linear-building-with-taste); [transcript][podcast]
- **Scope discipline does not excuse broken essentials.** Ryan Singer's accessible *Shape Up*, chapter 14, argues for comparing improvements with the existing baseline and questioning edge-case scope against audience and impact. Apply this to optional sophistication; do not use it to excuse data loss or inaccessible core tasks. This is an interpretation of the book's product method, not a controlled study. [Chapter][shape]

## Detailed independent reviews

These are individual judgments, not sentiment measurements. Historical reviews establish reasons people praised or disliked an interface; they do not establish current pricing or feature availability. TechRadar discloses affiliate commissions. The two personal essays sell their authors’ professional services/content; no product affiliate disclosure was observed. These reviews provide no controlled comparative task study.

- **Balsamiq — Christian Cawley, TechRadar, July 9, 2024.** The reviewer tested browser and Windows versions. Praises quick drag-and-drop mockups, reusable components and the narrow wireframing purpose. First-project guidance appears as editable wireframes inside the real editor; users can learn while modifying an actual artifact. Reports awkward multiple-element selection and distracting icons. Limited interactive prototyping is a scope boundary, while selection friction affects the core job. The review lists missing generative AI as a drawback; treat this as the reviewer’s preference, not a general product requirement. **Derived lesson:** teach through working examples, preserve a blank-start route, and fix frequent selection operations before expanding scope. Historical desktop/platform/pricing details omitted. [Full review](https://www.techradar.com/pro/balsamiq-review).

- **Basecamp — Collin Probst/Jacob Parker, TechRadar, February 21, 2022.** Praises project-centered discussions, schedules, assignments and files, plus company-wide HQ and scheduled notification pauses. Finds the first encounter potentially overwhelming and file editing inconvenient because files must be downloaded then uploaded again. This makes the tradeoff concrete: consolidating communication can reduce tool switching while leaving a particular collaborative editing job awkward. **Derived lesson:** assess the whole repeated task, including movement through external tools; an all-in-one feature list does not prove that work stays fluid. This review’s old plans and feature limits are not current evidence. [Full review](https://www.techradar.com/reviews/basecamp).

- **Plausible versus GA4 — Matt Olpinski, December 10, 2023.** A professional designer describes switching his own sites after a confusing analytics migration. He praises a single dashboard, retained date preset, quick goal setup and easy switching among five sites. He criticizes GA4’s persistent setup warnings, jargon, fragmented reports and truncated page titles. His task was basic freelance-site analytics, not enterprise attribution. His claimed traffic decline does not demonstrate measurement accuracy: configuration and migration effects were uncontrolled, and he acknowledges uncertainty about setup. **Derived lesson:** completion indicators must distinguish optional work from blocking setup; preserve routine context and show the full identity of records. Do not turn his anger into a market-wide verdict. [Full essay](https://mattolpinski.com/articles/why-i-switched-from-google-analytics-to-plausible-analytics/). Article body read through direct HTML retrieval after browser text fetch timed out.

- **Plausible self-hosting — Kevin Renskers, February 17, 2026.** After using hosted Plausible since July 2020, he migrated to Community Edition when traffic outgrew his plan. He reports daily unique visitors changing from roughly 200 to sometimes over 5,000 and attributes this to bots. He also dislikes a non-removable unavailable-funnel panel. This is a useful long-term switching account, but one uncontrolled deployment cannot measure product-wide accuracy. **Derived lesson:** an edition change can alter the meaning of a familiar metric; disclose semantic differences before export, account deletion or migration. Explain unavailable features without occupying permanent working space when they have no role in the selected edition. [Full essay](https://www.loopwerk.io/articles/2026/plausible/).

[Plausible’s current edition comparison](https://plausible.io/self-hosted-web-analytics) independently confirms the technical distinction: Cloud has data-center and behavioral filtering; CE has basic user-agent/referrer filtering. It also identifies Cloud-only premium features and assigns hosting, upgrades, backups and security to self-hosters. This validates the edition difference, not the reviewer’s traffic explanation or a guarantee of perfect Cloud accuracy. Vendor rationale: managed subscriptions fund the project; reviewers can still disagree with where the boundary falls.

### Fathom versus Plausible: an actual price-driven switch (2023-06-03)

[Harry's account](https://harrk.dev/why-i-switched-from-plausible-to-fathom-analytics/). After roughly a year using Plausible, author still preferred its interface but switched when higher-traffic, low-revenue sites made pricing unattractive. Praised Fathom's combined multi-site dashboard; lost continuity because no direct Plausible-to-Fathom import was available then. Affiliate credit links create a commercial incentive; prices and import limitations are historical, not current verified facts. This is useful precisely because affection did not prevent churn. Agency/blog economics differ from high-value enterprise analytics: a pageview is not revenue, and traffic-based billing can punish sites with weak monetization. Do not repeat his simplified privacy/legal claims as fact.

### Long-term Fathom enjoyment (2023-07-01)

[Mark Bowley's account](https://markbowley.me/why-fathom-analytics/). Says he had used Fathom since 2021 after Google Analytics complexity caused him to stop looking at insights. Small, understandable analytics restored interest in using the data. Individual, enthusiastic user testimony; not a usability study or evidence that analysts need fewer tools. For small-business owners who only need sources/top content/trends, lower interpretation effort can be emotional and rational value together. Article contains referral promotion; disclose rather than classify as fully independent commercial evidence. Exclude its blanket claims about cookies/law from technical guidance.

### Fathom API replaced, subscription retained (2026-01-11)

[Scott Spence's engineering account](https://scottspence.com/posts/migrating-off-fathom-analytics). Despite its title, author explicitly retained Fathom tracking while replacing API-powered public page statistics with local SQLite queries. This is **partial dependency replacement**, not complete product churn. Local/server and client counts differed greatly, including bots; author attributes some gap to blockers but does not isolate causation. Good lesson: distinguish metric definitions and collection paths before treating higher counts as greater accuracy. Custom operational requirements may justify owned components even when the SaaS remains valuable. This personal-site experiment is not proof ordinary businesses should self-host analytics.

### Tally embed regression: long-term-user complaint (2026, exact publication day not stable in extraction)

[User report and reply](https://www.reddit.com/r/TallyForms/comments/1vztsgp/changes_to_embed_and_date_field/). User says nearly a year of successful use preceded date-picker clipping inside an embedded reopened form; initial support advice suggested form/fixed-iframe changes. A reply says support escalated investigation. No verified fix or reproduction in this research. One report is not a defect-rate estimate. Design/test consequence: compatibility includes host iframe height, overflow and popup positioning, plus forms reopened after months—not only the standalone editor. Preserve a support reproduction path before shifting responsibility to customer configuration.

## 100 screen/component details

Each item pairs a useful behavior with a failure to avoid. Applicability and exceptions are part of the rule. W3C APG is implementation guidance; GOV.UK is a service-design recommendation, not a universal SaaS visual system. Product examples establish feasibility and shipped intent, not prevalence.

### Entry, onboarding and navigation

1. **Explain the first useful action.** An empty workspace should offer the next real task, such as importing records. Avoid a blank dashboard or unrelated feature tour; existing populated accounts need a different landing state. [Empty states][empty]

2. **Separate sample data.** Offer a clearly marked demonstration when users cannot yet supply data. Never mingle examples with operational records; an import-ready buyer may prefer to skip the demo. [Empty states][empty]

3. **Show setup dependencies.** Group long setup into meaningful tasks with status. Avoid a rigid wizard when finance, IT and operators can complete independent work in parallel. Sequence genuine prerequisites only. [Multiple tasks][tasks]

4. **Allow unfinished setup.** Distinguish in-progress from complete, and let users return. Visiting a screen does not prove its configuration is ready; some answers require another colleague. [Multiple tasks][tasks]

5. **Keep browser Back useful.** Restore the prior work context instead of restarting the workflow. An explicit parent link may navigate up; do not label that different action Back. [Control and freedom][freedom]

6. **Give overlays deliberate history behavior.** A full-screen record overlay often feels like navigation. Avoid Back unexpectedly leaving the underlying list; small transient menus need not create history entries. [Mental models][mental]

7. **Keep navigation landmarks consistent.** Put comparable header actions in comparable places across lists, projects and documents. Feature additions should not relocate familiar actions arbitrarily. [Linear refresh][refresh]

8. **Separate location from view controls.** Preserve a stable place for navigation while filters and display options describe the current dataset. Avoid several competing toolbars; sparse products may need only one. [Linear refresh][refresh]

9. **Make shortcuts discoverable.** Provide clickable search and commands alongside shortcuts. Linear documents different shortcuts for global and current-view search; copying hidden commands alone would disadvantage occasional users. [Search][search]

10. **Preserve context on return.** Keep a user's filters and place when returning from detail. Avoid making them reconstruct a search after every inspection; explicitly reset when the dataset or tenant changes. [Control and freedom][freedom]

### Tables, lists and comparison

11. **Choose tables for comparison.** Align the same attributes across records. Avoid decorative cards when operators compare many values; cards suit individually understood objects with little cross-record comparison. [NN/g tables][tables]

12. **Lead with a recognizable record name.** Keep important related fields adjacent. Avoid forcing users to decipher generated IDs first; IDs may lead when experts genuinely work by ticket or asset number. [NN/g tables][tables]

13. **Keep identity visible while scrolling.** Freeze headers and key identity columns where needed. Avoid losing the row's meaning; sticky regions must not consume the entire narrow viewport. [NN/g tables][tables]

14. **Align by data type.** Give numeric comparisons stable alignment and consistent precision. Avoid centered quantities or inconsistent units; codes and identifiers are text, even when composed of digits. [Table patterns][pencil]

15. **Use restrained row separation.** Choose rules, stripes or hover emphasis to support tracking. Avoid a heavy border around every cell by default; dense spreadsheet editing may justify stronger structure. [Balsamiq tables][balsamiq]

16. **Make sort state explicit.** Mark the active column and direction. Avoid decorative arrows with no clear state; nonsortable columns should not pretend to be interactive. [Balsamiq tables][balsamiq]

17. **Retain meaningful status text.** Pair status colors with labels. Avoid a table of unexplained colored dots; redundant labels can be abbreviated only where the meaning stays clear. [Table patterns][pencil]

18. **Support realistic long content.** Permit wrapping, expansion or resizing rather than permanent truncation. Avoid judging tables with short English placeholders; technical labels and translations need room. [Complex tables][complex]

19. **Keep editable cells recognizable.** Distinguish computed values from inputs. Avoid making identical-looking cells respond differently without a cue; a read-only table needs no editing chrome. [Complex tables][complex]

20. **Make density a task choice.** Dense scanning and touch manipulation need different spacing. Avoid treating a compact desktop analyst grid as the mobile UI; preserve legibility and targets. [Table patterns][pencil]

21. **Offer column control when roles differ.** Hide, reorder or resize relevant fields without destroying sensible defaults. Avoid customization as a substitute for understanding common tasks. [Table patterns][pencil]

22. **Choose table versus grid semantics deliberately.** Native tables suit reading; interactive grids need managed keyboard focus. Avoid assigning `role=grid` merely for styling. [APG grid][grid]

23. **Provide coherent cell navigation.** In a true grid, arrow keys move cells and editing has a distinct mode. Avoid hundreds of Tab stops or arrows that unexpectedly edit data. [APG grid][grid]

24. **Keep comparison possible on mobile.** Offer selected columns or a focused record view. Avoid blindly converting every row to a tall card when the task requires comparing values. [Enterprise resource review][walter]

### Search, filters and saved views

25. **Name search scope.** Distinguish workspace search from finding in the current list. Avoid identical unlabeled search boxes; Linear explicitly documents different result domains. [Search][search]

26. **Show why results match.** Highlight relevant title text or expose matching context. Avoid a result list that appears unrelated because matches occurred in hidden descriptions or comments. [Search][search]

27. **Support identifiers without ceremony.** Accept a recognizable ticket ID and common shorthand when unambiguous. Avoid requiring users to reproduce punctuation exactly; preserve strictness for ambiguous business identifiers. [Search][search]

28. **Reveal active filtering.** Show applied filters and an obvious reset. Avoid letting a returning user mistake a subset for all data; persistent views should carry clear names. [NN/g tables][tables]

29. **Expose filter logic.** Make operators and combinations readable. Avoid unexplained query syntax; expert domains may justify SQL-like conventions, with examples. [Complex tables][complex]

30. **Save useful queries.** Let repeated operational filters become named views. Avoid requiring users to rebuild the same daily queue; trivial one-off searches need no saved object. [Custom views][views]

31. **Distinguish personal and shared views.** Show who can find and change a view. Avoid silently changing a team's queue when a user meant to customize their own. [Custom views][views]

32. **Duplicate before diverging.** Offer a copy of a useful shared view as a starting point. Avoid forcing unrelated teams to fight over one configuration. [Custom views][views]

33. **Treat zero matches as a result.** State the scope and offer a relevant change. Avoid claiming there are no records while a query is still running or has failed. [Empty states][empty]

34. **Design search degradation.** Show failure with retry and another route to known records. Avoid an empty success state during an indexing outage; Linear's May 2025 incident confirms search can fail independently. [Search incident][searchincident]

### Selection and bulk operations

35. **State selection scope.** Distinguish this page from all matching records. Avoid an ambiguous Select all before expensive or destructive operations. [Bulk actions][bulk]

36. **Keep selection visible.** Show the selected count and a stable action bar. Avoid a control that disappears as users scroll through selected items. [Bulk actions][bulk]

37. **Explain eligibility.** Tell users which selected records cannot receive an action. Avoid silently skipping them; selecting only compatible items can be appropriate for strict operations. [Bulk actions][bulk]

38. **Report partial completion.** Show succeeded and failed counts with actionable failures. Avoid one generic success toast for a mixed result. [Bulk actions][bulk]

39. **Use undo for recoverable work.** Offer a clear reversal after low-risk batch edits. Avoid confirmation fatigue; irreversible actions still need specific warnings before execution. [Control and freedom][freedom]

40. **Name the destructive target.** A confirmation should state records and consequences, not only “Are you sure?”. Avoid turning reversible routine edits into compulsory dialogs. [Modal guidance][modal]

41. **Keep bulk jobs observable.** Let a user leave and later identify the operation and outcome. Avoid tying long server work to a blocking spinner. [Waits and interruptions][waits]

42. **Preserve an investigation trail.** Keep enough previous results and notes to resume interrupted analysis. Avoid overwriting the only evidence when a new batch runs. [Waits and interruptions][waits]

### Forms and settings

43. **Keep labels visible.** Put short labels near inputs, usually above them. Avoid placeholder-only labels that disappear during editing; very compact expert forms require tested alternatives. [Text input][text]

44. **Match field size to expected content.** A short code and a long description should not look identical. Avoid narrow fields that hide meaningful input; use a textarea for multiline content. [Text input][text]

45. **Explain unfamiliar units.** Put units and concise hints with the field. Avoid forcing users to discover whether a value is dollars, cents or percent by submitting it. [Text input][text]

46. **Accept harmless formatting.** Trim accidental whitespace and support unambiguous input variations. Avoid rejecting pasted codes or names with accents; do not guess ambiguous dates. [Validation][validation]

47. **Preserve failed input.** Return the filled form with actionable inline errors and an error summary. Avoid clearing the user's work after one invalid field. [Validation][validation]

48. **Validate at a useful moment.** Do not attack an unfinished value with errors on every keystroke. GOV.UK defaults to submit-time validation; earlier feedback needs task-specific evidence. [Validation][validation]

49. **Separate service failure from input failure.** A server outage is not a field error. Avoid asking users to change correct information; explain recovery in the right place. [Error messages][errors]

50. **Use the question's language in errors.** Tell users what to correct in familiar terms. Avoid backend names, codes without meaning, and blame. [Error messages][errors]

51. **Use checkboxes for independent choices.** Give each option a clear label and clickable target. Avoid radio-like exclusivity without explanation; “none” requires explicit mutually exclusive behavior. [Checkboxes][checks]

52. **Use radios for one choice.** Keep options visible when the list is short. Avoid multiple checkboxes for a single business state; long enumerations may justify a select. [Radios][radios]

53. **Do not preselect consequential answers casually.** An apparent default can become an accidental declaration. Product preferences may have sensible defaults; facts and consent need different treatment. [Radios][radios]

54. **Type memorable dates.** For dates users already know, support direct entry. Avoid calendar navigation across decades; scheduling tasks benefit from a calendar's weekday context. [Date input][date]

55. **State date interpretation.** Use explicit labels or examples for day/month/year. Avoid locale ambiguity; a familiar regional convention is useful only when the audience and parsing agree. [Date input][date]

56. **Review high-consequence submissions.** Provide a summary with direct Change links. Avoid forcing users back through every step; skip ceremony for easy-to-reverse settings. [Check answers][review]

57. **Separate draft changes from commitment.** Make the final action's effect clear on the review screen. Avoid a generic Continue that unexpectedly submits a transaction. [Check answers][review]

58. **Do not make a disabled button a puzzle.** Explain the missing prerequisite nearby, or let submission reveal errors. Disable actions with clear state constraints; avoid inaccessible hover-only explanations. [Disabled-button critique][disabled]

59. **Keep button states distinct.** Focus, hover, pressed, enabled and disabled should remain recognizable. Avoid a tasteful low-contrast active button that looks unavailable. [Button states][buttons]

60. **Use autocomplete honestly.** Distinguish suggestions from required known values. Avoid silently committing the first suggestion on blur unless that behavior fits the task and is clear. [APG combobox][combo]

### Dialogs, menus, tabs and editing

61. **Reserve modality for a focused decision.** Use a page for substantial multistep work. Avoid opening an onboarding or marketing interruption over someone else's unfinished task. [Modal guidance][modal]

62. **Keep relevant context visible.** A dialog should not cover information needed to answer it. Prefer a side panel for inspection that must coexist with the underlying list. [Modal guidance][modal]

63. **Move focus into a modal.** Trap focus while the background is inert; provide a visible close route and Escape. Avoid a visual overlay while keyboard focus still reaches hidden content. [APG dialog][dialog]

64. **Restore focus after dismissal.** Return to the invoking control or the next logical task location. Avoid dropping focus at the document start after deleting a row. [APG dialog][dialog]

65. **Choose safe initial focus.** For irreversible actions, consider the least destructive option. Avoid an accidental Enter approving destruction; lengthy dialog content may need initial focus on its heading. [APG dialog][dialog]

66. **Implement menus as menus.** Use arrow navigation and predictable dismissal for command menus. Avoid assigning menu roles to ordinary navigation links without the expected keyboard behavior. [APG menu][menu]

67. **Distinguish a command from a submenu.** Mark commands that open further choices. Avoid a label that suggests immediate action but opens an unexplained nested menu. [APG menu][menu]

68. **Make tabs switch related panels.** Expose the active tab and provide arrow-key movement. Avoid using tab styling for unrelated destinations without preserving navigation semantics. [APG tabs][tabs]

69. **Avoid slow activation on focus.** Automatic tab activation works when content appears promptly. Use explicit activation for costly loads so arrowing through tabs does not trigger several waits. [APG tabs][tabs]

70. **Support both syntax and visible formatting.** Markdown shortcuts can speed expert writing; a toolbar serves others. Avoid making users memorize syntax to create routine lists or links. [Linear editor][editor]

71. **Respect editor undo.** Undo and redo should reverse text edits predictably. Avoid a global command stealing undo while the cursor is inside a document. [Linear editor][editor]

72. **Make sending versus newline explicit.** Comment composition must have predictable Enter behavior. Linear's 2026 preference illustrates a legitimate choice; do not silently change it for existing users. [Linear changelog][enter]

73. **Offer portable copying.** Let users copy useful text in a predictable format. Avoid copying decorative UI alongside content; Linear documents Markdown copying as an expert escape route. [Linear editor][editor]

### Loading, interruptions and notifications

74. **Acknowledge work promptly.** Show that a request started before results arrive. Avoid encouraging repeated clicks through silence; feedback does not replace making the operation fast. [Progress][progress]

75. **Use truthful progress.** Show percent only when it has meaning; otherwise show stages. Avoid a bar stuck at 99% with no explanation. [Waits and interruptions][waits]

76. **Name completed work.** A completion message should identify the job or result. Avoid “Done” after the user switched context among several analyses. [Waits and interruptions][waits]

77. **Keep urgent alerts accessible.** Announce important dynamic messages without moving focus. Avoid interrupting typing for an ordinary notification; truly blocking decisions belong in an alert dialog. [APG alert][alert]

78. **Do not hide recovery in a fleeting toast.** Keep important failures and corrective actions reachable. Avoid making the only retry disappear before a user can read it. [APG alert][alert]

79. **Separate notification channels.** Let users control email, in-app and external-channel delivery. Avoid treating one global switch as sufficient for people with different work rhythms. [Notifications][notifications]

80. **Explain bundled notification categories.** State what each category includes. Avoid a toggle called status updates that also silently controls other important changes; Linear documents grouping limits. [Notifications][notifications]

81. **Retain an in-app destination.** Notifications should lead to the relevant work and remain discoverable. Avoid relying on ephemeral email or OS delivery as the sole record. [Notifications][notifications]

82. **Do not steal focus on ordinary status changes.** Updating feedback should let users continue working. Avoid every background refresh behaving like an urgent warning. [APG alert][alert]

### Organizations, permissions and invitations

83. **Show role and lifecycle state separately.** Pending, active and suspended are not permission levels. Avoid hiding past contributors when access is revoked; Linear retains suspended members for history. [Members and roles][roles]

84. **Explain where access is managed.** When an identity provider controls membership, link to that authority. Avoid editable controls that cannot persist their changes. [Members and roles][roles]

85. **Provide an administrator contact route.** A blocked member should know whom to ask. Avoid a dead-end permission error; Linear exposes a way to find workspace admins. [Members and roles][roles]

86. **Show effective access, not only one grant.** Explain inheritance and broader grants. Avoid a reassuring read-only control while group membership still permits editing. [Notion permissions][permissions]

87. **Preview permission changes when moving content.** Moving between private and shared areas can change access. Avoid treating all moves as harmless organization; inherited and explicit child permissions may differ. [Notion permissions][permissions]

88. **Test contractor contribution, not only viewing.** Verify creating and updating records without exposing unrelated work. Avoid assuming a guest role supports the actual subcontractor workflow. [Permission complaint][permissioncomplaint]

89. **Label invitation cost before sending.** Distinguish paid membership from limited guest access. Avoid an upsell embedded in invitation flow that looks like required setup. [Notion billing][notionbill]

90. **Show billing effect of removal.** State when seats stop billing and whether seats remain reusable. Avoid implying that removing a person produces an immediate prorated refund. [Notion billing][notionbill]

### Imports, exports, recovery and billing

91. **Keep a normal file picker.** Drag-and-drop may supplement it. Avoid drag-only upload; explain supported files before users prepare or choose them. [File upload][upload]

92. **Distinguish upload from processing.** Bytes transferred do not mean a document is accepted. Show later validation and completion; avoid 100% implying operational success. [Upload states][wireframes]

93. **Explain migration losses before import.** Map source concepts and identify unsupported content. Avoid promising a complete move based only on record counts; Linear documents that some concepts may not import. [Import guide][import]

94. **Allow a safe sample migration.** Let teams inspect representative data before the full move. Avoid requiring irreversible trust up front; Help Scout documents an Import2 sample and resumable status route. [Help Scout migration][helpscout]

95. **Make exports useful outside the app.** State formats, included files and scope. Avoid describing a proprietary dump as complete portability; Notion documents HTML, Markdown, CSV and attachments. [Export][export]

96. **Separate export from round-trip backup.** Explain what can be read or restored. Avoid implying an exported workspace can recreate every permission and relationship; verify import fidelity separately. [Export][export]

97. **Preview historical restoration.** Show author, time and differences before replacing content. Avoid forcing restoration merely to inspect an old version. [History][history]

98. **Expose recovery limits.** State retention and plan limits where users need recovery. Avoid discovering the history window only after an incident. [History][history]

99. **Make billing self-service.** Offer invoices, payment updates and clear cancellation timing. Avoid support tickets for routine administration; negotiated contracts may require a separate process. [Stripe portal][stripe]

100. **Confirm cancellation distinctly from payment failure.** Show effective date and remaining access, with a reachable export. Avoid ambiguous unpaid states and hidden exit routes; the Notion complaint shows why users may conflate them. [Stripe portal][stripe]; [user account][complaint]

## Visual design directions and resources

These are coherent directions supported by inspected examples, not a trend ranking or one prescribed average. A product screenshot establishes appearance. A release note establishes the maker’s shipped intent. Neither proves improved retention. Direct inspection on 2026-11-07 covered Linear’s published sidebar comparison, Plausible’s live public dashboard and date-range menu, and Basecamp’s published group-Pings image. Other examples below were read in product/design-system documentation, not audited in customer accounts.

### 1. Quiet, dense workbench

Linear’s March 2026 sidebar comparison retains a clear selection while quieting inactive navigation and separating groups. Use restrained neutrals, consistent icons and limited status color for expert queues. The risk is losing contrast and click cues. This is a funded reference, not indie-economics evidence. [Linear design account](https://linear.app/now/behind-the-latest-design-refresh)

### 2. Focused analytical dashboard

Plausible’s live demo puts a metric strip above a dominant line chart, then aligned breakdown panels. Inspected dark mode uses neutral cards, a purple series and small directional comparisons. The date menu exposes common periods, the current selection and shortcut hints together. This fits a product with a small set of recurring questions. Preserve consistent number alignment, restrained chart color and an explicit reporting period. It fails when every metric becomes a hero card or advanced questions require awkward workarounds. The public demo proves these visible states; no speed, screen-reader or long-term reliability benchmark was run. [Live dashboard](https://plausible.io/plausible.io), [dashboard guide](https://plausible.io/docs/guided-tour)

### 3. Familiar document editor

Tally documents a page-first form builder: type text, use `+` or `/` to insert questions, then configure blocks. This offers familiarity to people who think in documents. The corresponding direction uses readable text, strong content hierarchy, spare surrounding chrome and contextual tools. Keep a visible insertion route alongside shortcuts; explain consequential block settings. It fits forms, proposals and knowledge work. It fails when complex rules are hidden inside apparently plain prose or hover controls become the only way to edit. The guide establishes the model; this research did not execute a full Tally authoring session. [Tally authoring guide](https://tally.so/help/create-a-form)

### 4. Human, project-centred collaboration

Basecamp’s inspected October 2026 Pings image groups faces into circular collages and adds an explicit participant count beyond the visible avatars. That is character tied to useful information. Its Basecamp 5 account describes a home screen with recent projects/activity and notifications alongside work. A compatible direction uses recognisable people, readable project names, clear containers and friendly copy; reserve illustration for orientation or welcome states. It suits small-team collaboration. It fails when warmth becomes visual clutter or decorative avatars replace names/counts. Product claims and selected testimonials do not establish that every existing customer likes the redesign. [Pings change](https://basecamp.com/updates/a-better-look-for-group-pings), [Basecamp 5](https://basecamp.com/5)

### 5. Explicit enterprise system

Carbon’s table system provides structured toolbars, selection/expansion and five row sizes; it explicitly distinguishes a data table from a spreadsheet application. Atlassian separates marketing typography from app typography and defines text tokens for product hierarchy. This direction suits administrative workflows with many states and many contributors: use a deliberate grid, consistent field/control heights, visible action hierarchy and restrained semantic colors. Its cost is system maintenance; its trap is importing a vendor’s entire visual identity or every component variant into a small product. Documentation reviewed; no claim that stock components guarantee accessibility or task fit. [Carbon table guidelines](https://www.carbondesignsystem.com/building-blocks/core/components/data-table/guidelines), [Atlassian typography](https://atlassian.design/foundations/typography)

### Where restraint becomes ambiguity

NN/g’s 2017 experiment used 71 participants and nine modified web pages. Weak click cues increased time to locate a target by 22% and fixations by 25%. This was a controlled findability experiment, not a longitudinal B2B trial or a 22% conversion penalty. It supports testing whether buttons/links still look actionable when simplifying visuals. It does not establish that every border, shadow or saturated accent improves a product. Keep controls legible before making navigation quieter. [Study and limitations](https://www.nngroup.com/articles/flat-ui-less-attention-cause-uncertainty/)

### Motion

Atlassian’s current motion guidance distinguishes short interaction feedback from larger transitions, says motion should not block the next action, and labels the new token system Early Access. Its documented 50–150ms interaction and 150–400ms transition ranges are vendor starting points, not universal timing laws. For SaaS, use motion to show where an item went, what opened and whether a change succeeded; repeated work should remain fast. The example panels and labels were visually inspected; playback was not verified and timing was not measured frame by frame. [Atlassian motion](https://atlassian.design/foundations/motion)

Honor `prefers-reduced-motion`; reduce or replace non-essential scaling/panning. Keep a static indication of success and selection. Disable animation during review to verify that meaning remains. This is a platform preference, not an aesthetic dispute. [MDN reduced motion](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/At-rules/@media/prefers-reduced-motion)

### Resources worth using

| Resource | Best use | Limits and implementation fit |
| --- | --- | --- |
| [Mobbin](https://mobbin.com/) | Shipped screen references across web/mobile; compare the same task across products | Public site advertises weekly additions and a paid/full library. Check capture dates and web scope. Screens do not prove flow quality or grant reuse rights to brand assets. |
| [Page Flows](https://pageflows.com/) | Recorded flows, annotations and emails; better than a lone screenshot for sequence | Public site inspected in browser after text-fetch 403. Full access is paid; advertised trial is paid too. No paid recordings reviewed. Verify each capture’s recency. |
| [Linear’s design writing](https://linear.app/now/behind-the-latest-design-refresh) | Detailed product-design rationale and before/after references | First-party intent; reproduce the reasoning only when the task matches. No permission to copy its identity. |
| [Carbon](https://www.carbondesignsystem.com/building-blocks/core/components/data-table/guidelines) | Complex data/control states and working component references | Strong enterprise reference; a table is not a spreadsheet. Check component version and framework fit. |
| [Atlassian foundations](https://atlassian.design/foundations/typography) | Text hierarchy, spacing, motion and token discipline | Product/brand fonts differ; vendor assets may have restricted access or terms. Use the principles without assuming a font licence. |
| [Inter](https://rsms.me/inter/) | Open font for compact UI; tabular figures, disambiguation features and variable optical sizes | SIL OFL 1.1. Test your languages and small sizes; a broad glyph set is not complete world-script coverage. Self-hosting avoids a runtime font-CDN dependency. |
| [Lucide](https://lucide.dev/license) | Consistent SVG icon family across stacks | ISC, with MIT notices for inherited Feather icons. Keep required notices; add text/accessibility labels where meaning is ambiguous. |
| [Plausible source](https://github.com/plausible/analytics) | Inspect a real dashboard implementation and compare it with the public demo | AGPL-3.0; hosted and community editions differ. Read obligations before copying code. Product simplicity does not imply a trivial analytics backend. |

Choose a direction using a populated list, a long form, one error state and a narrow window. Compare typography, grouping, contrast and selected/focused/disabled states together. A landing-page mockup alone cannot settle an application’s design.

## Compatibility and platform citizenship

Treat compatibility as four promises: the app opens; core features work; the layout/input suit the device; important workflows have been tested there. A JavaScript build target answers only part of the first promise. Recommendations below are research-derived strategies, not universal support requirements.

### Browser support policies

**Start with audience evidence.** Baseline “newly available” means interoperability across its core browsers; “widely available” adds 30 months. It helps select web features, but does not establish your customers’ browser fleet, assistive-technology behavior or managed-device policies. Record a dated browser floor, test it, and use newer capabilities as enhancements where possible. Global usage percentages can hide an important contracted customer. [WebDX/Baseline](https://web.dev/baseline)

**Real products choose different windows.** Notion currently documents the last eight Chrome Extended Stable releases and the last two major Firefox, Safari and Edge releases. Slack describes roughly 12–18 months of browser support and six-month requirement updates; unsupported browsers can lose sign-in and administration access. These examples establish viable policy shapes, not the right floor for an indie app. Tell administrators before removing support; keep the unsupported-browser page usable without the failed feature. Checked 2026-11-07; Slack lists further retirements for November 9. [Notion](https://www.notion.com/help/system-requirements-for-notion), [Slack lifecycle](https://slack.com/help/articles/1500001836081-Slack-support-lifecycle-for-operating-systems-app-versions-and-browsers)

**Separate optional graphics from ordinary work.** Figma’s current requirements distinguish WebGL rendering from WebGPU shader support and list browser/OS minima separately. Its docs also discuss GPU drivers and a battery/performance tradeoff on dual-GPU machines. A canvas editor must test that chain; a CRM should not acquire it accidentally. Provide a comprehensible failure screen and preserve access to records/exports when an optional renderer fails. These are derived design consequences, not features verified in Figma. [Figma requirements](https://help.figma.com/hc/en-us/articles/360039827194-What-are-the-system-requirements-for-Figma)

| Strategy | Fits | Implementation and support cost | Failure to avoid |
| --- | --- | --- | --- |
| Conservative business forms | Mixed customer fleets; occasional use; procurement constraints | Semantic server-rendered core; documented browser floor; progressive enhancements; test oldest supported versions | Assuming a modern build tool supplies every missing runtime API |
| Current evergreen app | Frequent users with updateable machines; rich interactions | Chromium, Firefox and Safari test coverage; rolling deprecation notice; older open-tab handling | Testing Chrome only because customers use several Chrome-branded browsers |
| Feature-tiered specialist app | Graphics, local files, media, large editors | Capability detection; tested fallback or explicit feature restriction; GPU/device cases | Rejecting the whole app when one optional API is absent |
| Contracted enterprise fleet | Regulated or managed environments | Agree exact browser/security/network matrix; include its cost in the contract | Promising an untested legacy environment during a sale |

These are proposed support strategies derived from the policies above. No market-share ranking or measured small-team cost comparison is available from those sources.

### Screen, input and accessibility axes

**Window size and zoom.** Test a narrow desktop window, browser zoom and phone viewport separately. Reflow guidance uses 320 CSS pixels for vertically scrolling content, with exceptions for genuinely two-dimensional content such as data tables. That exception does not excuse the whole application shell or unreadable individual cells. Keep controls reachable, permit a bounded table scroller and provide a practical record detail view. Test long labels rather than only empty English fixtures. [W3C reflow](https://www.w3.org/WAI/WCAG22/Understanding/reflow.html)

**Mouse, touch and stylus.** Dense desktop lists can remain dense without tiny activation areas. WCAG 2.2’s minimum target criterion specifies 24×24 CSS pixels or qualifying alternatives, including spacing; it is not a universal recommendation to make every control exactly 24 pixels. Coarse pointers merit larger targets. Supply a non-drag way to reorder or move records and keep hover-only information reachable. Test hybrid laptops as well as phones. [W3C target size](https://www.w3.org/WAI/WCAG22/Understanding/target-size-minimum.html)

**High contrast and native semantics.** Windows forced-colors mode can remove shadows and replace colors. If a field or selected item exists only through a shadow or background tint, its boundary can disappear. Test actual forced colors; add targeted borders/system colors when needed. A `div` with a button role does not receive all native button color behavior. Do not disable the user’s palette across the whole app to preserve branding. [MDN forced colors](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/At-rules/@media/forced-colors)

### Interruptions, storage and multiple windows

**A background tab is not a running server.** Chrome documents frozen and discarded states; a discarded page cannot run a final callback. Save meaningful edits incrementally, stop unnecessary hidden work, restore view state and reconnect/revalidate on return. A scheduled business operation belongs on durable server infrastructure if it must run after the tab closes. Do not promise completion from a browser timer. These implementation consequences follow the documented lifecycle. [Chrome lifecycle](https://developer.chrome.com/docs/web-platform/page-lifecycle-api)

**Unsaved-change warnings are a last guard.** `beforeunload` is unreliable, especially when mobile users switch apps and later kill the browser. Attach it only while there is unsaved work; preserve drafts before that point. A successful navigation warning test does not prove crash recovery. Test tab termination, browser restart and expired authentication with a real partly completed form. [MDN beforeunload](https://developer.mozilla.org/en-US/docs/Web/API/Window/beforeunload_event)

**Local storage is not a backup.** Browser storage is best-effort by default; quotas and eviction differ, and private-session data is usually removed when the session ends. Handle quota errors, label unsynced work and explain what remains local. A persistence request can help but cannot prevent user deletion. Test low disk space and clearing site data. Offline write support also requires conflict, authorization and recovery rules; caching pages alone does not supply them. [MDN quotas and eviction](https://developer.mozilla.org/en-US/docs/Web/API/Storage_API/Storage_quotas_and_eviction_criteria)

**Tabs must not silently disagree about identity.** BroadcastChannel can coordinate same-origin contexts within the same storage partition. Use such messages to invalidate local views after logout or organization changes; the server still authorizes every request. Keep organization scope explicit in URLs, requests and caches. Revalidate stale forms before applying consequential writes. Embedded and top-level pages may be partitioned differently, so cross-tab communication is an optimization, not the authority. [MDN BroadcastChannel](https://developer.mozilla.org/en-US/docs/Web/API/Broadcast_Channel_API)

**Copy/paste is core business work.** Preserve selectable text and ordinary keyboard copy/paste. Programmatic clipboard APIs require secure contexts and browser-specific permission/activation behavior. Offer a manual copy path when access is denied; do not display “Copied” after failure. For rich tables, plain-text and HTML representations can serve different destinations. Test spreadsheet paste, multiline cells and paste into plain-text tools. [MDN Clipboard](https://developer.mozilla.org/en-US/docs/Web/API/Clipboard_API)

**Installation is an optional distribution surface.** Manifest-based installation, browser-installed websites and home-screen shortcuts differ. Desktop Chromium, Safari Add to Dock and mobile flows do not share one installation contract. Keep the URL experience complete and document supported installed modes separately. Installation does not establish offline availability, durable background execution or notification permission. Test authentication callbacks and external links in both modes. [MDN PWA installation](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Guides/Making_PWAs_installable)

**International data arrives before translated UI.** UTF-8 forms permit names and content in many scripts. Mixed-direction text needs direction/isolation handling; punctuation and identifiers can display misleadingly when simply concatenated. Test Arabic/Hebrew names next to Latin IDs, accented names, long company names and imported files. Full localization remains a product investment; safe storage and readable user data are foundational. [W3C multilingual forms](https://www.w3.org/International/questions/qa-forms-utf-8), [W3C bidirectional text](https://www.w3.org/International/articles/inline-bidi-markup/)

**Time-zone semantics are domain semantics.** Distinguish an instant, a date without time, and a recurring local appointment. Show the report or organization zone where it affects totals; preserve an all-day deadline as a date rather than converting midnight through each viewer’s zone. Test daylight-saving gaps/repeats and users travelling between zones. W3C’s July 2025 *Group Draft Note* gives the relevant distinctions; it remains draft guidance, not an endorsed standard. [Working with Time and Timezones](https://www.w3.org/TR/timezone/)

**Input methods need real typing tests.** Enter can confirm an IME composition rather than submit a form. Keyboard handlers must account for composition and not steal editing commands. Test Japanese/Chinese composition, alternate keyboard layouts, dictation and password-manager autofill in the actual browser/editor combination. `isComposing` exposes composition state, but API presence alone does not test the whole sequence. [MDN composition state](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/isComposing)

**Privacy settings are supported environments.** Embedded login or widgets may break when third-party cookies are blocked or partitioned. Test private browsing, Safari protections, Firefox protection and administrator restrictions. Prefer an authenticated top-level recovery path over asking customers to weaken global privacy settings. Set cookie policy deliberately; `SameSite=None` is not a universal escape from browser blocking. [MDN third-party cookies](https://developer.mozilla.org/en-US/docs/Web/Privacy/Guides/Third-party_cookies)

**Measure the work, including large accounts.** Google’s good Core Web Vitals thresholds are LCP ≤2.5s, INP ≤200ms and CLS ≤0.1 at the 75th percentile, segmented by mobile/desktop. These are useful web-health targets, not complete SaaS quality measures. Also measure opening the largest supported list, editing, searching, saving and export completion. Segment by tenant size and device; a fast empty demo can hide unusable mature accounts. [Web Vitals](https://web.dev/articles/vitals)

### Networks, deployment changes and test coverage

**Online is a hint, not proof.** `navigator.onLine` can report a connected LAN without internet, or misclassify access behind a VPN/firewall. Try the actual operation and handle its result; do not disable the application solely because the flag says offline. Preserve input after timeout and show uncertain completion separately from confirmed failure. For a write whose response was lost, reconcile before retrying a second effect. [MDN network status](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/onLine)

**Real-time transport needs a failure mode.** MDN documents low per-browser/domain connection limits for SSE over HTTP/1, shared across tabs; HTTP/2 negotiates streams differently. Test several tabs, connection loss and delayed messages. If push updates stop, show freshness and provide a refresh/polling route where practical. Reconnect must catch up from durable state; a new socket alone cannot recover missed work. These are derived requirements, not a claim every app needs live updates. [MDN SSE](https://developer.mozilla.org/en-US/docs/Web/API/Server-sent_events/Using_server-sent_events)

**Printed work has its own layout.** An invoice, approval record or operational report should include identity, period, units and context without the navigation shell. CSS print media and `@page` provide dedicated styling. Test long tables, page breaks, charts in monochrome and print-to-PDF; a screenshot export may cut off virtualized rows. Offer an explicit server export for complete large datasets rather than pretending the currently rendered viewport is the whole report. [MDN printing](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Media_queries/Printing)

**Test shipped environments, not only engine approximations.** Playwright runs Chromium, Firefox and WebKit variants and can target Chrome/Edge channels. Its WebKit is patched and can precede shipped Safari; it does not drive branded Safari. Browser policies, codecs and OS services can differ. Use engine tests for frequent regression coverage and real supported browser/OS/device checks for high-risk flows. A mobile viewport emulation does not reproduce an actual keyboard, file picker or memory limit. [Playwright browser scope](https://playwright.dev/docs/browsers)

**Accessibility checks are a floor.** W3C's Easy Checks explicitly warns that passing a quick review can leave significant barriers. Run the whole main workflow with keyboard and representative screen-reader/browser combinations, including errors, dialogs, tables and refreshed results. Verify meaningful headings, labels, focus order and announcements. Automated checks alone cannot prove a task is understandable or completable. [W3C first review](https://www.w3.org/WAI/test-evaluate/preliminary/)

The following is a proposed risk-based test matrix, derived from the platform contracts above and the incident evidence below. It is not a universal certification checklist. Select combinations from actual customers; every added promise carries ongoing regression and support cost.

| Scenario | Expected behavior; failure caught | Priority and cost |
| --- | --- | --- |
| Slow save; response lost after commit | Preserve draft; reconcile operation identity; prevent a duplicate charge/send | Core writes; cheap fault injection, harder external-system reconciliation |
| Session expires during long form | Reauthenticate and recover work within the same authorized tenant | Every authenticated editor; test redirects and sensitive draft handling |
| Two tabs edit the same record | Detect stale version or apply documented merge policy; make conflicts reviewable | Shared mutable records; requires server semantics, not only UI banners |
| Old tab survives a deployment | Compatible API/assets or a recoverable reload after saving draft | Frequent releases; test old client against new server before rollout |
| Large tenant with long names/files | Bounded response/render work; clear pagination/export scope; no hidden truncation | Data-heavy tools; fixtures and load tests need realistic distributions |
| Managed laptop behind proxy | Core works with agreed domains/features; explain blocked optional services | Enterprise buyers; extra procurement/debug/support work |
| Narrow window on a large monitor | Reflow based on available width; no assumption that desktop means full screen | Broad baseline; test zoom and split-screen, not only phone presets |
| Phone with keyboard open | Active input, errors and submit remain reachable; scrolling keeps context | Mobile approval/data-entry customers; real-device checks needed |
| Background/restart/low-memory tab | Recover last confirmed state and identify unsynced data | All long-lived sessions; local caches alone are insufficient |
| Large file; storage quota/full disk | Stop safely, preserve accepted work, explain retry/cleanup | Upload/offline products; adds resumability and quota testing |
| Invite opened on another device | Clear account/organization choice, expiry and existing-member handling | Collaboration products; do not assume email link opens the originating session |
| Account revocation while offline | Server rejects later unauthorized writes; local data policy is explicit | Offline-capable tools; expensive security/product contract |
| Print/export during filters or selection | Clearly state current subset versus all records; stable complete output | Finance/operations; dedicated output tests |

**Authentication must permit assistance.** WCAG 2.2’s accessible-authentication minimum covers the path through login, MFA and authentication used in recovery. Support password managers and pasted credentials/codes. A visually attractive six-box OTP control fails its purpose if a whole-code paste fills only its first digit. Do not replace a visual transcription CAPTCHA with an audio transcription challenge and assume the cognitive barrier disappeared. The AA criterion allows specified exceptions; it does not prohibit all passwords or all CAPTCHA. **Derived test:** exercise saved-password fill, whole-code paste and the actual recovery path, including expired-session reauthentication during work. The W3C document is explanatory guidance for the criterion, not a jurisdiction-specific legal opinion. [W3C explanation](https://www.w3.org/WAI/WCAG22/Understanding/accessible-authentication-minimum.html).

## Reliability, trust and optional AI

**Tenant isolation is part of product correctness.** A correct list rendered with another company’s cached data is a critical failure. Derive tenant context from authenticated authority; scope queries, files, jobs and caches consistently. Classify truly global data separately. Test guessed IDs, direct export URLs, search indexes, delayed jobs and a user who belongs to several organizations. Cache isolation does not replace authorization. [OWASP multi-tenant guidance](https://cheatsheetseries.owasp.org/cheatsheets/Multi_Tenant_Security_Cheat_Sheet.html)

**A hidden button is not a permission check.** Enforce access on every request and object, deny unmatched access by default, and test the negative cases. Do not assume an authentication library understands the domain’s roles, sharing relationships or object ownership. Guest, billing administrator and operator capabilities should be explainable in product language. [OWASP authorization](https://cheatsheetseries.owasp.org/cheatsheets/Authorization_Cheat_Sheet.html)

**Record decisions without leaking records.** Useful diagnostics link actor, operation, target and result across a request or job. Avoid placing passwords, tokens, raw sensitive payloads or unnecessary customer data into logs. Restrict log access and retention as deliberately as application data. A customer-visible audit trail and debugging logs serve different audiences; do not expose one as the other without review. [OWASP logging](https://cheatsheetseries.owasp.org/cheatsheets/Logging_Cheat_Sheet.html)

**Monitor the customer outcome.** Google’s SRE book distinguishes latency, traffic, errors and saturation and warns that noisy paging consumes human attention. A small team can apply those principles without adopting Google’s infrastructure. Monitor whether login, saving and background work succeed; a running process is insufficient. Set response expectations that someone can meet, and preserve enough evidence to explain an incident. This is operational guidance, not a selection of a telemetry backend. [SRE book, chapter 6](https://sre.google/sre-book/monitoring-distributed-systems/)

**Integrations are recurring work.** Stripe documents duplicate and out-of-order webhook delivery. Validate the sender, durably accept relevant events, deduplicate effects and reconcile against authoritative objects. Show integration health and actionable failures in the app. A one-time successful OAuth or webhook test does not establish reliability under revocation, replay or backlog. These conclusions apply by analogy to other integrations only after checking their contracts. [Stripe webhook contract](https://docs.stripe.com/webhooks)

**Retry one intent, not an accidental second purchase.** Idempotency keys allow safe retries, but their retention and error semantics are provider-specific. Stripe’s current documentation distinguishes API v1 and v2 behavior. Keep a stable operation identity through uncertain outcomes and show pending/unknown separately from failed. A disabled browser button does not prevent duplicates after timeout or reload. [Stripe idempotency](https://docs.stripe.com/api/idempotent_requests)

**AI is an optional workflow, not an authorization layer.** Retrieved documents, email and tool output can carry prompt injection. Enforce tenant access, tool permissions and argument validation outside the model; validate proposed high-impact actions before execution. Make source material, edited fields and resulting actions reviewable. Test refusals and incorrect plausible output as well as successful demos. Include model cost and latency in the business case. Do not infer that every B2B app needs a chat box or autonomous writes. [OWASP prompt-injection guidance](https://cheatsheetseries.owasp.org/cheatsheets/LLM_Prompt_Injection_Prevention_Cheat_Sheet.html)

## Incident evidence: bulk operations, migrations and recovery

These primary postmortems describe historical failures and the vendors’ own investigation. They support concrete failure modes, not current reliability rankings or incident prevalence. The design lessons are our inferences.

**Atlassian, April 2022; postmortem April 29.** An app-retirement operation received whole-site identifiers instead of app identifiers. The deletion API accepted both. An earlier 30-site canary used different, correct input; the later batch deleted 883 sites representing 775 customers. Monitoring missed a destructive action performed through an otherwise legitimate workflow. Existing recovery could restore individual stores/sites but was not ready for coordinated bulk restoration; some customers waited up to 14 days. **Derived controls:** preview target type, tenant, human-readable name and count; validate the actual batch; keep disable, reversible delete and permanent destruction distinct; alert on unusual volumes of valid actions. Rehearse multi-tenant restoration and show per-tenant recovery progress. A successful small canary is weak protection when the next batch’s input source changes. [Postmortem](https://www.atlassian.com/blog/how-we-build/post-incident-review-april-2022-outage).

**GitLab, January 2017; postmortem February 10.** During replica recovery, an engineer deleted primary database files. Scheduled dumps had been failing because of a tool/server version mismatch; failure emails were rejected. Recovery used a roughly six-hour-old staging snapshot. Staging had scrubbed webhooks, requiring separate recovery; slow storage made copying take roughly 18 hours. Repositories and wikis were unavailable but did not lose data, unlike affected database records. **Derived controls:** test restorability after upgrades, including hooks, identities and attachments; monitor backup age and test alert delivery. Protect restoration from accidental external side effects. Communicate unavailable versus lost versus recovered data separately. Show honest uncertainty until datasets are reconciled. Keep status publishing independent of the failed service. “Backup exists” and “service can recover within its promise” require separate evidence. [Postmortem](https://about.gitlab.com/blog/postmortem-of-database-outage-of-january-31/).

### Migration is an operating change

[Help Scout’s current import guide](https://docs.helpscout.com/article/1495-import-emails-or-tickets-into-help-scout) requires user/inbox setup before the sample and excludes several configurations. It recommends switching incoming email and pausing work at cutover. This adds a practical UX point: migration is a coordinated operating change, not merely a file picker. [Import2](https://help.import2.com/en/articles/630139-free-sample-migration-overview) describes a randomized sample across record types; a sample cannot certify every record. [Front’s guide](https://help.front.com/en/articles/2223), edited September 29, 2026, says its own Help Scout importer is no longer actively maintained and recommends partners; its built-in route excludes notes/comments. Do not infer portable support histories from a generic import checkbox.

## Conversion, retention and distribution

Evidence of signup lift is useful but incomplete. Compare qualified, retained paying accounts by acquisition cohort; measure support and infrastructure costs alongside the funnel.

### WorkZone: direct web-B2B demo-form A/B test

[Wingify/VWO case study](https://wingify.com/success-stories/workzone/). Web project/document collaboration app tested black-and-white customer logos against colored logos beside a demo-request form. Only new visitors; 22-day run. Vendor reports 34% more form submissions and 99% statistical significance. Sample count, allocation, stopping rule, test dates, qualified-lead rate and eventual sales absent from body. Heatmap clicks on logos supported the distraction hypothesis, but do not prove the mechanism. This is direct web-B2B experiment evidence, with vendor-selected success and reporting limitations. Lesson: social proof placement and visual hierarchy deserve testing. Do not prescribe grayscale logos or promise 34% revenue growth.

### Teamleader: direct web-B2B regional signup A/B tests

[Wingify/VWO case study](https://wingify.com/success-stories/teamleader/). European SME CRM/invoicing/project-planning vendor. Adding “No Credit Card Required” raised Netherlands signup conversion 48.7%→54.8%; Belgium 33%→38.6%. This tested explanation of existing terms, not requiring versus removing a card. A Belgium form redesign bundled CTA, font, fields and required markers: 34.3%→37.5%; cannot attribute improvement to one element. Netherlands customer-logo variant: 36%→40.3%. Vendor case lacks sample sizes, run dates, stopping rules and paid/retained outcomes in accessible text. Rates use visitors to signup pages, not all site visitors. Larger established vendor, not indie. Regional differences reinforce segmenting conversion; cannot infer national preference from two uncontrolled comparisons across audiences. Current page retrofits Wingify branding, so copyright/crawl dates are not experiment dates.

### ChartMogul / Growth Unhinged / ProductLed, Conversion Report (2026-02-04)

[Original report](https://chartmogul.com/reports/saas-conversion-report/). January 2026 survey of 200 products; free-to-paid means leads/free signups becoming paid within six months. Typical respondent: $1–10M ARR, $50–249 monthly revenue per customer. Median 8%; large dispersion makes it a poor universal target. 57% use trials, 26% freemium, 7% reverse trials; 62% of trial products use 14 days. Card-required trials report 30% conversion, over five times no-card trials. The report says freemium versus trial differences disappear after signup rates are included. These are **observational, self-reported comparisons**, not randomized effects. Enterprise self-serve often includes human help: 80% of trial products report human enterprise touchpoints. Design implication: instrument the whole account funnel, split acquisition channels, include assisted sales, and wait for cohorts to mature. Do not infer that adding a card field multiplies revenue fivefold. Its graphic and prose conflict on one signup statistic, which is excluded here.

### Yoganarasimhan, Barzegary, Pani, Design and Evaluation of Optimal Free Trials (2023)

[Published paper, author-hosted PDF](https://faculty.washington.edu/hemay/Free_Trial.pdf), Management Science 69(6):3220–3240, DOI 10.1287/mnsc.2022.4507. **Adjacent evidence: installed subscription software, not browser B2B workflow SaaS.** Experiment ran 2015-12-01–2016-01-06: 337,724 users in Australia/New Zealand, France, Germany, Japan, UK and US. Users learned their randomized 7/14/30-day duration only after starting through a downloaded app manager, reducing signup selection bias. Held-out conversion: 15.44% at seven days versus 14.63% at 30 (paper reports +0.82 percentage points/+5.59% relative). Personalized lasso policy yielded 6.8% more subscriptions than uniform 30 days; policy evaluation used held-out data, not another live experiment. Two-year follow-up supports retention/revenue analysis. Limits: unnamed near-monopolistic vendor, individual trials, 20.8% educational subscriptions, annual early-exit penalties; organizational imports/procurement/collaboration differ. Supports testing duration against time-to-value, not a universal seven-day prescription. Earlier 2020 working paper is superseded by published paper.

### ChartMogul billing/retention report (2025-05-18)

[Original report](https://chartmogul.com/reports/saas-billing-report/). Aggregated platform data from 2,500+ SaaS companies for 2024; ARPA segments exclude companies under $300K ARR, annual/monthly comparisons exclude single-model businesses. At $250–500 ARPA, reported median NRR is 88% for annual plans versus 76% for monthly. Monthly-to-annual upgrades peak around month two. **Correlation:** buyers choosing annual may already be more committed, and annual contracts alter cancellation opportunity. Do not claim forcing annual terms improves product love or causes the whole retention gap. Practical option: offer annual commitment after value is established, retain transparent monthly entry when useful, measure renewal cohorts and refunds. These companies are not a representative census of tiny new bootstrappers. NRR measures revenue, not the share of people still active.

### Product Hunt official launch guide

[Guide](https://www.producthunt.com/launch), [launch-day guidance](https://www.producthunt.com/launch/launch-day-duties), read 2026-11-07. Platform centers makers, technophiles, product people and early adopters. Daily votes/comments determine visible launch competition. This audience can fit developer tools and horizontal productivity, but is not a representative panel of accountants, procurement buyers or industry operators. Treat launch ranking as attention and feedback, then measure qualified accounts, activation and retained revenue. Official guide provides launch preparation; no guarantee of editorial featuring or business success. Launch-day body was subsequently read; exact featuring guidance appears below. Plausible's narrative separately supports niche communities/content; repeated retellings of its founder post are not independent evidence.

### Shopify: ecosystem-specific quality can aid distribution

[Built for Shopify](https://shopify.dev/docs/apps/launch/built-for-shopify). Program ties ease, safety and performance criteria to badge/highlight, search filtering/ranking and eligibility for personalized recommendations/story pages. Personalized placements are explicitly not guaranteed. Application and prerequisite criteria required; intermediate achievements have limited benefits. Current criteria include app standing/reviews and, where relevant, clean uninstall and checkout-speed impact. This is one ecosystem's distribution mechanism, not a universal web-app award or proof of sales uplift. Product Hunt launch tactics and Shopify merchant discovery address different audiences. Factor platform review/maintenance into the cost of choosing that channel.

### Sentry's marketing tradeoff (2024-01-10)

[Original operating account](https://blog.sentry.io/we-removed-advertising-cookies-heres-what-happened/). Removing nonessential advertising cookies/tracking in July 2023 supported its privacy-conscious developer audience but broke attribution and ad optimization. Reports roughly 30% higher Google search CPC after the change, loss of display conversions and work to salvage attribution; added self-reported acquisition surveys and shifted channel mix. Sequential, multi-change account, not randomized proof of a cookie-removal effect. Plausible supported simpler analytics but did not replace every marketing function. Do not carry forward the article's forecast about Chrome's cookie phaseout as current fact. Larger company's privacy preference and BI staffing are not a universal indie template.

### Sentry follow-up (2026-04-27)

[Two-year follow-up](https://blog.sentry.io/two-years-without-cookies-on-the-site/). Says tracking was not restored; about 70% of growth budget went to awareness, including developer media, sponsorship and large brand investments. Says activated-user growth improved; no controlled attribution of individual channel effects. Useful for recognizing peer conversations, podcasts and delayed discovery that click attribution misses. Do not prescribe its budget split or sports sponsorships to bootstrappers. Inference: preserve small, affordable channel experiments and ask customers how they found you, while testing whether those accounts retain. Existing brand/distribution resources materially change feasible tactics.

For an embedded Shopify product, the current requirements connect design to a concrete channel: qualifying installs/reviews, measured admin Web Vitals, integration and category-specific rules. Treat those as a continuing platform contract, not generic web-app requirements. A standalone SaaS has no equivalent universal app store. [Requirements checked November 7, 2026](https://shopify.dev/docs/apps/launch/built-for-shopify/requirements)

### Marketplace signals: useful discovery, weak financial evidence

Tally’s Product Hunt page records its 2023 launch recognition and displayed 4.9/5 from 99 reviews when inspected. An individual reviewer praises usable professional forms and asks for stronger design, mobile and reporting options. The page also presents an AI-generated summary; that summary was not treated as independent research. These are community signals, not audited active-user or revenue measures. [Tally listing and reviews](https://www.producthunt.com/products/tally/reviews?feed=single&filter=all)

Judge.me’s Shopify listing displayed Built for Shopify, a 2025 Build Award, a free plan and a $15/month paid plan. Visible November 2026 reviews include merchants reporting roughly three and seven years of use and praising hands-on setup/support. This makes support part of the product’s value, while leaving its labor cost unknown. The listing’s aggregate rating and AI-generated merchant summary do not establish causal sales uplift. Treat it as a platform-success reference; current independent ownership and audited profit were not established here. [Listing](https://apps.shopify.com/judgeme)

Balsamiq’s current Confluence offering embeds editable wireframes and clickable prototypes in existing team documents; its marketplace page is a distinct distribution surface from standalone Cloud. This is a useful way to meet an existing workflow, with platform integration and release costs. Current product material also includes AI drafting, so the 2024 reviewer’s missing-AI criticism is historical, not a current gap. Neither a marketplace listing nor vendor customer logos establish a revenue ranking. [Current product](https://balsamiq.com/product/confluence/), [Cloud marketplace listing](https://marketplace.atlassian.com/apps/1213404/balsamiq-for-confluence-cloud-wireframes-prototypes?hosting=cloud&tab=overview)

## Small-company economics and product choices

Amounts below are dated company disclosures unless labelled otherwise. Do not combine ARR, recognized revenue and cash into a ranking.

### Plausible, $1M ARR (2022-06-22)

[Founder retrospective](https://plausible.io/blog/open-source-saas). Four-person, self-funded team reports $1M ARR, over 7,000 subscribers and profitability. It took 324 days to reach $400 MRR after paid launch, then nine months to $10K MRR. Positioning combined simpler analytics, lightweight delivery, privacy and open source. Growth narrative includes a marketing cofounder, niche content, Hacker News, word of mouth and Google Analytics changes; not merely product quality. First general technical viral post had unclear immediate commercial benefit. Low entry pricing reflected competing with free Google Analytics. Distinct value: lower interpretation/setup burden for website owners. Limits: founder-selected retrospective, no audited margin or causal attribution. This establishes historical commercial success, not present revenue or universal superiority over advanced analytics. Guidance: pair a narrow job with a reachable audience; content relevance matters more than raw traffic spikes.

### Tally, $3M ARR (2025-06-10)

[Founder update](https://blog.tally.so/from-2-to-3m-arr-how-we-bootstrapped-tally-with-a-tiny-team/). Reports $258K MRR/$3M ARR, 800K users and eight workers (four full-time, four part-time), without VC. Free features supported growth; premium customization then supported upgrades. ChatGPT became its largest tracked referral source; authors explicitly call proposed explanation a theory. Avoid presenting their GPT rollout speculation as verified platform history. Document-like form creation, generous free use and public form distribution are coherent product/distribution choices. Their success is a useful counterexample to “freemium never works”; it is not a controlled comparison against trials. Revenue is not profit and cumulative users are not active teams. More recent evidence below supersedes the milestone as a current-size claim.

### Tally, $5M ARR and quality (2026-04-15)

[Founder update](https://blog.tally.so/the-road-from-4m-to-5m-arr/). Reports $422K MRR/$5M ARR, 11-person bootstrapped team. Describes feedback button, quarterly NPS (66), office hours, reviews and sharing support/feedback across the whole team. Shipped mobile builder fixes, long-form navigation, conditional-logic improvements, custom-domain setup and answer analytics. This supports a practical quality loop, not a measured claim that these changes caused ARR growth. Particularly useful buyer evidence: Tally left Canny after tracked-user pricing became unaffordable for its million-user audience, choosing UserJot. That is one customer's fit judgment, not proof Canny pricing is universally wrong. Poor pricing metric fit can drive migration even when users like a product. The September disclosure below supplies a later milestone.

### Tally, $6M ARR (2026-09-22)

[Founder update](https://blog.tally.so/6-years-in-6-million-far/). Reports $501K MRR/$6M ARR, 2.5M users, team of ten. Badge-driven signups reportedly upgrade around 1%; AI recommendations became a major channel, which a model change could disrupt. This is channel-specific, not overall conversion. Reports optional AI adoption alongside user resistance; keeping it opt-in preserves existing workflows. Also discloses an August Metabase compromise exposed account emails/hashed passwords; says forms/accounts were not accessed. Removed Metabase and planned certifications by year-end—do not claim certification completed. These are company statements, not independent incident verification. Useful balanced profile: strong distribution/small-team economics plus real operational trust costs. User replies selected by founders do not measure all customer sentiment.

### Fathom Analytics, profitability definition (2022-02-07)

[Founder essay](https://usefathom.com/blog/spending-money). Defines profit after expenses, taxes and livable founder salaries; keeps reserves and spends existing cash. Founders acknowledge other income made the early bootstrap period possible and that outside capital can suit others. Good business evidence because it identifies unpaid labor and starting privilege rather than treating every dollar of revenue as profit. Small analytics scope, privacy positioning and sustainable operations are the relevant lessons; exact current margin/revenue not disclosed here. Do not extrapolate “profitable every month” in a 2022 essay to 2026. Founder philosophy is not audited financial evidence or proof bootstrapping is always better.

### Buttondown: supported simplicity with explicit costs

[About](https://buttondown.com/about), [support](https://buttondown.com/support), [2026-04-20 paywall change](https://marketing.buttondown.com/blog/paywall-changes). Customer-funded newsletter software says it is profitable, avoids excessive free plans and offers export/deletion plus opt-in tracking. Human support generally operates 6am–6pm US Eastern weekdays, not a 24/7 SLA; migration help is available. In April 2026, metadata, transactional-email customization and integrations became paid for new users while existing use was preserved. Company names upkeep, infrastructure, support tickets and documentation as costs. Useful example: a low-complexity product can charge for expert workflows without breaking existing workflows abruptly. Weakness/tradeoff: paid capabilities and finite support availability may not fit low-budget or always-on operations. No independent profit audit or disclosed support hours per account. Creator newsletters straddle B2B/B2C; apply to businesses publishing newsletters, not all enterprise software.

### Balsamiq: durable niche, revenue decline (2025-02-04 report)

[2024 retrospective](https://balsamiq.com/blog/looking-back-2024/). Reports $6.58M revenue, down 6%, alongside retirement of Google Drive product and winding down Desktop to focus on Cloud and Atlassian integrations. Forecast further intentional decline while retaining profitability; forecast is not realized 2025 performance. Editor improvements focused on snapping/alignment, symbols, speed and templates. Admitted customer conversations alone no longer gave sufficient operating clarity; added metrics. Great app meaning: a focused professional workflow and long-term business can matter more than explosive annual growth. Limits: original company began before today's web market; aggregate revenue mixes product lines. Do not call it pure SaaS ARR. Third-party revenue databases disagree substantially; use this original dated report instead.

### Transistor: benefits and existing audience

[2022 company account](https://transistor.fm/giving-more/), [prelaunch podcast transcript](https://saas.transistor.fm/episodes/meet-me-in-chicago/transcript). Company says low overhead/profitability allowed higher download allowances and multiple shows without per-show charges. Historical service promise; not independently audited profit. B2B fit includes brand/network/private organizational podcasts, with creator crossover. Prelaunch transcript reports roughly 1,000 waiting-list contacts and about 1,900 podcast downloads per episode; founders explicitly planned community outreach, media assets, billing/onboarding tests and multiple launch messages. Thus success did not begin with a cold launch into no audience. Transcript provides contemporaneous intentions, not proof those tactics individually caused sales. Product scope and margins still depend on media bandwidth, support and distribution-platform rules.

### Buffer, transparent mature reference (December 2025; posted 2026-01-20)

[Shareholder update](https://buffer.com/shareholders/december-2025). Reports $23.365M ARR, 69,760 paying customers, 198,537 MAU, 74 staff; FY2025 recognized revenue $22.462M and net income $2.5M. December cash receipts were lower partly due to fewer annual subscriptions; cash, revenue and ARR differ. Product work included a whole-team customer-experience week spanning onboarding, billing, support tools and workflows. No isolated causal lift is reported. Larger than an indie team; use as a transparency/accounting reference, not a small-team staffing template. Approximate net margin from reported annual figures is 11.1% (our calculation), far below “software has no costs.” These are company disclosures, not independently audited in this research. The live open dashboard has newer figures; preserve the dated cohort instead of blending them.

### Prezly, actual tool and infrastructure cost disclosure (2023 costs, posted 2024)

[Founder disclosure/discussion](https://www.reddit.com/r/SaaS/comments/1arbtj8/costtools_to_run_saas_with_a_few_mio_arr_link_to/). Identifies a 19-person bootstrapped PR SaaS serving about 600 customers. Itemizes AWS €6,500/month, Uploadcare €2,335.90, Algolia €1,802, Sendgrid €1,268, Plausible €1,300. The Plausible spend serves thousands of customer newsrooms, not merely marketing-site analytics. Labor is excluded. Headline total, rounded subtotal and per-person figures disagree; avoid one precise total. Founder says changing support-seat allocation cut Intercom from €770 to €309 while developers still worked on customer bugs. This shows how commercial licensing affects internal workflows. Context rebuts simplistic “replace CDN with object storage” advice: resizing, conversion and customer domains were part of the workload. Source is self-report, not invoice audit or typical SaaS bill.

## Failures, strain and abandonment

### Baremetrics freemium failure (2015; page updated 2026)

[Founder account](https://baremetrics.com/blog/freemium-saas-implode). Introduced free accounts with limited visible features but no customer-count cap; still imported/processed history. Over 1,000 free accounts arrived in 11 weeks. It reverted to a 14-day full trial and stopped processing after an unpaid trial expired. Resource growth and poor fit harmed the business; author did not reject freemium universally. Distinguish **feature entitlement** from **cost entitlement**: hiding historical charts does not reduce historical ingestion cost. Proposed alternative caps might reduce costs, but author did not test them conclusively. Original article is November 2015 despite its 2026 “updated” label. Pair with Tally, not a blanket anti-free prescription.

### College Conductor (2019-12-18)

[Matt Layman's postmortem](https://www.mattlayman.com/blog/failed-saas-postmortem). Three-year, part-time vertical SaaS for independent education consultants never secured real customers. Founder describes too many unfamiliar tools, package-upgrade busywork, SPA/API duplication and delayed useful delivery. Removing Ember and using familiar Django SSR let him reproduce original features in two weeks after years of prior effort. He explicitly says Ember was wrong **for his familiarity/team**, not intrinsically bad. Wife's interest faded before useful product delivery; he lacked further industry relationships. Valuable failure comparison: niche access and an identified complaint still do not establish distribution, urgency or willingness to switch. Avoid turning his “only upgrade when necessary” lesson into permission to ignore security fixes. Historical evidence supports minimizing learning and integration load, not declaring current libraries abandoned.

### Airplane acquisition and shutdown (2024)

[Former employee account](https://yolken.net/blog/end-of-airplanedev), 2024-03-03; [contemporaneous discussion](https://news.ycombinator.com/item?id=38861271), 2024-01-03. Internal-tool SaaS announced sunset for March 1 after acquisition by Airtable. Employee reports happy customers, slower growth and substantial remaining cash; he cannot know every offer/board consideration. Customers in the discussion describe lack of a comparable migration path and disappointment. Use as **continuity failure**, not proof UX or demand failed. Anonymous speculation about payouts is not reliable evidence. The announcement date does not establish the exact shutdown instant for every workflow. Implication: export must include executable workflows/configuration and dependencies where those constitute value; data CSV alone may not replace a workflow system.

## Pricing, payments and full operating economics

### Stripe published US pricing, read 2026-11-07

[Official pricing](https://stripe.com/pricing). Domestic online cards 2.9% + $0.30; international cards +1.5%, currency conversion +1% where required. Additional products have separate charges. These are US standard-price examples, not Georgian merchant eligibility or universal fees. At $10/month, domestic card fee is $0.59 (5.9%); at $100, $3.20 (3.2%), before other products or taxes (our arithmetic). Merchant-of-record services are separately priced; do not compare processor-only pricing with an all-inclusive MoR price as equivalent service. Refund treatment is documented separately below. Contract/custom rates can differ.

### Paddle published pricing, read 2026-11-07

[Official pricing](https://www.paddle.com/pricing). Standard checkout pricing 5% + $0.50; lists payments, billing, tax compliance, fraud/chargebacks and buyer support, without monthly fee. Custom pricing exists. At $10, listed transaction fee is $1 (10%); at $100, $5.50 (5.5%), our arithmetic. Higher headline price can buy operational work otherwise done by the seller; actual fit still depends on eligible products, countries, contract and support needs. No jurisdiction-specific tax advice established.

### Refund costs

[Stripe refund policy](https://support.stripe.com/questions/understanding-fees-for-refunded-payments) was available as full search extraction; direct open reports unsupported Markdown content type. Standard refunds generally have no new fee except some bank-transfer cases; original processing/Connect/conversion fees are not returned. Pricing schedules can differ. Budget a refund reserve; never count every charged dollar as retained revenue.

### Tally: billing and payments are distinct product surfaces

[Subscription billing guide](https://tally.so/help/billing-and-payment-info). USD/EUR determined by IP; invoice language by supported browser setting. Paid plans have no free trial; free plan is separate. Immediate upgrades apply prorated remaining credit and preserve billing date. Cancellation preserves features through prepaid period; policy excludes unused-time/late-cancellation refunds. These are current vendor terms, not general legal conclusions.

[Form payments guide](https://tally.so/help/payment-forms). Embedded customer payments require Stripe connection; Stripe account/country/FX fees apply with no added Tally fee. Processing occurs on Next or Submit, a potentially consequential interaction before whole-form completion. Provider capabilities do not imply every local method exists in the app integration.

[Public payment feature request](https://tallyforms.userjot.com/board/p/more-payment-options). 2026 requests mention Mollie, Wero, Bizum and other local options. Staff reply on September 25 suggests credit/prepaid-card payment block or redirecting to a separately configured provider. This documents real geographic/workflow friction, not its population frequency. Avoid claiming Stripe availability alone makes forms suitable in every market.

[Stripe currency documentation](https://docs.stripe.com/currencies). Distinguishes card currency, presentment and settlement; methods and account country constrain supported currencies. Customer banks may assess FX/cross-border fees even outside the app's price. Country-specific invoicing, merchant eligibility, payout and local payment requirements need checking for the intended market; no country eligibility inferred from user location.

### Dunning: recover payments without confusing account health

[Stripe retry documentation](https://docs.stripe.com/billing/revenue-recovery/smart-retries), full current body read 2026-11-07. Retry behavior differs by failure and payment method: no automatic retry for missing method, hard decline, India-issued card or disconnected Connect account. Hard-decline scheduled attempt counts can rise without an actual charge. Updating a customer default does not replace a subscription-specific default. Recovery exhaustion can cancel, mark unpaid, leave past-due or pause eligible subscriptions. Thus implement and test payment-update UX, retry ownership, notifications, grace/access policy and final recovery state; do not merely count webhook attempts as money recovered. Country/method exceptions make universal retry recipes unsafe. No numerical recovery uplift inferred from vendor documentation.

[ChartMogul past-due handling](https://help.chartmogul.com/article/303-handling-past-due-subscriptions), updated October 26, 2026, full body read. Default delinquent subscriptions continue contributing to MRR until cancellation arrives; configurable auto-churn changes analytics only, not billing. A 1–90-day threshold is supported. Inference: reported ARR/MRR and churn depend partly on delinquency definitions, so reconcile dashboard figures with cash, failed invoices and service access. A cancellation in analytics is not an actual cancelled contract. Compare revenue cohorts using consistent settings.

### Practical economic model — research synthesis, not benchmark

Measure per account/cohort: subscription revenue net of refunds/credits, less processing/MoR, hosting/storage/egress, third-party API/AI, allocated support labor and incident costs. Then fund product development, acquisition, remaining salaries, taxes and reserves; allocate each cost once. Include migration/onboarding labor in acquisition economics; annual prepayment improves cash timing but creates future service obligations. Split free-user costs from paid-user costs and heavy users from median users. Track retention at the company/account level as well as seats; a removed employee is not necessarily account churn. Keep gross revenue retention separate from net revenue retention, which can conceal lost accounts through expansion. These formulas are analytical guidance; no universal margin target is established.

## Stack choices

**Server-rendered monolith with selective JavaScript.** Fits approvals, CRM, reporting, settings, CRUD and operational workflows whose durable state lives on the server. Turbo intercepts navigation/forms and returns HTML; htmx targets HTML fragments; Stimulus adds local controllers. These tools reduce the need for a parallel client data model. They do not eliminate UI lifecycle, focus, race, history or accessibility work. Network-dependent interactions still need failure handling. Rich editors can be isolated components. [Turbo](https://turbo.hotwired.dev/handbook/introduction), [htmx](https://htmx.org/docs/), [Stimulus](https://stimulus.hotwired.dev/handbook/introduction).

**Rich client when the task warrants it.** Diagramming, spreadsheet-like manipulation, complex local drafts and collaborative editing justify more client state. React, Vue and Svelte offer component ecosystems; route/data frameworks integrate loading, navigation, pending/error states and code splitting. React's recommendation to use a framework is vendor guidance, not evidence every B2B app needs React. Next.js supports Node/Docker self-hosting; static export omits server features. [React installation](https://react.dev/learn/installation), [CRA rationale](https://react.dev/blog/2025/02/14/sunsetting-create-react-app), [Next deployment](https://nextjs.org/docs/app/getting-started/deploying), [React Router modes](https://reactrouter.com/start/modes).

**Server-driven reactive UI.** Phoenix LiveView first renders HTML, then maintains a connection and sends diffs from server processes. Laravel Livewire keeps component work in PHP. Both offer richer interactions without writing a separate frontend API; latency, reconnection and server-side per-session state still matter. Inertia combines server routing/controllers with React/Vue/Svelte views. It is a useful middle path, not HTML-only delivery. [LiveView](https://hexdocs.pm/phoenix_live_view/welcome.html), [Livewire](https://livewire.laravel.com/), [Inertia](https://inertiajs.com/).

**Data and jobs.** Choose storage against concurrency, recovery and deployment shape. SQLite's owning guidance distinguishes local simplicity from shared server databases; PostgreSQL offers a separate multi-client SQL service. A transactional DB queue can commit the domain write and job together; River documents that design for Postgres/SQLite. An external queue adds a service and a boundary between commits. Neither design makes email delivery exactly once. [SQLite fit](https://sqlite.org/whentouse.html), [PostgreSQL](https://www.postgresql.org/about/), [River](https://riverqueue.com/).

**Prefer a coherent small set.** Start with browser HTML, forms, CSS, `fetch`, `Intl` and native animation. Add a table engine when sorting/selection/virtualization justify it; add a document engine when rich content is the product. A custom table remains responsible for semantics and keyboard interaction; a CRDT remains responsible for transport/auth/persistence integration. [Fetch](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API), [Intl](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl), [Web Animations](https://developer.mozilla.org/en-US/docs/Web/API/Web_Animations_API), [TanStack Table](https://github.com/TanStack/table), [Yjs](https://github.com/yjs/yjs).

## Builder accounts: stack fit and ownership

These are builders' own accounts, independent of framework marketing. They establish actual use and reported tradeoffs, not controlled comparisons or proof that a stack caused business success.

| Builder / evidence | What to carry into an indie recipe |
|---|---|
| **Buttondown**, current [stack](https://buttondown.com/stack), Justin Duke's [Django account](https://marketing.buttondown.com/blog/what-i-love-about-django), 2026-08-05 | Django backend, Vue application, Next.js marketing/docs, Postgres, Tiptap, CodeMirror, Tailwind and Vite demonstrate separate choices for separate surfaces. Duke values middleware for tenant routing, response headers and log context; light model inheritance provides IDs, timestamps and optional change tracking. Actions live beside models as one verb per module. Inference: familiar backend conventions can coexist with a rich client; avoid requiring one frontend architecture across the app and marketing site. Stack-page expenses include donations, so a Django line is not a license fee. |
| **Plausible**, Uku Taht's [technology choices](https://plausible.io/blog/technology-choices), 2019-01-29; current [owning README](https://github.com/plausible/analytics/blob/master/README.md) | Founder chose Elixir/Phoenix from prior commercial experience and Postgres as a mature default, with future analytics storage left open. Current code documents Elixir/Phoenix, Postgres for general data, ClickHouse for analytics, React/Tailwind frontend. Inference: start with known tools; add a specialized database for a demonstrated workload. The 2019 plan is historical evidence, not the current full stack. |
| **37signals**, [ONCE app-server discussion](https://dev.37signals.com/once-app-server/), 2026-04-17; [Campfire deployment docs](https://github.com/basecamp/once-campfire/blob/main/docs/self-hosting.md) | Builder distinguishes bespoke SaaS deployments from ONCE's one-company, one-machine, one-directory scope. Campfire bundles app/jobs/cache/files/SSL in a container and stores persistent data under a mounted directory. SQLite backup requires the documented snapshot step, not copying a live DB. Inference: single-tenant distribution can remove infrastructure, but does not establish equivalent economics for shared multi-tenant SaaS. Existing team expertise limits transfer to a first-time operator. |
| **Linear**, [delta-sync read-path account](https://linear.app/now/rebuilding-delta-sync-read-path), 2026-08-18 | Local databases eliminate request latency for common interactions; returning clients need permission- and subscription-filtered changes. Large workspaces exposed expensive Postgres intersections and variable catch-up latency. A dedicated serving index moved filtering to turbopuffer while action payloads stayed in Postgres. Inference: local-first UX brings a sync and authorization system to operate. This is a larger-scale reference, not an indie baseline or evidence that all SaaS needs another database. |

Shared inference: server-rendered CRUD remains a good starting scope when navigation/forms dominate. Rich client state earns its cost for editing, manipulation or interaction that must proceed without round trips. Neither claim is a measured SSR-versus-SPA productivity result; the builder accounts show feasible combinations and workload-specific reasons.

## Integration costs that catalogs hide

- Copied components need an owner for future fixes; a headless table needs actual markup, semantics and interaction design. Buying a grid may cost less than reproducing keyboard selection, Excel export, pinning and aggregation. License gates should enter requirements before implementation. [shadcn/ui](https://ui.shadcn.com/docs), [AG Grid](https://www.ag-grid.com/javascript-data-grid/community-vs-enterprise/).
- A rich editor changes the stored-data model. Budget schema evolution, importing old data, sanitation, paste, mobile composition, cursor restoration, undo and export. The engine choice constrains these jobs; a toolbar screenshot cannot establish correctness. [ProseMirror](https://github.com/ProseMirror/prosemirror), [Slate](https://github.com/ianstormtaylor/slate), [DOMPurify](https://github.com/cure53/DOMPurify).
- Cache/state libraries solve different jobs. Query caches remote data; a local store owns transient UI state; CRDTs merge concurrent document changes. Combining them without explicit ownership creates duplicate state, stale permissions and hard-to-reproduce reload behavior. This is synthesis from their documented scope, not measured comparative defect data. [Query](https://github.com/TanStack/query), [Zustand](https://github.com/pmndrs/zustand), [Yjs](https://github.com/yjs/yjs).
- Build and runtime compatibility have separate floors: Vite dev tooling, production syntax, CSS features, server Node and component peer dependencies. Recharts explicitly requires matching React/`react-is`; Tailwind CSS floor is not fixed by Babel. [Vite](https://vite.dev/guide/), [Tailwind](https://tailwindcss.com/docs/compatibility), [Recharts](https://github.com/recharts/recharts).
- Auth packages do not decide who may see each tenant's data; search indexes and caches must preserve the same authorization boundary. Authorization engines also need a domain model, negative tests and revocation behavior. [Casbin](https://github.com/casbin/casbin), [Better Auth](https://github.com/better-auth/better-auth), [Keycloak](https://github.com/keycloak/keycloak).

## Commercial component boundaries

- **MUI X:** Community packages use MIT. Commercial Pro adds examples including multi-filter/sort, column resizing/pinning, range pickers and tree reordering; Premium adds row grouping and Excel export. Select the package edition before promising these features. This is the owner's current division, not a license review of a purchased contract. [Owner licensing](https://mui.com/x/introduction/licensing/).
- **Tiptap:** Open-source core can be self-hosted and extended. Platform plans add commercial infrastructure/extensions: Start lists inline AI and simple DOCX import/export; Team adds Pages and webhook/API access. Managed document infrastructure on-premises is Enterprise. Advanced managed collaboration should not be inferred from core's OSS license; distinguish an owned collaboration backend from buying the platform. Expired subscriptions/overages can restrict paid cloud features. [Owner pricing and FAQ](https://tiptap.dev/pricing).
- **AG Grid:** Community/Enterprise boundaries already sit beside its catalog entry; do not treat enterprise grouping/export features as available from an arbitrary free grid package. [Owner comparison](https://www.ag-grid.com/javascript-data-grid/community-vs-enterprise/).

## Other familiar backend ecosystems

ASP.NET Core and Spring Boot are viable alternatives for founders already fluent in C# or Java/Kotlin. ASP.NET Core supplies HTTP serving, dependency injection, auth, Minimal APIs, Blazor and SignalR. Spring Boot supplies embedded serving, starter dependencies, auto-configuration, health checks and metrics. Familiarity can outweigh switching to a fashionable indie stack; this is a scope alternative, not a request to change confirmed scaffold choices. These ecosystems received a capability check, not a package-by-package dependency audit. [Microsoft overview](https://learn.microsoft.com/en-us/aspnet/core/overview?view=aspnetcore-10.0), [Spring Boot](https://spring.io/projects/spring-boot/).

## Named ecosystem catalog

This is a selection map, not an install list or popularity ranking. Sources establish purpose and documented constraints; vendor speed/accessibility claims are not independent measurements. A live README is not proof of responsive maintenance. Rows name explicit maturity/status evidence where available; a per-release dependency audit remains necessary for a chosen stack. Adoption evidence appears only where attributed. Alternatives are other rows in the same group unless named. Inspect the exact version's license and transitive dependencies before shipping; special commercial/copyleft terms are called out below.

**Evidence labels for every row:** unless stronger evidence is stated in that row or the linked status/builders sections, read it as **docs only; adoption unmeasured**. “Docs only” means capabilities were checked, not release cadence or response quality. Builder-confirmed use, owner-listed customers and measured adoption are different evidence. Platform ownership alone establishes none of them. Public release activity cannot establish maintainability inside an unbuilt app or future security response. [Builder accounts](#builder-accounts-stack-fit-and-ownership) and [status checks](#shortlist-maintenance-and-security-snapshot) provide the stronger evidence available here.

### Languages, server frameworks, delivery

| # | Tool / source | Fit; alternative; cost or limit |
|---|---|---|
| 1 | [Go `net/http`](https://pkg.go.dev/net/http) | HTTP clients/server in the standard library; fit explicit server architecture. Framework routing/middleware can add convenience, but are not prerequisites. Runtime-owned API rather than a separate service. |
| 2 | [Go `html/template`](https://pkg.go.dev/html/template) | Contextual HTML escaping in the standard library. Useful minimal rendering; component ergonomics may require other tooling. Use instead of `text/template` for HTML; trusted HTML types bypass protections. |
| 3 | [Rails](https://github.com/rails/rails) | Ruby MVC, Active Record and HTML templates in one framework family. Fit integrated business apps; custom Go offers more explicit assembly. MIT; team must accept Rails conventions. |
| 4 | [Django](https://docs.djangoproject.com/en/5.2/intro/overview/) | Python database models, migrations, views/templates and generated administration. Good operational apps; admin is not a finished customer product. Read 5.2 overview, not a claim 5.2 is latest. |
| 5 | [Laravel](https://github.com/laravel/framework) | PHP framework includes routing, sessions, migrations, queues and broadcasting. Fit integrated monoliths; MIT. Runtime/ecosystem expertise matters more than a generic speed ranking. |
| 6 | [Phoenix / LiveView](https://hexdocs.pm/phoenix_live_view/welcome.html) | Elixir processes and server-rendered reactive diffs. Fit real-time operational screens; persistent connection and server process lifecycle need testing. Docs observed v1.2.13; PHP Livewire is a different ecosystem. |
| 7 | [FastAPI](https://github.com/fastapi/fastapi) | Python type-hint-based APIs/OpenAPI; useful beside Python analytics. It does not supply a whole customer UI. README productivity percentages are internal estimates, not independent evidence. |
| 8 | [Express](https://github.com/expressjs/express) | Minimal Node HTTP framework, routing and middleware. Fit teams wanting assembly freedom; more integration choices than Rails/Django. MIT. Node 18 minimum in README is not a safe production-support recommendation. |
| 9 | [Fastify](https://github.com/fastify/fastify) | Node framework emphasizing low overhead and plugins. Alternative to Express; validate real workload and plugin compatibility. Main README describes v6; v5 has its own branch. MIT. |
| 10 | [Hono](https://github.com/honojs/hono) | Web-standard JS server APIs across Node, Workers, Deno and Bun. Good portability candidate; provider services still differ. MIT; multi-runtime claim does not prove every dependency is portable. |
| 11 | [Turbo](https://turbo.hotwired.dev/handbook/introduction) | Persistent-page navigation, frames and HTML streams. Fit server-rendered apps; htmx is an alternative with explicit fragment attributes. Review persistent DOM lifecycle and cache behavior. |
| 12 | [Stimulus](https://stimulus.hotwired.dev/handbook/introduction) | Small controllers attached to existing HTML. Fit local widgets on SSR pages; Alpine offers template expressions. Does not replace an editor or global data model. |
| 13 | [htmx](https://htmx.org/docs/) | Dependency-free HTML attributes drive requests/swaps; usable without a build step. Fit incremental interactions; own server rendering and response/history semantics. |
| 14 | [Alpine.js](https://github.com/alpinejs/alpine) | Local reactive behavior in markup; fits SSR widgets. Repository includes focus, morph and separate CSP-safe build. Select the CSP build when its constraints apply; do not weaken CSP automatically. |
| 15 | [Livewire](https://livewire.laravel.com/) | Laravel/PHP reactive components; useful when server team wants one language. Contrast Inertia for richer client components; network round trips still shape interaction quality. |
| 16 | [Inertia](https://inertiajs.com/) | Server routes/controllers plus React/Vue/Svelte pages. Fit a modern monolith without a separately designed page API. Browser components and build tooling remain. |
| 17 | [React](https://react.dev/learn/installation) | Incrementally adoptable component library; strong rich-widget fit. React docs support adding it to existing pages, not only whole-app replacement. Routing and data policy need separate choices. |
| 18 | [Vue 3](https://github.com/vuejs/core) | Component/reactivity framework; Nuxt adds application structure. MIT, sponsor-backed project. Use current Vue, not EOL Vue 2; migration affects ecosystem components. |
| 19 | [Svelte](https://github.com/sveltejs/svelte) | Compiler translates components into DOM-updating JavaScript. MIT; SvelteKit supplies the app framework. Different authoring/compiler model, not proof of universally smaller apps. |
| 20 | [Next.js](https://nextjs.org/docs/app/getting-started/deploying) | React full-stack deployment to Node, Docker, static export or adapters. Node/Docker support full features; static export has limits. Hosting on Vercel is optional. |
| 21 | [React Router](https://reactrouter.com/start/modes) | Declarative, data and framework modes let teams choose integration depth. Useful routing/history/pending-state foundation; avoid implementing routes only in component state. |
| 22 | [TanStack Router / Start](https://github.com/TanStack/router) | Typed routes/search parameters and data-aware navigation; Start adds SSR/server functions. Fit TypeScript-heavy clients; additional types/build conventions may be unnecessary for SSR forms. |
| 23 | [SvelteKit](https://svelte.dev/docs/kit/introduction) | Routing, loading, form actions and deployment adapters around Svelte. Fit full Svelte products; adapters and deployment capabilities require explicit selection. |
| 24 | [Nuxt](https://github.com/nuxt/nuxt) | Full-stack Vue framework, rendering and hosting integrations. MIT; fit Vue teams. Modules widen capabilities and dependency surface. README inspected after docs access failed. |
| 25 | [Astro](https://github.com/withastro/astro) | Website framework with lightweight output. Good candidate for marketing/docs alongside an app; evaluate authenticated workflow needs before making it the application center. MIT. |

### Build, packaging, code quality

| # | Tool / source | Fit; alternative; cost or limit |
|---|---|---|
| 26 | [TypeScript](https://github.com/microsoft/TypeScript) | Optional static types compiled to JS; helps large shared client contracts. Plain JS remains viable; typing does not validate network input or replace tests. |
| 27 | [Node.js LTS](https://nodejs.org/en/about/previous-releases) | JS server/build runtime. Owning policy recommends Active/Maintenance LTS for production. On read date 22/24/26 were LTS; 20 and earlier EOL. Browser JS target is a separate decision. |
| 28 | [Vite](https://vite.dev/guide/) | Dev server and production asset build; current guide uses Rolldown. Fit component apps or backend asset integration; esbuild can suit a smaller custom build. Default production target is version-specific Baseline Widely Available. |
| 29 | [esbuild](https://github.com/evanw/esbuild) | JS/TS/JSX/CSS bundling, minification and Go/JS/CLI APIs. Fit small explicit pipelines; does not provide routing or application data policy. Measure your build, not README speed slogans. |
| 30 | [npm](https://github.com/npm/cli) | Node-bundled package manager; simplest default for many JS teams. Use supported Node and a lockfile. Alternative pnpm changes dependency layout, not application behavior. |
| 31 | [pnpm](https://github.com/pnpm/pnpm) | Shared content-addressed package store, strict dependency access and workspaces. README cites Microsoft Rush usage; not market-share data. MIT except the separate `pnpr` directory's PolyForm Shield terms. |
| 32 | [ESLint](https://github.com/eslint/eslint) | Pluggable JS lint rules; good when framework/plugin-specific checks matter. Node-version requirements change; rules/plugins need upgrades. MIT; formatter remains a separate concern. |
| 33 | [Prettier](https://github.com/prettier/prettier) | Consistent multi-language code formatting. Fit reducing formatting debates; does not check business correctness. Alternative Biome combines formatting/linting. |
| 34 | [Biome](https://biomejs.dev/) | Combined formatter/linter toolchain. Fit fewer tools where required syntax/rules are supported; inspect documented limitations before replacing ESLint/Prettier. Vendor compatibility/performance numbers are claims. |

### UI, tables, forms, client state

| # | Tool / source | Fit; alternative; cost or limit |
|---|---|---|
| 35 | [Tailwind CSS](https://tailwindcss.com/docs/compatibility) | Utility-based styling vocabulary; v4 requires Chrome 111, Safari 16.4, Firefox 128 for core functionality. Newer utilities can require more. Not designed to combine with Sass/Less/Stylus. |
| 36 | [Bootstrap](https://getbootstrap.com/docs/5.3/getting-started/introduction/) | Prebuilt CSS/components with documented RTL, color modes and JS. Fit conventional admin UI; custom styling avoids generic-looking output. Read v5.3 docs; accessibility still depends on composition/content. |
| 37 | [Material UI](https://mui.com/material-ui/getting-started/) | Prebuilt React components implementing Material Design 2, despite current library version. Fit consistent controls quickly; not an automatic Material 3 implementation. Advanced MUI X licensing is separate. |
| 38 | [Radix Primitives](https://www.radix-ui.com/primitives/docs/overview/introduction) | Low-level accessible React behaviors for custom design systems. Fit branded controls; styling/composition/testing still yours. Alternative React Aria emphasizes adaptive interaction and internationalization. |
| 39 | [React Aria](https://react-aria.adobe.com/) | Unstyled React components with accessibility, adaptive behavior and locale support. Good complex controls; not an app-level accessibility guarantee. Adobe-owned implementation documentation inspected. |
| 40 | [shadcn/ui](https://ui.shadcn.com/docs) | Distributes editable component code. Fit app-owned design systems; ownership also means tracking local changes and upstream fixes. A component distribution approach rather than a frozen theme package. |
| 41 | [Polaris Web Components](https://shopify.dev/docs/api/app-home/latest/web-components) | Shopify-admin-native components; fit embedded Shopify apps. Not a universal independent SaaS design kit. Use current web-components route instead of archived Polaris React. |
| 42 | [TanStack Table](https://github.com/TanStack/table) | Headless, framework-agnostic table state, sorting/filtering/grouping/selection. Fit custom tables; markup/styles/keyboard behavior remain yours. Current README lists v9 adapters; old React-only descriptions are stale. |
| 43 | [AG Grid](https://www.ag-grid.com/javascript-data-grid/community-vs-enterprise/) | Complete JS/React/Vue/Angular grid. Community is free for production; Enterprise license covers advanced server-side rows, pivoting, Excel export and other features. Evaluate paid features before designing around them. |
| 44 | [TanStack Virtual](https://github.com/TanStack/virtual) | Headless vertical/horizontal/grid virtualization. Fit measured large-render bottlenecks; keyboard focus, find-in-page and accessible row representation need product tests. Pagination may be enough. |
| 45 | [React Hook Form](https://github.com/react-hook-form/react-hook-form) | React form state and validation integration; uses native form validation concepts and schema resolvers. Useful complex forms; simple server forms need no equivalent client dependency. |
| 46 | [Zod](https://zod.dev/) | Runtime schemas with TS inference and JS support. Zod 4 is stable; docs test TS 5.5+ with strict mode. Good network/form boundaries; does not enforce permissions or DB invariants. |
| 47 | [Valibot](https://valibot.dev/guides/introduction/) | Modular runtime schemas, no dependencies, JS environments. Alternative to Zod when bundle composition matters; compare needed ecosystem adapters and schema ergonomics. |
| 48 | [TanStack Query](https://github.com/TanStack/query) | Client server-state fetching, caching, mutations and invalidation. Fit rich clients; set ownership and staleness deliberately. Duplicating router and query caches without a policy adds complexity. |
| 49 | [Zustand](https://github.com/pmndrs/zustand) | Small React-oriented shared client store, immutable updates. Fit state shared beyond local components; not an authoritative server database or permission boundary. |
| 50 | [Redux Toolkit / RTK Query](https://redux.js.org/toolkit/introduction/getting-started) | Official recommended way to write Redux; structured state plus optional fetching/cache. Fit substantial shared workflows; local state or Query can be simpler. Avoid hand-building old Redux boilerplate by default. |
| 51 | [Floating UI](https://github.com/floating-ui/floating-ui) | Collision-aware positioning for tooltips/popovers, plus React interaction helpers. Fit menus in scroll containers; native popover/anchor positioning may suffice on supported browsers. Popper's successor, not evidence Popper instantly breaks. |
| 52 | [Pragmatic drag and drop](https://github.com/atlassian/pragmatic-drag-and-drop) | Framework-neutral low-level browser drag/drop. Atlassian says it powers Trello/Jira/Confluence. Core is unopinionated about visual language/accessibility: add alternatives and announcements. |
| 53 | [dnd-kit](https://github.com/clauderic/dnd-kit) | Current framework-agnostic core, DOM implementation, framework adapters and pointer/touch/keyboard sensors. Fit sortable/custom drag interactions; check package generation because older tutorials describe React-only APIs. MIT. |

### Editors, collaboration, visualization, assets

| # | Tool / source | Fit; alternative; cost or limit |
|---|---|---|
| 54 | [ProseMirror](https://github.com/ProseMirror/prosemirror) | Rich semantic editor with schemas and collaborative-editing support. Fit a controlled document model; substantial toolbar/paste/schema work. MIT. Repository moved to code.haverbeke.berlin; a quiet GitHub mirror is not abandonment. |
| 55 | [Tiptap](https://tiptap.dev/docs/editor/getting-started/overview) | Editor framework and extension ecosystem, with adapters beyond React. Fit faster ProseMirror-based product integration; commercial extensions/services and collaboration costs need exact selection. |
| 56 | [Lexical](https://lexical.dev/) | Lean editor core and plugins; modular lists/links/tables. Fit custom editor UX; toolbar and product features are not supplied by the core. Official replacement direction from archived Draft.js. |
| 57 | [Slate](https://github.com/ianstormtaylor/slate) | Highly customizable React editor model. README explicitly says beta, contributor-driven, APIs may change and advanced bugs may need your contribution. Viable for deep customization; risky for a team wanting turnkey support. |
| 58 | [CodeMirror](https://github.com/codemirror/dev) | Modular code editor packages. Fit query/code/rule editors; not a rich-document editor. Development repo moved to code.haverbeke.berlin; install individual npm packages, not the development workspace. |
| 59 | [Yjs](https://github.com/yjs/yjs) | CRDT shared types, editor bindings, snapshots and offline capability. MIT; transport-independent. README lists Linear, GitBook and others as users; these are project-listed examples, not independent adoption measurement. |
| 60 | [Automerge](https://github.com/automerge/automerge) | CRDTs, compression and sync protocol; Rust core with JS/Wasm. README identifies stable JS package. Fit local-first shared documents; still design auth, storage, document lifecycle and semantic conflicts. |
| 61 | [Chart.js](https://github.com/chartjs/Chart.js) | Common chart forms; MIT. Fit ordinary dashboards; provide readable summaries/data tables. D3 gives deeper control at greater implementation cost. README points to v4 docs. |
| 62 | [Apache ECharts](https://github.com/apache/echarts) | Broad interactive visualization library. Fit analytic dashboards with many chart types; configuration and bundle budget need discipline. Verify chart accessibility and actual dataset performance. |
| 63 | [D3](https://github.com/d3/d3) | Low-level web-standard visualization primitives. Fit distinctive domain visualizations; more work than a prebuilt chart library. Project describes decade-plus history; no market-share claim made. |
| 64 | [Recharts](https://github.com/recharts/recharts) | Declarative React/SVG chart components built with D3. MIT; fit React dashboards. README requires `react-is` version to match React; main and release branches differ. |
| 65 | [deck.gl](https://github.com/visgl/deck.gl) | GPU layers for large geospatial/data visualization. Fit data volume and visual complexity beyond ordinary charts; GPU/browser/resource requirements matter. Plain JS and React integration available. |
| 66 | [MapLibre GL JS](https://github.com/maplibre/maplibre-gl-js) | GPU vector maps; BSD-3-Clause. Fit independent map rendering; tiles/geocoding/data licenses and hosting are separate. Fork originated before Mapbox GL JS licensing changed. |
| 67 | [Leaflet](https://github.com/Leaflet/Leaflet) | Interactive maps with plugins; fit straightforward location UI. Alternative to GPU-heavy mapping when needs are simpler. Audit plugin compatibility separately. |
| 68 | [React Flow / Svelte Flow](https://github.com/xyflow/xyflow) | Node/edge workflow canvases. MIT core with optional Pro support/examples. Fit automation builders; domain validation, execution and accessible alternatives are product work. |
| 69 | [Lucide](https://github.com/lucide-icons/lucide) | SVG icons with framework packages; ISC indicated in repository. Fit one coherent icon vocabulary. No brand logos; label unfamiliar icons instead of assuming recognition. |
| 70 | [Motion](https://github.com/motiondivision/motion) | JS/React/Vue gestures, springs and layout transitions. Framer Motion is now Motion; `motion/react` is documented route. Native CSS/Web Animations can suffice for simple transitions; inspect paid extras separately. |
| 71 | [Uppy](https://github.com/transloadit/uppy) | Modular uploads, previews, remote sources and Tus integration. MIT. Fit substantial uploads; server validation/durable completion remain necessary. Avoid shipping the all-plugin bundle when using a subset. |
| 72 | [Papa Parse](https://github.com/PapaParse/PapaParse) | Browser CSV parsing/serialization, streaming and workers; no dependencies. Fit import previews; server validation and spreadsheet-formula handling are separate requirements. Do not treat README fastest claims as benchmarks. |
| 73 | [PDF.js](https://github.com/mozilla/pdf.js) | Mozilla-supported HTML-based PDF rendering. Fit embedded document inspection; choose modern/legacy build against target browsers. Lazy loading and patching matter for a large file parser. |
| 74 | [sharp](https://github.com/lovell/sharp) | Node-API image resize/conversion via libvips; Apache-2.0. Fit upload derivatives. Native runtime/architecture support differs from pure JS; validate deployment images and memory use. |

### Dates, locale, network, security, browser storage

| # | Tool / source | Fit; alternative; cost or limit |
|---|---|---|
| 75 | [`fetch`](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API) | Browser HTTP without a library. Good default for modest requests; HTTP errors still resolve the promise, so check status. Add policy for abort/retry/auth deliberately. |
| 76 | [`Intl`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl) | Built-in number/date formatting, comparison and locale-sensitive functions. Often enough without locale bundles; support differs by individual constructor. Translation catalogs remain separate. |
| 77 | [date-fns](https://github.com/date-fns/date-fns) | Modular immutable operations on native dates; v4 time-zone support. MIT. Fit function-oriented date work; preserve distinctions between calendar dates and instants. |
| 78 | [Luxon](https://github.com/moment/luxon) | Immutable DateTime/Duration/Interval, native zones/Intl. MIT. Fit explicit zone-heavy scheduling; uses runtime locale/time-zone data rather than bundled data files. |
| 79 | [i18next](https://github.com/i18next/i18next) | Translation loading, plurals, context and detection. Fit multi-language apps across frameworks. Current README says Node 22+ and ES2020 browsers; pin exact version for older targets. |
| 80 | [FormatJS](https://github.com/formatjs/formatjs) | Internationalization ecosystem with message formatting, framework support, Intl polyfills and tooling. Fit structured translation workflows; inspect each package's platform/license/version rather than treating monorepo as one dependency. |
| 81 | [DOMPurify](https://github.com/cure53/DOMPurify) | HTML/MathML/SVG sanitizer. MPL-2.0 OR Apache-2.0. Fit rendering permitted untrusted markup; server-side DOM implementation and later mutations can change safety. Modern branch does nothing on unsupported legacy browsers. |
| 82 | [Dexie.js](https://github.com/dexie/Dexie.js) | IndexedDB wrapper for browser records and migrations. Fit substantial local cache/drafts. Dexie Cloud adds sync/auth separately; local IndexedDB itself is not a durable backup. Deprecated older sync plugins below. |
| 83 | [Better Auth](https://github.com/better-auth/better-auth) | TS auth framework with plugins for capabilities such as 2FA/multitenancy. MIT. Fit owning auth integration; validate required passkey/SSO/recovery flows and security updates. Broad README claims are not a security audit. |
| 84 | [openid-client](https://github.com/panva/openid-client) | OAuth/OIDC flows for JS runtimes. Fit standards-based identity integration; not an entire user-management system. Verify issuer configuration and flow requirements. |
| 85 | [Keycloak](https://github.com/keycloak/keycloak) | Self-hosted identity/access management, federation and administration. Apache-2.0. Fit enterprise identity needs; additional service, upgrades and operational responsibility. |
| 86 | [Apache Casbin](https://github.com/casbin/casbin) | Authorization policy engine, originally Go with language implementations. Apache-2.0. Useful complex policy models; tenant filtering and application invariants still require enforcement/tests. |

### Data, jobs, search

| # | Tool / source | Fit; alternative; cost or limit |
|---|---|---|
| 87 | [PostgreSQL](https://www.postgresql.org/about/) | Multi-client relational DB with SQL and long project history. Fit shared business records and transactions; backup/restore/schema operations remain your responsibility. |
| 88 | [SQLite](https://sqlite.org/whentouse.html) | Embedded DB avoids separate server operations. Fit local/single-host architectures where write concurrency is compatible; client/server DB better for many machines directly sharing data. Avoid universal scale slogans. |
| 89 | [sqlc](https://github.com/sqlc-dev/sqlc) | Generates typed query code from SQL, with language plugins. Fit explicit SQL plus compile-time interfaces; generation is a build step and supported SQL differs by backend. Optional ecosystem candidate, not scaffold policy. |
| 90 | [Goose](https://github.com/pressly/goose) | SQL/Go schema migrations as library or CLI; MIT. Fit Go deployment tooling; supports multiple DBs and embedded migrations. A down migration is not proof of safe data rollback. |
| 91 | [Prisma](https://github.com/prisma/prisma) | TS ORM/tooling; Apache-2.0. Current README describes Prisma 8 as release candidate and 7 supported for 18 months after 8 final. Assess current feature gaps/migration cost; do not call the RC stable. |
| 92 | [Drizzle](https://github.com/drizzle-team/drizzle-orm) | TS/JS SQL-oriented ORM with Postgres/MySQL/SQLite support. Fit typed app queries; validate driver, migration and hosting combination instead of relying on broad portability claims. |
| 93 | [River](https://riverqueue.com/) | Jobs transactionally enqueued in Postgres/SQLite; current docs list multiple languages. Fit reducing external queue services. Pro adds workflows/sequences/concurrency features; evaluate edition boundaries. |
| 94 | [BullMQ](https://github.com/taskforcesh/bullmq) | Redis-backed jobs; Node/Bun plus documented other-language implementations. Fit existing Redis infrastructure; worker idempotence and Redis operations still required. Paid frontend/Pro are separate. |
| 95 | [Sidekiq](https://github.com/sidekiq/sidekiq) | Ruby threaded jobs; current requirements include Redis/Valkey alternatives. Core LGPLv3; Pro/Enterprise commercial licenses. Good Ruby fit, not a free interchangeable universal queue. |
| 96 | [Celery](https://github.com/celery/celery) | Python distributed task framework with broker ecosystem. Fit existing Python workers; larger operational surface than an embedded/simple DB queue. Broker choice affects behavior. |
| 97 | [Valkey](https://valkey.io/) | BSD key/value service under Linux Foundation. Fit caching/queues with permissive licensing preference; verify client/queue compatibility. Current release visible, not an independent performance test. |
| 98 | [Redis](https://github.com/redis/redis) | Cache/data structures/search. License depends on version: ≤7.2 BSD; 8+ offers RSALv2/SSPLv1/AGPLv3 choice. Some optional optimizations have incompatible terms; do not describe current Redis as BSD-only. |
| 99 | [Meilisearch](https://www.meilisearch.com/docs/getting_started/overview) | Search/index service; managed/self-host options. [Repository license](https://github.com/meilisearch/meilisearch/blob/main/LICENSE) splits MIT and BUSL-1.1 Enterprise parts. Adds index synchronization and permission-filtering work. |
| 100 | [Typesense](https://github.com/typesense/typesense) | Typo-tolerant search engine. Server GPL, client libraries Apache per owning README; hosted service optional. Fit search-as-you-type; DB full-text may avoid another service for simpler needs. |

### Testing, diagnostics, delivery

| # | Tool / source | Fit; alternative; cost or limit |
|---|---|---|
| 101 | [Playwright](https://github.com/microsoft/playwright) | Browser tests across Chromium/Firefox/WebKit; auto-waiting and isolation. Fit real workflow/recovery testing; WebKit coverage is not identical to all shipped Safari devices. |
| 102 | [Vitest](https://github.com/vitest-dev/vitest) | Vite-integrated tests, mocks, coverage and browser mode. MIT. Fit component/JS logic tests; DOM simulation is not browser reliability evidence. |
| 103 | [DOM Testing Library](https://github.com/testing-library/dom-testing-library) | Queries/tests aligned with user-visible DOM. MIT. Good semantic interaction tests; combine with browser tests for layout/native behavior. |
| 104 | [axe-core](https://github.com/dequelabs/axe-core) | Automated accessibility checks; useful CI floor. Owner estimates average 57% automatic WCAG issue detection, not 100% compliance. Manual keyboard/screen-reader testing remains. |
| 105 | [MSW](https://github.com/mswjs/msw) | Network-layer request mocking, including delays/errors. Fit deterministic UI failure scenarios; integration tests must still exercise the real backend. |
| 106 | [k6](https://github.com/grafana/k6) | Scripted load/protocol/browser testing with metrics output. AGPL-3.0 core; Cloud optional. Fit concurrency/tail latency tests, not a substitute for realistic traffic/data models. |
| 107 | [Storybook](https://github.com/storybookjs/storybook) | Isolated component states/documentation/testing. Useful shared component systems; maintenance cost may exceed value for tiny custom SSR pages. Source's “thousands of teams” is owner-reported. |
| 108 | [Sentry JS SDKs](https://github.com/getsentry/sentry-javascript) | Browser/server/framework diagnostic SDKs. Fit correlating errors and releases; backend service terms/costs differ from SDK license. Review data scrubbing and sampling. |
| 109 | [OpenTelemetry JS](https://github.com/open-telemetry/opentelemetry-js) | Traces/metrics/log instrumentation framework, Apache-2.0. Package-version matrix and ESM/CommonJS integration matter. Candidate for general ecosystem only; does not override deferred scaffold observability choices. |
| 110 | [Prometheus Go client](https://github.com/prometheus/client_golang) | Go metrics instrumentation and HTTP API client. Supports two most recent Go major releases; HTTP API client is experimental despite stable instrumentation APIs. Not a mandate for Prometheus storage. |
| 111 | [GoReleaser](https://github.com/goreleaser/goreleaser) | Go release packaging/CI automation; MIT core. Fit distributing binaries; a simple server build may need less tooling. Check Pro-only features separately. |
| 112 | [Caddy](https://github.com/caddyserver/caddy) | TLS-default web server/reverse proxy, automatic HTTPS and JSON configuration. Fit small-team hosting; cert/domain/storage lifecycle still needs operational tests. |
| 113 | [Kamal](https://github.com/basecamp/kamal) | SSH-driven Docker app deployments with proxy cutover. MIT; works beyond Rails. Fit owning VMs without adopting a cluster scheduler; Docker/host/backup operations remain. |
| 114 | [Trivy](https://github.com/aquasecurity/trivy) | Dependency/container/config/secret/license scanning; Apache-2.0. Fit release checks; results require triage and do not prove absence of vulnerabilities. Owner warns canary builds may contain critical bugs. |
| 115 | [Dependabot](https://github.com/dependabot/dependabot-core) | Dependency-update PRs with manifest/lockfile changes; GitHub uses core in production. Fit regular updates; review/tests must distinguish security fixes from breaking upgrades. |

## Verified avoid / migrate / context list

Status read 2026-11-07. “Avoid new” does not imply immediately rewriting a working product. Migration burden is a product risk; preserve saved documents, URLs and customer workflows while changing internals.

| Choice | Status, reason, replacement and exception |
|---|---|
| Create React App | **Avoid new; plan migration.** Deprecated 2025-02-14; React says no active maintainers. Framework or Vite/Parcel/Rsbuild replacement. Existing maintenance mode is not an emergency rewrite; routing/build/test differences need checking. [Owner](https://react.dev/blog/2025/02/14/sunsetting-create-react-app). |
| AngularJS | **Avoid new; migrate supported production.** Official support ended Jan 2022. Current Angular or another maintained stack; migration is not a simple package rename. Third-party support may buy time for legacy systems. [Owner](https://docs.angularjs.org/misc/version-support-status). |
| Vue 2 | **Avoid new; migrate or pay for explicit legacy support.** EOL 2023-12-31, no new upstream fixes. Vue 3; plugin/API migration required. Owner names HeroDevs security support for teams unable to move. [Owner](https://v2.vuejs.org/eol/). |
| Node Sass | **Migrate.** EOL 2024-07-24; package deprecated/repository archived. Dart Sass is owning project's replacement. Native binding/build fragility compounds old Node dependencies. Sass language remains viable. [Owner](https://sass-lang.com/blog/node-sass-is-end-of-life/). |
| Draft.js | **Avoid new; plan document-aware migration.** Owner archived repository 2023-02-06. README directs users toward Lexical; Tiptap/ProseMirror are other model choices. Stored content conversion, paste and selection regressions need tests. [Owner](https://github.com/facebookarchive/draft-js). |
| react-beautiful-dnd | **Avoid new; migrate as needed.** Archived and npm-deprecated; owner points to Pragmatic drag and drop. dnd-kit is another option. Keyboard/screen-reader behavior and visual continuity may differ; replacement is not drop-in. [Owner](https://github.com/atlassian/react-beautiful-dnd). |
| Polaris React | **Avoid new Shopify development.** Archived/unmaintained; Polaris Web Components released 2025-10-01 are owning direction. Existing embedded apps require an explicit transition. Outside Shopify, old code license was already restricted. [Owner](https://github.com/Shopify/polaris-react-archive), [license](https://github.com/Shopify/polaris-react-archive/blob/main/LICENSE.md). |
| `request` | **Avoid new; migrate Node HTTP code.** Fully deprecated 2020-02-11 with no new changes expected. Native `fetch` or an actively supported client; preserve proxy, cookie, timeout and streaming semantics. [Owner](https://github.com/request/request). |
| Moment.js | **Avoid by default for new work; existing use can remain.** Owner labels it legacy/maintenance. Native Intl, date-fns or Luxon can fit new work. Migration can change mutable date assumptions, parsing and timezone behavior. Maintenance is not abandonment. [Owner](https://momentjs.com/docs/). |
| Lucia npm library | **Avoid new dependency.** Current site says deprecated March 2025 and revised July 2026; now points to educational material and a single-file replacement. Better Auth or owned reviewed session code are options; educational code does not become an automatic security guarantee. [Owner](https://lucia-auth.com/). |
| `dexie-observable` / `dexie-syncable` | **Avoid new sync design.** Dexie README explicitly deprecates them and says they are incompatible with Dexie Cloud. Choose current supported sync design or owned protocol. Core Dexie remains viable. [Owner](https://github.com/dexie/Dexie.js). |
| EOL Node versions | **Migrate production runtime.** Runtime install compatibility is not maintained support. Official table on read date lists 20 and earlier EOL and 22/24/26 LTS. Recheck native modules, container images, CI and package engines during upgrade. [Owner](https://nodejs.org/en/about/previous-releases). |
| Tailwind v4 for older required browsers | **Unsuitable for that target, not deprecated.** Chrome 111/Safari 16.4/Firefox 128 minimum core requirements. Older Tailwind/custom CSS may be required; lowering JS transpilation target cannot polyfill every CSS behavior. [Owner](https://tailwindcss.com/docs/compatibility). |
| Slate as a turnkey editor | **Context warning, still viable.** Owning README says beta, contributor-driven and breaking APIs possible. Strong custom editor candidate for a capable team; Tiptap/prebuilt editor integration may reduce some ownership. [Owner](https://github.com/ianstormtaylor/slate). |
| Prisma 8 RC as assumed stable | **Context warning.** Current README explicitly labels RC and publishes feature gaps. Use supported stable version when release risk is unacceptable, or evaluate RC deliberately; do not infer that latest branch equals final. [Owner](https://github.com/prisma/prisma). |
| Current Redis as “BSD” | **License assumption to avoid, not technology ban.** Current README distinguishes ≤7.2 BSD from 8+ tri-license and optional optimization constraints. Evaluate exact distribution; Valkey is BSD alternative where technically compatible. [Owner](https://github.com/redis/redis), [Valkey](https://valkey.io/). |
| Meilisearch as uniformly MIT | **License assumption to avoid.** Repository explicitly separates MIT and BUSL-1.1 Enterprise code. Check edition/features; this does not make Community unusable. [License](https://github.com/meilisearch/meilisearch/blob/main/LICENSE). |
| Abandoned-looking ProseMirror/CodeMirror GitHub mirrors | **Do not avoid based on mirror activity.** Both READMEs state repositories moved to code.haverbeke.berlin. Check new owners before judging maintenance. [ProseMirror](https://github.com/ProseMirror/prosemirror), [CodeMirror](https://github.com/codemirror/dev). |

## Shortlist maintenance and security snapshot

Read 2026-11-07. Narrow check of release pages, policies and published advisories; no installation, dependency resolution, code audit or exploit testing. Versions are observations, not permanent recipe pins. Public reporting policies show a reporting route, not independently verified response performance. Advisory counts cannot rank projects' security.

| Shortlist item | Observed owner evidence / adoption consequence |
|---|---|
| **Turbo** | [Releases](https://github.com/hotwired/turbo/releases) show 8.0.23 on 2026-01-29. [Cookie-session race advisory](https://github.com/hotwired/turbo/security/advisories/GHSA-qppm-g56g-fpvp) affects ≤8.0.20; fixed 8.0.21. Delayed frame responses could restore old cookie sessions after logout. Server-side session stores remain authoritative. Check logout with in-flight frames; this specific fix does not certify the whole session design. |
| **htmx** | [Releases](https://github.com/bigskysoftware/htmx/releases) show 4.0.1 on 2026-11-01 alongside 2.0.11. Versioned docs/examples must match the selected major; do not mix current releases with older snippets. [Advisory page](https://github.com/bigskysoftware/htmx/security/advisories) showed no published advisories; that is not evidence of no vulnerabilities. |
| **React Aria Components** | [Owner releases](https://github.com/adobe/react-spectrum/releases) show 1.22.0 on 2026-10-09 with preceding releases. [Security policy](https://github.com/adobe/react-spectrum/security/policy) routes reports through Adobe. This establishes active release/reporting infrastructure, not accessibility compliance of an app assembled from the components. |
| **TanStack Table** | [Release page](https://github.com/TanStack/table/releases) lists core and React adapter 9.3.1, 2026-10-12; adapter fix addresses stale rows under cached React elements. Match adapter/core versions and framework major. [Policy page](https://github.com/TanStack/table/security/policy) had no detected SECURITY.md; do not infer abandonment or lack of any reporting route from that alone. |
| **DOMPurify** | [Releases](https://github.com/cure53/DOMPurify/releases) show 3.4.17, 2026-10-12. [Critical advisory](https://github.com/cure53/DOMPurify/security/advisories/GHSA-cg2g-xh64-v4q7) affects 3.4.4–3.4.16 with SAFE_FOR_TEMPLATES plus DOM-returning/in-place modes and attached shadow-root input; fixed 3.4.17. Keep sanitizer patches prompt and test the actual input/output mode. This is not a claim that every configuration was exploitable. |
| **Better Auth** | [Releases](https://github.com/better-auth/better-auth/releases) show stable 1.7.18, 2026-11-05, separately from 1.8 beta. [Email OTP advisory](https://github.com/better-auth/better-auth/security/advisories/GHSA-2f9c-7xj7-gh55) affects ≥1.3.7,<1.7.16: concurrent guesses bypass attempt counting; additional address problems depend on email-change settings/database collation. [OAuth advisory](https://github.com/better-auth/better-auth/security/advisories/GHSA-9hm7-xhfp-cx58) affects ≥0.4.9,<1.7.16 for specified provider/claim configurations. Both fixed in stable 1.7.16 or beta.5. Prefer current supported stable; review enabled plugins, provider claims and account-linking tests. |
| **Playwright** | [Releases](https://github.com/microsoft/playwright/releases) show 1.65.0, 2026-11-05; Node 20 no longer tested, supported Node 22/24/26, Docker image moves to Node 26. [Policy](https://github.com/microsoft/playwright/security/policy) routes private reports to MSRC. Align local/CI runtime and browser image versions; the release's runtime statement does not establish compatibility for every test dependency. |

No package lockfile was selected for this research. Exact transitive dependencies, peer resolution and application regressions remain implementation checks; this limits the claims above, rather than leaving an unfinished general survey. Primary READMEs establish the broader catalog's capabilities and stated licenses; these targeted checks must not be generalized into an equal maintenance rating for all 115 entries.

### Additional support and patch checks

The following owner checks address consequential lifecycle differences. A fix floor identifies a particular historical issue; choose a current supported release and inspect later advisories before implementation.

| Tool | Verified status and consequence |
| --- | --- |
| Rails | Published policy gives a minor series one year of bug fixes and two years of security fixes. Compare dates, not only the page’s “currently supported” heading, which retained some past bug-fix dates on inspection. [Policy](https://rubyonrails.org/maintenance) |
| Django | Owner lists 5.2 LTS extended support through April 2028 and 6.1.3 as latest official release. The catalog intentionally cites 5.2 capabilities. Buttondown supplies actual builder-use evidence, not market share. [Support table](https://www.djangoproject.com/download/) |
| React Server Components | Updated advisory lists fixes 19.0.4/19.1.5/19.2.4 after incomplete earlier fixes. Client-only React and tooling without RSC are unaffected by these particular issues. Check framework-bundled server dependencies too. [Advisory](https://react.dev/blog/2025/12/11/denial-of-service-and-source-code-exposure-in-react-server-components) |
| Next.js | Policy lists 16 Active LTS, 15 Maintenance LTS extended through January 31, 2027, and 14 unsupported; canary is not recommended for production. Maintenance updates can require behavioral changes. [Policy](https://nextjs.org/support-policy) |
| TanStack Start | Current v1 docs explicitly mark Start stable and provide RC migration guidance. Router and Start are separate lifecycle questions; old beta descriptions are stale. [Owner docs](https://tanstack.com/start/latest/docs/framework/react/overview) |
| PDF.js | July 2026 advisory names 6.2.108 as patched for malicious PDFs with scripting enabled and no blocking CSP. Its affected-version field omits an upper bound; do not infer all later versions are vulnerable. Check the actual parser configuration and current supported fix. [Advisory](https://github.com/mozilla/pdf.js/security/advisories/GHSA-hq66-cqwq-w95j) |
| openid-client | Owner lists v6 support for features, bugs and security; security EOL is TBD. README reports OpenID conformance certification, which covers protocol profiles rather than the whole app. [Support policy](https://github.com/panva/openid-client/security/policy), [README](https://github.com/panva/openid-client) |
| Drizzle | Release page shows 1.0.0-rc.5 alongside 0.45.4 and separate Kit releases. RC notes include breaking query/API changes. Match ORM, migration tooling and driver versions deliberately. [Releases](https://github.com/drizzle-team/drizzle-orm/releases) |

## What to build first

These priorities synthesize the cases, component reference and platform contracts above. They are proposed product guidance, not changes to repository architecture decisions. A sector-specific requirement can move an item earlier; no evidence here authorizes every optional feature in every app.

### 1. Prove one valuable workflow

Identify the operator, buyer, triggering event and durable result. Build one realistic path from existing data to completed work, including a representative import and a usable output. Watch intended customers perform it with their own vocabulary. Record failed steps and workarounds, not only enthusiasm. The College Conductor case warns that domain access and years of coding can still produce no customers; the focused products show why a narrow job can be enough.

Choose the first home screen from that job: an action queue for operators, a recent-work view for collaborators, a report for decision makers. Do not start with a dashboard of empty cards merely because other SaaS products have dashboards. Establish plain navigation, readable list/detail screens, persistent labels, useful defaults and predictable save behavior. Use the 100-detail reference to finish those few screens before adding more modules.

### 2. Make ordinary work safe

Before paid operational use, complete authentication/recovery, tenant authorization, reliable writes, validation, error recovery, export and tested restoration. Separate pending, failed and confirmed results. Make organization and permission context visible. Preserve input through refresh, session expiry and common interruptions. Test a real large record and long names; empty demos are inadequate fixtures.

For collaboration, add invitations with clear roles and billing consequences. Permission enforcement belongs in the foundation; a customer-facing role designer is optional product scope. For background operations, persist intent and expose outcomes. For imported data, preview mapping/losses and make a controlled cutover possible. The outage and migration cases explain why these are quality features rather than invisible backend work.

### 3. Set a support promise the team can maintain

Pick supported browser/OS/device combinations from actual customers and the core feature. Write down feature exceptions and retirement notice. Test the main workflow with keyboard, zoom, touch where needed, poor connectivity and the oldest supported browser. Keep monitoring, backup checks and customer contact usable during the app’s own outage. A promise of full offline editing or 24/7 response changes architecture and staffing; price and staff it deliberately.

Start with a familiar coherent stack. Server-rendered forms plus small widgets fit many business workflows. A document editor, canvas or latency-sensitive manipulation may justify a richer client. Add a second database, sync engine or orchestration service for a demonstrated workload and an explicit owner. The builder accounts support multiple successful combinations, not a winning framework.

### 4. Make the purchase understandable

Explain the charging unit, included usage, renewal timing, taxes/fees where applicable, and what inviting another person changes. Make invoices, payment updates, cancellation and export findable. Model free users, heavy users, support and third-party processing before launching unlimited plans. Show when payment failure threatens access and give a practical recovery route.

Measure the complete account funnel: qualified visitor or lead → first useful result → repeated team value → paid account → renewal. Keep acquisition channel, plan, company size and assistance visible in the analysis. A/B test where volume supports it; use observed task failures and customer interviews where it does not. Do not optimize a signup percentage by removing difficult but valuable buyers from its denominator.

### 5. Differentiate where work repeats

Good candidates are fast keyboard paths, useful saved views, clear comparison, bulk actions with partial-result recovery, excellent domain-specific imports, restrained notification controls and a coherent visual direction. Choose from actual repeated work. An expert queue may earn dense tables and shortcuts; an occasional approval flow may earn plain language and fewer choices. Character should clarify people, state or purpose rather than consume working space.

Test each differentiator against a baseline: does the operator finish accurately, with fewer interruptions and less reconstruction of context? Keep richer features optional when they serve only one role. The contrasting analytics reviews show that “simpler” is useful only relative to a specific question and workload.

### 6. Delay costly promises until justified

| Investment | Earns its cost when | First lower-cost approach |
| --- | --- | --- |
| Full offline collaboration | Work must continue through disconnection and merge later | Recoverable drafts; explicit online writes |
| Custom spreadsheet/grid | Frequent cell editing, comparison and bulk manipulation are central | Semantic table, focused edit form, pagination |
| General workflow builder | Customers repeatedly need different supported processes | A few explicit workflows and integration hooks |
| Custom rich editor | Structured document work defines the product | Plain text/Markdown or a carefully scoped existing engine |
| SSO/provisioning/residency variants | Target buyers require them and contracts cover operation | Clear account/admin model and an honest supported-market scope |
| Autonomous AI actions | A bounded task has measurable value and enforceable permissions/review | Suggestions, drafts or deterministic automation |
| New distribution ecosystem | Its buyers match the niche and ongoing review work is affordable | One direct channel with retained-account measurement |
| Full design system | Repeated components and contributors create real inconsistency | A small coherent set with documented states |

### Ideas to test, not universal prescriptions

Try meaningful sample data versus direct import; compare a project home with a personal queue; test clearer pricing terms before changing the price model; test contextual help against a full tour; compare annual offers after demonstrated value with offers at signup. Define the outcome and guardrails first: qualified activation, task error, retained revenue, support load and customer trust. Stop experiments that win the local metric by damaging the actual job.

## Sources read and scope

Citations throughout the report link to inspected source material; the definitions below resolve the shorter component references. Research combined official docs/design systems, owning repositories and advisories, founder accounts, independent reviews, first-person switching reports, experiment reports, accessible book chapters, podcast transcripts and direct visual inspection. Relevant sections of long references were read, not necessarily every page end to end. Repeated coverage of one founder claim is not independent corroboration.

Direct visual work covered the published Linear sidebar comparison, Plausible’s public dashboard/date menu, Basecamp’s Pings image, Page Flows’ public catalog and Atlassian motion panels. No customer accounts, full assistive-technology audit, package installation or comparative performance benchmark was used. Paid flow libraries were not accessed; public live screens and product/design-system examples supplied alternatives. Motion playback was not verified. These limits constrain appearance/interaction claims beside the examples.

Financial cases favor publicly transparent English-language companies. Where profit, support labor or acquisition cost is undisclosed, the report leaves it undisclosed; revenue stories cannot fill it in. Sector-specific legal obligations and country eligibility require a defined product/market before a precise implementation plan. Historical reviews, incidents and pricing stories remain dated; they do not establish current defect rates. Groove’s inaccessible historical pricing article was excluded after direct URL variants failed, using the direct WorkZone and Teamleader cases instead.

Repository docs establish capabilities and stated licenses. The maintenance snapshot is a targeted additional check, not an audit of every catalog entry or transitive dependency. Broken primary URLs were recovered through owning READMEs, replacement documentation and public release/security pages where possible. Sources that could not support a claim were omitted rather than promoted from a search snippet.

[tables]: https://www.nngroup.com/articles/data-tables/
[empty]: https://www.nngroup.com/articles/empty-state-interface-design/
[refresh]: https://linear.app/now/behind-the-latest-design-refresh
[complex]: https://www.smashingmagazine.com/2019/02/complex-web-tables/
[pencil]: https://www.pencilandpaper.io/articles/ux-pattern-analysis-enterprise-data-tables
[balsamiq]: https://balsamiq.com/learn/tables-data-grids/
[walter]: https://stephaniewalter.design/blog/essential-resources-design-complex-data-tables/
[grid]: https://www.w3.org/WAI/ARIA/apg/patterns/grid/
[validation]: https://design-system.service.gov.uk/patterns/validation/
[errors]: https://design-system.service.gov.uk/components/error-message/
[text]: https://design-system.service.gov.uk/components/text-input/
[checks]: https://design-system.service.gov.uk/components/checkboxes/
[radios]: https://design-system.service.gov.uk/components/radios/
[date]: https://design-system.service.gov.uk/components/date-input/
[review]: https://design-system.service.gov.uk/patterns/check-answers/
[tasks]: https://design-system.service.gov.uk/patterns/complete-multiple-tasks/
[upload]: https://design-system.service.gov.uk/components/file-upload/
[combo]: https://www.w3.org/WAI/ARIA/apg/patterns/combobox/
[dialog]: https://www.w3.org/WAI/ARIA/apg/patterns/dialog-modal/
[menu]: https://www.w3.org/WAI/ARIA/apg/patterns/menubar/
[tabs]: https://www.w3.org/WAI/ARIA/apg/patterns/tabs/
[alert]: https://www.w3.org/WAI/ARIA/apg/patterns/alert/
[modal]: https://www.nngroup.com/articles/modal-nonmodal-dialog/
[freedom]: https://www.nngroup.com/articles/user-control-and-freedom/
[mental]: https://www.nngroup.com/articles/mental-models/
[bulk]: https://www.eleken.co/blog-posts/bulk-actions-ux
[waits]: https://www.nngroup.com/articles/designing-for-waits-and-interruptions/
[progress]: https://www.nngroup.com/articles/progress-indicators/
[disabled]: https://www.smashingmagazine.com/2021/08/frustrating-design-patterns-disabled-buttons/
[buttons]: https://www.nngroup.com/articles/button-states-communicate-interaction/
[search]: https://linear.app/docs/search
[views]: https://linear.app/docs/custom-views
[editor]: https://linear.app/docs/editor
[enter]: https://linear.app/changelog/2026-03-12-ui-refresh
[roles]: https://linear.app/docs/members-roles
[notifications]: https://linear.app/docs/notifications
[import]: https://linear.app/docs/import-issues
[searchincident]: https://linearstatus.com/incidents/01JTQDWV0B4AVY6X3SXK1P9FJN
[notionbill]: https://www.notion.com/help/members-and-billing
[permissions]: https://www.notion.com/help/sharing-and-permissions
[complaint]: https://www.reddit.com/r/Notion/comments/1qhj2cs/i_was_one_of_notions_biggest_cheerleaders_now_i/
[permissioncomplaint]: https://www.reddit.com/r/Notion/comments/1nzek5p/granular_notion_database_permissions_expectations/
[export]: https://www.notion.com/help/export-your-content
[history]: https://www.notion.com/help/duplicate-delete-and-restore-content
[stripe]: https://docs.stripe.com/customer-management
[helpscout]: https://docs.helpscout.com/article/1495-import-emails-or-tickets-into-help-scout
[wireframes]: https://www.smashingmagazine.com/2016/11/wireframe-perfectionist-guide/
[podcast]: https://www.usetranscribe.io/yt/4muxFVZ4XfM/linear-design-culture
[shape]: https://basecamp.com/shapeup/3.5-chapter-14
