# Chapter 13: Plasma-Induced Damage to the Capacitor Dielectric

## Overview

During the plate etch, the capacitor dielectric of every cell on the wafer is in the circuit. Above it lies the plate being etched; below it lie the storage nodes, wired through landing pads to the drains of the access transistors and, through their junctions, to the silicon substrate. The plasma touches the plate across the whole open area until the plate is cut, and touches the substrate, faintly, at the bevel and through the chuck. Wherever the plasma is not perfectly uniform, the plate and the substrate float at different potentials, and that difference appears across 5.5 nm of ZAZ.

This chapter builds the circuit, estimates the voltage and current the dielectric sees in each phase of the etch, explains why one polarity is far more dangerous than the other, and shows why ultraviolet light and halogens, which damage gate dielectrics in other modules, are confined here to the plate edge. It closes with test structures and mitigation.

**Learning Objectives:**
- Draw the charging circuit from the plasma through the plate, dielectric, storage node, and junction to the substrate
- Explain why a negative plate stresses the dielectric and a positive plate largely does not
- Estimate the antenna ratio and the steady-state dielectric voltage in the wafer-continuous phase
- Compute the injected charge and compare it with charge-to-breakdown
- Explain why UV and halogen damage are confined to the plate edge
- Design antenna test structures and choose mitigation for a damage excursion

---

## 13.1 The Circuit

```
Charging path during the plate etch:

  plasma (open area) ──► exposed plate conductor (W/SiGe/TiN in the open
                          area, until cleared)
                              │
                         plate island(s)
                              │  ZAZ: C = N × 8.6 fF; tunnelling leakage
                              ▼
                         storage nodes (TiN pillars)
                              │  landing pad, buried contact
                              ▼
                         n⁺ drain junction of each access transistor
                              │  diode to the p-well
                              ▼
                         p-well / substrate ──► reached by the plasma only at
                                                the bevel and capacitively
                                                through the chuck
```

The access transistors are off and their gates (the buried word lines) are not part of this path. The only dielectric in series is the capacitor dielectric, and the only other element is the drain junction of each cell.

### 13.1.1 Polarity

The junction makes the circuit asymmetric:

```
Plate positive relative to substrate:
  Storage node pulled positive → n⁺/p junction reverse-biased
  Junction leakage (fA per cell) is comparable to or lower than the
  dielectric's; the voltage divides, the junction taking much of it
  (it can hold 5–8 V before breakdown)
  → dielectric partly protected

Plate negative relative to substrate:
  Storage node pulled negative → junction forward-biased above ≈ 0.6 V
  Node clamped at ≈ −0.6 V; the rest of the voltage appears across
  the dielectric
  → dielectric fully stressed
```

The dangerous condition is a **negative plate**. It arises where the region of plasma seen by the exposed plate floats below the region seen by the substrate.

---

## 13.2 Phases of the Etch

```
Phase             Duration     Plate electrically           Antenna
──────────────────────────────────────────────────────────────────────────────
A: wafer-         BARC → TiN   one conductor across the     exposed plate in the
   continuous     clears in    whole wafer (W, SiGe, or     open area, 45% of the
                  the open     TiN still connects the       wafer (≈ 318 cm²)
                  area         islands)
                  (≈ 115 s)
B: separation     ≈ 1–2 s      islands detach as the last   the last TiN webs:
                  near HK      TiN in the open area clears  large for a few islands
                  t ≈ 6 s                                    for a fraction of a s
C: island         rest of HK   each island isolated; top    plate-edge sidewall
                  (≈ 85 s)     covered by resist            only (≈ 10⁻³ of the
                                                            island's dielectric)
```

---

## 13.3 Phase A: The Wafer-Continuous Plate

### 13.3.1 Antenna Ratio

