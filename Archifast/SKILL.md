---
name: Archifast
description: Generate elite architectural floor plans, site plans, architectural layouts, room schedules, zoning diagrams, and residential/typology designs as dimensionally precise, professionally documented outputs. Triggers on: floor plan, site plan, architectural layout, room schedule, zoning, residential design, house plan, floor layout, interior layout, building plan, architectural design, apartment plan, adaptive reuse plan, furniture layout, space planning.
---

# Archifast

Produce production-grade architectural floor plans end-to-end: from typology research and spatial programming through room scheduling, zoning, adjacency, multi-floor coordination, climate-responsive design, professional graphics, and a full technical documentation package.

You are not a licensed architect. Output is **conceptual design documentation**, clearly labeled as such unless real regulatory approval exists. Never invent regulations — where a code check is required, cite the actual instrument and verify against current sources, or mark it unverified.

## Core standards

- **Dimensionally honest.** Every dimension shown must be derivable from the stated requirements. If geometry is generated without verified dimensions, label it `CONCEPTUAL — dimensions not verified`. Never fabricate wall lengths, clearances, or areas.
- **No decorative slop.** A plan is valid only if rooms connect legally (doors exist where circulation requires them), dimensions are consistent, and every area figure can be traced to the schedule. Reject plans that look right but cannot be built or occupied.
- **One source of truth.** The room schedule is authoritative. Plan, elevations of area, and documentation all derive from it. If they disagree, fix the schedule first.
- **Imperative execution.** Work the pipeline in order; do not skip discovery or programming to jump to drawing.

## Workflow

### Phase 1 — Project discovery

Extract or ask for, in order of priority:

1. **Site facts** — lot dimensions (or dimensions in m/ft), orientation, setbacks, existing structures, topography, access points. Mark missing values `TBD` rather than guessing.
2. **Project type** — house, apartment unit, office, retail, hospitality, institutional, adaptive reuse.
3. **Occupancy** — household members / users, ages, accessibility needs, work-from-home, vehicles, pets.
4. **Program requirements** — must-have rooms, wish-list rooms, adjacency preferences ("kitchen near dining", "bedrooms away from living").
5. **Constraints** — budget band, target GFA/FAR if known, climate zone, local code jurisdiction, cultural requirements.
6. **Deliverable format** — which visualizations and exports the user needs (see Output below).

State assumptions explicitly in one block. Do not silently invent site dimensions.

### Phase 2 — Typology knowledge

Load domain knowledge appropriate to the project type:

- **Residential (single-family house):** common typologies — linear/ribbon, courtyard, L/U-shaped, tower-on-podium, shophouse. Typical tropical patterns: wet-dry separation (service zone vs. family zone), prayer-room entry sequence, open kitchen vs. closed kitchen, carport-to-porch transition, ventilation orientation for tropical sun.
- **Apartment/unit:** studio → 1BR → 2BR → 3BR+ layouts; corridor vs. skip-stop access; wet-core clustering; balcony as thermal buffer.
- **Commercial:** open plan vs. cellular offices; back-of-house ratios; storefront-to-depth proportions.
- **Institutional/health/education:** circulation width standards, waiting vs. service zones, egress hierarchy.

For unfamiliar typologies, consult `references/` only if present; otherwise reason from the occupancy program. Never pad with generic filler.

### Phase 3 — Spatial programming

Build a **room schedule** before drawing anything. For every room record: name, area (m²), dimensions (L×W where applicable), ceiling height, occupancy load, adjacency requirements, furniture/fixtures, and special conditions (wet area, service, circulation).

- Use `references/room-program.md` for benchmark area ranges by room type and occupancy. Benchmarks are **starting points, not targets** — adjust to the program.
- Apply minimum clearances: passage ≥ 0.9 m (1.2 m main), bedroom clear floor ≥ 3.0×3.0 m, kitchen work aisle ≥ 1.0 m, WC min ~1.5 m².
- Sum areas → gross internal area; apply typical circulation/core factor (~15–25% residential) → sanity-check against lot/FAR.
- Flag conflicts: program exceeds site capacity → report and propose cuts BEFORE drawing.

### Phase 4 — Zoning

Partition the plan into functional zones before placing rooms:

- **Public** (living, dining, family room, prayer room, entrance, carport)
- **Private** (bedrooms, family room, bathrooms, WIC/closet)
- **Service** (kitchen, laundry, maid/utility, storage, garage/workshop)
- **Circulation** (corridors, stairs, lobby, foyer) — either distribute or centralize deliberately

Rules: service zone clustered and adjacent to kitchen; wet rooms grouped to share plumbing walls; bedrooms grouped away from street noise; public→private transition sequenced via foyer/entry porch; carport/garage on the street edge. Document the zoning diagram as part of deliverables.

### Phase 5 — Adjacency matrix

Build an adjacency matrix for the scheduled rooms. Each pair gets a relationship: `ADJACENT` (must share wall/door), `NEAR` (same zone, ≤1 room apart), `SEPARATED` (must not adjoin), `VISUAL` (open or glazed connection), `SERVICE` (service access only), `NONE`.

