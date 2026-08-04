# PCG Production Auditor

PCG Production Auditor is an editor-only C++ plugin for Unreal Engine 5.8 that audits native PCG Graphs and PCG Components for configuration, structure, organization, and workflow issues.

The plugin provides a dedicated editor interface with categorized findings, direct navigation, configurable audit profiles, CSV and JSON report export, and commandlet support for automated validation and CI/CD workflows.

## Requirements

- Unreal Engine 5.8
- Unreal Engine's built-in PCG plugin enabled
- PCG Production Auditor enabled

PCG Production Auditor is editor-only and does not add a runtime module to packaged games.

## Main Capabilities

- 24 focused audit rules
- 14 Graph Audit rules
- 10 Component Audit rules
- Level and selection-based scans
- Content Browser support for selected PCG Graph assets
- Viewport support for selected PCG actors and components
- Direct navigation to affected graphs and actors
- Severity, category, and text filters
- CSV and JSON report export
- Configurable profiles, thresholds, and per-rule controls
- `PCGAudit` commandlet for automated validation

## Quick Start

1. Enable Unreal Engine's native PCG plugin.
2. Enable PCG Production Auditor.
3. Restart the Unreal Editor if prompted.
4. Open the PCG Production Auditor editor interface.
5. Choose **Scan Level** or **Scan Selected**.
6. Review the generated findings and recommendations.
7. Double-click Graph Audit findings to open the affected PCG Graph.
8. Use Component Audit findings to select and focus the affected actor in the viewport.

Audit operations are read-only. The plugin reports and explains findings without automatically modifying PCG Graphs, actors, components, or project content.

## Scan Modes

### Scan Level

Audits supported PCG Components and their referenced graphs in the currently loaded level.

### Scan Selected

Audits the relevant current selection, including:

- Selected PCG actors and components in the viewport
- Selected PCG Graph assets in the Content Browser
- Multiple selected PCG Graph assets

Audits can also be started from supported PCG Graph and actor context menus.

## Findings and Navigation

Each finding includes:

- Rule ID and rule name
- Severity
- Affected graph, actor, or component
- Problem description
- Recommended action
- Relevant target information

Graph Audit findings can open the affected PCG Graph.

Component Audit findings can select and focus the affected actor in the viewport, including a temporary visual highlight.

## Filters and Search

The editor interface supports:

- Independent Error, Warning, and Info filters
- Graph Audit and Component Audit filters
- Search by rule name, target, and problem text
- Sortable result columns
- Graph and component summary statistics
- Level-wide and selection-specific result clearing

A scan-in-progress guard prevents overlapping audit operations.

## Audit Rules

### Graph Audit Rules

- GA-01 — Unconnected Inputs
- GA-02 — Unconnected/Dead Nodes
- GA-03 — Disabled Nodes
- GA-04 — Empty Mesh Selector
- GA-05 — Duplicate Nodes
- GA-06 — Circular Subgraph Dependency
- GA-07 — Hardcoded Seed
- GA-09 — Read-Before-Write (Experimental)
- GA-10 — Debug Mode Active
- GA-11 — Subgraph Missing Input Node
- GA-12 — Invalid Filter/Empty Data
- GA-13 — Missing Landscape Connection
- GA-14 — Missing Output Node
- GA-15 — Missing Required Pin

`GA-08` is intentionally unused. Rule IDs are kept stable and are not reassigned.

### Component Audit Rules

- CA-01 — Missing Graph
- CA-02 — Oversized Bounds
- CA-03 — Bounds Overlap
- CA-04 — RuntimeGen Component Check
- CA-05 — Excessive Component Count
- CA-06 — Component Naming Convention
- CA-07 — Component Tag Check
- CA-08 — Invalid Graph Reference
- CA-09 — Dirty Components
- CA-10 — Graph Type Mismatch

## Project Settings

Configuration is available under:

**Project Settings → Plugins → PCG Production Auditor**

Available options include:

- Default, Strict, and Relaxed profiles
- Maximum component bounds threshold
- Maximum recommended PCG component count
- Individual enable or disable controls for all 24 audit rules

The same enabled and disabled rule configuration is used by Editor scans and commandlet scans.

## CSV and JSON Reports

The currently visible findings can be exported as CSV or JSON.

Active severity, category, and search filters are respected during export.

### CSV

- UTF-8 output with BOM
- RFC 4180-compatible field escaping

### JSON

JSON reports use a versioned schema and include:

- `findings_count`
- `source_plugin`
- `plugin_version`
- `engine_version`
- `timestamp`
- `scan_mode`
- `findings`

Editor and commandlet exports use a consistent report structure.

## Commandlet and CI/CD

PCG Production Auditor includes the `PCGAudit` commandlet for automated audits without opening the interactive Unreal Editor.

Example:

```text
UnrealEditor-Cmd.exe Project.uproject -run=PCGAudit -Map=/Game/Maps/MyLevel -Output=audit.json -Format=json -Rules=GA-01,CA-02 -Severity=Error,Warning
```

Supported options allow you to:

- Select a map
- Choose CSV or JSON output
- Execute specific audit rules
- Filter reported severity levels

The commandlet respects rules disabled through PCG Production Auditor Project Settings.

### Exit Codes

- `0` — No matching findings
- `1` — Matching findings were detected
- `2` — Invalid arguments, map loading failure, or report export failure

## Subgraph-Aware Analysis

Applicable Graph Audit rules account for internal subgraph implementation nodes. This helps keep findings focused on relevant user-authored graph structures instead of treating internally expanded subgraph nodes as normal project issues.

## Current Limitations

- Dead-node analysis detects isolated nodes and immediate dead ends but does not trace complete chained dead branches.
- Graph findings open the affected PCG Graph but do not focus the exact node inside the Graph Editor.
- Read-Before-Write analysis is experimental and may require manual review.
- Editor search covers rule names, targets, and problem text, but not Rule IDs or recommendation text.
- Scan cancellation is not available in version 1.0.0.

## Support

- Discord: https://discord.gg/vgpmnN6nCR
- Email: Tom.Hanke.Official@web.de

For setup questions, bug reports, feature requests, and product support, use the Hanke Unreal Tools Discord or the public support email.

## Copyright

Copyright © 2026 Tom Leon Vincent Hanke. All rights reserved.
