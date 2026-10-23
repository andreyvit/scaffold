# Deleted-data recovery

## Confirmed · C86 · 2026-10-23
For ordinary user-deleted data, default to a 30-day recovery window. User supplied this as a default, not an immutable limit for every product.

This sets recoverability duration. No soft-delete representation, trash UI, purge schedule or recovery operator selected. Implement against the existing changes/undo architecture; storage mechanics follow the actual data model. Existing backup and analytics retention policies are separate and remain unchanged. A 30-day recovery window does not itself establish a deadline to erase every copy or a policy for explicit permanent-erasure requests.

[Recipe](../../skills/scaffold/references/deleted-data.md).

C87 separately requires user-data export and deletion. See [scope and minimum export](109-data-export-and-deletion.md); the ordinary recovery window does not determine all erasure mechanics.
