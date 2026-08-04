# 08 — Troubleshooting

This page applies to PCG Production Auditor version 1.0.0 for Unreal Engine 5.8.

## The Plugin Does Not Load

**Symptom:** Unreal reports that PCG Production Auditor cannot be loaded.

**Likely causes:**

- the project is not using Unreal Engine 5.8
- the plugin folder is nested incorrectly
- a C++ project requires regenerated project files or a rebuild
- stale build folders are interfering with the current plugin build

**Resolution:**

1. Confirm the project uses Unreal Engine 5.8.
2. Confirm **PCG Production Auditor** is enabled under **Edit → Plugins**.
3. Confirm Unreal Engine's native **PCG** plugin is enabled.
4. Confirm the plugin folder is not nested incorrectly.
5. For a C++ project, regenerate project files and rebuild.
6. Remove stale project or plugin `Binaries` and `Intermediate` folders before rebuilding when necessary.

**Expected result:** The project opens and the plugin registers its toolbar icon, Tools menu entry, and dockable tab.

## The Toolbar Icon Is Missing

**Symptom:** The PCG Production Auditor icon is not visible in the Level Editor Play toolbar.

The expected location is to the right of the standard Play controls. The button has no text label. Its tooltip is:

**Open PCG Production Auditor — scan graphs and components for production issues**

**Resolution:**

1. Confirm the plugin is enabled under **Edit → Plugins**.
2. Confirm the native PCG plugin is enabled.
3. Restart Unreal Editor.
4. Check **Tools → PCG Production Auditor** as the alternative entry point.
5. Check the Output Log for plugin startup or menu-registration errors.
6. Reset or reopen the relevant editor toolbar area when the editor layout has been customized.

**Expected result:** The icon appears in the Play toolbar and opens the **PCG Production Auditor** tab.

## The Tools Menu Entry Is Missing

**Symptom:** **Tools → PCG Production Auditor** is not available.

**Resolution:**

1. Confirm the plugin is enabled under **Edit → Plugins**.
2. Confirm the native PCG plugin is enabled.
3. Restart Unreal Editor.
4. Check whether the toolbar icon is available.
5. Check the Output Log for startup or ToolMenus registration errors.

There is no separate **Window → PCG Production Auditor** entry in version 1.0.0.

**Expected result:** **Tools → PCG Production Auditor** opens the same dockable tab as the toolbar icon.

## The Tab Does Not Open

**Symptom:** The toolbar icon or Tools menu entry is visible, but the Auditor tab does not appear.

**Resolution:**

1. Invoke the tab again through **Tools → PCG Production Auditor**.
2. Check whether the tab is already docked or hidden in another editor area.
3. Reset the Unreal Editor layout when a previously saved layout places the tab off-screen.
4. Check the Output Log for tab-spawner or Slate errors.
5. Restart Unreal Editor and try both entry points again.

**Expected result:** A dockable tab titled **PCG Production Auditor** opens or receives focus.

## Scan Level Returns No Findings

**Symptom:** The scan completes but the result list is empty.

**Resolution:**

1. Confirm the current level contains supported PCG Components.
2. Confirm the components reference PCG Graphs where required.
3. Confirm relevant audit rules are enabled in Project Settings.
4. Enable all severity and category filters.
5. Clear the text search field.
6. Confirm the intended level is currently loaded.

An empty result can also mean no enabled rule detected a matching condition.

## Scan Selected Returns No Findings

**Symptom:** A selection scan completes without expected results.

**Resolution:**

1. Select a supported PCG actor or component in the viewport, or a PCG Graph asset in the Content Browser.
2. For graph assets, confirm the selected assets are PCG Graphs.
3. Confirm the relevant Graph Audit or Component Audit category filter is enabled.
4. Clear the text search field.
5. Confirm the required audit rules are enabled.

## A Finding Is Hidden

**Symptom:** A known finding is not visible after a scan.

