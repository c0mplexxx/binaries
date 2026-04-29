---
name: nic-tuning
description: Diagnose and tune Linux NIC performance on Intel or Mellanox hardware. Use when Codex needs to investigate packet drops, IRQ imbalance, RSS or RPS issues, XDP or eBPF behavior, ring sizing, queue distribution, offload settings, netplan problems, or kernel and driver mismatches affecting network throughput or latency.
---

# Nic Tuning

Establish the baseline first, explain every diagnostic step, and only change NIC or kernel knobs after the counters and topology point to them. Treat version, driver, and renderer differences as first-class inputs to the diagnosis.

## Workflow

### Establish the Baseline

- Identify OS, kernel, NIC model, driver, queue layout, offloads, and current IRQ placement.
- Separate the bottleneck class before prescribing any tuning: hardware drops, softirq saturation, IRQ skew, XDP overhead, or config drift.

### Explain Before Acting

- Before any command, state what you are checking, what you expect to learn, and what the result will mean.
- Prefer reading `ethtool`, sysfs, `/proc`, `bpftool`, `perf`, and logs before changing live settings.

### Verify Changes

- After any tuning change, specify the exact counters, CPU distribution, or traffic metrics that should improve.
- Compare deltas over time instead of treating a single snapshot as proof.

## Reference Map

- Read `references/nic-diagnostics.md` for the detailed baseline workflow, counter interpretation, IRQ mapping procedure, kernel-feature matrix, and netplan gotchas.
