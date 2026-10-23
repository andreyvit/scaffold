# Backups

Include scheduled off-server backups and a tested restore procedure from day one. Production restore requires an operator's explicit action.

Support S3-compatible storage and SSH/SCP destinations. Configure through [app configuration](app-config.md):
- S3 endpoint, region, bucket/path and credentials.
- SSH key, host/user/port and SCP destination path.
- Schedule, local staging/storage and local/remote retention.

Keep credentials encrypted in config under the existing keyring scheme. Restrict backup/restore access; do not log secrets.

Prefer encrypting backups before upload. For Go, evaluate [sealer](https://github.com/andreyvit/sealer): stream snapshot through its compressing/encrypting writer into the backup file, close successfully, then upload. Restore through its reader using the recorded key ID to find the secret key. Integration remains to be designed and tested.

Use a dedicated backup key in encrypted config; save a separate recovery copy in 1Password. Rotate monthly where appropriate, at least annually while starting out. Keep old keys while any retained backups need them. Rotation automation is not prescribed.

Create a consistent database snapshot; distinguish incomplete files from completed backups. Test restore into an isolated instance with external effects disabled.

For now, use snapshot backups only. Add WAL-based recovery when EDB supports it; do not build a separate interim WAL or off-server change-history replication system. Recovery between snapshots is not provided yet.

Metrics: last successful off-server backup, failures, duration and bytes. Logs: preparation/upload/cleanup results, destination identifier and errors. Expose stale or failed backups; do not automatically restore production.

Default to hourly full backups for small, early-stage databases. Off-server retention: all hourly backups for the last week, then daily backups for 60 days, unless storage space becomes a concern. Adjust frequency and retention per project for data-loss requirements and I/O/storage cost.

Test snapshot/restore, upload failures and retention before relying on backups. Provider choice must support expected backup sizes.

When the user requests a second server for higher availability, use the [standby restore loop](standby.md).
