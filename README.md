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

Close the PR and delete its branch before re-running a failing version.

## Results

| Version | Run | Result |
|---|---|---|
| 44.181.0 | [42382892877](https://github.com/linusfr/renovate-hermit-symlink-repro/actions/runs/42382892877) | `EEXIST`, no PR |
| 44.222.1 | [42383095280](https://github.com/linusfr/renovate-hermit-symlink-repro/actions/runs/42383095280) | `EEXIST`, no PR |
| 44.180.0 | [42383377126](https://github.com/linusfr/renovate-hermit-symlink-repro/actions/runs/42383377126) | [#1](https://github.com/linusfr/renovate-hermit-symlink-repro/pull/1) opened |
