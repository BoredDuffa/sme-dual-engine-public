# Galway/Dublin Company Universe Export Request

- Status: `ready`
- Request rows: 108
- Galway rows: 54
- Dublin rows: 54

## Acceptance Rule

- Approve only when company_count and all five director-age threshold counts come from an approved backend/director/CRO account-holder export and source_note, source_url, source_date, and approved_by are filled.

## Source Notes

- CRO address-search URLs are included for collection triage.
- CRO Open Services address search does not expose director-age bands; use an approved backend/director export or CRO account-holder data for all director thresholds.
- Keep county, local_area, region_label, and gics_sector unchanged in completed exports.
- Fill source_note, source_url, source_date, and approved_by before merge or dashboard approval.
