# Appendix F: Metrology Reference

Methods used for the electrode etch modules: what each measures, its sensitivity and precision, its sampling cost, and its main pitfalls. Values are illustrative.

---

## F.1 In-Line Dimensional Metrology

```
Method          Measures                       Precision (3σ)   Time/site   Pitfalls
──────────────────────────────────────────────────────────────────────────────────────────
OCD             rim recess, cup (modelled),    0.3 nm (rim)      ≈ 2 s       rim/cup correlation;
(scatterometry) top SiN; plate sidewall,       0.5° (angle)                  model must follow
                foot, notch (on gratings)                                    fill changes
AFM             rim recess vs SiN top          0.3 nm            ≈ 3 min     tip cannot reach cup
                                                                             bottom; tip wear
Ellipsometry    SiN thickness in periphery;    0.2 nm            ≈ 1 s       residue films bias
                residual ZAZ (≥ 0.5 nm)                                      the fit
Reflectometry   TiN thickness (in-situ)        0.3 nm            real time   spot over array uses
                                                                             effective-medium
                                                                             model
CD-SEM          plate CD, placement            3 nm              ≈ 5 s       charging on SiN;
                                                                             resist shrink
TEM / STEM      rim, cup, seam groove, rim     0.2 nm            hours       sampling; FIB damage
                radius; plate-edge profile                                   at TiN/SiGe edges
XRF             TiN fill thickness (Ti         0.2 nm            ≈ 10 s      calibration to fill
                counts)                                                      density
```

---

## F.2 Composition and Residue

```
Method          Measures                       Sensitivity        Area        Notes
──────────────────────────────────────────────────────────────────────────────────────────
XPS             Cl, Br, F, B, O, Ti, Zr;       0.1–0.5 at%        ≈ 50 µm     chemical state;
                chemical state                 (≈ 10¹³ cm⁻²)                  top 5–8 nm
TXRF            Zr, Ti, W, Ge, Fe, Ni, Cu, Y   10⁹–10¹¹ cm⁻²      ≈ 1 cm²     averages; blind to
                                                                              isolated grains
VPD-ICPMS       metals (front/back)            10⁸–10⁹ cm⁻²       whole       destructive; the
                                                                  surface     reference for metals
TOF-SIMS        Cl, F, B depth profiles;       ppm                ≈ 100 µm    semi-quantitative;
                Zr maps                                                       slow
Ion             extractable Cl⁻, Br⁻, F⁻       ≈ 10¹¹ cm⁻²        whole       sacrificial wafer
chromatography                                                    wafer
```

---

## F.3 Defect Inspection

```
Method                 Detects                          Sensitivity        Throughput
──────────────────────────────────────────────────────────────────────────────────────
Optical darkfield      particles, flakes, veils         ≥ 30–45 nm         wafer/min
Optical brightfield    pattern defects, residue         ≥ 40 nm            wafer/10 min
                       islands on SiN
E-beam VC              node shorts (monitor arrays)     single pillar      ≈ 20 mm²/h
E-beam material        ZrO₂ islands, W/SiGe residue     ≳ 20 nm            die-scale;
contrast (review)                                                          sampling
HV-SEM review          pillar tops, seam openings       few nm             review only
```

---

## F.4 Electrical Test Structures

```
Structure                 Location   Measured after   Detects                   Reach
──────────────────────────────────────────────────────────────────────────────────────────
Node comb (10⁷ pairs)     scribe     metal 1          node-to-node shorts       ≈ 10⁻⁹ per wafer
                                                                                (100 combs)
VC monitor array          scribe /   SNS (in-line)    shorts (contrast)         ≈ 10⁻¹⁰ (1 wfr)
                          dummy
Capacitor array           scribe     metal 1          C_s, leakage at ± 1 V     distribution
(10⁶ cells)                                                                     tails
Antenna arrays            scribe     metal 1          charging (vs reference)   10% leakage
(10×–1000×)                                                                     shift
Polarity pairs            scribe     metal 1          charging polarity         5% asymmetry
Periphery contact chains  scribe     contact + M1     ZrO₂ residue opens        ≈ 10⁻⁹ per
(10⁶ contacts)                                                                  contact
Plate R_s (van der Pauw)  scribe     metal 1          plate sheet resistance    ± 2%
Plate-edge proximity      scribe     metal 1          edge damage vs overlap    —
arrays
```

---

## F.5 Statistical Reach

The number of opportunities a measurement inspects sets the smallest failure rate it can detect:

```
To detect a rate p with at least one failure at 90% confidence:
  N ≥ ln(10) / p ≈ 2.3 / p

  p = 3.9 × 10⁻¹⁰ (node-short spec) → N ≥ 5.9 × 10⁹ pairs
  p = 8 × 10⁻¹⁰ (contact open)      → N ≥ 2.9 × 10⁹ contacts

To distinguish a 2× increase in rate (Poisson, ≈ 2σ):
  expected count at baseline ≥ ≈ 10
```

One wafer of node combs (10⁹ pairs) cannot alone prove compliance with a 3.9 × 10⁻¹⁰ specification; a lot (25 wafers) can.

---

## F.6 Sampling Summary

```
Module 1: OCD every lot (VM every wafer); VC 1 wafer/lot; particles every lot;
          XPS/TXRF weekly; TEM monthly and after changes
Module 2: CD-SEM, OCD, ellipsometry every lot; TXRF weekly and after PM;
          post-strip defects every lot
Electrical: all wafers at metal 1 and sort (scribe structures and bit maps)
```

---

**Appendix F Version:** 1.0
