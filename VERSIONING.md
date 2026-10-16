# Versioning Convention

## Semantic versioning

Production releases use Semantic Versioning:

- **MAJOR** increments for incompatible or breaking changes. Example: `v1.4.2` -> `v2.0.0` when an API or checkout contract breaks.
- **MINOR** increments for backward-compatible functionality. Example: `v1.4.2` -> `v1.5.0` when a new optional checkout capability is added.
- **PATCH** increments for backward-compatible bug fixes. Example: `v1.4.2` -> `v1.4.3` when a checkout timeout is fixed without changing the public contract.

## Tag names

Every stable release uses the exact pattern `vMAJOR.MINOR.PATCH`, with numeric non-negative components and a lowercase `v` prefix. For example, `v1.5.0`.

## Annotated release tags

Release tags are **annotated**, not lightweight. An annotation records who created the tag, when it was created, and a meaningful release message in Git's tag object, which makes audits and release verification reproducible.

Create one with:

```bash
git tag -a v1.5.0 -m "Release 1.5.0: add optional checkout capability"
```

The tag must point to the reviewed release commit and must be pushed with `git push origin --tags`.

## Pre-releases

Release candidates and betas append a dot-separated identifier, such as `v1.5.0-rc.1` or `v1.5.0-beta.1`. Pre-release tags are tested but are not production releases. SemVer ordering places them before the corresponding final version, so `v1.5.0-rc.1 < v1.5.0`; the final `v1.5.0` replaces the candidate once approved.
