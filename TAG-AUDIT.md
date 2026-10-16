# Tag Audit

## Findings

The repository currently has no Git tag references (`git tag` returns no entries). The names below are nevertheless used in the inherited deployment records and old release notes, so they are evidence of the release-history problems the team must correct.

| Evidence | Problem | Team impact | Rollback and traceability risk |
| --- | --- | --- | --- |
| `v1.4.2` | A release-looking tag is mentioned in the deployment history, but no `v1.4.2` ref exists in this clone. | Operators cannot resolve the name to a commit or inspect exactly what was deployed. | A responder cannot check out the supposed production version, making rollback guesswork. |
| `version-1.0` | The `version-1.0` name does not follow a complete semantic version and uses a different prefix/style from other records. | Sorting and tooling cannot reliably compare it with patch releases. | It is unclear whether this means `1.0.0`, a major line, or an informal milestone, so an audit cannot establish release order. |
| `release_2` | The incident log identifies `release_2` as a lightweight tag with no annotation. | The name does not communicate a semantic version or what changed. | The documented emergency rollback pointed to an older unsupported commit, with no embedded release message to verify its suitability. |
| `1.5.0` | The old notes use a bare numeric tag without the required `v` prefix, and no matching ref is present. | Teams and automation must special-case multiple naming conventions. | A command such as `git tag --sort=-v:refname` produces an inconsistent release list, and the intended deployment commit cannot be proven. |
| `v2-final-FINAL` | The tag contains duplicated final-status wording and is not a valid stable release format. | The name is ambiguous and cannot be used as a predictable version identifier. | Responders cannot tell whether it supersedes `v1.5.0` or whether another “final” build exists. |
| `latest-good` | Production history records deployment and rollback using a moving, descriptive label rather than a version. | The label can be repointed without making the deployment record self-contained. | A future checkout of `latest-good` may not reproduce the commit that was known good during the incident. |
| `stable-build` and `patch-new` | These names describe intent rather than an immutable release version and appear without commit/deployment records. | Release discovery depends on tribal knowledge instead of an ordered history. | There is no deterministic previous release to compare, audit, or redeploy. |

## Remediation

The new release history uses annotated `vMAJOR.MINOR.PATCH` tags, each tied to a specific historical commit and documented in [RELEASE-MAP.md](./RELEASE-MAP.md). The convention and pre-release policy are defined in [VERSIONING.md](./VERSIONING.md), while rollback targets and shipped changes are recorded in [RELEASES.md](./RELEASES.md).
