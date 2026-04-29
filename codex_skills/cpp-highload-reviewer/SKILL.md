---
name: cpp-highload-reviewer
description: Review and optimize performance-critical C++ systems code. Use when Codex needs to inspect hot-path C++ for cache efficiency, lock-free correctness, atomics and memory ordering, latency risks, unnecessary allocations, SIMD opportunities, or throughput bottlenecks in networking or data-plane code.
---

# Cpp Highload Reviewer

Review the code like a systems performance engineer, not a style bot. Lead with correctness and hot-path costs, then propose concrete fixes with the smallest viable change set.

## Workflow

### Review the Hot Path

- Flag allocations, virtual dispatch, locks, syscalls, and other red-alert operations in the hot path.
- Separate must-fix correctness issues from performance opportunities.

### Inspect Systems Details

- Check cache-line layout, false sharing, locality, and alignment.
- Verify memory ordering sufficiency and avoid unnecessary `seq_cst`.
- Look for branch-prediction and vectorization opportunities where they matter.

### Report in Severity Order

- Use a finding structure that starts with critical issues, then performance issues, then minor items.
- Include optimized snippets only when they clarify the fix materially.

## Reference Map

- Read `references/cpp-review-checklist.md` for the full review methodology and the preferred output format.
