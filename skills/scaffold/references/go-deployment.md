# Go deployment

Default to one self-contained executable with templates and frontend assets embedded. Keep configuration, secrets and databases external. Do not require a container runtime.

Deploy: finish in-flight work → stop old process → start new process. Have the proxy briefly hold incoming requests during the restart. Keep one process owning the embedded database; target seconds of downtime hidden from users.

Failed deploy: stop and report; let an operator decide recovery. No automatic rollback or other corrective action by default. Keep infrastructure dumb until serious SRE scenario testing justifies automation: undertested recovery can misread failures and make them worse.

Follow the [migration policy](migrations.md): small startup migrations, 5-second budget each; large rewrites handled as maintenance operations.

These are Go defaults. Process supervision remains open. When higher availability is requested, use a [standby server](standby.md).
