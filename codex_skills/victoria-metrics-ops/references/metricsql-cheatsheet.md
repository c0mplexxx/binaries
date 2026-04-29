# MetricsQL Cheatsheet

## Counter and Gauge Basics

- `rate(counter[5m])` for most counters
- `irate(counter[5m])` only for burst-sensitive inspection
- `increase(counter[5m])` for total increase over the window
- `delta(gauge[5m])` for gauges, not counters

## Rollups

- `avg_over_time`
- `min_over_time`
- `max_over_time`
- `sum_over_time`
- `count_over_time`
- `last_over_time`
- `quantile_over_time`
- `absent_over_time`

Good defaults:

- `last_over_time(metric[1m])` for replaying sparse gauge-like series
- `avg_over_time(metric[1m])` for smoothing push-style rates

## Label Helpers

- `label_replace`
- `label_join`
- `alias`
- `drop_common_labels`
- `label_copy`
- `label_del`
- `label_keep`
- `label_move`
- `label_set`

## Matching and Filling

- `on(...)`
- `ignoring(...)`
- `group_left(...)`
- `group_right(...)`
- `default 0`

## Common Gotchas

- `topk` changes membership on each step unless stabilized by a rollup
- `absent(metric)` is instant-only; use `absent_over_time(metric[5m])` for sustained absence
- `histogram_quantile` must be applied to bucket rates, not raw buckets
- `keep_metric_names` is a query operator, not a YAML field in vmalert rules

## VM-Specific Helpers

- `union(a, b)`
- `interpolate(v)`
- `remove_resets()`
- `ru(used, total)`
- `range_normalize(v)`
