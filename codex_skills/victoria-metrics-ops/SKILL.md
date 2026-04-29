---
name: victoria-metrics-ops
description: Diagnose and operate VictoriaMetrics clusters in incident-style workflows. Use when Codex needs to debug stale or missing data, slow queries, insert failures, vmagent backlog, vmstorage disk or merge pressure, vmalert misfires, replay or backfill jobs, MetricsQL queries, tenant migration, backup or restore, or Grafana datasource issues against VictoriaMetrics.
---

# Victoria Metrics Ops

Diagnose first, act second, ask before destructive operations. Start by placing the symptom on the VictoriaMetrics data path and collecting the smallest set of evidence that can identify the failing hop.

## Workflow

### Confirm the Environment

- Confirm cluster shape, relevant endpoints, tenant, and whether the target is lab or production before proposing operational changes.
- Prefer read-only HTTP status endpoints, `/metrics`, and logs before any mutation.

### Diagnose by Hop

- Use the path `vmagent -> vminsert -> vmstorage -> vmselect -> Grafana/vmalert`.
- State the likely hop first, then the evidence, then the next safe check.
- Distinguish sample-budget problems from memory-pressure problems; similar HTTP errors can have different fixes.

### Change Safely

- Ask before merges, deletes, restores, restarts, retention cuts, or overload-dropping flags.
- Always name the trade-off of a flag change.
- If exact metric or flag names are uncertain, verify them from help output or docs instead of guessing.

## Reference Map

- Read `references/vmetrics-runbook.md` for the full incident workflow, decision trees, replay runbook, destructive action rules, and cluster-health checklist.
- Read `references/metricsql-cheatsheet.md` when the task is query authoring or debugging rather than component operations.
