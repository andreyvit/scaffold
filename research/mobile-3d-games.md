# Great cross-platform 3D mobile games for iOS and Android

Research checked 2026-11-08. Recommendations are research, not confirmed scaffold decisions.

## Scope

Indie and small-team games shipping on both iOS and Android: spatial puzzles, tactile objects, runners, exploration, action and simulation. Include 2.5D play rendered in 3D; distinguish it from free-camera 3D. Premium, free-to-play and subscription distribution have separate economics. Larger games supply bounded lessons, not indie production budgets. AR, VR, console-only games and full MMO operations are outside the core scope; discuss only where they expose a relevant tradeoff.

No genre, audience, region or monetization model was specified. Compare those branches instead of selecting one for every game.

Related guidance: [iOS app research](ios-apps.md), [Android app research](android-apps.md), [engineering values](../skills/scaffold/references/values.md), [iOS layering](../skills/scaffold/references/ios-layering.md), [testing](../skills/scaffold/references/testing.md), [analytics](../skills/scaffold/references/analytics.md), [optional offline sync](../skills/scaffold/references/offline-sync.md). Existing native app preferences do not answer which shared game engine to use. Web Stripe defaults do not decide mobile billing. Game progress, purchases and multiplayer state need their own conflict semantics; do not copy document timestamp merging into currency balances.

## How to use this report