```
Exposed conductor (open area):     A_ant = 0.45 × 707 cm² ≈ 318 cm²
Dielectric area per wafer:
  cells per wafer    ≈ 860 die × 1.72 × 10¹⁰ = 1.48 × 10¹³
  area per cell      1.24 × 10⁵ nm² = 1.24 × 10⁻⁹ cm²
  A_diel             1.48×10¹³ × 1.24×10⁻⁹ ≈ 1.8 × 10⁴ cm²
Antenna ratio:     A_ant / A_diel ≈ 0.017
```

This is the opposite of a gate-oxide antenna, where a small gate hangs on a large antenna (ratios of 10³–10⁵). Here an enormous dielectric hangs on a modest antenna. The dielectric current density is correspondingly small, but the dielectric is also unusually leaky (it is a capacitor dielectric, not a gate oxide), and its breakdown voltage is only about 2.5 V.

### 13.3.2 Steady-State Voltage

In phase A, the plate floats at the area-weighted floating potential of the plasma over the open area. The substrate floats at a potential set by the bevel and the chuck coupling. A non-uniform plasma gives them a difference ΔV₀ of order 1–2 V. The dielectric then carries whatever current the plasma imbalance can supply at that voltage:

```
Dielectric leakage (reference ZAZ after plate deposition):
  J(1.0 V) ≈ 1 fA per cell / 1.24×10⁻⁹ cm² ≈ 8 × 10⁻⁷ A/cm²
  J(V) ≈ J(1.0 V) · exp((V − 1.0)/0.12 V)       (≈ one decade per 0.28 V)

  V        J (A/cm²)        Total over 1.8×10⁴ cm²
  ────────────────────────────────────────────────
  1.0      8 × 10⁻⁷          0.015 A
  1.3      1.0 × 10⁻⁵        0.18 A
  1.5      5.2 × 10⁻⁵        0.95 A
  1.7      2.8 × 10⁻⁴        5 A

Available plasma imbalance current (illustrative):
  Ion current to the open area ≈ 3.2 mA/cm² × 318 cm² ≈ 1.0 A
  A floating conductor can draw at most a fraction of this as net current
  before its potential moves to cancel it: say 10–30% → 0.1–0.3 A
```

The dielectric leakage rises so steeply with voltage that it clamps the voltage: at about 1.3 V it already draws 0.2 A, comparable to the net current a floating plate can extract from the plasma. The dielectric therefore sees at most about **1.3–1.4 V** in phase A, even if the plasma non-uniformity would drive 2 V. The large dielectric area, which makes the capacitor useful, also protects it.

### 13.3.3 Injected Charge

```
Phase A stress (negative-plate regions only, illustrative):
  J ≈ 1 × 10⁻⁵ A/cm² for ≈ 100 s
  Q_inj ≈ 1 × 10⁻³ C/cm²

Charge to breakdown of ZAZ (illustrative):  Q_bd ≈ 0.5–5 C/cm²
  Q_inj / Q_bd ≈ 0.02–0.2%
```

Breakdown is not a risk at this charge. What is a risk is **stress-induced leakage**: a fraction of a percent of Q_bd generates enough traps to shift the leakage tail of the capacitor population. The specification of Chapter 1, cell leakage after plate etch within 10% of an unetched reference, is set to catch exactly this.

### 13.3.4 Where Phase A Is Worst

Phase A stress is largest where the plasma is least uniform relative to the substrate's reference, usually at the wafer edge or in a ring corresponding to the coil's density peak. A leakage-tail map after plate etch that shows a ring is a charging signature, not a material one.

---

## 13.4 Phase B: Separation

As the last conducting film (the top-electrode TiN) clears from the open area, the plate breaks into islands. The clearing is not simultaneous: for a second or so, some islands remain connected through webs of TiN to large remaining areas of open-area TiN, while their neighbours have already been isolated.

```
A late-separating island (illustrative):
  Island dielectric area     5.4 × 10⁸ cells × 1.24×10⁻⁹ cm² ≈ 0.67 cm²
  Connected TiN web area     up to a few cm² for a fraction of a second
  Antenna ratio              up to ≈ 5 (vs 0.017 in phase A)
```

