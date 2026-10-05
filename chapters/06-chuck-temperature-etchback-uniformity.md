# Chapter 6: Electrostatic Chucks, Temperature & Etch-Back Uniformity

## Overview

A blanket etch-back has no pattern to hide behind. Every site on the wafer is etching the same film, and the site that clears last decides when the overetch can stop; the site that clears first decides how deep the pillars recess. Across-wafer uniformity is therefore not a quality metric in storage-node separation but a direct input to the two numbers the module is judged on: residue and recess. In the plate etch, uniformity sets the overetch of each of four films and the SiN loss at the end.

This chapter covers the hardware that sets uniformity at the wafer: the electrostatic chuck and its temperature zones, the temperature sensitivity of each step, the edge ring and the wafer edge, and the bow that the W strap introduces. It closes with the arithmetic that connects rate and thickness uniformity to the overetch and the recess range.

**Learning Objectives:**
- Compute the clearing-time spread from film-thickness and etch-rate non-uniformity
- Translate the clearing-time spread into a rim-recess range and an overetch requirement
- Explain which steps are temperature-sensitive and how chuck zones are used to tune them
- Describe how edge-ring erosion changes ion energy and angle at the wafer edge
- Estimate wafer bow from the W strap with Stoney's equation and its effect on chucking

---

## 6.1 Why Uniformity Is the Overetch

### 6.1.1 Clearing-Time Spread

The local clearing time is the local film thickness divided by the local rate:

```
t_c(r) = t_TiN(r) / R(r)

Relative spread (3σ), independent contributions:
  σ_t/t  (field TiN thickness)      5%
  σ_R/R  (main-etch rate)           3%
  σ_tc/tc = √(5² + 3²) = 5.8%

Reference: nominal ME clearing 16 nm / 0.70 nm/s = 22.9 s (after BT)
  3σ spread: ± 1.33 s → fastest site 21.6 s, slowest 24.2 s
  Endpoint declared at ≈ 24.5 s (signal reaches plateau; Chapter 8)
```

### 6.1.2 Rim Recess Range

A site begins recessing when its own field clears. The rim recess at the end of the overetch is

```
recess(r) = (t_EP − t_c(r)) · R_ME,loaded + t_OE · R_OE,loaded

  R_ME,loaded ≈ 1.0 nm/s during the transition (the wafer-average exposed
                area is falling, so the loaded rate rises from 0.7 to 1.23)
  R_OE,loaded = 0.40 × 1.76 = 0.70 nm/s

Fastest-clearing site:  (24.5 − 21.6) × 1.0 + 10 × 0.70 = 2.9 + 7.0 = 9.9 nm
Slowest-clearing site:  (24.5 − 24.2) × 1.0 + 10 × 0.70 = 0.3 + 7.0 = 7.3 nm
Range across the wafer: ≈ 2.6 nm (3σ), mean ≈ 8.6 nm
```

Thickness and rate uniformity contribute almost the entire recess range. Improving rate uniformity from ± 3% to ± 1.5% narrows the range only to 2.4 nm, because the thickness term dominates. Improving the **fill** uniformity from ± 5% to ± 3% narrows it to 1.9 nm. The etch-back inherits its range from deposition, and the best remedy is often feed-forward (Chapter 15) or a radial rate profile that matches the deposition profile.

### 6.1.3 Matching the Deposition Profile

CVD TiN is typically thicker at the centre or at the edge in a stable radial pattern. If the etch rate has the same radial shape, the clearing time is flat:

```
Example: TiN 18.6 nm at centre, 17.4 nm at edge (± 3.3% radial)
  Rate tuned to 0.72 nm/s at centre, 0.68 nm/s at edge
  t_c,centre = 16.6/0.72 = 23.1 s;  t_c,edge = 15.4/0.68 = 22.6 s
  Residual radial spread 0.5 s (vs 1.6 s with a flat rate)
```

Coil current ratio, gas split, and chuck temperature zones are the knobs. The deposition profile drifts with the CVD chamber's own maintenance, so the match must be checked regularly; a matched profile that has drifted is worse than a flat one.

---

## 6.2 The Electrostatic Chuck

### 6.2.1 Construction

```
Reference ESC (illustrative):
  Type                 Johnsen–Rahbek ceramic (AlN-based), bipolar
  Clamp voltage        ± 1.5 kV
  Backside He          10 Torr inner zone, 20 Torr outer zone
  Heater zones         4 radial zones (production) or > 100 zones (advanced)
  Coolant              −10 to +20 °C base; heaters raise the surface to
                       40–80 °C
  Temperature range    40–110 °C (standard); up to 250 °C (heated-chuck
                       variant, Chapter 7)
  Uniformity           ± 0.5 °C across the wafer with plasma on
```

### 6.2.2 Heat Load

```
Heat flux to the wafer (SNS ME):
  Ion power     I_i × E_i = 2.3 A × 70 V ≈ 160 W
  Recombination, radiation, electrons    ≈ 100–200 W
  Total         ≈ 300 W over 707 cm² ≈ 0.4 W/cm²
HK step:
  Ion power     3.4 A × 150 V ≈ 510 W; total ≈ 800 W ≈ 1.1 W/cm²
```

