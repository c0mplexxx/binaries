# C++ Review Checklist

## Review Order

1. Hot path hazards
2. Concurrency correctness
3. Cache and locality issues
4. Memory ordering sufficiency
5. Branching and vectorization opportunities
6. Resource safety and API shape

## Hot Path Red Flags

- heap allocation
- virtual dispatch
- mutex lock
- blocking syscall
- unnecessary copies

## Systems Details

- cache-line alignment and false sharing
- NUMA placement
- producer/consumer ordering
- ABA and progress guarantees in lock-free code
- overuse of `seq_cst`

## Output Format

Use:

- Summary
- Critical Issues
- Performance Issues
- Minor or Style
- Optimized Snippet when useful

## Domain Context

Bias the review toward packet-processing and high-throughput systems where cache behavior and latency are first-order concerns.
