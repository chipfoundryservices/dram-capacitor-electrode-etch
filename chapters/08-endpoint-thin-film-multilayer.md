# Chapter 8: Endpoint Detection for Thin-Film & Multilayer Electrode Etch

## Overview

Endpoint detection in electrode etch is easy in one sense and treacherous in another. It is easy because the open areas are large: the whole wafer at storage-node separation, 45% of it at the plate etch. When a film clears, the emission spectrum changes by tens of percent, not by the fraction of a percent that a contact etch must detect. It is treacherous because what the endpoint detects is not what the module is judged by. The endpoint sees the moment when most of the wafer has cleared. The specification is set by the one site in a billion that has not.

This chapter describes how optical emission spectroscopy (OES) detects field clearing in module 1 and each of the four film transitions in module 2, how interferometry and reflectometry follow thin metal films, how RF and pressure signals complement them, and the failure modes that turn an endpoint into a residue.

**Learning Objectives:**
- Choose OES lines and actinometric ratios for TiN, W, SiGe, and high-k clearing
- Predict the shape and size of the field-clearing signal from the loading model
- Explain why the endpoint cannot detect residue, and what it can detect
- Design a four-endpoint plate recipe, including the Al-marker method for ZAZ
- Recognize and correct endpoint failure modes

---

## 8.1 What the Endpoint Must Do

```
Module 1 (SNS):
  Event               field TiN clears from the SiN top support
  Open area before    100% TiN
  Open area after     21% TiN (pillar tops), 79% SiN
  Action              stop ME, start timed OE (10 s)
  Required precision  ± 1 s (1 s of ME ≈ 1.2 nm of recess after clearing)

Module 2 (plate):
  Event 1   BARC clears          → stop BARC open, start W
  Event 2   W clears             → stop W after 25% OE, start SiGe ME
  Event 3   SiGe clears to TiN   → stop ME, start timed SiGe OE
  Event 4   ZAZ clears to SiN    → start timed HK OE (50% of clearing time)
  Open area                      45% throughout
```

---

## 8.2 Optical Emission Basics

### 8.2.1 Emission and Actinometry

The intensity of an emission line from species X is proportional to the density of X, the electron density, and an excitation rate coefficient that depends on the electron temperature:

```
I_X ∝ n_X · n_e · k_exc,X(T_e)
```

Changes in n_e or T_e move every line. Dividing by a line of an inert gas with a similar excitation threshold, usually Ar 750.4 nm, removes most of that common variation:

```
n_X ∝ (I_X / I_Ar) · n_Ar      (actinometry)
```

### 8.2.2 Lines Used

```
Species     Line or band (nm)        Behaviour at the event it marks
──────────────────────────────────────────────────────────────────────────
N₂          337.1 (C→B)              falls when TiN clears (N product);
                                     rises when SiN starts etching
Ti I        399.9, 453.3, 498.2      falls when TiN clears
Cl I        837.6, 725.7             rises when a Cl-consuming film clears
CO          483.5, 519.8             falls when BARC clears
W I         400.9, 429.5             falls when W clears
F I         703.7                    rises modestly when W clears
SiF         ≈ 440 (band)             rises when SiGe is exposed in SF₆
Si I        288.2                    falls when SiGe clears
SiBr        ≈ 290–300 (band)         falls when SiGe clears in HBr
Ge I        265.1, 303.9             falls when SiGe clears (UV; window-
                                     sensitive)
BCl         272                      falls when BCl₃ consumption rises
Al I        394.4, 396.2             transient as the Al₂O₃ layer etches
Zr I        360.1, 339.2             weak; rarely usable alone
SiCl        287                      rises when SiN starts etching in BCl₃
Ar I        750.4, 811.5             actinometer
```

---

## 8.3 Field Clearing in Module 1

### 8.3.1 The Expected Signal

The loading model of Chapter 3 predicts the size of the change. When the field clears:

