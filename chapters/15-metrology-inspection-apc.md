# Chapter 15: Metrology, Inspection & Advanced Process Control

## Overview

The electrode etches are judged by absences: no TiN between pillars, no ZrO₂ under contacts, no damage to a dielectric nobody can see. Absences are hard to measure. A metrology tool can measure how deep the pillar rims are recessed or how much SiN was lost; it cannot easily prove that none of 5 × 10¹⁰ pillar pairs on a die is bridged. The metrology of this module therefore has two layers: fast in-line measurements of the shapes the etch leaves (recess, cup, SiN, plate edge), which feed process control; and slow electrical measurements of the absences (shorts, opens, leakage), which arrive weeks later and decide whether the in-line numbers meant what they were assumed to mean.

This chapter lists what is measured, by which method and how often; shows why in-line inspection cannot reach the short-rate specification and what does; and builds the feed-forward and feedback loops that hold the recess and the high-k overetch on target.

**Learning Objectives:**
- Map each specification line to a measurement method and a sampling plan
- Explain voltage-contrast inspection of storage-node shorts and its statistical limits
- Choose methods for rim recess, cup depth, plate-edge profile, SiN loss, and high-k residue
- Design an EWMA feedback loop for the overetch and a feed-forward loop for fill thickness
- List the fault-detection signals that guard each module between measurements

---

## 15.1 Measurement Map

```
Specification line              Method (in-line)              Method (electrical, later)
──────────────────────────────────────────────────────────────────────────────────────────
Module 1
  Field TiN residue             VC on monitor arrays; XPS/    node-comb leakage; bit-map
                                TXRF Ti on periphery pads     pair failures
  Rim recess                    OCD on array pads; AFM        —
  Cup depth, seam               TEM (calibration); OCD        —
  Top SiN thickness             ellipsometry / OCD            —
  Cl on TiN                     XPS (monitor)                 leakage tail (indirect)
  Particles                     optical / e-beam inspection   cluster fails in bit maps
Module 2
  Plate CD, placement           CD-SEM; overlay               —
  Plate-edge profile            OCD on plate-edge gratings;   ILD void (later x-section)
                                x-section (calibration)
  W, SiGe, TiN residue          optical / e-beam inspection   contact-to-contact shorts
  High-k residue                TXRF / XPS on periphery pads  periphery contact chains
                                                              (opens)
  SiN loss                      ellipsometry on pads          —
  Dielectric damage             —                             antenna arrays; cell leakage
                                                              distribution
  Plate R_s                     4-point / van der Pauw        plate-bounce margin tests
```

---

## 15.2 Detecting Storage-Node Shorts

### 15.2.1 Voltage Contrast

A scanning electron beam charges the surface it scans. Conductors connected to the substrate discharge and look bright (in positive-mode contrast); isolated conductors charge and look dark. In the product array, every storage node lands on a drain junction, so every node looks alike, and a short between two nodes does not change their contrast. Voltage contrast detects shorts only in **monitor arrays** designed for it:

```
VC monitor array (reference):
  Pillars on alternate rows land on grounded pads (n⁺ to the p-well, forward
  biased by the beam's charging) → bright
  Pillars on the other rows land on isolated pads (on oxide) → dark
  A dark-row pillar shorted to a bright neighbour → bright: a defect
```

### 15.2.2 Statistical Reach

```
E-beam VC throughput (illustrative):
  Pixel 15 nm (3 pixels per 45 nm pitch), 100 MHz pixel rate
  Raw area rate = (15 nm)² × 10⁸ s⁻¹ = 2.25 × 10⁴ µm²/s ≈ 81 mm²/h
  With stage moves and overhead (≈ 25% efficiency)   ≈ 20 mm²/h
  Monitor arrays 1 mm² per die site × 20 sites = 20 mm² → ≈ 1 h per wafer
  Pillars inspected = 2 × 10⁷ µm² × 577 µm⁻² = 1.2 × 10¹⁰; pairs ≈ 3.5 × 10¹⁰

Short-rate specification: 3.9 × 10⁻¹⁰ per pair (Chapter 10)
Expected detections at the specification: 3.5 × 10¹⁰ × 3.9 × 10⁻¹⁰ ≈ 14
```

