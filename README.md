# @tummycrypt/tinyland-admin-audit (retired)

This repository is retired and archived (2026-10-09, estate uplift rulings
RU2, RU6, RU7, RU8).

Its code now lives in
[xoxd-ai/tinyland-logging](https://github.com/xoxd-ai/tinyland-logging) as
the `./admin-audit` subpath export of `@tummycrypt/tinyland-logging`, starting
with tinyland-logging 1.2.0. The API is unchanged: `configureAdminAudit`,
`getAdminAuditConfig`, `resetAdminAuditConfig`, `extractClientContext`,
`calculateChangedFields`, `logAdminAction`, `logAdminActionFailure`,
`logUserManagement`, `logPermissionChange`, `logContentManagement` and the
`Logger`, `AuditRequestEvent`, `AdminAuditPackageConfig`, `AdminAction`,
`ResourceType`, `DeviceType`, `AdminAuditLog` and `AdminAuditOptions` types.

## Migrating

1. In `MODULE.bazel`, replace
   `bazel_dep(name = "tummycrypt_tinyland_admin_audit", ...)` with
   `bazel_dep(name = "tummycrypt_tinyland_logging", version = "1.2.0")`
   from [xoxd-ai/bazel-registry](https://github.com/xoxd-ai/bazel-registry),
   and link `@tummycrypt_tinyland_logging//:pkg` with `npm_link_package`.
2. Change imports (and `vi.mock` targets) from
   `@tummycrypt/tinyland-admin-audit` to
   `@tummycrypt/tinyland-logging/admin-audit`.

The registry module `tummycrypt_tinyland_admin_audit` is marked deprecated.
Its 0.2.2 and 0.2.3 entries stay resolvable and nothing is yanked, so
existing pins keep building until they move. The package is no longer
published to npm or GitHub Packages; the publish workflow is removed.
