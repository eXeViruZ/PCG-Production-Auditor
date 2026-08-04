# 04 — Audit Rule Reference

PCG Production Auditor version 1.0.0 includes 24 audit rules:

- 14 Graph Audit rules
- 10 Component Audit rules

Rule IDs are stable. `GA-08` is intentionally unused and is not reassigned.

## Severity Guide

| Severity | Meaning |
|---|---|
| Error | A condition that can invalidate or block an expected PCG workflow |
| Warning | A condition that should be reviewed because it can cause incorrect, incomplete, or difficult-to-maintain behavior |
| Info | An organizational, consistency, or review finding that is not treated as an immediate failure |

---

## Graph Audit Rules

### GA-01 — Unconnected Inputs

**Severity:** Warning  
**Category:** Graph Audit

Checks for relevant graph inputs that are not connected as expected.

**Recommended review:** Confirm whether the input is intentionally unused. Connect the required upstream data when the node depends on that input.

### GA-02 — Unconnected/Dead Nodes

**Severity:** Warning  
**Category:** Graph Audit

Checks for isolated nodes and immediate dead-end nodes that do not contribute to an active graph path.

**Recommended review:** Remove obsolete nodes or reconnect nodes that are intended to participate in the graph.

**Scope note:** Version 1.0.0 detects isolated nodes and immediate dead ends. It does not trace complete chained dead branches.

### GA-03 — Disabled Nodes

**Severity:** Info  
**Category:** Graph Audit

Reports disabled nodes for review.

**Recommended review:** Confirm the disabled state is intentional. Remove obsolete nodes or re-enable nodes required by the current workflow.

### GA-04 — Empty Mesh Selector

**Severity:** Warning  
**Category:** Graph Audit

Checks supported mesh-selection configurations that do not contain a usable mesh selection.

**Recommended review:** Assign the intended mesh entries or confirm the selector is intentionally left empty.

### GA-05 — Duplicate Nodes

**Severity:** Info  
**Category:** Graph Audit

Reports duplicate node configurations that may indicate repeated or accidental graph setup.

**Recommended review:** Compare the reported nodes and keep both only when the duplication is intentional.

### GA-06 — Circular Subgraph Dependency

**Severity:** Error  
**Category:** Graph Audit

Checks for circular dependency chains between PCG subgraphs.

**Recommended review:** Break the circular reference so that subgraph dependencies form a valid non-recursive structure.

### GA-07 — Hardcoded Seed

**Severity:** Info  
**Category:** Graph Audit

Reports seed usage that should be reviewed for project consistency and intentional determinism.

**Recommended review:** Confirm the seed is deliberate and matches the expected variation or reproducibility requirements.

### GA-09 — Read-Before-Write

**Severity:** Info  
**Category:** Graph Audit  
**Status:** Experimental

Reports potential read-before-write conditions for manual review.

**Recommended review:** Inspect the relevant data flow and confirm that required attributes or values are written before they are read.

**Important:** This rule is experimental and its findings may require manual interpretation.

### GA-10 — Debug Mode Active

**Severity:** Info  
**Category:** Graph Audit

Reports supported debug modes that remain enabled.

**Recommended review:** Keep debug behavior only when it is currently required. Disable it before final delivery when appropriate for the project.

### GA-11 — Subgraph Missing Input Node

**Severity:** Error  
**Category:** Graph Audit

Checks subgraphs that are missing the expected input node structure.

**Recommended review:** Add or restore the required subgraph input configuration.

### GA-12 — Invalid Filter/Empty Data

**Severity:** Warning  
**Category:** Graph Audit

Checks supported filter configurations for invalid ranges or conditions that can produce empty data.

**Recommended review:** Verify the filter range, comparison values, and expected input data.

### GA-13 — Missing Landscape Connection

**Severity:** Warning  
**Category:** Graph Audit

Checks supported Landscape-dependent graph configurations for a missing Landscape connection.

**Recommended review:** Connect or reference the intended Landscape data source.

### GA-14 — Missing Output Node

**Severity:** Error  
**Category:** Graph Audit

Checks graphs that do not provide the expected output node structure.

**Recommended review:** Add or restore the required graph output.

### GA-15 — Missing Required Pin

**Severity:** Error  
**Category:** Graph Audit

Checks supported nodes for missing required pin connections.

**Recommended review:** Connect the required data path and confirm the node receives the expected input type.

---

## Component Audit Rules

### CA-01 — Missing Graph

**Severity:** Error  
**Category:** Component Audit

Checks PCG Components that do not have an assigned graph where a graph is required.

**Recommended review:** Assign the intended PCG Graph or remove the component when it is no longer required.

### CA-02 — Oversized Bounds

**Severity:** Warning  
**Category:** Component Audit

Checks PCG Component bounds against the configured maximum bounds threshold.

**Recommended review:** Confirm the component requires the reported bounds size. Reduce the bounds or adjust the project threshold when the size is intentional.

### CA-03 — Bounds Overlap

**Severity:** Info  
**Category:** Component Audit

Reports overlapping PCG Component bounds for review.

**Recommended review:** Confirm the overlap is intentional and does not create duplicated or conflicting generation areas.

### CA-04 — RuntimeGen Component Check

**Severity:** Warning  
**Category:** Component Audit

Checks supported PCG Component runtime-generation configuration.

**Recommended review:** Confirm the generation mode matches the intended editor or runtime workflow.

### CA-05 — Excessive Component Count

**Severity:** Info  
**Category:** Component Audit

Reports when the relevant PCG Component count exceeds the configured project threshold.

**Recommended review:** Confirm the count is intentional or consolidate the workflow where appropriate.

### CA-06 — Component Naming Convention

**Severity:** Info  
**Category:** Component Audit

Checks PCG Component naming for the supported organizational convention.

**Recommended review:** Rename the component when consistent naming would improve identification and maintenance.

### CA-07 — Component Tag Check

**Severity:** Info  
**Category:** Component Audit

Checks supported component tag organization.

**Recommended review:** Add, remove, or standardize tags according to the project's PCG workflow.

### CA-08 — Invalid Graph Reference

**Severity:** Error  
**Category:** Component Audit

Checks for an invalid PCG Graph reference on a component.

**Recommended review:** Restore a valid graph reference or replace the invalid assignment.

### CA-09 — Dirty Components

**Severity:** Warning  
**Category:** Component Audit

Reports PCG Components that require regeneration or review of their current generated state.

**Recommended review:** Confirm recent graph or component changes, then regenerate the component when appropriate.

### CA-10 — Graph Type Mismatch

**Severity:** Warning  
**Category:** Component Audit

Checks for a mismatch between the component configuration and the assigned graph type or expected graph usage.

**Recommended review:** Confirm that the assigned graph is intended for the component's current configuration.

---

## Subgraph-Aware Analysis

Applicable Graph Audit rules skip internal subgraph implementation nodes. This keeps findings focused on relevant user-authored graph structures instead of treating internally expanded subgraph nodes as ordinary project nodes.

---

Previous: [03 — Editor Workflow](03_Editor_Workflow.md) · [Documentation Index](INDEX.md) · Next: [05 — Settings and Profiles](05_Settings_And_Profiles.md)