**Resolution:**

1. Enable Error, Warning, and Info filters.
2. Enable Graph Audit and Component Audit filters.
3. Clear the search text.
4. Confirm results were not cleared after the scan.
5. Confirm the expected rule is enabled.

Exports use the same visible filtered result set.

## A Graph Finding Opens the Graph but Not the Exact Node

This is expected in version 1.0.0.

Graph findings open the affected PCG Graph. Exact node focus inside the Graph Editor is not currently available.

Use the finding's rule, target, problem description, and recommendation to locate the relevant graph area.

## A Component Finding Does Not Focus the Expected Actor

**Resolution:**

1. Confirm the actor still exists in the current level.
2. Confirm the finding belongs to the currently loaded level state.
3. Clear old results and rescan when actors were renamed, replaced, or removed.
4. Confirm the viewport is not locked to an unrelated context.

Component navigation selects and focuses the actor and applies a temporary highlight.

## Export Contains Fewer Findings Than Expected

Exports include only currently visible findings.

Before exporting:

1. Enable all required severity filters.
2. Enable the required category filters.
3. Clear the search field for a complete report.
4. Confirm the visible finding count.
5. Export again.

## CSV Opens with Incorrect Characters

CSV output uses UTF-8 with BOM.

Open or import the file using UTF-8 in the target spreadsheet application. Avoid forcing a legacy local encoding.

## JSON Processing Fails

**Resolution:**

1. Confirm the file is complete and not empty.
2. Confirm the consumer expects UTF-8 without BOM.
3. Read the versioned schema fields before processing findings.
4. Confirm the report was generated by the expected plugin version.
5. Confirm the consumer handles the top-level `findings` collection.

See [06 — Reports and Exports](06_Reports_And_Exports.md).

## Commandlet Returns Exit Code 1

Exit code `1` means matching findings were detected.

It does not mean the commandlet failed to execute.

Review the generated report and decide whether the CI/CD stage should fail, warn, or continue.

## Commandlet Returns Exit Code 2

Exit code `2` indicates:

- invalid arguments
- map loading failure
- report export failure

Check the project path, map path, output path, requested format, command-line spelling, and output write permissions.

## A Requested Rule Does Not Run in the Commandlet

**Resolution:**

1. Confirm the Rule ID is written correctly.
2. Confirm the rule is enabled in Project Settings.
3. Confirm `-Rules=` uses comma-separated IDs.
4. Confirm the selected severity filter includes the rule's severity.
5. Confirm the audited map contains a relevant target.

## GA-09 Reports a Questionable Finding

`GA-09 — Read-Before-Write` is experimental.

Review the actual graph data flow manually. Do not treat the finding as automatic proof of a defect.

Disable GA-09 when the project does not currently use experimental analysis.

## GA-02 Does Not Report a Complete Dead Branch

Version 1.0.0 detects isolated nodes and immediate dead-end nodes.

It does not trace complete chained dead branches. Review longer unused chains manually.

## A Scan Cannot Be Cancelled

Scan cancellation is not available in version 1.0.0.

Allow the current scan to finish. The scan-in-progress guard prevents a second overlapping audit from starting.

## Still Not Working?

Use the [Hanke Unreal Tools Discord](https://discord.gg/vgpmnN6nCR) for bug reports, setup questions, feature requests, and community support.

For direct or individual support, contact [Tom.Hanke.Official@web.de](mailto:Tom.Hanke.Official@web.de).

Include:

- Unreal Engine version
- PCG Production Auditor version
- operating system
- scan mode or opening method
- affected Rule ID, when relevant
- relevant graph or component setup
- reproduction steps
- expected result
- actual result
- screenshots, Output Log lines, or exported reports when useful

---

Previous: [07 — Commandlet and CI/CD](07_Commandlet_And_CI_CD.md) · [Documentation Index](INDEX.md) · Next: [09 — Known Limitations](09_Known_Limitations.md)
