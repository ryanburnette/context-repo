# context-repo

A context repo is a git repo scoped to a **subject** instead of a codebase. It
holds the runbooks, reference docs, inventories, skills, and scripts for one
area of work, and it exists so you can open a coding agent in that directory and
have it already know the terrain.

The working directory is the interface. You `cd` into the repo for the subject
you're about to work on, start the agent, and the repo tells it where it is,
what the targets are, what it may touch, and which procedures already exist.

This repo documents how I put that together and ships a skeleton you can copy.
I didn't invent any of the pieces — see [PRIOR-ART.md](PRIOR-ART.md). What's
here is an assembly, not a standard.

## When you want one

Reach for a context repo when the work is ongoing, has real-world targets, and
keeps producing procedures you'd otherwise re-derive. Infrastructure, a fleet of
servers, a vendor relationship, a certification you're studying for, a home lab.

You don't want one for a codebase. A codebase already has a repo; its agent
guidance belongs in that repo's `AGENTS.md`.

## The invariants

These are what make it a context repo rather than a pile of markdown.

1. **No first-party buildable code.** Scripts that drive something external are
   fine. An application that lives here is not. If it compiles and ships, it
   belongs in its own repo.
2. **`AGENTS.md` is the entry point.** One file at the root that states the
   scope, the targets, the conventions, and the safety rails. Everything else is
   reachable from it.
3. **Current state, not a changelog.** Update docs in place. Git already has the
   history; a doc that narrates its own edits ("moved 2026-03-04", "validated
   via…") costs context on every read and goes stale.
4. **No secrets.** Document *where* a credential lives, never the credential.
5. **Read-only by default.** The agent gathers information freely and stops
   before it changes anything. See [Safety](#safety).

## Anatomy

Not every repo needs every directory. These are the kinds that keep recurring,
with the one-line test for what belongs in each.

| Directory | Kind | Test |
| --- | --- | --- |
| `AGENTS.md` | Charter | Rules of engagement. Must hold on every task in this repo. |
| `environments/` | Targets | The distinct places work lands. Structure, access, what's where. |
| `inventory/` | Registry | Identity and collision avoidance. Not a live health dashboard. |
| `entities/` | Per-thing docs | One doc per long-lived thing with enough moving parts to need a record. |
| `runbooks/` | Procedures | Numbered steps, followed top to bottom. |
| `.agents/skills/` | Skills | Reusable procedure that outgrew this repo. Vendor as a submodule. |
| `LOCAL.md` | Local facts | True in this checkout only. Gitignored, never committed. |

Rename them to the subject's own vocabulary. An infrastructure repo's entities
might be `hosts/` and `guests/`; a vendor repo's might be `accounts/`. The test
is what stays constant.

Two distinctions that do the most work:

**Charter vs. runbook.** The charter is declarative policy that must hold on
every task; it loads every session, so keep it short. A runbook is an imperative
procedure for one task; it loads only when that task comes up, so length is
cheap. When the charter grows a numbered list, that list wants to be a runbook.

**Registry vs. per-thing doc.** The registry is one row per thing: identity,
role, where it lives. The per-thing doc is everything else. Keeping the registry
thin is what makes it readable as a single table, and most things never earn a
doc of their own.

## Safety

The part that matters most in a repo whose subject is a real system. The
pattern, stated in the charter and inherited by every session:

1. **Read-only is the default.** Name the specific read-only commands the agent
   may run unprompted. Everything else is a mutation.
2. **Mutations go plan → read back → confirm → execute.** The agent writes out
   the exact commands with the target named explicitly, reads the target's
   current state back to prove it has the right one, then stops and waits.
3. **Execute one logical step at a time**, stopping again if anything looks off.
4. **Name what's off-limits explicitly.** A system managed by hand gets a
   section saying so. "Don't touch X" is a rule an agent can follow; "be
   careful" is not.

Point 2 is the load-bearing one. Most damage from an agent in an ops context
isn't a wrong command, it's a right command aimed at the wrong target.

## Naming

The pattern is **context repo**. Individual repos are named `<subject>-ops`.

The `-ops` suffix is a useful signal: both humans and agents read it as
operational-domain rather than application code, and it sorts the repos together
in a listing. It fits when the subject is something you operate. When it isn't —
research, study, a reference collection — drop the suffix and name it for the
subject. The repo is still a context repo.

Inside, name files so the filename alone identifies the thing: `<id>-<name>.md`
where the subject has stable IDs, otherwise `<name>.md`.

## Using the template

Copy the skeleton and fill it in:

```sh
cp -r template/ ../my-subject-ops
cd ../my-subject-ops
git init -b main
```

Then work through `AGENTS.md` top to bottom. Every `<angle bracket>` is a
placeholder; every `_TODO_` is a decision you haven't made yet. Delete the
directories you don't need — an empty `inventory/` is worse than no
`inventory/`.

`CLAUDE.md` is a one-line shim that imports `AGENTS.md`, because Claude Code
auto-loads `CLAUDE.md` and most other agents read `AGENTS.md`. One source of
truth, no drift.

## Prior art

Every piece of this exists elsewhere, mostly done better in its own narrow lane.
[PRIOR-ART.md](PRIOR-ART.md) credits the specific sources and says what each one
got right.

## License

CC0. Copy it, rename it, claim it. No attribution needed.
