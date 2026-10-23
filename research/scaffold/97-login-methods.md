# Email codes and passkeys

## Confirmed · C71 · 2026-10-23
- Where sending email is possible, default initial login to an emailed code. Andrey's reasons: security and ease of access.
- A code is required because the email may arrive on another machine. A link may be included too; never make the link the only way to finish login.
- Ensure macOS/iOS recognize the message as a verification-code email and offer autofill. This is a required experience, not a claim already tested.
- Offer passkeys for login from the start with smooth UX. Desired entry: use a passkey or enter email. Andrey has not implemented passkeys before and asked whether they can work before email entry.
- Other login methods are product decisions; no universal password, federation or enterprise-SSO rollout selected.

## Confirmed · C72 · 2026-10-23
Flow: sign up or log in with an email code, automatically offer passkey creation with the normal confirmation prompt, then continue using either the passkey or email codes. The user explicitly clarified that confirmation is welcome; “automatic” means offering enrollment without waiting for the user to request it. Email-code login stays available after enrollment. Existing company login requirements remain in force.

Silent creation is not required. The research below explains why the normal confirmation flow is the appropriate implementation.

## Technical findings · 2026-10-23
External capabilities, not additional user decisions. No app implementation or device tests performed.

### Passkeys before email
Yes. Discoverable credentials let the browser/provider offer accounts for the site before the user enters an email. Start a challenge without a specific account/credential allow-list; verify the returned assertion and map its credential to the account on the server. The site learns the chosen account through successful authentication, not a silent inventory of saved accounts.

For the desired UI, use conditional WebAuthn authentication alongside an email field annotated `type="email" autocomplete="username webauthn"`. Available passkeys appear through browser autofill; selecting one authenticates. Otherwise the person types email and requests a code. A separate passkey button can invoke the browser chooser. Detect capabilities and handle cancellation/no usable credential without blocking email entry. A passkey must already have been registered for that account/site; provider/device storage and sync make it available later.

Sources: [Google form autofill guide](https://web.dev/articles/passkey-form-autofill), [Google server authentication](https://developers.google.com/identity/passkeys/developer-guides/server-authentication), [Apple passkey support](https://developer.apple.com/documentation/authenticationservices/supporting-passkeys).

### Apple email-code autofill
Apple documents Mail-to-Safari code autofill from iOS 17 and macOS Sonoma. Mark the web code field `autocomplete="one-time-code"`; field eligibility and recognizing the incoming message are separate requirements. Use a clearly labelled, copyable code in the email and validate the exact delivered template on supported Apple devices with Mail configured. Manual entry must still work, including when the email is read on another machine.

No normative email-body syntax guaranteeing recognition was found in the consulted docs. Do not claim the SMS domain-binding format is an email standard or promise autofill in every third-party mail app. Exact template recognition remains to be tested.

Sources: [Apple iOS 17 release notes](https://support.apple.com/en-ie/118723), [Apple Sonoma announcement](https://www.apple.com/newsroom/2023/06/macos-sonoma-brings-new-capabilities-for-elevating-productivity-and-creativity/), [Apple HTML autofill fields](https://developer.apple.com/documentation/security/enabling-password-autofill-on-an-html-input-element), [WebKit code input](https://webkit.org/blog/14787/webkit-features-in-safari-17-2/).

### Authentication strength and policies
An email code used alone is passwordless single-factor login, not automatically two-factor authentication despite OS terminology. Passkeys authenticate with a site-bound cryptographic key; a server stores the public key, and the provider signs the challenge. Do not treat an optional email route as having the same phishing resistance as passkeys. Existing company login requirements still apply (82).

C72 selects enrollment following email-code signup/login and continued email login. Remaining: enrollment prompt details, credential management, recovery when email is unavailable and stronger assurance requirements. No exact code length, expiry or server library selected.

[Recipe](../../skills/scaffold/references/login.md).

### Creation after email login · checked 2026-10-23
Ordinary passkey registration can follow verified email login, using the browser/provider creation flow. The provider may require confirmation/device verification; cancellation must leave the completed email login usable. Initiate enrollment in this flow rather than making the person find settings. Avoid duplicate registration and use an inline action if the platform needs a fresh user gesture. These are implementation consequences of the desired flow, not new interview decisions.

Silent automatic creation (WebAuthn Conditional Create) has additional conditions. Chrome's current guide explicitly requires a recently used saved password and excludes passwordless sign-ins. Apple's upgrade flow likewise checks recent password autofill for the matching account. Email-code verification alone does not satisfy those documented prerequisites. Browser capability detection alone does not establish provider eligibility. Do not add a password just to unlock an automatic upgrade.

Thus email verification followed by automatically offered normal passkey enrollment with system UI satisfies the clarified intent. Silent creation is unnecessary. No provider/device test performed.

Sources: [Google Conditional Create](https://developer.chrome.com/docs/identity/webauthn-conditional-create), [Apple automatic upgrades](https://developer.apple.com/videos/play/wwdc2024/10125/), [Standard passkey registration](https://web.dev/articles/passkey-registration).
