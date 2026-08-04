# 05 — Settings and Profiles

PCG Production Auditor settings are available under:

**Project Settings → Plugins → PCG Production Auditor**

Settings are stored at project level and are used by both editor scans and commandlet scans.

---

## Audit Profiles

Three profiles are included:

- **Default**
- **Strict**
- **Relaxed**

Profiles provide prepared audit configurations for different review goals.

Use:

- **Default** for normal project review
- **Strict** for a more demanding validation pass
- **Relaxed** when the project intentionally uses broader thresholds or fewer active checks

After choosing a profile, review the resulting rule and threshold settings to confirm they match the current project.

---

## Component Bounds Threshold

The maximum component bounds threshold is used by:

- **CA-02 — Oversized Bounds**

When a component exceeds the configured threshold, the rule reports a Warning.

Set the threshold according to the scale of the project's intended PCG areas. A large open-world workflow may need a different threshold from a compact level.

---

## Component Count Threshold

The maximum recommended PCG Component count is used by:

- **CA-05 — Excessive Component Count**

When the relevant count exceeds the configured threshold, the rule reports an Info finding.

This threshold is a project review aid, not an automatic performance guarantee.

---

## Individual Rule Controls

All 24 audit rules can be enabled or disabled individually.

Use per-rule controls when:

- a rule does not apply to the current project
- a project uses an intentional convention that would otherwise produce repeated findings
- a focused audit should run only a selected group of checks
- an experimental rule should be reviewed separately

Disabled rules are not included in normal editor scans.

---

## Editor and Commandlet Consistency

The commandlet respects rules disabled in Project Settings.

The optional commandlet `-Rules` argument can be used to request a focused subset of rule IDs. Project rule configuration remains part of the audit behavior.

See [07 — Commandlet and CI/CD](07_Commandlet_And_CI_CD.md).

---

## Recommended Configuration Workflow

1. Start with the **Default** profile.
2. Run a level scan.
3. Review repeated findings.
4. Adjust component bounds and count thresholds when the project's scale requires it.
5. Disable only rules that are intentionally outside the project's workflow.
6. Keep Error rules enabled unless there is a documented project-specific reason not to.
7. Save the project configuration.
8. Use the same configuration for editor and automated audits.

---

## GA-09 Experimental Rule

**GA-09 — Read-Before-Write** is experimental.

Recommended use:

1. Enable the rule for a focused review.
2. Inspect each reported graph manually.
3. Confirm the actual attribute or data-flow order.
4. Do not treat an experimental finding as automatic proof of a graph defect.

---

Previous: [04 — Audit Rule Reference](04_Audit_Rule_Reference.md) · [Documentation Index](INDEX.md) · Next: [06 — Reports and Exports](06_Reports_And_Exports.md)
