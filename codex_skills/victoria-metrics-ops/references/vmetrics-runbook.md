# VictoriaMetrics Runbook

## Contents

- Data Path
- Hard Constraints
- Environment Checklist
- First 30 Seconds
- Symptom Map
- Replay Rules
- Destructive Actions
- Cluster-Health Checklist
- Output Style

## Data Path

```text
vmagent -> vminsert -> vmstorage -> vmselect -> Grafana / vmalert
```

Always identify the failing hop before proposing a fix.

## Hard Constraints

1. Explain before acting.
2. Ask for environment details if cluster, tenant, or prod-vs-lab scope is unclear.
3. Default to read-only checks first.
4. Name the trade-off of every flag change.
5. Verify metric and flag names instead of guessing.

## Environment Checklist

Confirm or infer:

- cluster shape
- endpoints for vmagent, vminsert, vmstorage, vmselect, vmalert
- tenant ID
- lab or production
- application version

## First 30 Seconds

```bash
curl -s http://<vmstorage>:8482/metrics | grep -E '^(vm_rows_inserted_total|vm_slow_row_inserts_total|vm_free_disk_space_bytes|vm_active_merges|vm_rows_ignored_total)'
curl -s http://<vmagent>:8429/metrics | grep -E '^(vmagent_remotewrite_pending_data_bytes|vmagent_remotewrite_packets_dropped_total|vm_promscrape_targets)'
curl -s http://<vminsert>:8480/metrics | grep -E '^(vm_rpc_send_duration_seconds_sum|vm_rpc_errors_total)'
curl -s http://<vmselect>:8481/metrics | grep -E '^(vm_request_duration_seconds|vm_concurrent_select|vm_cache_size_bytes)'
curl -s 'http://<vmselect>:8481/select/<TENANT>/prometheus/api/v1/status/tsdb?topN=20'
```

## Symptom Map

### Stale or Delayed Data

- Check whether data is missing or only hidden by `rawRows` buffering plus `-search.latencyOffset`.
- If freshness matters more than stability, consider the trade-off before lowering offsets or disabling cache.

### Query Latency or Timeout

- Check `vm_request_duration_seconds`, concurrency, cache pressure, and expensive query patterns.
- Nested subqueries and unstable `topk` patterns are common causes.

### Insert Slow or Failing

- Inspect `vm_slow_row_inserts_total`, RPC errors, and vmagent backlog.
- Separate source backlog from storage-node pressure.

### Disk Pressure or Merge Stall

- Check free disk space, active merges, and part growth.
- Low free space can stall merges and amplify latency cluster-wide.

### vmagent Backlog Growing

- Inspect `pending_data_bytes`, packet drops, queue sizing, and downstream availability.
- Decide whether backlog, throttling, or loss is acceptable for the scenario.

### vmalert Rules Misfiring

- Check evaluation delay against query latency offset.
- Flapping alerts often come from mismatched timing assumptions.

## Replay Rules

- `-replay.maxDatapointsPerQuery` is in minutes, not points.
- Start with `1080` as the mixed-workload safe default.
- Keep `-replay.ruleEvaluationConcurrency=1` unless low cardinality is proven.
- Raise `-search.maxSamplesPerQuery` on vmselect for replay if sample budget is the problem.
- If the error says memory is insufficient, reduce batch size instead of raising sample budget.
- During replay, use `-search.disableCache=true` and avoid heavy diagnostic `query_range` calls on the same vmselect.

## Destructive Actions

Ask explicitly before:

- `force_merge`
- `delete_series`
- `force_flush`
- retention cuts
- `-dropSamplesOnOverload`
- restarts
- restore operations

For each action, state:

1. purpose
2. blast radius
3. rollback or recovery assumptions

## Cluster-Health Checklist

1. ingestion rate
2. slow inserts
3. free disk
4. resident memory
5. remote-write backlog
6. query latency
7. RPC errors

## Output Style

- State the hop first.
- Show the metric or log line that supports the diagnosis.
- Give the next safe step, not a monograph.
- Be terse.
