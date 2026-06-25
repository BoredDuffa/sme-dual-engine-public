# Investment-Grade Data Room Checklist

- Status: `data_room_required`
- Approved rows: 27 / 120
- Remaining row gaps: 108
- Company-universe request rows: 108
- Collection waves: 6
- Advertised sale listings: 225

## Summary

The dashboard is interactive and public-safe, but 108 source rows still need approved director/company evidence before investment-grade use.

## Downloads

- [Director export template](director_export_template.csv)
- [Director data runbook](director_data_runbook.md)
- [Company collection plan](company_universe_request/company-universe-collection-plan.md)
- [Company export request](company_universe_request/company-universe-export-request.csv)

## Required Data

### 1. Approved director/officer export

- Status: `required`
- Owner: CRO account holder or approved private company-data provider
- Required for: Director-age thresholds: 50+, 55+, 60+, 65+, and 70+ by company-universe row.
- Accepted format: CSV matching director_export_template.csv with company_number and director_age fields.
- Approval gate: validate_director_export.py passes with zero invalid active-director rows.
- Public/private rule: Do not publish the filled export; publish only aggregate validated company-universe rows.

### 2. Completed company-universe waves

- Status: `required`
- Owner: Research operator using the six published wave CSVs
- Required for: 108 company-universe rows that need approved counts or metadata.
- Accepted format: Completed company-universe-wave-N.csv rows with source_note, source_url, source_date, and approved_by filled.
- Approval gate: Each completed wave reconciles to the director-age import and has no count_mismatch rows.
- Public/private rule: Wave CSVs may stay public only while they contain request rows, not private director data.

### 3. CRO/company-number reconciliation

- Status: `required`
- Owner: CRO Open Services user or company registry data owner
- Required for: Company-number join keys and company-count baseline checks before aggregation.
- Accepted format: CRO company evidence CSV plus completed company-number join keys.
- Approval gate: Unique active-company counts reconcile to the company universe before approved rows are merged.
- Public/private rule: Publish aggregate company-count evidence only.

### 4. Sale-listing feed review

- Status: `ready`
- Owner: Origination analyst
- Required for: Keeping advertised-for-sale targets fresh and removing duplicates or irrelevant listings.
- Accepted format: Published sale listing CSV or refreshed source audit with URL, source, observed date, and listing metadata.
- Approval gate: Public sale refresh audit returns status ok and stale/duplicate rows are reviewed.
- Public/private rule: Public listing metadata and source URLs are publishable; private broker notes are not.

### 5. Approval metadata

- Status: `required`
- Owner: Investment or data-quality reviewer
- Required for: Moving rows from sample/incomplete to approved in the dashboard readiness gate.
- Accepted format: source_note, source_url, source_date, approved_by, and validation report references.
- Approval gate: Approved source collection reaches 120 of 120 rows with no placeholder or missing approval fields.
- Public/private rule: Approval metadata can be published when it identifies source class and reviewer without private personal data.

## Success Definition

- All 120 expected public-source rows are approved.
- All director-age threshold counts come from an approved private director/company export.
- No filled director-level export or private personal data is committed or published.
- Live dashboard verifier passes with collection_progress_status approved_collection_complete.
