# Prayer data distribution tree

Layout for published catalog and immutable annual package ZIP artifacts.

```text
prayer/
  catalog.json
  <countryCode>/
    <year>/
      <packageVersion>/
        prayer-<countryCode>-<year>-<packageVersion>.zip
```

## Rules

- Publish a ZIP only when its destination path does not already exist.
- Never overwrite bytes for an existing `packageVersion` path.
- Supersede defects with a new `packageVersion` and update `catalog.json`.
- Keep this tree free of source builders, evidence, and app code.

Artifacts are JAKIM-derived and verified by Project Noor tooling before upload.
Clients verify pinned SHA-256 and inner package integrity.
