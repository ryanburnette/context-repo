# <subject>-ops

<One or two sentences: what this repo covers.> See `AGENTS.md` for conventions
and the target list.

## Layout

- `environments/` — per-<target> structure, access, and index
- `inventory/` — registry of <things> (identity, not live health)
- `entities/` — one doc per <thing> that needs its own record
- `runbooks/` — repeatable procedures as step lists
- `.agents/skills/` — skill submodules

## Targets

| Alias | Status |
| --- | --- |
| `<alias>` | <live / planned / decommissioned>; `environments/<name>.md` |

## Runbooks

| Runbook | What it covers |
| --- | --- |
| `runbooks/<name>.md` | <one line> |
