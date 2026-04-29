---
name: obsidian-moc-workspace
description: Operate inside the user's Obsidian vault with a MOC-first workflow rooted in `/Users/mbarinov/Documents/ObsidiavVault/Codex/MOC.md`, note frontmatter with type/status/related, and TL;DR-first reading. Use when Codex is resuming a vault session, continuing prior work, deciding which notes to read, reading project context, updating architecture notes, or navigating the vault without scanning directories blindly.
---

# Obsidian MOC Workspace

Use the vault as a low-token working memory system. Treat `/Users/mbarinov/Documents/ObsidiavVault/Codex/MOC.md` as the primary entrypoint, read only relevant notes, and keep the index plus note metadata consistent with every durable change.

## Quick Start

1. Open `/Users/mbarinov/Documents/ObsidiavVault/Codex/MOC.md` first.
2. Use the MOC line plus the target note's `TL;DR` to decide relevance before reading deeper.
3. Prefer updating an existing note over creating a duplicate note with overlapping scope.
4. When you create or close a note, update `Codex/MOC.md` in the same work session.

## Workflow

### Read Context

- Start with `Codex/MOC.md`; do not scan the directory blindly.
- Read the target note's frontmatter and `TL;DR` before the rest of the note.
- If a note points to related files, read only the files that matter for the current task.
- Treat relative links to `../Claude/...` as valid historical context that should remain readable from the Codex workspace.

### Maintain Context

- Keep durable conclusions in notes, not only in chat replies.
- Keep `status` current: `active`, `paused`, or `done`.
- Keep `related` useful and specific; prefer filenames that already exist.
- Prefer creating new durable notes in `/Users/mbarinov/Documents/ObsidiavVault/Codex/` unless an older note in another folder clearly still owns the topic.

### Handle Architecture Changes

- Any time an architectural component is added, changed, or removed, create or update a `{topic}-architecture.md` note in the relevant vault topic directory.
- Update `/Users/mbarinov/Documents/ObsidiavVault/Codex/MOC.md` when that architecture note becomes part of the current working context.
- If the architecture note is relevant to ongoing historical context in `Claude/`, also update `/Users/mbarinov/Documents/ObsidiavVault/Claude/MOC.md`.
- Use the standard note structure from the vault references, not ad hoc prose.

## Reading Rules

- Read broadly only when the MOC is insufficient.
- If several notes look adjacent, read the shortest decisive note first.
- Prefer exact file references over reconstructing history from memory.
- When a note is stale or misleading, correct the note rather than silently working around it.

## Reference Map

- Read `references/workspace-rules.md` for the canonical vault workflow, note structure, and MOC maintenance rules.
- Read `references/engineering-context.md` when the task needs the user's background, preferred response style, or the global architecture-documentation rule.
