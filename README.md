# AILux release manifests

This repo holds **signed manifest.json** files for the AILux update daemon.

## What this repo contains

- One GitHub Release per AILux version (`v0.1.0`, `v0.1.1`, ...).
- Each release has exactly one asset: `manifest.json`, signed with ed25519.
- Nothing else. No code, no Docker images, no executables.

## Why the manifests are public

Manifests are short-lived JSON pointers (versions, SHAs, image digests) that
must be fetchable by every customer's update daemon. They contain no secrets.
Each manifest is signed with the AILux release private key (held offline by
the maintainer). The daemon refuses any manifest with an invalid signature.

Publishing here does NOT publish source code. Source code lives in
`TFBizzle/ailux-platform` and stays private.

## Tag protection

Tags matching `v*` are protected: cannot be deleted or moved. To "fix" a
broken release, publish a new version.

## How releases are published

By the maintainer, locally, via `tools/release-local.ps1` in the
`ailux-platform` repo. The signing key never leaves the maintainer's machine.
No GitHub Actions secrets, no automation.