At this sampling, VC on one wafer per lot can see the specification rate, but only just, and only on monitor arrays that may not share every product defect mechanism (for example, saddles at hole-top CDs specific to the product array). VC is a **trend and excursion** tool: a jump from 14 to 100 detections in a wafer is unmistakable; a drift from 14 to 20 is not.

### 15.2.3 Electrical Combs

```
Node-comb test structure (reference):
  Two interdigitated sets of storage nodes, each set tied to its own pad
  through landing pads and contacts formed in the normal flow
  Pairs per comb          10⁷
  Combs per wafer         100 (in scribe lines)
  Pairs per wafer         10⁹
  Test                    leakage between the sets at 1.0 V after metal 1;
                          any short > 1 pA flags the comb
  Reach                   per-wafer short rate down to ≈ 10⁻⁹; per-lot ≈ 10⁻¹⁰
```

Combs arrive weeks after the etch but measure the real thing: shorts that conduct. Bit-map analysis at wafer sort is the final measurement: shorted pairs appear as adjacent-cell pair failures with a characteristic data-pattern dependence (they fail when the two cells hold opposite data).

---

## 15.3 Recess, Cup, and Top SiN

```
Method                 Measures                         Notes
──────────────────────────────────────────────────────────────────────────────
OCD (scatterometry)    rim recess, cup depth (modelled),  every wafer, 13 sites;
on array test pads     SiN thickness                      model calibrated by TEM;
                                                          precision ≈ 0.3 nm (rim)
AFM                    rim recess relative to SiN top     tip cannot reach the cup
                       (direct)                           bottom (32 nm, 10 nm
                                                          deep cone); weekly
TEM / STEM             rim, cup, seam groove, rim radius  calibration, qualification;
                                                          slow
HV-SEM top-down        pillar-top shape, seam openings    defect review
Ellipsometry           SiN thickness in periphery         every wafer
```

The OCD model has more parameters than the measurement can fully separate: rim recess and cup depth correlate. The reference fixes the cup shape from the fill dimple (it does not vary with the etch, Chapter 10) and floats the rim recess and the SiN thickness. A change in the fill thickness must be passed to the OCD model, or the model will report a cup change as a recess change.

---

## 15.4 Plate Etch Metrology

### 15.4.1 Profile and CD

Plate-edge gratings in the scribe (1 µm lines and spaces of the full plate stack) are measured by OCD for sidewall angle, foot, and TiN notch (as a modelled undercut). CD-SEM measures plate CD and placement on product features.

### 15.4.2 High-k Residue

```
Method       Sensitivity (Zr)          Area          Use
──────────────────────────────────────────────────────────────────────────
TXRF         ≈ 10¹⁰–10¹¹ atoms/cm²    ≈ 1 cm² spot  average residue on a
                                                    large periphery pad;
                                                    weekly monitor
XPS          ≈ 0.1 at% (≈ 10¹³ cm⁻²)  ≈ 50 µm       chemical state; Cl, B too
TOF-SIMS     ppm; mapping              ≈ 100 µm      islands in maps; slow
E-beam       islands ≳ 20 nm with      die-scale     grain clusters, veils;
inspection   material contrast                       review
Contact      functional                full contact  the decisive test;
chains                                 module        weeks later
```

The specification of 1 × 10¹³ Zr cm⁻² is an average; TXRF meets it easily even with a tail of residual grains (Chapter 4). The periphery contact chain is the only measurement that sees the tail. For that reason, the in-line control of the HK overetch relies on process signals (Al-marker time, edge-ring life) more than on residue metrology.

### 15.4.3 Dielectric Damage

Antenna arrays and reference capacitor arrays (Chapter 13) are measured after the first metal level: leakage distributions at ± 1.0 V, breakdown voltage on sacrificial structures, and the polarity pair. The comparison of interest is the shift between antenna and reference arrays, wafer by wafer, plotted against radius.

