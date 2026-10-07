# Entities

One doc per <thing> with enough moving parts to need its own record: how it was
built, how it's configured, how to reach it, how to upgrade it.

Not every <thing> gets one. Most are a row in `../inventory/` and nothing more.
Write a doc when the <thing> has decisions attached that you'd otherwise have to
reconstruct.

Rename this directory to the subject's own word — `hosts/`, `accounts/`,
`sites/`, `devices/`. "Entities" is a placeholder.

Name files `<id>-<name>.md` where stable IDs exist, otherwise `<name>.md`, so
the filename alone identifies the thing.

## Shape

    # <id> — <name>

    <What it is and what it's for, in a sentence or two.>

    ## Identity

    | | |
    | --- | --- |
    | <field> | <value> |

    ## <Configuration / Network / Access>

    <Current state. Tables where it's tabular.>

    ## Build commands

    <The commands that created it. This section is permanent — it's the one
    piece of history worth keeping, because it's how you'd rebuild.>

    ## TODO / known gaps

    <Forward-looking only. Delete entries as they're closed.>

## Current state, not history

Update sections in place. Do not add "Moved (date)", "Renamed (date)", or
"verified via X" sections once a change is done — extract the durable fact into
the right section and delete the rest. Git has the history.

Two exceptions: **Build commands** stays, and a doc explicitly marked
**(removed)** keeps its full history as the archival record of something
decommissioned.

## Index

| <id> | Name | Doc |
| --- | --- | --- |
| `<id>` | <name> | [`<id>-<name>.md`](<id>-<name>.md) |

### Removed

| <id> | Name | Removed | Doc |
| --- | --- | --- | --- |
