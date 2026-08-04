# 07 — Commandlet and CI/CD

PCG Production Auditor includes the `PCGAudit` commandlet for automated audits without opening the interactive Unreal Editor.

## Basic Example

```text
UnrealEditor-Cmd.exe Project.uproject -run=PCGAudit -Map=/Game/Maps/MyLevel -Output=audit.json -Format=json -Rules=GA-01,CA-02 -Severity=Error,Warning
```

Replace the editor executable, project path, map, and output path with values appropriate for the current environment.

---

## Main Options

| Option | Purpose | Example |
|---|---|---|
| `-Map=` | Map to load and audit | `-Map=/Game/Maps/MyLevel` |
| `-Output=` | Report output path | `-Output=Saved/Audits/audit.json` |
| `-Format=` | Report format | `-Format=json` or `-Format=csv` |
| `-Rules=` | Comma-separated rule IDs | `-Rules=GA-01,GA-14,CA-01` |
| `-Severity=` | Comma-separated severity levels | `-Severity=Error,Warning` |

The commandlet respects rules disabled through **Project Settings → Plugins → PCG Production Auditor**.

---

## Exit Codes

| Exit Code | Meaning |
|---:|---|
| `0` | No matching findings were detected |
| `1` | Matching findings were detected |
| `2` | Invalid arguments, map loading failure, or report export failure |

Exit code `1` is an audit result, not a commandlet crash. CI/CD logic should decide whether matching findings fail the pipeline.

---

## Example — Error and Warning Gate

```text
UnrealEditor-Cmd.exe Project.uproject -run=PCGAudit -Map=/Game/Maps/Production -Output=Saved/Audits/Production.json -Format=json -Severity=Error,Warning
```

Possible pipeline behavior:

- `0` — continue the pipeline
- `1` — fail the validation stage or mark it for review
- `2` — fail the commandlet stage because the audit could not complete correctly

---

## Example — Selected Rule Set

```text
UnrealEditor-Cmd.exe Project.uproject -run=PCGAudit -Map=/Game/Maps/Production -Output=Saved/Audits/GraphStructure.csv -Format=csv -Rules=GA-01,GA-02,GA-06,GA-11,GA-14,GA-15 -Severity=Error,Warning
```

This example requests a focused graph-structure report.

---

## Example — Component Configuration Review

```text
UnrealEditor-Cmd.exe Project.uproject -run=PCGAudit -Map=/Game/Maps/Production -Output=Saved/Audits/Components.json -Format=json -Rules=CA-01,CA-02,CA-04,CA-08,CA-09,CA-10 -Severity=Error,Warning
```

---

## CI/CD Recommendations

1. Store audit configuration in the project.
2. Keep rule IDs stable in pipeline scripts.
3. Use JSON for structured automation and CSV for human review.
4. Archive reports with the build or commit that produced them.
5. Treat exit code `2` separately from detected findings.
6. Start with Error findings as the blocking condition.
7. Add Warning gates only after the team has agreed on the expected standard.
8. Review experimental `GA-09` findings manually before using them as a strict pipeline gate.

---

## Commandlet Scope

The commandlet audits the specified map using the enabled project rule configuration and optional command-line filters.

Use editor selection scans for asset-focused interactive work. Use the commandlet for repeatable map-based automation.

---

## Diagnosing Commandlet Problems

See [08 — Troubleshooting](08_Troubleshooting.md) when:

- the map cannot be loaded
- the report is not created
- the command returns exit code `1` unexpectedly
- the command returns exit code `2`
- a requested rule does not appear in the report

---

Previous: [06 — Reports and Exports](06_Reports_And_Exports.md) · [Documentation Index](INDEX.md) · Next: [08 — Troubleshooting](08_Troubleshooting.md)