---

## 15.5 Feed-Forward Control

### 15.5.1 Fill Thickness to Overetch

The main etch is endpointed, so the clearing time adapts to the fill thickness automatically. What the endpoint cannot adapt is the **spread**: a wafer with a wider radial thickness profile clears over a longer interval, and its first-clearing sites recess more. Feed-forward uses the measured fill profile:

```
Feed-forward (reference):
  Input       TiN fill thickness at 9 radial sites (XRF Ti counts on array
              pads, calibrated to thickness)
  Model       clearing-time spread Δt_c ∝ thickness range / ME rate
  Actions     (1) chuck/coil zone offsets that tilt the ME rate radially to
                  match the fill profile (Chapter 6)
              (2) OE time reduced by (Δt_c,wafer − Δt_c,nominal) × 0.5 when the
                  spread is small, to hold the mean recess on target
```

### 15.5.2 Resist Thickness and Plate Stack

For module 2, the resist thickness, the SiGe thickness, and the W thickness are fed forward to set the maximum step times (the endpoint limits of Chapter 8) and to flag wafers whose resist budget would fall below 150 nm.

---

## 15.6 Feedback Control

### 15.6.1 EWMA on the Overetch

```
Rim-recess feedback (reference):
  Measurement  OCD rim recess, wafer mean, one wafer per lot
  Model        recess = a + b · t_OE,   b = R_OE,loaded ≈ 0.70 nm/s
  Update       a_{n+1} = λ (recess_n − b · t_OE,n) + (1 − λ) a_n,  λ = 0.4
  Recipe       t_OE,n+1 = (target − a_{n+1}) / b

Example: target 8.6 nm; a_n = 1.6 nm; lot n measured 9.6 nm at t_OE = 10 s
  a_{n+1} = 0.4 × (9.6 − 7.0) + 0.6 × 1.6 = 1.04 + 0.96 = 2.00 nm
  t_OE,n+1 = (8.6 − 2.00) / 0.70 = 9.4 s
```

Limits: the overetch may not fall below 7 s (the edge and saddle margins of Chapter 10) or rise above 14 s (the recess ceiling). A correction that hits a limit is a signal that something upstream has changed, typically loading (wall state) or the fill.

### 15.6.2 High-k Overetch

The Al marker gives a per-wafer clearing prediction within the chamber (Chapter 8), so the HK step is self-correcting for rate drift. The feedback loop acts on the overetch **fraction**, which is held at 50% unless the periphery SiN loss (ellipsometry) or the contact-chain yield (weeks later) says otherwise. Because the contact-chain feedback is slow, its role is to re-centre the overetch after a process change, not to correct lot-to-lot noise.

### 15.6.3 Edge Compensation

Edge-ring wear is tracked by RF hours and by the edge rim recess (OCD at r = 145 mm) in module 1 and by the edge SiN loss in module 2. The ring height or the outer chuck zone is adjusted in steps when the edge parameter drifts by more than a set amount (for example, edge rim recess 1.0 nm below the centre).

---

## 15.7 Fault Detection

Between measurements, the process is guarded by tool signals recorded on every wafer:

```
Fault-detection signals (reference):
  Signal                        Module   Indicates
  ──────────────────────────────────────────────────────────────────────
  ME endpoint time              1        fill thickness; BT; rate; loading
  Post-EP slope of Cl/N₂        1        late edge; incomplete clearing
  BT-to-ME onset delay          1        surface oxide (queue time)
  Al-marker time                2        ZrO₂ rate drift
  SiN-onset sharpness (N₂ rise) 2        HK uniformity
  WAC clear time (Ti, Zr)       1, 2     wall loading
  Bias V_pp at fixed power      1, 2     source density drift; ion energy
  Reflected power, arc counts   1, 2     match, bevel arcing
  He leak rate                  1, 2     bow, chuck condition
  Foreline pressure             2        chloride condensation
  Wall/liner temperatures       2        recombination, deposits
```

