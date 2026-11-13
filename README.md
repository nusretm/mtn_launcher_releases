# RemVibe Releases

Public binary distribution repository for approved RemVibe application and independently deployable component releases.

**This repository distributes release artifacts; it is not a source-code, build-definition, or private-identity repository.**

## Repository responsibilities

| Repository | Responsibility |
| --- | --- |
| `nusretm/remvibe_networking` | Owns Rust Networking source and FFI ABI/build |
| `nusretm/remvibe_updates` | Owns the central project catalog and authorized release-selection metadata |
| `nusretm/remvibe_update_center` | Owns release verification, installation, update and recovery orchestration |
| **`nusretm/remvibe_releases`** | Hosts reviewed, versioned downloadable GitHub Release assets |

## First planned component

**RemVibe Networking — Windows x64 native FFI DLL** (`remvibe_networking_ffi.dll`).

The first release will be prepared manually from an immutable `remvibe_networking` source commit, with exact file digests, platform/architecture, ABI compatibility and an approved authorization/signature contract. The release has **not** been created by this repository preparation step.

Consumers must select a **compatible, authorized** version, not blindly download the newest asset. A downloaded DLL is verified before it is exposed at a stable local path. An in-use native library is not replaced in place; its host process must be quiesced/restarted as required by the Update Center component-update contract.

## Security and distribution limits

- **Never publish RemVibe Update Center Server source, Server AOT release, Noise NK private key, credential, signing key or private operational data here.**
- Public GitHub visibility means uploaded release assets can be downloaded by anyone.
- A SHA-256 checksum detects accidental or malicious modification only when the expected hash is authenticated. It does **not** prove publisher identity by itself.
- Follow the accepted release-signature, provenance and package validation mechanisms in Update Center; do not introduce an incompatible manifest schema in this repository.
- No automatic installation of unsigned or unapproved pilot artifacts.

## Publication

See [release preparation and verification policy](docs/RELEASE_POLICY.md).

> **Migration note:** This repository was renamed from `mtn_launcher_releases`. Legacy MTN Launcher releases, tags or branches must not be interpreted as RemVibe releases. Legacy cleanup is a separate explicitly reviewed action; no existing release is republished or relabeled automatically.
