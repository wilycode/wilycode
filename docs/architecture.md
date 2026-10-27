# Architecture and package boundaries

[← Back to WilyCode](../README.md) · [Getting started](getting-started.md)

WilyCode follows one main idea: **small libraries with clear responsibilities**. You can use a single package without adopting the rest of the ecosystem.

## How the packages fit together

Some packages define **contracts** (interfaces); others provide implementations or optional features.

| Area | Core package | Optional implementations and extensions |
| --- | --- | --- |
| Filtering | [`filter`](https://github.com/wilycode/filter) | [`filters`](https://github.com/wilycode/filters) |
| Validation | [`validator`](https://github.com/wilycode/validator) | [`validators`](https://github.com/wilycode/validators), [`recaptcha-validator`](https://github.com/wilycode/recaptcha-validator) |
| Forms | [`form`](https://github.com/wilycode/form) | [`form-csrf`](https://github.com/wilycode/form-csrf), [`form-image-upload`](https://github.com/wilycode/form-image-upload) |
| Database | [`database`](https://github.com/wilycode/database) | [`database-pdo`](https://github.com/wilycode/database-pdo), [`database-mysqli`](https://github.com/wilycode/database-mysqli) |
| Translation | [`translation`](https://github.com/wilycode/translation) | [`translation-array`](https://github.com/wilycode/translation-array), [`translation-database`](https://github.com/wilycode/translation-database) |
| Sessions | [`session`](https://github.com/wilycode/session) | [`session-php`](https://github.com/wilycode/session-php) |
| Profiling | [`profiler`](https://github.com/wilycode/profiler) | [`profiler-php`](https://github.com/wilycode/profiler-php) |

The table shows responsibilities, **not an exact Composer dependency graph**. Refer to each package's `composer.json` for required dependencies.

## Three practical examples

### Forms: contracts stay in the core

`wilycode/form` requires the `filter` and `validator` contracts, **not** the ready-made `filters` and `validators` collections. Applications can use their own implementations or install the provided ones.

`form-image-upload` is a separate package because upload-specific metadata does not belong in every form. It may depend on more packages without adding those requirements to the form core.

`form-csrf` is another optional extension. It provides a CSRF token field and validator with session-backed token management through the `session` contract. CSRF fields use the core Form's transparent-field behavior, so they are validated but excluded from aggregate business data. Applications can choose their session implementation without making native PHP sessions mandatory for `form`.

### Database: building is not executing

`database-query` builds SQL and parameters without a connection. `database-query-executor` handles execution with database adapters such as `database-pdo` or `database-mysqli`. `migration` handles schema versioning separately.

This lets applications choose their database-related parts without pulling in an entire framework.

### Routing: extensions are optional

`router` handles HTTP routing. `router-attribute` adds attribute discovery, and `router-profiler` adds diagnostics. Neither extension should be required just to use basic routing.

## Design rules

1. **One responsibility per package.** Avoid putting application-specific features in shared contracts.
2. **Depend on the smallest useful abstraction.** Keep ready-made implementations optional unless a package truly needs them.
3. **Separate development tools from runtime dependencies.** PHPUnit belongs in `require-dev`, not `require`.
4. **Keep versions independent.** A new release of one library does not require releases of all the others.
5. **Document limits.** Each README should explain what the package does *not* handle.

## What remains the application's responsibility?

WilyCode packages do not automatically configure your application's authorization rules, CSRF coverage across endpoints, file storage, production secrets or token revocation. `form-csrf` supplies reusable CSRF protection for forms, but the application must enable it for relevant requests and configure secure session handling. Likewise, `jwt-token` verifies tokens but does not implement a complete identity system, and `form-image-upload` does not persist files.

## Renamed database packages

For new projects use these names:

| Previous name | Current name |
| --- | --- |
| `wilycode/database-driver` | `wilycode/database` |
| `wilycode/database-driver-pdo` | `wilycode/database-pdo` |
| `wilycode/database-driver-mysqli` | `wilycode/database-mysqli` |

When updating an existing project, review namespaces and APIs as well as Composer dependencies.

See the [package catalog](../README.md#package-catalog) for all repositories.
