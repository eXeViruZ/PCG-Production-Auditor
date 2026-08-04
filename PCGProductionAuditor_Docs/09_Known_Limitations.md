# 09 — Known Limitations

This page documents confirmed scope boundaries for PCG Production Auditor version 1.0.0.

These items describe the current product scope and are not automatic indicators of a defect.

## Dead-Node Analysis

`GA-02 — Unconnected/Dead Nodes` detects:

- isolated nodes
- immediate dead-end nodes

Version 1.0.0 does not trace complete chained dead branches.

Review longer unused graph chains manually.

---

## Graph Navigation

Graph Audit findings open the affected PCG Graph.

Version 1.0.0 does not focus the exact internal node associated with the finding inside the Graph Editor.

Use the Rule ID, target, problem description, and recommendation to locate the relevant graph area.

---

## Experimental Read-Before-Write Analysis

`GA-09 — Read-Before-Write` is experimental.

Its findings are intended for manual review and may require interpretation of the actual graph data flow.

Do not use GA-09 as a strict automated failure condition without validating it against the project's graph conventions.

---

## Search Scope

Editor search covers:

- rule name
- target name
- problem text

Version 1.0.0 search does not include:

- Rule IDs
- recommendation text

Use the category and severity filters together with text search for focused review.

---

## Scan Cancellation

Scan cancellation is not available in version 1.0.0.

The active scan must complete before another scan can begin. A scan-in-progress guard prevents overlapping audit operations.

---

## Read-Only Scope

PCG Production Auditor does not automatically modify project content.

It does not provide automatic fixes for reported findings in version 1.0.0.

This is an intentional product behavior: the plugin reports and explains findings while the user controls every graph and component change.

---

## Internal Subgraph Nodes

Applicable Graph Audit rules skip internal subgraph implementation nodes.

This reduces irrelevant findings from internally expanded subgraph structures. The audit remains focused on supported user-authored graph structures.

---

Previous: [08 — Troubleshooting](08_Troubleshooting.md) · [Documentation Index](INDEX.md) · Next: [10 — Changelog](10_Changelog.md)
