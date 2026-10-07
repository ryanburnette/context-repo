# <subject>-ops

<One or two sentences: what subject this repo covers and what it's for.>

This is a context repo, not a code repo: docs and scripts that document and
reproduce the state of <subject>. No secrets are committed.

Work directly on `main`. <Or: feature branches and PRs — pick one and say which.>

## What lives here

Delete the lines you don't use. Rename directories to this subject's own
vocabulary.

- `environments/` — per-<target> structure: <what distinguishes one target from
  another>, how it's reached, what lives on it. Not live health; read that from
  the system.
- `inventory/` — registry of <things>: identity, role, and location. For lookup
  and collision avoidance, not a dashboard. Updated when things change, not
  continuously.
- `entities/` — one doc per <thing> with enough moving parts to need a record.
  Not every <thing> has one. Name as `<id>-<name>.md`.
- `runbooks/` — repeatable procedures as numbered step lists, meant to be
  followed top to bottom.
- `.agents/skills/` — skill submodules.

## Targets

<Every place work can land. The agent must confirm which one a task means before
running anything; commands are not interchangeable across them.>

| Alias | How it's reached | Notes |
| --- | --- | --- |
| `<alias>` | `<command or address>` | <status, scope, which doc covers it> |
| `<alias>` | — | **decommissioned <date>** — history in `environments/<name>.md` |

## Conventions

<The decisions already made, so they aren't re-litigated each session. Each one
is a rule an agent can check its own work against. Delete this heading if the
subject has none yet; do not fill it with generic advice.>

- <Naming and numbering schemes, with the reserved ranges spelled out.>
- <Defaults a new <thing> inherits, and the reason, so an exception is visible
  as an exception.>
- <A thing that looks correct but isn't, with what actually happens.>
- Docs describe current state, not how it got there. When something is moved,
  renamed, or reconfigured, update the relevant section in place rather than
  adding a dated section narrating the change. Extract the durable fact, delete
  the process narrative.

## Running commands

Commands run against <target> must be non-destructive and strictly
information-gathering: `<read-only command>`, `<read-only command>`, and the
like. Never run a mutating command unprompted.

When a task requires changing something, the agent must:

1. Write out a plan: the exact commands, in order, with the target and affected
   <thing> called out explicitly.
2. Read the target's current state back (`<read-back command>`) and confirm it
   matches what the user expects.
3. Stop and wait for the user to review and explicitly confirm before running
   any of it.

Run the plan one logical step at a time and stop again if anything looks off.

## Destructive operations

<There is no rollback point on a live system. Before any mutation:>

1. Confirm the target.
2. Read back the affected <thing> and confirm it is the right one.
3. Check for collisions before creating anything.
4. Run one logical step at a time and stop for approval on anything that
   creates, destroys, or resizes.

## Off-limits

<Name anything the agent must not touch, and say so plainly. "Do not connect to
X" is a rule an agent can follow; "be careful with X" is not. Include the
exceptions — a host that is off-limits may still have things on it that are fine
to reach directly when the user asks.>

<Delete this section if nothing is off-limits. Do not leave it empty.>

## Credentials

No credentials are committed. Locations only:

- <what>: _TODO (password manager location)_
- <what>: _TODO_

## Skills to load

- `skill:git-workflow` before any git operation in this repo.
- `skill:shell-scripting` for any `.sh` file or inline command list.
- `skill:prose` when editing docs here.
- `skill:<name>` (submodule at `.agents/skills/<name>`) before any <task> work.
  Put reusable lessons in that skill; keep this subject's specifics here.