A multivariate model of these signals, trained on wafers with good electrical results, gives a per-wafer health score. A wafer outside the model's envelope is held for review before it proceeds to the support open (module 1) or the ILD (module 2).

---

## 15.8 Virtual Metrology

The endpoint time, the OE time, and the loading-sensitive OES ratio predict the rim recess of each wafer with an error of about 0.5 nm:

```
Virtual metrology for rim recess (illustrative):
  recess_VM = c₀ + c₁ · t_OE + c₂ · (t_EP − t_infl) + c₃ · (Cl/N₂)_OE
    t_infl   inflection time of the clearing transition (≈ mean t_c)
    (t_EP − t_infl) ≈ the time the average site spent etching after clearing
    (Cl/N₂)_OE measures the loading during the overetch
  Fitted on OCD wafers; used for every wafer not measured
```

Virtual metrology lets every wafer, not one per lot, feed the EWMA loop, and flags wafers whose predicted recess falls outside 5–15 nm.

---

## 15.9 Sampling Plan

```
Measurement                     Frequency
────────────────────────────────────────────────────────────────────
Module 1
  OCD rim recess, SiN            1 wafer/lot, 13 sites (all wafers by VM)
  VC monitor arrays              1 wafer/lot
  Particle inspection            1 wafer/lot + daily monitors
  XPS Cl / TXRF Ti               weekly monitor wafers
  TEM cup / seam / rim radius    monthly; after any fill or etch change
Module 2
  CD-SEM plate CD                1 wafer/lot, 9 sites
  OCD plate-edge profile         1 wafer/lot
  Ellipsometry SiN loss          1 wafer/lot, 13 sites
  TXRF Zr (periphery pad)        weekly monitor; every wafer after PM (first lot)
  Defect inspection after strip  1 wafer/lot
Electrical (all wafers, scribe)
  Node combs, contact chains,    after metal 1 / wafer sort
  antenna arrays, plate R_s
```

---

## Summary and Key Takeaways

1. **Shapes in-line, absences electrically.** OCD and ellipsometry measure recess and SiN; combs, chains, and antenna arrays measure shorts, opens, and damage weeks later.

2. **VC sees shorts only in monitor arrays.** At 1 wafer per lot it reaches the specification rate barely; it is an excursion tool.

3. **Combs give the real short rate.** 10⁹ pairs per wafer resolve ≈ 10⁻⁹ per wafer and ≈ 10⁻¹⁰ per lot.

4. **TXRF sees averages, chains see tails.** High-k control relies on the Al marker and edge-ring life, verified by contact chains.

5. **EWMA on the overetch holds the recess.** λ = 0.4, b = 0.70 nm/s, limits 7–14 s; a limit hit means an upstream change.

6. **Fault detection guards every wafer.** EP time, post-EP slope, Al-marker time, WAC clear time, and V_pp are the key signals.

---

## Study Questions

1. A VC monitor wafer shows 45 shorts in 3.5 × 10¹⁰ pairs. Is this significantly above the specification rate of 3.9 × 10⁻¹⁰? (Use Poisson statistics.)

2. How many node-comb pairs must be tested to detect, with 90% confidence, a short rate of 5 × 10⁻¹⁰ if at least one short must be found?

3. Run the EWMA loop of Section 15.6.1 for three lots measuring 9.6, 9.2, and 8.9 nm with the recipe updated after each. What overetch times result?

4. The fill thickness increases by 1 nm, but the OCD model is not updated. What will the model report, and how will the EWMA loop react? What is the true recess after a few lots?

5. TXRF reports Zr at 3 × 10¹² cm⁻² on every monitor, but the contact chains of one week's lots show a 5× increase in opens at the wafer edge. Which process signals would you examine first?

6. Design a fault-detection rule using the post-EP slope that would catch the late-edge case of Chapter 6, Study Question 4.

---

**Next Chapter:** [Chapter 16: Integration, Yield & Cost of Ownership](./16-integration-yield-coo.md)

---

**Chapter 15 Development Status:** Complete  
**Version:** 1.0
