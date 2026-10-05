# Chapter 12: Plate Patterning — Profile, Notching, High-k Residue & Periphery Landing

## Overview

The plate etch is a stack etch with a generous pattern and an unforgiving bottom. Its features are a micrometre wide and its stack is 200 nm tall, so profile and CD are rarely the yield problem. The problems are at the transitions: a W island left at the end of the W step, a Ge-rich foot that notches, a TiN top electrode that undercuts while the high-k clears, a ZrO₂ grain left on the periphery SiN, and a veil of redeposited zirconium standing where the resist used to be.

This chapter assembles the four chemistries of Chapters 3 and 4 into one recipe, accounts for the resist, follows the plate-edge profile from top to foot, and treats the residues that come from the high-k step. It ends with the hard-mask alternative and a list of plate-etch failure modes.

**Learning Objectives:**
- Lay out the five-step plate recipe with endpoints, overetches, and times
- Build the resist budget and estimate the CD shift from resist erosion
- Explain the profile of each layer of the plate edge and the origin of the SiGe foot notch
- Compute the TiN notch during the high-k step and its consequences
- Describe veil formation and how to prevent it
- Compare the resist and hard-mask routes for plate patterning

---

## 12.1 The Recipe

```
Reference plate etch (single ICP chamber, ESC 60 °C):
  Step      Chemistry (sccm)                 P (mT)  Src/Bias (W)  E_i (eV)  Time
  ──────────────────────────────────────────────────────────────────────────────────
  BARC      CF₄ 80 / O₂ 10 / Ar 100            8     600 / 150      ≈ 75     20 s
  W         SF₆ 40 / N₂ 20 / Cl₂ 30 / Ar 50     8     600 / 180      ≈ 85     EP ≈ 12 s
                                                                              + 3 s
  SiGe ME   HBr 150 / Cl₂ 50 / O₂ 5            10     600 / 250      ≈ 110    EP ≈ 47 s
  SiGe OE   HBr 200 / O₂ 6 / He 100            15     500 / 90       ≈ 55     25 s
  HK        BCl₃ 80 / Cl₂ 20 / Ar 50            5     800 / 450      ≈ 150    Al marker
                                                                              → ≈ 90 s
  Transitions (5 × 3 s, bias off)                                             15 s
  Total plasma time                                                           ≈ 212 s
```

The W overetch removes about 15 nm of SiGe (3 s at ≈ 300 nm/min), so the SiGe main etch clears about 135–140 nm in 47 s.

---

## 12.2 The Resist Budget

### 12.2.1 Vertical Loss

```
Resist consumed (reference, 500 nm KrF on 60 nm BARC):
  Step          Time    Resist rate (nm/min)    Loss (nm)
  ───────────────────────────────────────────────────────
  BARC open     20 s         150                   50
  W             15 s         150                   38
  SiGe ME       47 s          60                   47
  SiGe OE       25 s          20                    8
  HK            90 s          50                   75
  Total                                           218
  Remaining                                      ≈ 280 nm
  Required at end                                 ≥ 150 nm
```

The requirement of 150 nm at the end is not arbitrary. Thin resist at the end of the HK step lets ions reach the W top through pinholes and at the faceted resist edge, and a very thin crust is hard to strip without damaging the plate edge.

### 12.2.2 Lateral Loss and CD

The resist edge also recedes sideways as it thins, because the top corner facets:

```
Lateral resist pull-back ≈ 0.15 × vertical loss (illustrative, 85° resist wall)
  0.15 × 218 nm ≈ 33 nm per edge
Plate CD loss ≈ 2 × 33 = 65 nm on a 1 µm feature (≈ 6.5%)
```

Most of the pull-back happens in the BARC and W steps, where the resist rate is highest, and it transfers to the plate edge as a slight taper at the W level. The mask is biased by +30 nm per edge to compensate. For the plate-edge placement specification (± 100 nm), the bias makes the pull-back harmless; its variation across the wafer (± 10 nm) is what counts.

