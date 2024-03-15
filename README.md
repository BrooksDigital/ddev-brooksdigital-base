[![tests](https://github.com/BrooksDigital/ddev-brooksdigital-base/actions/workflows/tests.yml/badge.svg)](https://github.com/BrooksDigital/ddev-brooksdigital-base/actions/workflows/tests.yml)
![project is maintained](https://img.shields.io/maintenance/yes/2024.svg)

# ddev-brooks-digital-base

<!-- toc -->

- [What is ddev-brooksdigital-base?](#what-is-ddev-brooksdigital-base)
- [Framework-specific documentation](#framework-specific-documentation)
  * [Drupal](#drupal)
    + [Dev settings](#dev-settings)
    + [ahoy commands](#ahoy-commands)
- [ddev features](#ddev-features)
  * [Dev additions](#dev-additions)
  * [Readme](#readme)
  * [Shell additions](#shell-additions)
- [ddev installation/use](#ddev-installationuse)

<!-- tocstop -->

## What is ddev-brooksdigital-base?

This is our main ddev add-on, used to have an opinionated configuration for all
of our projects.

It adds other addons, have useful shortcuts and things we want to have on all
projects. This README will also serve as our central documentation for
ddev-relative work.

## Framework-specific documentation

### Drupal

#### Dev settings

There's a common
[settings.dev.php](brooksdigital/base/assets/drupal/settings.dev.php) included
in this addon that provide general dev default settings for all of our Drupal
projects.

To use this file you need to add the following snippet to your main
`settings.php` file:

```php
// include for dev settings managed by ddev-brooksdigital-base.
$dev_settings = '/var/www/html/.ddev/brooksdigital/base/assets/drupal/settings.dev.php';
if (getenv('IS_DDEV_PROJECT') == 'true' && is_readable($dev_settings)) {
  require $dev_settings;
}
```

**The above should be after all main includes and before including
`settings.local.php`.**

If you need to override any of this setting like the stage file proxy url or
anything specific to the project that you wish to commit and maintain on the
project repo you should create a `web/sites/default/settings.dev.php`, commit it
and include it after the above and before `settings.local.php` with:

```php
// Project dev settings.
$project_dev_settings = $app_root . '/' . $site_path . '/settings.dev.php';
if (getenv('IS_DDEV_PROJECT') == 'true' && is_readable($project_dev_settings)) {
  require $app_root . '/' . $site_path . '/settings.dev.php';
}
```

#### ahoy commands

- `ahoy drupal drush:uli`: A fancier drush uli

## ddev features

If you don't have `ddev` installed, read
[What is ddev-brooksdigital-base?](#what-is-ddev-brooksdigital-base) below.

This add-on adds the following add-ons, refer to the README of each for more
details.

### Dev additions

- https://github.com/hanoii/ddev-ahoy: Adds `ahoy` to namespace common tasks
  across projects.
- Runs any executable script on
  `.ddev/brooksdigital/base/hooks/post-import-db.d/` on ddev's post-import-db
  hook through our own
  [`.ddev/brooksdigital/base/hooks/post-import-db.sh/`](brooksdigital/base/hooks/posrt-import-db.sh).
  This allows for the same scripts to be run from within the container, used by
  other of our addons and/or projects' own scripts.

### Readme

- https://github.com/hanoii/ddev-readme: Format README.md through some
  opinionated defaults.

### Shell additions

- https://github.com/hanoii/ddev-starship - A nice prompt!
- https://github.com/hanoii/ddev-fish - Fish shell
- https://github.com/hanoii/ddev-fzf - Fuzzy seach tool

## ddev installation/use

1. Install Docker for Mac/Windows. ddev also supports and [recommends
   colima][colima]. [Orbstack][orbstack] is a great tool as well, also
   supported.
1. Give your Docker installation reasonable resources according to your
   computer. (ddev recommends 4 cpu and 6gb of ram - if you can spare more,
   probably worth it)
1. Install [ddev][ddev-install].
1. If on Mac/Windows, run `ddev config global --mutagen-enabled` to enable
   mutagen globally for [performance][ddev-performance] reasons.
1. Clone the project repo and `cd` into it
1. Run `ddev start` to start everything.
1. Refer to the project's README for more details.

[orbstack]: https://orbstack.dev/
[colima]:
  https://ddev.readthedocs.io/en/latest/users/install/docker-installation/#colima
[ddev-install]: https://ddev.readthedocs.io/en/stable/
[ddev-performance]:
  https://ddev.readthedocs.io/en/stable/users/install/performance/

**Contributed and maintained by
[@BrooksDigital](https://github.com/BrooksDigital)**
