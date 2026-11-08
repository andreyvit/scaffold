---
name: research-how-to-build-great-apps
description: Research what makes great, successful indie apps for a user-specified platform and app category. Use for exhaustive research on app quality, UX, business and technology choices; deliver a practical scaffold playbook.
---

Research what constitutes a great app within the user's scope and turn the findings into a practical playbook for planning, building and reviewing that kind of product. Write max-terse, plain English; preserve detail.

## Scope and duration

This is exhaustive, multi-hour or even multi-day research. Set up a goal. Run as long as you need to cover everything. Do not stop until every gap and weak evidence is either filled conclusively, or you can explain why it is unsolvable. OK to run out of rate limits; user will resume after limits reset.

- Establish platform, app category and any specified niches, locales, audiences or constraints. Ask only for missing scope; one question at a time.
- For an app part, feature or component, apply all sections below only where relevant. Cover the requested scope thoroughly; omit unrelated areas such as full business economics when they do not apply. Briefly explain exclusions in the playbook's scope.
- Inspect related existing playbooks and recipes before research. Expand a matching playbook instead of creating a duplicate. For a subset of a recipe or a component shared by several recipes, focus on what is unique to the request. Cross-link shared guidance in those recipes and highlight differences in requirements, behavior and tradeoffs; avoid repeating their full coverage.
- Goal: cover all relevant research areas below and deliver one finished playbook.
- Save findings and exact next steps often. Resume saved work; do not restart the survey.
- Track coverage, sources read, open questions and next steps in a working section of the playbook. Update the playbook as you go. Treat each known gap as further work. Continue until every question is resolved or you can explain why it cannot be resolved. Before delivery, remove working notes; explain unobtainable knowledge beside affected claims. Mark goal complete only after this check, coverage and playbook review.
- Use short-lived data gathering subagents to save context and speed up research.

## Meanings of great

Research all relevant meanings:

- User love: emotional appeal.
- Problem solving: rational value to users.
- Downloads and retention: audience-building value to owner.
- Cash earned: short-term value to owner.
- Stable, viable business: long-term value to owner.
- Simple, maintainable code: development speed and user-facing stability.
- Being featured: what platform owners and industry publications are looking for.

## Research app quality

Search broadly; follow useful references in depth. Cover official sources and third-party books, UI catalogs/libraries, magazines, blog posts, podcasts and videos:

- Official guidelines as starting points. They may be basic or lag current practice; examine where excellent apps go further.
- Opinions on good and bad apps, with reasons and concrete behaviors.
- In-depth app reviews, especially by people who value quality apps, UX and UI. Capture each app's strengths and weaknesses.
- Indie developer blogs, especially building-in-public accounts.
- Catalogs of good and bad patterns.
- Design sites and mockups. Distinguish sleek appearance from evidence of pleasant daily use.
- Top indie apps in relevant app stores.
- Technical approaches indie developers prefer or avoid, and why. Verify technical claims against current primary sources.
- Failed, stalled and shut-down apps; why users switch, cancel or feel abandoned. Compare winners with failures; examine timing, distribution and existing audiences before crediting product choices.
- Edge cases, uncommon scenarios and good platform citizenship, including use under strain. Research expected behavior for relevant platform features and user settings: accessibility, keyboard/input methods, locales, time zones, multiple windows/displays, permissions, app lifecycle and system integrations. Include slow networks, offline work, large datasets, low resources, interruptions, data loss and recovery. Derive further cases from platform/category evidence; these examples are not exhaustive. Seek long-term use reports; reviews and mockups can miss these problems.

Read sources beyond search snippets. Use accessible book text, podcast/video transcripts and relevant visuals; distinguish direct inspection from another source's summary. If evidence is inaccessible, seek alternative access or independent sources; do not stop at recording a gap.

## Specific screens, components and small details

Build a substantial practical reference, grouped by screen/task and component, with good and bad choices together. For a broad mature platform, seek roughly 100 distinct useful details; do not pad, repeat generic principles or force a quota onto a narrow category. One short paragraph per detail: expected appearance/behavior, tempting mistake, reason, applicable exceptions, source/example. Cover common pieces such as home/list/detail, settings, onboarding, navigation/Back, search, selection, forms, dialogs/sheets, menus, notifications, feedback, loading/empty/error states, purchases and account/data management. Derive further groups from evidence.