---

## 12.3 The Profile, Layer by Layer

```
Plate-edge profile (reference, illustrative):
  Layer       Thickness   Angle       Feature
  ──────────────────────────────────────────────────────────────────────
  W           40 nm       84–86°      slight taper from resist pull-back;
                                      WNₓ sidewall passivation
  SiGe        150 nm      86–88°      SiOₓBrᵧ passivation; F memory can
                                      bow the top 20 nm by 2–3 nm
  SiGe foot   ≈ 10 nm     notch       2–3 nm (Ge-rich initial layer)
  TiN         5 nm        recessed    4 nm notch under the SiGe
  ZAZ         5.5 nm      ≈ 80°       foot of 2–5 nm beyond the SiGe edge
  SiN         landing     —           4 nm recess in the open area
```

A slightly tapered edge (80–88°) is preferred to a vertical one: the inter-layer dielectric deposited over the 200 nm plate step fills a tapered edge without a void at the foot. A re-entrant edge, which a bowed SiGe or a deep notch can produce, leaves a keyhole in the ILD that later opens during periphery contact etch.

---

## 12.4 The SiGe Foot Notch

### 12.4.1 Origin

The first 10 nm of the LPCVD SiGe, deposited on the TiN, are richer in Ge (Chapter 2): about Si₀.₆₅Ge₀.₃₅ instead of Si₀.₇Ge₀.₃. The spontaneous lateral etch rises steeply with Ge content (Chapter 3), and this layer is exposed laterally during the last part of the main etch, when the Cl-containing chemistry is still on:

```
Foot notch (illustrative):
  Lateral rate, Ge-rich foot, SiGe ME (25% Cl)    ≈ 8 nm/min
  Exposure in ME after the foot is uncovered       ≈ 8 s → ≈ 1.1 nm
  Lateral rate in OE (HBr/O₂)                      ≈ 1 nm/min
  Exposure in OE                                   25 s → ≈ 0.4 nm
  F memory early in ME (top only)                  —
  Total foot notch                                 ≈ 1.5–3 nm
```

### 12.4.2 No Charging Notch

In gate etch, a notch often forms at the foot of polysilicon where it lands on gate oxide: electrons are shaded by the resist, ions charge the insulating bottom positively, and the deflected ions etch the foot. The plate etch lands on TiN, a conductor connected to the whole plate island, so the bottom cannot charge locally. The plate etch's foot notch is chemical, not electrostatic, and it is controlled by the Ge profile of the plate fill and by the Cl fraction at the end of the main etch.

---

## 12.5 The TiN Notch

The 5 nm top-electrode TiN is exposed at the plate edge from the moment it clears in the open area, about 6 s into the HK step, until the step ends:

```
TiN lateral etch in BCl₃/Cl₂ at 60 °C:    ≈ 3 nm/min
Exposure                                   ≈ 90 − 6 = 84 s
Notch                                      ≈ 4.2 nm
Specification                              ≤ 15 nm
```

### 12.5.1 Why It Matters Even Over the Periphery

The notch leaves a 5 nm-high slot under the SiGe edge, with the ZAZ as its floor. Consequences:

1. **ILD void.** A slot 5 nm high and 4 nm deep is too small to fill. It stays as a void along the plate perimeter. A void that is a few nanometres deep is harmless; one that is 20 nm deep (after corrosion, Chapter 11) is a path for moisture.
2. **Exposed ZAZ edge.** The dielectric edge at the slot has seen BCl₃, Cl, and UV. It is not over an active cell (the plate edge is 1.5 µm from the last dummy row), so its leakage does not reach a storage node. But a notch that grows by corrosion or by a much longer HK step moves the exposed region toward the array.
3. **Edge field.** The plate edge is a conductor edge over the periphery SiN, which is not a capacitor; no field enhancement concern arises there.

---

## 12.6 High-k Clearing in Practice

### 12.6.1 The Endpoint and the Overetch

