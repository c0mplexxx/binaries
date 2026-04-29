---
name: grafana-dashboards
description: Inspect and modify Grafana dashboards through the HTTP API, especially when working with dashboard JSON, datasources, Infinity datasource panels, panel layout, or replay and migration dashboards. Use when Codex needs to fetch the current dashboard state safely, patch specific panels, avoid common Infinity gotchas, or automate repeatable Grafana dashboard changes without using the UI.
---

# Grafana Dashboards

Treat the Grafana API as the source of truth and avoid UI-only assumptions. Fetch the current dashboard first, extract only the fields you need, and patch dashboards with the smallest controlled JSON change.

## Workflow

### Inspect Before Editing

- Always fetch the current dashboard JSON before proposing changes.
- Do not guess dashboard `version`, panel ids, or panel placement.
- Avoid dumping raw dashboard JSON unless a specific panel requires inspection.

### Patch with Minimal Scope

- Extract only the relevant version, panel ids, titles, and layout metadata.
- Build or patch panel JSON deterministically.
- Return only the changed state and the outcome.

### Respect Secrets and Environment

- Do not embed API tokens or instance-specific secrets in skill instructions.
- Expect URL, token, and datasource identifiers to come from runtime context or explicit user input.

## Reference Map

- Read `references/grafana-api-playbook.md` for API patterns, Infinity datasource gotchas, panel construction rules, and replay-dashboard notes.
