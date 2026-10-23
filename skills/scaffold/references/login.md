# Login

Where sending email is possible, use an emailed code as the default initial login method. The code is mandatory; an accompanying link is optional. People must be able to read the email on another machine and type the code into the original login page.

Offer passkeys from the start. Aim for “use a passkey or enter email,” without requiring email before using an existing passkey. Other methods—passwords, federated login, enterprise SSO—are product choices.

After successful email-code signup/login, automatically offer passkey creation with the normal browser/provider confirmation prompt. Do not wait for the user to request enrollment or find it in settings. Silent creation is not required. Email-code login remains available afterward; cancelling enrollment must not invalidate the completed email login.

## Web implementation guidance
Use discoverable passkeys and conditional WebAuthn authentication with `type="email" autocomplete="username webauthn"`. This lets the browser suggest a saved account before email entry. Verify the assertion on the server before identifying/signing in the account. Keep email entry available when passkey UI is unsupported, cancelled or unused. Enroll after verified email login. Total lockout is handled as a one-off below; detailed credential-management UX remains product-specific.

Mark code entry `autocomplete="one-time-code"`. Send a clearly labelled, copyable code and verify actual Mail recognition/autofill on supported iOS/macOS versions. Keep manual entry usable. Apple documents email autofill, but the exact email template still needs device testing; do not assume an SMS-specific format guarantees email recognition.

Email-code login alone is not 2FA. Respect existing company authentication requirements; email login remains available after passkey enrollment under those requirements.

Normal passkey creation may require browser/provider confirmation or device verification. Current Apple/Google silent-upgrade flows depend on recent password-manager password use; email-code login alone does not qualify. Do not promise silent creation after email-only login. Use standard enrollment, avoid duplicates, preserve login on cancellation, and request an explicit click only where the platform needs it.

[Evidence and remaining questions](../../../research/scaffold/97-login-methods.md).

## Total lockout
If email, all passkeys and existing sessions are unavailable, treat recovery as a one-off support case. Do not build a dedicated recovery flow by default. Selected staff may use privileged raw-data editing to repair an email where the actual case warrants it; ownership proof is not assumed. A B2B org-admin request may merit review, but is not automatic proof or a grant of direct shared-login editing to company admins. [Decision](../../../research/scaffold/105-one-off-support-repairs.md).
