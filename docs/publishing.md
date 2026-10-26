# Publishing a WilyCode package

[← Back to WilyCode](../README.md) · [Architecture](architecture.md)

This guide is for maintainers publishing an **individual library**. The central `wilycode/wilycode` repository is only a documentation hub and is **not** submitted to Packagist.

## 1. Check the package

Before creating a release, verify:

- `composer.json`: package name, description, MIT license, PHP requirements, PSR-4 autoloading, correct `require` and `require-dev` sections.
- `README.md`: installation, a working example, key features, limitations and a clear link to the [WilyCode ecosystem](https://github.com/wilycode/wilycode).
- `CHANGELOG.md`: notable changes to behavior or public API.
- `tests/` and `.github/workflows/`: tests and CI are present in Git but excluded from Composer distribution archives using `.gitattributes` `export-ignore` where appropriate.

Keep the documentation in **English** and verify that examples use APIs available in the version being released.

## 2. Run tests locally

Inside the **library's own directory**:

```bash
composer install
composer validate --strict
composer test
```

When no `composer.lock` exists, `composer install` resolves dependencies and creates one locally. Libraries commonly exclude `composer.lock` and `vendor/` from Git. Do not release while validation or tests are failing.

## 3. Commit and check GitHub Actions

```bash
git status --short
git add -A
git commit -m "chore: prepare release"
git push origin main
```

Commit only when there are actual changes. Before the tag, confirm that GitHub Actions passed for the **exact commit** you intend to release (including all supported PHP versions configured in that repository).

## 4. Create a version tag

For the first release, use `v0.1.0`; for later releases, choose the appropriate next version.

```bash
git status --short
git pull --ff-only origin main
git tag -a v0.1.0 -m "Initial public release"
git push origin v0.1.0
```

Do not tag with uncommitted changes. **Do not move or overwrite a published tag**; create a new version when releasing a change.

## 5. Publish a GitHub Release

In your package repository, open **Releases → Draft a new release**. Select the existing tag and use a short title such as `WilyCode Form v0.1.0`.

Include a concise summary:

- Main features and important changes.
- Installation: `composer require wilycode/<package>`.
- Any relevant compatibility or security notes.
- A link to the [WilyCode PHP Ecosystem](https://github.com/wilycode/wilycode).

Use **Pre-release** only for a version that is genuinely not intended as a stable release.

## 6. Register or update Packagist

Submit the **package repository**, for example `https://github.com/wilycode/form`, at [Packagist Submit](https://packagist.org/packages/submit). Configure automatic GitHub updates and verify the new version appears.

Then test installation in an empty project:

```bash
mkdir -p /tmp/wilycode-package-check
cd /tmp/wilycode-package-check
composer require wilycode/form:^0.1
composer show wilycode/form
```

Replace `form` and `^0.1` with the name and compatible version you are publishing.

## Quick checklist

- [ ] Composer validation and PHPUnit pass.
- [ ] CI passes on the commit being released.
- [ ] Tag points to that tested commit.
- [ ] GitHub Release has clear notes.
- [ ] Packagist lists the intended version.
- [ ] Installation in a clean project works.

**Tip:** If only documentation changes after a release, you can update `main` without immediately publishing another version. The existing tag still refers to the original release snapshot.
