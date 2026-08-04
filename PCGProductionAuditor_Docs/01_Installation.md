# 01 — Installation

## Requirements

| Requirement | Value |
|---|---|
| Unreal Engine | **5.8** |
| Required built-in plugin | Unreal Engine **PCG** |
| Plugin type | Editor-only C++ plugin |
| Supported target platforms | Win64, Linux, Mac |

PCG Production Auditor does not require engine modifications or third-party software.

---

## Option A — Install from Fab

1. Add **PCG Production Auditor** to your Fab library.
2. Install the Unreal Engine 5.8 version through the Epic Games Launcher or Fab integration.
3. Open your Unreal Engine 5.8 project.
4. Open **Edit → Plugins**.
5. Enable Unreal Engine's built-in **PCG** plugin.
6. Enable **PCG Production Auditor**.
7. Restart Unreal Editor when prompted.

---

## Option B — Install as a Project Plugin

1. Close Unreal Editor.
2. Copy the supplied plugin folder into:

```text
<YourProject>/Plugins/
```

3. Confirm the plugin descriptor is inside the copied plugin folder.
4. Reopen the project.
5. Enable Unreal Engine's built-in **PCG** plugin.
6. Enable **PCG Production Auditor**.
7. Restart Unreal Editor when prompted.

For C++ projects, regenerate project files and rebuild when Unreal requests it.

---

## Verify the Installation

After restarting the editor:

1. Confirm **PCG Production Auditor** is enabled under **Edit → Plugins**.
2. Confirm the built-in **PCG** plugin is enabled.
3. Open the PCG Production Auditor editor tab from the plugin's toolbar entry.
4. Confirm the interface opens without an error.
5. Load a level containing at least one PCG Component or select a PCG Graph asset for the first test scan.

Continue with [02 — Quick Start](02_Quick_Start.md).

---

## Updating the Plugin

1. Close Unreal Editor.
2. Replace the existing plugin build with the new version.
3. Do not merge old `Binaries` or `Intermediate` folders into the new build.
4. Reopen the project.
5. Rebuild if Unreal requests it.
6. Confirm the plugin version and supported Engine version before continuing work.

Release-specific changes are documented in [10 — Changelog](10_Changelog.md).

---

## Removing the Plugin

PCG Production Auditor is editor-only and does not automatically modify PCG Graphs, actors, components, or project content.

To remove it:

1. Close Unreal Editor.
2. Disable or uninstall PCG Production Auditor.
3. Remove the project plugin folder when installed manually.
4. Reopen the project.

Previously exported CSV and JSON files remain normal external report files and can be kept or deleted independently.

---

## Installation Problems

See [08 — Troubleshooting](08_Troubleshooting.md) when:

- the toolbar entry is missing
- the plugin does not load
- Unreal reports a version mismatch
- the editor tab does not open

---

Previous: [Documentation Index](INDEX.md) · Next: [02 — Quick Start](02_Quick_Start.md)
