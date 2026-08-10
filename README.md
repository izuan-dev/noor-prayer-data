# noor-prayer-data

Public distribution host for verified **Project Noor** prayer-data artifacts.

This repository publishes downloadable annual prayer packages for clients.
**Source code, builders, evidence, and canonical package JSON remain in a
separate private repository.**

## Trust model

- Artifacts are **JAKIM-derived** and verified by Project Noor tooling before
  publication.
- Clients must verify the **outer ZIP SHA-256** against an app-embedded trust
  pin, then verify **inner package integrity** (manifest digests / structure).
- Catalog metadata alone is not a trust root.

## Immutability

- Artifact paths are **write-once**.
- The same `packageVersion` must **never** change bytes after publication.
- Bad artifacts are **superseded** with a new `packageVersion`, never
  overwritten in place.
- `prayer/catalog.json` may evolve independently (add or yank entries).

## Serving

Static files are intended for anonymous HTTPS GET via
`raw.githubusercontent.com` (direct `200`, no redirect).
**GitHub Releases are not required** for distribution and should not be used
as the client download URL.

Never rewrite an existing artifact path after publication.

## Path convention

```text
prayer/catalog.json

prayer/<countryCode>/<year>/<packageVersion>/
  prayer-<countryCode>-<year>-<packageVersion>.zip
```

Example (not yet published):

```text
prayer/MY/2026/2026.nationwide.1/
  prayer-MY-2026-2026.nationwide.1.zip
```