An antenna ratio of 5 lets the local plasma imbalance drive the island to a higher voltage than in phase A, limited again by the steep leakage, but now with 300 times less dielectric to absorb the current. The voltage can approach 1.6–1.8 V, briefly. The stress is short (≪ 1 s) and its charge small, but it falls on a few islands, so it appears as a **bank-level** leakage signature rather than a wafer-level one.

Shortening phase B, by making the TiN clear uniformly and quickly, is the main control: the high TiN rate in the HK step (50 nm/min, 6 s to clear 5 nm) helps, and so does a uniform SiGe overetch that leaves the TiN equally exposed everywhere when the HK step starts.

---

## 13.5 Phase C: Isolated Islands

```
Island antenna in phase C:
  Exposed plate area      the plate-edge sidewall only:
                          perimeter ≈ 2 × (1.1 + 1.2) mm = 4.6 mm
                          × 200 nm height = 9 × 10⁻⁴ cm²
  Island dielectric       0.67 cm²
  Antenna ratio           ≈ 1.4 × 10⁻³
```

The resist covering the top of the island collects charge but is an insulator; it charges itself, not the plate. The sidewall collects little, because ions arrive at grazing incidence and electrons are partly shaded. Phase C is the longest phase of the HK step and the least damaging.

---

## 13.6 Ultraviolet Light

The plasma emits vacuum-ultraviolet (VUV) photons that can create electron–hole pairs and traps in dielectrics:

```
VUV sources (illustrative):
  Cl         134–139 nm
  Ar         104.8, 106.7 nm
  BCl, BCl₂  bands in the VUV/UV
```

Metals absorb VUV within a few nanometres. Over the array, the ZAZ is covered by 5 nm of TiN, 150 nm of SiGe, and 40 nm of W throughout the etch: no VUV reaches it. VUV reaches ZAZ only:

1. In the open area, where the ZAZ is being removed anyway.
2. At the plate edge, in the notch under the SiGe and within a few tens of nanometres of the edge.

Both are over the periphery, 1.5 µm from the last dummy row. VUV is therefore not a capacitor-damage mechanism in the plate etch, unlike in gate etch, where the gate dielectric extends beyond the gate edge into the source/drain region. It becomes one only if the plate edge is moved close to active cells, or if the plate stack has holes over the array (for example, a design with plate openings over the support-open pattern).

---

## 13.7 Halogens at the Edge

Chlorine and boron enter the exposed ZAZ edge during the HK step. They diffuse along the grain boundaries of the crystallized ZrO₂:

```
Halogen penetration into the ZAZ edge (illustrative):
  During the HK step (60 °C, 90 s)       ≈ 5–10 nm
  After ILD and anneals (400–450 °C)     ≈ 20–50 nm
Plate overlap beyond the last dummy row  1500 nm
```

The overlap is 30–75 times the penetration. Halogen damage at the edge is not a cell-leakage mechanism with the reference layout. It is a reason not to shrink the overlap below a few hundred nanometres.

---

## 13.8 What About Module 1?

During storage-node separation, the dielectric does not yet exist. The field TiN connects every storage node of the wafer, and through them every drain junction, to the plasma: it is an antenna with a junction behind it. Junctions tolerate this: the current flows through the forward- or reverse-biased diodes into the substrate with no thin dielectric in the path. The access transistors' gates are not connected to the storage nodes. Module 1 has no dielectric-damage mechanism of its own; its device concerns are shorts (Chapter 10) and the electrode surface (Chapter 11).

The inter-layer dielectric deposited over the plate after module 2 is a PECVD process and charges the plate again. Its charging falls under the same circuit and the same polarity rule, and it is controlled in that module.

---

## 13.9 Test Structures

