# Observability Implementation

## Default Stack

- metrics: Prometheus-compatible clients to VictoriaMetrics
- logs: structured JSON to Loki
- traces: OpenTelemetry to Tempo
- visualization: Grafana
- alerting: Alertmanager or Grafana alerting

## Deliverable Shape

Return:

1. the implementation
2. an Observability section

The Observability section should include:

- key metrics
- critical alerts
- dashboard panel suggestions
- at least one LogQL query
- key trace attributes or events

## Metric Naming

- counters: `<service>_<subsystem>_<operation>_<unit>_total`
- histograms: `<service>_<subsystem>_<operation>_duration_seconds`
- gauges: `<service>_<subsystem>_<resource>_<state>`

Use consistent labels such as `service`, `env`, `version`, plus operation-specific labels.

## Structured Log Fields

Every log record should include:

- `timestamp`
- `level`
- `service`
- `trace_id`
- `span_id`
- `msg`
- domain-specific context

## Quality Checks

- every important operation has a span
- errors are logged with context
- external calls are measured
- metric labels are consistent
- no silent error swallowing
