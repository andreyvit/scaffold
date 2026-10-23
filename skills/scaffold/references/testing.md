# Testing

Use HappiGrid's default:

- Unit-test substantial algorithmic code: parsing, transformations, data structures and similar logic.
- Make most other tests whole-app integration tests.
- Cover every feature and its real-life use scenarios.
- Aim for near-100% coverage; exceptions are edge cases genuinely impractical to test.

Purpose: make changes and refactoring safe. Coverage and scenario completeness complement each other; neither replaces checking real behavior.

Provide the [AI development harness](development-harness.md) from day one; share fixtures with integration tests.
