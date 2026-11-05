> English | [中文](clash-report-template.zh-CN.md)

# Clash detection report template

> Usage: copy one per detection round, rename it to `clash-report_YYYYMMDD_round-N.md`, and fill it in with the actual results. The report states only what is "understandable and actionable".

## Report header

| Item | Content |
| --- | --- |
| Project | (building name, e.g. "Community Service Center (self-built exercise)") |
| Detection round | Round N |
| Detection date | YYYY-MM-DD |
| Model version | Architecture: `YYYYMMDD`; HVAC/plumbing/electrical: `YYYYMMDD` |
| Exported file | `YYYYMMDD_round-N.nwc` (Navisworks is not installed on this machine, so NWC export is unavailable) |
| Detection tool | Navisworks Manage (not installed, Clash Detective unavailable) |
| Detection scope | HVAC×architecture, plumbing×architecture, electrical×architecture, HVAC×plumbing, HVAC×electrical, plumbing×electrical |
| Tolerance | Hard clash 0 mm; headroom per the requirement of each space |
| Inspector | (alias / code name) |

## Summary

| Discipline pair | Total clashes | Grade A | Grade B | Grade C | Resolved | Outstanding |
| --- | --- | --- | --- | --- | --- | --- |
| HVAC × Architecture | | | | | | |
| Plumbing × Architecture | | | | | | |
| Electrical × Architecture | | | | | | |
| HVAC × Plumbing | | | | | | |
| HVAC × Electrical | | | | | | |
| Plumbing × Electrical | | | | | | |
| **Total** | | | | | | |

## Grading criteria

- **Grade A / must fix**: penetration of structural beams or columns, penetration of a fire-rated wall without a fire damper, headroom failing the code or the brief, maintenance access completely blocked.
- **Grade B / should fix**: resolvable by an offset or a shift, insufficient space for supports and hangers, insulation clash.
- **Grade C / acceptable**: surface contact, soft clash (clearance within the permitted tolerance), duplicates confirmed as requiring no action.

> Grading is not guesswork: every Grade A item must state "which clause it violates" (a code clause or the number of a project-specific rule).

## Details

| No. | Clash ID | Grade | Level | Grid location | Discipline A | Element A (family:type / ID) | Discipline B | Element B (family:type / ID) | Clash type | Headroom/clearance | Recommended action | Responsible discipline | Status |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | C-001 | A | 2F | 3–4 / B–C | HVAC | Supply duct:Rectangular 800×400 / 123456 | Structure | Beam:KL-3 / 234567 | Hard clash | — | Drop the duct 150 to clear the beam soffit | HVAC | To be resolved |
| 2 | C-002 | B | 1F | Corridor 5–6 / A–B | Plumbing | Sprinkler main:DN100 / 345678 | HVAC | Supply duct:500×300 / 456789 | Hard clash | — | Offset the sprinkler branch around the duct | Plumbing | To be resolved |

Field notes:

- **Clash ID**: numbered by discipline pair plus a sequence number, e.g. `C-001` (HVAC×architecture), `M-001` (MEP against MEP), so that the same location can be tracked across rounds.
- **Element ID**: the Element ID visible in Navisworks, which must be locatable in Revit with "Select by ID".
- **Status**: To be resolved / Resolved / Re-check passed / Accepted (Grade C) / Void (duplicate).

## Typical issues and handling (example section)

### 1. Duct through beam (Grade A)

- Observation: the 2F corridor supply duct 800×400 has −120 mm clearance to the soffit of beam KL-3.
- Cause: the beam depth is 700 per the structural scheme, while the duct elevation follows the typical floor.
- Action: drop the duct 150 mm overall and adjust the terminal branches accordingly; check that corridor headroom ≥ 2.4 m.
- Re-check: the clash with the same ID is gone in round 2, headroom 2.42 m.

### 2. Cable tray crossing a water pipe (Grade B)

- Observation: the 1F electrical cable tray 300×100 crosses the water supply pipe DN80 at the same elevation.
- Action: raise the tray by 100 (tight to the beam soffit), keep the water pipe; the tray fill ratio is unchanged.

## Re-check log

| Round | Date | New | Closed | Outstanding | Notes |
| --- | --- | --- | --- | --- | --- |
| 1 | | — | — | | First round |
| 2 | | | | | Re-check whether the Grade A items from round 1 are cleared |

## Screenshot requirements

- One screenshot per Grade A clash: a 3D view (both elements visible) plus a plan or section (grids and levels visible).
- Hide project information, organization name and file path before taking screenshots; use consistent viewpoints and colours.
- Re-check comparison images: two shots from the same viewpoint, before and after, annotated with the round number.