Research the details experienced platform users notice: label/control alignment, density, grouping, ordering, defaults, immediate versus explicit save, control semantics, keyboard/focus, dismissal, navigation history, contextual/hidden commands, gestures, transition continuity and accessibility. Establish what each platform actually expects; examples from another platform are prompts, not transferable rules.

Seek complaints, expert critiques, issue discussions, redesign comparisons and long-term reviews, beyond official guidance. Extract the specific bad decision and proposed better behavior; verify technical claims. Separate broad convention, vendor recommendation, category exception, individual preference and disputed practice. Record relevant version/date. Do not turn one angry comment into consensus. Show how evidence guides building each common piece of a new app, not merely how to audit platform citizenship.

## Visual design directions and resources

Research how excellent current apps look and feel, beyond compliance with the platform's official system. Identify distinct live design sensibilities with actual examples: typography, spacing/density, color, surfaces, shapes, icons, illustration, content hierarchy, controls and motion. Describe the coherent choices that make each direction work, where it fits, costs/risks, and what would undermine it. Separate platform-wide shifts from niche styles, historical movements and speculative concepts. Do not invent five trends if evidence supports fewer; do not blend incompatible styles into one prescribed average.

Read independent designer/veteran critiques and inspect real screens, component states and motion where accessible. Explain what was directly inspected versus described by a source. A screenshot supports appearance, not interaction quality; a changelog supports shipped intent, not measured delight. Seek distinctive, highly polished apps as well as well-executed stock components. Explain disagreements over brand character, platform fidelity, density and playfulness.

Provide useful places to continue designing: curated app/flow catalogs, independent design writing, design-system references, icon/type resources, component/motion examples and source projects. Assess recency, platform specificity, access limits, licensing and implementation fit where relevant. Distinguish shipped apps from mockups; do not give a link dump or treat popularity as quality. The reader should be able to choose a strong coherent visual direction before drawing screens.

## Compatibility and supported targets

Give compatibility its own in-depth section. Explain the available support range and what supporting each target actually entails: OS/API versions, hardware/resource tiers, screen/window sizes, input devices, device categories, vendor behavior, services/distribution variants and relevant cross-device execution. Separate install compatibility, supported features, adapted UX and tested reliability.

For each consequential axis, describe differences users experience, APIs/layout/input/dependency/distribution work required, graceful degradation, testing/support cost, common inclusion/exclusion choices and evidence behind them. Explain minimum versus target/build versions or platform equivalents; distinguish store deadlines from runtime requirements. Include representative support strategies for small teams, supported by real apps where possible. Never infer prevalence from a few examples or recommend universal device coverage. Show how audience, geography, economics and the core feature change the choice; verify dates and current requirements.

## Technology ecosystem: named tools, libraries and components

Go below framework names. Research the practical stack: language/compiler, build/dependency/package tools, compatibility libraries, UI/component collections, navigation/state, storage/migrations, concurrency/background work, networking/serialization, images/media, maps/charts/editors, animation/icons, purchases, diagnostics, testing and release tooling where relevant. Cover both platform libraries and independent open-source choices. Service-specific SDKs are secondary unless their integration itself creates a consequential choice.

Provide a broad grouped catalog of widely used or otherwise important named libraries/components. Seek breadth comparable to a top-100 ecosystem survey when warranted, without padding or claiming every app needs them. For each, identify purpose, fit, alternatives, maintenance/maturity, license or service constraints when material, platform/stack limits and adoption evidence. Distinguish measured usage, public dependent projects, prominent examples, stars and personal recommendations; do not call a library universal or popular without support. Explain when the platform already supplies enough.

Add a separate named-tools/libraries-to-avoid section: deprecated, archived, superseded, fragile, unsuitable or costly choices, with exact reason/date, affected use cases, replacement and legitimate exceptions. Verify status in owning repositories/docs. Distinguish “avoid for new work,” “migrate existing use,” “only unsuitable for this task” and “still viable.” Include compatibility/build-tool interactions, migration burden and component integration costs. Do not equate old release dates, dislike, or GitHub stars with abandonment or quality.

