---
name: scaffold
description: Use Andrey Tarantsov's opinionated templates and specs to start a new feature or a whole new project with the right pragmatic design.
---

Use when requested or when the project already uses Andrey Tarantsov's scaffolds. Existing project decisions override these defaults unless the user requests a change.

## How to apply
1. Read [values](references/values.md). For a whole Go/server/web app, use [the assembled recipe](references/app-web.md).
2. Read the subsystem recipes relevant to the task, including linked rules the implementation depends on. Research links supply reasons and evidence; do not recursively load the research archive.
3. Distinguish required foundations, optional capabilities and product UI. Recommend contextual defaults; ask only about real unresolved tradeoffs. Derive routine implementation consequences and verify feasibility yourself.
4. Implement and verify actual behavior using the [testing](references/testing.md) and [development harness](references/development-harness.md) defaults.
5. Preserve project decisions and reasons. Do not turn a candidate tool, historical source or deferred question into an approved default.

These files are design recipes, not a claim that a starter app or every framework described here is implemented.

## Recipe index

| Area | Recipes |
|---|---|
| Whole app and structure | [Go/server/web](references/app-web.md), [Go layering](references/go-layering.md), [library boundaries](references/library-boundaries.md) |
| State and ownership | [Changes/undo/history](references/changes.md), [accounts/workspaces](references/accounts.md), [optional offline sync](references/offline-sync.md) |
| Access | [Login](references/login.md), [permissions](references/permissions.md), [customer-data access audit](references/customer-data-access.md) |
| Web | [Rendering](references/web-rendering.md), [frontend tooling](references/frontend-tooling.md), [APIs](references/apis.md) |
| Business and integrations | [Analytics/experiments](references/analytics.md), [session replay](references/session-replay.md), [jobs](references/jobs.md), [email](references/email.md), [payments](references/payments.md), [uploads](references/uploads.md) |
| Data lifecycle | [Export/deletion](references/data-rights.md), [deleted-data recovery](references/deleted-data.md), [migrations](references/migrations.md) |
| Development | [Testing](references/testing.md), [AI harness](references/development-harness.md), [error handling](references/error-handling.md) |
| Operation | [Configuration](references/app-config.md), [environments](references/app-environments.md), [deployment](references/go-deployment.md), [backups](references/backups.md), [optional standby](references/standby.md), [observability](references/observability.md) |
| Native mobile | [iOS layering](references/ios-layering.md); native UI is settled, modern internals remain separate work |

## Deferred work
Observability/anomaly details await Andrey's experiments. Component-capable templating is a separate strategic project. Staff/customer identity separation awaits reflection. Refine detailed changes/operations machinery through implementation. Modern Apple internals need later research; Android implementation recipes remain to be developed.

Do not reopen these as a generic interview queue. For research/interview work, resume from [STATE](../../research/scaffold/STATE.md#resume-here); [the review overview](../../research/scaffold/104-interview-overview.md) records current scope.
