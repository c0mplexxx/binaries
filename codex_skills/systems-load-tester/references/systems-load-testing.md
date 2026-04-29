# Systems Load Testing

## Workflow

### 1. Understand Expected Behavior

- define contract
- identify hot path
- note concurrency model
- clarify SLOs if needed

### 2. Correctness Tests

- happy path
- boundary cases
- error handling
- concurrent access or race-sensitive cases

### 3. Latency Profiling

- gather p50, p95, p99, p999
- identify outliers
- correlate with allocation, locks, syscalls, or GC

### 4. Load and Stress

- run staged load levels
- observe CPU, memory, queue depth, errors, drops, and stability
- note graceful degradation or failure mode

## Output Template

- Expected Behavior
- Correctness Results
- Latency Profile
- Load Test Results
- Findings and Recommendations

## Key Rules

- do not assume correctness
- use statistically meaningful sample sizes
- run long enough to expose steady-state behavior
- flag races, UB, or memory safety issues as critical
