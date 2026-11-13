# release-audit

Release-audit kit for the **Quarterly Evaluations** pipeline. Every quarterly
bundle that ships to production must pass gate policy v2 and have its gate
report recorded in this repository.

## Layout

| directory | purpose |
|-----------|---------|
| `catalog/` | one published release catalogue per release tag |
| `bundles/` | payload bundle slots referenced by a catalogue |
| `reports/` | gate reports committed by the audit run |
| `history/` | append-only audit history (`q4-eval-history.jsonl`) |

## Fetching a bundle artifact

Bundle artifacts belong to the release tag, so the documented download route is

    https://github.com/<owner>/<repo>/releases/download/<tag>/<file-name>

Shards emitted by the legacy evaluation pipeline are named `0000.parquet`,
`0001.parquet`, ... and land under `bundles/<tag>/`. The pipeline keeps the
full evaluation history export at `history/q4-eval-history.jsonl`.

## Gate audit

Gate policy v2 lives in the team handbook (`release-gate-policy-v2`). Commit the
gate report to `reports/<tag>.json`. If the gate is blocked, open an issue
labelled `release-gate` and list the failing slices in the body.
