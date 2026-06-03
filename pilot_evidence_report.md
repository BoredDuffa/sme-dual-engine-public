# Galway/Dublin Pilot Evidence Report

## Run Summary

- Input: `/Users/benjaminfalkenburg/repo-reorg/principia-split/SME-Dual_Engine/samples/galway-dublin-sme-dashboard-sample.json`
- Market data: `/Users/benjaminfalkenburg/repo-reorg/principia-split/SME-Dual_Engine/samples/galway-dublin-market-data-sample.csv`
- Company universe data: `/Users/benjaminfalkenburg/repo-reorg/principia-split/SME-Dual_Engine/samples/galway-dublin-company-universe-sample.csv`
- Target rows loaded: 4
- Deduplicated entities: 4
- Ranked assessments: 4
- Review queue rows: 4

## Data Readiness

- Status: `sample_or_incomplete`
- Score: 50
- Required counties: Dublin, Galway
- Sector-spend counties: Dublin, Galway
- Company-universe counties: Dublin, Galway
- Sector-spend rows: 6
- Company-universe rows: 8
- Universe company count: 538

## Issues

- sector spend source notes still indicate sample or placeholder data
- company universe source notes still indicate sample or placeholder data

## Warnings

- some sector spend rows are missing source_url, source_date, or approved_by
- some company universe rows are missing source_url, source_date, or approved_by

## Sector-Spend Sources

- Sample Chamber-style data; replace with approved Dublin source. | No source URL | No source date | approved by No approver | 3 row(s)
- Sample Chamber-style data; replace with approved Galway source. | No source URL | No source date | approved by No approver | 3 row(s)

## Company-Universe Sources

- Sample CRO/directory-style count; replace with approved source extract. | No source URL | No source date | approved by No approver | 8 row(s)

## Next Actions

- sector spend source notes still indicate sample or placeholder data
- company universe source notes still indicate sample or placeholder data
- some sector spend rows are missing source_url, source_date, or approved_by
- some company universe rows are missing source_url, source_date, or approved_by
- replace sample/placeholder Galway and Dublin rows with approved source data
