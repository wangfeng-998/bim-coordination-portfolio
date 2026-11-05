> English | [中文](README.zh-CN.md)

# bim-coordination-portfolio

BIM MEP coordination portfolio: one **self-selected small public building**, documented end to end — from architectural LOD300 modeling through coordinated MEP services, Navisworks clash detection and the remediation loop.

> A personal portfolio project, meant to show the full "model → coordinate → report → re-check" workflow rather than a handful of renderings.
>
> The repository holds text, screenshots and anonymized reports only. **Revit models and Navisworks files are not committed** (they are large and version control gives nothing here); download links are attached separately when needed.

## What problem does this project solve

The daily work of an MEP coordination role: overlay the architectural, structural, HVAC, plumbing/drainage and electrical models, find **hard clashes** (pipes through beams, ducts through walls) and **insufficient headroom**, then drive the disciplines to revise their drawings. The difficulty is not in the software operation, it is in:

1. Clash counts run to the thousands at a time — how to grade them, deduplicate them and assign them;
2. How to prove a fix is correct afterwards (re-check), rather than "it looks about right to me";
3. Making the report understandable to the contractor — which floor, which grid, what headroom, and what change is recommended.

This project walks all three through on one small building and distills the method into templates.

## Project overview (planned)

| Item | Content |
| --- | --- |
| Building type | Self-selected small public building (a community service center / small library, or similar), 2–3 storeys, floor area 3000–5000 m² |
| Modeling depth | Architecture LOD300 (walls, floors, doors and windows, stairs, rooms and dimensions complete) |
| MEP scope | HVAC (ducts, water pipes), plumbing and drainage (water supply, drainage, fire protection), electrical (cable trays, busways) |
| Coordination tools | Revit 2020 (the version actually used on this project) + Navisworks Manage: **not installed**, so NWC export and clash detection are unavailable on this machine |
| Deliverables | Architectural model screenshots, coordinated MEP model screenshots, clash detection report, headroom analysis drawings, before/after remediation comparisons |

Model source: **built from scratch**, using no real project drawings. Publicly available architectural design material and standard dimensions are used for reference, avoiding copyright and confidentiality issues.

## Deliverable list

| # | Deliverable | Form | Status |
| --- | --- | --- | --- |
| 1 | Project brief (building overview, discipline breakdown, modeling standards) | `docs/project-brief.md` | 🟡 Draft |
| 2 | Architectural model LOD300 | Screenshots + model notes | ⬜ Not started |
| 3 | Coordinated MEP model | Screenshots + system notes | ⬜ Not started |
| 4 | Clash detection report (with grading and remediation recommendations) | Filled instance of `docs/clash-report-template.md` + PDF | 🟡 Template finalized |
| 5 | Headroom analysis | Colour-coded plans + statistics table | ⬜ Not started |
| 6 | Before/after remediation comparison | Screenshot pairs | ⬜ Not started |
| 7 | Retrospective: methodology and lessons learned | `docs/retrospective.md` | ⬜ Not started |

## Coordination workflow

```
Revit modeling (architecture LOD300 / MEP disciplines)
        │  Export NWC (Navisworks not installed, this step unavailable)
        ▼
Navisworks integration → clash run in Clash Detective
        │  Export XML/HTML results
        ▼
Grading and dedupe (hard clash / headroom / soft clash) → fill in the report
        │  Assign by discipline
        ▼
Revit revisions → re-export NWC → re-check the same clash set
        │
        ▼
Before/after comparison + retrospective
```

Grading criteria (written into the report so that not everything ends up Grade A):

- **Grade A / must fix**: services penetrating structural beams or columns, ducts penetrating a fire-rated wall without a fire damper, headroom below code or client requirement.
- **Grade B / should fix**: services crossing but resolvable by an offset, insufficient space for supports and hangers.
- **Grade C / acceptable**: insulation in contact with a cable tray surface, soft clash (clearance within the permitted tolerance).

## Directory structure

```
bim-coordination-portfolio/
├─ README.md                        # English (default entry)
├─ README.zh-CN.md                  # Chinese
├─ docs/
│  ├─ project-brief.md              # building overview, discipline scope, modeling standards (English)
│  ├─ project-brief.zh-CN.md        # same, Chinese
│  ├─ clash-report-template.md      # report structure and grading criteria (English)
│  ├─ clash-report-template.zh-CN.md # same, Chinese
│  └─ retrospective.md              # methodology and lessons learned (to be written)
└─ assets/                          # screenshots (anonymized)
```

## Progress board

- [x] Project positioning and deliverable list defined
- [x] Clash report template and grading criteria
- [ ] Building selected (floor plans and storey heights)
- [ ] Architectural LOD300 modeling complete
- [ ] Three MEP disciplines modeled
- [ ] First clash detection round + report
- [ ] Remediation + re-check + before/after comparison
- [ ] Retrospective written

## Ground rules

- No real project drawings, company title blocks or internal standards.
- Clear the project information (project name, organization, author, file path) before taking screenshots; model files are not committed.
- Element IDs and grid numbers in the report stay consistent with the model so that results can be reproduced; a screenshot that cannot be reproduced does not count as evidence.

## License

Documentation and screenshots are licensed under [CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/); please cite the source when quoting.
