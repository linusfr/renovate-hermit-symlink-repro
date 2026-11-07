# renovate-hermit-symlink-repro

Minimal reproduction: Renovate 44.181.0 and later fail every Hermit update with

```
EEXIST: file already exists, symlink '.jq-<new>.pkg' -> '…/bin/jq'
```

`bin/` pins `jq` 1.7, so Renovate proposes an update.

## Reproduce

Run the `renovate` workflow (Actions → renovate → Run workflow):

- default version (44.222.1): the update fails with `EEXIST`, no PR is opened
- `44.180.0`: the update PR is opened
