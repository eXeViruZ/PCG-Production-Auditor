# PCG Production Auditor

PCG Production Auditor provides a production-ready quality-control workflow for Unreal Engine's native PCG framework. It audits PCG Graphs and level-side PCG Components, presents structured findings with practical recommendations, and helps developers review procedural setups before configuration problems become difficult to trace.

The plugin is designed for interactive editor reviews, repeatable project checks, report generation, and automated validation through the included `PCGAudit` commandlet.

## Product Information

| Field | Value |
|---|---|
| Version | 1.0.0 |
| Unreal Engine | 5.8 |
| Plugin Type | Editor-only C++ plugin |
| Required Engine Plugin | Unreal Engine PCG |
| Supported Platforms | Win64, Linux, Mac |
| Audit Rules | 24 total: 14 Graph Audit and 10 Component Audit |
| Report Formats | CSV and JSON |

## Main Capabilities

- Audit the current level, selected PCG actors and components, or selected PCG Graph assets
- Review 24 focused Graph Audit and Component Audit rules
- Filter findings by severity, category, and search text
- Open affected PCG Graphs or focus relevant actors directly from the results
- Configure Default, Strict, and Relaxed profiles, project thresholds, and individual rules
- Export the currently visible findings as CSV or versioned JSON
- Run automated audits through the `PCGAudit` commandlet and CI/CD workflows

Audit operations are read-only. PCG Production Auditor reports and explains findings without automatically modifying PCG Graphs, actors, components, or project content.

## Requirements

- Unreal Engine 5.8
- PCG Production Auditor enabled
- Unreal Engine's built-in PCG plugin enabled

The plugin is editor-only and does not add a runtime module to packaged games.

## Quick Start

1. Enable **PCG Production Auditor** under **Edit → Plugins**.
2. Restart Unreal Editor when prompted.
3. Open the Auditor through either entry point:
   - click the PCG Production Auditor icon in the Level Editor Play toolbar, to the right of the standard Play controls
   - open **Tools → PCG Production Auditor**
4. Select **Scan Level** for the currently loaded level or **Scan Selected** for selected actors, components, or PCG Graph assets.
5. Review the findings, recommendations, and affected targets.
6. Double-click a Graph Audit finding to open the affected PCG Graph, or use a Component Audit finding to focus the relevant actor.

Both entry points open the same dockable **PCG Production Auditor** tab.

For the complete first-use workflow, see [02 — Quick Start](PCGProductionAuditor_Docs/02_Quick_Start.md).

## Documentation

| Document | Contents |
|---|---|
| [Documentation Index](PCGProductionAuditor_Docs/INDEX.md) | Complete navigation and quick-answer guide |
| [01 — Installation](PCGProductionAuditor_Docs/01_Installation.md) | Requirements, installation, activation, updating, and removal |
| [02 — Quick Start](PCGProductionAuditor_Docs/02_Quick_Start.md) | First scan, finding review, navigation, and export |
| [03 — Editor Workflow](PCGProductionAuditor_Docs/03_Editor_Workflow.md) | Interface, scan modes, filters, findings, and direct navigation |
| [04 — Audit Rule Reference](PCGProductionAuditor_Docs/04_Audit_Rule_Reference.md) | All 24 Graph Audit and Component Audit rules |
| [05 — Settings and Profiles](PCGProductionAuditor_Docs/05_Settings_And_Profiles.md) | Profiles, thresholds, and per-rule configuration |
| [06 — Reports and Exports](PCGProductionAuditor_Docs/06_Reports_And_Exports.md) | CSV and JSON behavior, filtering, encoding, and schema overview |
| [07 — Commandlet and CI/CD](PCGProductionAuditor_Docs/07_Commandlet_And_CI_CD.md) | Command syntax, options, examples, and exit codes |
| [08 — Troubleshooting](PCGProductionAuditor_Docs/08_Troubleshooting.md) | Common setup, scan, navigation, export, and commandlet problems |
| [09 — Known Limitations](PCGProductionAuditor_Docs/09_Known_Limitations.md) | Confirmed scope boundaries and experimental behavior |
| [10 — Changelog](PCGProductionAuditor_Docs/10_Changelog.md) | Public version history |

## Important Notes

- `GA-09 — Read-Before-Write` is experimental and its findings should be reviewed manually.
- Graph findings open the affected PCG Graph but do not focus the exact internal node in version 1.0.0.
- Export operations include only the findings currently visible after severity, category, and text filters are applied.
- Rule IDs are stable. `GA-08` is intentionally unused and is not reassigned.

## Support

For setup questions, bug reports, feature requests, and product support, join the [Hanke Unreal Tools Discord](https://discord.gg/vgpmnN6nCR).

## Copyright

Copyright © 2026 Tom Leon Vincent Hanke. All rights reserved.
