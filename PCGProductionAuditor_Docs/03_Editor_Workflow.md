# 03 — Editor Workflow

PCG Production Auditor provides one editor interface for reviewing PCG Graph structure and level-side PCG Component configuration.

## Interface Overview

The editor interface includes:

- scan controls
- Error, Warning, and Info summary counts
- severity filters
- Graph Audit and Component Audit category filters
- text search
- sortable finding columns
- finding details and recommendations
- direct navigation to affected graphs and actors
- CSV and JSON export controls
- scan status and progress feedback
- result clearing controls

A scan-in-progress guard prevents overlapping audit operations.

---

## Scan Level

**Scan Level** audits the currently loaded level.

The scan reviews:

- supported PCG Components in the level
- PCG Graphs referenced by those components
- graph and component conditions covered by enabled audit rules

Use this mode for broader level reviews, milestone checks, pre-handoff validation, and repeated quality-control passes.

---

## Scan Selected

**Scan Selected** audits the relevant current selection.

Supported selection workflows include:

- selected PCG actors in the viewport
- selected PCG Components in the viewport
- selected PCG Graph assets in the Content Browser
- multiple selected PCG Graph assets

Use this mode while developing or reviewing a specific graph, actor, or group of graph assets.

---

## Context Menu Audits

Supported audits can be started from:

- PCG Graph asset context menus in the Content Browser
- supported PCG actor context menus in the editor

Context menu scans provide a faster entry point when the target is already selected.

---

## Findings and Details

Each finding contains structured information:

| Field | Purpose |
|---|---|
| Rule ID | Stable identifier for the audit rule |
| Rule Name | Human-readable rule name |
| Severity | Error, Warning, or Info |
| Category | Graph Audit or Component Audit |
| Target | Affected graph, actor, or component |
| Problem | Description of the detected condition |
| Recommendation | Suggested review or corrective action |

Select a finding to review its full details before changing the project.

---

## Severity Filters

Severity filters can be enabled independently:

- **Error** — conditions that can prevent or invalidate an expected PCG workflow
- **Warning** — conditions that should be reviewed because they may produce incorrect, incomplete, or difficult-to-maintain behavior
- **Info** — organizational, consistency, or review findings that are not treated as immediate failures

A rule's exact severity is listed in [04 — Audit Rule Reference](04_Audit_Rule_Reference.md).

---

## Category Filters

Use category filters to separate:

- **Graph Audit** findings
- **Component Audit** findings

Graph Audit rules inspect PCG Graph structure and node configuration.

Component Audit rules inspect level-side PCG Component setup and references.

---

## Search

Text search covers:

- rule name
- target name
- problem text

Search does not currently include Rule IDs or recommendation text. See [09 — Known Limitations](09_Known_Limitations.md).

---

## Sorting

Use sortable result columns to group or compare findings by fields such as severity, rule, target, or category.

Sorting changes the display order only. It does not change the audit result data.

---

## Direct Navigation

### Graph Audit Findings

Double-click a Graph Audit finding to open the affected PCG Graph.

The graph is opened for review. Version 1.0.0 does not focus the exact internal node associated with the finding.

### Component Audit Findings

Component findings can:

- select the affected actor
- focus the actor in the viewport
- apply a temporary visual highlight

This helps identify the level-side target without manually searching for it.

---

## Clearing Results

Use the available clearing controls to remove level-wide or selection-specific results.

Clearing results does not modify the scanned PCG Graphs or Components.

---

## Read-Only Behavior

Audit operations are read-only.

PCG Production Auditor does not automatically:

- reconnect graph pins
- delete or enable nodes
- change component bounds
- assign graphs
- rename actors or components
- regenerate components as a corrective action
- modify project content based on a finding

The user remains in control of every project change.

---

Previous: [02 — Quick Start](02_Quick_Start.md) · [Documentation Index](INDEX.md) · Next: [04 — Audit Rule Reference](04_Audit_Rule_Reference.md)
