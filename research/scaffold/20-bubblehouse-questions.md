# Before Bubblehouse

Happy Grid settled some preferences. Test their limits in Andrey’s code before 2025-06-01.

1. Does a monolith stay modular as the product grows? What gets extracted, and why?
2. Which state belongs in memory, in durable storage, or in a queue?
3. How are auth, tenant boundaries and public error messages enforced consistently?
4. What does a failed external call leave behind: logs, metrics, retry state, operator actions?
5. What makes a performance optimization worth its complexity?
6. How do tests represent business scenarios without hiding the app behind mocks?
7. What differs across browser, iOS and Android: shared rules, native interaction, caching, offline behavior?

Look for counterexamples. Infer values only from Andrey’s attributable lines and changes, not the team’s aggregate style.
