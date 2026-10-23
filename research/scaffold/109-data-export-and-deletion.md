# User data export and deletion

## Confirmed · C87 · 2026-10-23
User-data deletion and export are required capabilities, not optional product extras. Andrey cites GDPR as the reason. Minimum viable export: a ZIP archive containing JSON files with all the user's data.

This records the product/architecture requirement and the user's rationale; it is not a legal determination that every record is subject to identical rights or that this format alone establishes compliance.

Provide an actual usable way to request/receive the export and request deletion; specific self-service screens versus supported operational flows are not selected. Do not narrow the export to a profile summary. Exact record ownership, shared/company data boundaries, attachment packaging and exceptions must follow the real product/data model; no new blanket access grant or third-party data exposure inferred.

C86's 30-day recovery window applies to ordinary user deletion. It does not by itself define handling of explicit permanent-erasure requests or expiration of backups/history. Existing retention and audit requirements remain recorded; reconcile them in implementation without inventing a universal legal policy in the interview.

No import feature, round-trip restoration guarantee, ZIP schema or deletion schedule selected. [Recipe](../../skills/scaffold/references/data-rights.md).
