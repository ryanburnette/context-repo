# context-repo

Documentation and a copyable skeleton for the context repo pattern. This repo
describes a way of organizing other repos; it operates nothing and has no
targets. Nothing here is destructive.

Work directly on `main`.

## What lives here

- `README.md` — the pattern: what a context repo is, its invariants, anatomy,
  safety contract, and naming.
- `PRIOR-ART.md` — credit for every borrowed idea, with what each source got
  right. Add to this rather than quietly absorbing a source.
- `template/` — the skeleton users copy. Every file in it is a placeholder
  someone will fill in.

## Public repo

This is public. It must stay free of anything specific to the systems that
inspired it: no hostnames, IP addresses, domains, VM or device IDs, serial
numbers, account names, or internal topology. Examples use `<angle bracket>`
placeholders or obviously-fake values.

When adding an example, write it from the generic case. Do not paste from a real
repo and redact.

## Editing the template

`template/` is read by people starting a new repo, so it carries a different
burden than documentation:

- Every placeholder is `<angle brackets>` for a value, `_TODO_` for a decision.
  Both are meant to be conspicuous enough that an unfilled one is obvious.
- Each directory keeps a `README.md` stating what belongs there and what doesn't.
  The "what doesn't" half is what keeps the directory from becoming a junk
  drawer.
- Prefer deleting a section over leaving it vague. A user who copies this is
  better served by four sharp directories than nine hedged ones.
- `template/AGENTS.md` is the most-read file in the project. Keep it short enough
  to read in one sitting and specific enough to be fillable.

## Keep the two layers separate

The root files explain the pattern. The `template/` files *are* the pattern. A
rationale paragraph belongs in `README.md`, not in `template/AGENTS.md` where it
will be copied into every repo and loaded into every session.

## Skills to load

- `skill:git-workflow` before any git operation in this repo.
- `skill:prose` when editing any markdown here. All of it is prose someone reads.
- `skill:shell-scripting` for any `.sh` file.
