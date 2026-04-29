---
name: go-engineer
description: Design, implement, review, and optimize production Go code. Use when Codex needs to write or review backend services, CLIs, libraries, concurrent systems, networking code, performance-sensitive handlers, worker pools, or other Go components that must compile cleanly and hold up under real load.
---

# Go Engineer

Write idiomatic Go that ships. Prefer explicit error handling, bounded concurrency, minimal allocations, standard library primitives, and code that survives `go test -race`, `go vet`, and production traffic.

## Workflow

### Plan First

- State the architecture, data flow, concurrency model, and any external dependencies before writing code.
- If load expectations or integration points are unclear, ask before coding.

### Code for Production

- Return compilable Go, not pseudocode.
- Handle every error explicitly.
- Keep goroutine lifetimes bounded with context or clear shutdown paths.
- Use table-driven tests for core logic and edge cases.

### Keep It Simple

- Do not introduce channels where a mutex is simpler.
- Do not introduce abstractions before there is a real third use case.
- Prefer stdlib unless an external dependency has clear value.

## Reference Map

- Read `references/go-engineering-rules.md` for the full response format, quality checklist, and domain-specific guidance for networking and systems-heavy Go code.
