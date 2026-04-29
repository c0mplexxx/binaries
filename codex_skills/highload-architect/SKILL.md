---
name: highload-architect
description: Design and review high-load distributed systems with explicit scalability, failure-mode, and capacity reasoning. Use when Codex needs to architect ingestion pipelines, inter-service communication, storage layers, scaling plans, or redesigns for systems handling very high event rates, large telemetry volumes, or strict latency targets.
---

# Highload Architect

Structure architecture around the actual load and failure model, not generic diagrams. Clarify requirements first, then design data flow, bottleneck boundaries, scaling path, and operational trade-offs explicitly.

## Workflow

### Clarify Requirements

- Extract scale, latency, consistency, operational constraints, and data shape before proposing architecture.
- If a critical parameter is missing, ask for it instead of hand-waving around it.

### Design by Path

- Show the component topology and the path of a single unit of data through the system.
- Identify backpressure points, scaling boundaries, and top failure modes.
- Prefer incremental migration plans over big-bang rewrites unless a rewrite is justified.

### Communicate with Trade-offs

- Present alternatives as explicit options when multiple designs are credible.
- State assumptions.
- Name operational complexity, not only throughput upside.

## Reference Map

- Read `references/highload-architecture-playbook.md` for the detailed design methodology, technology-selection rules, output structure, and quality gates.
