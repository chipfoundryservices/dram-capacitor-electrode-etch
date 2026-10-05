# Chapter 11: Electrode Surface Chemistry — Chlorine, Oxidation & Corrosion

## Overview

Every surface the electrode etches leave behind is a halogenated surface. The TiN pillar tops after storage-node separation carry several atomic percent of chlorine. The W, SiGe, and TiN at the plate edge carry fluorine, bromine, and chlorine. In vacuum these halogens are inert. In air they meet water, hydrolyse to acids, and attack the metal beneath. And some of the surfaces they sit on become, a few steps later, part of the capacitor.

This chapter follows the halogen from the etch to the device. It describes the chemistry of chlorine in TiN, the post-etch treatments that remove it, what Book #30's support open and dip-out do to the pillar tops in turn, how the pillar top and its rim become part of the capacitor, how the plate edge corrodes if left unprotected, and the queue-time rules that follow.

**Learning Objectives:**
- Describe the chemistry of chlorine in the TiN surface after etch-back and its reaction with air
- Choose a post-etch treatment and estimate the time needed to reduce Cl below a target
- Explain why storage-node separation affects only the pillar tops and seams, and why those still matter
- Compute the field enhancement at a sharp pillar rim and its effect on leakage
- Describe W and TiN corrosion at the plate edge and set queue-time limits

---

## 11.1 Chlorine in the TiN Surface

### 11.1.1 What the Etch Leaves

```
TiN pillar tops after the SNS overetch (illustrative, XPS):
  Cl in the top 2 nm             3–6 at% (as TiClₓ and Cl in the lattice)
  O                              5–10 at% (from the BT residue and the wall)
  B                              0.5–1 at% (BₓClᵧ)
  Seam region                    Cl up to 10 at% (fast-diffusion path;
                                 chlorine from the fill plus the etch)
```

### 11.1.2 Reaction With Air

When the wafer leaves vacuum, the surface meets humidity:

```
TiClₓ(surface) + H₂O → TiOₓ(OH)ᵧ + HCl
HCl + TiN → further TiClₓ, consumed by H₂O → TiOₓ growth
```

Chlorine catalyses oxidation. A chlorinated TiN surface left in clean-room air grows oxide faster than a clean one:

```
TiOₓ thickness on TiN after 24 h in air (illustrative):
  Clean TiN (no Cl)              ≈ 1.5 nm
  TiN with 5 at% Cl              ≈ 3.0 nm, uneven, with Cl-rich nodules
```

The oxide is not just thicker but patchier, and the nodules are hygroscopic. In the seam, where liquid water can condense by capillarity, the attack is concentrated.

---

## 11.2 Post-Etch Treatment

### 11.2.1 Options

```
Treatment (downstream plasma         Removes Cl as      Effect on TiN surface
unless noted)
─────────────────────────────────────────────────────────────────────────────
H₂/N₂ (forming gas) 150–250 °C       HCl                little oxide; mild
(reference)                                             nitridation
H₂O vapor plasma                     HCl                1–1.5 nm uniform TiOₓ
NH₃ plasma                           NH₄Cl (volatile    nitridation; NH₄Cl can
                                     above ≈ 340 °C)    condense if cool
O₂ plasma                            Cl₂, ClO           2–3 nm TiO₂: thick,
                                                        avoid
In-situ vacuum anneal                Cl desorption      slow below 300 °C
DIW rinse (wet, after air break)     Cl⁻ dissolved      oxide grows during the
                                                        rinse; queue critical
```

### 11.2.2 Kinetics

Hydrogen removes surface chlorine with roughly first-order kinetics:

```
[Cl](t) = [Cl]₀ · exp(−t/τ)

Reference H₂/N₂ downstream, 200 °C:   τ ≈ 10 s
  From 5 at% to 1 at%:   t = τ ln 5 = 16 s
  Reference time 30 s:   [Cl] ≈ 5 × e⁻³ = 0.25 at% (top surface);
                          XPS-averaged ≤ 1 at% (specification)
τ rises about 2× for every 40 °C lower (E_a ≈ 0.3 eV); at 150 °C, τ ≈ 20 s.
```

The seam is not reached by a surface treatment. The chlorine in it comes out slowly during later heating, which is one reason a deep seam groove is undesirable (Chapter 10).

### 11.2.3 Vacuum Transfer

The reference performs the post-etch treatment on the same mainframe as the etch-back, transferring the wafer under vacuum. The surface never meets air while it carries 3–6 at% Cl. A wafer that is exposed to air before treatment, for example after an aborted sequence, should be treated as a different product: its oxide is thicker and patchier, and the treatment removes less of its chlorine.

---

## 11.3 What Happens Next to the Pillar Tops

### 11.3.1 The Pillar Tops Are the Only Etched Surface

Storage-node separation touches only the top of each pillar: the cup and the rim, about 804 nm² per pillar (π × 16²), plus the seam. The outer surface of the pillar, which carries 99.4% of the capacitor area, is still buried in the mold and never sees the etch-back plasma. Its condition is decided by the TiN fill and by Book #30's dip-out.

