# Permissions and roles

Include permissions and roles in the code from the start. Supply default roles.

Offer a UI for customizing roles as an optional feature. Implement that UI only when authorized for the product; the underlying permissions/roles model is part of the foundation regardless.

Choose concrete permissions and default roles for the product. Do not hardwire the internal model to a fixed-role-only product UI.

For superstaff access and audit granularity, follow [customer data access](customer-data-access.md).

Grant selected staff a distinct raw-data editing permission for exceptional repairs. Do not grant it to all staff or company admins by default. No generic editor UI selected. [Scope](../../../research/scaffold/105-one-off-support-repairs.md).
