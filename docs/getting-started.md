# Getting started

[← Back to WilyCode](../README.md) · [Package catalog](../README.md#package-catalog)

WilyCode is a collection of independent **PHP 8.4+** libraries, not a framework. Install only the packages your project needs. Each package has its own README, dependencies and version.

## Before you start

You need PHP 8.4 or later and Composer 2. Some packages require PHP extensions or implementations of PSR interfaces. Composer reports missing requirements during installation.

## Choose the packages you need

### HTTP routing

```bash
composer require wilycode/router
```

Add [`router-attribute`](https://github.com/wilycode/router-attribute) for PHP attribute routes, or [`router-profiler`](https://github.com/wilycode/router-profiler) for diagnostics. Both are optional.

### Forms and validation

```bash
composer require wilycode/form
```

`form` uses the small `filter` and `validator` **contracts**. Add ready-made implementations when needed:

```bash
composer require wilycode/filters wilycode/validators
```

For optional CSRF protection in session-backed forms, install [`form-csrf`](https://github.com/wilycode/form-csrf) and a session implementation, such as `session-php`:

```bash
composer require wilycode/form-csrf wilycode/session-php
```

`form-csrf` provides a required, transparent CSRF token field, validation, and a session-backed token manager. The submitted token is validated but excluded from `Form::getData()`. See its [README](https://github.com/wilycode/form-csrf#quick-start) for integration and [Packagist](https://packagist.org/packages/wilycode/form-csrf) for available versions.

[`form-image-upload`](https://github.com/wilycode/form-image-upload) is a separate extension for image-upload **metadata**. It does not store or process uploaded images.

### Database and migrations

For SQL building and execution with a PDO adapter:

```bash
composer require wilycode/database-query wilycode/database-query-executor wilycode/database-pdo
```

The query builder creates SQL and bound parameters; the executor and driver handle database execution. If you only need compiled SQL, install `wilycode/database-query` by itself.

Schema migrations are available separately:

```bash
composer require wilycode/migration
```

### Templates and translations

```bash
composer require wilycode/template wilycode/translation-array
```

Add [`template-translation`](https://github.com/wilycode/template-translation) only if your templates need translation filters. Other providers and extensions are optional.

### Authentication helpers

```bash
composer require wilycode/jwt-token
```

[`jwt-token`](https://github.com/wilycode/jwt-token) is an HS256 signing and verification helper, **not** a complete authentication, OAuth or OpenID Connect system. For server-side Google reCAPTCHA v3 verification, use [`recaptcha-validator`](https://github.com/wilycode/recaptcha-validator).

## Use a package in PHP

After installing a package, load Composer's autoloader (unless your application already does so). For example, `database-query` can compile SQL without opening a connection:

```php
<?php

declare(strict_types=1);

require __DIR__ . '/vendor/autoload.php';

use WilyCode\Database\Query\Query;

$compiled = Query::select('users')
    ->where('active', true)
    ->compile();

// $compiled->sql contains SQL with placeholders.
// $compiled->params contains the values to bind.
```

For real application examples and configuration, use the **README of the package you installed**.

## A few useful rules

- **Do not install the hub.** This repository is documentation, not a Composer package.
- **Let Composer resolve dependencies.** You do not need to install each contract separately when another package already requires it.
- **Prefer narrow dependencies.** Add optional features only when your application needs them.
- **Check the package version.** Libraries are versioned and released independently.

For an overview of package relationships, see [Architecture](architecture.md). If you maintain a WilyCode library, see [Publishing](publishing.md).
