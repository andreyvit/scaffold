# Standby server

Add a second server when the user requests higher availability. Poll [backup storage](backups.md) for a newer completed backup about every 10 minutes. When available, download and restore it so the standby is ready to run.

Automatic restore here refreshes the standby only. Production restore and promotion remain operator-controlled under the [deployment policy](go-deployment.md). Backup frequency still determines data freshness; polling every 10 minutes does not imply 10-minute data loss at most.

Restrict backup/key access to authorized operators and the restore process. Track restored-backup timestamp, last successful restore, duration and failures; log restore results without secrets.

Verify that the app can launch against the restored data. For most apps, keep it stopped until the standby becomes primary; do not run it continuously merely to demonstrate readiness. Exact launch-verification mechanism remains to be designed; verification must not produce external effects.
