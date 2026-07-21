# Bill of Materials

All prices in **MXN (Mexican pesos)**, sourced locally by the author. Links/vendors to be added as available.

## 3D Printed Parts

| Part | Description |
|---|---|
| `pump_body` | Main pump structure |
| `pump_sled` | Carriage that pushes the syringe plunger |
| `syringe_holder` | Holds the syringe barrel |
| `motor_mount` | NEMA 17 motor mount |

> Custom parts (sleeve adapter, Eppendorf bracket) are tracked separately — see [Design Decisions](DECISIONS.md).

### Print Settings

| Setting | Value |
|---|---|
| Material | PLA |
| Layer height | 0.2 mm |
| Perimeters / walls | 3 |
| Print speed | 50 mm/s (normal) |

**⚠️ Print note:** The Eppendorf bracket (in the `ExtraBases` file) has a diagonal 45° internal channel and **requires supports**. Without supports, the interior tunnel deforms during printing.

---

## Mechanical Components

| Component | Cost (MXN) |
|---|---|
| NEMA 17 motor (1.7 A, 200 steps) | 166.34 |
| T8 lead screw, 200 mm + bronze nut | 80.00 |
| Linear rods, 8 mm × 200 mm (×2) | 221.00 |
| LM8UU linear bearings | 80.00 |
| Coupler 5 mm–8 mm (motor to lead screw) | 190.00 |
| M3 screws (assorted) + nuts | 229.00 |
| Wing nuts / thumb screws | 664.00 |

## Electronics

| Component | Cost (MXN) |
|---|---|
| Arduino Uno | 131.24 |
| CNC Shield V3 | 159.00 |
| A4988 driver | *included with CNC Shield above* |
| 12V 2A power supply | 119.46 |
| Wiring / connectors | 115.00 |
| Switch | 167.00 |
| Auto shutoff system | — |
| Zip ties | 41.00 |

---

## Total (approx.)

**~$1,738 MXN**

> Note: this is the author's working estimate. Some line items above may reflect bulk purchases or partial units — a fully itemized cost breakdown will be added as the BOM is finalized.

---

## Open Items

- [ ] Double-check dimensions/tolerances: **0.85 and 0.90** (device calibration — see build notes)
- [x] Eppendorf angle bracket geometry — done
- [ ] Add vendor links per component
- [ ] Reconcile itemized costs with total
