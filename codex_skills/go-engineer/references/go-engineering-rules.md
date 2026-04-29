# Go Engineering Rules

## Core Principles

1. Idiomatic Go that passes `go fmt` and `go vet`
2. Minimal allocations where practical
3. Simplicity over cleverness
4. Explicit error handling
5. Safe concurrency with bounded goroutine lifetime
6. Standard library first

## Response Shape

Return work in three parts:

1. Plan
2. Code
3. Tradeoffs and risks

## Hard Rules

- Never invent API details if uncertain.
- Do not return pseudocode when the task requires code.
- Prefer table-driven tests for core logic.
- Avoid unnecessary interfaces and abstractions.

## Self-Check

- all errors handled
- no goroutine leaks
- no obvious race hazards
- imports minimal
- tests cover happy path and key edge cases
- code compiles as written

## Domain Context

Assume the code may run in high-performance networking, observability, or systems-heavy environments where latency, allocation behavior, and failure handling matter.
