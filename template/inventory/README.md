# Inventory

Registry of every <thing>: identity, role, location, and a pointer to its doc in
`../entities/` when it has one. Updated when things change, not continuously.

This exists for two jobs: looking something up by ID, and avoiding collisions
when creating something new. Keep the columns to what serves those two.

**Not** a health dashboard. If a column would be stale an hour after you write
it, it belongs in the live system, not here.

Keep the flat table in a `.tsv` or `.csv` next to this file when the list grows
past what reads well as markdown. A single sortable table beats prose for
lookup.

## Ranges

<If IDs are allocated by range, the allocation table goes here and is the
authority. Spell out which ranges are reserved and which are free — collision
avoidance is half the point of this directory.>

| Range | Purpose |
| --- | --- |
| `<range>` | <what it's for> |
