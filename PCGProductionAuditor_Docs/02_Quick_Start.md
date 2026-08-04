# 02 — Quick Start

This guide runs a first audit, explains the result list, and exports a focused report.

## Before You Start

Confirm:

- Unreal Engine 5.8 is running.
- Unreal Engine's built-in PCG plugin is enabled.
- PCG Production Auditor is enabled.
- A level with PCG Components is loaded, or one or more PCG Graph assets are selected in the Content Browser.

---

## Open PCG Production Auditor

Use either confirmed entry point:

- click the PCG Production Auditor icon in the Level Editor Play toolbar, to the right of the standard Play controls
- open **Tools → PCG Production Auditor**

The toolbar button has no text label. Its tooltip reads:

**Open PCG Production Auditor — scan graphs and components for production issues**

Both entry points open the same dockable tab titled **PCG Production Auditor**.

---

## Run a Level Audit

1. Open **PCG Production Auditor**.
2. Select **Scan Level**.
3. Wait for the scan to complete.
4. Review the summary counts for Errors, Warnings, and Info findings.
5. Select a finding to read its problem description and recommended action.

**Scan Level** audits supported PCG Components in the currently loaded level and the PCG Graphs referenced by those components.

**Expected result:** The result list displays all findings produced by the enabled rules for the current level.

---

## Run a Selection Audit

Use **Scan Selected** for a focused review.

Supported selections include:

- PCG actors or components selected in the viewport
- one selected PCG Graph asset in the Content Browser
- multiple selected PCG Graph assets in the Content Browser

Steps:

1. Select the relevant actors, components, or graph assets.
2. Open **PCG Production Auditor** through the toolbar icon or **Tools → PCG Production Auditor**.
3. Select **Scan Selected**.
4. Review the generated findings.

Supported audits can also be started from PCG Graph and actor context menus.

**Expected result:** Only findings related to the supported current selection are added to the result list.

---

## Review a Finding

Each finding provides:

- Rule ID
- Rule name
- Severity
- Audit category
- Affected graph, actor, or component
- Problem description
- Recommended action
- Relevant target information

Use the severity and category filters to reduce the list before reviewing individual findings.

---

## Navigate to the Affected Target

- Double-click a **Graph Audit** finding to open the affected PCG Graph.
- Use a **Component Audit** finding to select and focus the affected actor in the viewport.
- Component navigation includes a temporary visual highlight to make the actor easier to identify.

PCG Production Auditor reports issues but does not automatically change project content.

---

## Export the Current Results

1. Apply the required severity, category, and text filters.
2. Confirm the result list contains the findings that should be included.
3. Select **Export CSV** or **Export JSON**.
4. Choose an output location.

Only the currently visible filtered findings are exported.

See [06 — Reports and Exports](06_Reports_And_Exports.md) for format details.

---

## Recommended First Review

1. Run **Scan Level**.
2. Review all Error findings first.
3. Review Warning findings.
4. Use Info findings for organization and workflow cleanup.
5. Open affected graphs and actors from the results.
6. Export a JSON or CSV baseline before making changes.
7. Rescan after the project has been adjusted.

---

Previous: [01 — Installation](01_Installation.md) · [Documentation Index](INDEX.md) · Next: [03 — Editor Workflow](03_Editor_Workflow.md)