With 10–20 Torr of He, the chuck removes these fluxes with a wafer-to-chuck temperature rise of a few degrees. The HK step is the hottest; its wafer temperature rises about 5–8 °C above the chuck setpoint during the step.

---

## 6.3 Temperature Sensitivity of Each Step

### 6.3.1 Ion-Assisted and Spontaneous Components

Each rate has an ion-assisted part, nearly independent of temperature, and a spontaneous or volatility-limited part that follows an Arrhenius law:

```
R(T) = R_ion + R_sp,0 · exp(−E_a / kT)

Temperature coefficients near 60 °C (illustrative):
  Step / film               dR/dT (%/°C)    Dominant mechanism
  ─────────────────────────────────────────────────────────────────
  SNS ME, TiN vertical      +0.2            ion-assisted
  SNS ME, TiN lateral       +2.5            spontaneous Cl (E_a ≈ 0.25 eV)
  SiGe ME, vertical         +0.3            ion-assisted
  SiGe lateral (Ge)         +3.0            spontaneous Cl (E_a ≈ 0.3 eV)
  W, vertical               +0.5            F etch partly spontaneous
  HK, ZrO₂                  +0.8            ZrCl₄ desorption
  Sidewall passivation      −1 to −2        SiOₓBrᵧ, WNₓ deposition falls
```

### 6.3.2 Consequences

- The **vertical** rates of the main steps barely move with temperature: a 5 °C zone difference changes the TiN rate by about 1%. Temperature is a weak knob for vertical uniformity.
- The **lateral** rates move strongly: 5 °C raises the TiN lateral etch by about 13% and the SiGe lateral etch by 16%. The radial profile of the pillar-top cup and the plate-edge notch follow the chuck temperature profile.
- The **HK** rate moves enough (0.8%/°C) that edge zones are used to speed the edge ZrO₂ clearing (Section 6.4).

The reference holds the SNS chuck at 60 °C to keep the spontaneous lateral etch low and uniform, and the plate chuck at 60 °C as a compromise between SiGe lateral etch (wants cold) and ZrO₂ clearing (wants hot).

---

## 6.4 The Wafer Edge

### 6.4.1 Edge Ring and Sheath

The wafer sits inside an edge ring of Si or SiC whose top surface is nominally level with the wafer. When the two are level, the sheath above the wafer edge is flat and ions arrive normal to the surface. When the ring erodes, its surface drops below the wafer; the sheath bends down at the edge, ions arrive tilted outward, and the ion flux and energy at the outer 5 mm change:

```
Edge-ring erosion (illustrative):
  Erosion rate          ≈ 0.1 mm per 100 RF hours (Cl/BCl₃ chemistry)
  After 300 RF h        ring 0.3 mm low
  Effect at r = 145 mm  ion tilt ≈ 1–2° outward; edge rate −3 to −5%
                        (module 1); edge ZrO₂ rate −8% (module 2)
```

### 6.4.2 What Edge Drift Does

In module 1, a lower edge rate means the edge clears last. The endpoint is a wafer-average signal; if the outer 5 mm is 5% slower, it represents only about 6% of the wafer area, and the endpoint arrives before the edge has cleared. The overetch must then clear the edge at the loaded overetch rate. The reference 10 s overetch clears up to 7 nm of TiN at 0.70 nm/s, enough for an edge 1.2 s late, but not for a gross edge delay. A drifting ring shows up first as edge-die node shorts.

In module 2, a slower edge HK rate eats the 50% overetch margin of Chapter 4. A ring at 300 RF h leaves the edge with only about 40% effective overetch and raises the residue tail there.

### 6.4.3 Remedies

```
Remedies for edge drift:
  Ring height compensation    lift the ring as it erodes (motorized rings)
  Edge temperature zone       +3 to +5 °C on the outer zone to restore HK rate
  Edge gas injection          extra Cl₂ or BCl₃ at the edge
  Ring replacement interval   set by edge residue monitors, not by RF hours alone
```

---

## 6.5 Wafer Bow

### 6.5.1 Stoney's Equation

The W strap carries about 1 GPa of tensile stress. With the other films (mold, supports, SiGe), the wafer bows:

```
Curvature from one film:  κ = 6 σ_f t_f / (M_s t_s²)

W strap:  σ_f t_f = 1.0×10⁹ Pa × 40×10⁻⁹ m = 40 N/m
Si(100):  M_s ≈ 180 GPa;  t_s = 775 µm
κ = 6 × 40 / (180×10⁹ × (775×10⁻⁶)²) = 240 / 1.08×10⁵ = 2.2 × 10⁻³ m⁻¹

Bow (sagitta) over 150 mm radius:  b = κ r² / 2 = 2.2×10⁻³ × 0.0225 / 2 = 25 µm
```

The W alone bows the wafer about 25 µm. With the capacitor mold and other films, the incoming bow at the plate etch can reach 60–80 µm.

### 6.5.2 Effect on the Chuck

