# PCG Production Auditor — Documentation Index

**Version:** 1.0.0 · **Engine:** Unreal Engine 5.8 · **Plugin type:** Editor-only C++ plugin

PCG Production Auditor provides a production-ready audit workflow for Unreal Engine's native PCG framework. It scans PCG Graphs and PCG Components, reports structured findings, and supports repeatable review through the editor, report exports, and the `PCGAudit` commandlet.

---

## Documentation

| # | Document | Contents |
|---|---|---|
| 01 | [Installation](01_Installation.md) | Requirements, installation, activation, first launch, and removal |
| 02 | [Quick Start](02_Quick_Start.md) | Run the first scan, review findings, navigate to targets, and export results |
| 03 | [Editor Workflow](03_Editor_Workflow.md) | Scan modes, filters, findings, navigation, context menus, and result clearing |
| 04 | [Audit Rule Reference](04_Audit_Rule_Reference.md) | All 24 Graph Audit and Component Audit rules |
| 05 | [Settings and Profiles](05_Settings_And_Profiles.md) | Profiles, thresholds, rule controls, and shared editor/commandlet behavior |
| 06 | [Reports and Exports](06_Reports_And_Exports.md) | Filtered CSV and JSON exports, encoding, and report schema |
| 07 | [Commandlet and CI/CD](07_Commandlet_And_CI_CD.md) | Command syntax, options, exit codes, and automation guidance |
| 08 | [Troubleshooting](08_Troubleshooting.md) | Common setup, scan, navigation, export, and commandlet problems |
| 09 | [Known Limitations](09_Known_Limitations.md) | Confirmed scope boundaries and experimental behavior |
| 10 | [Changelog](10_Changelog.md) | Initial release notes for version 1.0.0 |

---

## Quick Answers

| I need to… | Go to |
|---|---|
| Install and enable the plugin | [01 — Installation](01_Installation.md) |
| Run my first audit | [02 — Quick Start](02_Quick_Start.md) |
| Audit the current level | [03 — Scan Level](03_Editor_Workflow.md#scan-level) |
| Audit selected actors or graphs | [03 — Scan Selected](03_Editor_Workflow.md#scan-selected) |
| Understand a finding | [03 — Findings and Details](03_Editor_Workflow.md#findings-and-details) |
| Look up a rule | [04 — Audit Rule Reference](04_Audit_Rule_Reference.md) |
| Change a profile or threshold | [05 — Settings and Profiles](05_Settings_And_Profiles.md) |
| Export a focused report | [06 — Reports and Exports](06_Reports_And_Exports.md) |
| Run an automated audit | [07 — Commandlet and CI/CD](07_Commandlet_And_CI_CD.md) |
| Diagnose a problem | [08 — Troubleshooting](08_Troubleshooting.md) |
| Review product boundaries | [09 — Known Limitations](09_Known_Limitations.md) |

---

## Product Summary

| Area | Value |
|---|---|
| Unreal Engine | 5.8 |
| Plugin type | Editor-only C++ plugin |
| Required Engine plugin | Unreal Engine PCG |
| Supported target platforms | Win64, Linux, Mac |
| Audit rules | 24 total: 14 Graph Audit and 10 Component Audit |
| Reports | CSV and JSON |
| Automation | `PCGAudit` commandlet |
| Content modification | Read-only; no automatic graph or component changes |

---

## Support

For setup questions, bug reports, feature requests, and product support, join the [Hanke Unreal Tools Discord](https://discord.gg/vgpmnN6nCR).

Next: [01 — Installation](01_Installation.md)