```
Pillar-top area as a fraction of capacitor area:
  804 nm² / 1.24 × 10⁵ nm² = 0.65%
```

### 11.3.2 Through the Mold Etch

Between the two modules of this book, the pillar tops pass through Book #30:

```
Pillar-top surface history (reference):
  After SNS + PET         TiN, Cl ≤ 1 at%, TiOₓ ≈ 1 nm
  Support-open mask       ACL deposited over the tops (≈ 400 °C)
  Support-open etch       crescents of the tops exposed in the openings;
                          fluorocarbon plasma (TiFₓ, CFₓ)
  Mask strip (O₂)         TiOₓ grows on the exposed tops (2–3 nm)
  Dip-out (HF)            TiOₓ partly dissolved, TiOₓFᵧ formed; seam
                          exposed to HF if open
  Dielectric ALD          on whatever surface the dip-out left
```

The SNS surface chemistry is therefore largely overwritten by Book #30's steps on the exposed crescents, while the parts of the pillar tops still covered by top support after the support open keep the SNS surface until the dip-out. Two SNS legacies survive: the **shape** of the top (rim, cup, seam) and any **chlorine held in the seam**.

### 11.3.3 Why the Top Still Matters: the Rim Corner

The top face of each pillar is covered by dielectric and plate like the rest of the pillar: it is part of the capacitor. A recessed rim has an edge where the top face meets the pillar sidewall. If that edge is sharp, the field in the dielectric there is enhanced:

```
Field at a rounded edge of radius r, dielectric thickness t
(cylindrical approximation):
  E_edge = V / (r · ln(1 + t/r))
  E_flat = V / t

Reference t = 5.5 nm:
  r = 2 nm:  E_edge = V / (2 × ln 3.75) = V / 2.64 nm  → 2.1 × E_flat
  r = 5 nm:  E_edge = V / (5 × ln 2.10) = V / 3.71 nm  → 1.5 × E_flat
  r = 10 nm: E_edge = V / (10 × ln 1.55) = V / 4.38 nm → 1.25 × E_flat
```

Leakage through ZAZ rises steeply with field: at the operating point, roughly a decade for every 0.5–1 MV/cm. A rim with a 2 nm radius, at twice the flat-surface field, can leak as much as the whole flat surface of the pillar despite being a tiny fraction of the area. Rounding the rim to r ≥ 5 nm is therefore a device requirement on the etch-back:

```
Rim rounding (reference):
  The 50 eV overetch and the angle dependence of the yield (Chapter 10)
  facet the rim; the H₂/N₂ treatment and Book #30's HF further round it.
  Target r ≥ 5 nm (TEM), checked at module qualification.
```

### 11.3.4 The Cup Corner

The bottom of the cup is a concave corner, where the field in the dielectric is reduced rather than enhanced. The cup itself is harmless electrically. Its risk is chemical: if the seam below it is open, it is a pocket that holds residues and precursors.

---

## 11.4 The Electrode–Dielectric Interface

The dielectric is grown on the pillar surface. The interface it forms decides the leakage of the capacitor:

```
Interface factors and their effect (illustrative):
  Factor                           Effect
  ─────────────────────────────────────────────────────────────────────
  TiOₓ thickness 0.5–1 nm          helps tetragonal ZrO₂ nucleate; adds a
                                   low-band-offset layer (TiO₂ conduction
                                   band close to TiN Fermi level); leakage ↑
                                   if > 1.5 nm
  Cl at the interface > 2 at%      trap-assisted tunnelling; leakage tail ×3
  F at the interface (from HF)     passivates some traps; excess → voids
  C, B (from etch residues)        local defects; breakdown tail
```

For the pillar sidewalls these factors are Book #30's responsibility. For the pillar tops, which are 0.65% of the area but contain the rim corners, they are partly this book's. For the top electrode, the interface is formed by the TiN ALD on the dielectric and is not touched by any etch until the plate etch reaches the periphery (Section 11.5).

---

## 11.5 The Plate Edge After Etch

### 11.5.1 What the Etch Leaves

```
Plate-edge sidewall after the four-step etch (illustrative):
  W            F and Cl 1–3 at%; WOₓFᵧ skin 1–2 nm
  SiGe         SiOₓBrᵧ passivation 1–2 nm; Br 2–4 at%
  TiN          Cl 3–5 at% (from the HK step), recessed 4 nm (the notch)
  ZAZ edge     Cl and B in the top nanometre of the exposed edge
  Periphery    SiN with B and Cl 2–5 at%; BₓClᵧ residue ≈ 0.5 nm
  Resist       chlorinated, brominated crust on top
```

### 11.5.2 Strip and Treatment

