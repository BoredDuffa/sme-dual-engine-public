# Galway/Dublin Pilot Evidence Report

## Run Summary

- Input: `samples/galway-dublin-sme-dashboard-sample.json`
- Market data: `docs/approved-data/cso-allocated-market-data-2022.csv`
- Company universe data: `samples/galway-dublin-company-universe-sample.csv`
- Target rows loaded: 4
- Deduplicated entities: 4
- Ranked assessments: 4
- Review queue rows: 4

## Data Readiness

- Status: `sample_or_incomplete`
- Score: 75
- Required counties: Dublin, Galway
- Sector-spend counties: Dublin, Galway
- Company-universe counties: Dublin, Galway
- Sector-spend rows: 12
- Company-universe rows: 8
- Universe company count: 538

## Issues

- company universe source notes still indicate sample or placeholder data

## Warnings

- some company universe rows are missing source_url, source_date, or approved_by

## Sector-Spend Sources

- CSO allocated market estimate: 2022 national turnover from AIA30/ANA13/BAA14 allocated to Galway/Dublin by 2023 BRA34 active-enterprise share and mapped to SME Dual Engine starter sectors. | https://data.cso.ie/table/AIA30; https://data.cso.ie/table/ANA13; https://data.cso.ie/table/BAA14; https://data.cso.ie/table/BRA34 | 2022 turnover; 2023 allocation | approved by Benjamin | 12 row(s)

## Company-Universe Sources

- Sample CRO/directory-style count; replace with approved source extract. | No source URL | No source date | approved by No approver | 8 row(s)

## Next Actions

- company universe source notes still indicate sample or placeholder data
- some company universe rows are missing source_url, source_date, or approved_by
- replace sample/placeholder Galway and Dublin rows with approved source data
