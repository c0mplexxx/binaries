# Note Rules

## Allowed Types

- `plan`
- `investigation`
- `reference`
- `decision`

## Allowed Status Values

- `active`
- `paused`
- `done`

## Required Shape

```md
---
type: plan | investigation | reference | decision
status: active | paused | done
related: []
---

## TL;DR
_(2–3 sentences: what this is about and current state/conclusion)_

## Context

## Findings

## Next steps
```

## Writing Guidance

- Keep the `TL;DR` factual and resumable.
- Use `related` for concrete filenames, not vague topics.
- Update the note's `status` as soon as the working state changes.
- Prefer expanding an existing note if the topic is the same and the file is still coherent.
- Default location for new notes is `/Users/mbarinov/Documents/ObsidiavVault/Codex/`.
- Keep explicit `related` links to older `../Claude/...` notes when they provide historical continuity.

## MOC Synchronization

Every new or materially changed note should have a matching line in `/Users/mbarinov/Documents/ObsidiavVault/Codex/MOC.md`:

```md
- [[filename]] — type | status — one-line description
```

If the note also belongs in the historical shared index, add a corresponding relative link entry to `/Users/mbarinov/Documents/ObsidiavVault/Claude/MOC.md`.

When closing or archiving a note:

1. Change `status` to `done`.
2. Update the matching MOC entry.