Start with the [build priorities](#prioritized-build-guidance), then compare [game examples](#exemplary-games-strengths-and-weaknesses), [visual directions](#visual-design-directions-and-resources) and [business models](#model-fit-and-full-economics-derived-decision-guidance). Use the [100 practical details](#specific-screens-and-components-100-practical-details), [compatibility matrix](#compatibility-support-means-four-separate-promises) and [99-entry catalog](#named-ecosystem-catalog) for implementation planning.

Evidence types remain separate: official requirements; vendor recommendations; developer disclosures; independent reviews; individual player reports; direct static/recorded visual inspection; and derived design guidance. Historical reviews do not establish current defects. No game was installed or live-playtested, no engine benchmark was run, and no private financial accounts were audited. Public-access limits sit beside the affected claims.

## What “great” means here

A great mobile game makes its central action satisfying with fingers on a small, warm device. Its camera, levels, feedback and business model support that action. Fidelity is one possible tool. It cannot compensate for unreadable targets, unreliable saves or controls that require an absent gamepad.

Evaluate seven outcomes separately:

| Outcome | Evidence to seek | Misleading substitute |
|---|---|---|
| Emotional appeal | Players describe moments, return voluntarily, recommend it | Beautiful promotional renders |
| Player value | Enjoyment, mastery, relaxation, discovery or connection | More systems, currencies or playtime |
| Audience | Qualified installs, retained cohorts, referrals | Raw downloads from a giveaway |
| Cash | Net receipts by channel and cohort | Gross consumer spending |
| Viability | Receipts cover production, acquisition, updates and support | A successful launch week |
| Maintainability | Reproducible builds, inspectable state, safe migrations, manageable content tools | An engine or language reputation |
| Featuring | Distinctive work, platform fit, technical quality, editorial readiness | An assumed entitlement to promotion |

This is an evaluation framework, not a measured ranking. A finite premium puzzle can satisfy its audience without daily retention. A social game can retain users yet lose money. Treat repeated grinding, genuine pleasure and fear of missing rewards as different reasons to return.

## Platform behavior and accessibility

Apple recommends touch-native controls, playable onboarding, suitable defaults and readable layouts. Its game guidance allows branded in-game UI; copying a console controller onto a phone is not the intended endpoint. Google treats stability, loading, frame delivery and resource use as parts of quality that can affect discovery. Neither source proves that a specific design increases revenue. [Apple game design](https://developer.apple.com/design/human-interface-guidelines/designing-for-games), [Android technical quality](https://developer.android.com/quality/technical).

Accessibility guidance is broader than platform compliance. Microsoft’s XAG 107 includes mobile input and recommends substantially larger physical targets than Apple’s nominal point sizes. These are different recommendations, not interchangeable units or store mandates. Use them to test reach and accuracy with intended players. A fixed-camera puzzle can remove the need for camera steering; a free-camera action game must budget for controls, sensitivity and motion comfort. [XAG 107](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/107).

## Exemplary games: strengths and weaknesses

These are scoped references, not a universal ranking. Reviews describe their dated builds; current listings establish availability, not current defect rates.

- **Monument Valley — sculptural spatial puzzle; emotional appeal and editorial quality.** Harry Slater's 2014 review praises tactile manipulation, distinct visual affordances and compact, surprising levels. Its main drawback is brevity. Useful model: constrain the camera and available verbs to make impossible geometry readable on a phone. Do not infer that short playtime maximizes revenue or retention. [Review](https://www.pocketgamer.com/monument-valley/review/).
- **The Room: Old Sins — close-up mechanical puzzle; tactile pleasure.** Eli Hodapp's 2018 review values drag-operated mechanisms and the dollhouse's nested structure; he preferred the renewed object focus to The Room Three's broader environmental exploration. This is a critic's preference, not proof that every sequel should contract. The first Room's abrupt ending needed an epilogue: deliver a satisfying finish, not merely content volume. [Review](https://toucharcade.com/2018/01/24/the-room-old-sins-review/). Pocket Gamer's staff separately describe dials and simultaneous touches as pleasingly physical; those same gestures need motor-access alternatives. [Staff discussion](https://www.pocketgamer.com/the-room-old-sins/pocket-gamer-speaks-what-does-the-team-think-of-box-based-horror-adventure-the-r/).
- **Mekorama — solo-made mechanical dioramas; scope efficiency and community creation.** Martin Magni documents 50 small levels, an editor and self-contained QR level cards; his press kit says pay-what-you-want was profitable largely because he kept expenses low. Do not promote this to a normal income model. [Press kit](https://www.mekorama.com/press/). Pocket Gamer's 2016 comparison found camera rotation clunky and pushing robots dull; the developer calls falling off platforms intentional physics. This is a useful disagreement: a valid simulation can still communicate failure poorly. [Critique](https://www.pocketgamer.com/mekorama/review/), [developer FAQ](https://www.mekorama.com/faq/).
- **Townscaper — creative 3D toy; relaxation and self-expression.** PC Gamer's 2021 desktop review praises coherent, automatically adapting architecture, sound and incidental signs of life. No goals or simulated population makes it relaxing for some and insubstantial for others. Its screenshot/export features extend the creative payoff, but this desktop review does not verify mobile feature parity. [Review](https://www.pcgamer.com/townscaper-review/). Mobile release is separately catalogued for iOS and Android. [Mobile listing](https://www.pocketgamer.com/townscaper/).
- **Suzy Cube — true 3D platformer; charm with input caveats.** Christine Chan's 2018 iOS review likes characters, music and environments, but describes invisible touch zones as vague, automatic camera turns as initially jarring, and depth judgment as a cause of missed jumps. A clean screenshot can hide a poor control contract. [Review](https://www.imore.com/suzy-cube-review-putting-some-bounce-back-your-platforming).
- **Riptide GP: Renegade — arcade racing; repeatable mastery.** SuperPhillip's 2016 mobile review praises tilt/touch/controller choices and course readability, but reports unreliable multi-flick tricks, repetitive track reuse and slow matchmaking. A good race loop still needs input recognition and an audience for online modes. These are launch-era observations. [Review](https://www.superphillipcentral.com/2016/09/riptide-gp-renegade-ios-android-review.html). Vector Unit added mobile cross-platform matchmaking in November 2016; shared builds and shared player pools are separate work. [Developer announcement](https://www.vectorunit.com/blog-posts/2016/11/14/renegade-goes-cross-platform-for-online-play-on-mobile).
- **Crossy Road — 3D presentation with constrained movement; immediate replay.** Pocket Gamer's 2014 review praises simple taps/swipes, quick restart, readable personal competition and humorous, functionally equivalent characters. Its limitation is deliberate simplicity; it is a useful small-team scope reference, not a free-camera 3D action model. [Review](https://www.pocketgamer.com/crossy-road/review/). TIME's contemporary reviewer enjoyed short sessions but disliked recurring ad prompts even though spending was unnecessary. Optional monetization can still interrupt. [Review](https://time.com/3602328/crossy-road-iphone/).
- **Bad North — bounded real-time tactics.** Craig Grannell’s 2019 mobile review praises touch rotation, short battles and selection that slows time. Permanent squad loss felt harsh; higher difficulty did not necessarily add strategic depth. Approachable input and forgiving consequences are different choices. Its developer also documented an iOS snag delaying the joint launch. [Stuff review, updated 2021](https://www.stuff.tv/review/app-of-the-week-bad-north-jotunn-edition-review/), [developer announcement](https://www.badnorth.com/news/android-ios-preorder).
- **Sky: Children of the Light — social exploration; a large-scope comparison.** Pocket Gamer's 2019 review praises optional companionship and expressive gestures, while criticizing conspicuous boundaries and the effort needed for the secondary ending. [Review](https://www.pocketgamer.com/sky-children-of-the-light/review/). A June 2024 player discussion describes burnout from currency routes and misunderstood season rewards; replies disagree on whether daily grinding is necessary. Use it as a failure hypothesis and comprehension test, not a population-level retention result. [Discussion](https://www.reddit.com/r/SkyChildrenOfLight/comments/1djv955/i_feel_so_burned_by_this_game/).
- **Hitman GO — major-publisher comparison, not an indie.** Mark Brown's 2014 review praises the coherent tabletop world and turn-based interpretation of stealth; he dislikes the lack of undo. It shows how a mobile adaptation can preserve a fantasy while changing the control and time model. [Review](https://www.pocketgamer.com/hitman-go/review/).

### Current listing checks, 2026-11-08

All ten profiles have live first-party listings on both platforms. Apple entries checked through the public US iTunes lookup endpoint (`https://itunes.apple.com/lookup?id=ID&country=us`); all Google Play URLs opened and returned the named game. This establishes publicly listed availability, not successful installation for every account, territory or phone. OS values below are published metadata, not tested reliability.

| Game | iOS listing / published version / minimum OS | Android listing |
|---|---|---|
| Suzy Cube | [App Store](https://apps.apple.com/us/app/suzy-cube/id1293337633?uo=4) · 1.0.2 · iOS 8.0 | [Google Play](https://play.google.com/store/apps/details?id=com.noodlecake.suzycube) |
| Bad North | [App Store](https://apps.apple.com/us/app/bad-north-jotunn-edition/id1367121168?uo=4) · 2.00.23 · iOS 15.0 | [Google Play](https://play.google.com/store/apps/details?id=com.PlausibleConcept.BadNorthFull) |
| Crossy Road | [App Store](https://apps.apple.com/us/app/crossy-road/id924373886?uo=4) · 7.14.3 · iOS 15.0 | [Google Play](https://play.google.com/store/apps/details?id=com.yodo1.crossyroad) |
| Riptide | [App Store](https://apps.apple.com/us/app/riptide-gp-renegade/id1090577736?uo=4) · 2026.08.27 · iOS 15.0 | [Google Play](https://play.google.com/store/apps/details?id=com.vectorunit.silver.googleplay) |
| Mekorama | [App Store](https://apps.apple.com/us/app/mekorama/id1079464948?uo=4) · 1.7.2 · iOS 11.0 | [Google Play](https://play.google.com/store/apps/details?id=com.martinmagni.mekorama) |
| Old Sins | [App Store](https://apps.apple.com/us/app/the-room-old-sins/id1286676015?uo=4) · 1.0.4 · iOS 10.0 | [Google Play](https://play.google.com/store/apps/details?id=com.FireproofStudios.TheRoom4) |
| Townscaper | [App Store](https://apps.apple.com/us/app/townscaper/id1549531491?uo=4) · 1.04 · iOS 11.0 | [Google Play](https://play.google.com/store/apps/details?id=com.OskarStalberg.Townscaper) |
| Monument Valley | [App Store](https://apps.apple.com/us/app/monument-valley/id728293409?uo=4) · 3.9.744 · iOS 15.0 | [Google Play](https://play.google.com/store/apps/details?id=com.ustwo.monumentvalley) |
| Sky | [App Store](https://apps.apple.com/us/app/sky-children-of-the-light/id1462117269?uo=4) · 0.35.2 · iOS 15.0 | [Google Play](https://play.google.com/store/apps/details?id=com.tgc.sky.android) |
| Hitman GO | [App Store](https://apps.apple.com/us/app/hitman-go/id731645633?uo=4) · 1.18 · iOS 13.0 | [Google Play](https://play.google.com/store/apps/details?id=com.squareenixmontreal.hitmango) |

Old listed builds can retain lower published runtime minima than today’s new-upload rules. Their iOS 8/10/11 metadata does not mean a new game can submit with those deployment targets. It also does not establish reliable play on every current device.

Notable correction: Mekorama’s old press kit says iOS 9; current Apple metadata says iOS 11. Treat the kit’s compatibility line as historical. Google Play now labels Mekorama as containing ads and IAP; its historic pay-what-you-want model is not its current full monetization description.

## Visual design directions and resources

These are named design families inferred from examples, not measured market trends.

- **Sculptural diorama.** Monument Valley / Hitman GO / Mekorama: bounded stage, legible geometry, spare interface, small figures, coherent object affordances. Fits puzzles and tactics. Main risk is unreadable paths or misleading perspective; camera and level design cost more than the low-detail geometry suggests. Brand typography belongs in framing UI, not across paths. The current store screenshot inspection below supports the appearance; the reviews support interaction judgments.
- **Tactile cabinet.** Old Sins: close framing, dark surroundings and material contrast, visible in the inspected image below. Fits object inspection. Budget detailed assets; keep text brighter and simpler than the world. The review supports tactile interaction; no direct play was performed.
- **Atmospheric journey.** Sky: broad light/color families, distant landmarks, small caped silhouette, luminous points of focus. Fits exploration and companionship. Risks: overexposure, inaccessible low-contrast forms, GPU-heavy effects and scope inflation. **Direct inspection:** rendered page 18 of Yuichiro Tanabe's 2020 GDC art deck; six environment strips move from pale dawn through clear blue daylight, cyan rain, warm pink sunset, green dusk and dark blue night. This supports authored mood progression, not motion quality or current mobile performance. [Art deck](https://media.gdcvault.com/gdcsummer2020/presentations/Tanabe-Yuichiro-Art%20of%20Sky_%20Children%20of%20the%20Light.pdf).
- **Playful block world.** Crossy Road / Suzy Cube: chunked forms, clear character silhouettes, limited text during action, comic animation. Fits small-screen arcade play and collectible variation. Risk: visually distinct characters can conceal ambiguous movement or collide with camera readability. Avoid equating simple art with simple production.
- **Creative miniature.** Townscaper: a restrained palette, automatic architectural detail and little visible pressure. Fits toys and creative sandboxes. Avoid adding currencies and alert badges solely to imitate other mobile games; the absence of chores is part of the promise. Desktop review supports this interpretation; mobile parity unverified.

### Turn a direction into a coherent interface

The following are proposed design systems derived from the inspected appearances and reviewed interactions. They are not claims that every named game uses these exact fonts or spacing values.

| Direction | Type, spacing and surfaces | Controls and motion | What undermines it |
|---|---|---|---|
| Sculptural diorama | Quiet readable sans text; sparse edge framing; generous space around the stage; flat panels that do not compete with geometry | Small visual handles with generous hit regions; measured mechanical transitions; minimal overlays | Decorative text across paths, arbitrary rotations, too many badges, hidden walkable edges |
| Tactile cabinet | Display serif or engraved lettering only for atmosphere; clear functional text; dark framing with bright local focus; inventory slots with stable alignment | Consistent inspect/operate modes; movement suggests hinges, weight and friction; restrained highlights | Tiny decorative type, dark-on-dark clues, excessive surface noise, every object moving differently |
| Atmospheric journey | Low-density HUD, gentle typography, generous separation, translucent framing only where contrast remains sufficient | Small set of expressive verbs; camera motion supports landmarks; readable non-motion alternatives | Bloom hiding silhouettes, low-contrast prompts, UI made invisible in pursuit of immersion |
| Playful block world | Bold compact headings, plain numeric scores, broad color areas, repeated simple icon shapes | Snappy but readable anticipation/impact/recovery; immediate retry; characters remain identifiable at distance | Inconsistent asset-pack proportions, tiny detailed icons, effects hiding hazards, screenshot-clean invisible controls |
| Creative miniature | Quiet tool labels, compact repeatable palette controls, neutral panels around colorful creations | Immediate construction feedback, clear undo, camera gestures that do not accidentally build | Currency clutter, constant prompts, unclear selection, publishing that interrupts private experimentation |

Choose one world/character language and one functional UI language. Use the same spacing and type hierarchy across pause, settings, shop and results, while keeping their priorities different. A purchase price or error message must remain legible even when it is less atmospheric than the scene. Prototype disabled, focused, pressed, loading and long-localized states before polishing only the default screen.

The evidence does not establish a single cross-platform visual trend. These are durable, currently listed game families, some rooted in decade-old designs. Sleek mockups supply composition ideas; shipped screenshots establish appearance; reviews and recorded footage add behavioral evidence. None alone establishes daily comfort or conversion.

### Inspected visual evidence

Inspected the second iPhone screenshot returned by each current US App Store listing. These are publisher-selected static images, not hands-on verification or necessarily newly captured builds.

- **Monument Valley:** Tall warm yellow/orange towers fill a portrait frame. Pink ledges and stairs separate walkable surfaces; tiny white Ida contrasts with dark crow figures. A small circle in the upper left is the only obvious overlay. Strong shape hierarchy and restrained UI support the sculptural-diorama family; the image cannot establish pathfinding or touch precision. [Exact image](https://is1-ssl.mzstatic.com/image/thumb/Purple114/v4/9c/3d/9b/9c3d9bb0-6ae5-f0dd-4349-32aba7f268ec/mzl.sbjggnvt.png/392x696bb.png).
- **Old Sins:** Landscape attic shot: a lit dollhouse on a table, large projector at right, dark beams and textured surfaces. Five empty inventory slots line the left; a small pause control sits upper right. Lighting directs attention without a large quest panel. The dark visual field needs brightness/contrast checks on real devices; this screenshot supports atmosphere, not proof of legibility outdoors. [Exact image](https://is1-ssl.mzstatic.com/image/thumb/Purple118/v4/93/e1/95/93e195ba-b877-b2d1-e1e7-6cb72e2f551a/pr_source.jpg/406x228bb.jpg).
- **Crossy Road:** Portrait scene uses chunky rectangular vehicles, pedestrians and building forms with hard shadows and broad grey road bands. Strong orange, blue and yellow accents separate objects. It is a scene sample without visible score/control overlays; do not claim this proves the full gameplay HUD is absent. [Exact image](https://is1-ssl.mzstatic.com/image/thumb/PurpleSource211/v4/94/73/24/9473247b-1ba6-cd56-f3ec-71e5409f09e5/OS_iPhone5.5in_1242x2208.00_00_18_22.Still005.png/392x696bb.png).
- **Townscaper:** Promotional portrait composite contains two framed town views above the large TOWNSCAPER wordmark. Pale walls and warm roofs sit against muted teal water; varied heights and irregular bridges build miniature charm. Because this is a marketing composite, it supports palette/material direction only, not in-game control layout. [Exact image](https://is1-ssl.mzstatic.com/image/thumb/PurpleSource115/v4/72/48/48/724848f8-bebd-ca31-64ff-8f918d2c1e64/4a1a20f5-a36a-4347-8a87-d7a1109e8b9a_Townscaper_Apple_AppStore_5.5_Inch_2.png/392x696bb.png).

### Recorded motion inspection

The official **Mekorama** mobile trailer (Martin Magni, April 26, 2016; 27 seconds) was inspected through half-second frame sequences across 0–24 seconds. At 0–9s a robot tumbles into water while the view changes; at 9–14s a narrow tower stays central during traversal; at 17–20s an open cube rocks; at 20–24s an editor palette appears below built scenes. These samples support physical character animation and a centered miniature composition. [Official trailer](https://www.youtube.com/watch?v=vaSJyEDmgWA), [developer press kit](https://www.mekorama.com/press/).

This is sampled recorded motion, not continuous playback or live play. Editorial crossfades do not establish native transitions. Input contacts are absent, so gesture recognition, latency and current-build behavior remain untested. The useful design inference is to let clearly framed object movement communicate change before adding explanatory HUD text. A separate Old Sins clip proved to be the PC remaster and was excluded from mobile-fidelity evidence.

### Design reference sources

**Game UI Database** is a free shipped-game reference collection; the 2024 snapshot had 55,000+ screenshots, 1,700+ videos and 1,341 titles. Filters include screen types, controls and HUD elements; gallery tools expose typography/icon details and color-vision simulations. Use it to compare pause, inventory, shop and failure states under the same input constraints. The creator explicitly documents Mobile/Tablet filtering. Counts are dated, not a 2026 census. Direct site fetch was restricted, so the described facilities were checked through the creator/report; the current search interface was not tested. Screenshots remain references, not licensed production art; a simulation does not replace accessibility testing. [Creator announcement](https://www.reddit.com/r/gamedev/comments/npac2u/game_ui_database_end_of_may_update/), [relaunch report](https://www.gamedeveloper.com/design/game-ui-database-relaunches-with-new-features-video-support-and-over-55-000-screenshots).

**Type and icons:** Google Fonts’ repository carries each family’s license; most use OFL, some Apache or Ubuntu terms. Preserve notices and reserved-name restrictions when modifying fonts. Select one readable UI family with the required scripts, then test the actual engine’s shaping/fallback path. Game-icons.net requires author credit; Material Symbols use Apache-2.0. The former suits objects/actions, the latter neutral settings. Neither replaces testing whether players understand an icon. See catalog entries 97–99 for owning sources.

**Art and authoring resources:** Kenney supports coherent simple prototypes; Poly Haven and ambientCG supply material/lighting references; Quaternius offers stylized sets under its current QAL. Use each pack’s actual license and render cost, not the site’s reputation. Blender/engine demo projects are inspectable production starting points, but examples do not supply a complete save, purchase or accessibility architecture. See the asset workflow and catalog for terms and limits.

**Independent critique and primary craft:** The paired game reviews explain what screenshots conceal: depth errors, camera turns, repetition and harsh consequences. Sky’s art deck explains authored mood; the accessible Game Programming Patterns chapters explain implementation tradeoffs. Use these to form hypotheses, then test the prototype. No source establishes that mimicking a hit’s surface design reproduces its audience or revenue.

## Specific screens and components: 100 practical details

### Screen compositions to prototype

**Title/return screen:** Continue with recognizable save context; secondary level selection and settings; optional account/sync status only when relevant. Keep New Game apart from Continue and explain destructive replacement. A new player should reach the core verb before optional news, sign-in and promotions. This composition applies the onboarding, save and input evidence above; it is not a required template.

**Pause screen:** Resume first; current objective/hint access; controls and accessibility settings; restart/quit with the actual progress consequence. Keep the gameplay scene legible but still where possible. For an unpausable online match, label the menu honestly and keep essential status visible; never imply the world stopped.

**Level browser:** Distinguish completed, available, locked, paid and downloading states with more than color. Preserve position after play and return to the selected chapter. Show why a level is locked. A finite puzzle benefits from chapter structure; an endless runner may need only mode choice and best score.

**Shop:** Separate owned, equipped, locked, previewable and purchasable goods. Keep local currency formatting, the exact bundle contents and a normal route back. Show a cosmetic on the actual character/camera scale before buying. Verify localized prices with store products; stale hardcoded price text can disagree with checkout.

**Settings:** Group controls, sound, display/performance, accessibility, language, account and support according to actual features. Apply reversible settings immediately with a nearby preview; isolate Reset and destructive actions. A complex remapping editor may need explicit Save/Cancel. Do not add native-app forms, search or tabs where the game has no corresponding task.

**Creation browser/editor:** New, duplicate, rename, save, undo/redo, test-play and export should form one recoverable loop. Keep an unsaved editing session separate from the last published level. Import errors identify unsupported version or malformed content without replacing the current creation. The Mekorama example below motivates portable sharing; public discovery adds moderation and storage obligations.

**Result/retry screen:** Show what happened, earned progress and the next playable action. Keep Retry stable and prominent for short runs; make replay objectives secondary. Separate earned rewards from optional ad multipliers so a player knows what is already theirs. A narrative ending may deserve time to breathe instead of an immediate sales panel.

**Download/recovery screen:** Name the needed chapter, bytes/progress when known, network/storage problem and available Retry/Cancel actions. Show already playable content. Distinguish a save-sync problem from missing assets; deleting a local save is not a normal network repair.

**Inventory/loadout:** Show selected versus equipped state, usable versus cosmetic effects, and a readable preview. Preserve selection while inspecting another item. Offer clear categories or search only when collection size earns them. A tactile puzzle inventory can remain small and spatial; a large equipment list needs filtering and comparison.

**Lobby/matchmaking:** Show party members, readiness, region/version mismatch, search state and cancellation. Keep invitation failures specific. Distinguish a private room from a publicly discoverable one; a disabled Start button should explain the missing condition. Do not imply everyone paused when one player opens settings.

### Practical reference: platform, input and recovery

Each paragraph pairs a build choice with its failure mode. “Derived” means engineering or design guidance inferred from the cited mechanism, not a vendor rule or measured experiment. Genre exceptions matter.

**P01 — First playable content.** Ship a meaningful opening in the initial install. An immediate second download turns anticipation into another wait. Apple’s 2024 talk suggests about 15 minutes of initial play; this is a design example, not a universal size quota. Tiny complete games need no streaming. [WWDC24 transcript](https://developer.apple.com/videos/play/wwdc2024/10085/).

**P02 — Adaptive HUD anchors.** Anchor controls in separate groups and preserve usable sizes across aspect ratios. Scaling one screenshot can leave buttons tiny or beyond thumb reach. Adjust the camera separately from the HUD; do not sacrifice important scene content to fill every pixel. [WWDC24 transcript](https://developer.apple.com/videos/play/wwdc2024/10085/).

**P03 — Concurrent actions.** Prototype movement, aiming and firing together. Three independently reachable buttons can still require an impossible third thumb. Combine or rearrange actions according to the mechanic; automation changes difficulty and needs playtesting. [WWDC24 transcript](https://developer.apple.com/videos/play/wwdc2024/10085/).

**P04 — Direct camera drag.** Compare direct dragging with a virtual right stick. Apple demonstrates direct pan for fast camera movement; inertia and pinch fit some overhead views. Neither suits every precise platformer or spatial puzzle. Test accidental movement while selecting objects. [WWDC24 transcript](https://developer.apple.com/videos/play/wwdc2024/10085/).

**P05 — Meaningful touch icons.** Show the action, such as jump or interact, instead of an unexplained controller letter. Reflect changing context without moving the target under the player’s finger. Hide irrelevant controls when safe; persistent disabled controls can better explain a locked ability. [Apple controls](https://developer.apple.com/design/human-interface-guidelines/game-controls).

**P06 — Press feedback outside the thumb.** Show an immediate highlight or halo that survives finger occlusion. Sound and haptics can reinforce it but cannot be the only confirmation. A server response should not be required to acknowledge the local press. [Apple controls](https://developer.apple.com/design/human-interface-guidelines/game-controls); networking distinction is derived.

**P07 — Real target sizes.** Apple recommends 44×44 pt frequent controls; its game guidance permits 28×28 pt secondary targets. Do not use that smaller allowance as the default for urgent actions. Engine pixels need correct conversion, spacing and device checks. [Apple controls](https://developer.apple.com/design/human-interface-guidelines/game-controls).

**P08 — Safe reach.** Keep frequent actions near thumbs and away from cutouts and system gesture zones. A full-bleed world does not require full-bleed controls. Test left/right landscape orientations with the charging cable and both hands. The physical setup test is derived. [Apple controls](https://developer.apple.com/design/human-interface-guidelines/game-controls).

**P09 — Reconfigurable controls.** Offer useful presets and size/position adjustment for a dense HUD. A full editor is unnecessary for a one-tap game. Validate saved layouts after resolution changes; never let customization make Reset unreachable. [XAG 107](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/107); reset validation is derived.

**P10 — Release-to-activate menus.** Allow a menu press to cancel when dragged away before release. Triggering purchases or destructive commands on touch-down removes that escape. Immediate gameplay actions, such as a shot or musical note, have a legitimate latency exception. [XAG 107](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/107).

**P11 — Stable targets.** Keep accurate menu targets stationary while selecting them. A rotating carousel or reward button that shifts as it appears turns selection into a timing test. Animate decoration or wait until the transition ends before accepting input. [Game Accessibility Guidelines](https://gameaccessibilityguidelines.com/make-interactive-elements-that-require-accuracy-eg-cursor-touch-controlled-menu-options-stationary/).

**P12 — Gesture alternatives.** Provide a tap or sequential alternative to essential multi-finger and sustained drag gestures where the mechanic permits. A two-finger requirement excludes some players even when every button is large. Avoid calling the whole game accessible based on menus alone. [Game Accessibility Guidelines](https://gameaccessibilityguidelines.com/ensure-that-multiple-simultaneous-actions-eg-click-drag-or-swipe-are-not-required-and-included-only-as-a-supplementary-alternative-input-method/).

**P13 — Game-level remapping.** Keep prompts and tutorials in sync with remapped actions. System remapping is a fallback, not a substitute for findable, contextual in-game settings. Walking and driving may need different action maps; retain a safe menu map. [IGDA remapping guidance](https://igda-gasig.org/how/platform-level-accessibility-recommendations/system-level-button-remapping/).

**P14 — Input switching.** Accept touch after controller use and update hints when the active input changes. Do not trap players in a controller-only mode after disconnection. A short visual delay can prevent hints flickering from stick noise; input acceptance should remain immediate. [Android natural input](https://developer.android.com/games/develop/multiplatform/enable-natural-input-on-all-form-factors).

**P15 — Real mouse support.** On supported desktop-like Android targets, handle pointer hover, buttons and relative movement where relevant. Mouse-as-touch compatibility can launch a game without making camera steering or inventory pleasant. Treat PC support as an adapted experience and test it separately. [Android natural input](https://developer.android.com/games/develop/multiplatform/enable-natural-input-on-all-form-factors).

**P16 — Complete controller navigation.** A controller-supported game must let the player start, change settings, dismiss dialogs and recover from failure with that controller. Gameplay alone is insufficient. Preserve visible focus and a predictable route back after closing an overlay. [XAG 107](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/107).

**P17 — Input latency.** Measure response, not only average FPS. A full render queue can delay a press even when animation appears smooth. Trace input and frame delivery; reduce queued work before compensating with exaggerated animation. [Android tracing guidance](https://developer.android.com/games/optimize).

**P18 — Honest performance modes.** Offer comprehensible battery/performance/quality choices when useful. Do not promise 60 FPS on every supported device. Google describes 30 FPS as a reasonable general floor and higher rates as a genre/device tradeoff, not a guarantee of good action feel. [Android technical quality](https://developer.android.com/quality/technical).

**P19 — Quiet menus.** Reduce unnecessary menu rendering and costly background scenes. A settings screen should not heat the phone like combat. Preserve needed animation and responsiveness while reducing idle GPU work. [Android technical quality](https://developer.android.com/quality/technical).

**P20 — Motion controls.** Expose independent camera sensitivity, shake/bob intensity and motion-blur choices when those effects exist. A single “effects low” switch can remove useful combat information while retaining the offending motion. FOV changes need gameplay and performance review. [XAG 117](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/117).

**P21 — Still menus behind text.** Let players stop decorative motion and auto-updating text. An opaque text panel helps when gameplay must continue. Do not interpret reduced motion as a demand to remove every animation essential to the mechanic. [XAG 117](https://learn.microsoft.com/en-us/xbox/accessibility/xbox-accessibility-guidelines/117).

**P22 — Honest accessibility labels.** Evaluate the shipped flows against the claimed feature, including cutscenes and settings. A shake toggle does not prove all reduced-motion criteria. Publish precise capabilities so players can judge before buying. [Apple reduced-motion criteria](https://developer.apple.com/help/app-store-connect/manage-app-accessibility/reduced-motion-evaluation-criteria).

**P23 — Redundant color encoding.** Give keys, teams, hazards and rarity meaningful shapes, symbols or patterns as well as color. A whole-screen color filter can distort art without making the relevant pair distinguishable. Test the actual puzzle or combat state, not just a palette swatch. [Game Accessibility Guidelines](https://gameaccessibilityguidelines.com/ensure-no-essential-information-is-conveyed-by-a-fixed-colour-alone/).

**P24 — Captions beyond dialogue.** Convey consequential non-speech sounds, such as an offscreen threat, through captions or equivalent cues. Translated dialogue alone leaves hearing-dependent mechanics intact. Avoid covering the threat with the caption itself. [W3C captions guidance](https://www.w3.org/WAI/media/av/captions/); threat placement is a game-specific inference.

**P25 — Readable instructions.** Use short concrete verbs, then let the player try the action. Ornate lore can retain its voice elsewhere. Dense prerequisite instructions exclude some readers and conceal the very action being taught. [Game Accessibility Guidelines](https://gameaccessibilityguidelines.com/use-simple-clear-language/).

**P26 — Early accessibility settings.** Make sound, text and motion options reachable before an intense opening. A settings menu unlocked after the tutorial arrives too late. Offer contextual defaults rather than a compulsory questionnaire. [Game Accessibility Guidelines](https://gameaccessibilityguidelines.com/full-list/).

**P27 — Adjustable effort.** Where compatible with the game, offer alternatives to mashing, prolonged holds and precise timing. Remapping alone does not remove fatigue. Separate assists from core difficulty so a player can change one barrier without changing every rule. [Game Accessibility Guidelines](https://gameaccessibilityguidelines.com/full-list/); independent assist design is derived.

**P28 — Audio channels.** Separate music, effects and speech volumes. Muting music should not remove a critical cue; mono output and visual cues help players without reliable stereo hearing. Test speaker, headphones and Bluetooth routes. [Game Accessibility Guidelines](https://gameaccessibilityguidelines.com/full-list/).

**P29 — Silent mode.** Respect iPhone silence for incidental game audio and system volume changes. Do not assume that audio engine defaults match the intended platform behavior. Explicit media playback has different expectations; inspect the configured session. [Apple audio guidance](https://developer.apple.com/design/human-interface-guidelines/playing-audio).

**P30 — Audio interruption recovery.** Handle calls and output-route changes without stale loops or sudden full-volume playback. Resuming sound and resuming dangerous gameplay are separate decisions. A returned player may need a paused view even if the audio session is available. [Apple audio guidance](https://developer.apple.com/design/human-interface-guidelines/playing-audio); gameplay distinction is derived.

**P31 — Save expectations.** Explain autosave briefly and show a discreet completed checkpoint. A decorative “saving” icon must correspond to actual durability. Checkpoint-based games should make the amount of possible replay clear. [Accessible Game Design: saving](https://www.accessiblegamedesign.com/guidelines/saving.html).

**P32 — Suspend without punishment.** Distinguish deliberate in-game death from an OS interruption. Derived design: preserve a suspend state for offline runs without turning it into an unlimited reload exploit. Test force-kill after each meaningful transition; a quit callback alone cannot demonstrate safety. [Accessible Game Design: saving](https://www.accessiblegamedesign.com/guidelines/saving.html).

**P33 — Save conflict context.** If a safe automatic merge is impossible, show both saves with chapter, playtime and timestamp before replacement. “Local or cloud?” is insufficient. Preserve a recoverable copy where feasible. Google explicitly leaves game-specific conflict resolution to the developer. [Android saved games](https://developer.android.com/games/pgs/android/saved-games).

**P34 — Currency is not a high score.** Derived from snapshot conflict semantics: merging maximum level completion may be safe; taking maximum currency after offline spending can create money. Define separate rules for unlocks, settings, world state and transactions. Cloud storage does not make those rules correct. [Android saved games](https://developer.android.com/games/pgs/android/saved-games).

**P35 — Sync completion.** Distinguish saved-on-device from uploaded. Keep retries bounded and recoverable; another conflict can occur during resolution. A spinner that blocks offline play indefinitely defeats a local-first game. Online-authoritative economies need a different offline contract. [Android saved games](https://developer.android.com/games/pgs/android/saved-games).

**P36 — Android Back.** Back closes the top overlay or returns through the game’s menu hierarchy; during active offline play it can open Pause. Test the actual engine’s current Back integration. Legacy key interception is insufficient for modern predictive Back. Root exit should use supported system behavior. [Android Back migration](https://developer.android.com/guide/navigation/custom-back/predictive-back-gesture); hierarchy is derived game guidance.

**P37 — System gesture escape.** Keep home/back escape usable. Limit gesture exclusions to necessary gameplay regions and remove them in menus. A swipe mechanic along the edge needs real-device tests; demanding that players disable gesture navigation is a poor workaround. [Android gesture compatibility](https://developer.android.com/develop/ui/views/touch-and-input/gestures/gesturenav).

**P38 — Language selection.** Use language names, support a clear return path and persist the choice. Separate locale-sensitive resources; test long translations and mixed-direction player names. Engine-rendered text does not gain Android resource layout behavior automatically. [Android language support](https://developer.android.com/training/basics/supporting-devices/languages); engine boundary is derived.

**P39 — RTL without reversed mechanics.** Mirror reading order and appropriate navigation while preserving intentional world coordinates and puzzle geometry. Arabic shaping, punctuation and embedded Latin names need real examples. Blindly flipping the render surface changes gameplay, not just language. [Android language support](https://developer.android.com/training/basics/supporting-devices/languages); world-coordinate distinction is derived.

**P40 — Contextual reminders.** Ask for notification permission when a player chooses a useful reminder, not before the first action. Recheck authorization; denied reminders must not block play. Distinguish a desired friend/turn alert from habitual re-engagement spam. [Apple notification authorization](https://developer.apple.com/documentation/usernotifications/asking-permission-to-use-notifications).

### Practical reference: purchases, service states and tools

These details apply only when the game supports the named feature. Backend and QA recommendations are derived from the failure mechanisms, not universal requirements for a small offline toy.

**P41 — Pending purchase state.** Show Pending separately from failure and success. Payment can finish outside the game; reconcile on return. Do not grant currency while the payment remains pending or encourage another purchase to clear the spinner. [Play Billing integration](https://developer.android.com/google/play/billing/integrate).

**P42 — Delivery acknowledgement.** Grant verified value durably, then acknowledge/consume as appropriate. Play’s three-day acknowledgement clock starts at Purchased, not Pending. A lost acknowledgement can trigger a refund; a retry must not deliver twice. [Play Billing integration](https://developer.android.com/google/play/billing/integrate).

**P43 — Purchase completion timing.** Queue a clear receipt/reward message at a safe point if approval arrives during combat. Do not cover the action or silently change the balance. Cancellation is an ordinary outcome, not an alarming error. [Play Billing integration](https://developer.android.com/google/play/billing/integrate).

**P44 — Transaction identity.** Deduplicate using the store’s documented purchase identity, bound to the intended game account. Do not use Google order ID as the universal key: some purchases lack it. Restore and retry need the same protection as the initial callback. [Play billing security](https://developer.android.com/google/play/billing/security).

**P45 — Refund handling.** Define what happens to unused and already-spent goods after revocation. Explain the result and provide a support route; a cryptic negative balance looks like corruption. Aggressive account bans are a product policy, not an automatic consequence of every refund. [Play billing security](https://developer.android.com/google/play/billing/security).

**P46 — Store outage.** Keep owned offline content playable when the product catalog fails to load. Offer Retry and a precise unavailable state for new purchases. Local StoreKit simulation cannot establish production catalog availability; test sandbox/store configurations too. [Apple purchase testing](https://developer.apple.com/documentation/storekit/testing-in-app-purchases-in-xcode); offline behavior is derived.

**P47 — Restore clarity.** A permanent unlock needs a visible recovery route and a clear account/store explanation. Distinguish restoring entitlement from restoring a save. Neither necessarily transfers an iOS purchase to Android; any cross-store promise needs an explicit product/account design. [App Review Guidelines](https://developer.apple.com/app-store/review/guidelines/); transfer distinction is derived.

**P48 — Account deletion.** If accounts exist, make deletion initiation findable and explain progress, purchases and billing consequences before confirmation. “Log out” or temporary deactivation is insufficient. Keep subscription cancellation distinct from data deletion. [Apple account deletion](https://developer.apple.com/help/app-review/guideline-reference/5-1-1-account-deletion).

**P49 — Child-directed ads.** Decide audience before selecting ad SDKs and formats. Google requires appropriate certified SDK versions and restricts targeting and disruptive formats for children/unknown-age users in applicable mixed-audience apps. A neutral age screen is not permission to misstate the audience. [Google Families policy](https://support.google.com/googleplay/android-developer/answer/9893335).

**P50 — Dismissible commercial content.** Keep ads visibly distinct from gameplay, with a real close target. Google Families rules specifically prohibit deceptive placement and emotionally manipulative tactics, with detailed five-second dismissal conditions. Read those conditions rather than transplanting ordinary rewarded-video assumptions. [Google Families policy](https://support.google.com/googleplay/android-developer/answer/9893335).

**P51 — Social safety controls.** Ship reporting, blocking and a response process with public social/UGC features. A Report button without anyone handling reports is incomplete. Private offline level editing has a different service burden from hosting a searchable public gallery. [App Review Guidelines §1.2](https://developer.apple.com/app-store/review/guidelines/).

**P52 — Loading that admits uncertainty.** Show real determinate progress when available; otherwise say what is happening and provide recovery. Avoid invented percentages that sit at 99%. Let players revisit downloaded content while a later level loads when architecture permits. [Apple loading guidance](https://developer.apple.com/design/human-interface-guidelines/loading).

**P53 — Interrupted asset downloads.** Derived: retain verified completed chunks, check free space, and distinguish no network from corrupt content. Do not erase a working installed chapter before its replacement is usable. A reliable updater protects play as well as bandwidth. [Apple loading guidance](https://developer.apple.com/design/human-interface-guidelines/loading).

**P54 — Warm-device quality.** Test after sustained play, while charging, and in a warm environment. A cold launch benchmark can hide throttling. Lower expensive visual work before changing the rules; offer a stable fallback if thermal signals are unavailable. [Android Thermal API](https://developer.android.com/games/optimize/adpf/thermal).

**P55 — Hysteresis in quality changes.** Derived: avoid switching quality every few frames around a threshold. Use a slow recovery path after reducing load, preserve manual preferences and avoid resolution jumps during precise aiming. Thermal APIs report imperfect device-dependent signals; validate the policy on hardware. [Android Thermal API](https://developer.android.com/games/optimize/adpf/thermal).

**P56 — Transition memory peaks.** Measure old-level plus new-level overlap, not only steady gameplay. Release references deliberately and avoid loading all cosmetics to show one. A temporarily expanded heap may retain resident memory after the visible scene shrinks. [Android game memory reduction](https://developer.android.com/games/optimize/memory-reduction).

**P57 — Background resource ownership.** Stop or release unnecessary rendering, audio and loaded assets when leaving play. A small native download service need not retain the whole engine world. Test resumed state after the OS kills the cached process. [Android game memory reduction](https://developer.android.com/games/optimize/memory-reduction).

**P58 — Deterministic test fixtures.** Derived: record seed, level/content version, input sequence and relevant timing for reproducible bugs. Randomness without a recoverable seed makes a rare impossible layout hard to diagnose. Cross-device determinism needs proof beyond a fixed timestep. [Game Loop](https://gameprogrammingpatterns.com/game-loop.html).

**P59 — Pooled object reset.** Reset timers, ownership, physics, effects and subscriptions when recycling objects. A reused projectile must not inherit its predecessor’s damage or target. Set an intentional exhaustion policy: dropping a particle and dropping a quest item have different consequences. [Object Pool](https://gameprogrammingpatterns.com/object-pool.html).

**P60 — Explicit overlay ownership.** Derived: only the active modal accepts menu input; dismissing it restores the intended focus and pause state. A store sheet, ad and OS interruption can overlap. Independent booleans easily resume play while one blocker remains. [State](https://gameprogrammingpatterns.com/state.html).

### Practical reference: first play, levels, creation and social play

These design applications draw on the reviewed games and accessibility specialists. They are not measured conversion claims.

**P61 — Teach the first verb by using it.** Put a safe interaction beside a brief cue; avoid a detached instruction wall. It reduces the memory gap between reading and doing. [Interactive teaching](https://gameaccessibilityguidelines.com/include-interactive-tutorials/).

**P62 — Teach combinations after single actions.** Introduce move, camera and interaction separately before asking for coordination; a first-room control exam hides the game's appeal. [Interactive teaching](https://gameaccessibilityguidelines.com/include-interactive-tutorials/).

**P63 — Offer a current-objective reminder.** Restore the immediate task after days away; a story recap alone does not explain which door or item mattered. [Objectives](https://gameaccessibilityguidelines.com/indicate-allow-reminder-of-current-objectives-during-gameplay/).

**P64 — Make hints requested and progressive.** Reveal a nudge before the solution; automatic spoilers erase puzzle ownership. Mekorama places help in Pause. [FAQ](https://www.mekorama.com/faq/).

**P65 — Show an honest product promise.** Describe a creative toy as such. Artificial goals may damage its appeal; hiding the absence of challenge creates mismatched expectations. [Townscaper](https://www.pcgamer.com/townscaper-review/).

**P66 — Expose the touch zone when needed.** A subtle optional joystick teaches its center and limits; invisible controls can produce attractive screenshots and vague play. [Suzy Cube](https://www.imore.com/suzy-cube-review-putting-some-bounce-back-your-platforming).

**P67 — Test camera turns during jumps.** Avoid reversing apparent directions mid-action; fixed or guided cameras need their own transition tests. [Suzy Cube](https://www.imore.com/suzy-cube-review-putting-some-bounce-back-your-platforming).

**P68 — Make landing depth legible.** Use a stable landing marker/shadow and unobstructed surfaces; decorative perspective must not decide whether players can judge a jump. [Suzy Cube](https://www.imore.com/suzy-cube-review-putting-some-bounce-back-your-platforming).

**P69 — Distinguish movable architecture.** Repeated handle/dot language is preferable to random tapping of decorative geometry. A deliberate hidden-object game can hide clues. [Monument Valley](https://www.pocketgamer.com/monument-valley/review/).

**P70 — Show why an affordance is unavailable.** Retracting an occupied platform's handle explains the rule in place; a dead tap does not. [Monument Valley](https://www.pocketgamer.com/monument-valley/review/).

**P71 — Map touch to object motion.** Sliding a latch or rotating a dial can carry more meaning than a universal Use button; retain a simpler alternate input. [Old Sins](https://toucharcade.com/2018/01/24/the-room-old-sins-review/).

**P72 — Separate inspect from operate.** A consistent zoom context reduces camera/object drag conflicts; avoid making every swipe both orbit and manipulate. [Old Sins](https://toucharcade.com/2018/01/24/the-room-old-sins-review/).

**P73 — Offer touch alternatives to tilt.** Motion may be enjoyable but unsuitable when lying down, travelling or using a mount; calibrate when tilt is chosen. [Riptide](https://www.superphillipcentral.com/2016/09/riptide-gp-renegade-ios-android-review.html).

**P74 — Test complex gestures under pressure.** Multi-flick recognition must survive fast input; simplify or offer buttons if skilled intent repeatedly goes unrecognized. [Riptide](https://www.superphillipcentral.com/2016/09/riptide-gp-renegade-ios-android-review.html).

**P75 — Provide undo where reasoning is the challenge.** A mistaken tap should not force replaying an already solved sequence; omit undo only for a deliberate consequence model. [Hitman GO](https://www.pocketgamer.com/hitman-go/review/).

**P76 — Use extra objectives for replay.** Move limits or no-kill routes add a second problem without demanding a larger world; make the base completion goal clear. [Hitman GO](https://www.pocketgamer.com/hitman-go/review/).

**P77 — Do not add precision timing merely for variety.** A thinking game can offer pauses/skips for timed sections; action games can keep timing central while offering assists. [Timing](https://gameaccessibilityguidelines.com/do-not-make-precise-timing-essential-to-gameplay-offer-alternatives-actions-that-can-be-carried-out-while-paused-or-a-skip-mechanism/).

**P78 — Explain physics failure.** A robot falling is valid simulation, but the player needs a readable cause and quick recovery. Developer intent does not cancel reported frustration. [Mekorama comparison](https://www.pocketgamer.com/mekorama/review/), [FAQ](https://www.mekorama.com/faq/).

**P79 — Frame the puzzle before adding camera freedom.** Unhelpful views turn reasoning into camera maintenance; a rotatable scene still needs useful stopping angles. [Mekorama comparison](https://www.pocketgamer.com/mekorama/review/).

**P80 — Restart near the action.** Short arcade failure benefits from a direct retry; insert offers between selected runs rather than after every death. [Crossy Road](https://www.pocketgamer.com/crossy-road/review/).

**P81 — Put comparisons in context.** A friend's distance marker makes a score tangible during play; an isolated leaderboard is easier to ignore. Allow players to hide competition. [Crossy Road](https://www.pocketgamer.com/crossy-road/review/).

**P82 — Vary decisions before inflating duration.** Reusing tracks can support mastery, but repeated event templates can feel like padding. Distinct objectives must change how a route is played. [Riptide](https://www.superphillipcentral.com/2016/09/riptide-gp-renegade-ios-android-review.html).

**P83 — Deliver a real ending.** Short games can feel complete; an abrupt stop is a different problem from length. Budget the ending before optional sequel hooks. [Old Sins retrospective](https://toucharcade.com/2018/01/24/the-room-old-sins-review/).

**P84 — Let construction yield coherent results early.** Automatic roofs and connections make low-skill input rewarding; keep manual precision optional if relaxation is the promise. [Townscaper](https://www.pcgamer.com/townscaper-review/).

**P85 — Make creation shareable without rebuilding it.** Self-contained level cards can outlive one hosting site. Cloud links offer richer discovery but add service dependence. [Mekorama press kit](https://www.mekorama.com/press/).

**P86 — Support importing from the same phone.** Camera-only QR import fails when the code is already on screen; offer image import and clear scan recovery. [Mekorama FAQ](https://www.mekorama.com/faq/).

**P87 — Let cooperation emerge.** Shared actions and expressive gestures can create companionship without assigning compulsory team chores; this fits social exploration, not every competitive game. [Sky review](https://www.pocketgamer.com/sky-children-of-the-light/review/).

**P88 — Show the full cost of a seasonal goal.** State remaining time, required progress and paid gates before purchase; a currency tree should not conceal the actual commitment. [Sky player discussion](https://www.reddit.com/r/SkyChildrenOfLight/comments/1djv955/i_feel_so_burned_by_this_game/).

**P89 — Make stopping acceptable.** Reward return without implying daily completion is mandatory. Some users enjoy a routine; others report burnout. Test each audience separately. [Sky player discussion](https://www.reddit.com/r/SkyChildrenOfLight/comments/1djv955/i_feel_so_burned_by_this_game/).

**P90 — Keep cosmetics expressive without mandatory power.** Character humor can reward collection while preserving an equal core challenge; cosmetics still need honest availability and pricing. [Crossy Road](https://www.pocketgamer.com/crossy-road/review/).

**P91 — Make narrative text player-paced.** Let readers advance and revisit; automatic expiry penalizes reading speed and interruptions. Real-time dialogue needs a log or equivalent. [Guidelines](https://gameaccessibilityguidelines.com/full-list/).

**P92 — Label menus for screen readers.** An accessible options screen is useful but does not establish accessible spatial gameplay. Budget both semantics and a navigation model. [Screen-reader guidance](https://gameaccessibilityguidelines.com/ensure-screenreader-support-for-mobile-devices/).

### Practical reference: recovery and multiplayer

**P93 — Recoverable checkpoints.** Offer a visible support/recovery route to an earlier good checkpoint. Fireproof documents a hidden five-tap rollback menu and stuck iCloud sync workarounds. Keep the useful recovery capability; do not copy its discoverability problem. These support notes establish failure types, not their frequency. [Fireproof support](https://www.fireproofgames.com/ios_help).

**P94 — Friends across regions.** Explain region and version restrictions before an invitation fails. Riptide’s March 2025 support page says friends in different countries may use different servers. “Cross-platform” does not promise cross-region play; make the actual supported party contract visible. [Vector Unit support](https://vector-unit-faq.instantdocsbase.com/help/how-do-i-connect-with-my-friends-in-online-multiplayer).

**P95 — Cancellable matchmaking.** Show searching state, elapsed time and a real Cancel action; remove the server ticket, not just the spinner. Derived: reconcile a match-found response racing with cancellation and never silently join after the player returns to another mode. [Nakama matchmaker](https://heroiclabs.com/docs/nakama/concepts/multiplayer/matchmaker/).

**P96 — Population-aware modes.** Derived: each region, skill band and mode splits the available pool. Start with fewer queues, measure wait distributions and disclose bot practice if offered. Relaxing filters can improve waits while worsening fairness or latency; choose that tradeoff deliberately. [Nakama matchmaker](https://heroiclabs.com/docs/nakama/concepts/multiplayer/matchmaker/).

**P97 — Reconnect rules.** Derived: show reconnecting, the remaining grace period and what continues while disconnected. A server-authoritative game must define join-in-progress and departure rules; an SDK cannot infer them. Do not reset a ranked loss merely because the client disappeared. [Nakama authoritative multiplayer](https://heroiclabs.com/docs/nakama/concepts/multiplayer/authoritative/).

**P98 — Reward authority.** Derived: validate competitive outcomes and valuable rewards on the intended authority; treat client animation as presentation. Replaying a result message must not duplicate rewards. A low-stakes offline toy can accept local trust; a tradable economy needs stronger guarantees. [Nakama authoritative multiplayer](https://heroiclabs.com/docs/nakama/concepts/multiplayer/authoritative/).

**P99 — Save upgrades.** Derived: version persistent data and migrate a copy before replacing the last good file. Unsupported or malformed data should produce recovery options, not a fresh empty save. Engine serialization samples demonstrate mechanics; they do not provide a complete migration policy. [Godot saving guide](https://docs.godotengine.org/en/stable/tutorials/io/saving_games.html).

**P100 — Persistent object identity.** Derived: save stable content/object IDs and required state rather than assuming scene order remains fixed. Renaming a level or changing its hierarchy can invalidate naive saves. Keep settings, campaign state and purchased entitlements independently recoverable. [Godot saving guide](https://docs.godotengine.org/en/stable/tutorials/io/saving_games.html).

## Business: cases, conversion and sustainability

Historical figures are developer claims unless stated otherwise. Revenue, profit and a sustainable studio are separate outcomes.

### Cases: revenue, love and a viable studio are different

**The Room: scope matched skills and cash.** Fireproof's 2013 interview reports a sub-£80,000 development budget, largely six months' wages, more than $100,000 in the first featured week, and over two million paid sales by June 2013. The team had senior AAA art experience and financed development through outsourcing. One programmer and many artists favored a small, richly polished puzzle box. Apple featuring and simultaneous reviews helped launch; sales fell afterward, then continued. The lesson is a focused interaction and content scope matched to the actual team, not that a new solo developer should expect these returns. Costs and payback are interview claims with incomplete overhead/tax accounting. [Original developer interview, 2013-06-19](https://www.pocketgamer.biz/thinking-outside-the-box-the-making-of-the-room/).

**The Room: durable franchise, not mobile-only revenue evidence.** Fireproof currently calls itself independent, reports 21 developers and over 18 million series unit sales across 12 stores. Its later work includes VR and other platforms. This supports longevity and portable IP; it cannot isolate current Android/iOS income or profit. [Fireproof studio account, read 2026-11-08](https://www.fireproofgames.com/about).

**Crossy Road: optional monetization can earn substantial cash.** The founders' GDC 2015 deck reports 50 million downloads, six million peak DAU and $10 million in 90 days, with no paid user acquisition. It documents cosmetic characters, opt-in rewarded video, no energy gate, no interstitials, no paid save-me button and the same gameplay ability for every character. The initial six-week scope doubled to twelve. Their explanation emphasizes retention, sharing and re-engagement. These are self-reported outcomes from a breakout hit, not controlled proof that removing interstitials increases revenue or a modern CPI benchmark. [Founders' GDC slides, 2015, read PDF text](https://media.gdcvault.com/gdc2015/presentations/Hall_Matthew_Crossy_Road_Whale.pdf).

**Crossy Road's exact intent.** Andrew Sum said the team wanted a broad audience, simple understandable purchases and cosmetics that did not buy advantage; optional video produced over $1 million early revenue. This is developer testimony. Do not combine that launch snapshot with today's store behavior without reinspection. [Original interview, 2015-01-29](https://www.gamedeveloper.com/business/how-i-crossy-road-i-made-1-million-from-video-ads).

**Monument Valley 2: large revenue, exceptional distribution.** Reporting of ustwo's infographic gives $10.4 million revenue from June 5, 2017–June 4, 2018, $2.3 million development cost, 16 core developers and 70 weeks. It launched from Apple's WWDC stage after a beloved predecessor. China supplied 91.4% of unique installs and 62.3% of purchases; an initially free Android download there changes how installs should be interpreted. These figures establish neither profit nor a typical premium-game funnel. The original image failed direct access (403); this paragraph uses the readable contemporary transcription, not a claim of direct image inspection. [MacRumors, 2018-06-25](https://www.macrumors.com/2018/06/25/monument-valley-2-first-year-revenue/).

**The developer rejects treating its hit as normal.** Ustwo's own accompanying post calls Monument Valley exceptional and warns that it cannot forecast every project from those results. It also recalls Whale Trail struggling to break even; that 2D game is an adjacent studio-finance lesson, not a core 3D example. [Ustwo, 2018-06-25](https://ustwogames.co.uk/news/a-year-of-monument-valley-2/).

**Monument Valley's 2026 business warning.** At Develop Brighton, CEO Maria Sayans said Apple/Netflix deals had supported a profitable business but left it dependent on commissioned projects and platform funding. Their preferred games could not be made profitably on mobile at the studio's costs without those deals. The partners shifted toward longer-retained games; ustwo chose PC-first instead of becoming a F2P studio. This is evidence about this studio's costs and content, not proof premium mobile is impossible. Ustwo is building an audience outside individual releases through its Beautiful Games Club. [Reported talk, 2026-07-15](https://www.pocketgamer.biz/why-ustwo-games-shifted-from-mobile-to-pc-and-mind-boggling-discovery-problem/).

**Subscription delisting changes the product.** The directly read January 7, 2026 Mobilegamer interview says MV3’s Netflix departure required reworking its ending and content for premium distribution. Subscription deals had supplied stable income while separating ustwo from its audience and exposing it to partners’ changing strategies. Sayans did not reject F2P ethically: the team lacked skills, funding and risk appetite. Party games and free-to-start were possibilities, not guarantees at its production costs. Derived guidance: negotiate delisting notice, port/save rights and a funded standalone transition. [Original interview](https://mobilegamer.biz/ustwo-games-is-weaning-itself-off-apple-arcade-and-netflix-amid-strategy-shifts/).

## Measured conversion evidence, including disagreement

**Interstitials are a testable tradeoff, not a universal revenue failure.** Firebase's Pomelo/Once Upon a Tower case says a two-week A/B test produced 25% higher AdMob revenue, 35% more IAP and almost no retention change. Buying removed ads; the founder believed that motivated purchases. The source does not publish sample size, allocation, confidence intervals, exact ad cadence, cohort breakdown or long-term retention. This is a vendor case study of an adjacent stylized mobile game; do not present it as a 3D-specific causal law or copy its percentages into a forecast. [Firebase case study](https://firebase.google.com/case-studies/pomelo-games).

**Counterexample is valuable.** Crossy Road's deliberately unobtrusive design succeeded without interstitials; Pomelo says adding them improved revenue without detected retention loss. Different games, audiences, economies and measurement windows explain why both can be true. Test the intended placement at a natural break, keep a holdout, and track quits, next-session return, purchases, refunds and complaints alongside ad revenue. This recommendation is a research inference from the cases, not an experimentally proven optimal policy.

**Store tests measure acquisition, not fun.** Google Play's current experiment documentation supports graphics/text experiments, up to two variants, minimum detectable effect and configurable confidence; current target metrics are unique user install, open or pre-registration clicks. Older advice about retained first-time installers can now be stale. Test a real gameplay image versus an alternate composition and isolate locale/source; follow acquired cohorts into successful first play. [Current Play experiment guide](https://support.google.com/googleplay/android-developer/answer/12053285?hl=en).

**Small traffic limits inference.** Apple's current operational guide says a product-page test runs up to 90 days and results appear after five attributed first-time downloads; five is a display threshold, not adequate proof. A separate analytics page uses 90% confidence labels. Do not stop because an early point estimate looks favorable. Note that Apple's analytics page also suggests extending beyond 90 days “if possible,” which conflicts with the operational cap; use the run guide for setup and rerun if needed. [Run guide](https://developer.apple.com/help/app-store-connect/create-product-page-optimization-tests/run-a-test/), [analytics definitions](https://developer.apple.com/help/app-store-connect-analytics/acquisition/product-page-optimization/).

**No defensible universal D1/D7/CPI threshold.** The read case studies omit enough cohort, market, genre and attribution detail that they cannot supply a reliable benchmark for a new 3D game. Keep premium completion, arcade return frequency, multiplayer liquidity and F2P contribution separate. This is a boundary on the inference, not evidence that benchmarks do not exist. Genre-specific comparable cohorts or the project's own pilot are needed.

### Further experiments and current market context

**A test with an explicit retention cost.** ZiMAD's Dig Out! compared rewarded video + banners against those formats plus day-one interstitials. The vendor's Dec 10, 2019 case reports revenue +17%, ARPDAU +18%, D7 retention −2.5% and rewarded impressions −3%. It does not clarify whether the retention drop is relative or percentage points, nor disclose sample size, test length, statistical uncertainty or later LTV. The reported drop cannot be converted reliably to percentage points. This adjacent 2D game's monetization result is useful for methodology, not direct 3D guidance. A small retention loss can accompany higher immediate revenue; the decision needs future contribution and trust, not ARPDAU alone. [Unity/ironSource case](https://unity.com/resources/zimad-dig-out).

**Ad frequency matters within one format.** Cross Field began three-cohort app-open-ad tests in April 2022, using three casual games and observation windows of two weeks to two months. AdMob reports that frequency capping to half of eligible occasions balanced retention and revenue; later deployment across 18 apps yielded ARPU improvement over 30%, while app-open ads supplied 20% of ad revenue. The case describes a correlation between exposure and retention but omits exact cohort results, sample size and uncertainty. It is vendor-selected evidence, not a claim that app-open ads suit a premium adventure or interruption-sensitive game. [AdMob case](https://admob.google.com/home/resources/cross-field-boosts-arpu-30-after-adopting-app-open-ads/).

**Academic evidence read through an accessible publisher CDN.** Burns, Roseboom and Ross (AIIDE 2016) analyzed 99,620 users across 21 F2P mobile games and found no statistically significant association between first-session ad density and three retention measures after accounting for game effects. This was observational, not randomized; 81,868 users saw no first-session ad, ad formats were inconsistently instrumented, and no sampled game averaged over one ad/minute across user lifetimes. Game effects dominated. It cannot justify heavy ad spam, establish causation or represent 2026 3D games. One author worked at analytics vendor DeltaDNA. The paper supports testing actual implementations and resisting universal claims; it does not prove ads harmless. [Full paper, publisher CDN](https://cdn.aaai.org/ojs/12906/12906-52-16423-1-2-20201228.pdf).

**Current grossing context, explicitly outside small-indie ranking.** Sensor Tower's November 2026 report ranks October worldwide store consumer spending: Roblox first, followed by Honor of Kings, Gossip Harbor, Royal Match and Whiteout Survival. Its narrative describes anniversary/Halloween events and excludes third-party Android stores. This measures estimated spending on covered stores, not profit, all-platform receipts, ad revenue or an indie-success league. Roblox is a platform containing many creators, not one comparable small-studio game. The top chart shows the live-service competition for attention; it does not invalidate premium niches or prove events caused the ranks. Do not label these companies small indies because some once had small founding teams. [Sensor Tower original report, November 2026](https://develop.sensortower.com/blog/top-10-worldwide-mobile-games-by-revenue-and-downloads-in-october-2026).

**Limit of current rankings.** Public category charts do not identify a clean independent-studio, cross-platform-3D subset or disclose costs. A current “highest-profit indie 3D mobile game” ranking cannot be reconstructed honestly from these data. Historical developer disclosures remain the stronger scoped business cases; current mainstream ranking supplies competitive context only.

## Model fit and full economics: derived decision guidance

The following is accounting/design reasoning, not private financial data or measured price elasticity.

| Model | Fits | Principal burden | What validates it |
|---|---|---|---|
| Paid download | A complete premium puzzle/adventure with a clear trailer and recognizable value | Upfront purchase friction; discovery; support after sales decay | Qualified store visitors → paid purchases, refunds, net receipts; completed players recommending it |
| Free chapter plus permanent unlock | A tactile mechanic best understood by trying it | Additional entitlement/restore flow; free users cost support; stop boundary can frustrate | Tutorial/chapter completion → unlock, net receipts per install; clear paywall preview |
| Cosmetic F2P + rewarded ads | A repeatable skill loop with appealing identity/collection | Enough audience and return sessions; ad mediation/privacy/QA; cosmetic production | Incremental net revenue and retention in holdout tests; reward fraud and fill rate |
| Consumable/progression F2P | A game whose economy and ongoing service are part of its premise | Balance, content cadence, fraud, support, behavioral pressure, acquisition cash | Mature cohort contribution after UA, refunds and service costs, not launch ARPDAU |
| Platform subscription deal | A contract that funds a suitable complete or retained experience | Concentrated buyer risk, milestones, exclusivity, delisting and port rights | Cash and rights in signed contract; survival under nonrenewal scenario |
| Live multiplayer | Social play central to value | Servers, concurrency, moderation, abuse, matchmaking and operational coverage | Enough players per region/mode/time band; positive contribution at realistic concurrency |

**Budget the whole production.** Include salaries/contractors plus employer costs; design prototypes; 3D art, animation, rigging, audio and localization; tools/assets and licenses; Macs and Android/iOS device coverage; QA/accessibility; store media and trailer; legal/accounting; engine migration work; launch support; content updates; cloud saves/CDN/backend; moderation for social games; and a reserve for OS/store SDK changes. Keep sunk development separate from monthly survival costs.

**Calculate net contribution explicitly.** For one cohort: net store receipts + ad receipts − acquisition spend − variable backend/CDN/support/fraud costs. Allocate fixed costs separately to estimate operating profit. Refunds, taxes, currency conversions, publisher shares and payment timing affect cash. Do not subtract a store fee twice if using net receipts. Do not treat ad impressions as revenue before fill, valid impressions and eCPM are known.

**Illustrative premium arithmetic only.** At a hypothetical $5 pretax price and 15% fee, receipts before other costs are $4.25. A $100,000 project requires about 23,530 paid copies before refunds, overhead and maintenance. At 30%, $3.50 receipts require about 28,572 copies. These are sensitivity examples, not quoted regional fees or a viability forecast. Weighted geography and actual contractual fees should replace the assumptions.

**Support has a measurable production cost.** Hypothetical: 20 tickets per 1,000 players × 15 minutes each × $40 loaded hourly cost = $200 per 1,000 players, before tooling and escalation. Count founder time even when no salary is paid. Compare purchase/sync failures and device-specific crashes by ticket rate; a cheap game can incur expensive support. These inputs are illustrative, not a market benchmark.

**Compare production structures, not just winners.** The Room matched a constrained design to experienced artists and a small reported budget, then benefited from featuring. Ustwo later faced larger fixed costs and concentrated platform funding. Different eras, teams and distribution prevent a causal comparison; both show why production cost and buyer concentration belong beside sales totals.

**Paid acquisition requires payback cash.** A cohort may be profitable over months and still bankrupt a studio that pays for installs now. Forecast cumulative cash by cohort and stress low retention, weaker ad demand, delayed payments and a price promotion. Do not combine organic and paid users into one LTV if their behavior differs. Buying reach for an unproven loop accelerates loss.

**A 3D asset is recurring cost.** Every new character may need rig compatibility, animation transitions, camera/readability checks, low-tier memory/performance validation, store imagery and QA. A new biome multiplies lighting, shaders and streaming concerns. Estimate cost per shippable content unit, including testing, rather than mesh-production hours alone.

**Sales and local price points.** Test prices within the actual market and value promise. Regional affordability, tax-inclusive display, local payment access and different ad rates can invert a global-average business case. MV2's China distribution is evidence that installs and purchases vary by arrangement, not permission to assume the same partner/market access today. Do not infer a universal ideal price from historical winners.

**Ending is a valid outcome.** A finite premium puzzle's completion can mean delivered value; low D30 is not automatically failure. For endless F2P, return sessions are necessary for the model. Avoid adding daily obligations merely to make both dashboards look alike. Pair retention with the game's promise, repeat purchases/recommendations and complaints.

## Current platform fees and distribution, checked 2026-11-08

**Apple Small Business Program.** Enrolled eligible developers receive 15% on paid apps and IAP; eligibility aggregates associated developer accounts and uses proceeds, not sticker-price sales. Crossing the current-year $1 million threshold changes future sales to the standard rate. Regional alternative terms differ. This is not “every small app automatically pays 15%.” [Apple primary terms summary](https://developer.apple.com/app-store/small-business-program/).

**Google fees changed in 2026.** The official page separates rolled-out markets (EEA/UK/US from June 30; Australia/Japan from September 30) from remaining markets and distinguishes new/existing installs. In rolled-out markets, its first-$1M row is 10% service plus 5% billing. Standard auto-renewals are 10%+5%; other new installs 20%+5%; other existing installs 25%+5%, or 20% through external web links. Level Up/Apps Experience rates for those three columns are 10%+5%, 15%+5%, and 20%+5% (15% external links). The billing footnote covers Play Billing digital purchases and initial paid-app purchases. Remaining markets retain the enrolled first-$1M 15%/above-$1M 30% structure and 15% auto-renewal rate until rollout. Eligibility and transaction definitions matter. The original HTML table’s merged cells were inspected; do not turn this dated table into a global fee constant. [Official fees](https://support.google.com/googleplay/android-developer/answer/112622?hl=en).

**Store-featuring work has a concrete route.** Apple asks for at least two weeks' notice through Featuring Nominations and suggests up to three months for broader consideration. It evaluates controls, gameplay, art/animation, sound, performance and value, plus accessibility/localization and a compelling product page. These are selection considerations, not a guarantee or published ranking weights. Prepare a working representative build and honest assets; plan finances without a feature. [Apple featuring](https://developer.apple.com/app-store/getting-featured/).

**Google Level Up is optional.** The revamped program opened enrollment September 1, 2026. Its benefits require program-specific integration, achievements, cross-device and quality criteria. These are not universal requirements for every Play game. Evaluate the extra work and the actual fee benefit for the intended audience; child-focused games have specified exemptions. [Program guidelines](https://developer.android.com/games/guidelines).

**Google indie support is scoped.** The current program page describes a $2 million equity-free Indie Games Fund for selected Latin American studios and an Accelerator education/mentorship program. It does not establish an always-open global grant or guaranteed placement. Check specific cohort terms rather than budgeting assumed funds. [Google Indie Games](https://google.play/business/programs/indiegames/).

**Purchase trust.** Apple requires odds disclosure before purchases yielding randomized items; bought currencies cannot expire; restorable IAP need restoration. These rules address concrete failures: hidden odds, disappearing balances and paying twice after reinstall. They do not settle every jurisdiction's law. Keep paid randomness out of a small team's initial economy unless its product value justifies the extra policy, support and design burden. [App Review Guidelines §3.1.1](https://developer.apple.com/app-store/review/guidelines/).

## Continuity, failure and recovery

**Deus Ex GO is a historical service-loss case, currently restored.** VGC's November 23, 2022 report reproduces Onoma's announcement: removal December 1, access ending January 4, 2023, and no IAP refunds. This is evidence of the announced shutdown terms; it does not prove every previously installed/offline build stopped identically. [Contemporary report](https://www.videogameschronicle.com/news/four-square-enix-montreal-mobile-games-including-deus-ex-go-are-shutting-down/).

DECA's community manager announced the iOS/Android relaunch in April 2025; Pocket Gamer independently reported the return April 10, 2025. Current first-party listings show DECA as seller, iOS version 2.6.11 and an Android update dated October 7, 2026. [DECA announcement](https://www.reddit.com/r/Deusex/comments/1jr68jk/deus_ex_go_is_relaunching_under_deca_games/), [dated news](https://www.pocketgamer.com/deus-ex-go/back-on-ios-and-android/), [App Store](https://apps.apple.com/us/app/deus-ex-go/id1020481008), [Google Play](https://play.google.com/store/apps/details?id=com.squareenixmontreal.deusexgo).

Lesson (inference): premium payment does not secure continuity; plan local play, transferable saves and an explicit sunset path where feasible. Restoration is possible but depends on ownership and maintenance. Do not claim the revival restores every historical online event or achievement; no installed gameplay or old-purchase restoration test was performed.

### A practical strain test matrix

Use this as an acceptance plan for the chosen game, not a claim that tests were run here. The platform, memory, purchase and save sources above establish the failure mechanisms; the test combinations are engineering proposals.

| Scenario | Expected behavior | Consequence if missed |
|---|---|---|
| Lock, call or app switch during a jump/puzzle operation | Safe pause/suspend for offline play; explicit online continuation; no stuck input | Unfair death, missed action or corrupt state |
| Kill after reward commit but before acknowledgement | Exactly-once reward and retryable completion | Duplicate goods or paid value lost |
| Deny login, notifications, tracking or microphone | Explain only unavailable feature; preserve independent play | Optional features become launch blockers |
| Airplane mode after downloading a premium chapter | Owned local content works according to stated offline promise | Paying players lose access unexpectedly |
| Captive portal, Wi-Fi/cellular handoff, high loss | Bounded retry, clear state, reconnect/cancel | Permanent spinner or duplicate operation |
| Storage fills during save/update | Keep last good save/content; explain space needed | Blank profile or unlaunchable game |
| Two devices progress offline | Apply defined merge or informed choice; retain recovery copy | Silent regression, duplicated currency |
| New client followed by old client | Detect schema incompatibility without overwriting | Downgrade destroys progress |
| Long session, charging, battery saver | Sustainable frame delivery and readable reduced effects | Heat, battery drain, aiming latency |
| Repeated scene changes and cosmetics preview | Memory plateaus within budget | Late-session low-memory kill |
| Fold/rotate/window resize during drag | Stable touch ownership, layout and camera recalculation | Teleport, stuck joystick or hidden button |
| Controller disconnect while a modal is open | Touch/fallback input remains usable, focus restored | Player cannot dismiss or resume |
| Font scaling, long translation, RTL, CJK names | Readable wrapping/shaping and reachable controls | Broken shop price, invisible objective |
| Cloud service or ad network outage | Local game remains usable; reward offer unavailable honestly | Core gameplay held hostage by monetization |
| Refund, revoked entitlement, family approval | Reconcile state and explain next action | Support load, fraud or unfair lockout |
| New ad/analytics SDK release | Audit native binaries, manifests, data declarations and memory | Store rejection or regressions outside game code |
| Seasonal boundary, daylight-saving or device clock change | Server-authoritative event boundary where valuable; clear local display | Lost rewards or exploitable timers |
| Public level import/chat abuse | Validate size/content, rate limits, report/block and moderation | Crashes, harassment or unsafe content |

## Technology and compatibility

Primary documents checked 2026-11-08. No engine build, device benchmark or private SDK validation was performed. Recommendations are conditional.

### Consequential current findings

- **Store build requirements differ from install requirements.** Apple requires Xcode 26+ and iOS/iPadOS 26 SDK+ for uploads since 2026-04-28; deployment target iOS/iPadOS 13+ since 2026-09-09. This does not require every player to run iOS 26. [Apple requirements](https://developer.apple.com/news/upcoming-requirements/)
- Google Play new apps/updates must target API 36 since 2026-08-31; the extension ended November 1. Existing-app discoverability has an API 35 rule. `minSdkVersion` independently sets oldest installable Android. [Play target policy](https://support.google.com/googleplay/android-developer/answer/11926878?hl=en)
- **Do not repeat the old 16 KB deadline.** Current Android page-size documentation says updates lacking 16 KB support are blocked starting **2027-02-01**; all apps targeting Android 15+ must support it on 64-bit devices. Rebuild/check every native library, including ad, audio, physics and analytics SDK binaries. A compliant engine does not repair an incompatible third-party `.so`. Test on a 16 KB system. [Page sizes](https://developer.android.com/guide/practices/page-sizes)
- Play Billing 7's extension ended 2026-11-01. Billing 8 remains eligible until 2027-08-31, Billing 9 until 2028-08-31. Check the transitive version in the final Android artifact, including a Unity IAP wrapper. Existing installations continuing to work does not mean updates remain eligible. [Billing schedule](https://developer.android.com/google/play/billing/deprecation-faq)
- **Engine documentation can lag stores.** Epic's current UE 5.8 Android page recommends target SDK 35, NDK r27c, OpenJDK 21 and install API 26. Godot stable Android export instructions also name SDK 35. Unity 6.0 docs list API 35 among bundled tools. Those instructions do not override Play's API 36 submission requirement. Choose an engine patch/toolchain combination verified with a real Play upload; a documentation read cannot establish that exact combination. [Epic Android](https://dev.epicgames.com/documentation/en-us/unreal-engine/android-development-requirements-for-unreal-engine), [Godot export](https://docs.godotengine.org/en/stable/tutorials/export/exporting_for_android.html), [Unity 6.0 requirements](https://docs.unity3d.com/6000.0/Documentation/Manual/system-requirements.html)

## Compatibility: support means four separate promises

Specify **installable**, **feature-complete**, **adapted**, **tested** separately. A tablet installing a stretched phone game meets only the first. Practical strategies below are proposals, not measured prevalence:

- Contained premium puzzle: prioritize reliable older-device support, offline play, one curated quality tier plus inexpensive reductions. Godot Compatibility or a restrained Unity renderer can fit. Add screen sizes without creating expensive high-end effects.
- Action/ad-supported broad-reach game: budget a low-memory Android baseline early, adaptive quality and small install; test several GPU/vendor families. Cheap-device reach may matter more than a maximum graphics preset.
- High-end premium adventure: explicitly limit devices using measured requirements, offer stable frame-rate/quality modes and state storage requirements. A smaller audience can be coherent if pricing/distribution supports it. Never infer the profitable minimum hardware from another game's store listing.
- Live multiplayer: add backend protocol/version compatibility, reconnect and account linkage to device compatibility. Every supported client version is another operational burden.

| Axis | User-visible difference; work and fallback | Testing/support consequence |
|---|---|---|
| OS versus SDK | New build SDK does not force new runtime OS. Gate optional APIs; preserve core game on supported older OS. | Test oldest OS plus current release; validate submission separately. Apple/Play policy links above. |
| Engine version | Engine minima and native plugin ABI differ by release. | Pin editor, exporter, NDK/JDK/Xcode, packages; do a signed build before large production investment. |
| GPU/API | Vulkan, GLES and Metal features differ; shader compilation and vendor drivers can fail differently. | Test at least representative Adreno/Mali plus Apple devices; fallback rendering must preserve gameplay cues. [Godot renderer guidance](https://docs.godotengine.org/en/stable/tutorials/rendering/renderers.html) |
| RAM | Loading next scene while retaining old assets creates peak memory beyond steady-state use. | Test low-memory transitions and repeated scene loads; unload ownership explicitly. Memory Profiler below. |
| Thermal state | Cold-start FPS can collapse during a long session or charging. | Measure sustained runs, lower expensive effects/resolution before missing deadlines; use supported thermal signals. [ADPF](https://developer.android.com/games/optimize/adpf) |
| Refresh rate | Average FPS hides uneven presentation; 60/90/120Hz screens expose pacing mistakes. | Choose sustainable cadence, test frame-time distribution and touch latency. [Swappy](https://developer.android.com/games/sdk/frame-pacing) |
| Display shape | Phone notches, tablets and foldables change safe regions and camera framing. | Anchor HUD; set minimum readable size; define camera crop versus extra world visibility deliberately. Do not give competitive advantage accidentally. Derived design guidance. |
| Orientation/window changes | Rotation or fold/unfold can invalidate viewport and touch coordinates. | Preserve current run; recompute layout and camera; test mid-drag and during modal/store overlay. Derived acceptance tests. |
| Touch/controller | Controller presence, remapping and disconnect differ. | Menus and gameplay must both work; pause or show clear fallback after loss. [Apple Game Controller](https://developer.apple.com/documentation/gamecontroller), [Paddleboat](https://developer.android.com/games/sdk/game-controller) |
| Haptics/audio | Some tablets/controllers lack actuators; Bluetooth adds latency. | Treat vibration as supplementary; allow disable; do not use it as the sole cue. [Core Haptics](https://developer.apple.com/documentation/corehaptics), [Oboe](https://github.com/google/oboe) |
| Native libraries | 64-bit and 16 KB requirements apply to dependencies too. | Inspect final package and execute all SDK paths on relevant devices. Page-size source above. |
| Storage/download | Install success does not mean every asset is ready; updates can invalidate downloaded packs. | Keep tutorial/core playable, resumable download states and low-disk handling. Never assume cached pack path persists. [PAD](https://developer.android.com/guide/playcore/asset-delivery) |
| iOS asset API level | Background Assets exists from iOS 16; newer managed/hosted features have their own availability. | Keep bundled/self-managed fallback or raise support floor intentionally; verify engine bridge. [Background Assets](https://developer.apple.com/documentation/backgroundassets) |
| Store/services variant | Google Play services and billing do not exist on every Android distribution. | Isolate store adapter; avoid requiring a failed optional login to open an offline game. Cocos lists Huawei/native branches; each is separate release work. |
| Network quality | Cell handoff, packet loss, captive portals and IPv6-only networks disrupt realtime games differently from HTTP menus. | Simulate loss/jitter and reconnect; preserve local progress; authority design must survive replay. [Godot multiplayer](https://docs.godotengine.org/en/stable/tutorials/networking/high_level_multiplayer.html) |
| Save/protocol versions | A newer client may write data an older device cannot read. | Version saves; keep migration tests and backups; reject unsupported data without replacing it with blank state. [Godot save guide](https://docs.godotengine.org/en/stable/tutorials/io/saving_games.html) plus derived recovery policy. |
| AOT/stripping | Editor reflection success does not establish IL2CPP/native success. | Test serializers and SDK callbacks in release builds; preserve generated metadata where needed. MessagePack source below. |
| Secondary execution | iPhone-on-Mac, Android-on-PC and emulators have different input/performance expectations. | Deliberately support or exclude; simulator success cannot establish real GPU/thermal performance. Godot iOS simulator only supports Compatibility renderer. [iOS export](https://docs.godotengine.org/en/stable/tutorials/export/exporting_for_ios.html) |

## Engine choice

**Unity, C#, URP: practical candidate for a small commercial 3D mobile team needing substantial store SDK integration.** Editor, asset workflow, mobile packages and third-party integrations reduce bespoke plumbing. Costs: package/version coordination, managed allocations, IL2CPP/AOT surprises, vendor terms and potentially paid seats. Unity 6.0 documents Android API 23+, GLES3/Vulkan, iOS 13+/A8/Metal as engine minima; these are not credible performance promises for a particular game. Pin a supported patch plus package lockfile and build both platforms early. [Requirements](https://docs.unity3d.com/6000.0/Documentation/Manual/system-requirements.html), [released packages](https://docs.unity3d.com/6000.0/Documentation/Manual/pack-safe.html)

Unity Personal's 2026 revenue/funding threshold is $200,000; Pro is $2,310/year per seat prepaid yearly on the inspected page. A successful project can change eligibility before it has spare cash. The 2026 Havok changes matter to future engine upgrades. These are dated prices, not a quote or complete contract analysis. [Unity pricing](https://unity.com/products/pricing-updates)

**Godot, GDScript, Mobile or Compatibility renderer: good ownership-oriented candidate for contained stylized 3D.** Built-in scene tools, animation, navigation, UI and networking can cover much of an indie game without a package collection. Mobile targets newer GPUs; Compatibility offers wider reach with fewer effects. Renderer switching can change lighting/material output; treat both as separate tested presentations. Godot C# exports on Android/iOS remain explicitly experimental in current docs, despite being possible since 4.2. If C# is mandatory, first prove the complete device/export/plugin path. [Renderers](https://docs.godotengine.org/en/stable/tutorials/rendering/renderers.html), [iOS export](https://docs.godotengine.org/en/stable/tutorials/export/exporting_for_ios.html), [features](https://docs.godotengine.org/en/stable/about/list_of_features.html)

**Unreal, C++/Blueprints, mobile rendering path: good for teams already fluent in Unreal or demanding 3D authoring.** Strong tooling does not make desktop effects or materials cheap on phones. Start the project with mobile constraints; budget content cooking, shader permutations, native SDK bridges and heavier iteration. Source access helps specialists but does not remove the maintenance burden. Standard game terms charge 5% of lifetime gross product revenue above $1 million; exclusions/programs require separate contract review. Do not confuse the game royalty model with non-game seat licensing. [Epic license](https://www.unrealengine.com/license), [Android support](https://dev.epicgames.com/documentation/en-us/unreal-engine/android-development-requirements-for-unreal-engine)

**Cocos Creator 3.8 LTS:** TypeScript-oriented alternative with native Android/iOS output, 3D assets, physics and regional distribution documentation. Worth considering when the team's existing tooling or target distribution favors Cocos. Verify specific native plugins and 3D rendering budget; a long platform list is not proof of equivalent polish. [Cocos manual](https://docs.cocos.com/creator/3.8/manual/en/)

**Defold:** Lua-oriented lightweight alternative with 3D model support; consider deliberately constrained scenes and custom rendering work. Its Defold License derives from Apache 2.0 but has its own terms; do not label it MIT or plain Apache. Compare the actual 3D production workflow against Unity/Godot rather than rejecting it as “2D only.” [Models](https://defold.com/manuals/model/), [license](https://defold.com/license/)

**Owned C++ engine:** SDL + bgfx plus selected physics/navigation libraries can make sense when engine control itself is strategic and the team has shipped such tooling. Otherwise authoring, asset conversion, UI accessibility, store bridges and debugging become a second product. `bgfx` is explicitly a bring-your-own-engine rendering library, not a complete mobile game engine. Its current README lists iOS 16+ support, illustrating how dependencies can raise minimum OS independently of Metal itself. [SDL](https://github.com/libsdl-org/SDL), [bgfx](https://github.com/bkaradzic/bgfx)

### Rendering, UI and asset-license changes

**Unity rendering direction changed.** Unity's 2026 strategy marks Built-In RP deprecated starting 6.5, recommends URP for new work, and promises Built-In availability in 6.7 LTS with support at least through end 2028. No removal date selected. HDRP maintenance continues; feature investment moves toward URP. This adds an avoid-for-new-work case, not a demand to port a stable shipped game immediately. [Unity strategy](https://unity.com/topics/render-pipelines-strategy-for-2026)

**Do not repeat old UI Toolkit limitations.** The inspected comparison page, reached through a 6000.0 URL, labels its comparison tables **Unity 6.6**. It lists world-space rendering and custom materials/shaders for both UI Toolkit and uGUI. It still recommends uGUI generally for runtime and specifically for 3D-world UI/custom effects; UI Toolkit suits substantial multi-resolution menus/HUDs. It lists Animation Clips/Timeline integration for uGUI and not UI Toolkit; data binding/global styles/advanced layout for UI Toolkit. Treat the mixed URL/table versions as a reason to check the project's exact editor documentation before selecting. [Comparison](https://docs.unity3d.com/6000.0/Documentation/Manual/UI-system-compare.html)

**Text shaping has real resource and feature costs.** Unity's Advanced Text Generator uses HarfBuzz, ICU and FreeType; it supports RTL shaping but only dynamic font assets. Current docs list unsupported rich-text/spacing features and a 4.8 MB ICU data footprint. Do not assume a translated string plus an atlas makes Arabic or bidirectional input work. Test the actual font, mixed-script punctuation, cursor movement, emoji and labels in release builds. [Advanced Text Generator](https://docs.unity3d.com/6000.0/Documentation/Manual/UIE-advanced-text-generator.html)

**Quaternius is no longer a safe blanket CC0 shorthand.** Current owner's license page is **QAL v1.0**, updated 2026-08-28: free personal/commercial use and no required credit, but standalone asset redistribution/resale prohibited. Preserve the license included with each downloaded pack; don't infer that a new site license rewrites a previously acquired CC0 grant. [Current license](https://quaternius.com/license.html)

## Named ecosystem catalog

Fit notes are engineering judgment informed by the linked owner material. “Official” means vendor-maintained/documented, not universal adoption. Except named status changes below, repository inspection establishes a usable documented project, not a promise of future maintenance. Pin versions and verify release artifacts. Engine packages have engine/package terms; cloud tools additionally have service/privacy/usage terms. Prefer built-in functionality until a specific gap justifies a dependency.

### Engine, simulation and gameplay

| # | Tool | Fit, alternative and material limit |
|---|---|---|
| 1 | [Unity](https://docs.unity3d.com/6000.0/Documentation/Manual/system-requirements.html) | C#/editor ecosystem; strong commercial integration candidate. Compare Godot ownership and Unreal authoring. Paid eligibility above. |
| 2 | [Godot](https://docs.godotengine.org/en/stable/about/list_of_features.html) | Integrated GDScript/scene workflow; small-team stylized games. C# mobile remains experimental. |
| 3 | [Unreal Engine](https://dev.epicgames.com/documentation/en-us/unreal-engine/android-development-requirements-for-unreal-engine) | C++/Blueprints; use mobile-specific rendering and measured device floor. Royalty terms above. |
| 4 | [Cocos Creator](https://docs.cocos.com/creator/3.8/manual/en/) | TypeScript/native 3D; relevant regional platform integrations. Check each chosen plugin. |
| 5 | [Defold](https://defold.com/manuals/model/) | Lua/lightweight constrained 3D; custom workflow tradeoff. Custom Defold License. |
| 6 | [SDL](https://github.com/libsdl-org/SDL) | zlib-licensed platform/input/audio substrate for owned engine; not a level editor. |
| 7 | [bgfx](https://github.com/bkaradzic/bgfx) | BSD-2-Clause cross-API rendering; supplies no game architecture. Current Apple floor can narrow reach. |
| 8 | [Jolt Physics](https://github.com/jrouwe/JoltPhysics) | Native multicore rigid-body simulation; owner names Horizon Forbidden West/Death Stranding 2 usage. Mobile performance still needs own scene tests. Prefer engine integration when available. |
| 9 | [Recast/Detour](https://github.com/recastnavigation/recastnavigation) | Native navmesh construction/pathfinding; suitable owned engine. Engine navigation wrapper often enough. Dynamic tiled worlds increase complexity. |
| 10 | [Flecs](https://github.com/SanderMertens/flecs) | MIT C/C++ ECS with relationships and queries; simulation-heavy custom engine. Millions-of-entities claims are owner benchmarks, not mobile budget. |
| 11 | [EnTT](https://github.com/skypjack/entt) | Header-only modern C++ ECS; owner identifies Minecraft usage. Alternative to Flecs, not an extra mandatory layer. |
| 12 | [Unity AI Navigation](https://docs.unity3d.com/Packages/com.unity.ai.navigation@2.0/manual/index.html) | Navmesh agents, obstacles, links; simpler than adding external pathfinding when requirements fit. Runtime rebakes need CPU budget. |
| 13 | [Burst](https://docs.unity3d.com/Packages/com.unity.burst@1.8/manual/index.html) | Compiles compatible C# subset to optimized native code; useful measured CPU hot paths, not arbitrary managed code. |
| 14 | [Unity Collections](https://docs.unity3d.com/6000.0/Documentation/Manual/pack-safe.html) | Native containers supporting job/data workflows; explicit lifetime cost. Avoid adding solely because ECS is fashionable. |
| 15 | [Unity Entities](https://docs.unity3d.com/6000.0/Documentation/Manual/pack-safe.html) | Data-oriented simulation option; scene/component approach often simpler for small counts. Adds authoring/debugging conventions. |
| 16 | [Unity Mathematics](https://docs.unity3d.com/6000.0/Documentation/Manual/pack-safe.html) | Math types for Burst-oriented work; ordinary engine vectors sufficient elsewhere. |

### Presentation, UI and assets

| # | Tool | Fit, alternative and material limit |
|---|---|---|
| 17 | [Unity Input System](https://docs.unity3d.com/Packages/com.unity.inputsystem@1.14/manual/index.html) | Input actions across touch/device/gesture; intended replacement for classic Input Manager. Test rebinding and simultaneous input. |
| 18 | [Cinemachine](https://docs.unity3d.com/Packages/com.unity.cinemachine@3.1/manual/index.html) | Camera tracking/composition/blends. Reduces bespoke camera math; cannot choose comfortable mobile camera behavior for you. |
| 19 | [Timeline](https://docs.unity3d.com/Packages/com.unity.timeline@1.8/manual/index.html) | Authored gameplay/cutscene/audio sequences. Define skip and resume semantics separately. |
| 20 | [Animation Rigging](https://docs.unity3d.com/Packages/com.unity.animation.rigging@1.3/manual/index.html) | IK/aim and procedural constraints; useful character interaction, costly when multiplied without profiling. |
| 21 | [uGUI](https://docs.unity3d.com/Packages/com.unity.ugui@2.0/manual/index.html) | GameObject/Canvas UI integrated with scene animation. Measure batching/rebuilds; platform accessibility requires explicit work. |
| 22 | [Unity Localization](https://docs.unity3d.com/Packages/com.unity.localization@1.5/manual/index.html) | String/asset locales, plurals and pseudo-localization; preferable to scattered translated literals. Font/layout QA remains. |
| 23 | [DOTween](https://github.com/Demigiant/dotween) | Unity C# tweens for UI/object motion. Alternative to authored animation for simple transitions; cancel on scene teardown and honor reduced motion. Check license separately from paid Pro. |
| 24 | [Addressables](https://docs.unity3d.com/Packages/com.unity.addressables@2.7/manual/index.html) | Asset location/dependency loading above AssetBundles; useful growing content catalog. Release handles; remote content requires version/rollback design. |
| 25 | [glTF](https://github.com/KhronosGroup/glTF) | Standard runtime asset exchange; verify extension/importer support rather than assuming every material transfers. |
| 26 | [meshoptimizer / gltfpack](https://github.com/zeux/meshoptimizer) | MIT mesh simplification/cache/compression and glTF optimization; asset-pipeline tool. Inspect visual error and importer extension support. |
| 27 | [KTX-Software](https://github.com/KhronosGroup/KTX-Software) | Khronos texture tools/lib with Basis transcoding; useful custom delivery. Engine texture importer may already cover the need. |
| 28 | [astcenc](https://github.com/ARM-software/astc-encoder) | Apache-2.0 ASTC encoding with quality/time tradeoffs; use in automated asset processing, test UI/normal-map artifacts. |
| 29 | [FMOD](https://www.fmod.com/licensing) | Authored adaptive audio/middleware; built-in mixer enough for simple games. Free indie requires both <$200k yearly revenue and <$600k budget; project registration/logo terms. |
| 30 | [Oboe](https://github.com/google/oboe) | Native Android low-latency audio wrapper with API-specific workarounds. Useful custom audio engine; no need to duplicate engine integration. |
| 31 | [Godot AnimationTree/AnimationPlayer](https://docs.godotengine.org/en/stable/about/list_of_features.html) | Built-in animation workflow; start here before external animation framework. Keep transitions testable. |
| 32 | [Godot Control/theme UI](https://docs.godotengine.org/en/stable/about/list_of_features.html) | Built-in game menus and themes; keeps stack small. Native purchase/accessibility integration is separate. |

### Async, storage and services

| # | Tool | Fit, alternative and material limit |
|---|---|---|
| 33 | [UniTask](https://github.com/Cysharp/UniTask) | MIT Unity PlayerLoop async/await; lower-allocation async operations. Cancellation/lifetime still owned by game. Native engine awaiters/coroutines may suffice. |
| 34 | [R3](https://github.com/Cysharp/R3) | MIT reactive library with Unity/Godot support; successor direction to UniRx. Use when event composition earns learning cost; direct events simpler otherwise. |
| 35 | [VContainer](https://github.com/hadashiA/VContainer) | Unity DI/scoped composition; alternative to manual constructors/wiring. Owner performance claims need own profile; avoid invisible lifetime ownership. |
| 36 | [MessagePack-CSharp](https://github.com/MessagePack-CSharp/MessagePack-CSharp) | Binary serialization with Unity/AOT support; useful network/save size. Requires schema/version discipline and release-build testing; JSON easier to inspect. |
| 37 | [Godot FileAccess/JSON/ConfigFile](https://docs.godotengine.org/en/stable/tutorials/io/saving_games.html) | Built-in save/config primitives. Small games need no database by default; add atomic replacement, migration and recovery yourself. |
| 38 | [Godot high-level multiplayer/ENet](https://docs.godotengine.org/en/stable/tutorials/networking/high_level_multiplayer.html) | Scene-oriented RPC/replication; backend/authority/security remain game work. HTTP sufficient for scores or asynchronous turns. |
| 39 | [Mirror](https://github.com/MirrorNetworking/Mirror) | MIT Unity networking, self-hostable, owner cites shipped games. Strong alternative when owning infrastructure; not free server operations. |
| 40 | [Photon Fusion](https://doc.photonengine.com/pun/current/getting-started/get-help) | Vendor-recommended successor for new PUN-style projects; evaluate topology/CCU/service terms. This source establishes recommendation, not measured superiority. |
| 41 | [Photon Quantum](https://doc.photonengine.com/pun/current/getting-started/get-help) | Vendor's other new-project option; evaluate deterministic model fit before choosing. Not a drop-in PUN upgrade. |
| 42 | [Nakama](https://github.com/heroiclabs/nakama) | Apache-2.0 backend: accounts, storage, social, leaderboards, multiplayer, validation. Hosted or self-operated; don't deploy all features for offline puzzle. |
| 43 | [Unity Multiplayer Services SDK](https://docs.unity.cn/Packages/com.unity.services.multiplayer%402.1/changelog/CHANGELOG.html) | Consolidated multiplayer integration. Hosting deprecation does not mean Lobby/Relay disappeared. Pin service/package compatibility. |
| 44 | [Unity Matchmaker](https://discussions.unity.com/t/unity-matchmaker-third-party-hosting-support-is-now-generally-available/1706478/1) | Official third-party-hosting support announced Jan 29 2026. Needs allocation bridge and operational testing. |
| 45 | [Unity Cloud Save](https://docs.unity3d.com/6000.0/Documentation/Manual/pack-safe.html) | Documented service package for cloud state; conflict/identity/offline policy still yours. Alternative own backend or platform-only save. |
| 46 | [Unity Authentication](https://docs.unity3d.com/6000.0/Documentation/Manual/pack-safe.html) | Service identity integration; don't confuse anonymous identity with recoverable account. |
| 47 | [Unity IAP](https://docs.unity3d.com/Packages/com.unity.purchasing@5.0/manual/index.html) | Cross-store purchase integration; inspect underlying Billing version and native restore/refund behavior. Wrapper does not establish entitlement authority. |
| 48 | [Firebase Unity SDK](https://github.com/firebase/quickstart-unity) | Owner provides iOS/Android samples. Select only required modules; service terms/data collection/native dependencies matter. |

### Native platform bridges and delivery

| # | Tool | Fit, alternative and material limit |
|---|---|---|
| 49 | [StoreKit](https://developer.apple.com/documentation/storekit) | Apple purchases, signed transactions and reviews; native bridge or engine wrapper. Product policy varies by storefront/program. |
| 50 | [Google Play Billing](https://developer.android.com/google/play/billing/deprecation-faq) | Android Play purchases; enforce current library eligibility. Must test pending/replayed purchase callbacks. |
| 51 | [GameKit](https://developer.apple.com/documentation/gamekit) | Apple Game Center achievements, social/multiplayer; not Android cross-play backend. |
| 52 | [Play Games Services v2](https://developer.android.com/games/pgs/deprecation) | Current PGS migration destination. Authentication/session integration remains platform-specific. |
| 53 | [Game Controller](https://developer.apple.com/documentation/gamecontroller) | Apple physical/virtual controller profiles and remapping; use correct user-mapped glyphs. |
| 54 | [Paddleboat](https://developer.android.com/games/sdk/game-controller) | Android controller mappings, connect/disconnect, extended features; C++/Gradle library. Engine may already expose enough. |
| 55 | [Core Haptics](https://developer.apple.com/documentation/corehaptics) | Apple patterned tactile/audio feedback; capability checks and nonhaptic equivalents required. |
| 56 | [Background Assets](https://developer.apple.com/documentation/backgroundassets) | Apple managed asset downloads and optional hosting; native extension/export integration, newer-feature availability gates. |
| 57 | [Play Asset Delivery](https://developer.android.com/guide/playcore/asset-delivery) | Play-hosted install/fast-follow/on-demand packs, format targeting; does not serve other Android stores. |
| 58 | [Google Play Unity plugins](https://github.com/google/play-unity-plugins) | Separate maintained plugin repos for delivery, integrity, reviews/updates. Avoid old monorepo releases; owner says they fail target34. |
| 59 | [EDM4U](https://github.com/googlesamples/unity-jar-resolver) | Resolves Android/iOS native dependencies in Unity. Helps SDK integration; must review resolved conflicts and generated native project. |
| 60 | [Metal](https://developer.apple.com/documentation/metal) | Apple GPU API, usually engine-owned. Direct shader/rendering work only when needed; not Android portability layer. |
| 61 | [ADPF](https://developer.android.com/games/optimize/adpf) | Thermal/performance feedback for Android; vary workload sustainably. Device capability varies. |
| 62 | [Unity Adaptive Performance](https://docs.unity3d.com/Packages/com.unity.adaptiveperformance@5.1/manual/index.html) | Engine abstraction around power/thermal providers; verify provider/device support. Does not choose quality policy automatically. |
| 63 | [Swappy](https://developer.android.com/games/sdk/frame-pacing) | Android OpenGL/Vulkan presentation pacing. Check engine's built-in use before integrating another copy. |

### Diagnostics, testing and release

| # | Tool | Fit, alternative and material limit |
|---|---|---|
| 64 | [Unity Memory Profiler](https://docs.unity3d.com/Packages/com.unity.memoryprofiler@1.1/manual/index.html) | Heap/native snapshots, leak/peak analysis. Capture device transitions, not just editor idle. |
| 65 | [Unity Test Framework](https://docs.unity3d.com/Packages/com.unity.test-framework@1.4/manual/index.html) | NUnit-based Edit/Play/device tests; use saves, purchase state machine and level invariants. Cannot prove touch feel. |
| 66 | [GUT](https://github.com/bitwes/Gut) | Godot GDScript test framework; explicit Godot-version compatibility matrix. Pin corresponding version. |
| 67 | [GameCI Unity Builder](https://github.com/game-ci/unity-builder) | MIT GitHub build action; Unity licensing/signing/Mac final build remain. Alternative engine's own CI service. |
| 68 | [GameCI Test Runner](https://github.com/game-ci/unity-test-runner) | MIT CI test action; complements physical-device acceptance. |
| 69 | [Sentry Unity](https://github.com/getsentry/sentry-unity) | Crash/performance SDK; tested Unity 2020.3+ per owner, service/data costs. Symbol uploads and privacy controls required. |
| 70 | [MetricKit](https://developer.apple.com/documentation/metrickit) | Apple real-device metrics/diagnostics; daily metrics are not realtime alerting. Complements engine profiler. |
| 71 | [Godot demo projects](https://github.com/godotengine/godot-demo-projects) | Official examples and regression starting points; select matching version branch. Demo working is not complete product architecture. |
| 72 | [Unity Android Logcat](https://docs.unity3d.com/6000.0/Documentation/Manual/pack-safe.html) | Device log access in editor; redact user/private data. Alternative adb/logcat directly. |

### Rendering, text, asset production and release

| # | Tool/resource | Fit, alternatives, maintenance/license evidence and integration cost |
|---|---|---|
| 73 | [Universal Render Pipeline](https://docs.unity.com/en-us/engine/6000.5/manual/render-pipelines/universal-render-pipeline) | Official Unity cross-platform renderer, explicitly includes mobile. Sensible new Unity 3D baseline; still budget lights, transparencies, shadows and post effects. Stock URP versus a small custom renderer feature is a measured choice, not permission to recreate HDRP. |
| 74 | [UI Toolkit](https://docs.unity3d.com/6000.0/Documentation/Manual/UI-system-compare.html) | Official document/style-oriented UI; useful complex menus and adaptive layouts. Compare uGUI authoring/animation workflow. Current capability claims must match editor version; see correction above. |
| 75 | [TextMeshPro](https://docs.unity3d.com/Packages/com.unity.textmeshpro@3.0/manual/index.html) | Official mesh/Canvas text replacement with font assets and rich text. Import required TMP resources; validate atlas coverage, fallback and size. TMP3.0.6 guide read; don't infer latest-editor packaging from that historical package number. |
| 76 | [Unity Advanced Text Generator](https://docs.unity3d.com/6000.0/Documentation/Manual/UIE-advanced-text-generator.html) | Official Unicode/shaping option for UI Toolkit. Useful RTL/complex scripts; dynamic fonts and documented unsupported styling are concrete limits. Compare existing text path using the exact target locales. |
| 77 | [Blender](https://www.blender.org/about/license/) | Modeling, rigging, animation, baking and export starting point for an independent 3D pipeline. GPL software does not force created artwork/.blend files to become GPL; owner explicitly permits commercial artwork. Add-ons and imported assets keep their own terms. |
| 78 | [Maya / Maya Indie](https://blogs.autodesk.com/media-and-entertainment/2026/10/26/autodesk-maya-vs-maya-creative-vs-maya-indie-which-one-is-best-for-you/) | Mature character/rig/animation production alternative when artists already know it. Indie provides full toolset, but country, creative revenue, project value and work-for-hire restrictions apply. Owner's Oct26 2026 US example: <$100k creative revenue, no project>$100k, one license/user or organization. Verify local terms. |
| 79 | [Substance 3D Painter](https://experienceleague.adobe.com/en/docs/substance-3d-painter/using/home) | Commercial 3D mesh painting/baked texture export. Useful authored PBR surfaces; Blender/Material Maker can cover simpler work. Docs updated Oct23 2026. Export the correct normal-map convention/channel layout for engine; baking quality doesn't prove mobile material cost. |
| 80 | [Material Maker](https://github.com/RodZill4/material-maker) | MIT Godot-based procedural texture and 3D model painting tool. Alternative to paid procedural tools when its nodes/export fit. Maintainer distinguishes stable downloads from use-at-own-risk master builds; pin a release. |
| 81 | [Krita](https://krita.org/en/about/license/) | Hand-painted textures, icons and concept art. GPLv3 tool; owner states art remains yours and commercial use allowed. Complements 3D authoring rather than replacing UV/rigging. |
| 82 | [Mixamo](https://helpx.adobe.com/creative-cloud/faq/mixamo-faq.html) | Adobe auto-rigging/motion library; free Adobe ID, royalty-free commercial game use per still-published 2021 FAQ. Bipedal humanoids only; unusual appendages/proportions fail. Save results locally: service keeps only last character. Exported motion still needs retarget/foot-contact/root-motion review. |
| 83 | [Houdini Indie / Engine Indie](https://www.sidefx.com/faq/indie-new/) | Procedural asset generation earns cost when many variations/rebuilds recur. Owner limits organizations to revenue<$100k and funding<$1m in trailing 24 months, up to 3 Indie and 3 Engine Indie seats; full commercial required beyond eligibility. Unneeded for a few handmade puzzle levels. |
| 84 | [TexturePacker](https://www.codeandweb.com/texturepacker) | Commercial atlas tool for HUD/effects/sprite components within 3D games. Current page offers 8.3.0 and engine exporters. Engine-native atlasing may suffice; check packing rotation, trimming, padding and importer conventions. Tool license and input-image license are separate. |
| 85 | [Android GPU Inspector](https://developer.android.com/agi/start) | Official Android frame/system capture. Debuggable builds and Vulkan validation setup apply. Current docs recommend APA for system profiling; retain AGI where frame inspection fits. Don't call entire AGI removed/dead. |
| 86 | [Android Performance Analyzer](https://developer.android.com/android-performance-analyzer) | New official recommended system profiler; inspected Nov6 page offers beta 0.9.0 and canary 0.10.0. Uses Perfetto-derived system context; choose stable workflow after proving device support. [May 19 launch article](https://android-developers.googleblog.com/2026/05/introducing-android-performance-analyzer.html) recommends Android 12+ for best system/GPU capture. |
| 87 | [Perfetto](https://perfetto.dev/docs/) | Open-source Android scheduling/CPU/memory/ANR trace analysis and local timeline/SQL tools. Good for stalls caused outside engine markers. Owner says specialized game GPU work is better served by game-oriented tools; complements APA/AGI instead of replacing GPU debugging. |
| 88 | [Xcode Instruments Game Performance](https://developer.apple.com/documentation/xcode/analyzing-the-performance-of-your-metal-app) | Official Apple frame-time/system/thermal/CPU/GPU trace. Find long frames and correlated work over time. Capture representative gameplay on devices; optional counters must be enabled. Engine profiler alone misses system effects. |
| 89 | [Xcode Metal debugger](https://developer.apple.com/documentation/xcode/metal-debugger) | Official GPU trace, render-pass dependencies, resources, shader debugging/counters. Use for visual artifacts and expensive passes; Instruments explains longer temporal patterns. Apple/Mac toolchain required. |
| 90 | [fastlane](https://docs.fastlane.tools/) | MIT release/signing/screenshots automation for iOS/Android. Owner recommends Bundler/Gemfile.lock and managed Ruby; macOS fully supported, other hosts partially. Does not replace engine build, store review or physical-device verification. |
| 91 | [Kenney](https://kenney.nl/support) | CC0 asset-page packs, commercial use/no attribution required; good prototypes and coherent simple style. Preserve per-pack file; owner provides no engine-import support. Logos excluded from optional attribution use. |
| 92 | [Poly Haven](https://polyhaven.com/license) | CC0 HDRIs/textures/models; useful lighting and realistic material references. High-resolution source assets need mobile reductions. Website text/example renders/API access have separate terms; asset CC0 doesn't license scraping entire site. |
| 93 | [ambientCG](https://docs.ambientcg.com/license/) | CC0 materials/models; owner also covers material preview renders. Useful repeatable PBR library, reduce channels/resolution and avoid visually inconsistent surfaces. No attribution required. |
| 94 | [Quaternius](https://quaternius.com/license.html) | Coherent stylized 3D assets/animations. Current QAL permits commercial projects, bars redistribution as raw asset products. Do not blanket-label new downloads CC0; see dated correction. |
| 95 | [Fab](https://www.fab.com/eula) | Commercial marketplace; Standard-license summary permits compatible tools beyond Unreal and collaboration within project, prohibits standalone asset resale. Some listings use CC-BY instead. Inspect listing/receipt/license and shader/rig portability; “available on Fab” proves no mobile optimization. |

### Audio, type and icons

| # | Tool/resource | Fit and constraint |
|---|---|---|
| 96 | [Wwise](https://www.audiokinetic.com/en/wwise/pricing/) | Conditional middleware candidate; current owner pricing inaccessible, so no free-tier assumption. |
| 97 | [Google Fonts](https://github.com/google/fonts) | Redistributable type families with per-family licenses and language metadata. Bundle chosen fonts for offline use; test glyph coverage, atlas memory and small-size readability. |
| 98 | [Material Symbols](https://github.com/google/material-design-icons) | Apache-2.0 neutral settings/navigation icons; useful across both platforms. Current Symbols replace the no-longer-updated classic Material Icons set. Avoid mixing unrelated weights/styles. |
| 99 | [Game-icons.net](https://game-icons.net/about.html) | Game-specific monochrome symbols under CC BY 3.0 with author attribution. Useful action/item vocabulary; simplify dense artwork at phone sizes and test comprehension. |

### Audio middleware

**FMOD** suits layered music, routing and designer-authored audio when the engine mixer is insufficient. The owner’s current indie production-budget threshold is below $600,000; free indie additionally requires developer revenue below $200,000/year. Otherwise the listed indie fee is $2,000 per game. Project registration and logo terms apply; all platforms/features are included in that category. Check eligibility before relying on the free tier. [FMOD licensing](https://www.fmod.com/licensing).

**Wwise** remains a conditional audio-authoring/runtime candidate. Its current pricing could not be verified: current, legacy and regional owner URLs plus direct HTTPS returned 403/inaccessible responses. Third-party pricing claims cannot establish a current project entitlement. Obtain the applicable license before selection; this access limit says nothing about product quality. Compare the engine mixer and verified FMOD terms. [Owner pricing](https://www.audiokinetic.com/en/wwise/pricing/).

## Named avoid/migrate guidance

| Choice/status checked 2026-11-08 | Exact reason and action | Exceptions |
|---|---|---|
| Unity HDRP for this target | Official HDRP17 platform list excludes Android/iOS; renderer assets are not interchangeable. Start URP/mobile-compatible path. [Requirements](https://docs.unity3d.com/Packages/com.unity.render-pipelines.high-definition@17.0/manual/System-Requirements.html) | HDRP remains legitimate desktop/console choice; unsupported hacks are a separate maintenance commitment. |
| Godot Forward+ as blanket phone baseline | Godot recommends it for desktop; Mobile/Compatibility fit phone tiers. [Renderers](https://docs.godotengine.org/en/stable/tutorials/rendering/renderers.html) | Controlled high-end experiment may work; own benchmark required. Not deprecated. |
| Godot C# mobile as risk-free default | Current export docs explicitly experimental. Prove device plugins/AOT before committing; GDScript alternative. [iOS](https://docs.godotengine.org/en/stable/tutorials/export/exporting_for_ios.html) | Existing tested games may continue; no universal “unshippable” claim. |
| UniRx for new work | Archived 2024-02-16; consider R3/direct events. [Owner](https://github.com/neuecc/UniRx) | Stable existing use can stay while migration cost exceeds benefit; R3 is not API-identical. |
| Photon PUN2 for new feature-heavy work | Maintenance/LTS since 2023; owner recommends Fusion/Quantum for new projects. [Owner](https://doc.photonengine.com/pun/current/getting-started/get-help) | Existing projects continue; no immediate forced rewrite. |
| Standalone Godot Jolt extension by habit | Built into Godot 4.4; extension now maintenance-only. Prefer built-in when it meets needs. [Owner](https://github.com/godot-jolt/godot-jolt) | README records joint-feature differences; verify before migration. |
| Unity Multiplay hosting | Deprecated Apr 1 2026; new servers/allocations stopped, except prearranged migration customers. Choose hosting separately. [Status](https://status.unity.com/info_notices/362941) | Do not generalize to Unity Relay/Lobby/Matchmaker. |
| Play Games Services v1 | Deprecated; v25 removes v1 APIs; new titles cannot use v1. Migrate v2. Owner page contradicts itself on May versus June 2027 shutdown; plan before earliest date, recheck rather than assert exact day. [Schedule](https://developer.android.com/games/pgs/deprecation) | Existing binary may still work now; dependency updates can break compilation sooner. |
| Play Billing7 or older for new update | Final extension ended Nov 1 2026; use supported8/9 via compatible SDK. [Schedule](https://developer.android.com/google/play/billing/deprecation-faq) | Old installed versions continuing to function doesn't grant upload eligibility. |
| Old play-unity-plugins monorepo downloads | Owner says old releases do not work at target34; use each plugin's current repo. [README](https://github.com/google/play-unity-plugins) | Historical reference only; do not install from a stale tutorial. |
| Sentry Unity Lite for new work | Current Sentry README calls lite deprecated; current SDK supports Unity 2020.3+. [Owner](https://github.com/getsentry/sentry-unity) | Legacy engines may still use lite with server compatibility; plan upgrade separately. |
| Havok Physics for Unity as future-proof bundled entitlement | No longer included starting Unity 6.3; support remains for 2022  LTS/6.0 LTS remainder. [Pricing notice](https://unity.com/products/pricing-updates) | Existing supported branch differs from new-project selection; assess physics migration. |
| Unity classic Input Manager for new complex input | New Input System explicitly replaces it and supports richer device/action model. [Input docs](https://docs.unity3d.com/Packages/com.unity.inputsystem@1.14/manual/index.html) | Old simple projects need no automatic rewrite; don't run duplicate input handling accidentally. |

**Additional avoid-for-new-work cases:** Unity deprecated Built-In RP in 6.5 and recommends URP; existing support continues through 6.7 LTS, at least through end 2028, with no removal date selected. Stale blanket claims about UI Toolkit’s missing world-space/custom-material support also need replacement: the current comparison lists them, but label/version mismatches require checking the chosen editor. AGI’s system-profiling role is being superseded by APA; AGI is not wholly retired. See the owning-source checks above and catalog.

## Practical 3D asset workflow

These are derived implementation recommendations, not measured universal thresholds. Start with one fully representative level/character and prove the pipeline on each target before buying a large asset library.

1. **Keep editable source and deterministic exports.** Version `.blend`/Maya/source textures plus export settings; generated FBX/glTF and platform textures should be rebuildable. Each import must preserve agreed units, axes, pivot, scale and animation names. A game that looks right only after undocumented editor fixes is expensive to update.
2. **Prove materials at the boundary.** Blender and a game's renderer don't share arbitrary shader graphs. Bake unsupported procedural surfaces; inspect normal direction, tangent seams, roughness/metal packing, transparency, emissive behavior and color space. glTF is an interchange agreement, not a promise every engine renders every extension identically. [Khronos glTF](https://github.com/KhronosGroup/glTF), [Substance export documentation](https://experienceleague.adobe.com/en/docs/substance-3d-painter/using/home)
3. **Budget the resulting asset, not its authoring screenshot.** Count exported vertices, materials, texture residency and skinned bones; examine lower mip levels and LOD transitions on a phone. Many tiny materials and transparent layers can cost more than the triangle count suggests. Use meshoptimizer/astcenc and the chosen renderer's profiler; preserve hero silhouette/readability.
4. **Treat purchased animation as raw material.** Retarget, confirm locomotion/root-motion conventions, contact timing, loops, interrupts and low-frame-rate behavior. Mixamo's humanoid scope saves setup but does not supply gameplay state design. [Mixamo](https://helpx.adobe.com/creative-cloud/faq/mixamo-faq.html)
5. **Keep a license manifest per asset.** Record origin, exact version/license, purchase receipt, attribution and whether raw redistribution is allowed. Store assets in private production repos when terms require; an open-source code release must not accidentally publish restricted source meshes/fonts/audio. Compare CC0 libraries with QAL/Fab restrictions above.
6. **Separate audio authoring from runtime reliability.** Small games can use the engine mixer and carefully edited clips; dynamic layered music/dialogue may justify middleware. Test voice-count limits, ducking, looping, Bluetooth/headphone changes and interruption recovery on real devices. Middleware doesn't choose those policies.

### Architecture lessons from accessible book text

Robert Nystrom’s *Game Programming Patterns* is useful for mechanisms, not current mobile SDK choices. The directly read [Game Loop](https://gameprogrammingpatterns.com/game-loop.html) chapter separates simulation time from rendering and explains why variable steps can destabilize physics. Derived mobile guidance: keep gameplay speed independent of 30/60/120 Hz rendering, bound catch-up work, and handle resume explicitly. A fixed step alone does not guarantee deterministic cross-platform physics.

The [State](https://gameprogrammingpatterns.com/state.html) chapter replaces contradictory flags with explicit states and transitions. For a mobile game, model playing, paused, backgrounded, reconnecting and presenting a store transaction explicitly; define who owns input and audio in each. Use a small enum or state machine before adding a general framework. This is a design application, not the book’s mobile prescription.

The [Object Pool](https://gameprogrammingpatterns.com/object-pool.html) chapter explains reuse and its costs: wasted capacity, exhaustion, stale fields and retained references. Pool measured hot allocations such as repeated effects; reset them fully and define overflow behavior. Do not pool every domain object or hide memory growth behind a large reserve. The historical discussion of mobile memory managers is not a current Unity/Godot benchmark.

## Prioritized build guidance

These priorities synthesize the cases and mechanisms above. They are proposals for a new game, not confirmed scaffold defaults.

1. **Prove one enjoyable touch loop.** Build a greybox on both platforms. Test grip, depth judgment, camera turns, failure and instant retry on a phone that represents the lower intended tier. A desktop demo or cinematic trailer cannot answer those questions.
2. **Choose the production shape.** Decide fixed-camera puzzle, constrained arcade, creative toy or free-camera action before selecting a rendering showcase. Estimate shippable level/character cost, including art, audio, localization and device QA. The Room’s focused team fit is a better lesson than copying its revenue.
3. **Select the engine through a complete slice.** Build signed iOS/Android artifacts, one production-like scene, a save migration, the chosen input paths and one real store integration if needed. Check current upload rules and native SDK dependencies. Compare measured iteration and maintenance costs; avoid an unsupported “fastest engine” claim.
4. **Make progress trustworthy.** Implement durable local state, explicit pause/background handling, checkpoint recovery and purchase reconciliation before adding content volume. Add cloud sync only with defined conflict and identity semantics.
5. **Set art and performance budgets together.** Pick a coherent visual direction and test it warm, at the busiest view and during transitions. Preserve gameplay signals when reducing effects. A fixed-camera miniature can spend detail where the camera will see it; a roamable world needs broader coverage.
6. **Build the needed menu system.** Include text scaling, reachable controls, input-complete dialogs and settings previews. Use the 100 practical details selectively. Do not add every screen or service because another genre uses it.
7. **Validate the business promise.** Test the paid/free boundary, understandable purchases and honest store media. Measure the actual funnel and contribution. With low traffic, interviews and observed play can identify confusion sooner than an underpowered A/B test.
8. **Expand only after recovery and content throughput work.** New modes, multiplayer, daily events and UGC each create permanent service or testing obligations. Before adding one, identify its player value, expected cost and exit plan.
9. **Prepare discovery and launch operations.** Build an audience channel, localized store assets, review materials and editorial nominations. Stage releases, monitor device-specific failures and preserve a known-good build/content set. Do not budget guaranteed featuring.
10. **Fund the tail.** Reserve time for store/engine changes, support, accessibility fixes and save compatibility after launch revenue declines. For server/subscription products, define notice, migration and shutdown behavior while contracts and code can still accommodate it.

**Expected basics:** clear touch interaction, readable scenes, reliable progress, predictable interruptions, honest purchases, stable performance on declared devices and working platform navigation. **Useful differentiators:** a distinctive central verb, authored visual identity, expressive creation/sharing, thoughtful assists, satisfying endings and unusually good return/recovery behavior. **Costly traps:** free-camera scope without control testing, an MMO-style service for a tiny audience, endless content before proving production throughput, unsupported native SDKs, monetization that depends on confusion, and a second custom engine project hidden inside a game schedule.

**Ideas to test, not defaults:** direct object manipulation versus virtual controls; fixed versus player-controlled camera; playable demo versus paid download; short authored campaign versus replay objectives; cosmetics versus new mechanics; quiet optional ads versus higher-frequency placements; one quality preset versus battery/performance modes. Define the audience, metric, guardrails and stopping rule for each. Do not use one game's uplift as the expected result.

## Sources and reading guide

Citations sit beside claims; this guide locates the main evidence groups without repeating the findings.

- **Platform requirements and engineering:** [current findings](#consequential-current-findings), [compatibility](#compatibility-support-means-four-separate-promises), and the [catalog](#named-ecosystem-catalog) link to owning documentation and repositories. Requirements and prices were checked on the report date; pinned versions and release artifacts still need project-specific verification.
- **Player experience:** [game profiles](#exemplary-games-strengths-and-weaknesses) combine publisher material with independent reviews. [Practical details](#specific-screens-and-components-100-practical-details) connect guidelines, support failures and critiques to concrete choices. Dated individual reports establish possible failure modes, not prevalence.
- **Visuals and motion:** [inspected images](#inspected-visual-evidence) link to exact publisher screenshots; [recorded motion](#recorded-motion-inspection) identifies the trailer and sampled intervals. [Design references](#design-reference-sources) separate shipped examples, production assets and implementation resources.
- **Business:** [developer cases](#cases-revenue-love-and-a-viable-studio-are-different), [experiments](#measured-conversion-evidence-including-disagreement), and [fees](#current-platform-fees-and-distribution-checked-2026-11-08) retain dates, metrics and limitations. Repeated reporting of the same disclosure is one evidence source. Model calculations are illustrative, not forecasts.
- **Architecture:** [book lessons](#architecture-lessons-from-accessible-book-text) use directly read chapters. [Build priorities](#prioritized-build-guidance) synthesize the report; they are proposed engineering choices, not measured universal rules.

Source review included full pages, repository documentation, PDF text, accessible book chapters, a WWDC transcript, published images and sampled trailer frames. Where direct access failed, the affected paragraph identifies the fallback and limits. Public evidence cannot establish private profitability, current defect rates or a tested engine/device combination; those conclusions require project data and execution.
