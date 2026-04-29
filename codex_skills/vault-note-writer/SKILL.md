---
name: vault-note-writer
description: Create and update Obsidian notes in the user's house style with frontmatter fields `type`, `status`, and `related`, a short `TL;DR`, and synchronized MOC entries. Use when Codex needs to create a new durable note in `/Users/mbarinov/Documents/ObsidiavVault/Codex/`, update an existing vault note, close or archive a note, or record an architectural change durably.
---

# Vault Note Writer

Write notes that are easy to resume later and cheap to navigate. Keep every note aligned to the template and update `Codex/MOC.md` immediately when note state changes.

## Workflow

### Create a Note

1. Decide whether this belongs in an existing note before creating a new file.
2. Choose `type` from `plan`, `investigation`, `reference`, or `decision`.
3. Choose `status` from `active`, `paused`, or `done`.
4. By default create the file under `/Users/mbarinov/Documents/ObsidiavVault/Codex/` unless an existing note elsewhere already owns the topic.
5. Start from `assets/note-template.md`.
6. Write a 2-3 sentence `TL;DR` that lets a future session decide relevance quickly.
7. Add or update the `Codex/MOC.md` line in the same edit pass.
8. If the note should stay visible from the historical `Claude/` index, add or update the matching `Claude/MOC.md` entry too.

### Update a Note

- Keep the frontmatter in sync with the actual state of the work.
- Refresh the `TL;DR` when the note's conclusion or current state changes materially.
- Add `related` links only when they improve navigation.
- When a Codex note supersedes a `Claude/` note, keep the cross-link explicit in `related`.

### Handle Architecture Notes

- When architecture changes, identify the topic directory under `/Users/mbarinov/Documents/ObsidiavVault/`.
- Create or update `{topic}-architecture.md`.
- Update `/Users/mbarinov/Documents/ObsidiavVault/Codex/MOC.md` if the note becomes part of the current ongoing context.
- Update `/Users/mbarinov/Documents/ObsidiavVault/Claude/MOC.md` only if the note also belongs in the shared historical context.

## Writing Rules

- Use the exact house frontmatter fields: `type`, `status`, `related`.
- Keep filenames descriptive and stable: `<topic>-<subtype>.md`.
- Prefer short, technical, resumable prose over essay-style notes.
- Do not create a new note for a tiny update if an existing note already owns that topic.
- Follow the `CLAUDE.md` note discipline: read the MOC first, keep `TL;DR` decisive, and maintain the MOC line immediately when note state changes.

## Reference Map

- Read `references/note-rules.md` for the canonical note structure, MOC line format, and close/archive rules.
- Use `assets/note-template.md` as the starting point for new notes.