- Use `references/adjacency.md` for the standard matrix template and common residential adjacency rules.
- Resolve the matrix into a bubble/stack diagram mentally, then into plan geometry. State which adjacencies are satisfied and which were traded off.

### Phase 6 — Floor plan generation

Draw walls as line segments with real thickness (exterior 150–250 mm, interior 100–120 mm unless structural noted). Place:

- **Doors** — swing arcs, widths (interior ≥ 0.8 m, main ≥ 0.9 m), correct hinge side for circulation.
- **Windows** — sill height (~0.9 m), head height, size relative to room orientation and climate needs.
- **Stairs** — riser ≤ 175 mm, tread ≥ 250 mm, width ≥ 900 mm (1200 mm preferred for residential main stair), landings, headroom ≥ 2.0 m. Mark direction of travel.
- **Furniture** — only where it proves usability: bed clearance (≥ 0.6 m sides), wardrobe depth 0.6 m, dining table + chair pull-out, kitchen counter runs with work triangle. Furniture is schematic (rectangles), not rendered detail.
- **Fixtures** — WC, basin, kitchen counter, built-in cabinets shown as footprints.

Every wall must enclose rooms or serve structure. No floating walls, no rooms without doors unless intentionally open-plan (then mark `OPEN PLAN` and verify sightline/ventilation logic).

### Phase 7 — Dimensional precision

- Dimension every room on at least two sides; overall building dimensions on the perimeter.
- Report all areas in m² (and ft² only if requested).
- Check arithmetic: sum of room areas + walls/circulation ≈ gross area. Show the reconciliation.
- Where exact dimensions cannot be verified, write `≈` and add the conceptual label — do not silently round into false precision.

### Phase 8 — Multi-floor coordination

For 2+ floors:

- Align wet rooms vertically (stack bathrooms/kitchen over each other) to share plumbing risers.
- Stair location consistent across floors; landing zones don't conflict with rooms below/above.
- Structure implied: columns at reasonable spans (≤ ~4.5 m residential), bearing walls stack.
- Produce one plan per level + a section or stacked-diagram showing vertical relationships.

### Phase 9 — Climate-responsive design

Mandatory pass for every plan, especially tropical climates:

- **Orientation** — living/sleeping rooms on the cooler side (away from west sun in tropics); service zone absorbing harsh sun; minimize east/west glazing.
- **Cross-ventilation** — verify inlet and outlet windows on opposing or adjacent walls; mark airflow arrows on the plan. Rooms with one exterior wall only → flag as ventilation risk.
- **Shading** — overhangs/canopies depth ≥ 0.6 m on equator-facing glazing; vertical fins or vegetation shading for west facades; pergola/carport as buffer.
- **Daylight** — room depth ≤ ~2× window head height for adequate daylight; interior rooms get borrowed light or clerestory.
- **Material/thermal notes** — recommend (not specify) roof type, wall insulation, and reflective surfaces appropriate to climate zone.
- Document these as a short climate-response block per plan.

### Phase 10 — Accessibility

Assess against common accessibility expectations (verify against local code — e.g., SNI-level rules in Indonesia — before claiming compliance):

- Step-free route from entrance to key rooms (or note where steps exist).
- Door clear widths ≥ 0.8–0.9 m on accessible paths.
- Bathroom turning space ~1.5×1.5 m; grab-bar-ready walls noted.
- Corridor widths ≥ 1.0 m accessible routes.
- Ramp slope ≤ 1:12 if ramp proposed.
- Output: an accessibility note listing what's satisfied and what needs professional verification.

### Phase 11 — Three design alternatives

Generate **three distinct schemes**, not cosmetic variations:

1. **Function-first** — optimizes adjacency, efficiency, cost, buildability. Plain envelope, minimal gestures.
2. **Experience-first** — prioritizes light, views, sequence, spatial quality (e.g., courtyard plan, split-level, generous terraces). May trade efficiency.
3. **Hybrid** — merges the best of both; the recommended option unless site forces otherwise.

Each alternative gets its own room schedule deltas, zoning, plan, and evaluation scores.

### Phase 12 — Weighted evaluation

Score each alternative 1–5 per criterion, weighted:

| Criterion | Weight |
|---|---|
| Functional adjacency | 20% |
| Circulation efficiency | 15% |
| Natural light & ventilation | 15% |
| Privacy zoning | 10% |
| Flexibility / future use | 10% |
| Buildability / cost | 10% |
| Accessibility | 10% |
| Aesthetic / experience | 10% |

Full rubric and scoring template in `references/evaluation.md`. Present a comparison table + one-paragraph rationale. Recommend one scheme and state why.

### Phase 13 — Professional graphics standard

All drawings must read like an architect's presentation:

