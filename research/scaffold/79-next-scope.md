# Initial scope interview — historical

Use [STATE.md](STATE.md#resume-here) for the current question and [confirmed decisions](78-confirmed-decisions.md) for subsequent answers. This outline is not a request to restart the scope interview.

Values are settled. Choose the problem space before more framework research.

## Proposed architecture families
1. **Server/web:** SSR first; rich-page and SPA alternatives.
2. **iOS:** native; platform-specific implementation.
3. **Android:** native; platform-specific implementation.

Products combine these families. Consumer/B2B, offline work, collaboration and media are requirement variants, not automatically separate whole-app architectures.

## First interview: scope only
Mark each **first / later / out**. Suggested starting scope, not approved:

| Requirement variant | Proposal | Why it earns a branch |
|---|---|---|
| Individual-owned data, optional/required account | First | Basic consumer and personal productivity apps |
| Company-owned data + member accounts | First | B2B permissions, invitations, lifecycle |
| Local-only app | First | Avoid server/account machinery when unnecessary |
| Server-backed app with cached reads | First | Common native experience; clear failure states |
| Durable offline edits + multi-device sync | **Confirmed: first, opt-in** | Simple version selection where acceptable; revision-gated rebasing otherwise. [Details](80-offline-sync.md). |
| Simultaneous collaborative editing | Later | Different conflict and interaction requirements |
| Entertainment/media + public contributions | Explicit decision | Uploads, playback/feed behavior, moderation and abuse |
| Host-embedded app | Later | Host identity, lifecycle and review constraints |

## Then, one branch at a time
Choose a representative app → map remaining decisions → recommend options using the confirmed values → ask preference and why → prove uncertain mechanisms → write terse recipes.

Start with server/web because the architecture is current. Then adapt the recovered mobile responsibility layout to modern native APIs. Keep privacy/durability/availability questions in the per-project requirements, with the confirmed defaults.

Do not reopen native vs shared UI, or interview all core values again.
