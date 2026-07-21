# Design Decisions

This document records key engineering decisions made during the build, along with the rationale behind them. Intended both as a build log and as reference for anyone adapting this design.

---

## Shearing Element: BD Ultra-Fine 0.3 mL, 31G Insulin Syringes

**Decision:** Use standard BD Ultra-Fine insulin syringes (0.3 mL, 31G needle) as the DNA shearing element, rather than a specialized/custom needle.

**Rationale:** Widely available, inexpensive, sterile, and consistent in gauge — removing a major source of part-to-part variability. The narrow 31G bore provides the shear force needed to fragment DNA as it's forced through under controlled plunger speed.

**Status:** Confirmed, in use.

---

## Safety System: Hybrid (Mechanical Limit Switch + Current Sensing)

**Decision:** Use a **normally-closed (NC) mechanical limit switch** as the primary fail-safe, with **current sensing** as a secondary/backup layer, rather than relying on software-only stall detection.

**Rationale:**
- A software-only approach (e.g., detecting stepper stall purely from expected vs. actual position) is not fail-safe: if the controller hangs, crashes, or the logic has a bug, there's nothing physically stopping the motor.
- An NC limit switch fails safe by design — if the switch, its wiring, or its connector fails, the circuit opens and the motor stops, rather than failing silently in the "everything is fine" state.
- Current sensing adds a second, independent detection method (motor drawing excess current under mechanical resistance/jam), catching failure modes the limit switch alone wouldn't (e.g., an obstruction before the switch is reached).

**Status:** Design finalized. Implementation pending full assembly.

---

## Custom Part: Sleeve Adapter

**Decision:** Design a custom sleeve adapter (OD 8 mm, ID 6.1 mm, 30 mm length) rather than using a stock Poseidon part.

**Rationale:** The stock Poseidon design didn't have a part matching the interface needed between the syringe holder and the linear rod system in this build's configuration. Dimensions were chosen to match the 8 mm linear rod OD while providing a snug fit for the mating component.

**Status:** Designed. Pending print + fit validation.

**Open item:** Tolerances (0.85 / 0.90 mm clearance, TBD which surfaces) still need double-checking against the actual assembled hardware — flagged in [BOM.md](BOM.md#open-items).

---

## Custom Part: Eppendorf Bracket (45°)

**Decision:** Design a custom bracket to hold an Eppendorf tube at a 45° angle, rather than a vertical/horizontal mount.

**Rationale:** *(add specific reasoning here — e.g., angle relative to shearing mechanism, ergonomics of loading/unloading, or clearance constraints)*

**Manufacturing note:** This part has a diagonal internal channel at 45° and **requires print supports**. Without supports, the interior tunnel deforms during printing, which would compromise fit and function. Documented in [BOM.md](BOM.md#3d-printed-parts).

**Status:** Geometry finalized ("Angulos del eppendorf — DONE" per build notes). Pending print with correct support settings.

---

## Print Settings: PLA, 0.2 mm Layer Height, 3 Perimeters

**Decision:** Standardize all structural 3D-printed parts on PLA, 0.2 mm layer height, 3 perimeters/walls, 50 mm/s print speed.

**Rationale:** *(add specific reasoning here — e.g., balance of print time vs. structural strength needed for the pump body and moving parts under repeated mechanical load)*

**Status:** Confirmed standard for this build.

---

## Base Platform: Poseidon Syringe Pump

**Decision:** Build on the open-source Poseidon design rather than designing a shearing mechanism from scratch.

**Rationale:** Poseidon is an already-validated, open-source syringe pump platform, letting this project focus engineering effort on the DNA-shearing-specific adaptations (custom parts, safety system, shearing element choice) rather than re-solving general syringe pump mechanics.

**Status:** Confirmed. 4 standard Poseidon parts used as-is (`pump_body`, `pump_sled`, `syringe_holder`, `motor_mount`), 2 custom parts added (sleeve adapter, Eppendorf bracket).

---

## Template for Future Entries

```
## [Decision Title]

**Decision:** What was decided.

**Rationale:** Why — what alternatives were considered and why this won.

**Status:** Confirmed / In progress / Superseded by [link].
```
