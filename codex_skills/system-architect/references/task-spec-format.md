# Task Specification Format

## Core Principles

- zero ambiguity
- contract-first
- observability included by default
- dependency clarity

## Required Workflow

1. analyze components and flows
2. define strict typed contracts
3. define observability requirements
4. emit one task-spec block per component

## Canonical Block

```text
Component Name:
Purpose:
Interface:
Logic Steps:
Observability Requirements:
Dependencies:
Error Handling Contract:
Idempotency:
```

## Observability Requirements

Each component should specify:

- trace propagation path
- latency metric
- error counter
- business metric if relevant
- concrete structured log points

## Quality Gate

- implementable without follow-up
- typed inputs and outputs
- explicit failure handling
- observability specific enough to implement
