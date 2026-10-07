# Prior art

None of the ideas here are mine. This file says where each piece came from and
what that source got right, so you can go read the better version.

## The repo-as-coordination-layer

[mriechers/ops-repo](https://github.com/mriechers/ops-repo) is the closest thing
to a definition in the wild. It defines an ops repo as "a coordination layer over
N independent sibling git repos" that "houses no first-party buildable code of
its own."

That second half is the invariant I took directly. The first half is a different
pattern from this one — that template is about orchestrating work that crosses
repo boundaries, where a context repo is scoped to a subject and may have no
sibling repos at all. Same name, different shape. Worth reading on its own terms.

## Splitting files by change frequency

[rabihkodeih/agentic-workflow](https://github.com/rabihkodeih/agentic-workflow)
organizes a context repo by how often each file changes: rules of engagement
that almost never change, domain knowledge that rarely changes, current state
that changes every session. Its tiebreak rule is the good part — when domain
knowledge and current state disagree, domain knowledge wins on mechanics.

It assumes the context repo sits next to a code repo and serves work on that
code. A subject-scoped context repo has no code repo to sit next to, so the
session-log half doesn't carry over. The split itself does.

## Charter vs. runbook

[Brian Takita, "Runbooks — On-Demand Procedural
Context"](https://briantakita.me/posts/agent-runbooks-on-demand-procedural-context/)
draws the distinction this repo leans on: rules are declarative policy that shape
how the agent thinks, runbooks are imperative procedures that say what to do.
Naming them differently tells both the agent and the human what to expect.

He argues for `.agent/` singular over `.agents/`, and notes the convention is
unsettled. This template uses `.agents/` to match the harnesses I run; pick one
and be consistent.

## What goes where

[Agent Skills vs Rules Files vs Retrieved
Context](https://getunblocked.com/blog/agent-skills-vs-rules-files/) has the
cleanest decision rules: how to do something → skill; must hold on every task →
rules file; could be false in three months → don't put it in a static file at
all.

That last test is the one that prunes a context repo. Anything genuinely live —
current health, running state, who's on call — should be read from the system,
not mirrored into a doc that silently goes wrong.

## Agent-friendly is human-friendly

Shopify's [Under the River](https://shopify.engineering/under-the-river) is a
monorepo case study at a different scale, but one line generalizes: "every change
we made for agents was also the right thing for humans." It's a good test for
whether a doc belongs in the repo. If it only exists to feed a model, it's
probably the wrong artifact.

## The entry-point file

[AGENTS.md](https://agents.md/) is the convention for the root file, now under
the Linux Foundation's Agentic AI Foundation and read by most coding agents.
Agents read from the git root down to the working directory, closest file wins —
which is what makes the repo a context boundary and `cd` the act of choosing one.

The `CLAUDE.md`-imports-`AGENTS.md` shim is the settled way to serve Claude Code
without maintaining two files.

## Runbooks

Runbooks predate all of this by decades. Operations teams have written
step-by-step procedures for as long as there have been systems to operate. The
only new part is keeping them in the repo next to the thing they operate, where
an agent can load one on demand, rather than in a wiki that drifts.