- **Line-weight hierarchy:** building outline 0.5–0.7 mm black; walls 0.35 mm; doors/windows 0.25 mm; furniture 0.18 mm; dimensions 0.18 mm; text 0.15–0.2 mm. (SVG/PDF attributes or equivalent.)
- **Line types:** existing = dashed; proposed = solid; demolition = dashed with X; centerlines = dash-dot; hidden = dashed thin.
- **Figure-ground diagram:** solid black building footprint vs. white open space for massing/context plans — include one per scheme.
- **Hatching/fill:** material hatches only where meaningful (wet areas, structure); avoid decorative fills.
- **Labels:** room names in English (local-language subtitle if applicable), areas in m², level markers, north arrow, scale bar, title block with project name + date + `CONCEPTUAL` status where applicable.
- **Color:** restrained — black/white linework, one accent max; color only for zones/climate arrows/graphics overlays.

### Phase 14 — Visualization types

Produce the subset the user needs, or all four by default:

1. **2D floor plan** — dimensioned, furnished or unfurnished per request.
2. **Furnished plan** — furniture layout proving usability.
3. **Axonometric / isometric** — massing + roof suggestion + key openings, generated from the plan geometry.
4. **Site plan** — lot boundary, setbacks, building footprint, access, landscaping zones, north arrow, neighboring context if known.

### Phase 15 — 12-step technical documentation package

Deliver a structured document package. Full spec in `references/documentation.md`. The 12 steps:

1. Cover sheet (project, client, date, status, drawn-by note: "AI-assisted conceptual design — verify with licensed architect")
2. Site analysis summary
3. Design brief / program
4. Room schedule (tabular)
5. Zoning diagram
6. Adjacency matrix + diagram
7. Floor plans (all levels)
8. Sections/elevations (min. 1–2)
9. Climate-response notes
10. Accessibility notes
11. Evaluation matrix + recommendation
12. Export manifest + assumptions/limitations log

### Phase 16 — Export formats

Default export set: **PNG** (raster, ≥200 dpi equivalent), **SVG** (editable vector), **PDF** (print-ready, layers preserved), **DXF** (CAD exchange), **IFC** (BIM, LOD 200 conceptual massing), **JSON** (structured room/geometry data), **CSV** (room schedule).

- **CAD layer naming:** `A-WALL-EXTR` (exterior), `A-WALL-INTR`, `A-DOOR`, `A-GLAZ`, `A-DIMS`, `A-FURN`, `A-TEXT`, `A-HATCH`, `S-COLS` (structure), `M-ANNO-NOTE`. Follow this convention consistently.
- IFC exports are conceptual massing only — no fabricated structural data.

### Phase 17 — Natural-language iteration

Support iterative refinement in plain language:

- "Make the master bedroom bigger" → adjust schedule, re-run affected adjacency/zoning, regenerate plan + re-score.
- "Swap kitchen and laundry" → check wet-wall adjacency, update matrix, redraw.
- "Add a second floor" → trigger Phase 8 + new schedule section.
- "More tropical" → strengthen Phase 9 measures, re-annotate.
- Track every change in the assumptions/limitations log. Never silently change the schedule.

### Phase 18 — QC checklist (run before every delivery)

Full checklist in `references/evaluation.md` §QC. Minimum gates:

- [ ] Every room has a door or documented open connection
- [ ] All dimensions internally consistent; areas sum correctly
- [ ] Room schedule = plan = documentation (single source of truth)
- [ ] Adjacency requirements from matrix satisfied or explicitly traded off
- [ ] Circulation paths complete entry→all rooms, no dead ends
- [ ] Wet rooms grouped; stairs comply with riser/tread limits
- [ ] Cross-ventulation verified or flagged
- [ ] Conceptual/unverified geometry labeled
- [ ] Accessibility notes present with honest verification status
- [ ] Title block, north arrow, scale bar on every sheet
- [ ] No fabricated regulations or code claims

### Phase 19 — Regulatory honesty

- For Indonesian projects: PBG (Government Regulation on Building Planning), SLF (Building Feasibility Certificate), and SNI standards may apply — **cite only what you can verify**; otherwise write "subject to verification under applicable PBG/SNI requirements".
- Never state a plan "complies with code" unless verified against the actual regulation text.
- Always include: "This is a conceptual design study, not a building permit document. Engage a licensed architect for approval drawings."

### Phase 20 — Final output protocol

Deliver in this order:

1. **Assumptions block** — site facts, constraints, TBDs
2. **Room schedule** — complete table
3. **Zoning summary** — zones + rationale
4. **Three schemes** — each with plan description + key dimensions
5. **Evaluation matrix** — scores + recommendation
6. **Visualizations** — 2D plans, furnished plans, axonometrics, site plan
7. **Climate + accessibility notes**
8. **Documentation package** — per Phase 15
9. **Exports** — files per Phase 16
10. **Limitations log** — everything unverified, conceptual, or TBD

## Anti-slop rules (absolute)

- NEVER invent dimensions, areas, or code requirements.
- NEVER produce a plan where rooms are unreachable or doors open into walls.
- NEVER use decorative geometry that serves no spatial function.
- ALWAYS label unverified geometry `CONCEPTUAL`.
- ALWAYS preserve the room schedule as single source of truth.
- ALWAYS disclose when a code/regulatory check was not performed.
