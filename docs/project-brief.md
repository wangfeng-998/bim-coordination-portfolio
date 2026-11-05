> English | [中文](project-brief.zh-CN.md)

# Project brief

> Status: draft. Dimensions, storey heights and discipline scope are completed once the building is selected.

## 1. Why this building

Selection criteria (in priority order):

1. **Manageable size**: 2–3 storeys, floor area 3000–5000 m², buildable by one person in 2–3 months, so it does not stall unfinished.
2. **All disciplines present**: it must have centralized plant rooms (AHU room, pump room, electrical distribution room) and ceiling voids — that is where MEP coordination clashes mostly occur.
3. **Headroom requirements**: corridors, lobbies and an underground car park, of the kind that produce genuine "insufficient headroom" cases.
4. **Public material**: self-built with reference to publicly available architectural design material and standard dimensions, touching no real project drawings.

Candidate directions: community service center / small library / community hospital outpatient building. Up to three storeys with one centralized plant room suits best.

## 2. Modeling scope and depth

### Architecture (LOD300)

| Component | Requirement |
| --- | --- |
| Walls | Architectural walls, interior and exterior distinguished, layered materials (blockwork + insulation + finish) |
| Floors | Structural slab thickness taken from the scheme; openings (stairs, pipe shafts, duct shafts) must be cut |
| Doors and windows | Families modeled from the door and window schedule, dimensions matching the schedule numbers |
| Stairs | Built to the storey height and riser/tread requirements, clear height of the flight ≥ 2.2 m |
| Rooms | All rooms placed and named, area scheme enabled |
| Grids / levels | Grids in both directions, levels up to roof |

### MEP (each discipline modeled separately, then linked and combined)

| Discipline | Systems | Key parameters |
| --- | --- | --- |
| HVAC | Supply air, return air, exhaust air, chilled/hot water pipes | Duct sizes, insulation thickness, elevations |
| Plumbing and drainage | Water supply, drainage, hydrants, sprinklers | Pipe diameters, slopes, insulation |
| Electrical | Cable trays, busways, distribution boards | Tray width and height, fill ratio |

MEP modeling only needs to reach the depth of "good enough to run clashes": pipe routes, elevations and diameters correct, valves and fittings may be simplified.

## 3. Coordination rules (project-specific)

1. Duct top at least 100 mm below beam soffit; where a water pipe crosses a cable tray, the tray is above.
2. Corridor headroom ≥ 2.4 m, plant room headroom ≥ 2.6 m, car park ≥ 2.2 m.
3. Sprinkler mains avoid the ducts, branches may be offset; headroom must still be satisfied after the offset.
4. Pipes penetrating fire-rated walls or floor slabs must have sleeves and be annotated with fire stopping.

## 4. Files and versions

- Revit models are split by discipline: `Architecture.rvt`, `HVAC.rvt`, `Plumbing.rvt`, `Electrical.rvt`, linked together into `Coordination-Central.rvt`.
- Before every clash run, export an NWC snapshot named `YYYYMMDD_round.nwc` and record the round number in the report so that results can be reproduced. **The NWC exporter is installed with Navisworks; Navisworks is not installed on this machine, so NWC export and clash detection are unavailable.**
- Model files are not committed; the repository holds screenshots, reports and notes only.

## 5. Schedule

| Phase | Time | Output |
| --- | --- | --- |
| Selection + floor plan scheme | 2026.12–2027.01 | Floor plans, storey height table |
| Architectural modeling | 2027.02–2027.04 | Architecture LOD300 |
| MEP modeling | 2027.04–2027.06 | Models for the three disciplines |
| First clash round | 2027.06–2027.07 | Report v1 |
| Remediation and re-check | 2027.07–2027.08 | Report v2 + comparison |
| Retrospective written | 2027.08–2027.09 | Retrospective, portfolio page |
