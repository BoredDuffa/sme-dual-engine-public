# Director Data Operator Runbook

- Status: `director_data_required`
- Approved rows: 27 / 120
- Remaining row gaps: 108
- Company-universe request rows: 108

## Why There Are So Few Companies

The public dashboard only promotes rows that pass approved evidence and director-age gates. Current approved coverage is 27 of 120 rows; 108 rows still need an approved director/company export.

## Required Inputs

- [Director export template](director_export_template.csv): Header-only schema with 14 fields for the private director-level export.
- [Company universe export request](company_universe_request/company-universe-export-request.csv): 108 Galway/Dublin rows that need company-number-backed director-age counts.
- [CRO company evidence](cro_company_evidence/cro-company-count-evidence.csv): Company-count evidence to reconcile against the director export before approval.

## Commands

### Preflight Director Export

```bash
python3 scripts/validate_director_export.py --director-export path/to/approved-director-export.csv --strict
```

- Output: `tmp/director-export-validation/director-export-validation.json and director-export-review.csv`

### Aggregate Director Age Import

```bash
python3 scripts/build_director_age_import_from_export.py --director-export path/to/approved-director-export.csv --company-request company_universe_request/company-universe-export-request.csv --source-note "Approved director export joined by company number." --source-url https://cro.ie/services-and-help/access-to-cro-data/ --source-date YYYY-MM-DD --approved-by "Name" --director-export-source-id cro-bulk-YYYY-MM-DD --output-csv tmp/director-age-import/director-age-import.csv --report-json tmp/director-age-import/director-age-import-report.json --review-csv tmp/director-age-import/director-age-import-review.csv --strict
```

- Output: `tmp/director-age-import/director-age-import.csv plus report and review CSV`

### Validate Approved Import

```bash
python3 scripts/validate_director_age_import.py --input tmp/director-age-import/director-age-import.csv --output-company tmp/director-age-import/approved-company-universe-update.csv --strict
```

- Output: `tmp/director-age-import/approved-company-universe-update.csv`

## Acceptance Gates

- Director export validator returns status `ready` with zero invalid rows.
- active_valid_row_count is greater than zero and unique_company_count reconciles with the requested company universe.
- Aggregation report returns status `ready`; any count_mismatch rows are reviewed before merge.
- Director-age import validator returns status `ready` and writes approved-company-universe-update.csv.
- Only aggregate approved company-universe rows are published; a filled director export is never committed or published.

## Private Data Policy

- A filled director export may contain non-public officer or personal data.
- Keep the filled export in a private local or approved internal location.
- Publish only the header template, validation summaries, and aggregate approved company rows after approval metadata is complete.

## Operator Next Steps

1. Obtain a director-level CRO/CORE/bulk export keyed by company number for the 108 request rows.
2. Preflight the director-level export with `scripts/validate_director_export.py --strict` before aggregation.
3. Join the director-level export to the existing CRO company-count evidence by company number and active appointment status.
4. Aggregate active companies by county, local area, and sector into director_50_plus through director_70_plus threshold counts.
5. Validate the completed import with `scripts/validate_director_age_import.py --strict` before merging.
6. Merge only rows with complete threshold counts and approval metadata into the approved company-universe CSV.
