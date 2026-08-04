# 10 — Changelog

## PCG Production Auditor v1.0.0

**Engine:** Unreal Engine 5.8  
**Release type:** Initial release  
**Plugin type:** Editor-only C++ plugin

### Release Summary

PCG Production Auditor introduces a structured quality-control workflow for Unreal Engine PCG Graphs and PCG Components. It combines 24 focused audit rules, direct editor navigation, configurable project settings, filtered reports, and commandlet support for repeatable manual and automated validation.

### Added

- Added 14 Graph Audit rules for PCG Graph structure and node-configuration review.
- Added 10 Component Audit rules for level-side PCG Component configuration and reference review.
- Added **Scan Level** for auditing supported PCG Components and their referenced graphs in the currently loaded level.
- Added **Scan Selected** for selected PCG actors, components, and one or more selected PCG Graph assets.
- Added PCG Graph and actor context menu audit entry points.
- Added Error, Warning, and Info severity filters.
- Added Graph Audit and Component Audit category filters.
- Added search by rule name, target name, and problem text.
- Added structured finding details with Rule ID, severity, target, problem description, and recommended action.
- Added direct navigation that opens affected PCG Graphs and focuses affected actors with a temporary viewport highlight.
- Added CSV report export using UTF-8 with BOM and RFC 4180-compatible escaping.
- Added JSON report export using UTF-8 without BOM and a versioned report schema.
- Added Default, Strict, and Relaxed audit profiles.
- Added configurable component bounds and component count thresholds.
- Added individual enable and disable controls for all 24 audit rules.
- Added the `PCGAudit` commandlet for automated validation and CI/CD workflows.
- Added commandlet filtering by map, output format, Rule IDs, and severity.
- Added commandlet exit codes for no findings, detected findings, and execution or export errors.
- Added subgraph-aware analysis that skips internal subgraph implementation nodes for applicable rules.
- Added a scan-in-progress guard to prevent overlapping audit operations.

### Compatibility

- Supports Unreal Engine 5.8.
- Editor-only; no runtime module is included.
- Requires Unreal Engine's built-in PCG plugin.
- Supported target platforms: Win64, Linux, Mac.

### Known Limitations

- Dead-node analysis detects isolated nodes and immediate dead ends but does not trace complete chained dead branches.
- Graph findings open the affected PCG Graph but do not focus the exact node inside the Graph Editor.
- Read-Before-Write analysis is experimental and may require manual review.
- Editor search does not include Rule IDs or recommendation text.
- Scan cancellation is not available in version 1.0.0.

See [09 — Known Limitations](09_Known_Limitations.md) for details.

---

Previous: [09 — Known Limitations](09_Known_Limitations.md) · [Documentation Index](INDEX.md)
