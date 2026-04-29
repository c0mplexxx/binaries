# Workspace Rules

## Purpose

This workspace is a context store inside the user's Obsidian vault. It preserves plans, investigations, decisions, and references across sessions so future work can resume with minimal rereading.

## Entry Point

Always read `/Users/mbarinov/Documents/ObsidiavVault/Codex/MOC.md` first. It is the authoritative index for current Codex work and exists specifically to prevent blind directory scans.

Historical notes may still live in `/Users/mbarinov/Documents/ObsidiavVault/Claude/` and remain linked from `Codex/MOC.md` via relative paths such as `[[../Claude/note-name]]`.

## MOC Format

- One line per note.
- Format: `- [[filename]] — type | status — one-line description`
- Add the line when creating a note.
- Update the line when a note changes status or meaningfully changes scope.
- New notes should normally be created under `/Users/mbarinov/Documents/ObsidiavVault/Codex/`.

## Note Structure

Every durable note should contain:

```md
---
type: plan | investigation | reference | decision
status: active | paused | done
related: ["other-note.md", ...]
---

## TL;DR
2–3 sentences with the note's purpose and current conclusion or state.
```

`TL;DR` is the first section to read when deciding whether the note matters.

## Reading Strategy

1. Read the matching MOC line.
2. Read the target note's frontmatter.
3. Read the `TL;DR`.
4. Only then read deeper sections if the current task needs them.

## Cross-Workspace Rule

- Use `Codex/MOC.md` as the primary index for new Codex sessions.
- Preserve links to historical `Claude/` notes instead of mass-copying them.
- Migrate a `Claude/` note into `Codex/` only when the note needs substantial new work or a clear ownership change.

## Naming

Use stable, technical filenames such as:

- `mlx5-rx-drop-investigation.md`
- `netplan-bond-plan.md`
- `dosgate-master-agent-architecture.md`

Pattern: `<topic>-<subtype>.md`