```
TiCl₄ production ∝ θ_A · ER:      1.00 → 0.21 × 1.76 = 0.37
N₂ production (from TiN):          same → 0.37
Cl density:                        1.00 → 1.76

Normalized signals:
  N₂(337)/Ar     falls to ≈ 0.4 of its main-etch plateau
  Ti(453)/Ar     falls to ≈ 0.4
  Cl(837)/Ar     rises to ≈ 1.7
  Ratio Cl/N₂    rises ≈ 4.7× — the reference endpoint trace
```

A 4.7× change is enormous by the standards of endpoint detection. Noise is not the problem.

### 8.3.2 The Shape of the Transition

Different sites clear at different times (Chapter 6: 21.6–24.2 s at 3σ). The OES signal is a wafer-area average, so it traces the cumulative distribution of clearing times:

```
Fraction of wafer cleared vs time (normal distribution of t_c):
  F(t) = ½ [1 + erf((t − 22.9)/(0.44 √2))]     (σ = 1.33/3 = 0.44 s)

Signal S(t) = S_before − (S_before − S_after) · F(t)

  t = 22.0 s:  F = 0.02      22.9 s:  F = 0.50      23.8 s:  F = 0.98
  t = 24.2 s:  F = 0.998
```

The signal turns at about 22 s, passes its inflection at 22.9 s, and reaches its plateau by about 24 s. The reference algorithm declares endpoint when the smoothed derivative of Cl/N₂ falls below 5% of its peak value after the inflection, at about 24.0–24.5 s.

### 8.3.3 What the Endpoint Cannot See

At the plateau, the signal is flat to within its noise, about 0.5% of the step. The endpoint is therefore blind to any remaining TiN that covers less than about 0.5% of the wafer:

```
Detection floor ≈ 0.005 × (S_before − S_after) → ≈ 0.5% of the wafer area
                 ≈ 3.5 cm² of TiN still present

Residue specification: zero conducting threads between 10¹⁰ pillar pairs
  (any residue covering 10⁻⁹ of the area is a yield problem)
```

Between what the endpoint can see (0.5% of the area) and what the specification forbids (any thread) lie seven orders of magnitude. **The endpoint tells the recipe when the field has cleared on average. It does not and cannot tell anyone that the field has cleared everywhere.** That is the overetch's job, and the metrology's job to confirm (Chapter 15).

### 8.3.4 The Late Edge

The outer 5 mm of the wafer is about 6% of the area. If it clears 1.2 s late because of edge-ring wear (Chapter 6), the signal at "plateau" is still 6% short of its true final value and slowly creeping. A derivative-based algorithm declares endpoint anyway. A useful diagnostic is the **post-endpoint slope**: the slope of Cl/N₂ during the first seconds of the overetch. On a healthy chamber it is near zero; a positive slope means part of the wafer is still clearing.

---

## 8.4 Interferometry and Reflectometry in Module 1

### 8.4.1 Thin Metal Films Are Partly Transparent

TiN 18 nm thick transmits a measurable fraction of visible light (its optical absorption length at 500 nm is roughly 20–30 nm). A broadband reflectometer looking at a spot on the wafer sees reflectance change continuously as the TiN thins, then a step as it clears and the SiN/oxide mold below contributes its interference fringes.

```
In-situ reflectometry (illustrative):
  Spot            ≈ 5 mm, on the array of a central die
  Wavelengths     250–800 nm
  Resolution      ≈ 0.3 nm of TiN thickness from model fit
  Uses            real-time rate; remaining thickness; predicts clearing
                  time 5–10 s ahead
```

### 8.4.2 Rate-Based Endpoint

A predicted clearing time from the reflectometer, combined with the OES transition, gives a two-sensor endpoint. If the two disagree by more than 1.5 s, the recipe holds the wafer for review rather than guessing. This catches cases where OES is distorted by wall emission or window clouding (Section 8.7).

---

## 8.5 Four Endpoints in Module 2

