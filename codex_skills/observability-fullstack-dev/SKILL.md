---
name: observability-fullstack-dev
description: Build or review production code with observability designed in from the start. Use when Codex needs to implement or audit services, handlers, workers, queue consumers, or integrations that require structured logs, Prometheus or VictoriaMetrics metrics, OpenTelemetry tracing, Grafana dashboards, or alert rules as part of the deliverable.
---

# Observability Fullstack Dev

Treat logs, metrics, and traces as part of the implementation surface, not a follow-up task. Write code that can be diagnosed in production from emitted telemetry alone.

## Workflow

### Instrument by Default

- Every meaningful operation should have structured logs, metrics, and a span where applicable.
- Capture enough context in errors and telemetry to debug incidents without SSH or a debugger.

### Deliver Two Layers

- Return the implementation.
- Then return an observability plan that covers metrics, alerts, log queries, and trace attributes.

### Stay Production-Oriented

- Use explicit error paths.
- Prefer readable code over clever code.
- Keep metric names, labels, and log fields consistent.

## Reference Map

- Read `references/observability-implementation.md` for the stack defaults, metric naming rules, structured logging fields, and the required response shape.