A bowed wafer clamps with uneven backside contact. The He gap is larger where the wafer is lifted, the thermal contact worse, and the temperature higher by a few degrees at the edge (for a bowl) or the centre (for a dome). Above about 100 µm, the chuck may fail to clamp the edge at all, with He leakage alarms. Since the plate etch's lateral etch and HK rate depend on temperature, bow becomes a radial profile change. Stress control at the W deposition is the remedy; chuck clamp-voltage increases are a mitigation.

---

## 6.6 The Chuck and the Capacitor

During the plate etch, the wafer substrate is clamped at a potential set by the plasma and the chuck. The plate is connected to the substrate through the capacitors of every cell in series with the storage-node junctions. Any fast change in substrate potential, at plasma ignition, at extinction, or at dechuck, drives a displacement current through the capacitor dielectric:

```
Displacement current through the cell capacitors:
  I = C_total · dV/dt
  C_total for one plate island ≈ (cells per island) × C_s
    = 5.4 × 10⁸ × 8.6 fF ≈ 4.6 µF
  dV/dt of 10 V in 1 ms → I ≈ 46 mA through the island's capacitors,
  but the voltage across each dielectric stays near zero if the plate
  follows the substrate through the large capacitance
```

The large capacitance protects the dielectric: the plate follows the substrate. What does stress it is a sustained difference between the plasma potential seen by the plate (through its exposed edge) and the substrate potential. Chapter 13 develops this; for the chuck, the practical rule is that ignition, extinction, and dechuck sequences should not apply voltage steps to a wafer whose plate is exposed at its edge to the plasma.

---

## 6.7 Uniformity of the Plate Steps

```
Plate step clearing spread (3σ, illustrative):
  W       thickness ± 3%, rate ± 3%     → ± 4.2% → ± 0.5 s on 12 s
  SiGe    thickness ± 4%, rate ± 3%     → ± 5.0% → ± 2.3 s on 47 s
  ZAZ     thickness ± 4%, rate ± 3%     → ± 5.0% → ± 3.1 s on 62 s
  (wafer edge outside 145 mm excluded; it is tuned separately)

Overetch needed to clear the slowest site, then add margin for tails:
  W      25%   (endpoint sharp; tail = W islands at grain boundaries)
  SiGe   OE step 25 s at 60 nm/min = 25 nm of SiGe capacity
         (vs ± 7.5 nm thickness spread at 3σ)
  ZAZ    50%   (Chapter 4: grain-level tail dominates)
```

The SiGe step has the largest absolute clearing spread, about 7.5 nm of film at 3σ. Because its overetch stops on TiN with selectivity 40, that spread costs little. The ZAZ step has a small absolute spread but no selective stop, so its overetch is set by the residue tail and paid for in SiN, resist, and edge exposure.

---

## Summary and Key Takeaways

1. **Clearing spread is √(thickness² + rate²).** At ± 5% and ± 3%, the SNS clearing time spreads ± 1.3 s around 22.9 s.

2. **The fill sets the recess range.** Rim recess ranges about 2.6 nm across the wafer, mostly from TiN thickness; matching the etch profile to the fill profile is the strongest knob.

3. **Temperature tunes lateral, not vertical.** Lateral TiN and SiGe rates rise 2.5–3%/°C; vertical rates only 0.2–0.5%/°C.

4. **The edge drifts with the ring.** At 300 RF h, a 0.3 mm low ring cuts edge rates 3–8%; edge-die shorts and residue are the first signal.

5. **Bow from the W strap is about 25 µm.** Total bow up to 80 µm changes chuck contact and the radial temperature.

6. **The capacitors follow the chuck.** The island's 4.6 µF ties the plate to the substrate; sustained potential differences, not transients, stress the dielectric.

---

## Study Questions

1. The field TiN uniformity improves to ± 3% (3σ) and the rate uniformity is ± 2%. Recompute the clearing-time spread and the rim-recess range with the reference endpoint logic.

2. The CVD TiN is 4% thicker at the edge than the centre. What radial rate profile flattens the clearing time? Which chamber knobs would you use?

3. The outer chuck zone is raised 5 °C to speed the edge HK rate. Using Section 6.3.1, estimate the change in ZrO₂ rate and in SiGe lateral etch at the edge. Is there a side effect on the plate-edge profile?

4. After 400 RF h the edge-ring top is 0.4 mm low and the edge TiN rate is 6% slower. The outer 5 mm is about 6.5% of the wafer area. Does the endpoint detect the late edge? How much TiN remains at the edge when the 10 s overetch starts, and does the overetch clear it?

5. Compute the bow from a 50 nm W strap at 1.2 GPa. What other films in the capacitor module contribute to bow, and which way?

6. A plate island holds 5.4 × 10⁸ cells. If the substrate potential steps by 5 V in 10 µs at dechuck and the plate is connected through 10 kΩ of plasma sheath resistance at its edge, estimate the time constant with which the plate follows. Does the dielectric see the step?

---

**Next Chapter:** [Chapter 7: High-Temperature & Halide Chambers for High-k Removal](./07-high-k-halide-chambers.md)

---

**Chapter 6 Development Status:** Complete  
**Version:** 1.0
