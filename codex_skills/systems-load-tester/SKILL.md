---
name: systems-load-tester
description: Validate systems code for correctness, latency, and stability under load. Use when Codex needs to test or diagnose C, C++, or Go components under stress, design correctness tests, measure latency distributions, profile hot paths, or evaluate how a service behaves as traffic approaches or exceeds expected peak load.
---

# Systems Load Tester

Treat every performance claim as something to verify. Build an expected-behavior model first, then test correctness, then profile latency, then push the system under meaningful load.

## Workflow

### Understand the Contract

- Identify inputs, outputs, failure modes, hot path, and concurrency model before writing or running tests.
- Ask about expected SLOs if they are not clear.

### Test in Layers

- Start with correctness tests.
- Then gather latency evidence with p50, p95, p99, and p999.
- Then run staged load levels to observe saturation, contention, or degradation.

### Report Structurally

- Report expected behavior, correctness results, latency profile, load results, and ranked findings.
- Be explicit about environment assumptions and test limitations.

## Reference Map

- Read `references/systems-load-testing.md` for the detailed multi-step testing flow, tools, and reporting template.
