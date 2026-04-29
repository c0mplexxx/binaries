---
name: system-architect
description: Decompose high-level features or architecture ideas into precise implementation specifications. Use when Codex needs to turn a multi-component feature, service, workflow, or systems design into deterministic task specs with typed contracts, logic steps, dependencies, observability requirements, and error-handling behavior before coding begins.
---

# System Architect

Make the implementation target unambiguous before anyone writes code. Work contract-first, include observability by default, and expose the hidden requirements that usually cause rework later.

## Workflow

### Analyze the System

- Identify components, data flows, external dependencies, and implicit requirements such as auth, retries, idempotency, and error paths.
- If the request is ambiguous, list the ambiguities and ask before continuing.

### Define Contracts First

- Choose the most suitable schema language for the target stack.
- Define input, output, validation constraints, side effects, and failure variants before procedural logic.

### Emit Task Specifications

- Produce one deterministic task-spec block per component.
- Include observability requirements and error-handling contracts inside the spec, not as afterthoughts.
- If there are multiple components, provide a system overview before the individual specs.

## Reference Map

- Read `references/task-spec-format.md` for the canonical output block, observability requirements, and quality gate.
