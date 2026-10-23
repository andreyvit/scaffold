# Engineering values

Apply these values to concrete needs. Preserve the reason for a choice and the condition that would change it. Existing project decisions take precedence unless the user asks to change them.

## Product and people
- Serve a real user or business outcome. Include how the product reaches users, delivers value and sustains itself.
- Understand actual users: their expectations, attention and likely reactions. Make workflows and wording convenient and unsurprising; do not depend on an error message being read.
- Supply smart defaults, especially where people will not spend attention choosing. A product-specific choice can still deserve a recommendation.
- Value developer/tester convenience. Fast feedback and easy inspection can justify product capability.

## Code and tools
- Keep future effort proportional to the change. Make correctness understandable locally; state, ownership and failure explicit.
- Make abstractions earn their cost. Build and own by default; accept dependencies for concrete benefits such as specialist knowledge, ongoing upkeep or lower total cost.
- Value simplicity, elegance and low churn. At comparable cost, spend the thought to avoid a worse design, even in a small detail. Concrete costs can justify compromise.
- Understand runtime, memory, build and operating costs. Neither fashionable tooling nor a universal ban on tooling substitutes for judgment.
- Fit architecture and process to the team and risk. Package boundaries must earn their cost; avoid speculative features and automatic library extraction.

## Evidence and operation
- Keep the running system inspectable and security evident in its design.
- Prove real behavior and make failures recoverable. Use the [testing](testing.md) and [development harness](development-harness.md) defaults.
- Aim for no data loss and seconds of downtime hidden from users. Establish the failure scenarios and budgets per product; the initial snapshot-backup design does not guarantee zero loss.
- Determine business measurement needs, then use the most private implementation that meets them. Prioritizing privacy above required metrics is an explicit product choice; see [analytics](analytics.md).
- Keep production recovery operator-directed until serious scenario testing earns automation; see [deployment](go-deployment.md).

Native mobile uses each platform's native APIs and UI, accepting duplicated implementation. Current mobile internals are a separate design task; [iOS layering](ios-layering.md) records only the settled organization.

These are confirmed values, not a permanent ranking for every conflict. Ask about a concrete unresolved cost or risk; derive routine engineering consequences yourself. Keep internal foundations, optional capabilities and authorized product UI distinct.

Source: [V1–V16 and qualifications](../../../research/scaffold/70-values.md), [C1–7, C20, C65](../../../research/scaffold/78-confirmed-decisions.md). The two later research candidates are not approved values.
