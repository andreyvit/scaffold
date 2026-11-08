# Great 2D cross-platform mobile games for iOS and Android

Researched 2026-11-08. Recommendations are research, not confirmed scaffold choices.

Read by task: [build priorities](#prioritized-build-guidance) · [game examples](#exemplary-games-including-weaknesses) · [visual directions](#five-coherent-visual-directions) · [100 practical details](#100-practical-details) · [commercial evidence](#commercial-conclusions) · [engine choices](#good-stacks-and-their-costs) · [compatibility](#compatibility-four-promises) · [tool catalog](#catalog-important-named-tools-and-components) · [avoid/migrate](#named-avoid-migrate-and-conditional-choices) · [sources](#sources-and-method)

## Scope

Indie and small-team games with 2D gameplay and primarily 2D presentation, shipping on iOS and Android. Puzzles, cards, tactics, platformers, arcade/action, simulation and narrative games; premium, free-to-start, ad-supported and subscription distribution. Include larger games only for bounded lessons. Compare genre, audience and region branches; none was selected by the user. Spatial 3D/2.5D production is covered in [3D mobile games](mobile-3d-games.md); this report emphasizes 2D controls, composition, animation, content and engineering. Real-money gambling, full MMO operations and console-only production are outside the core scope.

Related research: [iOS](ios-apps.md), [Android](android-apps.md). Related confirmed recipes: [values](../skills/scaffold/references/values.md), [iOS layering](../skills/scaffold/references/ios-layering.md), [testing](../skills/scaffold/references/testing.md), [offline sync](../skills/scaffold/references/offline-sync.md). Native non-game app defaults do not select a game engine; document conflict rules do not define currency/save reconciliation.


## What makes a 2D mobile game great

A strong 2D game makes one action or decision satisfying, teaches its rules and preserves progress through ordinary phone use. Flat graphics simplify some production work; they do not guarantee readable combat, precise touch, small memory use or a viable business.

Evaluate these outcomes separately:

| Meaning | Useful evidence | False substitute |
|---|---|---|
| Player love | Voluntary return, memorable moments, recommendations, pleasure in the central action | Compulsive collection or impressive screenshots |
| Player value | Relaxation, mastery, curiosity, expression, narrative or connection | Feature count and hours demanded |
| Audience | Qualified installs, completed first sessions, retained cohorts and referrals | Giveaway downloads alone |
| Cash | Net receipts, refunds and payer cohorts | Gross sales or ad impressions |
| Viability | Receipts cover labor, updates, acquisition and support over time | A strong launch week |
| Maintainability | Reproducible releases, inspectable rules, safe saves and usable authoring tools | An engine's reputation |
| Featuring | Distinctive design, technical quality and a clear editorial pitch | Guaranteed promotion after compliance |

This is a research evaluation framework, not a measured ranking. A finite story can succeed when players finish and leave satisfied. A roguelike may earn years of replay without daily chores. Retention targets must fit the promised experience.

### Genre changes the main constraint

| Branch | Protect first | Main cost or trap |
|---|---|---|
| Board, word, logic and number puzzles | Legible state, reliable discrete moves, useful undo, understandable rules | Difficulty disguised as unclear UI; enormous level-design effort |
| Cards, dice and turn-based tactics | Inspect-before-commit, readable consequences, predictable random boundaries, resumable runs | Dense desktop panels and tiny tooltips; endless combinatorial testing |
| Platformers, runners and arcade action | Touch accuracy, hazard visibility, predictable motion, quick retry | Fingers hiding action; frame-dependent difficulty; excessive effects |
| Survivor-like action | One clear movement verb, enemy/loot hierarchy, bounded simulation and effects | Late-run CPU/memory spikes that the tutorial never exercises |
| Farming and management | Selection, placement, inventories, time semantics and durable long saves | Tiny controls, repetitive chores, version drift and costly content |
| Narrative and adventure | Comfortable reading, expressive choices, scene continuity and accessible inspection | Localization, voice assets and branching QA outgrowing code effort |
| Rhythm | Calibrated timing, audio-route behavior and readable beat feedback | Bluetooth latency, interruptions and assuming all devices behave alike |
| Social/competitive | Match integrity, reconnect, moderation and supported service lifetime | Operations and acquisition requirements exceeding a small team's capacity |

These are derived planning distinctions, supported by the examples and implementation sections below. They are not recommendations to add every genre's systems.

## Prioritized build guidance

These are research recommendations. Confirm product goals before turning optional features into requirements.

1. **Prove the central action on both phone platforms.** Build one representative board, level or encounter. Test with fingers at the smallest intended viewport and weakest intended hardware. Include the stressful state: dense enemy waves, a crowded inventory, long translated text or a late-game board. The Downwell disagreement and Papers, Please recomposition show why a pleasant desktop prototype is insufficient.
2. **Choose the business promise before building progression.** Premium, a clear demo unlock, rewarded ads and a subscription catalog create different expectations. Prototype the free boundary and purchase explanation with the core loop. Treat the commercial case studies as hypotheses, not target conversion rates.
3. **Prove the shipping stack early.** Make signed iOS and Android builds with one real native integration, release configuration, a purchase sandbox round trip, suspend/resume and a save migration. A renderer demonstration does not prove that the selected engine/plugins can ship. Use the stack and compatibility sections to bound this test.
4. **Make state independent of visual effects.** Define durable progress, current-run state, settings and ownership separately. Save at meaningful boundaries; recover cleanly if the process dies during a transition. Store versioned state, not only scene paths or animation positions. Keep known-good recovery data before migrations. See the save examples above.
5. **Teach by controlled play.** Show the causal rule, let the player try it, then add a variation. Observe where fresh players hesitate. Preserve intentional challenge; fix invisible rules and unclear controls. Threes and Hundreds support iteration with strangers, not assuming minimal text means easy learning.
6. **Build the content workflow before multiplying content.** Export one complete level/card/story branch through the actual tools. Validate identifiers, missing references, localization and save compatibility. Count authoring/review hours per content unit. If a second level requires engineering edits everywhere, fix that before promising hundreds.
7. **Establish the visual and accessibility contract.** Choose one coherent art family and a readable functional UI. Test large text, color-independent states, reduced effects, muted audio and alternate input early. Add narrated navigation when it fits the intended audience and game; budget semantic game-state access instead of assuming a screen reader can read pixels.
8. **Release with a supportable scope.** Ship the supported device matrix, documented offline behavior, recovery path, privacy declarations and store-required flows. Delay multiplayer, cross-save, user levels and live events until their extra contracts are justified. An optional system still needs complete behavior once shipped.
9. **Measure the funnel and the burden together.** Track first-session comprehension, run completion, save failures, purchase failures, refunds, retained cohorts and support contacts. Segment by platform, build, hardware tier, region and acquisition source where sample sizes permit. Do not optimize aggregate revenue while hiding a device-specific crash or payer backlash.
10. **Keep an exit plan.** Preserve release tooling, signing access, source assets, export formats and a viable offline mode where promised. Budget store/SDK updates even for finished premium content. Explain service closure, catalog removal and entitlement changes before players discover them through a broken launch.

### Useful differentiators

For a puzzle, consider deep undo/redo, shareable deterministic challenges and hints that preserve discovery. For action, consider adjustable touch zones, effect intensity and controller parity. For tactics, provide readable consequence previews and resumable runs. For narrative, invest in text comfort, voice controls and meaningful choices. For creative/simulation play, prioritize placement recovery and save portability. Each differentiator should reinforce the central experience, not create a second product to maintain.

### Costly traps

Avoid choosing an engine by empty-scene FPS, promising every old device, equating pixel art with cheap animation, adding daily chores to a finite game, requiring accounts before offline play, or building an economy before demonstrating enjoyment. Avoid live multiplayer without enough concurrent players and an operations budget. Do not clone a hit's currencies or art and assume its launch audience follows.

### Tests worth running

| Hypothesis | Compare | Judge with |
|---|---|---|
| Players understand the first rule | Guided move versus a safe playable example | Correct next action without prompting; confusion and abandonment |
| Touch causes avoidable deaths | Fixed versus adjustable/floating controls, same encounter | Missed inputs, finger occlusion, comfort; separate expert learning |
| The demo ends at useful value | Two clear content boundaries | Qualified unlocks, refunds, satisfaction and unpaid return—not just taps |
| Rewarded ads fit the loop | Opt-in placement at a safe paused checkpoint versus after a run | Net receipts, retention, interruption complaints and reward failures |
| More effects improve feel | Restrained versus richer impact feedback | Readability, comfort, frame timing and battery use; allow reduction |
| Localization expands reach | Staged launch in one fully tested locale, controlling traffic source and region | Market validation: acquisition quality, conversion, support and maintenance cost; cross-locale differences do not isolate translation |

Define the unit of randomization and event semantics, retain variant exposure, choose a primary metric and guardrails, and predefine stopping criteria. A small premium audience may support observed playtests and staged releases better than an underpowered A/B test. Public case studies cannot supply your minimum detectable effect, acquisition cost or sustainable price without your audience and cost structure.

## Exemplary games, including weaknesses

These references answer different meanings of “great.” No single ranking follows from them; independent reviews are qualitative evidence, not retention or profit measurements.

**Threes! — compact systemic depth and character.** Mark Brown’s March 2014 review praises deliberate sliding, satisfying combinations, tile personalities and spare audiovisual style. He also finds unlucky tile placement frustrating. Its useful lesson is a legible core action that supports planning and expression; randomness needs to remain understandable when it ends a promising run. Emotional appeal and repeatable mastery are supported; financial sustainability is not measured here. [Pocket Gamer](https://www.pocketgamer.com/threes/review/).

**Mini Metro — readable systems with growing pressure.** Christian Valentin’s October 2016 iPad review describes initial confusion followed by satisfying network optimization. A simple transit-map surface conceals constrained resources and consequential rebuilding. The risk is mistaking visual minimalism for a self-explanatory simulation. Strong reference for direct manipulation and player value through problem solving; its daily mode does not prove daily retention. [Pocket Gamer](https://www.pocketgamer.com/mini-metro/review/).

**Downwell — action compressed into three buttons.** Harry Slater’s October 2015 iOS review praises responsive simple controls, hard-earned progress and weapon variety. Jump and shooting share one button according to state. High difficulty is central, so a broad casual audience is not implied. The lesson is to make a small verb set interact deeply with movement and resources before adding controls. [Pocket Gamer](https://www.pocketgamer.com/downwell/review/).

**Super Hexagon — severe focus; disputed touch feel.** Jon Mundy’s September 2012 mobile review finds it compelling but twitchy, disorienting and frustrating. Graham Smith’s December PC review describes learning over several days and praises subtle feedback and music. The disagreement is partly input/platform and partly taste; it is not a contradiction to erase. Strong mastery and audiovisual identity can coexist with exclusionary motion and precision demands. [Mobile review](https://www.pocketgamer.com/super-hexagon/review/), [PC review](https://www.pcgamer.com/super-hexagon-review/).

**Reigns — one gesture, consequential fiction.** Harry Slater’s August 2016 review values its strange humor and balancing of four pressures. Holding a swipe previews the reply, but outcomes remain partly hidden. It works when the uncertainty serves fiction; the same opacity would be wrong in purchase or save confirmation. A useful short-session narrative reference, not proof that binary choices always provide strategic agency. [Pocket Gamer](https://www.pocketgamer.com/reigns/review/).

**Florence — finite emotional value.** Harry Slater’s February 2018 review praises simple tactile scenes, the piano/cello score and the relationship story while stressing its short length and low replayability. Completion can be success: forcing endless progression would undermine this product. The interaction should convey feeling, not merely interrupt reading with chores. [Pocket Gamer](https://www.pocketgamer.com/florence/review/).

**Alto’s Adventure — coherent craft over novelty.** Federico Viticci’s 2015 review finds the runner familiar but values weather, parallax, scarves, natural sounds and carefully joined actions. The design offers a calm experience without requiring an original genre. Art polish is labor, however; imitating the palette alone does not reproduce the control feel or pacing. [MacStories](https://www.macstories.net/reviews/altos-adventure-review-a-beautiful-descent/).

**Baba Is You — rules become manipulable objects.** Jon Mundy’s July 2021 review, explicitly version 1.0, praises the small-board logic and alternate levels when stuck; he warns about difficulty and limited control choices. A July 2023 App Store reviewer separately dislikes repeated swipe movement and wants alternative input. These are dated critiques, not current verified defects. Undo and route choice encourage experimentation, while the core puzzle remains demanding. [TapSmart](https://www.tapsmart.com/games/baba-is-you-review/), [App Store player reports](https://apps.apple.com/gb/app/baba-is-you/id1517281887?platform=iphone&see-all=reviews).

**Papers, Please — adapt the work surface.** Lucas Pope’s August 2022 port account explains replacing the desktop document desk with a readable phone carousel and miniature rack. This changes how players compare documents; preserving the fiction mattered more than preserving every mouse action. The 2014 iPad review praised bureaucracy turned into moral tension, while noting fiddly paper handling. Do not use an iPad judgment to certify the later phone layout. [Developer account](https://dukope.com/devlogs/papers-please/mobile/), [iPad review](https://www.pocketgamer.com/papers-please/review/).

**Balatro — deep portable sessions with lifecycle risk.** Donovan Erskine’s September 2024 preview praises haptics and drag-to-buy/use/sell adaptations. It also reports runs lost after extended suspension. The reviewer speculates about the phone’s role; this is not a diagnosed OS bug. The practical lesson is to test genuine process death, not merely a quick background/foreground cycle. [Shacknews](https://www.shacknews.com/article/141549/balatro-mobile-impressions).

**Dead Cells — a demanding action port with options.** Playdigious documents adjustable button size/position, Original and Auto-Hit modes, and controller support. NME’s June 2020 review praises the action and build variety but finds imperfect touch control and hand strain. This supports optional assistance and customization, not a claim that complex action always transfers comfortably. [Publisher](https://playdigious.com/games/dead-cells), [NME review](https://www.nme.com/reviews/dead-cells-review-a-good-mobile-port-of-an-excellent-roguelike-game-2699135).

**Vampire Survivors — simplify execution, retain decisions.** Pocket Tactics’ review, updated October 2025, praises the one-stick loop, automatic attacks, portrait/landscape choices and upgrades. Dense escalation supplies spectacle and load; the low-detail appearance does not establish battery or late-run performance. Automatic firing changes the skill being tested from attack execution toward movement/build choices. [Pocket Tactics](https://www.pockettactics.com/vampire-survivors/review).

**Sword & Sworcery — audiovisual authorship with deliberate friction.** GameSpot’s April 2012 PC review praises the world, writing and music but notes that indiscriminate clicking can stumble onto puzzle solutions. VideoGamer’s iOS review praises presentation but finds the tone pretentious and describes orientation changes and moon-phase play. Treat these as historical design lessons; platform availability and current social integration need separate checks. [GameSpot](https://www.gamespot.com/reviews/superbrothers-sword-and-sworcery-ep-review/1900-6373114/), [VideoGamer](https://www.videogamer.com/reviews/superbrothers-sword-and-sworcery-ep-review/).

## Good and bad UX: decisions behind the examples

**Preserve the intended challenge.** A puzzle should test reasoning; an action game may test precision; a narrative may ask for attention and interpretation. Unreadable cards, blocked targets, lost saves and mandatory accounts usually add unrelated friction. Some friction is authored: Papers, Please uses administrative work to create moral pressure; Super Hexagon makes concentration demanding. Explain the distinction through playtests rather than calling all difficulty bad UX.

**Make failure informative.** The player should know what hit them, which rule failed, or which resource ran out. A difficult game can tolerate frequent defeat if retry is fast and mistakes teach. Hidden randomness, missed gestures and unreadable effects can make an honest result feel arbitrary. Use deterministic replay/debug views internally to separate misunderstanding, bad input and intended difficulty.

**Design for stopping.** An uninterrupted half-hour run may be enjoyable; requiring one on a phone is another matter. Durable suspension, clear checkpoints and graceful audio interruptions make long games fit short opportunities. A finite game should celebrate its ending. Do not treat every completion as churn to prevent.

**Make comfort adjustable without erasing identity.** Players disagree about virtual sticks, swipes, auto-attack and effects. Provide the options that remove an actual barrier, describe their consequences and preserve them. A menu full of undocumented sliders merely shifts design work onto the player. XAG’s difficulty examples are design prompts, not a demand that every puzzle ship four arbitrary difficulty levels. [XAG 108](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/108).

## Five coherent visual directions

These are durable design families inferred from shipped examples and criticism, not a measured 2026 trend census. Direct screenshot and sampled-motion observations appear below.

**Graphic board — Threes!, Mini Metro.** A limited palette, flat shapes, clear numeric or geometric hierarchy and generous board margins suit short puzzles and systems. Use a quiet readable UI face; reserve character or illustration for pieces and transitions. Animate only changes that explain the rule. Risk: minimal surfaces can hide selection, gesture affordances and the cause of failure. Do not turn every setting into an unlabeled geometric icon. The two reviews above support the simplicity/depth tension, not this exact proposed style specification.

**Dense tactical tabletop — Balatro, Slice & Dice.** Cards, dice, counters and repeated rows make combinations inspectable. Keep a stable alignment grid; distinguish selected, targeted, exhausted and unavailable states through shape/border plus color. Large previews and staged tooltips can coexist with a dense overview. Risk: copying desktop density, decorative tiny type, and numerals whose meaning depends on hidden hover text. Make action order visible before adding celebratory effects. This is a proposed direction; the Balatro preview supports a need for mobile control adaptation.

**Hard-edged arcade pixel art — Downwell, Super Hexagon’s geometric cousin.** Few colors, strong silhouettes, clear hit reactions and short transitions suit timing and repeated runs. Keep visual pixels and input regions independent: a tiny character need not mean a tiny button. Use large numeric scores and sparse wording. Risk: decorative shake, flash, color cycling and particles obscure threats or cause discomfort. Intensity needs an adjustable presentation layer. Historical reviews support the appeal and discomfort tradeoff; they do not establish current accessibility options.

**Illustrated vignette — Florence, Reigns.** Distinct characters, restrained panels, generous text spacing and scene-specific gestures suit story and choice. Use display lettering for identity while keeping dialogue and choices readable. Motion should convey an emotional beat or consequence. Risk: forcing a timed gesture during reading, hiding response meaning under a finger, and stretching a short narrative with repetitive chores. This is a product style, not an instruction to maximize session length.

**Layered landscape — Alto’s Adventure, Sword & Sworcery.** Foreground silhouettes, separated depth planes, changing light and carefully synchronized sound create place without freely controlled 3D cameras. Keep foreground hazards distinct from scenic detail; use quiet HUD framing. Risk: parallax discomfort, low contrast at night, motion competing with the landing point, and art budgets spread across too many biomes. Broadly similar mood does not imply identical rendering technology.

### Design resources worth using

Use **Game UI Database** to compare shipped menus/HUDs by task, not to copy a random attractive screenshot. The site was access-restricted in this pass; the related 3D research documents its mobile filter and independent coverage. Do not claim direct browsing of its catalog here. Screen references are not production asset licenses. [Game UI Database](https://www.gameuidatabase.com/), [existing resource assessment](mobile-3d-games.md#design-reference-sources).

Use **Apple HIG and WWDC24/26 transcripts** for device behavior, safe areas, touch feedback and physical control mapping. They are vendor recommendations with concrete implementations; they do not measure delight or prove a genre’s economics. WWDC26 demonstrates combining hold/drag/release into one action rather than requiring a third finger. The rendering/API examples are Apple-specific. [WWDC24](https://developer.apple.com/videos/play/wwdc2024/10085/), [WWDC26](https://developer.apple.com/videos/play/wwdc2026/358/).

Use **Game Accessibility Guidelines** to identify motor, sensory and cognitive barriers early, and **Microsoft XAG** for detailed states and examples. Both include useful guidance beyond a store checklist. Translate examples to mobile dimensions and input; do not import television text sizes as phone pixel values. A color simulation is a check, not proof that every player can distinguish every state. [GAG](https://gameaccessibilityguidelines.com/), [XAG](https://learn.microsoft.com/en-us/xbox/accessibility/guidelines).

Use **developer breakdowns** for decisions: Pope for changing layout without losing the central activity; Maddy Thorson for deliberate input forgiveness; the independent reviews above for what players felt after implementation. Thorson’s examples are from Celeste, a non-mobile comparison, so timing values require mobile testing. [Celeste & Forgiveness](https://maddythorson.medium.com/celeste-forgiveness-31e4a40399f1).

**Book access:** Read the public input introduction of Jonathon Manning and Paris Buttfield-Addison’s *iOS Game Development Cookbook* (2014), not the full paid chapter. It frames raw touches as begin/move/end events interpreted into gestures. Useful historical architecture vocabulary; its APIs and hardware assumptions are not a current stack recommendation. Current Apple documentation supplies the implementation check. [Public chapter excerpt](https://www.oreilly.com/library/view/ios-game-development/9781449369644/ch03.html).

## Screen compositions to prototype

**Return screen:** Continue with run/chapter context, then New Game/level selection and settings. Put account or cloud state beside the save when needed; an offline solo board should not make login the main event. Keep destructive New Game apart from Continue.

**Board/puzzle:** The playable area dominates. Put next piece, current constraint and score where they remain visible during a drag. Keep undo/restart/hint available but out of the movement path. A strategy board may require zoom and inspection; a tiny fixed puzzle should not inherit them automatically.

**Action play:** Reserve thumb areas, show character/hazards clearly, put infrequent menu controls away from action targets, and design simultaneous actions with two hands actually holding the phone. Prototype the late-run effect density as well as the empty first level.

**Pause/settings:** Resume, objective/controls reminder, then sound/display/accessibility and restart/leave. Keep the scene stable behind the menu. An online world may continue; state that explicitly. Apply reversible changes with a preview, and keep reset separate from ordinary adjustment.

**Level/result:** Preserve chapter position; distinguish available/completed/locked/downloading. On failure, show cause and Retry first. On success, distinguish already-earned rewards from optional extras; a story ending needs closure before a sales opportunity.

**Cards/inventory/shop:** Keep inspect, select, equip, use and buy distinct. Support a large preview, show actual price and effect, preserve browse position and make Back reliable. Collections need search/filter only when their size makes browsing difficult.

**Save/recovery:** Show local/cloud state with useful context: chapter, playtime, updated time, device if known. Show what choosing either copy discards. Do not describe a sync failure as a reason to erase local progress.

## 100 practical details

Each paragraph pairs expected behavior with a tempting mistake, reason and applicable exception. These are design/engineering applications of the cited source or example; they are not all direct quotations, store mandates or measured conversion effects. Cross-platform implementations must verify native lifecycle and input wiring separately.

### Opening, learning and returning

**P01 — First action.** Let a player perform the core verb before optional news or account setup. A wall of explanation prevents the feedback needed to understand it. Introduce a single movable piece, safe jump or choice; an explicitly account-bound multiplayer game may need identity first. [Apple game design](https://developer.apple.com/design/human-interface-guidelines/designing-for-games).

**P02 — Replayable instruction.** Keep controls and rules available after onboarding. A one-time arrow fails the player returning after months. Show a small example with the current input mapping; do not replay the entire opening cinematic to recover one rule. [XAG objective clarity](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/109).

**P03 — Real initial content.** Include enough playable content to demonstrate the promise. Opening into a second download wastes anticipation. Show progress only when missing assets block a real choice; large episodic games can stream later chapters while earlier ones remain playable. [WWDC24](https://developer.apple.com/videos/play/wwdc2024/10085/).

**P04 — Accessible before difficult.** Make text size, contrast and essential input options reachable before the first mandatory challenge. Burying them behind success makes them useless. A compact opening link is often enough; do not force everyone through an exhaustive configuration wizard. [GAG discoverability](https://gameaccessibilityguidelines.com/provide-details-of-accessibility-features-in-game/).

**P05 — Teach the constraint.** Demonstrate the rule that makes the game interesting, such as overcrowding or limited tracks. Showing only how to drag can leave players operating confidently but misunderstanding why they lose. Mini Metro’s reviewer needed several attempts before its system clicked. [Mini Metro review](https://www.pocketgamer.com/mini-metro/review/).

**P06 — Practice without loss.** Give an unfamiliar gesture a safe place to try. Teaching a swipe during a fatal hazard mixes input learning with punishment. A deliberate high-stakes opening can remain authored, but offer replay/help outside it. [GAG intermediate](https://gameaccessibilityguidelines.com/intermediate/).

**P07 — Return context.** Continue should name the run, chapter or current objective. A bare button can resume an opaque half-finished puzzle. Keep a compact reminder available; do not spoil a mystery by explaining its solution. [XAG 109](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/109).

**P08 — Optional requests.** Ask for notifications, ratings or optional data when their value is clear. Stacking prompts before play makes consent an obstacle. Permission denial should preserve unrelated local play; a required online capability needs an honest explanation. [Apple game design](https://developer.apple.com/design/human-interface-guidelines/designing-for-games).

### Touch and physical input

**P09 — Reachable targets.** Measure controls physically on phones. Apple recommends 44×44 pt frequent controls; its game-control page allows smaller secondary controls. Do not equate game texture pixels with points or turn the smaller allowance into the default attack button. [Apple controls](https://developer.apple.com/design/human-interface-guidelines/game-controls).

**P10 — Feedback beyond the thumb.** A pressed glow should extend enough to remain visible around a finger. A hidden color change makes a successful tap feel missed. Sound/haptics reinforce it, but muted phones still need visual confirmation. [Apple controls](https://developer.apple.com/design/human-interface-guidelines/game-controls).

**P11 — Action symbols.** Use jump, attack or inspect imagery rather than unexplained A/B labels for touch. Preserve location when context changes. Controller prompts should match the connected device; the same icon vocabulary need not serve every input. [Apple controls](https://developer.apple.com/design/human-interface-guidelines/game-controls).

**P12 — Two-thumb combinations.** Try movement plus every urgent action together. Separately reachable buttons can still need a third finger. Combine aiming and releasing when that suits the mechanic; test the new release semantics rather than assuming fewer buttons are always better. [WWDC26](https://developer.apple.com/videos/play/wwdc2026/358/).

**P13 — Fixed or floating stick.** Offer a stable option where accidental recentering harms precision. A floating stick can improve initial reach but alter directional interpretation. Dead Cells documents customizable controls; its existence supports an option, not a universal preferred layout. [Playdigious](https://playdigious.com/games/dead-cells).

**P14 — Swipe preview.** Reveal the pending choice before release and allow retreat to cancel. Immediate commitment on touch-down punishes exploratory movement. Reigns previews the reply while swiping; keep uncertainty in fictional outcomes, not the wording of the selected answer. [Reigns review](https://www.pocketgamer.com/reigns/review/).

**P15 — Drag visibility.** Keep the dragged piece or its landing preview visible beside/above the finger when precision matters. A beautiful tile directly under the fingertip conceals placement. A broad whole-board swipe needs no pointer offset. [Gesture design essay](https://www.gamedeveloper.com/design/using-gestures-in-mobile-game-design).

**P16 — Drag versus scroll.** Define which region owns an initial touch and when it becomes a drag. Otherwise a player browsing cards can move one accidentally. Test movement thresholds and holds with real hands; a longer hold is not automatically more accessible. [Gesture design essay](https://www.gamedeveloper.com/design/using-gestures-in-mobile-game-design).

**P17 — Gesture alternatives.** Offer tap-select/tap-destination or directional buttons when dragging or multi-touch is not the intended challenge. Gestures can remain the fastest route. A puzzle whose difficulty is reasoning should not silently demand two-handed motor precision. [XAG input](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/107).

**P18 — Repetition cost.** Avoid making each grid step an awkward new swipe in a large traversal. Offer tested repeat or alternate movement where appropriate. Baba’s launch critic and a later player both question control choice; do not infer that every player dislikes swiping. [TapSmart](https://www.tapsmart.com/games/baba-is-you-review/), [player reports](https://apps.apple.com/gb/app/baba-is-you/id1517281887?platform=iphone&see-all=reviews).

**P19 — Input cancellation.** Treat canceled touches as canceled actions, releasing held movement and charge state. A system interruption must not leave the avatar running. This is an engineering consequence of gesture state, not a need for another UI button. [Android gesture lifecycle](https://developer.android.com/develop/ui/views/touch-and-input/gestures/multi).

**P20 — Per-finger ownership.** Track each active touch consistently until release/cancellation. Reassigning the second finger when the first lifts can turn an attack into movement. Test crossed fingers and rapid re-entry; Android distinguishes persistent pointer IDs from changing indices. [Android multi-touch](https://developer.android.com/develop/ui/views/touch-and-input/gestures/multi).

**P21 — Remap everywhere.** If controls are remappable, update tutorials and prompts too. Correct gameplay with stale help is still confusing. Let a player recover defaults without wiping unrelated accessibility settings. [XAG 107](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/107).

**P22 — No compulsory mashing.** Replace repeated presses or sustained holds with optional toggles/automation when execution is not the core challenge. “Accessible” controls that still demand simultaneous hold-and-adjust merely move the barrier. Preserve deliberate timing challenges where required and describe alternatives. [XAG 107](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/107).

**P23 — Sensitivity preview.** Let players test changed controls in a harmless preview or paused scene. A number without units or feedback forces trial and error in combat. Separate pointer speed from game difficulty when possible. [GAG basic](https://gameaccessibilityguidelines.com/basic/).

**P24 — Whole-flow controller use.** A controller-supported game must also let players dismiss dialogs and navigate shops/settings. Requiring a touch halfway through breaks the input promise. A genuinely touch-specific level editor can be separately labeled. [XAG navigation](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/112).

### Boards, cards and puzzles

**P25 — Board stays legible.** Keep tile labels and important states readable at the smallest supported display. Shrinking the entire desktop layout preserves geometry but loses comprehension. Reflow peripheral panels or use inspection; do not zoom the board so far out that legal moves disappear. [WWDC24](https://developer.apple.com/videos/play/wwdc2024/10085/).

**P26 — Clear legal move.** Distinguish selectable, selected and valid target states. Highlighting everything creates noise; highlighting nothing forces blind experimentation. Hide legal moves only when discovering them is an intentional puzzle. [GAG interactive elements](https://gameaccessibilityguidelines.com/give-a-clear-indication-that-interactive-elements-are-interactive/).

**P27 — Preview before commit.** Show the result of a route/card placement where the rules are supposed to be known. If randomness is deliberate, identify its boundary rather than implying certainty. Threes’ next-tile information helps planning even though entry position remains uncertain. [Threes review](https://www.pocketgamer.com/threes/review/).

**P28 — Undo for exploration.** Make reversible puzzle actions easy to undo. Punishing experimental pushes with a full restart discourages learning. Competitive daily modes may constrain undo, but state the rule before the run. Baba demonstrates undo within a demanding puzzle rather than eliminating difficulty. [TapSmart](https://www.tapsmart.com/games/baba-is-you-review/).

**P29 — Alternate route when stuck.** Let players try another available puzzle when possible. One bottleneck can cause abandonment. Linear narrative dependencies may justify locks; explain the requirement. [Baba review](https://www.tapsmart.com/games/baba-is-you-review/).

**P30 — Inspect without spending.** A first tap may select/inspect; use an unmistakable subsequent action to spend a scarce item. Hover-only tooltips from desktop leave phones without a safe inspection route. Keep confirm burden proportional to consequence. [XAG destructive actions](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/115).

**P31 — Visible effect order.** Show how ordered card effects produce the result. An unexplained total prevents learning. Offer fast-forward after repeated sequences. Derived tactical-card guidance. [XAG objective clarity](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/109).

**P32 — Readable documents.** Replace a cramped desktop work surface when necessary. Pope’s carousel sacrifices free arrangement to keep phone documents large. Do not declare pixel-perfect preservation the only faithful port; test whether the central judgment survives the changed manipulation. [Pope devlog](https://dukope.com/devlogs/papers-please/mobile/).

**P33 — Stable stats.** Keep counters aligned and use persistent labels; animate changes without bouncing the whole layout. Reigns’ four pressures provide a compact overview, but unexplained icons need an inspect/help route. More counters do not automatically mean more strategy. [Reigns review](https://www.pocketgamer.com/reigns/review/).

**P34 — Inspect accumulated complexity.** Provide a way to review active modifiers and their sources. A new player may remember the last upgrade but not a dozen interactions. Use plain rule text and contextual help rather than forcing an external wiki. [XAG objective clarity](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/109).

**P35 — Pauseable planning.** For a real-time management board, decide whether selection or inspection pauses/slows simulation. A tooltip that covers a failing station while time advances can punish reading speed. If time pressure is essential, communicate it and offer an appropriate practice mode. [Mini Metro review](https://www.pocketgamer.com/mini-metro/review/).

### Action, camera and feedback

**P36 — Early jump buffer.** Consider accepting a jump pressed shortly before landing. Discarding it can feel like a dead button. Tune the window against the intended challenge on actual mobile input; Celeste’s example is craft evidence from another platform, not a universal timing constant. [Thorson](https://maddythorson.medium.com/celeste-forgiveness-31e4a40399f1).

**P37 — Ledge grace.** Consider a short post-edge jump allowance. Strict geometric contact can conflict with a player’s perception of the character silhouette. Make forgiveness consistent, and verify it cannot bypass required level constraints. [Thorson](https://maddythorson.medium.com/celeste-forgiveness-31e4a40399f1).

**P38 — Corner handling.** Small corrections can turn an almost-correct jump into a satisfying landing. Snapping large distances would conceal bad level design. Keep correction bounds inspectable and test moving platforms, slopes and dash interactions. [Thorson](https://maddythorson.medium.com/celeste-forgiveness-31e4a40399f1).

**P39 — Distinct threats.** Separate harmful, safe and decorative silhouettes before adding effects. A tiny red accent is insufficient for a rapidly approaching enemy. Keep a second cue such as shape, outline or motion pattern; color customization is additional support. [GAG color](https://gameaccessibilityguidelines.com/ensure-no-essential-information-is-conveyed-by-a-fixed-colour-alone/).

**P40 — Automate deliberately.** Auto-attack can free attention for positioning/build choices, as Vampire Survivors demonstrates. Adding it to a precision combat game changes agency and balance; do not describe it as a cost-free control patch. Offer and test the intended mode. [Vampire Survivors review](https://www.pockettactics.com/vampire-survivors/review).

**P41 — Shared actions need predictable state.** Downwell combines jump and airborne shooting. Reuse can reduce thumb burden if players understand when the meaning changes. Unannounced context switching creates wrong actions; show the relevant resource/cooldown when it matters. [Downwell review](https://www.pocketgamer.com/downwell/review/).

**P42 — Scene versus HUD scaling.** Keep important controls comfortably sized while adjusting the world view separately. Uniform scaling can make both enemies and buttons too small. More visible world can also alter difficulty, so test board/action bounds rather than only avoiding cropping. [WWDC24](https://developer.apple.com/videos/play/wwdc2024/10085/).

**P43 — Shake and parallax.** Let players reduce nonessential motion without losing hit information. Shaking the world and HUD together can obscure aim and discomfort users. Preserve a static flash, outline or sound cue when reducing effects. [GAG background movement](https://gameaccessibilityguidelines.com/provide-an-option-to-turn-off-hide-background-movement/).

**P44 — Late-run readability.** Test the maximum practical enemy/effect density, not only the empty tutorial. Spectacle that hides the player or the next threat can ruin the build payoff. Offer opacity/effect controls where necessary; profile this scenario separately. [Vampire Survivors review](https://www.pockettactics.com/vampire-survivors/review).

**P45 — Retry rhythm.** Keep Retry stable and quick in short-run action. Repeated menus or long score animations make failure expensive in the wrong way. A dramatic narrative death may deserve pacing; an arcade loop usually benefits from an immediate return. [Super Hexagon mobile review](https://www.pocketgamer.com/super-hexagon/review/).

**P46 — Explain the hit.** Briefly preserve or highlight the relevant hazard at failure. Instant disappearance can leave the player blaming input. A replay is optional; even a stable cause label can distinguish collision, timer expiry and a deliberate sacrifice. This is derived from precision-control complaints. [Super Hexagon review](https://www.pocketgamer.com/super-hexagon/review/).

### Typography, hierarchy and local adaptation

**P47 — Plain functional type.** Reserve decorative pixel/handwritten faces for headings where needed; long card rules need readable letterforms and spacing. A consistent art direction does not require every paragraph to imitate a sprite sheet. Test the actual font at phone size. [XAG text](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/101).

**P48 — Expand text, not ambiguity.** Allow larger text or a readable inspection view without clipping effects or prices. Simply scaling a label inside a fixed box truncates the very content people asked to read. A compact overview can coexist with enlarged details. [XAG 101](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/101).

**P49 — Group labels with controls.** Align setting labels and their switches/sliders in clear rows. Wide decorative gaps make it unclear which value belongs to which control. Shared focus outlines can preserve association on a denser layout. [XAG UI context](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/114).

**P50 — Contrast across real scenes.** Check HUD text over bright snow, dark caves and busy particles. A translucent panel that works on one background can fail elsewhere. An opaque backing option often preserves both world art and readable information. [XAG contrast](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/102).

**P51 — Beyond red versus green.** Pair color with symbols, patterns or labels for rarity, teams and valid moves. Whole-screen recoloring can damage unrelated art and create new clashes. Prefer targeted controls and redundant cues. [GAG color](https://gameaccessibilityguidelines.com/ensure-no-essential-information-is-conveyed-by-a-fixed-colour-alone/).

**P52 — Complete fallback language.** Every necessary message needs a default, including errors and downloaded content. Translating only the happy path can leave blanks or failures in another locale. Engine-localized assets need equivalent fallback tests even when native resource files are not used. [Android localization](https://developer.android.com/guide/topics/resources/localization).

**P53 — Text expansion.** Test long translated card effects and button labels in the actual layout. Shrinking text to preserve an English box trades layout tidiness for legibility. Use wrapping, reflow or inspection according to the task. [XAG text](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/101).

**P54 — Localized art deliberately.** Keep functional text separate from painted backgrounds where practical. Embedded English in a tutorial image defeats string translation. Some story artwork is integral; budget localized variants rather than pretending it is language-neutral. [Android localization](https://developer.android.com/guide/topics/resources/localization).

**P55 — Meaningful focus.** Highlight focused cards/buttons with a visible shape or fill as well as color. A controller cursor that disappears among similarly colored cards prevents reliable selection. Keep focus onscreen when lists scroll. [XAG focus](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/113).

### Accessibility and sound

**P56 — Read at your pace.** Let players advance dialogue and important instructions. Automatic dismissal assumes one reading speed and uninterrupted attention. Optional auto-advance may suit repeat scenes, but key choices should remain available. [GAG text pacing](https://gameaccessibilityguidelines.com/allow-players-to-progress-through-text-prompts-at-their-own-pace/).

**P57 — Caption meaningful audio.** Represent spoken instructions and essential non-speech cues, not only cinematic dialogue. A warning hidden in sound makes silent play unfair. Place captions away from action targets and identify the speaker/source where useful. [XAG captions](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/104).

**P58 — Configurable captions.** Offer readable size/background options and preview them. Tiny decorative subtitles over a moving scene defeat the feature. Keep simultaneous speakers distinguishable; do not flood the screen with redundant ambient labels. [XAG 104](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/104).

**P59 — Independent volume.** Separate music, effects and speech where those channels matter. One master slider forces players to lose useful information to reduce fatigue. Remember settings across runs and updates. [GAG basic](https://gameaccessibilityguidelines.com/basic/).

**P60 — Sound plus another cue.** Show a visual or haptic equivalent for a timed threat or success tone. Conversely, offer nonvisual information where feasible. Multiple channels help, but identical overloaded signals do not tell the player which event occurred. [XAG cue channels](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/103).

**P61 — Haptics under player control.** Let players disable or adjust vibration while retaining the information elsewhere. Constant intense haptics can hurt or fatigue users. Reserve distinct patterns for important events rather than every particle or coin. [XAG haptics](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/110).

**P62 — Screen-reader semantics.** Name controls, current values and actions; expose a logical focus order. A canvas of pixels does not become accessible by labeling only the title menu. For a board, design meaningful navigation among pieces and state changes before claiming blind play support. [XAG narration](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/106).

**P63 — Avoid narration overload.** Announce important state changes without reading every animation frame or repeated counter tick. Offer enough context to understand selection and consequences. Repetitive speech can block the next useful cue. [XAG 106](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/106).

**P64 — Adjustable challenge.** Expose relevant barriers: speed, timing windows, damage, hints or assist modes. A generic Easy label may change the wrong thing. Describe what changes and whether scored modes differ; do not shame players for using help. [XAG difficulty](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/108).

**P65 — Story beyond sight.** For visual-only narrative beats, consider audio description or equivalent text. Subtitles cannot describe an unspoken action by themselves. Budget this during scene design; it may require authored writing, not automatic captions. [XAG audio description](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/111).

### Menus, navigation and settings

**P66 — Predictable Back.** Android Back should unwind the current overlay/screen according to the game’s navigation state. Do not exit from a shop while an inspect panel is open or consume Back forever. Engine integration must use the supported platform path; iOS still needs visible dismissal. [Android Back](https://developer.android.com/guide/navigation/custom-back/predictive-back-gesture).

**P67 — Stable menu ordering.** Keep Resume, settings and navigation in familiar relative positions. Shuffling buttons after a promotion appears creates accidental actions. A result screen can differ from pause because its task differs; repeated controls within the same task should stay consistent. [XAG navigation](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/112).

**P68 — Modal focus.** Move focus into an open dialog and keep it there until dismissal. Invisible background buttons must not remain actionable. Restore useful prior focus afterward, especially in card collections and level browsers. [XAG focus](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/113).

**P69 — Consistent input semantics.** Keep select/back behavior consistent across menus and use the active input’s prompts. A shop that reverses the confirm/cancel convention can spend currency accidentally. Do not let aesthetic themes redefine basic navigation. [XAG navigation](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/112).

**P70 — Immediate reversible settings.** Apply audio or effect changes with visible feedback and persist them. Hidden Apply buttons make a simple adjustment appear broken. Complex remapping or graphics changes may need explicit confirmation and a safe revert; state that clearly. [GAG remembered settings](https://gameaccessibilityguidelines.com/ensure-that-all-settings-are-saved-remembered/).

**P71 — Explain disabled actions.** A locked level or unavailable equip action should say what is missing. Grey alone cannot distinguish an owned item, a network failure and an unmet requirement. Keep the explanation inspectable by the supported inputs. [XAG UI context](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/114).

**P72 — Browsing position.** Preserve the player’s place after inspecting or playing a level. Returning to the beginning of a long list creates repeated work. A newly unlocked chapter can get a deliberate shortcut without silently replacing their location. Derived from consistent navigation. [XAG 112](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/112).

**P73 — Search only when needed.** A large card collection may need text search, type filters and a clear reset. A six-item inventory needs neither. Keep the empty-result message distinct from “you own no items”; this is derived information-design guidance, not a genre convention. [XAG UI context](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/114).

**P74 — External links are explicit.** Label Help/community/privacy actions that open another app. An unexpected browser switch can interrupt a run. Save/hold local state first and let the player return cleanly. [XAG context](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/114).

**P75 — Reset has a scope.** Say whether Reset restores controls, clears the run or deletes all progress. One ambiguous button is dangerous. Offer review or undo where feasible, and keep destructive reset apart from everyday settings. [XAG 115](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/115).

### Interruptions, saves and recovery

**P76 — Durable suspend.** Resume the meaningful run state after process death, not only a short app switch. Balatro’s preview report illustrates the cost of losing a portable session. Test termination after purchases, level transitions and puzzle moves; an autosave icon is not proof of durability. [Shacknews](https://www.shacknews.com/article/141549/balatro-mobile-impressions).

**P77 — Autosave at useful boundaries.** Save enough progress that a necessary stop is not a penalty. A rare manual checkpoint can exclude players who must stop abruptly. A permadeath game can still persist its legitimate current state without offering unrestricted rewind. [GAG autosave](https://gameaccessibilityguidelines.com/provide-an-autosave-feature/).

**P78 — Honest pause.** Stop local action when a pause menu promises it. For online games, explain that the world continues and keep relevant status visible. Do not let a static overlay imply safety while enemies continue attacking. Derived accessibility guidance. [GAG intermediate](https://gameaccessibilityguidelines.com/intermediate/).

**P79 — Audio interruptions.** Respond to audio focus loss appropriately and preserve state. Fighting a call or another app’s audio is poor citizenship. Distinguish temporary duck/pause from permanent loss; test reconnecting headphones rather than assuming one speaker path. [Android audio focus](https://developer.android.com/media/optimize/audio-focus).

**P80 — Local versus cloud.** Display whether progress is saved locally and whether cloud upload is pending. “Saved” without qualification can falsely promise recovery on another device. Cloud absence should not erase valid offline progress. [Google cloud save](https://developer.android.com/games/pgs/savedgames).

**P81 — Conflict choices have context.** Show chapter/playtime/time for each conflicting save and what selection replaces. “Use server?” is not meaningful to players. Keep a recoverable copy when possible; currency or competitive state needs stricter authority than casual progress. [Google cloud save](https://developer.android.com/games/pgs/savedgames).

**P82 — Guest linking is a migration.** Before replacing a cloud account with local guest progress, show both histories. Signing in should not silently wipe either. This is especially important after a reinstall or shared-device account change. [Google cloud save](https://developer.android.com/games/pgs/savedgames).

**P83 — Cross-save promises are specific.** Say whether saves transfer between devices, operating systems or distribution editions. Dead Cells’ support separates these cases; “cloud save” does not mean universal portability. Show the limitation before a player switches editions expecting continuity. [Dead Cells account support](https://playdigious.helpshift.com/hc/en/7-dead-cells/section/33-account/).

**P84 — Recovery errors name the task.** Distinguish missing assets, network trouble, corrupt save and entitlement failure. Generic “something went wrong” cannot guide recovery. Never make reinstalling the first recommendation when it may erase the only local save. [XAG errors](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/115).

**P85 — Paid content after reinstall.** Provide a clear route to recheck entitlement using the correct store account. An empty DLC list is not the same as no purchase. Preserve the save while recovery is pending. [Dead Cells support](https://playdigious.helpshift.com/hc/en/7-dead-cells/section/33-account/).

### Purchases and reward presentation

**P86 — Inspect, buy and use differ.** Make irreversible item actions distinct from inspection or rearrangement. Balatro’s drag zones demonstrate a mobile adaptation, but the zones still need clear intent and cancellation. The right design depends on consequence, not copying a gesture from a hit. [Shacknews](https://www.shacknews.com/article/141549/balatro-mobile-impressions).

**P87 — Store price is authoritative.** Use current store product data for localized price and offer details. Hardcoded dollar labels can contradict checkout. If products cannot load, show unavailable/retry rather than inventing a price or granting a guessed entitlement. [Play Billing integration](https://developer.android.com/google/play/billing/integrate).

**P88 — Pending is not failure.** Distinguish pending approval/payment from canceled or completed purchases. Let a player continue unrelated play while appropriate. Grant paid content only through verified purchase handling; a UI callback alone is not durable proof. [Play Billing](https://developer.android.com/google/play/billing/integrate).

**P89 — Rewarded ads describe the trade.** State the action and reward before opt-in. Do not disguise an ad as the normal Continue button. Declining should preserve the promised unboosted path; the exact ad format has its own policy rules. [AdMob rewarded policy](https://support.google.com/admob/answer/7313578?hl=en).

**P90 — Earned versus bonus.** Show base rewards as already earned and the optional ad bonus separately. A screen that makes all rewards look conditional can mislead players. Keep both values legible and stable through the ad flow. [AdMob rewarded policy](https://support.google.com/admob/answer/7313578?hl=en).

**P91 — No ad available.** Make unavailable ads an explicit state and retain a normal route forward. An endless spinner or dead reward button punishes players for inventory/network conditions. Do not promise a reward the integration cannot deliver. [AdMob rewarded policy](https://support.google.com/admob/answer/7313578?hl=en).

**P92 — Purchase recovery survives return.** Reconcile completed purchases when the app resumes or reconnects. A player may pay while the game loses focus or process state. The UI should show checking/owned reliably instead of asking them to pay again. [Play Billing](https://developer.android.com/google/play/billing/integrate).

**P93 — Completion can be enough.** End a finite story cleanly, offer replay/credits, and make further content optional. Treating Florence-like short experiences as failed daily-retention products distorts their value. Measure satisfaction and recommendation as well as session counts. [Florence review](https://www.pocketgamer.com/florence/review/).

### Community, maintenance and long-term use

**P94 — Explain the score.** Show what a result measures and which mode produced it. A best score without rules/version context can become misleading after balance changes. Use separate boards when rules differ substantially; this is derived fairness guidance. [Threes review](https://www.pocketgamer.com/threes/review/).

**P95 — Daily challenge identity.** Name the challenge/date and preserve the run’s identity if midnight passes. Do not silently replace a board during play. Define time-zone/offline policy; daily modes are optional. [Mini Metro review](https://www.pocketgamer.com/mini-metro/review/).

**P96 — Community capacity.** Launch official chat/UGC only with moderation and support capacity. An unstaffed official channel can create unmet expectations. Dinosaur Polo Club explicitly discusses staffing across time zones as a reason not to rush a Discord server. [Developer support](https://dinopoloclub.com/support/mini-metro/).

**P97 — Useful feedback route.** Let players report device/build, relevant save context and a short description without retyping everything. Ask consent before attaching personal data. Accessibility feedback needs a route users can operate outside the failing game screen. [GAG basic](https://gameaccessibilityguidelines.com/solicit-accessibility-feedback/).

**P98 — Preserve learned settings.** Updates should retain accessibility, control placement and volume choices unless incompatible. A changed default can make a previously playable game inaccessible. If migration fails, explain the reset and offer recovery. [GAG basic](https://gameaccessibilityguidelines.com/ensure-that-all-settings-are-saved-remembered/).

**P99 — Long-term rule reference.** Keep current help/version notes aligned with shipped mechanics. An external guide for an older build can make a correct game look broken. Highlight consequential changes when returning, without repeatedly blocking play for minor release notes. [XAG objective clarity](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/109).

**P100 — Test comfort over time.** Include extended runs and returning players, not only a five-minute first impression. NME’s Dead Cells review reports hand strain despite strong gameplay. Watch for repeated stretch, grip changes and fatigue; control success once does not establish comfort for hours. [NME](https://www.nme.com/reviews/dead-cells-review-a-good-mobile-port-of-an-excellent-roguelike-game-2699135).


## Historical craft: small art does not mean small work

**Hundreds, 2013:** Adam Saltsman describes direct multitouch and experiments that teach each mechanic. Procedural minimalist art reduced asset work but exposed every rendering defect. The team repeatedly rebuilt rendering; older hardware and scope growth strained its schedule. More than 100,000 first-month sales barely covered the year-plus production, by his account. Its touchscreen design also limited straightforward desktop reuse. These are historical developer disclosures, not current market averages. The useful tension: design for fingers, but budget the resulting port limits, iteration and testing. “No marketing budget” still included press outreach, trailers and early contact with Apple. [Full postmortem, printed pp. 34–39](https://media.gdcvault.com/GD_Mag_Archives/GDM_May_2013.pdf).

**Threes, 2012–14:** The published design correspondence shows a tester trying to position individual tiles when the rule moved the board together; iterations changed presentation, teaching and affordances. Zach Gage questioned a dark palette and shrinking high-value numerals. The authors report 14 months of development, despite an early mockup resembling the final game. Treat recognizable appearance and understandable interaction as separate milestones. These are selected historical correspondence, not a controlled study. [Development emails](https://asherv.com/threes/threemails/).

## Long-term use and disagreements

**Downwell:** Gamereactor's November 2015 review praises its mechanics and short mobile sessions while finding controller play more confident and some touch deaths frustrating. [Review](https://www.gamereactor.eu/downwell-review/). Japanese player reviews collected by AppReview include years of enjoyment, complaints that fingers hide descending hazards, difficulty distinguishing dangerous red enemies, and missed simultaneous inputs. Dates are relative and builds unspecified; the aggregator is evidence of complaints, not independently reproduced defects. Translate these into playtests for finger occlusion, color-independent hazards and multi-touch under load. Do not label all touch players dissatisfied. [Japanese reviews](https://appreview.jp/app/5081468154e29149efab0272278381bd).

**Slice & Dice:** A 2026 patient-gamers discussion praises reversible experimentation, short tactical fights and resuming after decisions. A dissenting player reports roughly 100 hours in the free version yet resists paying a mobile price and finds characters impersonal. Enjoyment, time spent and conversion are distinct. Claims about perfect saving, win rates and a final update are unverified player assertions; current store metadata lists 3.2.19, so the post's “last update 3.0” claim is stale. [Discussion](https://www.reddit.com/r/patientgamers/comments/1whsvdw/slice_dice_my_favorite_roguelite_of_all_time/).

## Direct visual inspection

Inspected publisher-selected US App Store screenshots on 2026-11-08. Images support appearance only; they do not verify current interaction, readability on a physical phone or performance. Marketing words composited onto screenshots are not gameplay HUD.

- **Threes:** Pale teal board; red/blue base tiles; white merged tiles; heavy black numbers; tiny faces along yellow tile bases. Menu and challenge sit above the board. The personality lives inside the pieces, leaving the grid readable. The promotional diagram separates merging from a full game. [Gameplay image](https://is1-ssl.mzstatic.com/image/thumb/Purple114/v4/0c/21/ae/0c21ae08-5ca1-5692-68ed-e0c5ec3ddaa2/mzl.mbdynpch.png/392x696bb.png).
- **Mini Metro:** Cream graph-paper field; thin colored routes; outlined station shapes; quiet time/score at top right; tools at opposite edges. Its hierarchy makes infrastructure the picture. Routes overlap, so color alone should not carry all interaction feedback. [Image](https://is1-ssl.mzstatic.com/image/thumb/Purple211/v4/cd/03/20/cd03200e-02b6-3d75-4ddd-06220b3748dd/en-US-iOS-5.5-in-2.png/406x228bb.png).
- **Downwell:** Narrow black playfield, jagged white terrain and red accents, bold status bars above action. Sparse palette supports contrast, while dense terrain and effects can still compete with enemies. This frame does not show a complete touch-control layout. [Image](https://is1-ssl.mzstatic.com/image/thumb/Purple123/v4/52/d3/d7/52d3d79d-d770-6839-b67b-72314821f56f/mzl.ysirshsx.jpg/392x696bb.jpg).
- **Slice & Dice:** Portrait composition splits a tier-choice panel above party-versus-enemies rows. Colored borders group character roles; health pips and die faces repeat compactly. Pixel labels establish character but deserve minimum-size/localization checks. [Image](https://is1-ssl.mzstatic.com/image/thumb/PurpleSource211/v4/62/c5/b5/62c5b557-b8e4-cf6e-a19d-739f82939250/505669e4-df22-4fe1-9a98-aebca24c2cf9_1242x2208_5.png/392x696bb.png).
- **Baba Is You:** Tiny objects and rule words occupy a dark landscape board; a contrasting left rail exposes pause, restart and undo. Text is part of the game state, so localization and zoom affect mechanics as well as menus. The inspected level uses deliberately dark colors; it does not establish readability outdoors. [Image](https://is1-ssl.mzstatic.com/image/thumb/PurpleSource124/v4/2d/6e/18/2d6e18ad-3b45-c614-43ee-cea16727cbcb/3cfcc1cf-19d8-4a92-ba2d-473754734ec8_2208-1242.png/406x228bb.png).
- **Papers, Please:** Portrait stacks the queue, visitor and large open rulebook; document tabs sit at the bottom. Muted olive/brown pixel art preserves bureaucracy's mood while giving the active document most space. This is a recomposed phone workspace, not a miniature desktop screenshot. [Image](https://is1-ssl.mzstatic.com/image/thumb/PurpleSource122/v4/09/65/79/0965794b-1151-76ed-43c1-72ded05a04b3/0c515c4d-a03f-4481-826d-99fb518d2f3a_PapersPlease-Phone-1242x2208-en-03-Booth.png/392x696bb.png).
- **Vampire Survivors:** The promotional frame shows dense pixel enemies and pickups around a central character on green terrain. Large added marketing text obscures much of the action; use it for art direction only, not HUD or combat-readability assessment. [Image](https://is1-ssl.mzstatic.com/image/thumb/Purple112/v4/97/ed/d3/97edd3a4-b48a-3961-8042-9595ede0782d/7b0cb6c2-047c-4847-bebc-97cdaba45ebb_AppStore_5.5_-_BE_THE_BULLET_HELL.png/392x696bb.png).

**Recorded motion:** Inspected 17 evenly spaced frames from Threes' official 30-second animated GIF. It begins with separate 1 and 2 tiles, illustrates merging, then introduces a hand/phone and changing scenery while the board stays central. The animation teaches one rule before showing portable play. This is a historical promotional animation, not captured live input; samples do not establish frame pacing or gesture latency. [GIF](https://asherv.com/threes/images/THREES_trailer.gif), [press kit](https://asherv.com/threes/presskit/). The kit's old iOS 7 claim is historical; current listing metadata says iOS 12.

## Current listing evidence

Checked public US Apple lookup metadata and opened Google Play listings on 2026-11-08. These establish listings, not installation on every account/territory or tested device reliability. Existing apps' low published runtime minima are not new-upload SDK requirements. Android Play pages may vary price and metadata by region; no global price ranking follows.

| Game | Apple version / published minimum | Android listing |
|---|---|---|
| Threes! | [App Store](https://apps.apple.com/us/app/id779157948) · 3.3 · iOS 12.0 | [Google Play](https://play.google.com/store/apps/details?id=vo.threes.exclaim) |
| Mini Metro | [App Store](https://apps.apple.com/us/app/id837860959) · 1.57 · iOS 13.0 | [Google Play](https://play.google.com/store/apps/details?id=nz.co.codepoint.minimetro) |
| Downwell | [App Store](https://apps.apple.com/us/app/id1032708262) · 1.0.72 · iOS 8.0 | [Google Play](https://play.google.com/store/apps/details?id=com.devolver.downwell_rerelease) |
| Slice & Dice | [App Store](https://apps.apple.com/us/app/id6449848963) · 3.2.19 · iOS 13.0 | [Google Play](https://play.google.com/store/apps/details?id=com.com.tann.dice) |
| Vampire Survivors | [App Store](https://apps.apple.com/us/app/id6444525702) · 1.16.111 · iOS 13.0 | [Google Play](https://play.google.com/store/apps/details?id=com.poncle.vampiresurvivors) |
| Baba Is You | [App Store](https://apps.apple.com/us/app/id1517281887) · 1.11 · iOS 9.0 | [Google Play](https://play.google.com/store/apps/details?id=org.hempuli.baba) |
| Papers, Please | [App Store](https://apps.apple.com/us/app/id935216956) · 1.4.12 · iOS 11.0 | [Google Play](https://play.google.com/store/apps/details?id=com.llc3909.papersplease) |

## Code craft beyond engine choice

Robert Nystrom's accessible *Game Programming Patterns* chapters remain useful for implementation reasoning. Separate simulation steps from rendering and cap catch-up after a stall. Commands can support undo and replay; correctness still needs captured state and controlled randomness. Pool frequent short-lived objects when profiling warrants it, with explicit exhaustion and reset behavior; oversized pools retain memory. These are design techniques, not benchmarks or a reason to replace an engine's working loop. [Game loop](https://gameprogrammingpatterns.com/game-loop.html), [command](https://gameprogrammingpatterns.com/command.html), [object pool](https://gameprogrammingpatterns.com/object-pool.html).

Derived 2D application: a turn-based board can store compact logical state independently of tween progress. A bullet-heavy action game needs bounded simulation work and an explicit rule for exhausted cosmetic versus gameplay pools. Replaying input on different frame timings is not proof of deterministic outcomes. Validate state hashes and version save/replay formats; cross-platform floating-point physics needs separate verification.

## Accessibility preserves play, not merely access

A CHI 2025 study interviewed 32 experienced blind/low-vision mobile players in China. Participants valued mastery and social connection, but described repetitive simplified games, inaccessible first screens and fragile third-party aids. This qualitative sample does not measure the whole market or prove a commercial uplift. It supports a specific design goal: preserve meaningful decisions while changing how players perceive and operate them. [Study, methods and findings](https://arxiv.org/html/2502.09866v1).

**BROK the InvestiGator** demonstrates a substantial 2D accessibility branch: scene narration, adapted puzzles, positional fighting audio, repeatable instructions and optional skips. The 2023 independent coverage reports the work and player responses; it is not a mobile hands-on review. Its accessibility consultant's 2024 AppleVis entry reports iPhone/iOS 17 testing and a built-in narration mode used with VoiceOver off; narration is English-only in that entry. Distinguish screen-reader integration from a game-owned spoken interface, and test entry into the mode itself. [Can I Play That?](https://caniplaythat.com/2023/03/13/blind-accessibility-finds-its-way-to-brok-the-investigator/), [AppleVis](https://www.applevis.com/comment/163329).

The developer's July 27, 2026 Android update combines higher-resolution characters, texture compression, smaller files, SDK 36 and Turkish localization. A 2D art style does not remove ongoing platform or asset work. The notes report intended changes, not measured memory savings or performance. [Developer update](https://cowcat.itch.io/brok/devlog/1606525/android-version-updated).

## Narrative and asset production costs

Joseph Humfrey's 2016 account explains how ink grew around working writers and how large, structurally intertwined scripts made translating Sorcery!/80 Days difficult. Historical lesson: localization of branching prose includes logic and creative authorship, not merely replacing UI strings. It does not establish today's translation support or prove that every narrative needs ink. [Developer account](https://www.gamedeveloper.com/design/open-sourcing-80-days-narrative-scripting-language-ink).

Android's texture guide explains atlas sharing, filtering and GPU compression. Derived 2D consequence: choose atlas groups by scene residency and material compatibility, not a blanket “one giant atlas” rule. Pixel art may need nearest filtering; downscaled painted sprites need their own aliasing tests. Atlas packing does not eliminate transparent pixels, upload stalls or overdraw. A 2048×2048 RGBA8 image is 16 MiB before mipmaps; PNG download size does not predict decoded GPU memory. That arithmetic is uncompressed storage, not a measured engine allocation. [Texture guidance](https://developer.android.com/games/optimize/textures).

## Saves, simulation and cross-device promises

**Stardew Valley's experimental mobile multiplayer** illustrates the gap between sharing code and supporting an experience. The official guide exposes IP-based co-op on regular iOS/Android, excludes the Apple Arcade edition, requires matching versions and recommends a strong phone on a local network with a PC host. It explicitly warns about mobile interruptions and experimental save risk. This is a scoped experimental capability, not a normal seamless cross-play promise. [Developer guide](https://www.stardewvalley.net/mobile-multiplayer-guide/).

Save migration also limits rollback: the 1.6.9 beta announcement says a farm saved in that version cannot load in 1.6.8. Official recovery instructions depend on older copies and intact files. Derived release guidance: preserve a known-good pre-migration save, validate writes before replacing it, make cloud conflicts explicit and distinguish suspend snapshots from permanent progression. A rollback binary alone is not a recovery plan. [Version boundary](https://www.stardewvalley.net/stardew-valley-1-6-9-public-beta/), [recovery guide](https://www.stardewvalley.net/missing-corrupt-save-file-troubleshooting-guide/).

For an original game, define four contracts separately: purchases owned, durable progression, current run and competitive results. A local single-player puzzle can remain playable offline. Paid currency needs idempotent transaction handling; a leaderboard needs its own anti-cheat decision. Never choose “latest save wins” for everything merely because device timestamps are available. Preserve competing saves until their intended merge is known; a player may have advanced different campaigns on two devices.

## Commercial conclusions

A small 2D game can sustain a small team through paid copies, a free sample with a permanent unlock, restrained ads, expansions or a distribution contract. Those models make different games viable. No public evidence here establishes a universally best model, price or retention target. Famous ports bring an existing audience; their mobile results are poor forecasts for an unknown mobile-first release.

Make the core action understandable in a short clip; observe that intended players return voluntarily, or finish satisfied; price the whole production and support obligation. Track installs, repeat play, receipts, profit and owner workload separately. A finite puzzle can succeed when satisfied players finish it. A daily game can retain players yet fail to pay its makers.

## Measured commercial cases

| Case and period | Evidence | Useful conclusion; limit |
|---|---|---|
| **Threes free edition, June–July 2015** | Asher Vollmer reported that the additional ad-supported version doubled daily revenue. The paid edition remained. [Reported disclosure](https://www.gamedeveloper.com/business/-i-threes-i-devs-double-daily-income-with-free-version). | A free route can expand a paid game's audience. This was a before/after result for a famous, award-winning game, not randomized proof that ads double revenue. No lifetime profit or acquisition-cost result was disclosed. |
| **Card Crawl, first year to March 2016** | Developer's anniversary account, preserved in a translated republication, reports about $100,000 revenue plus about $2,000 from Amazon; 76% iOS, 24% Android. Android had 124,613 installs and 12,236 buyers; reported conversion 4.4% after one day, 8.6% after 15, 9% after 30. [Republished account](https://wnhub.io/news/other/item-11068). | A bounded demo and permanent unlock can work for a compact card game. Android shipped later and used a different model; platform shares do not isolate willingness to pay. Cumulative buyers/installs are not identical to a 30-day cohort rate. No experiment or general 9% benchmark. |
| **Once Upon a Tower, two-week experiment, publication undated** | Pomelo tested interstitial placement across the player base versus a segment; Firebase reports +25% AdMob revenue, +35% IAP and almost no retention effect. Purchases removed ads. [Vendor case study](https://firebase.google.com/case-studies/pomelo-games). | Test a disputed model with retention and stability guardrails. This is a 2D-play mobile game; rendering style is not the mechanism tested. Sample sizes, intervals, allocation and long-term results are absent. The founder's theory that ad removal drove IAP is plausible, not experimentally isolated. |
| **Balatro mobile, September–November 2024** | AppMagic estimated $3m net mobile revenue in two months, excluding Arcade: roughly $1.7m Google Play/$1.36m App Store; 52.9% US. The reported price was $9.99. [Report](https://app2top.com/news/balatro-earned-3-million-on-mobile-devices-274722.html). | Paid 2D mobile games are commercially possible on both stores. These are modeled proceeds, not audited profit; established PC/console sales preceded mobile. A post-nomination rise cannot prove an awards effect. Do not multiply present list price by estimated installs to infer profit. |
| **You Must Build a Boat, July 2015** | Luca Redwood said it passed his modest lifetime sales goal in ten days; iOS led, Google Play might pass it, and Steam was smaller. [Developer interview](https://www.gamedeveloper.com/business/designing-i-you-must-build-a-boat-i-amid-the-rising-tide-of-game-releases). | Android premium sales need not be negligible. The game inherited 10000000's audience; the goal and exact unit figures were not published. This contradicts a blanket “premium Android never works,” not present-day market shares. |
| **Mini Metro, July 2018** | Studio co-owner clarified 1.3–1.4m cumulative copies across platforms, having reached 1m in July 2017. [Direct clarification](https://www.pcgamesinsider.biz/news/67489/mini-metro-has-actually-sold-close-to-14m-copies/). | A readable systems game can support a long catalog life. Cross-platform units do not reveal mobile revenue, margin, retention or contemporary acquisition cost. |
| **Ridiculous Fishing, August 2013** | Contemporary reporting relays the founders' GDC Europe disclosure of 300,000 copies at $3; the article multiplies these to $900,000 sales. [Report](https://www.destructoid.com/ridiculous-fishing-brings-in-nearly-1m-since-launch/). | Recognizable, polished mobile originals can sell. This gross arithmetic predates the Android launch and omits tax, fees, collaborators and cost. Historical premium success is not a 2026 forecast. |

The Card Crawl original URL failed through the browser and direct TLS request; the nearby Pocket Gamer report independently confirms that the disclosure existed but repeats the same underlying numbers, so it is **not an independent financial audit**. The translated account supplies the missing platform/model context. Treat exact terminology and accounting basis as developer-reported, not reconstructed. [Contemporary coverage](https://www.pocketgamer.com/card-crawl/its-card-crawls-first-anniversary-so-tinytouchtales-released-sales-numbers-spoil/).

### What changes revenue, and what the evidence cannot establish

**Separate ads from the action.** In the 2015 Threes interview, Vollmer describes ads exchanged for stored play credits, usable later offline. He rejected banners that encouraged mistaken taps. This is an explicit design rationale, not measured superiority over every ad format. The credit model also imposes a play gate: test whether that fits the audience rather than assuming all optional-looking ads feel optional. [Interview](https://www.gamedeveloper.com/business/mending-the-developer-player-relationship-with-i-threes-i-free-to-play).

**Optional rewards can preserve the full game.** Poncle's January 2023 mobile explanation describes a full offline game with optional ad buttons, no interruptions, portrait/landscape and touch/controller support. Existing success and demand make this a poor forecast for a new mobile-only studio; the public account does not allocate costs by platform. The original Steam page would not expose its body here; the contemporary report reproduces the developer statement. This supports the chosen contract with players, not profitability or a claim that the present edition has no DLC. [Reported developer statement](https://www.pocketgamer.biz/vampire-survivors-developer-takes-new-approach-to-monetisation/).

**Do not assume cheaper means more profitable.** Card Crawl's June 2015 four-day $0.99 sale reportedly produced 4,758 downloads and $3,248 studio revenue, below the developers' $10,000 hope. Afterward it raised the regular price to $2.99 and reported roughly $350 daily over a few days. Update, promotion, timing and price changed together; this cannot identify price elasticity. [Contemporary report](https://www.pocketgamer.com/card-crawl/card-crawl-will-be-bringing-its-nifty-quickfire-dungeon-crawling-to-android-soon/).

**Test honest store assets.** Google supports randomized listing tests of graphics and localized text, reporting acquisitions and one-day retention. Its guidance recommends one changed asset at a time and at least a week to include weekday/weekend effects. Neither is sufficient statistical evidence by itself. For a small title, insufficient traffic may make playtesting and qualitative comprehension tests more useful than many underpowered variants. [Google listing experiments](https://google.play/business/store-listing-experiments/).

**A video is not automatically better.** Apple's own product-page cases include Simply Piano's original screenshot-only page beating a video treatment by 3% over 12 days, and Peak's brain icon beating robot variants by 8% over 44 days. These are adjacent app examples, not game effect estimates. Their role is to refute a universal asset rule; test the actual game, locale and audience. [Apple product-page optimization](https://developer.apple.com/app-store/product-page-optimization/).

For a new game, test comprehension of the core move, time to the first satisfying outcome, retry friction, control errors, failed-save recovery and a plainly explained offer. Define success before reading results. Keep a stable control, record eligibility and exposure, wait for the intended retention window, inspect refunds/support complaints, and avoid changing balance or acquisition targeting mid-test. This is derived experimental guidance; the public cases do not supply enough raw data to recalculate confidence or predict the best intervention.

## Business-model fit

| Model | Fits | Costs and failure modes |
|---|---|---|
| Paid download | Distinct finite puzzles, trusted premium ports, arcade mastery with enough depth | Purchase comes before proof. Store assets, reputation, reviews and recommendation matter. Budget maintenance after launch; a single payment does not fund unlimited new content. |
| Free sample + permanent unlock | Card/board/puzzle games with a useful self-contained sample | Define the boundary before play. Preserve trial progress. Test purchases and restoration. Free installs increase support load without guaranteeing buyers. |
| Free core + optional rewarded ads | Replayable short sessions where an extra reward does not destroy balance | Ad availability, consent, inappropriate creatives, callback failure and network delay become product work. Never make a declined or unavailable ad trap the player. |
| Free core + expansions | Systems games with separable new content and a satisfying base | Design versioned save compatibility, ownership/restoration and a sustainable content pipeline. Do not move already purchased content behind a new paywall. |
| Cosmetic IAP | Games whose players enjoy identity, collection or social display | Small single-player games may have little demand. Production and merchandising cost can exceed income; appearance must not conceal hazards or imply gameplay advantage. |
| Energy, consumables, paid boosts | Products explicitly designed around recurrent spending and live operation | They change balance, support, trust and analytics requirements. A prototype that is fun without them does not establish that it will remain fair with them. |
| Arcade/Play Pass/Netflix distribution | Contract-backed premium experiences or catalog licensing | Deal access, exclusivity, milestones, required targets, payment timing, removal and save migration matter. Subscriber count is not developer revenue. |
| Direct recurring subscription | A game with a credible continuing service/content promise | A poor default for a small finite game. Requires recurring value, cancellation clarity, renewal support and enough production capacity. No evidence here supports subscription merely because recurring revenue is attractive. |

These are derived fit judgments from the cases, not new user decisions. A game can offer different editions or models on each store, but it then owns the confusion, support and migration work. Mini Metro's current FAQ calls Mini Metro+ functionally identical to the paid game while explaining separate-store purchases and platform-dependent refunds. It also declines to launch an official Discord before staffing and moderation are ready. A community is an operating commitment, not a free retention feature. [Developer FAQ](https://dinopoloclub.com/support/mini-metro/).

### Subscription distribution: promise, disagreement and contract risk

Apple's accessible “From concept to catalog” video transcript describes funding, producer support and monthly bonus-pool payments, with many projects requiring little or no developer investment. It also distinguishes Arcade originals from existing “Greats”; the consumer offer has no ads/IAP. This is the platform's account, not an independent payment audit. [Transcript directly read](https://developer.apple.com/videos/play/meet-with-apple/244/).

Mobilegamer's February 2024 interviews report mixed experiences: some studios credit Arcade with their survival; others describe falling bonuses, cancelled projects and opaque qualifying-session calculations. Its anonymous sources also describe Netflix's then-generous upfront deals without recurring bonuses. These are dated reports, not today's contract terms. [Original reporting](https://mobilegamer.biz/inside-apple-arcade-axed-games-declining-payouts-disillusioned-studios-and-an-uncertain-future/).

No public rate card resolves the difference because deal terms, performance and obligations vary and the underlying contracts are private. Compare a concrete offer's guaranteed cash, timing, recoupment, exclusivity, porting scope, update duties, termination and post-removal rights. Model zero unguaranteed bonus income for survival planning. Apple's current funding description and the earlier complaints can both be true for different deals and periods.

## Failure and sustainability lessons

**Catalyst: competent production without a strong market reason.** Kevin John's February 2015 postmortem reports slow sales on both stores after five months of development. Small scope and simple art helped him ship, but the game read as another matching puzzle; “no ads or IAP” was not enough identity. He also describes engine support and startup problems. His conclusion that premium mobile was dead was an opinion from one failure, contradicted by other paid games in this report. The useful lesson is to test the hook and distribution before full production. [Developer postmortem](https://www.gamedeveloper.com/business/-quot-premium-mobile-games-are-dead-quot-catalyst-postmortem).

**Punch Quest: initial monetization failure, later recovery.** In November 2012, Rocketcat reported only low five-figure revenue from over 600,000 downloads; more visible IAP and new offers helped only briefly, so it temporarily became paid. Do not reduce this to a small buy-button problem: the developers said they had already tried changing it. [Contemporary developer interview](https://toucharcade.com/2012/11/14/amid-slumping-revenue-punch-quest-switches-to-a-paid-game/). A 2017 retrospective says revised economy/IAP eventually let it return to free and become a steady success, according to Kepa Auwae. The same critic had kept it installed for years, praising move combinations and replay depth. This is a recovery case, not permanent proof against F2P; raw profit and retention data are unavailable. [Long-term review](https://toucharcade.com/?p=218803).

**Outwitters: featuring and love can miss the budget.** An October 2012 interview reports roughly $300,000 development cost, 560,000 downloads and $40,000 revenue despite Apple's prominent placements. At launch a player could spend only $4. This is an iOS-era comparison; it does not establish present availability or a general spending cap. Budget, audience and offer must agree. Raising spend ceilings is only one possible response; reducing scope or charging upfront are alternatives. [WIRED interview](https://www.wired.com/2012/10/outwitters-sales-disaster/).

**HoloVista: awards do not establish a viable launch.** This is an adjacent iOS-only, 3D-scene narrative example, not a core 2D cross-platform exemplar. Its creators' 2021 postmortem explicitly says it did not become the hoped-for premium exception despite an Apple Design Award. They had compared themselves with games that possessed established reputations, publisher support or simultaneous PC/console launches. Use it to correct selection bias, not to infer 2D unit economics. [Creator postmortem](https://www.gamedeveloper.com/design/postmortem-aconites-holovista).

**Mini Metro: a small visual footprint can hide years of work.** The developers' 2016 account credits the free web prototype and Early Access with audience and runway, but records repeated scope expansion, mobile/desktop effort splitting and prolonged polish. They had spent a year expecting completion in two or three months. The postmortem predates mobile release; its Unity Web Player/Futile implementation is historical, not a recommended current stack. [Developer postmortem](https://www.gamedeveloper.com/audio/postmortem-dinosaur-polo-club-s-i-mini-metro-i-).

**You Must Build a Boat: design monetization around the experience.** Redwood says the project grew from an update into a three-year sequel, risking much of the prior game's proceeds. He rejected purchases that would bypass its progression. Touch and mouse players also needed different difficulty curves. Small overhead and multi-platform sales helped, but cannot erase the owner's time cost. [Developer interview](https://www.pocketgamer.biz/making-of-you-must-build-a-boat/).

**Balatro: financial success does not prevent burnout.** LocalThunk's September 2025 post explains that balance work and the mobile port followed launch without recovery; the promised 1.1 update slipped while he returned to a slower pace. Do not turn this dated announcement into a claim about today's release status. The planning lesson is to fund a maintainable pace and avoid promising an expansion date before understanding its workload. [Developer account](https://localthunk.com/blog/im-slow).

**Part Time UFO: quality does not guarantee permanent access.** HAL's own Japanese announcement ended mobile distribution and all services on October 22, 2024 at about 10:00; it gave no cause. The Switch edition remained. Do not label this a commercial failure or invent a maintenance-cost cause. It illustrates the need for preservation, clear retirement communication and offline survivability. [Official retirement notice](https://www.hallab.co.jp/news/detail/20241022/).

**Cloning and publicity have opposing costs.** Rami Ismail's 2015 talk, reported by Mark Brown, says secrecy left Ridiculous Fishing vulnerable to competing publicity, while streaming the next game's production consumed enormous development time. His claimed opportunity costs are retrospective estimates, not measured lost sales. Share a clear playable identity and evidence of authorship; do not assume either total secrecy or broadcasting every work hour solves imitation. [Talk report](https://www.pocketgamer.biz/rami-ismail-mistakes/).

### Existing audiences must remain visible in comparisons

LocalThunk's timeline records a quiet free beta, growing creator coverage, a spike after Dan Gheesling streamed it, and publisher interest before Balatro's commercial release. These precede its mobile port. This supports a plausible distribution chain; it does not prove a replicable recipe for going viral. His earlier hobby work, savings and partner's employment also differ from a studio that must pay several salaries immediately. [Developer timeline](https://localthunk.com/blog/balatro-timeline-3aarh).

Do not infer that a successful mobile port proves the mobile store created the audience. Conversely, do not treat a desktop audience as guaranteed mobile conversion: touch fit, price expectations, saves, duplicate purchases and device performance still matter. For unfamiliar mobile-first games, test a small playable build with the actual target audience and an honest payment offer before scaling content or advertising.

## Full economics

Use a per-store, per-country, per-model cash model. Derived accounting structure:

`contribution = actual store/ad/license receipts − paid acquisition − variable infrastructure − transaction/fraud/refund costs not already deducted − variable support/content cost`

`planning cash surplus = contribution − remaining owner/employee pay − contractors − tools/devices/localization/QA − fixed infrastructure/admin − maintenance reserve`

Allocate each cost once: support/content labor counted above must not reappear in payroll or contractor costs. A maintenance reserve is a planning allowance, not automatically an accounting expense. This cash model is not formal financial reporting. Do not subtract the store fee twice from a “net revenue” figure. Do not count unpaid owner labor as zero when asking whether the business replaces a job. Profit before the owner's wage and sustainable household income answer different questions.

**Premium planning example, invented inputs.** If a retained sale contributes $4 after deductions and variable costs, recovering $80,000 of production and support requires 20,000 retained sales. If the expected contribution is $2, it requires 40,000. These are arithmetic scenarios, not market benchmarks. Use the weighted realized price after regional pricing, discounts and refunds; list price is the wrong denominator.

**Free-to-play acquisition.** Compare expected net lifetime contribution per acquired player with fully loaded acquisition cost. Include creative production/testing, attribution fees, invalid traffic, mediation differences, support and future content. Observe payback time and cash runway, not only a promising lifetime extrapolation. Separate organic users, existing fans, paid cohorts, countries and devices; cheap installs can have lower monetization, while expensive markets can still lose money.

**Ad revenue.** Forecast impressions from voluntary opportunities actually completed, fill rate, consent/age eligibility, region and realized eCPM. A network's case-study CPM is not a rate card. Model no fill and offline play. A tiny title may not produce enough impressions to fund large SDK, privacy and support obligations. Avoid rewarded mechanics that require an ad to be available for the player to continue.

**Content and support.** Count new level/card production, balancing, localization, assets, rating updates, QA across old saves, purchase failures, community moderation and release work. Procedural content reduces hand-authored quantity but adds generation, solvability, fairness and seed-versioning work. A short game with a clear ending may cost less to support than a perpetual daily schedule.

**Publisher/distribution agreement.** Model advances as financing tied to obligations and recoupment, not automatically extra profit. Ask which costs recoup before royalties, who owns IP/source/accounts, who pays ports and QA, how reports can be checked, what happens on termination and how long exclusivity lasts. Actual contract terms are needed; public success stories cannot fill them in.

**Localization and region.** Buy translation and device coverage where the concept, payment access, expected receipts and support capacity justify them. Low-text 2D action can be cheaper to localize than card rules, humor or narrative. Test localized store assets, font shaping, prices and purchase paths together. Card Crawl and Balatro show different platform splits and audiences; neither supplies worldwide prevalence.

**Infrastructure.** A fully offline premium game may need only a website, support and release tooling; cloud saves and leaderboards add ongoing service and abuse costs. Real-time multiplayer adds servers, geographic latency, matchmaking population and moderation. Do not add live-service dependencies merely to justify a subscription. Preserve basic paid play if optional services fail.

## Current store and distribution rules that change economics

**Apple standard small-business program.** Qualified enrolled developers receive 15% commission on paid apps and IAP. Eligibility uses up to $1m prior-year proceeds across associated accounts; crossing the threshold changes future sales. It is not an automatic universal 15% rate and is not the full set of regional alternative terms. [Apple program, checked 2026-11-08](https://developer.apple.com/app-store/small-business-program/).

**Google changed its fee structure in 2026.** In EEA/UK/US from June 30 and Australia/Japan from September 30, the published table separates service and billing fees, new/existing installs and program eligibility. For the first $1m annual earnings it shows 10% service plus a 5% Google Play billing fee where applicable. Standard non-recurring transactions show 20% for new installs or 25% for existing installs before applicable billing fees; external-link treatment differs. Remaining markets retain older schedules until their rollout. [Current overview](https://support.google.com/googleplay/android-developer/answer/112622). The detailed page defines an install date using first Play installation, or first Play update if initially installed elsewhere; it schedules Korea for December 31, 2026 and remaining markets for September 30, 2027. Treat future dates as announced. [Detailed table and rollout](https://support.google.com/googleplay/android-developer/answer/16954621).

**External payment is not automatically fee-free or simpler.** Model applicable program terms, service charges, payment processing, fraud, taxes and support before comparing checkout routes. Apple's current guidelines distinguish US external-link treatment from other storefronts; its general IAP rules also require restoring restorable purchases, prohibit purchased currency expiration and require disclosed odds for paid randomized virtual items. The relevant region and distribution terms must be checked when shipping. [Apple review rules](https://developer.apple.com/app-store/review/guidelines/).

**Refunds.** Apple directs eligible refund requests through Report a Problem; cancellation and refund are different actions. Google says refunds depend on purchase, timing, method and location, and developers can help resolve purchase problems. Give the correct path and receipt/account troubleshooting. Do not promise a universal no-refund policy or wipe unrelated progress when one purchase is revoked. [Apple refunds](https://support.apple.com/en-us/118223), [Google refunds](https://support.google.com/googleplay/answer/2479637).

**Removal can break purchases in an installed game.** Google says removed apps can remain installed but cannot update; Play billing stops while an app is unavailable, and a removed installation cannot be redownloaded unless republished. Preserve local play and explain the difference between delisting, server shutdown and support ending. Do not require a fresh online purchase query to unlock already validated offline content on every launch. [Google removal policy](https://support.google.com/googleplay/answer/12246761?hl=en).

**Advertising is part of the game you ship.** Google's policy treats ad content and offers as app content, requires age-appropriate creatives, and restricts disruptive ads. A network's SDK does not transfer responsibility. Budget controls, reporting and ad-off switches; test close buttons, return-to-game state, no-fill and interrupted rewards. [Google ads policy](https://support.google.com/googleplay/android-developer/answer/9857753).

**Tracking and analytics are different decisions.** Apple requires permission for tracking as defined by its rules, including cross-company ad targeting/measurement; implementing analytics does not by itself answer whether ATT is needed. Inventory actual SDK behavior, avoid fingerprinting, preserve play after refusal and make disclosures match collection. [Apple privacy guidance](https://developer.apple.com/app-store/user-privacy-and-data-use/). A family game requires its own age/consent/advertising assessment; attractive cartoon art does not make an adult-targeted ad stack appropriate for children.

## Discovery, featuring and durable demand

Apple's current featuring page names gameplay, art/animation, controls, sound, technical performance, value, accessibility and localization; there is no guaranteed checklist. Featuring nominations need at least two weeks' notice, with up to three months recommended for wider consideration. Supply a stable build, accurate assets and a concise human story. [Apple featuring](https://developer.apple.com/app-store/getting-featured/).

Derived launch plan: show the core mechanic in the first screenshot/seconds; identify the audience in plain words; prepare direct store links, short clips, press kit and contact; invite a few relevant critics/creators early; use a bounded demo when it proves the game; collect voluntary updates from interested players; schedule support capacity around release. Budget a no-feature scenario. Awards and editorial attention can help distribution but are not cash guarantees, as HoloVista shows.

For long-lived games, new maps, challenges and expansions should add reasons to return without making absence feel like debt. Separate optional daily competition from basic access. Report meaningful updates accurately, preserve saves and keep purchase history intact. Prefer a finished scope and an honest maintenance promise over an unfunded permanent roadmap.


## Rhythm and audio timing

Oboe's current FAQ says requesting low latency does not guarantee it; route, sample rate, callback configuration and device support matter, and Bluetooth is a counterexample. Its stream reference says timestamp estimates cannot account for unknown downstream delay. Therefore “the engine supports audio” is not enough for rhythm. [Oboe FAQ](https://github.com/google/oboe/blob/main/docs/FAQ.md), [stream timing reference](https://google.github.io/oboe/classoboe_1_1_audio_stream.html).

Derived design: anchor scoring to a defined audio/input timeline, offer understandable calibration, preserve offsets where appropriate and re-evaluate them after route changes. Test speakers, wired/USB and Bluetooth, interruption/resume and thermal load. Calibration can compensate stable offsets; it cannot make delayed reactive sound instantaneous or remove variable jitter. Keep timing difficulty distinct from hardware delay and disclose unsupported routes rather than silently marking correct play as failure.

## Technology: consequential findings

1. **2D does not imply a light workload.** Large decoded atlases, transparent layers, full-screen effects, skeleton updates, text shaping and thousands of entities can dominate memory, fill rate and CPU. Optimize what the frame profile shows; polygon count alone says little. Unity recommends disabling texture Read/Write unless needed, trimming atlas space and checking actual atlas size. A single enormous atlas also retains unrelated assets. [Unity atlas workflow](https://docs.unity.com/en-us/engine/6000.0/manual/unity2d/sprite/atlas/create-sprite-atlas), [Android texture formats](https://developer.android.com/guide/playcore/asset-delivery/texture-compression).
2. **Choose the authoring loop before the engine brand.** A tile platformer needs collision/tile iteration; a card game needs text/layout and data tooling; a hand-animated game needs animation import; an arcade prototype may need only code, sprites and immediate reload. Add one real purchase, one save migration and one native overlay to the initial device slice. An export checkbox cannot prove these integrations. This is derived engineering guidance.
3. **Shared gameplay still needs platform work.** Playdigious says it retained most of Loop Hero's GameMaker core while rebuilding touch interaction and integrating services. It identified hover/drag precision, frame rate/battery and lifecycle/aspect-ratio/store requirements as separate porting problems. This is the porter's account on an engine-vendor blog, not a controlled engine comparison. [Interview, 2026-08-20](https://gamemaker.io/en/blog/pc-to-mobile-loop-hero).
4. **Current submission rules have moved.** Apple requires Xcode 26+/iOS 26 SDK+ for uploads since 2026-04-28 and deployment targets iOS/iPadOS 13+ since 2026-09-09. Google Play requires new apps/updates to target API 36 since 2026-08-31; extension ended November 1. Existing-app availability uses a separate API 35 rule. Build SDK, target API, minimum install OS and reliable game hardware are four different choices. [Apple](https://developer.apple.com/news/upcoming-requirements/), [Google Play](https://support.google.com/googleplay/android-developer/answer/11926878?hl=en).
5. **Check every native binary.** Android's current page says updates without 16 KB support become blocked **2027-02-01** for the relevant Android 15+ target requirement. Engine compliance does not fix an old ad, audio or physics `.so`. Inspect the final bundle and test a 16 KB environment. The currently published date supersedes older articles; do not copy the old deadline. [Android page sizes](https://developer.android.com/guide/practices/page-sizes).
6. **Billing wrappers age.** Billing 7's extension ended 2026-11-01; Billing 8 is eligible through 2027-08-31, Billing 9 through 2028-08-31, with listed extensions. Inspect the actual dependency embedded by the engine plugin. Existing installs continuing to purchase does not make a new upload eligible. [Google schedule](https://developer.android.com/google/play/billing/deprecation-faq).
7. **GameMaker pricing is changing, not already universally free.** On October 23, 2026, GameMaker announced free commercial GMRT distribution from January 1, 2027, including mobile. GMS2 commercial rights and source access remain tied to the relevant license; consoles retain separate requirements. GMRT is still rolling out in beta. The release site recommends LTS2026 and warns of incomplete GMRT functionality/platforms. Do not base a shipping date on future license terms or assume runtime parity. [Announcement](https://gamemaker.io/en/blog/gmrt-update), [releases](https://releases.gamemaker.io/).

## Good stacks and their costs

**Godot + GDScript + Compatibility renderer:** strong candidate for a contained independent 2D game whose team wants source ownership, scenes, built-in UI and visual authoring. Sprite animation, tile layers, physics, navigation and resource tools reduce bespoke plumbing. Godot explicitly lists Compatibility as a starting point for 2D and older mobile hardware; advanced effects may justify another renderer, with a new hardware/testing burden. Use built-in nodes before adding a second component architecture. C# mobile export is possible but remains marked experimental; iOS also has documented export/simulator limitations. Prove the required plugins and release builds before committing to C#. [Renderer guidance](https://docs.godotengine.org/en/stable/tutorials/rendering/renderers.html), [C# platforms](https://docs.godotengine.org/en/stable/tutorials/scripting/c_sharp/index.html), [2D animation](https://docs.godotengine.org/en/stable/tutorials/2d/2d_sprite_animation.html).

**Defold + Lua + built-in atlases/GUI + selected extensions:** strong 2D-focused option for small native/web builds and a compact code/content workflow. It supplies scene and GUI authoring, sprite/flipbook work and native extensions. Extensions can add C/C++/Objective-C/Java APIs; each dependency still needs device/build testing. The Foundation's showcase identifies Family Island and MicroMacro: Downtown Detective on iOS and Android; these establish shipped examples, not market share or an indie budget. Its custom license derives from Apache 2.0, permits commercial games and changes, requires notices, and restricts commercializing the editor/engine itself. Do not call it plain Apache or MIT. [Extensions](https://defold.com/manuals/extensions/), [showcase](https://defold.com/showcase/), [license](https://defold.com/license/).

**Unity + C# + URP 2D + uGUI/UI Toolkit as appropriate:** credible when the team already knows Unity or needs several commercial mobile integrations, skeletal authoring, editor tools and complex content. The price is package/editor coordination, allocations, AOT/stripping behavior and vendor licensing. Do not add Addressables, ECS, dependency injection, two UI systems and third-party tweening at project creation without a need. Built-in 2D packages supply sprites, tiles, skinning and pixel scaling. Unity cancelled its Runtime Fee; current seat eligibility/cost still matters. Built-In RP is deprecated from Unity 6.5, with availability promised through 6.7 LTS/support at least through 2028; this favors URP for new work, not an urgent rewrite of every stable game. [2D Animation](https://docs.unity3d.com/Packages/com.unity.2d.animation@10.0/manual/index.html), [pricing](https://unity.com/products/pricing-updates), [render pipeline policy](https://unity.com/topics/render-pipelines-strategy-for-2026).

**GameMaker + GML + LTS runtime:** suited to a team that values a focused 2D editor and quick gameplay iteration. Its room/object workflow can reduce tooling work; content architecture and extension quality remain the team's responsibility. Loop Hero is a concrete mobile port example. Test production LTS separately from GMRT; verify required extensions before switching. [Port account](https://gamemaker.io/en/blog/pc-to-mobile-loop-hero), [release guidance](https://releases.gamemaker.io/).

**Construct 3 or GDevelop:** useful for designers, event-driven prototypes and small games that benefit from web distribution too. Construct's mobile export uses Cordova; its iOS path produces an Xcode project. GDevelop's engine is MIT; its hosted build/account services are separate from that license. Event logic still needs disciplined state boundaries and reusable behaviors. Test WebView memory, audio unlock, lifecycle, native plugin compatibility and sustained action performance. These are legitimate stacks for fitting games; “web” neither proves unacceptable latency nor guarantees parity with native renderers. [Construct publishing](https://www.construct.net/en/make-games/manuals/construct-3/overview/publishing-projects), [mobile workflow](https://www.construct.net/en/tutorials/publish-mobile-apps-26), [GDevelop source](https://github.com/4ian/GDevelop), [iOS export](https://wiki.gdevelop.io/gdevelop5/publishing/ios/).

**Cocos Creator + TypeScript:** integrated authoring with native iOS/Android output and documented Huawei/HarmonyOS branches. Native output is a different runtime contract from a browser build; test JS/native boundaries and SDK plugins. The 3.8 LTS native guide warns that generated IDE changes can be overwritten on rebuild: put customizations in the supported extension/template flow. Good fit where existing Cocos expertise or distribution integration offsets ecosystem learning. [Native guide](https://docs.cocos.com/creator/3.8/manual/en/editor/publish/native-options.html).

**Axmol + C++/Lua:** ownership-oriented scene engine for a C++ team, especially one with Cocos2d-x experience. MIT-licensed. Current default `dev` is v3 prerelease/C++23; stable `release/2.x` is v2 LTS/C++20. The v3 Vulkan/Box2D3 feature list must not be advertised as stable-v2 capability. Smaller community means more native integration and troubleshooting may stay with the team. [Owner README](https://github.com/axmolengine/axmol).

**Solar2D + Lua:** compact code-first 2D engine with live iteration and native/plugin escape hatches. It is the maintained open-source successor to commercial Corona SDK, under MIT, without engine royalties. Evaluate the particular IAP/ad plugins and current build targets, not the old Corona company's status. Its claimed historical app counts are vendor claims, not a current adoption census. [Owner site](https://solar2d.com/).

**libGDX + Java/Kotlin + Gradle + MobiVM:** good for a code-first JVM team willing to own content tooling. The framework supplies rendering, input, audio, scene2d UI and extensions without forcing a scene editor. Generate with gdx-liftoff, use desktop iteration, then test real iOS early. The iOS path needs Xcode/macOS and a compatible RoboVM fork/toolchain. Framework maturity does not make its iOS dependency maintenance disappear. [Project setup](https://libgdx.com/wiki/start/project-generation), [framework source](https://github.com/libgdx/libgdx), [MobiVM](https://github.com/MobiVM/robovm).

**MonoGame + C# + .NET content pipeline:** good for teams that prefer explicit code, existing XNA-like architecture or reuse across desktop/mobile. Official templates include Android/iOS and shared logic. It supplies a framework rather than a full level/UI editor: budget authoring and native services. Test release AOT builds rather than judging from DesktopGL. [Supported platforms](https://docs.monogame.net/articles/getting_started/platforms.html).

**LÖVE + Lua:** small code-first 2D framework, with documented Android and iOS builds. Good for an existing LÖVE game or a developer who accepts platform packaging work. Its main branch is explicitly unstable; the Android README's API 34/NDK 26 instructions cannot by themselves meet today's API 36 upload policy. Build an updated, tested path; this mismatch does not prove the framework is abandoned. The old APKTool embedding method is explicitly obsolete. [LÖVE](https://github.com/love2d/love), [Android packaging](https://github.com/love2d/love-android).

**Ebitengine + Go + thin native hosts:** especially relevant to a Go-oriented team. `ebitenmobile bind` produces Android `.aar` and iOS `.xcframework` views; the host supplies platform services. The current document lists iOS 13 and Android API 16 minima, but the latter is an engine statement, not a guarantee for a chosen current Go/toolchain/plugin set. Version 2.10 initializes Android context itself. Native hosts must suspend/resume the game correctly. Good for explicit small systems; content editors, purchases and accessibility bridges cost engineering time. [Mobile guide](https://ebitengine.org/en/documents/mobile.html).

**Flame + Dart/Flutter:** fits board, casual, educational or UI-rich games when Flutter widgets and plugins are valuable. The engine offers a loop, components, sprites, input and collisions; bridge packages add physics, audio and state integration. A `GameWidget` can coexist with normal app UI. The docs' `/latest/` route currently warns it is older; choose the release selector and package constraints deliberately. Flutter platform reach does not establish game-performance equivalence. [Flame source](https://github.com/flame-engine/flame), [intro](https://docs.flame-engine.org/latest/).

**Phaser or PixiJS + TypeScript + Capacitor/Cordova:** useful when web play and existing JS tooling matter. Phaser provides game systems; PixiJS is principally a rendering foundation. A native shell adds store/device integration, not native performance by definition. Keep the canvas and native overlays in a documented coordinate/lifecycle contract. Verify package versions: Phaser's current site now distinguishes Phaser 4 open source from its separate AE product; old tutorials may target another major version. [Phaser](https://phaser.io/learn), [PixiJS](https://github.com/pixijs/pixijs), [Capacitor](https://capacitorjs.com/docs).

**Owned engine with SDL and specialist libraries:** reasonable when custom technology is a product advantage and the team can fund it. Otherwise scene tools, localization, accessibility, saves, stores and diagnostics become a second product. A small graphics API is not a small shipping obligation. Prefer an existing editor or framework until its concrete limits justify ownership. [SDL](https://github.com/libsdl-org/SDL).

## Compatibility: four promises

Record separately: **can install**, **has required features**, **has adapted controls/layout**, **was tested reliably**. A tablet that runs a stretched phone screenshot satisfies only the first. None of the researched stores or engines supplies a universal profitable minimum-device floor.

### Support strategies

- **Finite premium puzzle/card game:** target broad measured device reach, offline play, crisp readable UI and durable saves. Reduce effects before sacrificing card text. A contained art set and optional cloud sync can limit operations. Test the oldest actual supported devices, not just low editor quality settings.
- **Action/platformer/bullet-heavy game:** define sustained frame-time and input budgets first. Low-memory Android and older iPhone testing may change sprite effects, entity caps and animation design. Limit the device floor honestly if the essential action cannot meet it.
- **Hand-painted story game:** memory and storage may dominate despite little simulation. Segment chapter assets, stream long audio and preserve readable text at all ratios. An enormous high-resolution atlas can be worse than several scoped packages.
- **Ad-supported broad-reach game:** add consent/ad SDK memory, offline ad absence, web overlays and vendor device behavior to the minimum slice. An empty engine benchmark says little about the final monetization stack.
- **UI-rich educational/board game:** tablet, text scale, assistive access, touch/mouse and shared-device identity may matter more than 120 FPS. Use native or framework UI where it improves these requirements.

These are derived strategies, not market-share claims. Audience geography, device cost, game price and acquisition channel decide which is viable. Store listings show a promise; retained-cohort/device telemetry and support records show whether it works.

| Axis | What users experience; implementation and fallback | Cost and validation |
|---|---|---|
| Runtime versus upload | Current SDK/target compliance can coexist with older install OS. Optional APIs need availability checks. | Pin toolchain/exporter; test oldest runtime and current OS; submit a signed test build early. Apple/Google rules above. |
| Native ABI/page size | An SDK can crash before the first frame on a new 64-bit/16 KB device. | Include required 64-bit libraries; inspect every transitive `.so`, not just engine core. [64-bit guide](https://developer.android.com/games/optimize/64-bit). |
| Graphics API/driver | Sprite batches, shaders and blend modes can differ on Adreno/Mali/Apple. | Test representative GPU families; keep essential cues in a supported fallback. Godot renderer source above. |
| Pixel-art scale | Fractional scaling can produce uneven pixel widths, shimmer and camera jitter. | Decide logical resolution, integer scaling/crop/letterboxing and independently scaled UI. Test moving sprites, not still screenshots. [Godot resolutions](https://docs.godotengine.org/en/stable/tutorials/rendering/multiple_resolutions.html). |
| HD illustration | Raster art must survive smallest phone and largest tablet without excessive decoded memory. | Separate source art from runtime variants; trim padding and scope loaded chapters. Unity atlas source above. |
| Texture format | ASTC and ETC2 have different hardware coverage and quality; compression can damage thin outlines. | Supply a suitable fallback or Play texture-format targeting. Google calls ETC1/PVRTC older non-recommended choices; don't use dated coverage percentages as a 2026 census. [Format guide](https://developer.android.com/guide/playcore/asset-delivery/texture-compression). |
| Aspect ratio/cutout | Cropping can hide a platform edge; expanding can reveal threats earlier. HUD can collide with system gestures. | Define gameplay bounds separately from decorative fill and safe-area HUD. Fix competitive visibility intentionally. [Android all screens](https://developer.android.com/games/develop/all-screens). |
| Rotation/folding/resizing | Touch coordinates and board geometry can change mid-gesture. | Cancel or transform active drag safely, retain state and recompute layout. Do not equate orientation lock with immunity to window changes. Derived acceptance criteria. |
| Tablets | A centered phone layout can leave unreachable controls or tiny cards. | Adapt board density and control reach; exploit space without making targets physically smaller. Multiple-resolution source above. |
| Touch/controller/mouse | Hover is absent on touch; controller focus and disconnect need behavior. | Separate select/inspect/activate; make menus usable with supported devices. [Paddleboat](https://developer.android.com/games/sdk/game-controller), [Apple controllers](https://developer.apple.com/documentation/gamecontroller). |
| Refresh rate/frame pace | Uneven delivery feels worse than a stable lower cadence; speed must not depend on render frames. | Use bounded simulation steps; test 60/90/120Hz, low-power mode and pause-resume. [Swappy](https://developer.android.com/games/sdk/frame-pacing). |
| Heat/battery | A cold benchmark can hide throttling after ten minutes or while charging. | Measure sustained sessions; reduce particles/postprocessing and unnecessary idle rendering before action clarity. [ADPF](https://developer.android.com/games/optimize/adpf). |
| Memory pressure | Level transitions, ads and image decoding can cause peak memory kills. | Measure peak ownership across transitions; unload assets and keep a durable checkpoint. Atlas grouping is a lifetime decision. Derived from texture/engine guidance. |
| Background/process death | Calls, lock screen, store sheets or OS reclaim can interrupt anywhere. | Checkpoint at meaningful transactions; pause audio/input and restore a stable scene. Do not depend solely on an orderly quit callback. [Ebitengine host lifecycle](https://ebitengine.org/en/documents/mobile.html), [Godot saves](https://docs.godotengine.org/en/stable/tutorials/io/saving_games.html). |
| Audio/haptics | Bluetooth latency, silent mode, interruptions and missing actuators change cues. | Offer independent controls; use visual equivalents; resync rhythm calibration after route changes. Native mixer/backend choices matter. [Oboe](https://github.com/google/oboe). |
| Text/locales | Raster Latin labels fail with CJK, Arabic, mixed direction, long words or larger text. | Keep translatable strings out of art; test shaping/fallback and control expansion in the actual engine. [HarfBuzz](https://github.com/harfbuzz/harfbuzz). |
| Accessibility bridge | Custom canvas controls may be invisible to screen readers and switches. | Test semantic focus/action hooks, not only contrast. Budget native bridges or constrained accessible game modes; a framework checkbox is insufficient. Derived test requirement. |
| Saves/schema | A new update or older second device may read incompatible data. | Version format, validate before replacing, preserve last known-good state, test downgrade/upgrade. JSON versus binary is not a migration policy. [Godot saves](https://docs.godotengine.org/en/stable/tutorials/io/saving_games.html). |
| Cloud conflict | Offline progress on two devices cannot always be merged without duplication. | Define per-domain rules: settings, unlocks, run state and spendable currency differ. Show meaningful conflict choices; keep server authority where needed. Derived architecture. |
| Network/store absence | Airplane mode, captive portals or missing Play services should not deadlock a local game. | Time out optional services; separate game start from login/analytics/ads. Native distribution adapters need explicit fallbacks. |
| Store variants/regions | Billing, login, achievements and distribution differ outside Google Play/App Store. | Treat each store as another release integration; preserve a service-free core where appropriate. Cocos native distribution docs above. No blanket legal/geographic access claim. |
| Purchase state | Pending payments and callbacks after relaunch can otherwise lose or duplicate rewards. | Verify completed transactions, grant once, persist entitlement and acknowledge. Test cancellation/refund/restore and guest-account linkage. [Play billing](https://developer.android.com/google/play/billing/integrate). |
| AOT/stripping | Reflection-based serializers/plugins may work in editor and fail on iOS release. | Test code generation and preserved callbacks in stripped builds. [MessagePack Unity/AOT](https://github.com/MessagePack-CSharp/MessagePack-CSharp). |
| Alternate execution | Android-on-PC, iPhone apps on Mac and emulators change input and graphics assumptions. | Support deliberately or exclude; do not count simulator success as real-device reliability. |

**API 36 scope:** Android 16 normally ignores orientation/resizability/aspect constraints on large screens for target-36 apps, but explicitly exempts games identified with `android:appCategory`. That exception does not remove edge-to-edge/inset work or justify assuming fold/resize never occurs. [Android 16 behavior](https://developer.android.com/about/versions/16/behavior-changes-16).

**Optional Level Up is a separate contract:** voluntary program eligibility adds services, cloud saves, cross-device layout/distribution, controller and keyboard/mouse requirements, with genre/input exemptions. It also prescribes Vulkan or qualifying ANGLE paths according to engine and device capability, with exceptions. These are not blanket baseline Play upload requirements. A 2D engine chosen for its GLES renderer needs a program-specific feasibility check; review the actual engine/version route before promising benefits. [Revamped guidelines](https://developer.android.com/games/guidelines?hl=en).

**Published February 2027 baseline:** Play will enforce memory thresholds for phones/tablets using rolling 28-day P90 AnonRSS+swap and bitmap metrics, differentiated by state and RAM tier. For example, the 4GB game tier permits 2.25GB foreground AnonRSS+swap; this is a compliance ceiling, not a sensible indie target. Measurement includes Android 13+ devices, not only Android 17. Games above 50MB DEX must reach 25% each shrinking, optimization and obfuscation; native-heavy games below that floor are not subject to that DEX rule. Games are currently outside the separate April 2027 zero-tap sign-in restoration mandate. Track the final package and Play Console metrics, including SDK/background memory; do not infer compliance from texture sizes alone. [Play technical quality requirements](https://support.google.com/googleplay/android-developer/answer/17492799).

### A concrete release slice

Proposed acceptance slice: one representative level; a dense worst-case scene; long localized text; a small and large viewport; one purchase/restore; pause/lock/process kill; interrupted save; no network; ad unavailable if used; old-save migration; release-symbol upload. Run it on the oldest promised iPhone, a low-memory Android, representative Adreno/Mali devices and a tablet if supported. Exact devices follow audience evidence, not an arbitrary universal list. This tests integration risk before a content backlog makes engine changes expensive.

## Catalog: important named tools and components

This is a choice map, not an installation list or adoption ranking. “Official” means maintained/documented by the owning engine/platform; “community” means third-party ownership. Current documentation/repositories show a viable documented role, not future support guarantees. Pin compatible versions. Licenses below concern the named code/tool; bundled assets, plugins and cloud services can have separate terms. Built-in functions often suffice.

### Engines, languages and build paths

| # | Tool | Fit, alternative and constraint |
|---|---|---|
| 1 | [Godot/GDScript](https://docs.godotengine.org/en/stable/tutorials/2d/2d_sprite_animation.html) | Integrated 2D scenes/UI/animation; MIT engine, ownership-oriented candidate. Compare Defold's compact Lua workflow; C# mobile caveat above. |
| 2 | [Defold/Lua](https://defold.com/manuals/extensions/) | Native 2D workflow plus extensible engine; custom Defold License. Compare Solar2D or Godot. Native extension compiler/SDK compatibility is separate. |
| 3 | [Unity/C#](https://unity.com/products/pricing-updates) | Broad authoring/mobile ecosystem; proprietary seat terms. Useful existing expertise/SDK fit; no Runtime Fee. |
| 4 | [GameMaker/GML](https://releases.gamemaker.io/) | Focused 2D editor/runtime; production LTS versus GMRT beta. Paid commercial GMS2 terms differ from announced 2027 GMRT terms. |
| 5 | [Construct 3](https://www.construct.net/en/tutorials/publish-mobile-apps-26) | Event-driven web/native-shell games; proprietary subscription. Device testing and Cordova plugins remain necessary. |
| 6 | [GDevelop](https://github.com/4ian/GDevelop) | MIT engine, visual events and optional JS; hosted build/services have separate plans. Compare Construct workflow and export control. |
| 7 | [Cocos Creator](https://docs.cocos.com/creator/3.8/manual/en/editor/publish/native-options.html) | TypeScript/native authoring; 3.8 LTS documentation and regional distribution paths. Keep generated/native changes reproducible. |
| 8 | [Axmol](https://github.com/axmolengine/axmol) | MIT C++/Lua scene engine; stable v2 LTS and v3 prerelease differ. Best with native engine experience. |
| 9 | [Solar2D](https://solar2d.com/) | MIT Lua, live iteration and mobile plugins; community-supported Corona successor. Audit required plugins individually. |
| 10 | [libGDX](https://github.com/libgdx/libgdx) | Apache-2.0 Java framework; desktop iteration plus Android/iOS. Own authoring tools; iOS depends on compatible AOT stack. |
| 11 | [MonoGame](https://docs.monogame.net/articles/getting_started/platforms.html) | C# framework with Android/iOS templates and content pipeline. Suitable code-first/ported projects; no full scene editor. |
| 12 | [LÖVE](https://github.com/love2d/love) | Lua 2D framework; source builds for iOS/Android. Pin release tags; `main` is next-major development. |
| 13 | [Ebitengine/ebitenmobile](https://ebitengine.org/en/documents/mobile.html) | Go game logic embedded in native views. Excellent Go fit; own native services and content tooling. |
| 14 | [Flame](https://github.com/flame-engine/flame) | Flutter/Dart game loop and components; useful mixed app/game UI. Check Flutter and package support matrix. |
| 15 | [Phaser](https://phaser.io/learn) | JS/TS game framework with scenes, input and examples; current site separates Phaser 4 and AE. Native stores need shell/integrations. |
| 16 | [PixiJS](https://github.com/pixijs/pixijs) | WebGL/WebGPU 2D renderer/assets/text; choose when game architecture is owned. Phaser supplies more gameplay structure. |
| 17 | [Capacitor](https://capacitorjs.com/docs) | Native shell/plugin bridge for web games. Browser success does not prove lifecycle/audio/store behavior. |
| 18 | [gdx-liftoff](https://libgdx.com/wiki/start/project-generation) | Officially recommended libGDX project generator; Gradle/platform/language setup. Prefer over old tutorial setup JARs. |
| 19 | [MobiVM/RoboVM](https://github.com/MobiVM/robovm) | JVM bytecode AOT path for iOS; maintained fork. Native bindings and Xcode compatibility must match release. |
| 20 | [SDL](https://github.com/libsdl-org/SDL) | zlib-licensed native window/input/audio foundation. Useful owned engine; supplies no content pipeline or purchase semantics. |

### Art, animation and level authoring

| # | Tool | Fit, alternative and constraint |
|---|---|---|
| 21 | [Aseprite](https://www.aseprite.org/faq/) | Pixel drawing, animation and sprite export. Commercial/source-available tool, not current GPL; art can be sold. Compare Pixelorama/LibreSprite. |
| 22 | [Pixelorama](https://github.com/Orama-Interactive/Pixelorama) | MIT pixel-art/animation editor, built with Godot; desktop/web. Useful open workflow; validate export/import conventions. |
| 23 | [LibreSprite](https://libresprite.github.io/) | GPLv2 pixel-editor alternative. Tool licensing does not automatically license created art; assess current feature fit separately from Aseprite ancestry. |
| 24 | [Krita](https://krita.org/en/about/license/) | GPL painting/animation tool; artwork remains creator-owned. Fits painted backgrounds/frames; runtime atlas/import work separate. |
| 25 | [Tiled](https://www.mapeditor.org/) | Mature open-source tile/object/world editor; orthogonal/isometric/hex, rules and broad export support. Owner lists Coromon/Shovel Knight usage. Check importer coverage for custom properties/animations. |
| 26 | [LDtk](https://ldtk.io/) | MIT level editor with typed entities, auto layers, worlds and simple JSON/PNG export. Good deliberate 2D layout workflow; importers vary. |
| 27 | [TexturePacker](https://www.codeandweb.com/texturepacker) | Commercial atlas packing/trimming and engine exports; compare engine packer first. Polygon packing needs matching runtime support. |
| 28 | [Spine](https://esotericsoftware.com/spine-runtimes-license) | Skeletal 2D animation/runtime ecosystem. Proprietary editor/runtime license conditions, version-matched exports; source access is not unrestricted runtime redistribution. |
| 29 | [Rive](https://rive.app/runtimes) | Interactive vector animation and runtime integration for responsive UI/characters. Editor/service terms separate; test renderer features and integration on chosen engine. |
| 30 | [Unity 2D Animation](https://docs.unity3d.com/Packages/com.unity.2d.animation@10.0/manual/index.html) | Official sprite skinning/skeleton workflow; compare Spine when pipeline needs exceed it. Package version must match editor. |
| 31 | [Unity 2D Tilemap Extras](https://docs.unity3d.com/Packages/com.unity.2d.tilemap.extras@4.0/manual/index.html) | Official rule tiles/brushes for tile authoring. Prefer existing tile tools before writing an editor. |
| 32 | [Unity SpriteShape](https://docs.unity3d.com/Packages/com.unity.2d.spriteshape@10.0/manual/index.html) | Spline-based 2D shapes/terrain; fits curving ground, not every pixel-grid level. Geometry/collider updates need profiling. |
| 33 | [Unity 2D Pixel Perfect](https://docs.unity3d.com/Packages/com.unity.2d.pixel-perfect@5.0/manual/index.html) | Camera scaling for pixel art; solves a defined grid problem, not all aspect-ratio/UI decisions. |
| 34 | [Godot TileMapLayer/TileSet](https://docs.godotengine.org/en/stable/tutorials/2d/using_tilemaps.html) | Built-in tiles, collision/occlusion/navigation; reuse external TileSet resources across levels. Compare Tiled/LDtk if external authoring earns the import work. |
| 35 | [Godot AnimatedSprite2D/AnimationPlayer](https://docs.godotengine.org/en/stable/tutorials/2d/2d_sprite_animation.html) | Built-in frame animation versus general property tracks; often enough for a small game. Keep animation events separate from authoritative rewards. |
| 36 | [Defold Atlas](https://defold.com/manuals/atlas/) | Built-in packing/animation source. Scope atlases to actual simultaneous use; external TexturePacker is optional. |

### UI, camera, text and game logic

| # | Tool | Fit, alternative and constraint |
|---|---|---|
| 37 | [Druid](https://github.com/Insality/druid) | Community Defold GUI components: buttons, scrolling, lists/input and widgets. Adds behavior to existing GUI nodes; input ordering/lifetimes still need tests. |
| 38 | [libGDX Scene2d.ui](https://libgdx.com/wiki/graphics/2d/scene2d/scene2d-ui) | Built-in skinnable widgets/layout over scene graph; useful game menus. Not native OS accessibility automatically. |
| 39 | [Phantom Camera](https://github.com/ramokz/phantom-camera) | Godot camera follow/framing/transitions inspired by Cinemachine. Use built-in Camera2D for simple fixed follow; avoid camera complexity without need. |
| 40 | [DOTween](https://dotween.demigiant.com/) | Unity code-driven tweens/sequences; core and Pro differ. Current releases require newer Unity than historical releases; match version. |
| 41 | [UniTask](https://github.com/Cysharp/UniTask) | Unity async/await on player loop with cancellation and tracking. Compare built-in Awaitable/coroutines; not a general threading solution. |
| 42 | [R3](https://github.com/Cysharp/R3) | Reactive streams, UniRx successor. Use if streams simplify actual state/event logic; ordinary events often clearer. |
| 43 | [Ink](https://github.com/inkle/ink) | MIT narrative language/compiler/runtime from inkle; Unity integration and other ports. Good branching text; save story state with game schema. |
| 44 | [Yarn Spinner](https://github.com/YarnSpinnerTool/YarnSpinner) | Dialogue lines/options/commands; owner names Night in the Woods and DREDGE usage. Core engine-agnostic code versus engine integration are separate packages. |
| 45 | [Dialogic 2](https://github.com/dialogic-godot/dialogic) | MIT Godot dialogue/visual-novel tooling; current main requires Godot 4.5+. Version/beta API changes matter; don't use private underscore APIs as stable contracts. |
| 46 | [LimboAI](https://github.com/limbonaut/limboai) | Godot behavior trees/state machines with debugger. Native extension/module versions have exact Godot compatibility; simple explicit states can cost less. |
| 47 | [HarfBuzz](https://github.com/harfbuzz/harfbuzz) | Text shaping/font infrastructure; often already inside engine. Necessary script behavior is broader than drawing glyph atlas quads. |
| 48 | [msdfgen](https://github.com/Chlumsky/msdfgen) | Multi-channel distance fields for sharp scalable glyph/vector edges; custom renderer/tool pipeline. Does not provide shaping/layout by itself. |
| 49 | [stb_image/stb_truetype](https://github.com/nothings/stb) | Small C/C++ asset helpers under public-domain/MIT choice. Convenient owned pipelines; owner warns security fixes may be slow, so assess untrusted input. |

### Simulation, storage and networking

| # | Tool | Fit, alternative and constraint |
|---|---|---|
| 50 | [Box2D](https://box2d.org/documentation/) | Portable C17 2D rigid-body/collision library; engine integrations may embed older versions. Pin version; replay/network determinism must cover surrounding game code too. |
| 51 | [Forge2D](https://pub.dev/packages/forge2d) | Dart 2D physics used with Flame bridge; current 0.15.3 package lists mobile support. Not identical to current native Box2D API. |
| 52 | [Rapier](https://rapier.rs/docs/) | Rust 2D/3D physics with C/JS bindings, snapshots and optional cross-platform determinism. Fits custom engine; integration costs exceed using built-in physics. |
| 53 | [Ashley](https://github.com/libgdx/ashley) | Apache-2.0 Java entity system in libGDX ecosystem. Mature small scope; old release/activity alone does not prove abandonment. Avoid ECS for a handful of objects without benefit. |
| 54 | [gdx-ai](https://github.com/libgdx/gdx-ai) | Apache-2.0 steering/pathfinding/behavior trees/FSM utilities. Useful specialist algorithms; game-specific behavior still belongs to team. |
| 55 | [Godot FileAccess/ConfigFile](https://docs.godotengine.org/en/stable/tutorials/io/saving_games.html) | Built-in persistence primitives; explicit versioned data and recovery logic remain required. Config settings are not a currency ledger. |
| 56 | [Unity PlayerPrefs](https://docs.unity3d.com/6000.0/Documentation/ScriptReference/PlayerPrefs.html) | Small local preferences; not encrypted or suitable as authoritative paid entitlement storage. Use explicit saves for complex state. |
| 57 | [SQLite](https://sqlite.org/atomiccommit.html) | Transactional embedded structured data; useful complex inventories/local histories. A small validated atomic file may be simpler for one save blob. Keep DB and backup semantics coherent. |
| 58 | [MessagePack for C#](https://github.com/MessagePack-CSharp/MessagePack-CSharp) | Compact typed serialization; Unity integration/source generator/AOT constraints. JSON can be easier to inspect; neither handles schema migration automatically. |
| 59 | [Nakama](https://github.com/heroiclabs/nakama) | Apache-2.0 game backend with accounts, storage, social, matches and purchase validation. Broad capability adds operations; don't run it solely to save a local puzzle score. |
| 60 | [Colyseus](https://github.com/colyseus/colyseus) | MIT Node/TypeScript rooms, state synchronization and reconnect. Good authoritative realtime starting point; hosting and game-specific cheat prevention remain work. |
| 61 | [ENet](https://github.com/lsalzman/enet) | Reliable UDP transport for custom/native networking. Does not supply accounts, matchmaking, encryption policy or recovery semantics. |

### Native integration, audio and commerce

| # | Tool | Fit, alternative and constraint |
|---|---|---|
| 62 | [Oboe](https://github.com/google/oboe) | Android C++ low-latency audio; chooses AAudio/OpenSL ES by platform and includes workarounds. Useful rhythm/custom engine; engine audio may already suffice. |
| 63 | [miniaudio](https://miniaud.io/) | C/C++ single-file playback/capture across mobile/desktop; public-domain option. Good small owned audio layer; no graphical sound authoring. |
| 64 | [Swappy](https://developer.android.com/games/sdk/frame-pacing) | Android frame pacing for OpenGL/Vulkan. Use engine integration where available; frame pacing is separate from average FPS. |
| 65 | [ADPF](https://developer.android.com/games/optimize/adpf) | Thermal/power/performance signals; helps sustained quality adaptation. Availability differs; don't hardcode one device's thermal behavior. |
| 66 | [Paddleboat](https://developer.android.com/games/sdk/game-controller) | Android native controller mapping, hotplug and optional features. Useful custom engine; menu focus must still be implemented. |
| 67 | [Apple Game Controller](https://developer.apple.com/documentation/gamecontroller) | Native controller discovery/input; engine adapter can hide platform differences. Test disconnection and supported device mapping. |
| 68 | [StoreKit](https://developer.apple.com/documentation/storekit) | Native Apple commerce and transaction handling. Use current transaction APIs/engine integration; keep entitlement reconciliation separate from button UI. |
| 69 | [Google Play Billing](https://developer.android.com/google/play/billing/integrate) | Android commerce, pending/completed purchases and acknowledgement. Version deadlines above; no entitlement from a pending payment. |
| 70 | [Play Asset Delivery](https://developer.android.com/guide/playcore/asset-delivery/texture-compression) | Asset/texture-format targeting for larger Android content. Small games may be simpler fully bundled; packs need availability/download handling. |
| 71 | [Defold native extensions](https://defold.com/manuals/extensions/) | Supported path to platform APIs and third-party SDKs. Pin engine/extension revisions and validate generated native binaries. |
| 72 | [Flame bridge packages](https://github.com/flame-engine/flame) | `flame_audio`, `flame_forge2d`, `flame_tiled` and state integrations connect specialists. Select bridges individually; package support is not automatic game suitability. |

### Testing, diagnostics and releases

| # | Tool | Fit, alternative and constraint |
|---|---|---|
| 73 | [GUT](https://github.com/bitwes/Gut) | MIT Godot/GDScript unit tests, doubles, CLI/JUnit output; current table maps versions to Godot releases. Good deterministic rules/saves. |
| 74 | [GdUnit4](https://github.com/godot-gdunit-labs/gdUnit4) | Godot GDScript/C# and scene testing, input simulation, fuzzing and CI. Engine-version compatibility matters; not a substitute for touch/device feel. |
| 75 | [Firebase Crashlytics](https://firebase.google.com/docs/crashlytics) | Hosted Apple/Android/Flutter/Unity crash grouping and native support. Upload symbols; review collected context/privacy. |
| 76 | [Sentry Unity](https://docs.sentry.io/platforms/unity/) | Crash/error/performance diagnostics with service or self-hosting options. Check supported Unity/native SDK versions and data volume. |
| 77 | [fastlane](https://docs.fastlane.tools/) | Mobile signing/build/beta/release automation. Keep credentials out of project/logs; engine export is a preceding step. |
| 78 | [GameCI](https://game.ci/docs/) | Unity CI build/test workflows and images. License activation/build host costs remain; iOS still needs Apple's toolchain. |

### Asset rights, sound production and performance tools

| # | Tool/component | Useful role and boundary |
|---|---|---|
| 79 | [Kenney assets](https://kenney.nl/assets/1-bit-pack) | Coherent prototype/production art; the inspected 1-Bit Pack explicitly uses CC0. Save each downloaded pack's license rather than assuming every linked third-party asset shares it. |
| 80 | [Noto fonts](https://notofonts.github.io/) | Broad script fallback for localization. Inspect selected font license and glyph/shaping coverage; archive notices with bundled fonts. The [old aggregate repository](https://github.com/notofonts/noto-fonts) is archived and explicitly redirects to this active distribution. |
| 81 | [Game-icons.net](https://game-icons.net/about.html) | Editable game-oriented vectors under CC BY 3.0; credit individual authors. Particularly useful for ability/status/card icons; stylistic consistency still needs curation. |
| 82 | [Audacity](https://www.audacityteam.org/) | Free open-source desktop recording/editing/conversion on macOS, Windows and Linux. Author loops and effects, then test exported clips in the game's actual decoder/mixer. Tool licensing does not grant rights to imported recordings. |
| 83 | [FMOD Studio/Core](https://www.fmod.com/licensing) | Commercial audio middleware with a conditional free indie license: developer revenue below $200k/year and project budget below $600k; registration/logo conditions apply. Useful for complex adaptive audio; a small game may prefer its engine mixer. |
| 84 | [Unity IAP](https://docs.unity.com/en-us/iap) | Unified native App Store/Play purchase adapter, product types, restoration/fulfillment. Pin package and native billing versions. A unified API does not eliminate store setup, entitlement verification or regional policy differences. |
| 85 | [Instruments](https://developer.apple.com/documentation/xcode/improving-your-app-s-performance) | Time Profiler, Allocations/Leaks, energy and I/O investigation on real iOS devices; compare before/after captures. Xcode Organizer/MetricKit complement local profiles with shipped-device evidence. |
| 86 | [Android Studio Profiler](https://developer.android.com/studio/profile) | Prefer a release-profileable build for representative overhead; debuggable builds expose extra heap/allocation detail but perturb performance. Inspect CPU/memory/system behavior beyond engine counters. |
| 87 | [Unity Profiler](https://docs.unity.com/en-us/engine/6000.0/manual/analysis/profiler) | Connect target devices and inspect engine resource use; distinguish editor from player samples. Useful before selecting pooling, batching or script changes. |
| 88 | [Godot Profiler](https://docs.godotengine.org/en/stable/tutorials/scripting/debug/the_profiler.html) | Frame, physics and script timing; self versus inclusive samples prevent blaming callers for callee cost. Built-in script profiling does not support C#; docs point to Rider/dotTrace. |
| 89 | [Defold profiler/build report](https://defold.com/manuals/profiling/) | Runtime overlay, browser Remotery frame/resource inspection and asset-size reports. Enable profiler support in the tested build; profile the mobile target, not only desktop. |
| 90 | [Gradle Wrapper](https://docs.gradle.org/current/userguide/gradle_wrapper.html) | Commit wrapper files to standardize Android build version; verify distributions/JAR integrity. Pin compatible AGP/JDK/NDK too: the wrapper alone cannot reproduce a native exporter. |
| 91 | [Dart pub](https://dart.dev/tools/pub/dependencies) | Flame/Flutter dependency resolution and lockfile integrity. `--enforce-lockfile` verifies package hashes and resolved versions; test plugin changes on both native platforms, not only Dart tests. |

Keep an asset manifest recording creator, source, exact version/download, permitted use, attribution and modification conditions. Fonts, sound recordings, editor seats and runtime libraries have different licenses; a free editor does not license its marketplace content. These are production controls, not a substitute for reviewing the actual terms. The shared 3D report covers further cross-category store SDKs and diagnostics.

## Named avoid, migrate and conditional choices

Status checked 2026-11-08. “Avoid” identifies a use case; it does not condemn every existing project.

| Choice | Verdict, verified reason and replacement | Legitimate exception / migration cost |
|---|---|---|
| Construct 2 | Avoid new work; owner marks fully retired, no fixes/support; final release 2021-07-01. Use Construct 3 or another maintained engine. [Owner](https://www.construct.net/en/construct-2/download). | Stable existing offline desktop release can remain; mobile build/store changes eventually demand migration. Audit third-party event addons. |
| PhoneGap Build | Retired hosted workflow; use current Cordova or Capacitor/build tooling. Cordova explicitly separates its continued maintenance from PhoneGap's 2020 shutdown. [Cordova](https://cordova.apache.org/announcements/2020/08/14/goodbye-phonegap.html). | Historical reproducibility only; don't infer Cordova is dead. |
| Commercial Corona SDK as a current supported vendor | Use Solar2D successor; owner says Corona is no longer commercially supported. [Solar2D](https://solar2d.com/). | Existing code can be valuable; plugins/build settings need current validation. |
| Old LÖVE APKTool embedding | Avoid; Android owner README calls it obsolete and documents Gradle/AAB embedding. [Owner](https://github.com/love2d/love-android). | Historical build reproduction; not a current publishing strategy. |
| Copying old engine Android SDK versions | Avoid for release planning: LÖVE README names API 34, while Play now requires 36 for uploads. Upgrade/test actual toolchain. [LÖVE](https://github.com/love2d/love-android), [Play](https://support.google.com/googleplay/android-developer/answer/11926878?hl=en). | A documented old minimum can still describe historical builds; it is not evidence the engine cannot be updated. |
| UniRx | Avoid new dependency; archived 2024-02-16, owner directs users to R3. [Owner](https://github.com/neuecc/UniRx). | Keep tested existing use while evaluating API/lifetime changes; R3 is not a drop-in migration guarantee. |
| Unity Built-In RP for a new long-lived game | Prefer URP; deprecated from 6.5, supported availability through 6.7 LTS/end-2028 floor. [Unity strategy](https://unity.com/topics/render-pipelines-strategy-for-2026). | Do not rewrite a stable shipped 2D game solely for the label. Check shader/material/package conversion first. |
| Google Play Instant | Do not build acquisition around it; publishing/APIs ended starting December 2025. [Google](https://developer.android.com/topic/google-play-instant). | A web demo remains a different distribution option; old engine export menus are not proof of service availability. |
| Play Billing 7 or earlier in a new update | Migrate wrapper/native library; last v7 extension ended 2026-11-01. [Schedule](https://developer.android.com/google/play/billing/deprecation-faq). | Existing installed apps can still work; eligibility concerns future uploads. Test callbacks/pending states during migration. |
| Unaligned legacy native SDK binaries | Rebuild/update for 16 KB devices before the published 2027-02-01 update block. [Android](https://developer.android.com/guide/practices/page-sizes). | No exemption because a game uses only 2D sprites; third-party `.so` files count. |
| Godot C# mobile as a risk-free default | Conditional, not deprecated: Android/iOS explicitly experimental; choose GDScript or prove exact export/plugins if C# is important. [Godot](https://docs.godotengine.org/en/stable/tutorials/scripting/c_sharp/index.html). | Existing capable team can ship; label is not evidence every game fails. Budget troubleshooting and device tests. |
| GMRT merely because free commercial use was announced | Trial separately; pricing starts 2027, runtime currently beta and partial compatibility. Production LTS remains available. [Announcement](https://gamemaker.io/en/blog/gmrt-update), [releases](https://releases.gamemaker.io/). | Good experimentation branch; switch once required exports/extensions pass. |
| Axmol default `dev` as if stable | Explicit v3 prerelease; use `release/2.x` LTS for stable baseline unless v3 features justify risk. [README](https://github.com/axmolengine/axmol). | A team contributing/testing v3 may accept churn; C++23 and new backends change build surface. |
| Spine runtime as unrestricted freeware | Do not integrate without satisfying its runtime/editor license. Use licensed Spine or built-in animation. [Runtime terms, 2025-04-05](https://esotericsoftware.com/spine-runtimes-license). | Licensed teams get a mature pipeline; preserve notices and exporter/runtime versions. |
| PlayerPrefs as secrets/purchased-currency authority | Unsuitable role, not obsolete API. Owner states local preferences are unencrypted; use secure platform storage where needed and validated authoritative entitlements. [Unity](https://docs.unity3d.com/6000.0/Documentation/ScriptReference/PlayerPrefs.html). | Good for volume, options and non-sensitive tiny settings. |
| `stb` parsers for unrestricted player-supplied files without a security plan | Owner warns fixes may take significant time. Prefer controlled shipped assets or a maintained/hardened parsing path. [Owner](https://github.com/nothings/stb). | Useful small trusted-asset tools; do not label the whole library abandoned. |
| One atlas/one scene containing the entire game | Avoid when it forces peak/resident memory above budget. Group by simultaneous use and load boundaries. [Unity atlas guidance](https://docs.unity.com/en-us/engine/6000.0/manual/unity2d/sprite/atlas/create-sprite-atlas) plus derived lifetime rule. | A genuinely small game may be simplest fully resident. |
| Bespoke engine to avoid a small license bill | Usually poor small-team tradeoff unless ownership is strategic. Account for content tools, stores, accessibility and maintenance. This is an engineering inference, not a measured cost comparison. | Experienced engine team or unusual simulation/rendering may benefit. |

**Do not mislabel Cocos2d-x, DragonBones, Ashley or gdx-ai “archived” from old dates.** Inspected Cocos2d-x owner API returned `archived: false`; its README/tooling is old enough to require exact modern build verification, and Axmol offers an explicit maintained path. DragonBones' retrieved repository did not establish an archive/retirement declaration. That is insufficient to assert abandonment. For new work prefer a pipeline with verified current editor/runtime/build support; a team that owns a tested fork can reasonably retain it. [Cocos2d-x](https://github.com/cocos2d/cocos2d-x), [Axmol](https://github.com/axmolengine/axmol), [DragonBonesJS](https://github.com/DragonBones/DragonBonesJS).

## Evidence limits for technology

The report can establish documented platform support, shipped examples, licenses and dated requirements. It cannot establish the best engine's frame time, executable size or production support cost without a representative game and device set. Vendor empty-project benchmarks and unrelated desktop hits would not resolve that question. The required resolution is a signed device slice containing the intended animation, UI, plugins and worst-case scene; no universal winner is claimed.

Current docs sometimes redirect across versions or expose development branches. Pin evidence to release/package documentation when implementing; the Axmol, GameMaker, LÖVE and Flame caveats above are concrete cases, not generic caution. Public docs cannot prove today's exact editor/Xcode/NDK/plugin combination will pass both stores; only a real signed upload and device test can.

## Sources and method

Citations sit beside claims. Research combines current primary platform/engine documentation, developer postmortems, independent reviews, historical magazine/book text, WWDC transcripts and individual long-term reports. Reviews establish a critic’s experience at a dated version; developer revenue claims are not audited profit. Repeated reporting of one claim is one evidence source. The business cases do not isolate causality unless their design supports it.

Direct inspection covered seven published game screenshot sets and sampled frames of the official Threes promotional GIF. Store metadata was checked for the seven listed games. Screens establish composition; sampled promotion establishes shown motion, not live touch latency or sustained performance. No device playtests, engine builds, private financial audit or market-share survey were performed. The compatibility release slice explains what remains product-specific verification.

NME’s direct page returned 403; search exposed substantial review text and explicit pros/cons, used only for its dated criticism. Game UI Database restricted access; the resource assessment links related research rather than claiming a fresh catalog inspection. Book claims use accessible excerpts or chapters, identified beside them. Where public sources cannot determine a game’s profit, an exact failure cause or a current defect, the relevant section preserves that limit.

Useful entry points: [Apple game controls](https://developer.apple.com/design/human-interface-guidelines/game-controls), [Android game development](https://developer.android.com/games), [Game Accessibility Guidelines](https://gameaccessibilityguidelines.com/), [Game Programming Patterns](https://gameprogrammingpatterns.com/), [Papers, Please mobile port](https://dukope.com/devlogs/papers-please/mobile/), [Threes development correspondence](https://asherv.com/threes/threemails/). Use these with the linked independent critiques and dated business cases, not as a replacement for them.
