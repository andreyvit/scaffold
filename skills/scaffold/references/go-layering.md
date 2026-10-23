# Go layering

Organize by layer, following HappiGrid's guide. Layers express responsibilities and dependency direction. Experience favors keeping similar code together over grouping an entire feature across responsibilities.

Within each layer, prefer feature packages. Avoid one huge package with tangled internal dependencies. Keep inter-feature code together when useful circular references justify it: persistent models and model utilities can often stay separate, while interconnected in-memory representations may belong in one package. Do not distort useful models merely to force feature separation.

## Layers, low to high

| Packages | Responsibility |
|---|---|
| `utils/`, `utils/*/` | Generic helpers, algorithms and data structures; no domain concepts. Unprefixed: suitable for extraction into libraries. |
| `model/m*/` | Domain/synthetic types, helpers and simple algorithms. No persistence mechanics, logging, localization or configuration; persistence struct tags allowed. `mcom` holds shared IDs, enums and simple domain types. |
| `apps/` | `App` and `Ctx` interfaces, configuration and related contracts; expose shared concerns to layers above model/utils. |
| `db/`, `db/db*/`, `db/txns/` | Loading/saving mechanics and generic changes; no business decisions. |
| `shared/sh*/` | Logging, metrics and other shared mechanics on top of `apps`. Implementation-only peers live in `appimpl/*impl` to limit rebuilding. |
| `core/core*/` | Business logic, especially shared by handlers; domain-specific changes. |
| `handlers/h*/` | HTTP handlers; limited handler-specific business logic. |
| `activities/c*/` | Long-running controllers and activities. |
| `appimpl/`, `appimpl/*impl` | App/Ctx implementations, shared services and application wiring. |
| `apptesting/`, `apptesting/*testing/` | Integration-test infrastructure exercising the whole app. |

## Rules

- Dependencies go down layers, never up.
- Limit peer-package dependencies; designate shared packages such as `mcom`. Core packages may use one another more freely. Useful mutually referring types can share a package; this does not permit cyclic package imports.
- Prefixes identify layers and allow one feature to span them: `maccounts`, `coreaccounts`, `haccounts`, `accountstesting`.
- Separate algorithms, business decisions, integration mechanics and wiring. Tiny mixtures are fine; split when substantial. Extract business logic from a handler as integration mechanics grow.
- Handlers never call other handlers. Move shared functions/constants to core.
- `App` is shared wiring across requests/goroutines. `Ctx` belongs to one request/goroutine; do not share it concurrently.
- Substantial runtime code takes `ctx apps.Ctx` first. It implements `context.Context` and `edb.Txish`; model and utility code remain independent of runtime services.

Refine exact placement of new change/operation machinery through implementation experience; preserve these boundaries.