The HK step uses the Al marker (Chapter 8) to predict the clearing time of each wafer and runs 50% beyond it. The overetch is the tightest margin in the book: the grain-tail model of Chapter 4 asks for about 51% on the grain distribution alone and about 55% at the slowest site of the wafer.

### 12.6.2 Where Residue Appears

```
Location of ZrO₂ residue (most to least frequent, illustrative):
  1. Wafer edge (outer 5 mm)       edge-ring wear lowers HK rate
  2. Narrow spaces between plate   lower ion flux at the bottom of 3 µm spaces
     islands                       next to 200 nm walls (minor)
  3. Under redeposited material    sputtered W/SiGe products masking the ZAZ
                                   early in the HK step
  4. Particle shadows              Chapter 9
  5. Random grains                 the statistical tail of Chapter 4
```

### 12.6.3 Detecting It

Surface analysis (TXRF on a periphery pad) catches averages above about 10¹² Zr cm⁻² but not single grains (Chapter 15). The decisive test is electrical: periphery contact chains in the scribe, fabricated through the full contact module, fail open where ZrO₂ residue is present. Because that test arrives weeks later, the HK step is guarded in production by the Al-marker endpoint, the edge-ring life, and the per-wafer WAC record.

---

## 12.7 Veils

### 12.7.1 Mechanism

During the HK step, ZrClₓ, AlClₓ, and boron oxychloride fragments sputtered from the open area are only partly volatile at 60 °C. Some land on the resist sidewall a few hundred nanometres away and stick. As the step continues, a thin inorganic film builds on the resist sidewall:

```
Veil formation (illustrative):
  Composition         Zr-O-Cl-B with carbon from the resist
  Thickness           1–3 nm on the resist sidewall
  Height              the remaining resist height above the W, ≈ 250 nm
```

When the resist is stripped, the inorganic film does not burn. It is left standing as a thin wall, a **veil**, on top of the plate edge. Veils fall over during the clean and land as Zr-containing flakes on the periphery, where they can open contacts like any other ZrO₂ residue.

### 12.7.2 Prevention

```
Method                               How it works
────────────────────────────────────────────────────────────────────────────
Higher Cl₂ fraction at the end of    volatilizes more of the sputtered Zr as
the HK step (20% → 35%)              ZrCl₄; at some cost in BₓClᵧ balance
Bias pulsing in the HK step          lower peak ion flux; less sputtered
                                     non-volatile product
Resist taper                         a sloped resist wall collects less and
                                     is attacked by ions, which clean it
Strip sequence: H₂O/O₂ first         oxidizes and loosens the veil; megasonic
(Chapter 11), then megasonic rinse   rinse removes it before it dries on
                                     the surface
Hard-mask route (Section 12.9)       the veil forms on the oxide hard mask,
                                     which stays and is buried in the ILD
```

---

## 12.8 Landing on the Periphery SiN

```
Periphery SiN after the plate etch (reference):
  Starting thickness                 120 nm
  Loss in HK overetch                ≈ 4 nm (2–7 nm across the wafer)
  Loss in SiGe OE (none: SiGe still covers until clear; then ≈ 1 nm/min)
                                     ≈ 0.3 nm
  Remaining                          ≈ 115–118 nm
  Surface                            B and Cl 2–5 at%; ≈ 0.5 nm BₓClᵧ residue
                                     before strip and treatment
```

The SiN loss is small and harmless to the periphery contacts, which etch through it anyway. The surface residues matter for adhesion of the ILD: boron oxychloride is hygroscopic and leaves a weak interface if not removed in the strip (Chapter 11).

### 12.8.1 Alignment Marks and the Scribe

The plate is removed from the scribe lines and from over the alignment marks used by later lithography. The high-k is removed with it. A mark covered by residual ZAZ or a thin W island reads differently in the alignment system; a plate-etch change that alters the mark signal shows up as an overlay shift at the next critical layer.

---

## 12.9 The Hard-Mask Route

