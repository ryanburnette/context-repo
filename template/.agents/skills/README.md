# Skills

Skill submodules. A skill is a procedure that outgrew this repo — reusable
across subjects, versioned on its own, vendored here.

Add one when the same procedure shows up in a second context repo. Until then a
runbook is the right home; a skill that only ever has one caller is overhead.

```sh
git submodule add https://github.com/<owner>/skill-<name>.git .agents/skills/<name>
```

Then list it under "Skills to load" in `AGENTS.md`, with a line saying when to
load it.

## Split

Reusable lessons go in the skill. This subject's specifics stay in this repo —
usually in the relevant `entities/` doc. The test: would it still be true in
someone else's setup? If yes, the skill. If no, here.
