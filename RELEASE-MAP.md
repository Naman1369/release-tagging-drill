# Release Map

This map ties each release tag to an immutable commit and a deployment record. Dates are the commit dates for the historical commits selected as release baselines.

| Version (tag) | Commit (short hash) | Date | What Shipped |
| --- | --- | --- | --- |
| `v1.0.0` | `4febcc6` | 2026-06-06 | Repository initialization; established the first tracked baseline for the checkout-service exercise. |
| `v1.1.0` | `ff1fb9a` | 2026-06-06 | Added the dummy Checkout service and its initial deployment-history, incident-log, release-notes, and changelog records. |
| `v1.1.1` | `82535d9` | 2026-06-06 | Updated the Checkout service placeholder implementation while preserving the service's documented exercise behavior. |

## Rollback traceability

To identify the release currently at the top of the sortable release history and roll back to the previous known-good release, run:

```bash
git tag --sort=-v:refname        # the sortable release history
git checkout v1.1.0              # roll back to the last known-good tag, then redeploy
```

The annotated tags provide stable names for exact commits, and this map explains what each commit shipped. Unlike the original `release_2`, `latest-good`, and `v2-final-FINAL` references, the ordered semantic sequence makes the current release and its rollback target precise and reproducible.
