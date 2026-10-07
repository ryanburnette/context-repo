# Runbooks

Repeatable procedures for <subject>, written as numbered step lists to follow
top to bottom.

A runbook is imperative: it says what to do, for one task, and it only loads
when that task comes up. Length is cheap here. Policy that must hold on *every*
task is declarative and belongs in `AGENTS.md` instead.

Write one when you've done something twice, or when doing it wrong is expensive.

## Shape

    # <Verb the thing>

    <What this produces and when to use it. Any precondition. Whether it stops
    for approval.>

    ## 0. Confirm the target

    <Which target, and what makes this procedure specific to it.>

    ## 1. Read back current state

    <Read-only commands that prove you're aimed at the right thing.>

    ## 2. <First mutating step>

    <Commands, then what the expected output looks like.>

    ## Verify

    <How you know it worked. Not "it should work" — the command and the output.>

Number the steps. A step that can't be verified is a step that gets skipped.

## Index

- `<name>.md`: <one line — what it does and when you'd reach for it>
