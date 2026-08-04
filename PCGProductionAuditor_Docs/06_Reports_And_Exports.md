# 06 — Reports and Exports

PCG Production Auditor exports the currently visible findings as CSV or JSON.

Active severity, category, and text filters are respected.

---

## Export Workflow

1. Run **Scan Level** or **Scan Selected**.
2. Apply the required filters.
3. Confirm the visible result list contains the findings that should be reported.
4. Select **Export CSV** or **Export JSON**.
5. Choose the output path.
6. Open the exported file and confirm the report was created successfully.

Cleared or filtered-out findings are not included in the exported result set.

---

## CSV Reports

CSV reports are intended for:

- spreadsheet review
- issue tracking preparation
- team handoff
- manual sorting and filtering
- archived audit snapshots

### Encoding and Escaping

CSV output uses:

- UTF-8 with BOM
- RFC 4180-compatible field escaping

This supports stable handling of commas, quotes, line breaks, and international text in compatible spreadsheet applications.

---

## JSON Reports

JSON reports are intended for:

- automated processing
- CI/CD workflows
- custom reporting tools
- structured audit archives
- integration with project scripts

### Encoding

JSON output uses UTF-8 without BOM.

### Versioned Schema

The JSON report schema is versioned so that downstream tools can identify and handle the report structure consistently.

Top-level fields include:

| Field | Purpose |
|---|---|
| `findings_count` | Number of findings included in the report |
| `source_plugin` | Plugin that generated the report |
| `plugin_version` | PCG Production Auditor version |
| `engine_version` | Unreal Engine version used for the audit |
| `timestamp` | Report generation time |
| `scan_mode` | Audit mode used for the report |
| `findings` | Structured finding entries |

Editor and commandlet exports use a consistent report structure.

---

## Filtered Export Behavior

The export uses the current visible result set.

Examples:

- Disable **Info** to export only Errors and Warnings.
- Disable **Component Audit** to export only Graph Audit findings.
- Search for a target name to export findings associated with that visible target set.

Before exporting, clear the search field when a complete report is required.

---

## Recommended Report Naming

Use a consistent naming convention, for example:

```text
PCGAudit_ProjectName_MapName_2026-08-04.json
PCGAudit_ProjectName_SelectedGraphs_2026-08-04.csv
```

For automated workflows, include build, branch, map, or commit information when your CI/CD system provides it.

---

## Report Validation

After export:

1. Confirm the file exists.
2. Confirm the finding count matches the intended visible results.
3. Confirm the selected format opens correctly.
4. For JSON automation, validate the expected top-level fields before further processing.
5. Store the plugin version with archived reports.

---

## Export Failures

See [08 — Troubleshooting](08_Troubleshooting.md) when:

- the report contains fewer findings than expected
- the exported file is empty
- a commandlet returns exit code `2`
- the output path cannot be written

---

Previous: [05 — Settings and Profiles](05_Settings_And_Profiles.md) · [Documentation Index](INDEX.md) · Next: [07 — Commandlet and CI/CD](07_Commandlet_And_CI_CD.md)
