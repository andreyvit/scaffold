# Great web-based 3D games that run in the browser

## Scope

This covers indie/small-team 3D games and 2.5D games rendered in 3D: arcade, driving, time trial, creation, competitive multiplayer, relaxation and short narrative/horror. WebXR is a compatibility branch; full VR design, cloud-streamed native games, casino/real-money gambling and large MMO economies are outside the core scope. They require different delivery, economics or product research. No genre, locale or audience was specified, so the report compares branches rather than selecting one universally.

Evidence separates platform requirements, developer disclosures, independent reviews, individual complaints, direct interface observations and derived recommendations. No engine builds, sustained device benchmarks, paid purchases, live competitive matches or private financial audits were performed. Four shipped interfaces were inspected; sampled states do not establish long-term reliability. Financial and inaccessible-source limits sit beside the claims they affect.

Read [build priorities](#prioritized-build-guidance), then compare [examples](#exemplary-games-and-limits), [visual directions](#visual-directions-evidence-backed-design-hypotheses), [commercial models](#distribution-contracts-and-economics) and [compatibility](#compatibility-four-separate-promises). The practical references contain 93 details; the ecosystem catalog contains 70 named choices plus design resources.

Research checked 2026-11-08. Indie/small-team browser games: desktop and mobile; single-player and multiplayer; own-site and portal distribution. No genre, locale, engine or business model selected. Native mobile implementation is covered in [mobile 3D research](mobile-3d-games.md); web account/server foundations in the [web recipe](../skills/scaffold/references/app-web.md). Browser game rendering needs its own simulation/input loop; generic server-rendered app guidance does not prescribe the game runtime. Recommendations here are research, not confirmed scaffold choices.

## What makes a browser 3D game great

A great browser game makes its central action worth opening a link for, then preserves that value on the devices its audience owns. Rendering quality serves spatial understanding, atmosphere or expression. It cannot compensate for unreliable input, lost saves, empty matches or an opaque loader.

Judge seven outcomes separately:

| Outcome | Useful evidence | False substitute |
|---|---|---|
| Player love | Voluntary return, memorable moments, specific recommendations | Attractive promotional renders |
| Player value | Relaxation, mastery, creative expression or social connection | More currencies and longer sessions |
| Audience | Qualified starts, returning cohorts, invitations completed | Aggregate page views or downloaded bytes |
| Cash earned | Collected ad/purchase/licensing proceeds by channel | Gross consumer spending |
| Viability | Proceeds cover labor, infrastructure, content and support | One viral launch or low hosting bill |
| Maintainability | Reproducible releases, bounded simulation, inspectable failures | An engine's reputation |
| Featuring | Original promise, clear cover, quick playable entry, reliable host integration | Entitlement to portal placement |

This framework is a synthesis of the cases below, not a ranking. Finishing a short experience and leaving satisfied may be success; low D1 retention alone does not refute that product. A multiplayer service needs a different return pattern and operating budget.

## Prioritized build guidance

**First: prove one playable loop on the weakest intended tier.** Choose the emotional job, camera, core input and distribution route together. Build one representative scene through loading, input, failure/retry and progress saving. Measure cold first play and sustained frame pacing with realistic textures, effects and UI. Slow Roads, SWOOOP, Cannon Clash and Vortelli show distinct ways to reduce scope; none proves one engine is always best. See the named cases and stack choices.

**Before expanding content: prove browser citizenship.** Exercise pointer escape, tab switching, lost input, orientation/resize, audio activation, storage denial and context loss. Keep settings and recovery accessible outside the renderer. Test the actual portal iframe. These are basics, not late polish; see compatibility and practical details.

**For multiplayer: prove service health before buying more art.** Start with one region/mode population that can sustain useful matches. Add invitations, reconnect, correct rewards, moderation and operator diagnostics. Record latency, queue time, abandonment and error recovery. Narrow One's departures and TANX/Krunker's operating history show why fast join and popularity do not finish this work.

**For a creative game: protect player work before promoting sharing.** Implement undo, import validation, stable serialization, version-aware replay and migration fixtures. Separate local saves from publication and account ownership. PolyTrack's changelogs supply concrete examples; the general data requirements remain in the existing web recipe.

**Then choose a coherent visual direction.** Prototype the entry, in-play HUD, pause/settings and result screen as one family. Keep a small material/type/icon vocabulary. Reserve a readable value/color range for actionable targets; do not combine unrelated asset packs and call the result a style. Use actual gameplay captures at embedded dimensions to assess it.

**Before monetizing: prove the free promise and transaction failures.** Measure first-loop completion, revisits and net contribution. Validate no-fill, ad failure, declined payment, delayed confirmation, refresh during purchase and account recovery. Align the contract with the planned own-site/native funnel. The commercial section explains why portal metrics and revenue shares cannot be copied between hosts.

**Useful differentiators:** a world seed worth sharing, unusually fast retry, expressive creation tools, a clear social objective, deep control/accessibility options, a reliable low-spec mode or a distinctive calm experience. Choose the one that advances the game's promise. Each adds maintenance; none is mandatory across recipes.

**Costly traps:** realistic high-resolution assets before a download budget; high-DPI rendering by default; many modes with too few simultaneous players; an account wall before meaningful play; a sprawling currency system; custom engine work without a concrete constraint; a native export treated as a finished web port; or a free service without funded operation. These are conditional risk assessments supported by the compatibility, maintenance and commercial cases.

**Ideas to test:** fewer onboarding steps; a smaller first scene; practice before live matchmaking; one-click rejoin; simpler price choices; optional assists; a different thumbnail showing the true action. Define the success event, denominator and guardrails first. Portal case studies are hypotheses for your cohort, not guaranteed uplift.

### Acceptance scenarios under strain

Use these as scenario tests around the selected product, not a demand to support every device or feature.

| Scenario | Expected result; consequence if mishandled |
|---|---|
| Slow cold connection, interrupted asset request | Honest stage, bounded retry, useful error; no endless loader or discarded selection |
| Weak integrated GPU plus high-DPI display | Readable low tier and stable play; no unusable native-resolution default |
| Long session and repeated scene regeneration | Bounded memory and stable controls; no gradual crash or resource leak |
| Tab hidden, frozen, discarded, restored | Checkpoint recovery; solo pause or server reconciliation; no huge delta or false success |
| Mouse escape, alt-tab, controller disconnect, touch cancellation | Cleared input and a usable route back; no stuck movement/fire |
| Two tabs, stale client version, delayed save response | Explicit session/version policy; no silent rollback of progress |
| Storage unavailable, cleared or evicted | Accurate save status and recovery route where offered; no claim of permanent local ownership |
| Refresh during purchase or reward confirmation | Exactly one server entitlement and a recoverable pending state; no double spending or lost purchase |
| Empty, full, expired or geographically poor room | Honest availability, sensible retry/alternatives and friend continuity; no silent wrong-room join |
| Large inventory, long name, RTL text, IME, large score | Stable layout and correct input; no unreadable controls or unintended actions |
| Narrow embed, browser zoom, external display, rotation | HUD and controls remain operable; no clipped purchase/exit button |
| Locale/time-zone change during daily event | Server-defined cutoff with localized display; no duplicate reset or ambiguous expiry |
| Client attempts impossible moves/rewards or floods messages | Authoritative rejection and bounded resource use; no corrupted economy or denial of service |
| Platform SDK failure or no ad fill | Core game and explicit error path remain usable; no dependency deadlock |
| Service retirement | Communicated ending and an honest data/purchase policy; no indefinite sale of unusable content |

Daily events need a server-defined instant or explicit reset zone, displayed through locale-aware formatting. A player's local midnight is not a universal competition boundary. Keep countdowns synchronized after return from suspension; the browser's wall clock is not authority for paid rewards. [Intl.DateTimeFormat](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat); server authority is derived guidance.

## Exemplary games and limits

**Slow Roads: a specific emotional job.** Endless scenic driving serves decompression, rather than competition or completion. The official site lists web version 2.4.2 (15 June 2026), touch support introduced in 2.0 and fixes for gamepad controls and mobile rendering. It now offers a paid expanded Steam edition while promising continued free, ad-free web availability. This is evidence of a deliberate free/premium boundary, not audited profitability. The press kit still forecasts Steam release; the live game and store supersede that forecast. [Game](https://slowroads.io/), [Steam edition](https://store.steampowered.com/app/3431300/Slow_Roads/), [older press kit](https://topograph.io/slowroads).

Ars's 2022 review valued immediate, registration-free relaxation, easy reset after leaving the road and alternative mouse steering. It also warned that performance could strain machines. These are launch-version observations, not a current compatibility test. The lesson is to remove rules that conflict with the desired feeling; a driving game need not punish crashes. [Ars Technica, 24 October 2022](https://arstechnica.com/gaming/2022/10/slow-roads-offers-a-chill-endless-driving-experience-in-your-browser/).

**Townscaper web demo: creative pleasure without an economy.** PC Gamer's 2021 review praised welcoming architecture and short creative visits, while warning that players seeking challenge may leave quickly. It reviewed the paid desktop game; do not attribute all features to the browser demo. The official web page remains at Oskar Stålberg's site, but its extracted fallback says mobile WebGL builds are unsupported. “Opens on a phone” would not settle reliable support. This is an expressive toy and acquisition demo, not evidence that goal-free games universally retain players. [Review](https://www.pcgamer.com/townscaper-review/), [official demo](https://oskarstalberg.com/Townscaper/).

**Narrow One: a focused multiplayer identity.** Pelican Party's current listing describes medieval 5v5 archery, map shortcuts, squads, cosmetics and touch/gamepad support. Its itch listing shows 4.6/5 from 849 ratings at inspection, a self-selected response rather than a retention measure. Two named developers and an October 2026 listing update establish small-team authorship and ongoing publication, not service reliability. The strong design hypothesis: one legible weapon fantasy and shared capture objective can distinguish a browser shooter without a broad military loadout. [Developer listing](https://pelicanparty.itch.io/narrow-one).

The studio’s 2023 devlog reported about 70% leaving mid-match; reconnect and participation rewards were proposals, not measured fixes. Its map and matchmaking choices inform the practical details below. [Devlog, 31 May 2023](https://pelicanparty.itch.io/narrow-one/devlog/536795/spilling-our-trade-secrets-narrow-one-updates-).

**PolyTrack: mastery, creation and version-aware comparison.** Kodub's low-poly time-trial racer combines short attempts, an editor and shareable tracks. Current itch metadata lists HTML5 and native editions; version 0.6.3 is dated September 2026. Listing metadata is not a device test. [Developer page](https://kodub.itch.io/polytrack).

Poki describes asynchronous racing; the developer shipped experimental multiplayer in March 2026. Prefer current changelogs over stale portal copy. [Poki](https://poki.com/en/g/polytrack), [0.6.0](https://kodub.itch.io/polytrack/devlog/1454034/polytrack-060-multiplayer-car-customization).

**Drive Mad: low input count, demanding physics.** Poki describes two controls, acceleration and reverse/braking, with short retries and increasingly tricky physical situations. That makes a credible keyboard/touch crossover; it does not make the game easy. Its ad-based skip is one product choice. Conflicting localized content counts prevent a verified current total; ratings do not measure retention. [Poki listing](https://poki.com/en/g/drive-mad).

**SWOOOP: deliberately constrained arcade design.** A single held input raises the biplane; releasing lowers it. Keyboard, mouse and touch map to the same mechanic. Gem collection and finite fuel supply a compact score loop. PlayCanvas's 2014 post says two developers made it in four weeks; this is historical engine-vendor testimony, not a modern production estimate. Good teaching/reference project; no financial success claim. [Game](https://playcanvas.itch.io/swooop), [development account](https://blog.playcanvas.com/swooop/).

**Shell Shockers: memorable character over generic realism.** Blue Wizard identifies its egg-based FPS as a studio title; Babylon's current showcase links it as a shipped engine example. Its instantly describable premise is a useful brand lesson. These sources do not establish fair matchmaking, current device support or profit. Avoid same-name SEO mirrors: some assert incompatible save/account/device behavior and are not the developer. [Studio](https://bluewizard.com/), [engine showcase](https://www.babylonjs.com/games/).

**Krunker: a valuable negative case, not a blanket verdict.** A November 2024 Reddit post by a player claiming roughly 500 hours criticized weak team identity, a costly minimap, mismatched cosmetic art and monetization drift. Replies disputed the teamwork criticism; others agreed about the minimap. This supports specific risks to test, not population consensus or a causal decline story. A separate 2019 thread reported higher frame rates with ads blocked, but its uncontrolled hardware tests cannot establish a general numerical ad penalty. [Long-term complaint and disagreement](https://www.reddit.com/r/KrunkerIO/comments/1go8kvn/krunker_is_fundamentally_flawed_heres_how/), [ad-performance reports](https://www.reddit.com/r/KrunkerIO/comments/ca4434/getting_70_fps_difference_with_ads_enableddisabled/).

**TANX: popularity did not pay the maintenance opportunity cost.** PlayCanvas says its multiplayer tank game gained attention, then went offline when staff focused on the engine; it returned in June 2020. Its short sessions, shared match URLs and device reach did not eliminate service work. This is a documented maintenance shutdown, not proof of commercial failure or current unavailability. Budget ongoing ownership before choosing a service-dependent core. [Official retrospective](https://blog.playcanvas.com/tanx-lives-popular-webgl-online-game-returns/).

**Historical browser versions need rechecking.** Slide in the Woods has a 2021 “Web and linux build” devlog, but the current developer page offers a Windows download, not HTML5. Do not count historic browser coverage or unofficial embeds as a current official browser release. Its removal reason is not established by those pages. [Developer page](https://jonnys-games.itch.io/slide-in-the-woods).

## Visual directions: evidence-backed design hypotheses

These are coherent directions, not claims of a universal 2026 trend. See the direct inspection section for observed appearance.


- **Scenic restraint — Slow Roads.** Spend visual attention on road, horizon, weather and landscape. Small quiet overlays fit contemplative driving; muted environmental color and open composition support escape. Avoid a daily-reward wall, dense telemetry or high-frequency HUD animation. Risk: beautiful emptiness is weak value for players seeking competition. The direct inspection section records current typography and density. [Official site](https://slowroads.io/).

- **Handcrafted toy — Townscaper.** Compact colorful architecture, water and a palette can carry identity without a conventional home screen. Favor immediate world response and minimal control chrome. Avoid simulating a city-management game through fake statistics or adding goals only because other games have them. Risk: limited challenge is a real audience filter. [Independent review](https://www.pcgamer.com/townscaper-review/).

- **Readable sport — Narrow One / PolyTrack.** Strong silhouettes, deliberate geometry and clear routes make movement or aim legible. Keep competitive signals plain; reserve decoration for character/garage screens.  Avoid mixing a bright readable base with progressively ornate assets. Risk: “low poly” does not by itself guarantee frame rate or distinctive art. [Narrow One devlog](https://pelicanparty.itch.io/narrow-one/devlog/536795/spilling-our-trade-secrets-narrow-one-updates-), [PolyTrack](https://kodub.itch.io/polytrack).

- **Bright miniature arcade — SWOOOP / Drive Mad.** A contained diorama, obvious collectible/hazard forms and few controls make the scene readable at small size. Match rounded/boxy proportions and UI weight throughout; keep retry motion short. Avoid rendering a desktop game's tiny dense controls on a phone. Risk: attractive toy geometry can hide demanding physics; signal difficulty honestly. [SWOOOP](https://playcanvas.itch.io/swooop), [Drive Mad](https://poki.com/en/g/drive-mad).

## Direct visual inspection, 2026-11-08

Inspected in the desktop in-app browser at 1280×720; this is a small observation sample, not a device compatibility or accessibility audit.

**Slow Roads 2.4.2.** Entry uses a blurred landscape, thin widely spaced wordmark, one high-contrast Begin pill, and subordinate About/Discord/Steam links. Begin leads through “Loading environment” into a road-first scene: car low-center, horizon clear, tiny speed/distance readouts and a minimal bottom control strip. Settings use a full-width tab row, aligned label/control columns, section headers and per-section Reset; Gameplay exposes steering assistance, one-pedal driving, pause-on-unfocus, units and camera options. This supports calm exploration. Small low-contrast HUD text and custom controls deserve separate readability/keyboard tests; the accessibility tree exposes several interactive-looking items as text, which is a test lead rather than proof of complete keyboard failure. [Inspected game](https://slowroads.io/).

**Townscaper browser demo.** A small pastel building sits in a large teal water field; the left edge holds color swatches and the right gear reveals a narrow tool rail. The rail labels this as a demo, links full editions, and groups Undo/Redo, grid/light controls and audio. Hand-drawn edges, warm roofs, subtle reflection and abundant empty space make construction the focus. The tree exposed no semantic controls in this sample; a canvas toy needs deliberate accessible controls outside the bitmap. Loading initially showed an unlabeled progress bar; the scene eventually loaded. This was not a timed loading benchmark. [Inspected demo](https://oskarstalberg.com/Townscaper/).

**Narrow One.** The entry scene uses broad flat green/gray masses, angular cliffs, a central tower, archery targets and a bow at the right edge. Large outlined “Click to join” text remains readable against the scene. A privacy dialog appeared before play, with More options, Disagree and Agree; declining returned to the entry scene. This shows the real first-session cost of an ad-supported product even when the game itself has a short entry path. No live match or claim about input latency was tested. [Inspected game](https://narrow.one/).

**SWOOOP.** The start screen uses a large red/blue biplane, faceted island, warm sky and a bold blue badge. A large triangular Play control leads into a side-on scene with a large score and pause icon; a short unattended run reached Game Over. These sampled states show a consistent arcade visual vocabulary and a strong silhouette; they do not measure control feel or smoothness. This is a historical engine showcase still available, not evidence of a current visual trend or commercial hit. [Inspected game](https://playcanv.as/p/JtL2iqIH/), [2014 developer account](https://blog.playcanvas.com/swooop/).

## Screen compositions to prototype

These are proposed compositions, not observed layouts or user-approved product scope.

**Instant arcade.** On arrival, let the playable scene dominate; place a compact control hint beside one Start action. During play, retain only score, remaining resource and pause. After failure, preserve the scene, show score/best and put Retry in a stable location. Keep rewarded continuation visually separate. Test pointer/touch release so the failed action does not also trigger Retry. Grounding: SWOOOP's constrained loop and CrazyGames entry/ad guidance above.

**Team shooter.** Entry foregrounds Play, chosen class and squad joining; appearance editing stays secondary. In-game hierarchy: aim/near threats, objective and team state, then optional feed/minimap. Pause releases pointer and exposes controls, sound, reporting and Leave; leave must explain live-match consequences. End-of-round keeps squad identity visible and offers a clear next-round transition. Grounding: Narrow One and CrazyGames multiplayer guidance above.

**Time trial and editor.** Track list shows title, author, completion/personal best and a stable Play action; filters appear when catalog size merits them. Race HUD keeps timing, split and checkpoint status away from the road. Results lead to Retry, Replay and Next. Editor reserves explicit areas for parts, selection tools and test/save/share; nested import/export dialogs cannot also dismiss the editor. Grounding: PolyTrack's published feature and fix history above.

**Contemplative toy.** Start with the landscape or creation canvas and a terse cue. Group environment, camera and sound controls in a small retrievable panel; hide chrome without hiding the way back. Reset/clear must differ from routine scene manipulation. Provide optional share/export only when the product actually preserves a meaningful creation. Grounding: Slow Roads' stated purpose and Townscaper's reviewed creative use; see direct visual inspection above.

## Useful design resources

**Kenney.** Current asset catalog separates 3D, UI, audio and input prompts; use coherent packs to prototype an entire visual language. Do not combine incompatible packs merely because they are available. Inspect each pack license before shipping. Catalog availability alone is not a license audit. [Catalog](https://kenney.nl/assets).

**Game-icons.net.** Large editable monochrome game-icon collection. The site specifies CC BY 3.0 and crediting the original author. Suitable for inventory/action language; dense silhouettes still need small-size tests, and icons need text where meaning is ambiguous. [About/licensing](https://game-icons.net/about.html).

**Developer changelogs as component references.** PolyTrack exposes real fixes for safe areas, nested Escape, embedded-page scrolling, loading fonts and leaderboard timestamps. This is stronger shipped-state evidence than a polished mockup, although not proof that all bugs are now absent. [0.5.1](https://kodub.itch.io/polytrack/devlog/987596/polytrack-051-shadows-editor-undo), [0.6.0](https://kodub.itch.io/polytrack/devlog/1454034/polytrack-060-multiplayer-car-customization), [0.6.3](https://kodub.itch.io/polytrack/devlog/1665945/polytrack-063-track-of-the-week).

**Game Accessibility Guidelines.** Practical cross-game patterns and testimony. Use full-menu input access, rebinds, subtitles and motor-access considerations early. Examples may be historical/non-browser; check browser behavior independently, and do not treat cited user complaints as prevalence data. [Basic index](https://gameaccessibilityguidelines.com/basic/).

## Further design resources and a narrative exception

**Interface In Game — accessible catalog.** The live index groups real game screens by task (lobby, loading, inventory, game-over, settings), genre and visual theme; it also links video and interviews. Useful for comparing the same component across several shipped games. Its current index contains 2026 entries, but coverage is mostly broader PC/console/mobile work, not a browser support guide. The footer reserves game imagery to its owners: reference material, not reusable assets. We read the catalog and interviews; no claim of playing those games. [Catalog](https://interfaceingame.com/).

**Game UI Database — verify through accessible owner and independent coverage.** Direct access failed, but creator Edd Coates documents the August 2024 version's video, color and detailed search tools. Riley MacLeod's independent Aftermath article explains why comparing crafting and lockpicking interfaces is useful. Treat this as a well-supported resource recommendation, not direct inspection of its current catalog. [Creator](https://eddcoatesdesign.com/), [Aftermath, 7 August 2024](https://aftermath.site/game-ui-database/).

**Veteran view: motion should direct attention.** Sarah Robinson, identified in the interview as Dead by Daylight's lead UI designer with web/app experience, distinguishes a consistent interaction language from visual guidance through contrast, layout and carefully placed animation. She values making player intent easy to execute. Derived browser application: animate the newly unlocked action or changed state, rather than every panel; keep menu transitions shorter than a frequent retry. This is professional judgment, not an experiment or a browser-wide visual rule. [Interview](https://interfaceingame.com/articles/interview-with-sarah-robinson).

**Veteran counterweight to attractive mockups.** Emmanuel Vasquez Jr., interviewed as a senior Gameloft UI artist/animator, describes abandoning designs the team loved when players could not use them. His process joins UI art and animation from concept through implementation. Marc Sodermanns, whose background includes browser games, argues for early UX work and repeated player tests; he also recounts projects that failed financially despite professional design work. The practical conclusion is to test a coherent visual direction in an actual embedded game, not approve a static mood board as evidence of usability or viability. [Vasquez interview](https://interfaceingame.com/articles/interview-with-emmanuel-vasquez-jr), [Sodermanns interview](https://interfaceingame.com/articles/interview-with-marc-sodermanns).

**Inter — readable neutral utility text.** The owner repository documents tall x-height, tabular numbers and slashed zero under SIL OFL 1.1. Good candidate for timing, settings and account UI; pair it with a restrained display face if the game needs stronger character. The owner warns alternate distributions can lag; acquire a pinned official release and include its license. Test actual rasterization and localized glyphs; a font name is not a readability guarantee. [Owner repository](https://github.com/rsms/inter).

**Noto CJK — deliberate script coverage.** The project supplies language-specific CJK families and multiple packaging formats. Choose the languages, glyph set and font strategy rather than loading every regional font on first play. Broad coverage has a transfer/memory cost, especially for canvas atlases. Read the repository's font license and release instructions; test Japanese/Chinese/Korean shaping and fallback in the actual rendering path. [Owner repository](https://github.com/notofonts/noto-cjk).

**Codrops/The Aviator — source-based motion reference, not a starter stack.** The original 2016 tutorial and license pages returned 403; its author repository remains accessible, with the demo's source, Three.js and TweenMax credits. Its README permits building upon it for personal/commercial projects but forbids republishing or selling it unchanged. Useful for studying a small animated 3D scene; old dependency APIs need migration. Do not call it MIT or copy it wholesale. [Author repository](https://github.com/yakudoo/TheAviator).

**Tween.js and Three.js examples — implementation references.** Tween.js offers MIT-licensed interpolation without imposing a rendering engine; Three.js's own examples show engine-specific animation, materials and loading techniques. Use them for isolated behavior prototypes, then integrate time, cancellation and lifecycle with the game's loop. Examples demonstrate mechanisms, not a tested complete game or permission to ignore separate asset licenses. [Tween.js](https://github.com/tweenjs/tween.js), [Three.js examples](https://threejs.org/examples/).

**The Open House — a supported browser horror/exploration case.** Corpsepile's current page offers an HTML5 Unity build and native downloads. Its premise wraps exploration in a fictitious real-estate tour. The creator warns about WebGL trouble and separately warns streamers about a system-username reveal; the latter must not be read as evidence that the browser build can retrieve the operating-system username. Browser/native behavior needs separate testing. [Current developer page](https://corpsepile.itch.io/the-open-house).

PekoeBlaze's detailed 2022 review praised the contrast between corporate cheer, ordinary rooms, old software presentation and growing dread. It also reported needing a walkthrough for one clue and roughly 20–30 minutes to finish. Sidequest independently praised the familiar house becoming spatially uncanny in October 2023. These support a coherent visual direction: restrained faux-corporate UI and selective corruption can tell the story; maximal gore or constant jump scares are unnecessary. A frustrated player comment called the suspense unrewarding, so slow pacing is an audience tradeoff. No live playtest or profitability claim. [Review](https://pekoeblaze.wordpress.com/tag/the-open-house/), [Sidequest](https://sidequest.zone/2023/10/23/ten-short-horror-games-on-itchio/), [contrasting player comments](https://corpsepile.itch.io/the-open-house/comments?before=1005).

**Horror exception to ordinary UI cleanliness.** A fiction may deliberately corrupt its in-world interface, hide information or restrict movement. Keep real exit, volume, content information and recovery dependable. Test whether a stalled clue looks intentional or broken. This is derived guidance from The Open House critiques, not permission to spoof real browser security prompts or mishandle personal data.

## Accessibility foundations

The Game Accessibility Guidelines prioritize remapping, readable text, color-independent information and clear subtitles, while warning that complaint frequency differs from unmet need. Treat this as specialist guidance, not browser-game-specific prevalence. Keep gameplay and menus operable through the same supported input; save accessibility settings. [Basic guidance](https://gameaccessibilityguidelines.com/basic/).

For 3D camera comfort, expose appropriate FOV and test its interaction with distance to the screen; one number cannot suit a phone, laptop and ultrawide equally. Avoid mandatory shake, head bob and zoom punches; offer reduced-motion alternatives that retain essential cues. The guidelines’ FOV discussion is advice, not a universal guarantee against discomfort. [FOV guidance](https://gameaccessibilityguidelines.com/if-the-game-uses-field-of-view-3d-engine-only-set-an-appropriate-default-for-the-expected-viewing-environment/), [XAG 117](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/117).

A canvas does not expose its drawn objects as semantic HTML. Provide real buttons, headings, focus handling and text equivalents for menus, purchases, settings and status; use a scene accessibility model where the genre can support it. A single label describing the canvas does not make a spatial game playable without vision. Test keyboard and assistive technology with players; state supported features honestly. [MDN canvas accessibility](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/canvas).

## Practical reference: gameplay, creation and social play

### Entry, tutorial and input


1. **First action.** Put the playable action on the first screen; avoid launcher-like menu trees. CrazyGames Full implementations require gameplay immediately or within one click. A complex game may need selection, but name the necessary choice. [Platform rule](https://docs.crazygames.com/requirements/gameplay/).


2. **Teach by doing.** Introduce the immediate action in the scene; defer inventory, meta-currency and advanced movement. A skippable prompt lets returning friends join quickly. A wall of all controls teaches nothing at the moment of use. [Platform guidance](https://docs.crazygames.com/requirements/quality/).


3. **Promise the right activity.** Say “drive and relax,” “beat your time” or “capture the flag.” Do not imply progression where there is none. Townscaper's reviewer enjoyed it as a toy and explicitly rejected it as a challenge game. [Review](https://www.pcgamer.com/townscaper-review/).


4. **Simple controls can retain depth.** Test one-button or two-button mechanics before adding steering, camera, jump and inventory. SWOOOP maps one action across input devices; difficulty comes from timing. This suits arcade play, not every 3D genre. [SWOOOP](https://playcanvas.itch.io/swooop).


5. **Capture the pointer deliberately.** Start FPS look control after a clear play gesture; show a re-entry state if locking fails. Do not assume the cursor is confined because the canvas has focus. Pointer lock and drag capture solve different problems. [MDN](https://developer.mozilla.org/en-US/docs/Web/API/Pointer_Lock_API).


6. **Escape must release control.** Explain how to leave pointer lock and restore menus. Do not repeatedly recapture after the player leaves. A tiny embedded game must not make the next click fire into surrounding page controls. [Mouse-control guidance](https://docs.crazygames.com/resources/mouse-control/).


7. **Reach menus with gameplay input.** A keyboard-only game needs keyboard-accessible pause, settings and retry; controller play needs controller menus. One mouse-only button can exclude someone who can otherwise play. [Accessibility guidance](https://gameaccessibilityguidelines.com/ensure-that-all-areas-of-the-user-interface-can-be-accessed-using-the-same-input-method-as-the-gameplay/).


8. **Remapping includes prompts.** Show the chosen binding in tutorial and HUD hints. Presets alone cannot cover one-handed use, different keyboards or impairment. Detect collisions and retain a way to restore defaults; the latter are implementation inferences. [Remapping guidance](https://gameaccessibilityguidelines.com/allow-controls-to-be-remapped-reconfigured/).


9. **Touch buttons need space.** Separate steer, brake and restart hit areas; avoid packing desktop icons under thumbs. Test reduced dexterity as well as fast players. Physical size and spacing matter more than the icon's apparent neatness. [Touch guidance](https://gameaccessibilityguidelines.com/ensure-interactive-elements-virtual-controls-are-large-and-well-spaced-particularly-on-small-or-touch-screens/).


10. **Respect handedness and cutouts.** Offer sensible left/right arrangements and keep controls clear of safe areas. PolyTrack 0.5.1 added side switching and safe areas; a touch button hidden by hardware is a functional failure. [Release](https://kodub.itch.io/polytrack/devlog/987596/polytrack-051-shadows-editor-undo).

### World, camera and HUD


11. **Landmarks beat clutter.** Put the objective where a newcomer can orient, then add optional shortcuts. A minimap should earn its screen and render cost. [Developer rationale](https://pelicanparty.itch.io/narrow-one/devlog/536795/spilling-our-trade-secrets-narrow-one-updates-).


12. **Routes communicate risk.** Make fast exposed paths and slower cover distinguishable. Do not decorate every surface equally. [Developer rationale](https://pelicanparty.itch.io/narrow-one/devlog/536795/spilling-our-trade-secrets-narrow-one-updates-).


13. **Budget HUD rendering.** Measure optional overlays on weak devices. A minimap that costs frame pacing without useful navigation can damage an otherwise simple-looking game. The Krunker complaint is a hypothesis to reproduce, not a measured engine diagnosis. [Player discussion](https://www.reddit.com/r/KrunkerIO/comments/1go8kvn/krunker_is_fundamentally_flawed_heres_how/).


14. **Keep team cues redundant.** Pair colors with shapes, outlines or labels; a red/green team split alone excludes players. Preserve cue meaning in low quality and varied lighting. [Basic accessibility guidance](https://gameaccessibilityguidelines.com/basic/).


15. **Readable at embedded size.** Design text for the actual iframe, not a fullscreen marketing capture. CrazyGames explicitly tests smaller desktop frames and pixel ratio 1. Scaling down a complete 1080p HUD is not adapted UX. [Requirements](https://docs.crazygames.com/requirements/gameplay/).


16. **Comfort controls belong early.** Offer reduced camera shake, sensible field of view and stable reference cues where the mechanic allows. Avoid forcing cinematic camera motion throughout play. VR needs additional locomotion rules; do not transfer VR numerical targets wholesale to flat games. [Comfort guidance](https://gameaccessibilityguidelines.com/avoid-vr-simulation-sickness-triggers/).


17. **Subtitles survive bright scenery.** Offer readable size and a background plate; keep other HUD elements out of that region. Stylish thin white text over clouds fails precisely when dialogue matters. [Subtitle guidance](https://gameaccessibilityguidelines.com/if-any-subtitles-captions-are-used-present-them-in-a-clear-easy-to-read-way/).


18. **Separate audio channels.** Give music, effects and speech independent control; mirror essential audio cues visually. A single master slider forces players to lose useful feedback to silence repetitive music. [Accessibility guidance](https://gameaccessibilityguidelines.com/basic/).

### Retry, progression and creation


19. **Fast retry keeps skill practice intact.** Reset a failed attempt without navigating menus. PolyTrack's short improvement loop makes errors actionable; delays turn correction into waiting. Avoid confirmation for ordinary retry, but protect unsaved creations separately. [Poki description](https://poki.com/en/g/polytrack).


20. **Separate retry from checkpoint respawn.** Use distinct labels and bindings; show when a checkpoint is available. PolyTrack shipped a mobile checkpoint indicator. Ambiguous restart can erase a player's hard-won progress unintentionally. [0.5.1 release](https://kodub.itch.io/polytrack/devlog/987596/polytrack-051-shadows-editor-undo).


21. **Make improvement visible.** Show personal best, split or ghost where meaningful; avoid rewarding only global winners. PolyTrack's replay/checkpoint tools make mastery inspectable. A casual toy can omit scoring entirely. [Poki description](https://poki.com/en/g/polytrack).


22. **Offer a way past a repeated failure.** Consider practice, assist or optional skip. Drive Mad documents a rewarded-ad skip; do not infer that monetizing relief is necessary. Test whether the obstacle teaches timing or merely traps the player. [Poki description](https://poki.com/en/g/drive-mad).


23. **Creation requires undo.** Make track edits reversible before promoting a creation community. PolyTrack added editor undo/redo in 0.5.1. A forgiving play loop alongside destructive authoring is an avoidable mismatch. [Release](https://kodub.itch.io/polytrack/devlog/987596/polytrack-051-shadows-editor-undo).


24. **Share portable creations.** Export/import a track with visible success and validation feedback. PolyTrack's developer page exposes sharing as a core feature. Do not make the only surviving copy a screenshot or temporary tab. [Developer page](https://kodub.itch.io/polytrack).


25. **Close the topmost dialog only.** Escape from an import error should return to import, not close the underlying editor too. PolyTrack 0.6.0 fixed multiple nested-dismissal faults. Track dialog layering explicitly. [Release](https://kodub.itch.io/polytrack/devlog/1454034/polytrack-060-multiplayer-car-customization).


26. **Track selection needs search.** Search by author as well as title when community content grows; avoid endless undifferentiated thumbnails. PolyTrack shipped author search, then version tabs for community tracks. The latter fit release collections, not every catalog. [0.5.1](https://kodub.itch.io/polytrack/devlog/987596/polytrack-051-shadows-editor-undo), [0.6.3](https://kodub.itch.io/polytrack/devlog/1665945/polytrack-063-track-of-the-week).


27. **Explain scores precisely.** Show a useful relative record age with an exact timestamp on inspection. PolyTrack 0.6.3 does this. Do not let “yesterday” obscure a competition cutoff; public records also need moderation. [Release](https://kodub.itch.io/polytrack/devlog/1665945/polytrack-063-track-of-the-week).


28. **Version user content deliberately.** Keep old tracks/replays identifiable across simulation changes; test migration before deleting records. PolyTrack's compatibility statements show that cross-version behavior is a product concern. Compatibility here is release-specific, not permanent. [0.6.3](https://kodub.itch.io/polytrack/devlog/1665945/polytrack-063-track-of-the-week).

### Friends, ads and service states


29. **Invitation joins the promised room.** Skip redundant onboarding for invited players; say when the room is unavailable. Do not silently place a friend in another public match. [CrazyGames multiplayer guidance](https://docs.crazygames.com/requirements/multiplayer/).


30. **Keep friends together next round.** Reuse the room or move the group together. Returning each player to matchmaking breaks the social purpose of the link. [Platform requirement](https://docs.crazygames.com/requirements/multiplayer/).


31. **Joining late needs a real state.** Offer spectating or a clear unavailable message, not an endless spinner. Rejoining should work without a full page reload where possible. [Platform guidance](https://docs.crazygames.com/requirements/multiplayer/).


32. **Do not punish every departure.** Browser sessions suffer interruption. Consider reconnect and completion incentives before currency penalties; Narrow One explicitly recognized legitimate exits. This is a tradeoff, not permission to leave competitive abandonment unaddressed. [Developer discussion](https://pelicanparty.itch.io/narrow-one/devlog/536795/spilling-our-trade-secrets-narrow-one-updates-).


33. **Chat is an operated feature.** Provide moderation and a way to disable it; names and uploaded assets also carry abuse. A profanity filter is a platform minimum, not proof that harassment is solved. [Platform rules](https://docs.crazygames.com/requirements/multiplayer/).


34. **Put ads at breaks.** Never interrupt steering or aiming, or make Settings trigger an ad. Natural failure/level transitions fit better. [Platform rules](https://docs.crazygames.com/requirements/ads/).


35. **Make reward choice honest.** Label the ad and reward; keep the decline path visible and equivalent. Tiny delayed “No thanks” is not a valid difficulty setting. [Platform rules](https://docs.crazygames.com/requirements/ads/).


36. **Unfilled ads must resolve.** Resume after an ad error; grant the promised reward only on the correct completion callback. A request is not a watched ad. [Platform rules](https://docs.crazygames.com/requirements/ads/).


37. **Mute only when an ad starts.** Restore the player's prior volume afterward; do not dip music for an auction that returns no ad. [Platform rules](https://docs.crazygames.com/requirements/ads/).


38. **Allow normal play with blockers.** Explain unavailable rewarded features rather than leaving dead buttons or blocking the game. CrazyGames requires this behavior; direct-hosted policy choices still have trust costs. [Platform rules](https://docs.crazygames.com/requirements/ads/).

### Interruptions, settings and errors


39. **Backgrounding is a state transition.** Pause safe solo play, stop unwanted audio and resynchronize multiplayer on return. Browsers throttle hidden-tab work; simulating elapsed wall time as one huge frame is wrong. [MDN visibility](https://developer.mozilla.org/en-US/docs/Web/API/Page_Visibility_API).


40. **Settings must persist.** Restore accessibility, sound and control choices before play. Requiring a player to fight through inaccessible defaults every visit negates the setting. [Accessibility guidance](https://gameaccessibilityguidelines.com/basic/).


41. **Language changes should be visible immediately.** Reflow labels and selected controls when changing locale. PolyTrack 0.6.0 changed language updates to apply immediately; avoid requiring restart. [Release](https://kodub.itch.io/polytrack/devlog/1454034/polytrack-060-multiplayer-car-customization).


42. **Errors must sit above the toolbar.** Give recovery controls focus and a clear close path. PolyTrack fixed error-screen occlusion and failed-network crashes; show recovery in the UI. [Release](https://kodub.itch.io/polytrack/devlog/1454034/polytrack-060-multiplayer-car-customization).


43. **Quality settings must affect cost.** Provide lower render scale and optional effects before recommending new hardware. PolyTrack added lower scales and deferred editor/garage loading. Verify quality reduction does not hide gameplay signals. [Release](https://kodub.itch.io/polytrack/devlog/1454034/polytrack-060-multiplayer-car-customization).


44. **Cosmetics need an art contract.** Preserve silhouette, readability and material density as the catalog grows. A long-term Krunker player objected to mismatched high-detail cosmetics beside the original characters. That is individual criticism, but a useful review prompt for every new asset pack. [Discussion](https://www.reddit.com/r/KrunkerIO/comments/1go8kvn/krunker_is_fundamentally_flawed_heres_how/).

## Practical reference: browser integration and recovery

45. **First play:** load the first useful scene before distant levels or optional music. A branded loader followed by another opaque loader feels broken. Staged loading works only when each stage exposes real progress. [PlayCanvas load sequence](https://developer.playcanvas.com/user-manual/optimization/load-time/).

46. **Progress:** label downloading, preparing and connecting separately. Byte completion is not shader/scene readiness. Expose retry for a failed asset rather than inventing percentages. [PlayCanvas profiling](https://developer.playcanvas.com/user-manual/optimization/).

47. **Asset quality:** offer graphics presets before entering an expensive scene. Lower shadows/resolution first while keeping targets readable; never hide a minimum-performance failure behind a permanently moving spinner. [PlayCanvas optimization](https://developer.playcanvas.com/user-manual/optimization/).

48. **Retina:** keep menus sharp while lowering scene resolution. Rendering every physical pixel by default can overheat a laptop or phone without adding useful detail. [Pixel ratio](https://developer.playcanvas.com/user-manual/optimization/device-pixel-ratio/).

49. **Fullscreen:** make it optional and reversible; resize after changes. A failed permission request must leave windowed play intact. Embedded games need host permission. [Fullscreen](https://developer.mozilla.org/en-US/docs/Web/API/Fullscreen_API).

50. **Focus loss:** clear held movement/fire keys when focus disappears. Missing a key-up must not leave a character walking or shooting on return. [Lifecycle](https://developer.chrome.com/docs/web-platform/page-lifecycle-api).

51. **Discard recovery:** checkpoint meaningful progress during play. Saving only when the tab closes loses progress on process kill/discard, and unload is no longer dependable. [Unload deprecation](https://developer.chrome.com/docs/web-platform/deprecating-unload).

52. **Sound unlock:** resume the audio context from Play, with a visible mute toggle. Failed autoplay must not turn into a repeated permission nag. [Autoplay](https://developer.mozilla.org/en-US/docs/Web/Media/Guides/Autoplay).

53. **Local-save warning:** tell players when saving failed and retain the current session state if possible. Do not show “saved” merely because a synchronous local setting write succeeded. [Storage](https://developer.mozilla.org/en-US/docs/Web/API/Storage_API/Storage_quotas_and_eviction_criteria).

54. **Cloud indicator:** distinguish local checkpoint, upload pending and confirmed cloud revision. A connection icon alone cannot prove a save reached the server. This is derived from the separate storage/network failure modes. [IndexedDB wrapper](https://github.com/jakearchibald/idb), [WebSocket](https://developer.mozilla.org/en-US/docs/Web/API/WebSocket).

55. **Touch cancellation:** reset a virtual stick/fire button on pointercancel and lost capture. Do not assume every touch ends with pointerup. [Pointer events](https://developer.mozilla.org/en-US/docs/Web/API/Pointer_events).

56. **Gesture boundary:** disable browser pan only inside active controls/play surface. Disabling page zoom and scrolling everywhere makes surrounding help and account pages harder to use. [Pointer events](https://developer.mozilla.org/en-US/docs/Web/API/Pointer_events).

57. **Controller arrival:** switch hints when the player actually uses a controller; retain mouse navigation. A connected unused controller should not erase keyboard instructions. [Gamepad guide](https://developer.mozilla.org/en-US/docs/Web/API/Gamepad_API/Using_the_Gamepad_API).

58. **Controller loss:** pause solo play and show reconnection/alternate-input choices. Avoid an invisible lost-input state while hazards continue. [Gamepad guide](https://developer.mozilla.org/en-US/docs/Web/API/Gamepad_API/Using_the_Gamepad_API).

59. **Context loss:** show recovery status and rebuild resources or offer a safe reload. A black canvas with live audio is a failure, not a loading screen. [Context loss](https://developer.mozilla.org/en-US/docs/Web/API/WebGLRenderingContext/isContextLost).

60. **Shader warmup:** prepare likely first-use materials before a competitive encounter; measure compilation stalls. Do not hide every possible shader in the initial download if most players never use it. [PlayCanvas profiler](https://developer.playcanvas.com/user-manual/optimization/).

61. **Retry:** preserve scene/menu selection when a request fails; bound automated retry and offer manual retry. Re-downloading the full build for one failed optional asset wastes time and bandwidth. [PlayCanvas load time](https://developer.playcanvas.com/user-manual/optimization/load-time/).

62. **Disconnect:** show reconnecting, timeout and rejoin outcomes distinctly. A frozen last frame with live inputs implies actions were accepted when they were not. [Colyseus](https://github.com/colyseus/colyseus).

63. **Congestion:** limit queued state updates and expose sustained connection trouble. Increasing send frequency indefinitely can consume memory and worsen delay. [WebSocket](https://developer.mozilla.org/en-US/docs/Web/API/WebSocket).

64. **Server authority:** display confirmed rewards separately from provisional animation. Never trust client-submitted currency or victory solely because the UI reached its win screen. An authoritative framework still needs correct validation. [Colyseus](https://github.com/colyseus/colyseus).

65. **Update boundaries:** keep one coherent version of code/assets for an active session; update between sessions. A service worker swapping assets midway can invalidate loaded content or save assumptions. [Workbox](https://github.com/GoogleChrome/workbox).

66. **Offline choice:** distinguish “downloaded level” from “requires connection.” Do not promise offline mode because the title screen appears from cache. [Godot export](https://docs.godotengine.org/en/stable/tutorials/export/exporting_for_web.html).

67. **Unsupported GPU:** explain the missing capability before the expensive download when possible, with tested browser/device alternatives. Do not send players to unsafe experimental flags as normal onboarding. [WebGPU](https://developer.mozilla.org/en-US/docs/Web/API/WebGPU_API).

68. **Debug report:** offer build ID, renderer, browser, scene and sanitized error code. Avoid copying tokens, chats or full local saves into telemetry by default. [Spector.js](https://github.com/BabylonJS/Spector.js) provides graphics debugging; product diagnostics need deliberate data boundaries.

69. **Test the embedded flow:** account, ads, fullscreen, pointer capture and persistence must work in the real host. Passing a standalone browser test does not prove iframe permissions or cross-origin storage work. [Isolation guide](https://web.dev/articles/cross-origin-isolation-guide).

## Practical reference: localization, accessibility and continuity

The following are derived implementation recommendations. Browser APIs support the mechanism; they do not prove a conversion uplift. Apply only to the features the game actually has.

70. **Chat composition.** Suspend gameplay shortcuts while a text field has focus; respect composition before submitting on Enter. Treating every keydown as a shot or a finished message breaks IME entry. Test Japanese/Chinese composition, pasted text and escape-to-cancel. [Composition events](https://developer.mozilla.org/en-US/docs/Web/API/CompositionEvent).

71. **Bidirectional names.** Isolate user names and room titles with suitable `dir`/`bdi` handling in the DOM. Simply concatenating an Arabic name with a score can reorder punctuation and misattribute text. Canvas text needs equivalent shaping/direction support. [Direction](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/dir).

72. **Currency and units.** Format prices and numbers for the selected locale; keep the currency unambiguous. Do not hardcode two decimals for every currency or parse a displayed localized number as a protocol value. [Intl.NumberFormat](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/NumberFormat).

73. **Multiple tabs.** Detect conflicting active sessions and choose an explicit rule: separate runs, one active multiplayer seat, or a handoff. Silent last-writer-wins can destroy progress. BroadcastChannel can notify same-partition contexts; it is not a lock or cross-device authority. [BroadcastChannel](https://developer.mozilla.org/en-US/docs/Web/API/Broadcast_Channel_API).

74. **Embedded identity.** Explain when an own-site session differs from a portal session. A same-origin iframe under another top-level site may be in a different storage partition; neither local messaging nor a familiar logo proves shared ownership. Use explicit authenticated handoff where supported. [BroadcastChannel partition boundary](https://developer.mozilla.org/en-US/docs/Web/API/Broadcast_Channel_API).

75. **Focus and semantics.** Use labeled focusable controls for menus, not clickable text painted into a scene. A decorative canvas description cannot expose a purchase dialog or settings state. Keep focus visible and return it to the opener after dismissal. [Canvas accessibility](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/canvas).

76. **Cover-to-game continuity.** Show the real central action, readable at thumbnail size; carry the same visual identity into first play. A cinematic render that promises a different game earns the wrong clicks. CrazyGames permits animation that represents actual gameplay, not misleading action. [Cover requirements](https://docs.crazygames.com/requirements/game-covers/).

77. **Preview motion.** Capture meaningful action immediately and frame it for each required aspect ratio. A long logo reveal consumes the preview. CrazyGames currently requests silent previews no longer than 15–20 seconds and separate landscape/portrait sizes; other hosts have different rules. [Preview requirements](https://docs.crazygames.com/requirements/game-covers/).

78. **Imported saves.** Validate version, structure, bounds and ownership before replacement; retain a recovery copy and show the imported profile summary. Treat a file as untrusted data. Never evaluate serialized script or grant server currency from a local save. [HTML5 security](https://cheatsheetseries.owasp.org/cheatsheets/HTML5_Security_Cheat_Sheet.html).

79. **Connection expiry.** When authentication expires, preserve safe local work and explain reauthentication. Leaving an old socket authorized after logout undermines account controls; abruptly returning to title without a reason looks like lost progress. [WebSocket security](https://cheatsheetseries.owasp.org/cheatsheets/WebSocket_Security_Cheat_Sheet.html).

80. **Map-sharing links.** Separate a stable seed/version from sensitive access credentials. A shared route should recreate the intended generation version or explain incompatibility, not silently show a different world after an algorithm update. Slow Roads’ visible seed/code is a useful affordance; compatibility policy is the developer’s responsibility. [Observed example](https://slowroads.io/).

81. **Empty creation surface.** Provide a manipulable example or a clear first action, not a blank world with twenty unexplained tools. Townscaper’s small initial building makes the material visible before menu exploration. A professional editor may instead favor an empty project and reusable templates. [Observed demo](https://oskarstalberg.com/Townscaper/).

82. **Tool grouping.** Group related creation controls and keep the object visible. Townscaper’s narrow rail preserves the scene while opening lighting/grid controls; a full-screen panel suits more complex settings. Avoid making purchase links visually indistinguishable from editing commands. [Observed demo](https://oskarstalberg.com/Townscaper/).

83. **Repeatable simulation.** Keep game speed independent of display refresh. Test the same steering/jump sequence at low and high refresh rates; per-frame movement increments can change difficulty across hardware. Bound catch-up after long stalls. [Game-loop chapter](https://gameprogrammingpatterns.com/game-loop.html).

84. **Reset scope.** Name what a reset affects: one binding, graphics preset, local profile or purchased account. Keep recoverable preference resets near their section; separate destructive progress deletion. Slow Roads’ per-section resets show a useful grouping pattern; destructive confirmation is derived guidance. [Observed settings](https://slowroads.io/).

85. **Readable progress at scale.** Test scores, odometers, inventory quantities and player names at their largest valid values. Slow Roads’ public changelog records fixes for digit overlap and odometer rollover; a three-digit mockup misses long-use failures. [Changelog](https://slowroads.io/).

## Practical reference: monetization


86. **Offer rewards clearly.** Label the reward and video requirement before a click; a disguised ordinary button burns trust. Keep the free action primary and immediate. Poki explicitly recommends this hierarchy. [Monetization guidance](https://developers.poki.com/guide/monetization).

87. **Use real pauses.** Results, safe respawn and deliberate upgrades are better candidates than an active jump, steering correction or firefight. An ad must not let the server kill a player who cannot act. Smash Karts supplies a concrete pause example; suitability depends on the game.

88. **Grant exactly the promised reward.** Persist rewarded-ad completion and entitlement safely; retries must not duplicate or erase it. A no-fill or cancelled video should return the player to a usable game. This is derived transaction guidance, not a claim that every SDK guarantees delivery.

89. **Show real purchase totals.** Explain duration, recurrence and whether an item is cosmetic. A tiny currency bundle obscures value and worsens fixed payment costs. Premium progression must not make paying the only practical way to enjoy the promised free loop.

90. **Separate saved progress from the current tab.** Explain guest/save/account boundaries before a player invests or pays. Do not promise cross-portal ownership when identifiers and contracts differ. Resolve duplicate purchases and account recovery before heavy monetization.

91. **Measure fatigue.** Ad revenue per session can rise while return rate falls. Where the channel gives you control, test ad frequency with return-rate and net-revenue guardrails. On Poki, follow SDK pacing; its requirements prohibit internal timers that force frequency. [Poki requirements](https://developers.poki.com/guide/requirements-quality).

92. **Keep a coherent economy.** Poki recommends one legible currency and clear rewards rather than secondary-currency complexity. This is its audience guidance, not proof that a deep strategy game can never need multiple resources. [Monetization guidance](https://developers.poki.com/guide/monetization).

93. **Earn a return through content.** Add new routes, skill expression or meaningful progression where they serve the loop. Daily streak penalties and arbitrary waiting may inflate visits while undermining a relaxed game. Slow Roads and competitive FPS games should not share one retention recipe.

## What the business must prove

Browser access removes installation, but also removes commitment. Measure discovery → page open → usable first frame → first meaningful action → completed loop → return → monetized session. “Conversion” must name its denominator and event. A portal view, a unique player, a play, a session, an ad impression and a purchase are different units.

The most useful split is between a small self-contained game, a repeat-play multiplayer service and a persistent creation/social world. The first can survive modest traffic with static hosting. The second needs enough simultaneous players in each region/mode and continuing security work. The third adds moderation, storage, account recovery and content governance. This is derived cost guidance, not a claim that one genre wins financially.

## Named cases and counterexamples

**Shell Shockers: a real web business, with a specific audience.** GameDiscoverCo's 2023-01-30 interview with founder Jason Kapalka reports low-seven-figure annual revenue, almost all from the web game; 80–90% came from ads. Remaining microtransaction revenue split roughly equally between cosmetics and VIP. The reported audience was 51% Windows, 39% Chromebooks and about 10% mobile, mostly ages 10–15; 47.6% of traffic was U.S. and 6.4% Canadian. The 2022 DAU chart followed school holidays. Kapalka stressed weak conventional marketing channels, social play and low-end hardware. His PopCap history and operating team matter: this is not a novice's expected result. Figures are an attributed founder account, not audited accounts or current telemetry. The lesson is to match device, social loop and monetization to the actual niche. [Direct founder interview](https://newsletter.gamediscover.co/p/deep-dive-shell-shockers-multi-million).

**Smash Karts: ads can fund a small studio without forcing purchase-first design.** In Google's 2023 publisher interview, Tall Team reported 70–80% ad revenue across its business and banners during the five-to-seven-second destruction/respawn interval. The founders funded development through client work before the March 2020 launch; releases were planned around parental leave. This is a vendor-selected success story with founder testimony, not an experiment proving that respawn ads maximize lifetime value. The useful lesson is to find an existing pause rather than lengthen death solely to show an ad. [Google interview](https://www.google.com/ads/publisher/stories/tall_team/).

**Smash Karts: separate sustainability evidence.** Imirt's July 2024 budget submission says Smash Karts was Tall Team's sole revenue source for four years and had reached 40M+ players across mobile and web. It describes growth from five people in 2023 to an expected eleven in summer 2024, helped by Ireland's games tax credit, plus contracted art in Ukraine. This corroborates sustained company activity, not a web-only profit figure; it is an industry advocacy document, and hiring plans are not verified final headcount. Subsidies, contractor costs and prior experience belong in the story. [Imirt submission, pp. 13–14](https://static1.squarespace.com/static/5553dcdfe4b0df27f2734788/t/6703f8540cd1df7b0cd9daab/1728313430704/Imirt%2BBudget%2BSubmission%2B2024_1.2.pdf).

**Vortelli's Pizza Delivery: reach and engagement, not disclosed profit.** The developer's November 2023 account reports six million plays in the first 30 days, eight million by publication, and 1.2M accumulated player-hours. A prior game already had 40M plays and supplied player feedback and a familiar world. The sequel's success cannot be attributed to engine choice or loading alone. Its 2.14MB initial download came from deferred map chunks and compression. Timed and untimed jobs addressed conflicting difficulty preferences; an explicit destination arrow fixed confusion that the minimap did not. Real-time shadows were disabled after rare blank-world reports; the root cause remained unproven. These are useful design and support lessons, but no before/after causal retention numbers or profit accounts were published. [Developer postmortem](https://poki.com/blog/6-million-plays-in-30-days-vortellis-pizza-delivery).

**Slow Roads: user value without web revenue.** In a 2025 Reddit discussion, account `anslogen` said the web version made no money, cost $25/month to host, and was funded by outside employment; donations had been stopped as unnecessary. The author estimated a little over two years of full-time-equivalent work and hoped for Steam sales. Treat this as a historical developer statement, not today's hosting bill or employment status. It demonstrates why a tiny infrastructure bill is not a profitable business: unpaid development is still labor. [Developer discussion](https://www.reddit.com/r/slowroads/comments/1jo6bta/what_is_the_income_of_a_game_like_slow_roads/). Attribution matches the author's original [project announcement](https://www.reddit.com/r/proceduralgeneration/comments/yauf3q/slowroadsio_my_javascript_project_to_generate/) and [portfolio](https://anslo.dev/). The current official site's indexed text says full-time development; do not repeat the old outside-job statement as current.

**Krunker: acquisition did not preserve the original community automatically.** Brian Meidell's September 2024 public letter accepts responsibility for neglecting Krunker.io after FRVR's 2022 acquisition while pursuing other channels. He reported 2.7M active players the prior month yet called scams, compromised accounts, cheating, server infrastructure and community repair urgent. This is an admission and historical scale claim, not proof of present failure or shutdown. Reader replies ask for returning creators and lapsed players; they are individual reactions. Lesson: a popular live service can erode despite substantial traffic when the operator diverts support from its core game. Budget maintenance before expansion. [Public letter and replies](https://www.reddit.com/r/KrunkerIO/comments/1ff1k0h/open_letter_to_the_krunker_community_future_of/).

**Doodle Stack: an adjacent 2D failure that tests portal assumptions.** A solo Japanese studio's November 2026 postmortem reports failing CrazyGames Basic Launch. Final D1 retention was 2.71% desktop and 0% mobile; one-minute conversion was 62.27% and 37.92%. The developer chose to continue on its own site. This is not a 3D comparator and reports a small early/mid-test population without final device-specific cohort sizes, but it shows that passing technical review and receiving traffic do not guarantee monetization. The author attributes the main weakness to insufficient reason to return; that causal diagnosis was not experimentally isolated. [Developer postmortem](https://nandemo-factory.com/en/articles/crazygames-teishutsu/).

## Conversion evidence: what was actually measured

**Stickman Hook's loading rewrite: large before/after association.** Poki reports a change from a 40MB WebGL build, 29.5-second median load and 50% conversion to a 6MB HTML5 build, 3.7 seconds and 72% conversion. That is **22 percentage points, or 44% more starts for equal page traffic**, not “22% more plays.” It is an adjacent 2D game and a bundled rewrite, not randomized isolation of file size, engine or load time. Cohort sizes and traffic comparability are not disclosed. It supports testing faster first play; it does not establish a universal seconds-to-revenue formula. [Poki account, 2026-05-16](https://poki.com/blog/what-makes-high-quality-browser-game).

**Cannon Clash: a relevant 3D achieved result.** Leonidas Maliokas reports a 2.4MB initial download, 76 requests and 81% conversion in Poki's Web Fit test in November 2024. Changes included compressed assets, delayed nonessential loading and removal of an opening story animation after observed impatience in playtests. No baseline, randomized control, sample size or isolated revenue uplift is given. Treat 81% as an achieved test outcome, not “optimization increased conversion by X.” [Developer account](https://poki.com/blog/how-we-made-cannon-clash-load-fast-and-boosted-conversion).

**Poki's benchmarks are portal-specific.** Current documentation defines conversion to play as reaching the first `gameplayStart()` event. It suggests 65%+ conversion and five-minute average playtime, or ten minutes for management/simulation. It distinguishes roughly 500-player interest tests, roughly 10,000-player web-fit tests and qualitative recordings. Those are editorial targets and test designs, not universal retention thresholds. Its 2024 Cannon Clash article called 70% solid and 80% exceptional; this is different framing, not evidence the whole market changed. [Reading results](https://developers.poki.com/guide/reading-results), [Web Fit test](https://developers.poki.com/guide/web-fit-test).

**CrazyGames measures a different conversion.** Its Basic Launch guide defines conversion as playing at least one minute after starting. Published strong-game indicators are 10+ average minutes, 10–15% D1 retention, and 80%+ one-minute conversion, with loading below ten seconds and builds below 20MB. Basic Launch runs at least seven days and 500 plays, capped at 21 days if 500 is not reached. These are guidance, not a guaranteed acceptance contract, and not directly comparable to Poki's start event. [Basic Launch guide](https://docs.crazygames.com/resources/basic-launch-metrics/).

**Derived measurement plan.** Record real first interaction, load failures, elapsed and active playtime, first-loop completion, day-based retention, ad availability/completion, purchase starts/completions, refunds and reconnects. Segment at least by device/input, region, acquisition source and new/returning user. Keep SDK events honest; moving `gameplayStart()` earlier can improve reported conversion without helping a player. In experiments, compare net revenue and returning players over a declared horizon, not ads shown alone. Guard against bots, repeat refreshes, school-calendar effects and survivor bias. For low traffic, playtest observations can locate blockers sooner than an underpowered A/B test.

## Distribution, contracts and economics

| Route | Practical fit and cost | Limits |
|---|---|---|
| Curated portal | Existing discovery, hosting, ad operation, QA and testing; strong fit for approachable repeatable games | Acceptance, editorial performance, SDK rules, restricted links and sometimes exclusivity; discovery is not owed forever |
| Nonexclusive portal portfolio | More channels, less single-portal dependence | Multiple SDK/auth/save/ad adapters, duplicated QA, inconsistent accounts; verify each contract |
| Own site | Own brand, links, experiments, accounts and payment model | Must earn traffic; CDN, security, consent, support, fraud and live-service costs stay with developer |
| itch.io | Low-friction demos, jams, experiments, donations and downloadable companions | A standard embedded HTML5 project takes donations, not a conventional browser paywall |
| Free web → paid native edition | Browser proves the core experience and reaches sharers; paid edition may justify richer content/offline play | No automatic conversion; portal outbound-link or exclusivity terms may block the intended funnel |
| Commissioned/branded game | Client pays for a defined experience rather than relying on ad scale | Delivery scope, campaign hosting term, analytics/privacy and continuing support need explicit pricing; not evidence of consumer demand |

**Poki terms checked 2026-11-08.** Its public overview describes 100% of revenue from directly arriving users and a 50/50 split for users Poki brings. Its deal page says preferred web exclusivity normally lasts five years and includes Discord and YouTube Playables, while native stores/consoles remain outside scope. Those are indicative; the signed agreement controls. A nonexclusive deal may instead pay a one-time license fee without revenue share. Therefore “Poki always takes half,” “Poki is always exclusive” and “web exclusivity only means competing portals” are all incomplete. [Overview](https://developers.poki.com/guide/working-with-poki), [Deal types](https://developers.poki.com/guide/revenue-deal-types).

**CrazyGames terms checked 2026-11-08.** Basic Launch has no monetization; Full Launch requires integration. Selected games can use invited in-game purchases through its Xsolla account. [Requirements](https://docs.crazygames.com/requirements/intro/). The 2025-08-18 general terms publish performance-based compensation rather than one universal revenue-share percentage. Optional two-month web exclusivity increases compensation by 50%; that is an increase in compensation, not a 50% revenue share. Terms include yearly renewal and up to one year of continued publication after termination for SDK-integrated games. Model the exit as well as entry. [Terms, articles V and IX](https://files.crazygames.com/documents/developer_terms_20250818.pdf). The FAQ specifies monthly payment after €100 accrued and hosting/CDN for uploaded files; multiplayer servers remain the developer's concern. [FAQ](https://docs.crazygames.com/faq/).

**itch.io is not interchangeable with a paid native storefront.** Embedded HTML5 projects currently accept donations; its documentation suggests a Downloadable project type to sell access. [HTML5 guide](https://itch.io/docs/creators/html5). The seller chooses itch.io's share, default 10%; payment-provider fees are additional. Direct payments make the seller merchant of record; collected payouts make itch.io merchant of record. Refunds, chargebacks, payout costs and tax identity can reduce what is paid. The payout route requires at least $5 available and a seven-day transaction waiting period. These are service facts, not tax advice for a particular business. [Payment guide](https://itch.io/docs/creators/payments).

**Small payments have large effective fees.** U.S. Stripe standard domestic-card pricing lists 2.9% + $0.30; international and currency-conversion charges can add more. Original processing/currency fees are not returned on refunds. At those sample rates, a $1 payment costs $0.329 (32.9%); $5 costs $0.445 (8.9%); $10 costs $0.59 (5.9%), before taxes, refunds, support or other services. Do not apply this U.S. example to every merchant country. Bundling value can reduce fee overhead, but do not obscure real prices with currency packs. [Stripe pricing](https://stripe.com/pricing?locale=en-US).

**Multiplayer pricing has several denominators.** Photon Realtime currently lists 20 CCU free for development; its 100-CCU launch package costs $95 once for twelve months with 0.3TB monthly traffic, and 500 CCU costs $95/month with 1.5TB. Regional peaks are summed; traffic above allowance is separately charged. These are Realtime prices, not Fusion/Quantum's free-100-CCU offer. Its MAU equivalents are vendor rules of thumb, not capacity guarantees. [Realtime pricing](https://www.photonengine.com/realtime/pricing). Colyseus lists self-hosted open source and managed cloud starting at $15/month, with no CCU/DAU/MAU billing limits. Lack of a per-user meter does not mean infinite machine capacity; load-test the actual simulation and region topology. [Colyseus pricing](https://colyseus.io/pricing/).

**Engine costs can scale with success.** Wonderland's published royalty is 10% of attributable revenue above $120,000/year across engine-based products, subject to enterprise-license alternatives; ads, sales, purchases and licensing proceeds count. Model this with portal compensation and actual EULA definitions before choosing it for a revenue-heavy product. Do not mistake “free to start” for an always-free engine. [Royalty terms](https://wonderlandengine.com/royalty/).

## Commercial evidence: purchases, trials and acquisition


**Poki monetization boundary.** Current requirements explicitly say in-app purchases are unavailable; Poki ads are the only monetization. Keep direct-site premium/subscription guidance separate. The same page says to remove outgoing links yet later permits external-link buttons through `PokiSDK.openExternalLink()`. Treat outbound promotion as restricted and subject to platform review; do not assume either unrestricted Steam funnels or an exceptionless ban. It also forbids gating core progress behind rewarded videos. [Requirements](https://developers.poki.com/guide/requirements-quality).

**Purchase recovery and refunds are separate responsibilities.** CrazyGames purchases are invite-only and require a signed-in player. Its docs require order recovery through webhooks/inventory rather than trusting client completion, and require external payment flows disabled in the CrazyGames native app. A browser build working on mobile does not authorize that app's purchase path. [IAP integration](https://docs.crazygames.com/sdk/in-game-purchases/). Its April 2026 consumer terms direct refunds to Xsolla's policy. [Consumer terms](https://www.crazygames.com/terms-and-conditions). Xsolla offers Limited, Moderate and Flexible policies; the applicable one appears at checkout. Therefore there is no safe universal “web purchases are nonrefundable” or “all get fourteen days” rule. Show the actual policy, receipt and support route, and reconcile refunds with entitlements. [Refund policies](https://xsolla.com/refund-policy).

**Actual premium pricing example.** Slow Roads' official itch page lists the offline Web Edition at **US$3 or more**. It identifies this as a downloadable copy of the free web game, with higher-resolution assets but no extra features, and no touch support. Its Spring-2026 Steam-release expectation is stale: the actual Steam listing gives **2026-09-23** as release date and provides a demo. Thus do not use the itch page's launch prose to date today's Steam availability. The retrieved Steam page was priced in Brazilian reais; no U.S. price was verified. [Web Edition](https://topographinteractive.itch.io/slow-roads), [Steam](https://store.steampowered.com/app/3431300/Slow_Roads/). Price demonstrates an offered model, not unit sales or optimal willingness to pay.

**Trials have a real tradeoff.** In a pre-release Slow Roads discussion, one player objected that a distance-limited Steam demo interrupted a relaxed drive after roughly 10–15 minutes despite already restricting features. The developer explained testing an unlimited version, then 40km, then 25km; a remaining-distance label confused some testers about whether it was a timer/global allowance. He wanted a short compatibility/value sample while protecting the paid edition, with the unlimited browser version still available. This is a specific design disagreement, not an A/B conversion result. Derived guidance: disclose a demo's boundary before play, preserve configuration, offer immediate restart and explain the paid difference. For contemplative games, a surprise cutoff directly contradicts the experience being sold. [Player/developer discussion](https://www.reddit.com/r/slowroads/comments/1u20ggv/anyone_else_slightly_disappointed_in_steam_demo/).

**Discovery can lead to purchases, but the rate remains unknown.** Poki commissioned Atomik's May 11–19, 2026 survey of 2,000 weekly web players and 400 developers in the U.S./U.K. Among those players, 62% said they had downloaded or bought a game after discovering one on the web; 27% reported spending over $50/month across gaming. Neither measures conversion of a given browser demo to a paid copy, and “downloaded or bought” includes free downloads. It excludes infrequent/non-web players and other countries. Useful evidence for a discovery channel, not a revenue forecast. [Report and methodology](https://poki.com/blog/state-of-web-gaming-report-2026).

**An income survey exists, but cannot estimate commercial success odds.** Gamedev.js collected 620 opt-in responses in December 2024; 62.3% identified as hobbyists. Its income question reports 58.2% earning nothing from game development, 17.7% below $1,000/year and 2.8% above $100,000. This includes salary/client income, all game types and people without released products. It lacks a representative cohort of commercial 3D browser attempts, profit and longitudinal outcomes. Therefore no defensible success probability follows from it. Read these figures as community composition, not “75% of browser businesses fail.” [Survey](https://gamedevjs.com/survey/2024/).

**A low-earning portfolio counterexample.** DonislawDev's historical account reports 451,327 CrazyGames plays and €556.92 across eight web versions, plus 104,444 Kongregate plays and $163.79. The developer says revenue accumulated over years and costs/taxes made the overall effort unprofitable. These were early games, many 2D, with varying effort and mobile versions; the page discusses 2018–2019 activity and is not a 2026 yield benchmark. It counters “hundreds of thousands of plays guarantee a living,” without estimating a typical game's earnings. The current page did not expose a reliable original publication date, so cite it as historical rather than invent one. [Developer portfolio account](https://donislawdev.com/earnings-and-statistics-from-my-8-games-android-ios-webgl/).

**Acquisition experiment to run.** Test the promise before scaling: a truthful, readable thumbnail; a matching first screen; instant room invites for social games; clearly distinct free/paid editions for own-site games. Poki's thumbnail guidance separates CTR from conversion to first play and says its own tests favor text-free thumbnails, but supplies no uplift or sample. Do not turn that into a quantified universal rule. It also requires review for post-test thumbnail changes, so external A/B tooling cannot be assumed. [Thumbnail guidance](https://developers.poki.com/guide/game-thumbnail). Measure incremental starts and retained players by placement; do not celebrate clicks attracted by misleading art.

## Full cost model — derived, not a market forecast

Start with collected revenue, then subtract distribution share, payment/ad-service fees, refunds/chargebacks, taxes borne by the business, CDN/storage/egress, multiplayer compute/relay/voice, moderation, support, content production, tooling/licenses, monitoring, acquisition, contractors and owner compensation. Keep VAT collected for remittance separate from economic revenue; avoid double-subtracting fees when a portal already reports a net developer payout.

For ads, use **eligible ad requests × fill rate × net realized revenue per thousand / 1,000**, or reconcile directly from actual paid impressions and actual payout. Do not use all gameplays as ad impressions. Consent refusal, ad blocking, no-fill, country, format, season, session length and vendor deductions change yield. There is no justified universal browser-game CPM in the sources reviewed.

For multiplayer, **average concurrent players ≈ player-minutes per day / 1,440**. Peak concurrency and region/mode fragmentation determine provisioned capacity and matchmaking health. One million sessions averaging ten minutes each month imply about 231 average CCU over a 30-day month; peak capacity can be much larger. A game that adds ten modes without growing its audience can make every queue worse. Traffic follows payload size × recipients × update frequency, not just CCU. Include backups, rollback, DDoS response and idle off-peak capacity.

For paid acquisition, compare incremental net lifetime contribution per acquired player with cost per acquired player using the same horizon/cohort. Portal discovery has an economic price through revenue share/exclusivity even when the developer buys no ads. Distinguish owner cash surplus from profit after a fair wage; a volunteer project can be healthy by its own goals without funding a studio.

Maintain cash for payment delays, a bad ad quarter and emergency repair. A static single-player game can stay online cheaply after development slows; a competitive multiplayer game cannot promise continuity with an unpaid server invoice and no operator. Define a wind-down path: notice, purchase handling, export where useful, and a standalone/private-server option only if rights, architecture and safety permit it.

## Stack choices

**Web-first, authored game:** PlayCanvas supplies an entity/component engine, editor workflow, animation, UI, physics integration and browser deployment. Engine source is open; hosted editor/account terms are separate. Its current engine targets WebGL2 and WebGPU. Good when artists need a scene editor and immediate URL review. Export and self-host a representative project before committing to its workflow. [Engine](https://github.com/playcanvas/engine), [optimization](https://developer.playcanvas.com/user-manual/optimization/).

**Code-first game:** Babylon.js bundles more engine services than a renderer alone; its npm modules support tree shaking. Three.js fits a custom renderer/game architecture or unusual interaction. Neither selects your authoritative simulation, save format or moderation. Babylon's own README warns against production use of its public learning CDN: bundle/pin and serve packages yourself. [Babylon.js](https://github.com/BabylonJS/Babylon.js), [Three renderer](https://threejs.org/docs/pages/WebGPURenderer.html).

**Existing Unity game:** Reuse Unity expertise and content, but budget for download/decompression/Wasm initialization, web restrictions and browser-specific QA. Unity 6.0 docs now explicitly list mobile Safari 15+ and Android Chrome support; the old blanket “Unity web cannot run on mobile” is stale. Runtime capability is not a promise of playable performance. Unity's documented minimum Android Chrome version is not a sensible security/support target for a new product. [Unity 6 browser compatibility](https://docs.unity3d.com/6000.0/Documentation/Manual/webgl-browsercompatibility.html).

**Owned open-source editor workflow:** Godot 4 web uses Wasm/WebGL2 Compatibility rendering; C# export is unavailable. Single-threaded export, available since 4.3, is now preferred/default. Test web from the first scene. [Godot web export](https://docs.godotengine.org/en/stable/tutorials/export/exporting_for_web.html).

**React team or rich DOM shell:** React Three Fiber expresses Three scenes through React; pair versions: Fiber 8/React 18, Fiber 9/React 19. It does not make React state updates suitable for every animation tick. Keep frame simulation outside UI reconciliation; use components for composition. Author claims of no overhead are not independent benchmark evidence. [Fiber](https://github.com/pmndrs/react-three-fiber).

**C++/Rust simulation:** Emscripten or wasm-bindgen can reuse mature simulation and asset code. They add toolchain, asynchronous loading, JS/Wasm boundary and memory debugging work. A language port does not restore native sockets, filesystem semantics or unrestricted threads. [Emscripten](https://github.com/emscripten-core/emscripten), [wasm-bindgen](https://github.com/wasm-bindgen/wasm-bindgen).

## Compatibility: four separate promises

A game can load, expose its features, adapt its controls, and survive long sessions; these are four separate acceptance tests. Browser games have no Android-style target-SDK declaration that proves support. Define browser/OS floor, required graphics features, memory/performance tier, tested inputs and distribution host. Test the production embed and headers, not only localhost.

| Axis | User difference, work, fallback and support cost |
|---|---|
| WebGL2 vs WebGPU | WebGPU is available in major browser families, but OS/GPU/driver combinations still matter. Request an adapter/device; handle failure. Three's WebGPURenderer falls back to WebGL2; that does not make WebGPU-only compute algorithms portable. Maintain a WebGL2-compatible design or explicitly exclude unsupported hardware. [Chrome overview](https://developer.chrome.com/docs/web-platform/webgpu/overview), [Three](https://threejs.org/docs/pages/WebGPURenderer.html). |
| Old browser floors | Current Three WebGLRenderer removed WebGL1 at r163. Godot4 also requires WebGL2. Supporting old WebGL1 hardware means another renderer/engine branch, asset constraints and QA, not a checkbox. [Three migration](https://github.com/mrdoob/three.js/wiki/Migration-Guide). |
| Mobile browser vs desktop | Touch layout, orientation changes, keyboard obstruction, thermal load and memory must be designed separately. Unity's mobile support does not validate a desktop scene's cost. Test an actual iPhone/iPad and modest Android phone, not just desktop emulation. [Unity](https://docs.unity3d.com/6000.0/Documentation/Manual/webgl-browsercompatibility.html). |
| GPU memory | No portable WebGL API reports a safe VRAM budget. Account for decoded textures, render targets and retained CPU copies; reduce resolution/textures and handle context loss. A small compressed download can become a large resident scene. [MDN practices](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API/WebGL_best_practices). |
| High-DPI/large displays | Pixel cost grows with canvas area and pixel ratio. Cap internal resolution independently from CSS size; preserve sharp DOM text. Test browser zoom, Retina, external displays and resizing during play. [PlayCanvas pixel ratio](https://developer.playcanvas.com/user-manual/optimization/device-pixel-ratio/). |
| Texture formats | Use portable KTX2/Basis transcoding or verified per-device variants; retain a supported fallback. Check artifacts in normal maps and UI separately. File compression and GPU compression solve different problems. [Basis Universal](https://github.com/BinomialLLC/basis_universal), [KTX](https://github.com/KhronosGroup/KTX-Software). |
| Threads/isolation | Wasm threads require SharedArrayBuffer and cross-origin isolation. Headers affect embedded assets, ads and integrations. Emscripten needs separate threaded/non-threaded binaries if you want both; one binary cannot dynamically become non-threaded. [Emscripten pthreads](https://emscripten.org/docs/porting/pthreads.html), [isolation](https://web.dev/articles/cross-origin-isolation-guide). |
| Embedded portals | Sandbox flags can block pointer lock; Permissions Policy can block fullscreen; storage may be partitioned. Verify actual publisher integration. Do not assume opening the same game at its own URL shares embedded saves. [Pointer Lock](https://developer.mozilla.org/en-US/docs/Web/API/Pointer_Lock_API), [storage](https://developer.mozilla.org/en-US/docs/Web/API/Storage_API/Storage_quotas_and_eviction_criteria). |
| Pointer lock | Essential for many FPS controls; requires deliberate engagement and has failure/escape states. Handle both API styles and raw-motion rejection. Give a playable alternative only if it actually fits the genre. [MDN](https://developer.mozilla.org/en-US/docs/Web/API/Pointer_Lock_API). |
| Keyboard layouts | Physical movement keys and displayed characters differ. Allow remapping; use physical codes for position-based defaults and appropriate labels/text handling. Test AZERTY, IME chat and browser shortcuts. [KeyboardEvent.code](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/code). |
| Controller | Connection, mapping, dead zones and disconnect behavior need tests with real controllers. “Gamepad API present” does not prove all devices map identically. Keep menus usable when a controller disappears. [Gamepad guide](https://developer.mozilla.org/en-US/docs/Web/API/Gamepad_API/Using_the_Gamepad_API). |
| Touch/pen/hybrid | Pointer events unify input; capture and cancellation need explicit state cleanup. Limit gesture suppression to the play surface. A touchscreen laptop can change input mode mid-session. [Pointer events](https://developer.mozilla.org/en-US/docs/Web/API/Pointer_events). |
| Audio | Start/resume audio after user activation, handle blocked playback and preserve mute. Spatial sound needs a non-audio equivalent for essential cues. Do not make sound success a prerequisite for entering the game. [Autoplay](https://developer.mozilla.org/en-US/docs/Web/Media/Guides/Autoplay). |
| Background/frozen/discarded | Hidden pages may stop animation callbacks and timers; discarded pages reload. Save durable progress throughout play; restore state on return. Multiplayer must reconcile against server time/state. [Visibility](https://developer.mozilla.org/en-US/docs/Web/API/Page_Visibility_API), [lifecycle](https://developer.chrome.com/docs/web-platform/page-lifecycle-api). |
| Local persistence | IndexedDB is useful, not an unconditional permanent save. Quotas, eviction, private mode and clearing site data differ. Show local/cloud status and support export/account recovery where progress matters. [Storage](https://developer.mozilla.org/en-US/docs/Web/API/Storage_API/Storage_quotas_and_eviction_criteria). |
| Offline/PWA | A cached shell does not prove levels/audio are cached. Version manifests/saves; show available content. Installation does not prevent eviction. [Godot PWA export](https://docs.godotengine.org/en/stable/tutorials/export/exporting_for_web.html). |
| Transport/networks | WebSocket is widely available, but has no built-in backpressure. Bound queues and detect stalls. WebTransport now has MDN Baseline 2026 status, but old devices and HTTP/3-blocking networks still require a policy. [WebSocket](https://developer.mozilla.org/en-US/docs/Web/API/WebSocket), [WebTransport](https://developer.mozilla.org/en-US/docs/Web/API/WebTransport). |
| WebXR | Headset tracking, controllers, permissions, comfort and frame timing are a separate supported product. A-Frame supplies browser XR scaffolding, not cross-headset validation. Keep flat-screen entry when the game supports it. [A-Frame](https://github.com/aframevr/aframe). |


### Dated WebGPU support is narrower than browser branding

GPUWeb’s implementation matrix, updated 2026-10-02, lists Chromium 113 on Mac/Windows x86–64/ChromeOS; Android 121 for ARM/Qualcomm/Intel on Android 12+, and 139 for Imagination on Android 16+. Samsung Xclipse remains pending. Linux support includes Chromium 144 on Intel Gen12+ and 147 on NVIDIA with driver 535.183.01+ under Wayland; other combinations and Windows ARM64 remain behind flags. Firefox lists Windows 141 and Apple Silicon 145 on macOS 26+, expanded in 147; Intel Mac/Linux are Nightly-only and Android is flag-only. Safari requires the version-26 OS family. These are documented capability boundaries, not recommended security floors or tested game performance. Detect actual adapter/device creation and do not ask ordinary players to weaken browser settings. [GPUWeb status](https://github.com/gpuweb/gpuweb/wiki/Implementation-Status).

### Practical target strategies

**Desktop competitive game:** current Chrome/Edge/Firefox/Safari on explicitly tested OS/hardware; WebGL2 baseline; pointer lock and keyboard/mouse required; measured integrated-GPU tier. Offer a clear mobile landing page instead of unusable touch gameplay. Validate latency and reconnect before graphics tiers.

**Broad portal arcade game:** WebGL2, single-thread where practical, portrait/landscape and touch designed from day one, low-res graphics tier, tiny first playable scene, portal SDK/header/storage tests. This buys reach with art and simulation limits.

**Premium browser demo of a native game:** select a short scene, compressed assets, clear system requirements and save handoff only if implemented. Existing Unity/Godot production knowledge may outweigh engine-download cost. Test web early; do not promise that the entire native game can ship unchanged.

**WebGPU-focused niche:** explicit recent devices, advanced compute or renderer benefit, adapter checks and honest unsupported screen. Suitable for a technical audience or controlled deployment. Benchmark the actual scene; API novelty is not a user benefit.

These are derived strategies, not claims that most studios choose them.

## Architecture lessons from a book and developer interview

Robert Nystrom’s *Game Programming Patterns*, “Game Loop,” separates simulation time from input and machine speed. In a browser, return control to the host and schedule frames; do not transplant a blocking native loop. Fixed simulation steps plus bounded catch-up avoid making physics depend on display refresh. Interpolate rendered states when useful. A sleeping tab must not trigger an unlimited backlog of simulation work. These are architecture lessons, not a prescription to replace an engine’s scheduler. The chapter is freely readable; direct HTML retrieval succeeded after the web reader failed. [Book chapter](https://gameprogrammingpatterns.com/game-loop.html).

In Mux’s February 2024 interview transcript, Bruno Simon emphasizes the tension between a link anyone expects to open and widely varying hardware/bandwidth. He also criticizes the learning cost of overcomplicated web stacks. Use this as practitioner judgment: budget the first playable experience and adopt dependencies for concrete work saved. His informal native-versus-web performance ratio is not a benchmark, and his then-current WebGPU availability comments must not describe 2026. [Interview transcript](https://www.mux.com/blog/3d-web-development-and-beyond-a-chat-with-bruno-simon).

## A measured historical performance case

Anslo’s 2023 Slow Roads case study reports average initial environment generation of 3.2 seconds, over 97% below ten seconds, but only 52% of players above 55 FPS. Those are developer observations from that build, not a current browser benchmark or conversion experiment. The useful design decision was a single road corridor: generate nearby detail ahead, simplify distant terrain and omit unnecessary dynamic collisions. Recycle transient allocations to reduce collection spikes. WebP conversion reportedly halved the download bundle. Procedural assets trade network transfer for client computation; they do not eliminate startup work. Current 2.4.2 differs substantially. [Developer case study](https://web.dev/case-studies/slow-roads).

## Multiplayer security and continuity

A connected browser is an untrusted client. Use secure transport, validate allowed origins, authenticate sessions, authorize actions individually and bound message sizes/rates. Logout and expiry must affect existing connections. Do not mistake a successful WebSocket handshake for authorization to award currency or access another room. Log connection and action failures without credentials or private chat bodies. OWASP’s examples cover web services generally; the game-specific implication is server-owned competitive outcomes and entitlements. [WebSocket security](https://cheatsheetseries.owasp.org/cheatsheets/WebSocket_Security_Cheat_Sheet.html).

Portal bridges need exact origin/source checks and validated message shapes. Treat imported maps, chat names and save files as data; never execute them or interpolate them into HTML. Browser storage is not a safe place for secrets. Asset and multiplayer endpoints still need normal web security even when the visible UI is a canvas. [HTML5 security](https://cheatsheetseries.owasp.org/cheatsheets/HTML5_Security_Cheat_Sheet.html).

## Named ecosystem: 70 useful choices

This is a selection map, not an install list or popularity ranking. Alternatives appear beside each choice. Official engine integrations and examples show practical use; none prove comparative market share. Libraries with a browser runtime still need bundle-size, license and version checks in the selected build. Pin release versions and retain notices; model/font/audio licenses are independent from code licenses.

### Engines and rendering

| # | Choice | Purpose, fit, alternatives and constraints |
|---|---|---|
| 1 | [Three.js](https://threejs.org/docs/pages/WebGPURenderer.html) | Renderer/scene graph for custom games. Less prescribed game architecture than Babylon/PlayCanvas; separate physics and game systems. WebGPU renderer includes WebGL2 fallback. |
| 2 | [Babylon.js](https://github.com/BabylonJS/Babylon.js) | Integrated browser engine, typed npm modules and broad tooling. Alternative to assembling Three add-ons; tree-shake and self-host production dependencies. |
| 3 | [PlayCanvas Engine](https://github.com/playcanvas/engine) | Browser-first entity/component runtime; source independent from hosted editor. Good editor/art collaboration route; compare code-only Babylon/Three. |
| 4 | [Godot](https://docs.godotengine.org/en/stable/tutorials/export/exporting_for_web.html) | Open engine/editor; attractive existing GDScript workflow. Web feature limitations in stack section; evaluate web export before content production. |
| 5 | [Unity](https://docs.unity3d.com/6000.0/Documentation/Manual/webgl-technical-overview.html) | Reuse C# gameplay/editor assets. Proprietary editor terms and native/web differences; strongest when reuse justifies runtime and build complexity. |
| 6 | [A-Frame](https://github.com/aframevr/aframe) | HTML/entity-component layer over Three for WebXR scenes. Good approachable XR experiments; not a substitute for game-specific simulation or headset QA. |
| 7 | [React Three Fiber](https://github.com/pmndrs/react-three-fiber) | React renderer for Three, useful for declarative composition. Version coupling to React; plain Three avoids that dependency when DOM/React integration adds little. |
| 8 | [Drei](https://github.com/pmndrs/drei) | Fiber helpers for controls, loaders and scene pieces. Public integration evidence: built for Fiber and uses three-stdlib. Inspect individual helper cost instead of importing convenience blindly. |
| 9 | [postprocessing](https://github.com/pmndrs/postprocessing) | Three WebGL effects/composer. Alternative to engine effects; peer-version and backend compatibility matter. Effects add full-screen bandwidth cost. |
| 10 | [PixiJS](https://github.com/pixijs/pixijs) | 2D renderer for elaborate overlays or hybrid games. Its WebGPU support does not make it a full 3D game engine; DOM is often enough for menus. |

### Simulation, physics and spatial tools

| # | Choice | Purpose, fit, alternatives and constraints |
|---|---|---|
| 11 | [Rapier](https://github.com/dimforge/rapier) | Rust/Wasm 2D/3D rigid-body engine with JS bindings. Compare Jolt/Ammo against actual collision workload; initialization and Wasm delivery are integration costs. |
| 12 | [cannon-es](https://github.com/pmndrs/cannon-es) | JavaScript/TypeScript physics; README identifies a maintained cannon.js fork. Useful for simpler worlds and JS debugging; compare Rapier for demanding simulation. |
| 13 | [Ammo.js](https://github.com/kripken/ammo.js) | Emscripten Bullet port with vehicle/soft-body examples. Useful existing engine integration; native-style object ownership and payload need care. |
| 14 | [JoltPhysics.js](https://github.com/jrouwe/JoltPhysics.js) | Jolt browser bindings with separate Wasm, embedded-Wasm and threaded variants. Select build deliberately; threaded variant adds isolation requirements. |
| 15 | [react-three-rapier](https://github.com/pmndrs/react-three-rapier) | Fiber integration around Rapier. Saves scene/body binding work in React; does not remove simulation authority or timestep decisions. |
| 16 | [recast-navigation-js](https://github.com/isaac-mason/recast-navigation-js) | Wasm Recast/Detour navmesh tools, with Three/PlayCanvas integrations. Author says maintained alongside newer navcat; do not mislabel it abandoned. |
| 17 | [Yuka](https://github.com/Mugen87/yuka) | Steering, navigation, perception, state/goal-based game AI. Renderer-independent; useful beyond hand-coded finite states when behavior complexity warrants it. |
| 18 | [bitECS](https://github.com/NateTheGreatt/bitECS) | Minimal data-oriented entity/component tools. Useful many-entity systems; not required for a small game and not a renderer/editor. |
| 19 | [three-mesh-bvh](https://github.com/gkjohnson/three-mesh-bvh) | Accelerated Three mesh raycasts/spatial queries. Useful picking/collision queries; build/update cost and deforming geometry require care. |
| 20 | [gl-matrix](https://github.com/toji/gl-matrix) | Standalone vector/matrix math. Useful custom simulation/renderer; avoid duplicating an engine math library without a measured reason. |

### Asset pipeline and animation

| # | Choice | Purpose, fit, alternatives and constraints |
|---|---|---|
| 21 | [glTF Transform](https://github.com/donmccurdy/glTF-Transform) | Repeatable glTF editing/optimization in Node/browser. Good build pipeline; artistic edits still belong in DCC tools. |
| 22 | [meshoptimizer](https://github.com/zeux/meshoptimizer) | Mesh simplification, locality and compression. MIT source; compare Draco using total download plus decode time, not only bytes. |
| 23 | [Draco](https://github.com/google/draco) | Mesh/point-cloud compression. Version decoder URLs; compressed geometry needs client decoding. Does not compress an entire game or all textures. |
| 24 | [Basis Universal](https://github.com/BinomialLLC/basis_universal) | Portable GPU texture intermediates/transcoding. Texture quality/time choices depend on content and device; compare appropriate uncompressed small textures. |
| 25 | [KTX-Software](https://github.com/KhronosGroup/KTX-Software) | Khronos container tooling and texture conversion. Useful offline build step; the container alone does not ensure every runtime decodes every format. |
| 26 | [glTF Validator](https://github.com/KhronosGroup/glTF-Validator) | JSON/binary/extension correctness and asset statistics. Add to asset CI; valid assets can still be slow or ugly. |
| 27 | [glTF Sample Viewer](https://github.com/KhronosGroup/glTF-Sample-Viewer) | Khronos reference viewing for material/asset comparison. Helps isolate exporter vs engine problems; not a game runtime benchmark. |
| 28 | [GLTFLoader](https://threejs.org/docs/pages/GLTFLoader.html) | Three glTF import and extension integration. Track supported extensions; image-bitmap disposal requires care. |
| 29 | [KTX2Loader](https://threejs.org/docs/pages/KTX2Loader.html) | Three Basis/KTX2 transcoding into supported GPU formats. Configure decoder path/support; not every KTX2 payload is supported. |
| 30 | [DRACOLoader](https://threejs.org/docs/pages/DRACOLoader.html) | Three Draco decode, reused across models. Extra decoder startup/time; use only when geometry savings justify it. |
| 31 | [gltfjsx](https://github.com/pmndrs/gltfjsx) | Generates reusable Fiber components from glTF. Good React asset workflow; generated source must follow asset regeneration policy. |
| 32 | [AnimationMixer](https://threejs.org/docs/pages/AnimationMixer.html) | Three animation playback/blending. Usually sufficient before adding another timeline library; gameplay state and animation state still need coordination. |

### UI, camera, audio and local state

| # | Choice | Purpose, fit, alternatives and constraints |
|---|---|---|
| 33 | [OrbitControls](https://threejs.org/docs/pages/OrbitControls.html) | Object inspection/orbit camera. Good turntable/build views; wrong default for first-person aiming. |
| 34 | [PointerLockControls](https://threejs.org/docs/pages/PointerLockControls.html) | Three FPS camera capture and lock events. Movement/collision and permission UI remain app work. |
| 35 | [Troika](https://github.com/protectwise/troika) | Three tools including text; usable independently of the full framework. Useful in-world text; DOM remains better for many accessible forms. |
| 36 | [PCUI](https://developer.playcanvas.com/user-manual/pcui/) | Editor-style DOM controls; used by PlayCanvas Editor, SuperSplat and Model Viewer. Good creation/debug tooling, not automatically a polished game HUD. |
| 37 | [lil-gui](https://lil-gui.georgealways.com/) | Small tuning panels, presets and value controls. Documented dat.GUI migration route; use in dev or deliberate creator UI. |
| 38 | [Howler.js](https://github.com/goldfire/howler.js) | Audio sprites, groups and spatial sound with Web Audio/HTML audio fallback. Useful cross-browser abstraction; still handle user activation. |
| 39 | [Tone.js](https://tonejs.github.io/) | Musical transport, synths/effects and scheduling. Good adaptive/rhythm music; excessive for a few prerecorded sound effects. |
| 40 | [Zustand](https://github.com/pmndrs/zustand) | Shared UI/application state, especially React ecosystem. Keep high-frequency simulation out of broad reactive subscriptions. |
| 41 | [idb](https://github.com/jakearchibald/idb) | Small promise-oriented IndexedDB wrapper. Good simple saves/migrations; native API is enough for a tiny controlled store. |
| 42 | [Dexie](https://github.com/dexie/Dexie.js) | Richer IndexedDB queries and schema handling. Useful local inventories/world data; optional Dexie Cloud is a separate service choice. |
| 43 | [Workbox](https://github.com/GoogleChrome/workbox) | Service-worker caching/build helpers. Useful deliberate offline/update policy; adds cache invalidation/release QA. |
| 44 | [Comlink](https://github.com/GoogleChromeLabs/comlink) | Worker RPC over postMessage. Simplifies boundaries; transfer ownership and call granularity still matter. |

### Multiplayer and serialization

| # | Choice | Purpose, fit, alternatives and constraints |
|---|---|---|
| 45 | [Colyseus](https://github.com/colyseus/colyseus) | Authoritative rooms, matchmaking and synchronized state in Node/TS. Good small-team game-server framework; advertised scaling/cheat resistance needs application validation. |
| 46 | [Nakama](https://github.com/heroiclabs/nakama) | Users, storage, social, multiplayer, leaderboards and server runtime extensions. Good integrated backend; self-hosting/managed support is a separate operations choice. |
| 47 | [Socket.IO](https://github.com/socketio/socket.io) | Event transport ecosystem; useful lobby/casual multiplayer. Not raw-WebSocket protocol compatible; not a complete authoritative game server. |
| 48 | [Geckos.io](https://github.com/geckosio/geckos.io) | Client/server WebRTC data channels with Node. Suits real-time datagrams; native server dependency and network negotiation add work. |
| 49 | [PeerJS](https://github.com/peers/peerjs) | WebRTC peers/media/data abstraction. Useful co-op or voice experiments; signaling/relay cost and hostile peers remain design concerns. |
| 50 | [@msgpack/msgpack](https://github.com/msgpack/msgpack-javascript) | Binary serialization across browser/server. Compare against JSON for actual packet sizes; binary does not validate schemas or authorize actions. |

### Build, diagnostics and tests

| # | Choice | Purpose, fit, alternatives and constraints |
|---|---|---|
| 51 | [TypeScript](https://github.com/microsoft/TypeScript) | Static types/tooling for JS. Useful larger game systems; emitted JS target and library API support are separate. Not required by browser APIs. |
| 52 | [Vite](https://github.com/vitejs/vite) | Dev server/build pipeline for ES-module games. Current main docs describe Rolldown; avoid stale claims that every Vite release uses the same bundler. Pin toolchain. |
| 53 | [esbuild](https://github.com/evanw/esbuild) | Direct bundling/minification for small controlled builds. Supports TS syntax but does not replace type checking. Compare Vite for fuller dev workflow. |
| 54 | [Emscripten](https://github.com/emscripten-core/emscripten) | C/C++→Wasm toolchain with native API portability layers; Unity is a documented example. Build/debug burden justified by reusable native code. |
| 55 | [wasm-bindgen](https://github.com/wasm-bindgen/wasm-bindgen) | Rust/JS bindings. Canonical project moved from rustwasm organization; no reason to call it abandoned from the old URL. |
| 56 | [Spector.js](https://github.com/BabylonJS/Spector.js) | WebGL frame captures across engines. Useful draw/state diagnosis; not a WebGPU capture tool or player analytics SDK. |
| 57 | [stats.js](https://github.com/mrdoob/stats.js) | Lightweight frame-time/FPS display. Useful quick feedback; averages and restricted memory counters are not complete profiling. |
| 58 | [PlayCanvas MiniStats](https://developer.playcanvas.com/user-manual/optimization/mini-stats/) | Engine CPU/GPU/frame/resource overlays. Useful engine-aware runtime baseline; compare browser traces for main-thread stalls. |
| 59 | [Playwright](https://github.com/microsoft/playwright) | Chromium/Firefox/WebKit browser automation. Good boot, menus, saves, errors and reconnect checks; WebKit automation is not an actual iPhone GPU test. |
| 60 | [Vitest](https://github.com/vitest-dev/vitest) | Unit/integration testing beside Vite. Good deterministic game rules and codecs; DOM emulation cannot validate a 3D GPU pipeline. |

### Built-in platform components: do not add libraries without a need

| # | Choice | Purpose, fit, alternatives and constraints |
|---|---|---|
| 61 | [Web Audio](https://developer.mozilla.org/en-US/docs/Web/Media/Guides/Autoplay) | Native audio graph; enough for simple sound. Howler/Tone add convenience, not permission exemptions. |
| 62 | [WebSocket](https://developer.mozilla.org/en-US/docs/Web/API/WebSocket) | Broad reliable ordered server transport. Bound backlog; unsuitable to treat old queued movement as current state. |
| 63 | [WebTransport](https://developer.mozilla.org/en-US/docs/Web/API/WebTransport) | HTTP/3 streams/datagrams; recent baseline, older targets need strategy. Browser availability alone does not ensure network reachability. |
| 64 | [OffscreenCanvas](https://developer.mozilla.org/en-US/docs/Web/API/OffscreenCanvas) | Transfer rendering off main thread where engine/support permits. Input/DOM coordination and backend-specific support add complexity. |
| 65 | [ResizeObserver](https://developer.mozilla.org/en-US/docs/Web/API/ResizeObserver) | Canvas-container size changes, including embedded layouts. Prefer to guessing from window dimensions alone. |
| 66 | [Pointer events](https://developer.mozilla.org/en-US/docs/Web/API/Pointer_events) | Mouse/touch/pen event family; capture and cancellation. Native enough before an input library if needs are small. |
| 67 | [Gamepad API](https://developer.mozilla.org/en-US/docs/Web/API/Gamepad_API/Using_the_Gamepad_API) | Controller polling and connection integration. Map/dead-zone UX and hardware tests remain app responsibilities. |
| 68 | [Page Visibility](https://developer.mozilla.org/en-US/docs/Web/API/Page_Visibility_API) | Hidden/visible state for pause/resource policy. Not a guaranteed final persistence callback. |
| 69 | [Fullscreen API](https://developer.mozilla.org/en-US/docs/Web/API/Fullscreen_API) | Optional immersive surface; permissions/user activation and embedded policies apply. |
| 70 | [Storage API](https://developer.mozilla.org/en-US/docs/Web/API/Storage_API/Storage_quotas_and_eviction_criteria) | Quota estimates/persistence requests around browser storage. A granted request still cannot prevent user deletion; cloud/export can be separate recovery channels. |

## Named avoid/migrate guidance

Checked 2026-11-08. Distinguish incompatibility, migration work and abandonment.

| Choice | Exact problem; replacement; legitimate exception |
|---|---|
| Adobe Flash Player for new browser delivery | Support ended 2020-12-31; Adobe blocked Flash content from 2021-01-12. Use a maintained HTML5/WebGL/Wasm runtime for new work. Historical preservation is a separate project, not a reason to require an obsolete plugin from players. [Adobe EOL](https://www.adobe.com/products/flashplayer/end-of-life.html). |
| Three.js WebGL1 assumptions | Removed from WebGLRenderer in r163. Upgrade content/support floor to WebGL2; a deliberately frozen legacy app may retain an old branch with its own maintenance. [Migration guide](https://github.com/mrdoob/three.js/wiki/Migration-Guide). |
| Legacy Three global builds | `build/three.js` and `three.min.js` removed in r161. Use ES modules; old tutorials need translation, not a second mismatched renderer copy. [Migration guide](https://github.com/mrdoob/three.js/wiki/Migration-Guide). |
| Godot4 C# for mandatory web | No current export support. Use GDScript or another engine; native C# remains viable. [Export docs](https://docs.godotengine.org/en/stable/tutorials/export/exporting_for_web.html). |
| Godot Forward+/Mobile for mandatory web | Web uses Compatibility; native branches can retain richer effects. Same source as above. |
| Threaded Wasm as unconditional portal baseline | Needs isolation and compatible embedding/assets. Maintain separate non-threaded build or choose a compatible host; controlled high-performance deployments can justify it. [Emscripten](https://emscripten.org/docs/porting/pthreads.html). |
| Unreal HTML5 as turnkey new-project assumption | HTML5 support is a community extension with old-engine build instructions, not evidence of an ordinary current Unreal export. Use a web-first engine or budget custom fork maintenance; native Unreal and separately priced streaming are different products. [Community documentation](https://github.com/UnrealEngineHTML5/Documentation). |
| Babylon public CDN in production | Owner explicitly says it serves learning/experiments, not production. Bundle/pin/self-host; CDN playground examples remain useful. [README](https://github.com/BabylonJS/Babylon.js). |
| Unversioned Draco decoders | Owner warns propagation/cache delays can cause transient errors at release. Pin versioned decoders and deploy matching assets. Draco itself remains viable. [README](https://github.com/google/draco). |
| Old `rapier.js` repository as maintenance signal | Repository explicitly migrated to main Rapier `typescript` tree. Follow canonical source, not a stale repository's activity graph. Existing imports depend on package compatibility, not repository name. [Migration notice](https://github.com/dimforge/rapier.js). |
| Original cannon.js for new modern JS work | cannon-es documents maintained fork and merged fixes/ESM packaging. Prefer that fork or Rapier after testing; do not demand migration of a stable shipped game without benefit. [cannon-es](https://github.com/pmndrs/cannon-es). |
| dat.GUI as default new tuning panel | lil-gui provides a documented migration guide and modern alternative; dat.GUI has an explicit CSP inline-style caveat. This is a fit/migration recommendation, not a verified abandonment claim. [lil-gui](https://lil-gui.georgealways.com/), [dat.GUI](https://github.com/dataarts/dat.gui). |
| PixiJS/Phaser as full 3D engine | These are primarily 2D tools; WebGL/WebGPU backend support does not supply a full 3D pipeline. Good for 2D overlays/hybrid work; Three/Babylon/PlayCanvas provide direct 3D tooling. [PixiJS](https://github.com/pixijs/pixijs), [Phaser](https://github.com/phaserjs/phaser). |
| `unload`-only saving | Chrome docs updated Oct 16, 2026 say deprecation rollout complete in Chrome 155; event does not fire by default. Save/checkpoint earlier and react to visibility/page lifecycle. Existing opt-out is temporary compatibility, not a durability strategy. [Chrome](https://developer.chrome.com/docs/web-platform/deprecating-unload). |
| Unlimited WebSocket queues | API has no backpressure. Bound/coalesce state updates and detect overload; use suitable transport/flow control when needed. WebSocket remains a sound broad-support choice. [MDN](https://developer.mozilla.org/en-US/docs/Web/API/WebSocket). |

## Release tests worth funding

Measure first interaction, cold/warm load, percentile frame times, peak memory, context-loss recovery, first shader use, reconnect and save recovery on the selected real-device tiers. Exercise resize/zoom, mixed inputs, tab hiding/discard, private storage, denied permissions, low disk, slow/lost network and SDK failure. Test a signed-off production-host build with actual compression MIME types, Wasm paths, cache headers, CSP and iframe permissions. Automated smoke tests complement real GPUs; neither a high-end desktop demo nor an engine marketing support list proves reliability.

### License and service boundaries checked

PlayCanvas Engine carries the MIT permission text; its hosted editor is a separate product. Godot is MIT and requires its notice on redistribution. Babylon.js and Nakama use Apache-2.0; Colyseus uses MIT. These permissive code licenses do not buy hosting, support, game assets, fonts or permission to reuse an example game's branding. Preserve the actual license/notice files for the pinned dependency graph. [PlayCanvas license](https://github.com/playcanvas/engine/blob/main/LICENSE), [Godot](https://godotengine.org/license/), [Babylon](https://github.com/BabylonJS/Babylon.js/blob/master/license.md), [Nakama](https://github.com/heroiclabs/nakama/blob/master/LICENSE), [Colyseus](https://github.com/colyseus/colyseus/blob/master/LICENSE).

Socket.IO's current introduction confirms that plain WebSocket and Socket.IO peers cannot speak directly to each other; it adds its own packet metadata. Its reconnect buffering is useful for durable commands but needs care for obsolete movement input. Choose delivery semantics per message rather than treating every reconnect as replay-safe. [Socket.IO 4.x](https://socket.io/docs/v4/).

React Three Rapier v2 pairs with Fiber9/React19; React18 needs Rapier wrapper v1/Fiber8. Pin the family together; upgrading only one package can break integration. [Wrapper README](https://github.com/pmndrs/react-three-rapier/blob/main/packages/react-three-rapier/readme.md).

## Sources and reading guide

Citations sit beside claims. Read platform rules as dated channel requirements, vendor case studies as selected developer accounts, independent reviews as dated judgments and player threads as individual evidence. A changelog confirms a shipped intent/fix; it does not establish defect frequency or measured delight. Direct observations above describe the inspected desktop surfaces, not broad accessibility or performance certification.

- **Start with real product choices:** the Slow Roads, Narrow One, PolyTrack, Townscaper and The Open House profiles. Their different purposes prevent a single retention or visual recipe.
- **For first-play economics:** the Cannon Clash and Stickman Hook cases, then each portal’s own metric definitions. The rewrite comparison is observational; the 3D case reports an achieved result without a baseline.
- **For sustainable operation:** Shell Shockers, Tall Team, TANX, Krunker and the low-earning portfolio. Read revenue, total plays, studio support and owner labor separately.
- **For implementation:** owning engine/export documentation, GPUWeb’s dated platform matrix, MDN lifecycle/input/storage pages and the grouped ecosystem catalog. Moving documentation must be rechecked when pinning the production toolchain.
- **For visual work:** inspected game screens, Interface In Game interviews/catalog, the independently described Game UI Database and licensed asset/type resources. Screens teach appearance; source demos teach mechanisms; neither proves long-term usability.
- **For architecture:** the accessible *Game Programming Patterns* chapter and Mux interview transcript. Historical practitioner lessons remain useful; old availability or performance estimates are not current benchmarks.

No representative dataset links all commercial browser-3D attempts to audited profit, owner wages and acquisition costs. The surveys and disclosed cases here cannot determine a universal success rate, optimal price or best publisher. Current contract pages describe public offers; signed terms and a game's own cohorts remain necessary for those decisions. This limits generalization, not the concrete UX, compatibility and cost guidance above.
