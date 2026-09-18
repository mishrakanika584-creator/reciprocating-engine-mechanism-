# Single-Cylinder Reciprocating Engine Mechanism (SolidWorks)

Slider-crank mechanism modeled in SolidWorks, showcasing part modeling, GD&T application, mechanism assembly/mates, kinematic motion simulation, and detail drafting.

![Motion Study GIF](renders/motion_study.gif)
*(1–2 crank revolutions at constant RPM — piston reciprocation driven by crank rotation)*

---

## Overview

Brief 3–5 sentence project description: what this is (a mechanism-only single-cylinder piston-crankshaft assembly, not a full running engine), why you built it (portfolio piece to demonstrate CAD modeling, GD&T, and mechanism/motion simulation skills), and the scope (no combustion, no valvetrain — pure kinematic slider-crank).

**Baseline specs:**
- Bore: 40 mm
- Stroke: 45 mm
- Connecting rod length: 90 mm (L/R ratio ≈ 4.0)

## Design Intent

Explain your key design choices in a few sentences:
- Why this bore/stroke/rod-length combination (L/R ratio and what it does to piston side-thrust and rod angularity).
- Why an I-beam rod cross-section (weight vs. stiffness — the classic real-world reason).
- Why a partial-disc counterweight (approximate balance of reciprocating/rotating mass).
- Any deliberate simplifications (e.g., no valvetrain, minimal cylinder block instead of a full crankcase) and why they were reasonable for this project's goals.

## Key Engineering Decisions

- **Fits and clearances**: table or bullet list of the interface fits (piston/bore, pin/bore, crank pin/big end, main journal/bearing) — see the fits table in `/docs/build-plan.md`.
- **Material selections**: piston (aluminum alloy), rod (steel or aluminum — state which and why), crankshaft (steel), liner (cast iron or aluminum) — and the reasoning (weight, strength, wear, thermal expansion).
- **Modeling strategy**: e.g., "crankshaft throw driven off a single controlling dimension in a construction sketch so stroke can be revised in one place," "connecting rod shank built as a swept/lofted I-beam for a realistic taper."
- **Driver joint**: a rotary motor on the crankshaft main journal drives the whole chain; piston and rod motion are pure kinematic results of the mates, not separately driven.

## GD&T Application

Summarize the datum structure and FCFs you applied — this is the section reviewers with a design background will read closely. Suggested content:

| Part | Feature | Control | Datum Reference |
|---|---|---|---|
| Piston | Skirt OD | Cylindricity | — |
| Piston | Pin bore | Concentricity | Datum A (skirt axis) |
| Connecting Rod | Small/big end bores | Concentricity | Datum A (big end axis) |
| Connecting Rod | Cap bolt holes | Position | Datum A, B |
| Crankshaft | Main journals | Concentricity/Runout | Common datum axis |
| Crankshaft | Crank pin axis | Position | Datum A (main journal axis) |
| Cylinder Liner | Bore | Cylindricity | — |
| Cylinder Liner | Bore axis | Perpendicularity | Datum A (mounting face) |

Include a screenshot or crop of each detail drawing's title block/FCF area if you want this section to be visually skimmable.

## Bill of Materials

| # | Part | Qty | Material | Key Dimension |
|---|---|---|---|---|
| 1 | Piston | 1 | Al 4032 / A356 | Ø39.9 mm OD |
| 2 | Piston Rings | 2 | Cast iron / steel | Ø40.6 mm OD (free) |
| 3 | Gudgeon Pin | 1 | Case-hardened steel | Ø10 mm × 32 mm |
| 4 | Connecting Rod | 1 | Steel / Al 7075 | 90 mm C-C |
| 5 | Rod Cap | 1 | Matches rod | Ø32 mm big end OD |
| 6 | Rod Cap Bolts | 2 | Steel (Toolbox SHCS) | M4 × 18–20 mm |
| 7 | Crankshaft | 1 | Steel (4140) | 22.5 mm throw |
| 8 | Cylinder Liner | 1 | Cast iron / Al | Ø40 mm bore |

*(Full BOM with weights and finish notes: `/docs/bom.xlsx` or embedded in the assembly drawing.)*

## Motion Study

- **File**: `renders/motion_study.gif` (embedded at the top of this README)
- **Setup**: constant-speed rotary motor on the crankshaft main journal, [X] RPM, Basic Motion study, [N] second duration ([N] full crank revolutions)
- Consider also embedding a short note on what to look for in the GIF: piston TDC/BDC dwell, rod angularity through mid-stroke, counterweight rotation.

## Bonus: FEA on the Connecting Rod

- Load case, boundary conditions, max stress location, and factor of safety summary (see `/docs/fea-report.pdf`).
- State clearly that loads are illustrative (mechanism demo), not derived from a real cylinder pressure trace.

## Folder Structure

```
reciprocating-engine-mechanism/
├── README.md
├── CAD/
│   ├── piston.SLDPRT
│   ├── connecting_rod.SLDPRT
│   ├── rod_cap.SLDPRT
│   ├── crankshaft.SLDPRT
│   ├── cylinder_liner.SLDPRT
│   ├── piston_ring.SLDPRT
│   ├── gudgeon_pin.SLDPRT
│   └── engine_assembly.SLDASM
├── STEP/
│   ├── piston.step
│   ├── connecting_rod.step
│   ├── crankshaft.step
│   ├── cylinder_liner.step
│   └── engine_assembly.step
├── drawings/
│   ├── piston_drawing.pdf
│   ├── connecting_rod_drawing.pdf
│   ├── crankshaft_drawing.pdf
│   ├── cylinder_liner_drawing.pdf
│   └── assembly_drawing.pdf
├── renders/
│   ├── motion_study.gif
│   ├── isometric_render.png
│   └── exploded_view.png
└── docs/
    ├── build-plan.md
    ├── bom.xlsx
    └── fea-report.pdf
```

---

*Modeled in SolidWorks 2024 SP2. GD&T per ASME Y14.5.*