```
Antenna test structures in the scribe (reference):
  Structure             Description                               Measures
  ────────────────────────────────────────────────────────────────────────────────
  Reference capacitor   10⁶-cell array with plate island, no       baseline leakage,
  array                 extra antenna                              breakdown
  Antenna arrays        same array with plate connected to         leakage shift vs
                        exposed-plate antenna pads of 10×, 100×,   antenna ratio
                        1000× the island's own open-area share
  Late-separation       island connected to a large pad through    phase-B stress
  structure             a narrow TiN-only bridge that clears last
  Edge-proximity        arrays with plate overlap of 0.3, 0.6,     UV and halogen
  arrays                1.0, 1.5 µm                                edge effects
  Polarity pairs        arrays over n⁺/p junctions and over        polarity
                        p⁺/n junctions                             asymmetry
```

The polarity pair is the most diagnostic: if leakage shifts appear only on the arrays whose node junctions forward-bias for a negative plate, the mechanism is charging.

---

## 13.10 Mitigation

```
Lever                                 Phase    Effect
────────────────────────────────────────────────────────────────────────────
Plasma uniformity (coil, gas split)   A        smaller ΔV₀
Source/bias pulsing                   A, B     lower T_e; electrons reach
                                               surfaces in the off-phase;
                                               ΔV₀ reduced 30–60%
Lower bias as each film clears        A, B     less ion-driven imbalance at the
                                               moments of changing antenna
Fast, uniform TiN clearing in HK      B        shorter separation phase
Bevel condition (no exposed Si        A        substrate reference less
near the plasma)                               sensitive to the edge plasma
ESC sequence (no voltage steps with   all      no forced plate–substrate
plasma on)                                     transients (Chapter 6)
Plate overlap ≥ 1 µm                  edge     UV and halogens stay outside
                                               the array
```

---

## Summary and Key Takeaways

1. **The circuit is plate → ZAZ → node → junction → substrate.** No gate oxide is involved.

2. **A negative plate is the danger.** The node junction forward-biases and the whole voltage falls across the dielectric.

3. **The antenna ratio is 0.017, not 10⁴.** A huge, leaky dielectric clamps its own voltage near 1.3–1.4 V in the wafer-continuous phase.

4. **Stress-induced leakage, not breakdown.** Injected charge is ≈ 10⁻³ C/cm², 0.02–0.2% of Q_bd, enough to shift the leakage tail.

5. **Separation is the sharpest moment.** For a fraction of a second, a late island can see an antenna ratio near 5; uniform, fast TiN clearing shortens it.

6. **The plate shields its own capacitors.** VUV and halogens reach only the plate edge, 1.5 µm from active cells.

---

## Study Questions

1. Using the leakage model of Section 13.3.2, at what voltage does the dielectric of one wafer draw 0.3 A? How does the clamped voltage change if the dielectric is improved so that J(1.0 V) is ten times lower?

2. Compute the antenna ratio in phase A if the plate covers 70% of the wafer instead of 55%. Does the clamped voltage rise or fall, and why?

3. A late-separating island of 0.67 cm² is connected for 0.3 s to 3 cm² of TiN web. Estimate the antenna ratio and, assuming the net current density from the plasma to the web is 0.5 mA/cm², the voltage at which the island's leakage balances it.

4. Explain why the polarity of the plate relative to the substrate matters, using the storage-node junction. Which test structure would confirm a charging mechanism?

5. A new design reduces the plate overlap to 0.3 µm. Using Sections 13.6 and 13.7, which mechanisms could now reach active cells, and what would you measure?

6. A leakage-tail map after plate etch shows a ring at 120 mm radius. Propose two hypotheses, one from charging and one from material variation, and the measurement that distinguishes them.

---

**Next Chapter:** [Chapter 14: Advanced Schemes — Cylinder Electrodes, ALE, New Metals, 4F² & 3D DRAM](./14-advanced-electrode-schemes.md)

---

**Chapter 13 Development Status:** Complete  
**Version:** 1.0
