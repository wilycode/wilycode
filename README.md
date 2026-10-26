<p align="center">
  <img src="./docs/assets/wilycode-symbol-dark.svg" alt="WilyCode logo" width="176">
</p>

<h1 align="center">WilyCode</h1>
<p align="center"><strong>Clever, modular PHP components.</strong></p>
<p align="center">Independent, framework-agnostic libraries. Install only what your project needs.</p>

<p align="center">
  <a href="https://www.php.net/"><img alt="PHP 8.4+" src="https://img.shields.io/badge/PHP-8.4%2B-777BB4"></a>
  <a href="LICENSE"><img alt="MIT License" src="https://img.shields.io/badge/License-MIT-blue.svg"></a>
  <a href="https://packagist.org/?query=wilycode"><img alt="Composer packages on Packagist" src="https://img.shields.io/badge/Composer-Packagist-F28D1A"></a>
</p>

<p align="center">
  <a href="#getting-started">Getting started</a> ·
  <a href="#explore-the-ecosystem">Explore packages</a> ·
  <a href="#package-catalog">Package catalog</a> ·
  <a href="docs/architecture.md">Architecture</a> ·
  <a href="#documentation-and-support">Documentation</a>
</p>

WilyCode is a collection of **independent PHP 8.4+ libraries** for building web applications. It covers HTTP routing, database access, template rendering, form handling, translation and application infrastructure. **WilyCode is not a monolithic framework:** there is no meta-package that you must install.

Each library maintains its **own repository, README, tests, version tags and Composer installation**. This repository is the central documentation and navigation hub—not an installable framework.