```
Module 2 strip and post-etch treatment (reference, downstream, vacuum transfer):
  Step 1   H₂O vapor / O₂ plasma, 250 °C, 45 s   removes resist crust and
                                                 Cl/Br as HCl/HBr
  Step 2   O₂/N₂ plasma, 250 °C, 60 s             strips the resist
  Step 3   H₂/N₂ plasma, 250 °C, 20 s             reduces WOₓ grown in step 2;
                                                 removes residual Cl
After air exposure:
  DIW megasonic rinse and a W-compatible cleaner (no SC1: it dissolves W and
  TiN; no dilute HF: it attacks the ZAZ edge and the SiN)
```

### 11.5.3 Corrosion

```
Corrosion at the plate edge if halogens remain (illustrative):
  W     W + Cl⁻ + H₂O + O₂ → soluble oxychlorides; pits along grain
        boundaries; visible as "measles" on the W top near the edge after
        48 h in humid air
  TiN   Cl-catalysed oxidation and lateral attack under the SiGe: the notch
        grows from 4 nm to 10–20 nm in a few days
  SiGe  little corrosion; Br-rich passivation hydrolyses to SiOₓ
```

W corrosion is the critical one. Corroded W raises plate resistance locally and leaves particles that the inter-layer dielectric deposition buries.

---

## 11.6 Queue Times

```
Queue-time limits (reference, clean-room air, ≤ 45% RH):
  Module 1
    TiN fill → SNS etch-back             ≤ 24 h  (surface oxide, BT margin)
    SNS etch-back → PET                  0 (vacuum transfer, same tool)
    PET → support-open mask deposition   ≤ 24 h  (oxide regrowth, Cl in seam)
  Module 2
    W strap → plate mask (litho)         ≤ 48 h  (W surface oxide; BARC
                                                  adhesion)
    Plate etch → strip/PET               0 (vacuum transfer)
    PET → ILD deposition                 ≤ 8 h   (W corrosion, TiN notch
                                                  growth)
```

The tightest is the last: the plate edge is a fresh W/SiGe/TiN/ZAZ cross-section, and the ILD deposition is what seals it. A lot that misses the 8 h limit is re-treated (H₂/N₂ plasma) before ILD, and its plate edges are inspected for corrosion.

---

## 11.7 Measuring Halogens

```
Method                         What it measures                  Sensitivity
─────────────────────────────────────────────────────────────────────────────
XPS                            Cl, Br, F, B, O at the surface     ≈ 0.1–0.5 at%
                               (top 5–8 nm), chemical state
TOF-SIMS                       depth profile of Cl, F, B in       ppm-level;
                               the top 20 nm                      semi-quantitative
Ion chromatography of a wafer  extractable Cl⁻, Br⁻, F⁻ per cm²   ≈ 10¹¹ ions/cm²
rinse
TXRF                           Cl on the surface (with           ≈ 10¹¹ atoms/cm²
                               light-element detectors)
```

Monitor wafers with blanket TiN (module 1) and patterned plate test structures (module 2) are measured weekly; product is measured by ion chromatography of sacrificial wafers at module qualification.

---

## Summary and Key Takeaways

1. **The etch-back leaves 3–6 at% Cl in the TiN tops.** Chlorine catalyses oxidation and attacks the seam once the wafer meets air.

2. **Treat before air.** H₂/N₂ downstream plasma, τ ≈ 10 s at 200 °C, brings Cl below 1 at% in 30 s under vacuum transfer.

3. **The etch-back touches 0.65% of the capacitor area.** But that area contains the rim corners.

4. **Round the rim.** A 2 nm rim radius doubles the dielectric field; r ≥ 5 nm keeps the enhancement near 1.5×.

5. **The plate edge corrodes.** W and TiN with residual Cl pit and notch within days; strip, treat, and seal with ILD within 8 h.

6. **Queue times are part of the recipe.** Fill → etch-back ≤ 24 h; plate PET → ILD ≤ 8 h.

---

## Study Questions

1. The post-etch treatment chamber runs at 150 °C instead of 200 °C. With E_a = 0.3 eV, what is τ, and how long a treatment is needed to bring 5 at% Cl to 0.5 at%?

2. Compute the field enhancement at a rim of radius 3 nm with a 5.5 nm dielectric. If leakage rises a decade per 0.7 MV/cm and the flat-surface field at 1 V is 1.8 MV/cm, estimate how much more the rim leaks per unit area than the flat surface.

3. The pillar-top area is 0.65% of the capacitor area. Using your answer to Question 2, what fraction of the total pillar leakage comes from a rim band 3 nm wide around the circumference? (Circumference at the top ≈ π × 32 nm.)

4. Explain why an O₂ plasma is a poor post-etch treatment after storage-node separation but an acceptable resist strip after the plate etch, provided a reducing step follows.

5. A lot sits 30 h between plate PET and ILD at 55% RH. Describe what you would expect at the plate edge, and the inspections and re-treatment you would specify.

6. Why must the plate-etch clean avoid both SC1 and dilute HF? Propose an acceptable cleaning sequence.

---

**Next Chapter:** [Chapter 12: Plate Patterning — Profile, Notching, High-k Residue & Periphery Landing](./12-plate-patterning-profile-residue.md)

---

**Chapter 11 Development Status:** Complete  
**Version:** 1.0
