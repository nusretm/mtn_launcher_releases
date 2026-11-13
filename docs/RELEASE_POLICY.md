# RemVibe Releases — Release policy

## Purpose and scope

This **public** GitHub repository is the artifact distribution endpoint only. Source ownership, private catalog selection and Update Center verification/installation remain in their existing repositories. Do not duplicate the `remvibe_updates` catalog.

## Manual first-release gate: RemVibe Networking FFI, Windows x64

1. Select an immutable `nusretm/remvibe_networking` source commit and the intended component version.
2. Build from that source with the approved Windows x64 toolchain; record the exact build identity and result of the existing ABI/export/functional checks.
3. Verify the native library file, PE/x64 architecture, public ABI version and dependency/host compatibility. The presently documented public C ABI epoch is **2**; confirm the actual build's ABI at publication time.
4. Produce the exact artifact inventory (file names, sizes, SHA-256) and the approved signed release authorization metadata using the **existing** Update Center trust contract. A checksum file alone is not release authorization.
5. Review the candidate tag, filename and manifest compatibility with `remvibe_updates` and Update Center **before** publishing. Do not guess a new schema, tag policy or signing identity.
6. Publish the approved, non-secret assets as GitHub Release assets on this repository. Do not commit binary artifacts into Git history merely to distribute them.
7. Verify the published bytes against the reviewed inventory, then test the consumer's **compatible-version selection → download → verify → local prepare → explicit-path load** behavior.
8. Preserve a previous verified component version for rollback. Do not overwrite an in-use DLL or silently replace an incompatible ABI; host restart/quiescence requirements are controlled by the consuming application.

## Distribution rules

- No Server source code, Server AOT binaries, static Server private key, private key-containing build output, credentials or signing secrets.
- Never place an access token in a client/console binary. GitHub public releases need no token for public asset access.
- No unconditional `latest` selection; selection is by product/component identity, platform/architecture, verified compatibility, authorized version and signature.
- Until the signed authorization and end-to-end update path are verified, any uploaded test release must be clearly designated a **manual pilot**, not an unattended production update.
- Do not change accepted application, native ABI, install/update, rollback or trust contracts without explicit user approval.

## Repository reset boundary

The legacy `mtn_launcher_releases` README has been replaced on this preparation branch. Historical MTN Launcher published releases/tags and the old documentation branch are **not** deleted by this preparation. Removing them is a separate, potentially disruptive operation that needs asset/consumer impact verification and explicit confirmation.