**[Find packages on Packagist](https://packagist.org/?query=wilycode)** · **[GitHub organization](https://github.com/orgs/wilycode/repositories)** · **[Getting started guide](docs/getting-started.md)**

## Contents

- [Getting started](#getting-started)
- [Explore the ecosystem](#explore-the-ecosystem)
- [Package catalog](#package-catalog)
- [How the packages fit together](#how-the-packages-fit-together)
- [Documentation and support](#documentation-and-support)
- [Legacy package names](#legacy-package-names)
- [License](#license)

## Getting started

Install a specific package into your PHP application:

```bash
composer require wilycode/router
```

Or combine a small set of components for your use case:

```bash
# Forms with optional ready-made filters and validators
composer require wilycode/form wilycode/filters wilycode/validators

# SQL query building and PDO execution
composer require wilycode/database-query wilycode/database-pdo wilycode/database-query-executor
```

Composer automatically resolves declared dependencies. **Do not install every package by default.** Check the selected package's README for its runtime requirements and examples.

See the [getting started guide](docs/getting-started.md) for examples of choosing components.

## Explore the ecosystem

Browse packages by category. Select a category to jump to its package list.

<table width="100%">
<tbody>
<tr>
<td width="50%" valign="top">
<p><a href="#core"><img src="docs/assets/icons/core.png" alt="" width="48" height="48"></a></p>
<p><strong>Core & application</strong></p>
<p>Composable form handling, validation, dependency injection and configuration.</p>
<p><a href="#core">Explore packages →</a></p>
</td>
<td width="50%" valign="top">
<p><a href="#database"><img src="docs/assets/icons/database.png" alt="" width="48" height="48"></a></p>
<p><strong>Database & migrations</strong></p>
<p>Driver interfaces, query building, execution, models and schema versioning.</p>
<p><a href="#database">Explore packages →</a></p>
</td>
</tr>
</tbody>
<tbody>
<tr>
<td width="50%" valign="top">
<p><a href="#http-routing"><img src="docs/assets/icons/http-routing.png" alt="" width="48" height="48"></a></p>
<p><strong>HTTP & routing</strong></p>
<p>Request routing, controller discovery and PSR-7 responses.</p>
<p><a href="#http-routing">Explore packages →</a></p>
</td>
<td width="50%" valign="top">
<p><a href="#runtime"><img src="docs/assets/icons/runtime.png" alt="" width="48" height="48"></a></p>
<p><strong>Runtime & utilities</strong></p>
<p>Caching, sessions, JWT tokens and application logging.</p>
<p><a href="#runtime">Explore packages →</a></p>
</td>
</tr>
</tbody>
<tbody>
<tr>
<td width="50%" valign="top">
<p><a href="#templates"><img src="docs/assets/icons/templates.png" alt="" width="48" height="48"></a></p>
<p><strong>Templates</strong></p>
<p>PHP templates with optional assets, text utilities and translation.</p>
<p><a href="#templates">Explore packages →</a></p>
</td>
<td width="50%" valign="top">
<p><a href="#translation"><img src="docs/assets/icons/translation.png" alt="" width="48" height="48"></a></p>
<p><strong>Translation</strong></p>
<p>Localization contracts, language rules and translation providers.</p>
<p><a href="#translation">Explore packages →</a></p>
</td>
</tr>
</tbody>
<tbody>
<tr>
<td width="50%" valign="top">
<p><a href="#profiling"><img src="docs/assets/icons/profiling.png" alt="" width="48" height="48"></a></p>
<p><strong>Profiling</strong></p>
<p>Optional instrumentation and profiling decorators.</p>
<p><a href="#profiling">Explore packages →</a></p>
</td>
<td width="50%" valign="top">&nbsp;</td>
</tr>
</tbody>
</table>

## Package catalog

Below are the WilyCode libraries, grouped by responsibility. Follow each link for the library's full API documentation, installation requirements and latest release information. This index intentionally does not pin package versions.

<a id="core"></a>

### <img src="docs/assets/icons/core.svg" alt="" width="28" height="28"> Core & application

| Package | Purpose |
| --- | --- |
| [`wilycode/container`](https://github.com/wilycode/container) | PSR-11 dependency injection with factories and autowiring. |
| [`wilycode/dotenv`](https://github.com/wilycode/dotenv) | Strict, lightweight `.env` configuration loader. |
| [`wilycode/filter`](https://github.com/wilycode/filter) | Small reusable filter contract. |
| [`wilycode/filters`](https://github.com/wilycode/filters) | Ready-made string, type, array and slug filters. |
| [`wilycode/validator`](https://github.com/wilycode/validator) | Validation contracts and structured, nested errors. |
| [`wilycode/validators`](https://github.com/wilycode/validators) | Ready-made validators for common input types. |
| [`wilycode/form`](https://github.com/wilycode/form) | Form fields, nested fieldsets and collections. |
| [`wilycode/form-image-upload`](https://github.com/wilycode/form-image-upload) | Optional image-upload metadata fieldset for Form. |
| [`wilycode/recaptcha-validator`](https://github.com/wilycode/recaptcha-validator) | Server-side Google reCAPTCHA v3 verification. |

<a id="database"></a>

### <img src="docs/assets/icons/database.svg" alt="" width="28" height="28"> Database & migrations

| Package | Purpose |
| --- | --- |
| [`wilycode/database`](https://github.com/wilycode/database) | Driver-independent connection, query and transaction contracts. |
| [`wilycode/database-pdo`](https://github.com/wilycode/database-pdo) | PDO implementation and compiled-query binding. |
| [`wilycode/database-mysqli`](https://github.com/wilycode/database-mysqli) | MySQLi implementation and compiled-query binding. |
| [`wilycode/database-query`](https://github.com/wilycode/database-query) | SQL query builder and compiled query contracts. |
| [`wilycode/database-query-executor`](https://github.com/wilycode/database-query-executor) | Execution layer connecting compiled queries and drivers. |
| [`wilycode/database-query-executor-cache`](https://github.com/wilycode/database-query-executor-cache) | Optional PSR-16 cache decorator for query execution. |
| [`wilycode/database-model`](https://github.com/wilycode/database-model) | Attribute-based models, metadata, hydration and relationships. |
| [`wilycode/database-repository`](https://github.com/wilycode/database-repository) | Model repositories with CRUD, relationships and pagination. |
| [`wilycode/migration`](https://github.com/wilycode/migration) | Versioned database migrations, CLI and rollback. |

<a id="http-routing"></a>

### <img src="docs/assets/icons/http-routing.svg" alt="" width="28" height="28"> HTTP & routing

| Package | Purpose |
| --- | --- |
| [`wilycode/router`](https://github.com/wilycode/router) | PSR-7/PSR-15 routing, middleware, named routes and URL generation. |
| [`wilycode/router-attribute`](https://github.com/wilycode/router-attribute) | Attribute-based route declarations, discovery and caching. |
| [`wilycode/http-response`](https://github.com/wilycode/http-response) | Typed PSR-7 response factory for HTML, JSON and redirects. |

<a id="runtime"></a>

### <img src="docs/assets/icons/runtime.svg" alt="" width="28" height="28"> Runtime & utilities

| Package | Purpose |
| --- | --- |
| [`wilycode/cache-file`](https://github.com/wilycode/cache-file) | PSR-16 file cache with atomic writes and TTL. |
| [`wilycode/session`](https://github.com/wilycode/session) | Storage-independent session contract. |
| [`wilycode/session-php`](https://github.com/wilycode/session-php) | Adapter for native PHP sessions. |
| [`wilycode/jwt-token`](https://github.com/wilycode/jwt-token) | Minimal HS256 JWT issuing and verification. |
| [`wilycode/logger-file`](https://github.com/wilycode/logger-file) | PSR-3 file logging with channels and structured context. |

<a id="templates"></a>

### <img src="docs/assets/icons/templates.svg" alt="" width="28" height="28"> Templates

| Package | Purpose |
| --- | --- |
| [`wilycode/template`](https://github.com/wilycode/template) | Compiled PHP templates with layouts, sections and components. |
| [`wilycode/template-assets`](https://github.com/wilycode/template-assets) | CSS and JavaScript asset collection and processing. |
| [`wilycode/template-string`](https://github.com/wilycode/template-string) | String and formatting extensions for Template. |
| [`wilycode/template-translation`](https://github.com/wilycode/template-translation) | Translation extensions for Template. |

<a id="translation"></a>

### <img src="docs/assets/icons/translation.svg" alt="" width="28" height="28"> Translation

| Package | Purpose |
| --- | --- |
| [`wilycode/translation`](https://github.com/wilycode/translation) | Translation contracts and locale formatting. |
| [`wilycode/translation-array`](https://github.com/wilycode/translation-array) | PHP-array translation provider with fallback and pluralization. |
| [`wilycode/translation-database`](https://github.com/wilycode/translation-database) | Database-backed translation provider with optional caching. |
| [`wilycode/translation-languages`](https://github.com/wilycode/translation-languages) | Pluralization rules and locale resources. |

<a id="profiling"></a>

### <img src="docs/assets/icons/profiling.svg" alt="" width="28" height="28"> Profiling

| Package | Purpose |
| --- | --- |
| [`wilycode/profiler`](https://github.com/wilycode/profiler) | Profiling contracts and value objects. |
| [`wilycode/profiler-php`](https://github.com/wilycode/profiler-php) | Profiler implementation with timing and Server-Timing support. |
| [`wilycode/router-profiler`](https://github.com/wilycode/router-profiler) | Optional routing diagnostics and timings. |
| [`wilycode/database-query-executor-profiler`](https://github.com/wilycode/database-query-executor-profiler) | Optional profiling decorators for database execution. |

## How the packages fit together

Some packages define **contracts** while others supply optional implementations:

| Foundation | Optional implementation |
| --- | --- |
| [`filter`](https://github.com/wilycode/filter) | [`filters`](https://github.com/wilycode/filters) |
| [`validator`](https://github.com/wilycode/validator) | [`validators`](https://github.com/wilycode/validators), [`recaptcha-validator`](https://github.com/wilycode/recaptcha-validator) |
| [`form`](https://github.com/wilycode/form) | [`form-image-upload`](https://github.com/wilycode/form-image-upload) |
| [`database`](https://github.com/wilycode/database) | [`database-pdo`](https://github.com/wilycode/database-pdo), [`database-mysqli`](https://github.com/wilycode/database-mysqli) |
| [`translation`](https://github.com/wilycode/translation) | [`translation-array`](https://github.com/wilycode/translation-array), [`translation-database`](https://github.com/wilycode/translation-database) |
| [`session`](https://github.com/wilycode/session) | [`session-php`](https://github.com/wilycode/session-php) |
| [`profiler`](https://github.com/wilycode/profiler) | [`profiler-php`](https://github.com/wilycode/profiler-php) |

These examples illustrate dependencies rather than a requirement to install each pair. See [architecture](docs/architecture.md) for more information.

## Documentation and support

- **[Getting started](docs/getting-started.md)** — installing packages and choosing a minimal set.
- **[Architecture](docs/architecture.md)** — contracts, implementations and optional integrations.
- **[Package maintenance](docs/publishing.md)** — tests, release tags and Packagist updates.
- **[Contributing](CONTRIBUTING.md)** — where to open issues and submit changes.

For issues with an individual library, please use that package's **Issues** tab. This repository is for questions or corrections about the ecosystem-wide documentation.

## Legacy package names

Older Packagist entries may still exist under `wilycode/database-driver`, `wilycode/database-driver-pdo` and `wilycode/database-driver-mysqli`. For new projects, use **`wilycode/database`, `wilycode/database-pdo` and `wilycode/database-mysqli`**. See [the migration notes](docs/architecture.md#previous-database-package-names).

## License

Documentation in this repository is released under the [MIT License](LICENSE). Each code package is distributed and versioned separately; check its own repository for license details.
