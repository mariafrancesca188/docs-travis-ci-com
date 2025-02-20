---
title: Build a Nix Project
layout: en

---


This guide covers build environment and configuration topics specific to Nix projects. Please make sure to read our [Onboarding](/user/onboarding/) and [General Build configuration](/user/customizing-the-build/) guides first.


## Community-Supported Warning

Travis CI support for Nix is contributed by the community and may be removed
or altered at any time. If you run into any problems, please report them in the
[Travis CI issue tracker](https://github.com/travis-ci/travis-ci/issues/new?labels=community:nix)
and cc [@garbas](https://github.com/garbas), [@matthewbauer](https://github.com/matthewbauer), and [@grahamc](https://github.com/grahamc).

## Overview

To install the Nix store and set up a basic single-user profile, set the `language` key in `.travis.yml` to `nix`.

```yaml
language: nix
```
{: data-file=".travis.yml"}

The default channel for `nixpkgs` will be `nixpkgs-unstable`.

## Tools Available

The following command line tools are available in the Nix environment:

- nix
- nix-build
- nix-channel
- nix-collect-garbage
- nix-copy-closure
- nix-daemon
- nix-env
- nix-instantiate
- nix-prefetch-url
- nix-shell
- nix-store

## Default Nix Version

This installs Nix 2.3.6 using [https://nixos.org/releases/nix/nix-2.3.6/install](https://nixos.org/releases/nix/nix-2.3.6/install). You may specify a different version of Nix installer with the `nix:` key in your `.travis.yml`:

```yaml
language: nix
nix: 2.3.6
```
{: data-file=".travis.yml"}


> Note: This option supports all Nix releases, starting with version 1.11.16.

## Default Target

The default build script is `nix-build` which builds everything in the `default.nix` file of the repository root. This can be overridden by setting the `script` key in the `.travis.yml` file. For example,

```yaml
language: nix
script: nix-build -A tarball release.nix
```
{: data-file=".travis.yml"}

The above configuration will attempt to build the attribute "tarball" from the Nix expression in release.nix.

## Nix Manual

More information on writing Nix expressions and how each of the above tools works is available in the [Nix manual](https://nixos.org/nix/manual/).

## Build Config Reference

You can find more information on the build config format for [Nix](https://config.travis-ci.com/ref/language/nix) in our [Travis CI Build Config Reference](https://config.travis-ci.com/).
