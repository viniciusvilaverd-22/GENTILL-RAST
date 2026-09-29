# REST Gentill — Public Portfolio Assurance

The public repository is intentionally designed as a **documentation-only portfolio surface**.

Its goal is to demonstrate architecture, product thinking, security and engineering decisions without exposing private product source code or operational material.

## Automated guard

The repository includes a GitHub Actions workflow:

```text
.github/workflows/publication-guard.yml
```

It runs on pushes and pull requests targeting `main`.

## What the guard rejects

### Product source directories

The public repository must not contain private product implementation directories such as:

- application source;
- endpoint-agent source;
- service source;
- infrastructure source;
- private integration code;
- internal tests and operational tools.

### Generated binaries

The guard rejects common generated or sensitive artifact formats such as:

- APK;
- AAB;
- EXE;
- DLL;
- MSI/MSIX;
- database dumps;
- local databases;
- private key containers.

### Runtime environment files

Real runtime `.env` files are not accepted.

Only safe examples belong in public documentation when necessary.

### Credential-like patterns

The workflow checks for obvious credential signatures before accepting a publication change.

### Attribution hygiene

The public portfolio is also scanned for unwanted assistant/tool attribution markers.

The portfolio should represent the project and its author — not the tooling used during development.

## Human review model

Automated checks do not replace review.

The publication model expects:

1. documentation-first changes;
2. public-safe architecture content;
3. no internal endpoints or secrets;
4. no operational evidence with sensitive context;
5. explicit review before expanding the public surface.

## CODEOWNERS

Public content is owned by the project author.

This keeps review responsibility explicit even in a documentation-only repository.

## Security model

The public assurance layer works alongside:

- [Security Model](SECURITY_MODEL.md)
- [Threat Model](THREAT_MODEL.md)
- [Data Ownership Map](DATA_OWNERSHIP.md)

## Principle

> A portfolio can demonstrate engineering depth without exposing private implementation.

That principle is enforced by repository structure, documentation boundaries and automated checks.
