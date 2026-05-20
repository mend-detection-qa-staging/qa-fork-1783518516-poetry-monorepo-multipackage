# poetry-monorepo-multipackage

Tests *Poetry monorepo / multi-package layout*: a single root `poetry.lock` covering
two sub-packages under `packages/`.

## Structure

```
.
├── pyproject.toml              # root workspace
├── poetry.lock                 # shared lockfile
└── packages/
    ├── service-a/
    │   └── pyproject.toml      # requests + httpx
    └── service-b/
        └── pyproject.toml      # flask + click
```

## Key assertions

- All 4 cross-package direct deps appear in the merged dep tree
- Transitives from both sub-packages are resolved
- Coverage gap: no prior Poetry test covers multi-manifest monorepo layout