```
Hard-mask route (Chapter 7) compared with the resist route:
  Item                     Resist route (reference)     Oxide HM route
  ─────────────────────────────────────────────────────────────────────────
  Mask                     500 nm KrF + 60 nm BARC      100 nm PE-TEOS, opened
                                                        with resist, resist
                                                        stripped before W etch
  Extra steps              none                         HM dep, HM open, strip
  W surface                clean                        WOₓ from the strip:
                                                        W breakthrough needed
  Resist budget            218 of 500 nm                not applicable; HM loss
                                                        ≈ 15 nm
  HK step temperature      60 °C                        up to 250 °C possible
  Veils                    on resist; must be removed   on HM; buried in ILD
  CD shift                 ≈ 65 nm (biased)             ≈ 10 nm
  Plate-edge cleanliness   strip at the edge            no strip after etch
```

The hard-mask route is more expensive and more robust. It is the usual choice when a hot HK step is used, when veils are a recurring yield problem, or when the plate etch must also open other layers that a resist cannot survive.

---

## 12.10 Failure Modes

```
Symptom                              Likely cause                         Chapter
────────────────────────────────────────────────────────────────────────────────────
SiGe pips / micromask in open area   W islands left at the end of the     3, 8
                                     W step (late endpoint, grain tail)
Plate-edge bow at the SiGe top       F memory from the W step             9
Foot notch > 5 nm                    Ge-rich initial layer; high Cl in    12.4
                                     ME; chuck too hot
TiN notch > 10 nm                    long HK step; hot chuck; corrosion   12.5, 11
                                     after PET
Periphery contact opens (scribe      ZrO₂ residue: edge ring, HK rate     4, 6, 12.6
chains) at the wafer edge            drift, short Al-marker OE
Zr flakes on periphery               veils not removed; wall flakes       12.7, 9
Plate resistance high at the edge    W corrosion; W thinned by resist     11, 12.2
                                     pinholes
Overlay shift at the next layer      residue on alignment marks           12.8.1
ILD voids along the plate perimeter  re-entrant edge; deep TiN notch      12.3, 12.5
```

---

## Summary and Key Takeaways

1. **Five steps, about 212 s.** BARC, W, SiGe ME, SiGe OE, HK; the HK step is 90 s of it.

2. **Resist budget: 218 of 500 nm; CD shift ≈ 65 nm.** Bias the mask; keep ≥ 150 nm at the end.

3. **The foot notch is chemical.** Ge-rich SiGe at the TiN interface notches 1.5–3 nm; landing on a conductor prevents charging notch.

4. **The TiN notches ≈ 4 nm in the HK step.** It is over the periphery but it is a void and a corrosion path.

5. **Residue and veils come from the HK step.** Al-marker overetch, Cl fraction, pulsing, and the strip sequence control them.

6. **A hard mask buries the problems.** It costs steps but removes the resist budget and buries veils in the ILD.

---

## Study Questions

1. Recompute the resist budget if the HK overetch is raised from 50% to 70% and the SiGe is 170 nm thick. Is 500 nm of resist still enough?

2. With the lateral pull-back ratio of 0.15, what mask bias is needed to keep the plate edge within ± 20 nm of design? If the pull-back ratio varies ± 0.03 across the wafer, what is the placement variation?

3. The Ge content of the first 10 nm of SiGe rises to 40%. Using Chapter 3, estimate the new foot notch. Which recipe change would you make first?

4. The HK step lengthens to 110 s on a chamber with a worn ring. Compute the TiN notch. At what step time does the notch reach the 15 nm specification?

5. Explain why veils form on the resist sidewall during the HK step but not during the SiGe step.

6. A new product puts the plate edge only 0.5 µm from the last dummy row. Which failure modes in Section 12.10 become more serious, and why?

---

**Next Chapter:** [Chapter 13: Plasma-Induced Damage to the Capacitor Dielectric](./13-plasma-induced-dielectric-damage.md)

---

**Chapter 12 Development Status:** Complete  
**Version:** 1.0