### 8.5.1 BARC

CO emission (483.5 nm) from the organic BARC falls when the BARC clears in the 45% open area. The resist is still producing CO, so the signal falls only to about 60% of its plateau; the transition is clear.

### 8.5.2 W

```
W clearing signals (SF₆/N₂/Cl₂):
  W I 400.9 nm / Ar        falls to near zero
  SiF band / Ar            rises as SiGe is exposed
  F I 703.7 nm / Ar        rises modestly (SiGe consumes slightly less F per
                           nm than W: W uses 6 F per atom at 6.3 × 10²² cm⁻³)
Reference: endpoint on W I fall + SiF rise; overetch 25% (3 s)
```

### 8.5.3 SiGe to TiN

```
SiGe clearing signals (HBr/Cl₂/O₂):
  Si I 288.2 / Ar, SiBr band   fall as the SiGe clears in the open area
  Ge I 265.1 / Ar              falls (UV line: sensitive to window clouding)
  Br I / Ar                    rises (less Br consumed)
Reference: endpoint on Si I fall; then timed OE in HBr/O₂ (25 s)
```

The SiGe clearing transition is the broadest of the four (± 2.3 s at 3σ, Chapter 6) because the SiGe is the thickest film. The endpoint is placed at the plateau, and the selective overetch removes the remainder.

### 8.5.4 TiN and ZAZ: The Al Marker

The HK step has the weakest native signals. ZrCl₄ does not emit strongly, and Zr lines are weak and overlap other lines. Two features help:

```
HK step trace (BCl₃/Cl₂, illustrative):
  0–6 s      Ti I lines high, falling as the 5 nm TiN clears
  6–32 s     first ZrO₂ layer; weak Zr signal; BCl and Cl steady
  32–36 s    Al I 396.2 nm transient as the 0.3 nm Al₂O₃ etches
  36–62 s    second ZrO₂ layer
  ≈ 58–66 s  SiN exposed: N₂ 337 and SiCl 287 rise
```

**The Al marker.** The Al₂O₃ insertion layer sits at the middle of the ZAZ. The time at which Al emission peaks is, to within a second, the time at which the etch reached the middle of the dielectric. Doubling it, with a correction for the slightly different thickness above and below, predicts when the ZAZ will clear on that wafer in that chamber:

```
t_Al ≈ 6 + 26 + 2 = 34 s  (TiN + first ZrO₂ + half the Al₂O₃)
Predicted ZAZ clear:  t_clear ≈ 6 + 2 × (t_Al − 6) = 62 s
Overetch:             0.5 × (t_clear − 6) ≈ 28 s → step ends ≈ 90 s
```

The Al marker turns a timed HK step into a wafer-specific one. It compensates for chamber drift in ZrO₂ rate, which matters because the HK overetch has the least margin in the book.

### 8.5.5 SiN Onset

The rise of N₂ and SiCl emission as SiN begins to etch confirms the clearing of the bulk ZAZ. It cannot confirm the clearing of the last grains (Section 8.3.3 applies with even more force: the grains occupy 10⁻⁶ of the area long after the signal is flat).

---

## 8.6 Full-Spectrum and Multivariate Endpoint

Modern endpoint systems record the whole spectrum (200–900 nm) every 50–100 ms and use principal-component analysis or trained models to find the transition. Advantages: robustness to the loss of any one line, automatic actinometry, and the ability to detect unusual spectra (a contaminated wall, a leak, a wrong gas). The disadvantage is opacity: a model that endpoints correctly for a year can fail on a new film supplier with no line-level explanation. The reference keeps one physically interpretable ratio (Cl/N₂ in module 1; the four line pairs in module 2) alongside any multivariate model.

---

## 8.7 Other Signals

### 8.7.1 RF Signals

When the field TiN clears, the wafer surface changes from a continuous metal sheet to SiN with isolated metal dots. The wafer's RF coupling to the plasma changes:

