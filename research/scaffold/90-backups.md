# Backups

## Confirmed · C50
Day-one scheduled off-server backups and tested restore procedure. Production restores explicitly initiated by operator. Support S3-compatible storage or SSH uploads; S3 details or SSH key and SCP address/path in config. Andrey points to Bubblehouse for implementation details.

## Authored Bubblehouse baseline
Repository: `/Users/andreyvit/Developer/prairie/backend`. Snapshot `aaa53bdc6fbda464d7d563d696ebca76719469ed` (2025-05-31). All 445 lines of `fireback/backups.go` blame to Andrey Tarantsov at that snapshot.

- `fireback/backups.go:54–139`: scheduled job, staging file → completed local file → SSH/SCP and/or S3 upload. Size/duration/error logs. Local and remote trimming.
- `fireback/backups.go:278–375`: cancellable Bolt read-transaction snapshot, zstd compression, running metric/state. Historical long read-transaction costs require evaluation; do not blindly copy for large databases.
- `fireback/backups.go:377–408`: S3 upload uses one signed PUT; not proof of large-file or arbitrary S3-provider compatibility.
- `fire/fireappsettings/fireappsettings.go:53–65`: automatic flag, interval, local staging/storage, local/remote keep-latest and keep-days, S3 bucket, Hetzner user. AWS credentials/region in secret options. SSH key uses host SSH setup; user now explicitly requests configurable key/destination.
- `_readme/backups.md`, previously authenticated B4: local restore for debugging/testing, compact Bolt copy, invisible mode suppresses external writes. Historical S3 size/cost difficulties motivated SSH storage.

Current checkout uses newer ZFS/multiple-target/secondary-backup machinery, including Stanislav commits. Not imported as Andrey's values or scaffold defaults. No repository changes, uploads or restores performed.

## Recipe and remaining choices
[Recipe](../../skills/scaffold/references/backups.md). Generalized SSH/S3 configuration follows current user instruction; exact field names unselected. Snapshot integrity, isolated restore, logs/metrics and credential handling supply implementation checks, not additional interview confirmations.

Open: encryption integration, storage budget and recovery objectives. Hourly full backups initially (C54); off-server retention below (C55). Analytics retention does not set backup retention. No automatic production recovery.

## Encryption direction · C51 · 2026-10-23
Andrey: ideally encrypt before upload; unsure of mechanism, suggests sealer when writing backups. Preference confirmed; not a final library selection or key-management design.

Inspected [upstream README](https://github.com/andreyvit/sealer) and clean local checkout `/Users/andreyvit/Developer/andreyvit/sealer`, HEAD `9af18a9cdd9c97ecd16f10280da1f3aa6517aa9d` (Andrey, 2025-03-21). API/source observations, not a security audit:
- `Seal` supplies a streaming writer combining zstd compression and authenticated encryption. Candidate flow: snapshot → sealer writer → completed file → upload; no extra compression layer needed.
- Writer `Close` finishes compression and final encrypted chunk; check its error before marking backup complete.
- `Prepare` exposes key ID; `Open` uses caller-supplied secret key. Same long-term secret is needed for writing and restoring; per-file encryption keys are encapsulated internally.
- Key storage, recovery copies and retention of old keys belong to the app/operator. Library does not solve custody.

No integration or restore tests run. Before adoption, test full restore plus wrong/missing keys, corruption, truncation and write/close failures.

## Key custody and rotation · C52 · 2026-10-23
Dedicated backup key in encrypted config; separate recovery copy in 1Password. Keep old keys while their backups exist. Rotate monthly where appropriate, at least annually while starting out. User confirmed custody proposal and added cadence; no automatic rotation mechanism or re-encryption of existing backups selected.

## WAL deferred · C53 · 2026-10-23
Add WAL when EDB technically supports it. None for now; no separate interim change-history replication. Current recovery relies on completed snapshot backups. Future WAL transport/cadence and recovery mechanics remain unselected. This is the user's implementation dependency, not a fresh audit of EDB capabilities.

## Frequency · C54 · 2026-10-23
Hourly full backups by default for small, early-stage databases. Adjust per project: more frequent backups reduce potential data loss but add I/O and storage cost. Frequency is a schedule, not a guarantee that off-server backups are always less than an hour old.

## Retention · C55 · 2026-10-23
Unless storage space becomes a concern, keep all hourly backups for the last week, then daily backups for 60 days. Replaces proposed 24-hour hourly/30-day daily policy. Configurable per project; does not prescribe automatic retention reduction when space is low. Local staging retention remains separate.

## Standby restore loop · C56 · 2026-10-23
When the user requests higher availability via a second server/hot standby, repeatedly check for a newer backup, roughly every 10 minutes. Download and restore new backups so the standby is ready to run. [Recipe](../../skills/scaffold/references/standby.md).

This authorizes automatic standby refresh, not automatic production restore or failover. Poll interval does not change the hourly snapshot default. Standby app policy refined in C57 below; no additional day-one recurring restore-drill requirement inferred. Recipe access controls/metrics/logging are implementation guidance, not separately confirmed policy choices.

## Standby app execution · C57 · 2026-10-23
Verify the app can launch against restored data. For most apps, keep it stopped until the standby becomes primary. Verification mechanism remains open; do not infer a continuously running invisible-mode app or a mandatory brief full launch on every restore.
