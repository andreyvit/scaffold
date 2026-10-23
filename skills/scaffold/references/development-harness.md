# AI development harness

Build good AI harness support from day one. Treat development/testing convenience as architecture, not later polish.

- Run multiple isolated app instances without shared mutable test state or resource collisions.
- Use the same fixture definitions for interactive development and integration tests.
- Capture outgoing email so tests and agents can inspect messages and complete real flows.
- Expose database contents, logs and metrics in forms easy to inspect and query.
- For web apps, support browser access to running instances and exercise real user flows.

Let agents act as a chosen fixture user without completing login in development/testing. Also provide a mode that exercises real signup/login for authentication tests. Keep the shortcut and harness state/controls confined to development/testing. In isolated AI development, stop the app on unexpected failures by default so agents cannot overlook them. Keep normal request/job recovery available when testing failure handling. Expected validation/application errors still follow normal handling.

Verify isolation, fixture loading, email capture and observable state through a working end-to-end flow. Use the [testing policy](testing.md).
