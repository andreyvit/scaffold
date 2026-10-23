# Library boundaries

Build inside the project by default, in a separate package or unit.

Prefer separate libraries for entirely domain-independent, reusable, non-project-specific code, such as a templating language: separation keeps scope and boundaries clear. Make that choice explicitly each time.

Normally offer extraction once the code is proven in production and the API has stabilized over a few months of use. **Extract only with explicit user authorization for that extraction.** Do not extract automatically because code looks reusable or has aged enough.

Library API compatibility depends on who uses the library. Identify consumers and compatibility impact; have the user vet the decision. Do not assume either permission to break APIs or a universal promise to preserve them.
