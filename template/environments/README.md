# Environments

One doc per target: its structure, how it's reached, what lives on it, and an
index of the <things> on it.

Keep the per-<thing> rows short and push deep notes into `../entities/`, so an
environment doc stays readable as a map rather than becoming a second copy of
every record.

**Not** live state. Power, health, quorum, current load, who's connected — read
those from the system. A doc that mirrors live state is wrong silently, which is
worse than absent.

A decommissioned target keeps its doc, marked with the date it went away. The
history is why the current layout looks the way it does.

## Index

- `<name>.md`: <alias, status, one line>
