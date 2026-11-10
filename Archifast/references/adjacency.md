# Adjacency Matrix Template

Relationship codes: `ADJ` adjacent (share wall/door) · `NEAR` same zone, ≤1 room apart · `SEP` separated (must not adjoin) · `VIS` visual/open connection · `SVC` service access only · `—` none required.

## Standard residential matrix

Rows = from, columns = to. Upper triangle only (symmetric unless noted).

| | Living | Dining | Kitchen | Family | Master BR | BR2+ | Bath | Laundry | Foyer | Carport |
|---|---|---|---|---|---|---|---|---|---|---|
| **Living** | — | ADJ | NEAR | ADJ | SEP | NEAR | SVC | — | ADJ | NEAR |
| **Dining** | | — | ADJ | ADJ | SEP | — | SVC | NEAR | NEAR | — |
| **Kitchen** | | | — | NEAR | SEP | — | ADJ | ADJ | SVC | NEAR |
| **Family** | | | | — | NEAR | NEAR | ADJ | NEAR | — | — |
| **Master BR** | | | | | — | NEAR | ADJ | SEP | SEP | SEP |
| **Bed rooms** | | | | | | — | ADJ | SEP | SEP | SEP |
| **Bathrooms** | | | | | | | — | ADJ | SVC | — |
| **Laundry** | | | | | | | | — | SVC | — |
| **Foyer** | | | | | | | | | — | ADJ |
| **Carport** | | | | | | | | | | — |

## Rules extracted

- **Kitchen ↔ dining ↔ living:** ADJ/NEAR — serving flow.
- **Kitchen ↔ laundry ↔ bathroom:** cluster (wet wall sharing, plumbing efficiency).
- **Bedrooms ↔ bathrooms:** ADJ (ensuite or shared access); bedrooms SEP from living/kitchen noise sources.
- **Bedrooms ↔ street/carport:** SEP — acoustic and privacy buffer (garden, service zone, or extra room between).
- **Foyer ↔ carport:** ADJ — arrival sequence.
- **Foyer ↔ living:** ADJ/VIS — greeting sightline; SEP from bedrooms.
- **Prayer room / entry porch (ID homes):** ADJ to foyer, NEAR to living.

## Workflow

1. Copy matrix; add/remove rooms per program.
2. Assign codes for every required pair; `—` elsewhere.
3. Check consistency: no room ADJ to two SEP-locked zones simultaneously.
4. Draw bubble diagram grouping ADJ clusters; SEP pairs must land in different bubbles.
5. Translate to plan; verify each ADJ pair actually shares wall/door proximity.
6. Record satisfied vs. traded-off adjacencies in the delivery notes.

## Common trade-off log format

| Pair | Required | Achieved | Resolution |
|---|---|---|---|
| Kitchen–Dining | ADJ | NEAR via corridor | widened opening; acceptable |
| BR2–Bath | ADJ | shared bath ADJ | ensuite deferred to phase 2 |
