# Raw analytics and journals

Confirmed by Andrey, 2026-10-20. [Analytics goals and operation](83-business-and-onboarding.md).

## Early default
Store raw events. Early on, we do not yet know which questions or definitions will matter; preserve flexibility to change our minds and reprocess history.

Append-only files with sequential access are acceptable initially. Andrey created [journal](https://github.com/andreyvit/journal/) for this kind of use. It is a reference implementation, not an exclusive storage mandate.

## Journal requirements
- In B2B, use a journal per tenant.
- Compress and encrypt journals.
- Archive older files to external storage; remove archived copies from the app server. External archives follow the retention policy below.
- For high-volume raw analytics, devise an efficient binary event format avoiding repeated common strings such as page paths and user agents. No specific encoding/dictionary design selected.
- Reprocess retained events when metric definitions change.

## At scale
Keeping everything can become expensive; explicitly discuss the business/product tradeoff rather than carrying the early default forward blindly. Reprocessing all events may become infeasible. If retaining everything, change storage/access or aggregation design as needed for efficient analysis.

Reason: preserve learning flexibility while uncertainty is high; pay for more sophisticated processing when actual volume and business needs justify it. No permanent all-data retention or full-scan requirement.

## Implementation evidence — separate from decisions
Checked local journal HEAD `e29e3db284ce1d8135d2015b286fca7ed15f315d` and public README on 2026-10-20. README describes multi-file append-only journals, atomic commits, timestamps, compression and encryption. Local `seal.go` seals segments through sealer; `fileformat.go` provides binary segment/record framing.

This is not a validated analytics implementation. The brief code pass did not establish external upload orchestration or application-level deduplication of strings. Do not confuse binary record framing with the required efficient analytics payload format. No source code changed or tests run.

## Retention — confirmed
Always set a finite retention window, including external archives. Default raw analytics retention: **24 months**. An explicit product choice such as **60 months** is acceptable; do not imply a hard maximum of 24 months.

Reasons supplied by Andrey: early/pre-MVP products change enough over two years that older data loses usefulness; a stated cap, even a long one, is preferable to indefinite retention for privacy-policy clarity and vendor due diligence. This records his rationale, not a legal-compliance conclusion.

Implement expiry for retained raw events, not merely removal of local copies after archiving. Aggregate retention and detailed deletion mechanics are separate decisions; not inferred here.
