# Library boundaries and extraction

## Confirmed · C69 · 2026-10-23
Default to building inside the project, as a separate package or unit.

For entirely domain-independent, reusable, non-project-specific code, Andrey prefers separation because it keeps the boundary and scope crystal clear. A templating language is his example. Separation is an explicit decision each time, not an automatic consequence of noticing reusable code.

Normal extraction path: prove the code in production, let the API stabilize over a few months of usage, then offer extraction. **Each extraction requires explicit user authorization.** Reuse potential or an assistant's stability assessment does not supply that authorization.

The standalone preference and project-local default are complementary: clear generic scope makes separation desirable; project use establishes whether the boundary/API works before normal extraction. No fixed month count or universal prohibition on explicitly chosen standalone work is inferred.

[Recipe](../../skills/scaffold/references/library-boundaries.md).

## API compatibility · confirmed C70 · 2026-10-23
Compatibility depends on who uses the library. The decision must be vetted by the user. Do not prescribe either coordinated breaking changes or backward compatibility as a universal winner, including for libraries presumed to be shared only across owned applications.

Identify actual consumers and explain the proposed compatibility impact for user review. This is guidance for making the decision concrete, not a new requirement for approval of every internal implementation change.
