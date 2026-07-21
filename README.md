# Megaruptor

An open-source, low-cost DIY DNA shearing device built on the [Poseidon syringe pump](https://github.com/machineagency/poseidon) platform — designed as an accessible alternative to commercial mechanical shearing instruments (e.g., Diagenode Megaruptor 3) for genomic library preparation workflows, particularly long-read sequencing (Oxford Nanopore).

> **Status:** 🚧 In progress — components sourced, 3D printing and assembly underway.

---

## Overview

Mechanical DNA shearing instruments are a common bottleneck in labs working with long-read sequencing platforms, both in cost and accessibility. This project adapts the open-source Poseidon syringe pump design to build a functional, hackable shearing device using off-the-shelf electronics, 3D-printed parts, and standard insulin syringes as the shearing element.

The goal is a device that is:
- **Low-cost** — built from widely available components
- **Reproducible** — fully documented, open hardware
- **Hackable** — easy to modify shear force/speed parameters for different fragment size targets

---

## How It Works

DNA is sheared by repeatedly forcing a sample through a narrow-gauge needle at controlled speed, using a syringe pump mechanism driven by a stepper motor. Shear force and fragment size distribution are governed by needle gauge, plunger speed, and number of passes.

---

## Bill of Materials (Key Components)

| Component | Spec / Notes |
|---|---|
| Shearing element | BD Ultra-Fine 0.3 mL, 31G insulin syringes |
| Stepper motor | NEMA 17 |
| Motor driver | A4988 |
| Controller | CNC Shield V3 + Arduino Uno R3 |
| Safety | Mechanical limit switch (NC, fail-safe primary) + current sensing (secondary) |
| Frame/structural parts | 3D-printed (PLA), based on Poseidon design |

Full BOM with vendor links: [`docs/BOM.md`](docs/BOM.md) *(coming soon)*

---

## 3D Printed Parts

This build uses 4 standard components from the original Poseidon design, plus 2 custom parts designed for this build:

| Part | Type | Notes |
|---|---|---|
| Poseidon base/frame components (×4) | Standard | From original Poseidon design |
| Sleeve adapter | Custom | OD 8 mm, ID 6.1 mm, 30 mm length |
| Eppendorf bracket | Custom | 45° angle mount |

All STL files are available in [`/STL`](./STL). Source CAD files (where available) are in [`/CAD`](./CAD).

---

## Repository Structure

```
megaruptor/
├── README.md
├── STL/                  # Printable 3D files
├── CAD/                  # Source CAD files (Fusion 360 / FreeCAD)
├── firmware/             # Arduino control code
├── docs/
│   ├── BOM.md            # Full bill of materials with vendors/costs
│   ├── DECISIONS.md      # Design decisions & rationale
│   ├── ASSEMBLY.md       # Build/assembly instructions
│   └── images/           # Build photos
```

---

## Design Decisions

Key engineering choices and their rationale are documented in [`docs/DECISIONS.md`](docs/DECISIONS.md), including:
- Hybrid safety design (mechanical limit switch + current sensing) over software-only stall detection
- Choice of insulin syringe gauge for shearing element
- Custom part tolerances (e.g., sleeve adapter fit)

---

## Build Progress

- [x] Source components (NEMA 17, A4988, Arduino Uno R3, syringes)
- [x] Design custom parts (sleeve adapter, Eppendorf bracket)
- [ ] 3D print all components
- [ ] Full mechanical assembly
- [ ] Firmware integration and motor control testing
- [ ] Validation with real DNA samples (fragment size distribution vs. commercial shearing)

---

## Acknowledgments

This project builds on the open-source [Poseidon](https://github.com/machineagency/poseidon) syringe pump platform. Full credit to the original design team for the foundational mechanical design this project adapts.

---

## License

*(To be determined — consider MIT for firmware/code and CC-BY or CC-BY-SA for hardware designs)*

---

## Author

**Regina Ruiz** — Bioinformatics / Lab Sciences, Granatum Bioworks
[GitHub](https://github.com/reginaruizb) · *(add site/LinkedIn link here)*
