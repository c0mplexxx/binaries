# Highload Architecture Playbook

## Design Methodology

### Phase 1: Requirements Clarification

Collect:

- events or requests per second
- ingress volume
- latency targets
- consistency model
- operational constraints
- schema and cardinality shape

### Phase 2: Architecture Design

Present:

1. TL;DR
2. component topology
3. single-item data flow
4. critical design decisions
5. failure modes and mitigations
6. scaling path
7. operational considerations

### Phase 3: Review and Validation

- identify the critical path
- rank bottlenecks by severity
- prefer incremental redesign paths where possible

## Technology Selection Rules

- Prefer boring technology on the critical path.
- Match storage to access pattern.
- Avoid distributed transactions where possible.
- Add kernel-bypass complexity only when profiling proves it matters.
- Backpressure is mandatory in every queue or pipeline.

## Quality Gates

- peak load covered with headroom
- failure isolation is clear
- backpressure or shedding exists
- stateful pieces have replication or recovery paths
- complexity matches scale
- assumptions are explicit
