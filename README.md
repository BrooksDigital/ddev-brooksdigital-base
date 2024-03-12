[![tests](https://github.com/BrooksDigital/ddev-brooksdigital-base/actions/workflows/tests.yml/badge.svg)](https://github.com/BrooksDigital/ddev-brooksdigital-base/actions/workflows/tests.yml)
![project is maintained](https://img.shields.io/maintenance/yes/2024.svg)

# ddev-brooks-digital-base

<!-- toc -->

- [What is ddev-brooksdigital-base?](#what-is-ddev-brooksdigital-base)
- [ddev installation/use](#ddev-installationuse)

<!-- tocstop -->

## What is ddev-brooksdigital-base?

This is our main ddev add-on, used to have an opinionated configuration for all
of our projects.

It adds other addons, have useful shortcuts and things we want to have on all
projects. This README will also serve as our central documentation for
ddev-relative work.

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