## Research commercial success separately

Across similar sources, investigate top-grossing and financially successful indie apps:

- UX choices measured to help or hurt conversion. Record metric, result, study context and limits; distinguish experiments from correlation and opinion.
- What makes apps popular.
- What helps or hurts sales.
- Full business economics: pricing, trials, refunds, acquisition costs, platform fees, infrastructure bills and support workload. Examine profit and developer sustainability; high revenue alone proves neither.

For each, preserve differences by niche, locale, category and audience. Do not generalize a result beyond supporting evidence. Separate downloads, retention, revenue, profit and business viability; label estimates and developer claims.

## Evidence

- Link claims to sources. Record dates and relevant app/platform versions; separate historical lessons from current behavior.
- Preserve disagreements, exceptions and weak evidence. Distinguish user reports, reviewer judgments, developer claims, measurements and research inferences.
- Seek independent support for consequential conclusions. Do not count repeated coverage of one claim as independent evidence.
- Cover every requested area. Pursue missing evidence and contradictions through targeted searches, alternative sources and methods. Failed searches alone do not prove a question unresolvable; neither do time spent or rate limits.
- For each unresolvable question, explain beside the affected claim what you tried, what prevents resolution and how that limits the conclusion. Never invent certainty or deliver a separate unresolved-gaps list.

## Deliver one playbook

Default destination: `skills/scaffold/references/playbook-<topic>.md` in the scaffold repository, resolved as `../scaffold/references/` from this skill's directory. Honor an explicit user destination. Use a short, lowercase, hyphenated topic matching existing names, such as `playbook-macos-apps.md` or `playbook-mobile-api-sdks.md`. Keep dates in the content, not filenames. Title the playbook for its platform, category and other user criteria.

Write a practical guide, not a research diary: explain what to build, how it should behave, which choices fit, what to avoid and why. Preserve the full depth and evidence required below. Playbooks guide product quality; recipes specify confirmed implementation defaults. Recommendations do not override project decisions or promote themselves into recipe requirements.

For scaffold playbooks, add or update the link in the [scaffold skill's playbook index](../scaffold/SKILL.md#playbooks). Cross-link related playbooks and recipes with relative links; verify links after writing or moving files. Keep interview history and working state in their existing locations. Creating or updating a playbook does not authorize committing or pushing.

Cover the relevant sections below, applying the scope rules above:

1. Scope; what makes these apps different from other platforms, categories and audiences.
2. Great UX and behaviors, with concrete examples and reasons.
3. Poor UX and behaviors, with concrete examples and reasons.
4. Greatest indie apps: strengths, weaknesses and which meanings of great each satisfies.
5. What helps conversions and business, with context and measured results where available.
6. What hurts conversions and business, with the same detail.
7. Good technology stacks: fit, tradeoffs and developers' reasons.
8. Technology choices to avoid: failure modes, reasons and exceptions.
9. Prioritized build guidance: expected basics, useful differentiators, costly traps and ideas to test. Tie recommendations to evidence; state when each applies and what to build first.
10. Specific screens and components: substantial grouped reference of small good/bad details and platform conventions.
11. Visual design directions: distinct current sensibilities, examples, motion and practical design resources.
12. Compatibility: supported-target choices, concrete differences, implementation/testing costs and typical strategies.
13. Common libraries and components: grouped named ecosystem, fit, alternatives and adoption/maintenance evidence.
14. Named technologies/libraries to avoid: verified status, failure modes, replacements and exceptions.
15. Sources.

Keep the playbook readable: order these sections to suit the material, cross-link overlapping findings and preserve existing valid research when expanding a playbook.

Include lessons from failures, edge cases, uncommon scenarios, platform citizenship, use under strain and full business economics in relevant sections. For each relevant scenario, state expected behavior and consequences of mishandling it. Keep findings specific to researched scope.

Keep citations near claims. Give enough detail to guide app decisions; avoid generic design advice and unsupported rankings.