```
At field clearing (module 1, illustrative):
  Bias V_pp            +2 to +4% (at fixed bias power)
  Bias phase           shift of 1–2°
  Harmonics            change in second and third harmonic content
```

The RF signal is weaker than OES but is immune to window clouding. The same effect appears in module 2 when the W, SiGe, and TiN clear in the open area.

### 8.7.2 Pressure and Throttle

Clearing changes the product load (TiCl₄ in module 1). At fixed pressure, the throttle valve moves a few tenths of a percent. It is a confirmation signal, not a primary one.

---

## 8.8 Endpoint Failure Modes

```
Failure                          Signature                        Effect
──────────────────────────────────────────────────────────────────────────────────
Window clouding (TiClₓ, BₓClᵧ,   UV lines (Ge 265, SiCl 287)      Late or missed EP;
SiOₓ on the viewport)            fade first; S/N falls             fallback to max time
Wall emission (Ti, W from        Ti line does not fall fully at    Early "plateau";
sputtered wall deposits)         clearing                          incorrect EP
No breakthrough (BT skipped or   ME signal onset delayed 10–30 s   Timeout or late EP;
TiO₂ thicker)                                                      non-uniform clearing
Late edge (ring wear)            Positive post-EP slope           Edge residue
Wrong open area (new reticle,    Transition size and timing        Algorithm thresholds
test wafers)                     differ                            mis-set
Film change (thicker fill)       Later EP; same shape              Correct (EP adapts);
                                                                   recess unchanged
Al marker missing (ZAZ           No Al transient                   Fallback to timed HK
recipe change)                                                     step
```

The most dangerous failure is the one that produces a plausible endpoint at the wrong time. Every endpoint recipe therefore has **minimum and maximum times**: an endpoint earlier than the minimum is rejected and the step continues to the minimum; a step that reaches the maximum without an endpoint stops and holds the wafer.

---

## Summary and Key Takeaways

1. **Large open area, large signals.** Field clearing changes Cl/N₂ by about 4.7×.

2. **The trace is the clearing-time distribution.** It turns at the first sites, inflects at the mean, and plateaus at the last 3σ site.

3. **The endpoint is blind below about 0.5% of the area.** Residue that matters is seven orders of magnitude smaller. Overetch and metrology, not endpoint, protect against it.

4. **Two sensors are better than one.** Reflectometry predicts clearing; OES confirms it; disagreement holds the wafer.

5. **The Al₂O₃ layer is a built-in marker.** Its emission transient at mid-ZAZ predicts the clearing time of each wafer.

6. **Every endpoint needs limits.** Minimum and maximum times catch plausible but wrong endpoints.

---

## Study Questions

1. With a loading constant k = 1.5 and the pillar-top fraction of 21%, compute the expected change in N₂/Ar and Cl/Ar at field clearing. What is the change in the Cl/N₂ ratio?

2. The clearing-time spread is ± 2.0 s (3σ) instead of ± 1.33 s. Sketch the new signal transition. At what time is the endpoint declared, and what happens to the rim-recess range?

3. A viewport has lost 60% of its transmission below 300 nm and 10% above 400 nm. Which lines in the plate recipe are affected? Which endpoints would you move to other lines?

4. In the HK step, the Al marker appears at 38 s instead of 34 s on one chamber. What does it tell you about that chamber's ZrO₂ rate? What clearing time and overetch should the recipe use?

5. Explain why a perfect endpoint would still not guarantee zero TiN residue after storage-node separation.

6. Design minimum and maximum times for the SNS main etch, given a nominal clearing time of 22.9 s, ± 5% thickness variation, and ± 3% rate variation, and a 2 s uncertainty from the breakthrough.

---

**Next Chapter:** [Chapter 9: Chamber Walls, Seasoning, Metal Contamination & Defects](./09-chamber-walls-contamination-defects.md)

---

**Chapter 8 Development Status:** Complete  
**Version:** 1.0
