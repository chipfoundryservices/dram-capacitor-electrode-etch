# Chapter 9: Chamber Walls, Seasoning, Metal Contamination & Defects

## Overview

Every etch product that does not leave through the pump lands somewhere, and in a conductor chamber that somewhere is the wall. TiClₓ from storage-node separation, WOₓFᵧ and SiOₓBrᵧ from the plate etch, boron chlorides from every BCl₃ step, and zirconium and aluminium chlorides from the high-k: each builds a layer that changes how the wall recombines chlorine, how it releases fluorine, and what it eventually sheds onto wafers. The wall is part of the process.

This chapter treats the wall as a reactant and as a contamination source. It shows how wall state moves the etch rate through the radical balance, how seasoning and waferless cleaning keep the wall in a reproducible state, how metals cross from chamber to wafer to furnace, and how particles and flakes become node-short clusters and high-k residue. It closes with the wafer bevel, where films of every module collect, flake, and arc.

**Learning Objectives:**
- Compute the effect of a change in wall recombination on Cl density and etch rate
- Design waferless clean and seasoning sequences for module 1 and module 2
- List the metal contaminants of each module and the limits that protect DRAM retention
- Estimate the number of pillars a particle shorts during storage-node separation
- Explain bevel films, bevel etch, and arcing at the wafer edge

---

## 9.1 The Wall as a Reactant

### 9.1.1 Wall Recombination

Chlorine atoms lost on the wall recombine to Cl₂ and are no longer available to etch. The wall loss rate depends on the recombination probability γ of the wall surface, which depends on what coats it:

```
Cl recombination probability (illustrative):
  Clean Y₂O₃                    γ ≈ 0.03
  TiClₓOᵧ-coated                γ ≈ 0.01
  SiOₓClᵧ-coated                γ ≈ 0.005
  BₓClᵧ-coated (hot)            γ ≈ 0.02
  Stainless steel (bare)        γ ≈ 0.1–0.3
```

### 9.1.2 Effect on the Etch Rate

From the radical balance of Chapter 3:

```
n_Cl = G / (k_p + k_w + k_r A_exp)

Reference SNS chamber, full TiN coverage (normalized units):
  k_p = 1.0 (pumping), k_w = 3.0 (wall, seasoned TiClₓOᵧ),
  k_r A = 4.8 (wafer; gives k = k_r A / (k_p + k_w) = 1.2)
  denominator = 8.8

After a full clean that leaves bare Y₂O₃ (γ three times higher):
  k_w = 9.0 → denominator = 14.8
  n_Cl falls to 8.8/14.8 = 0.59 of the seasoned value
```

A freshly cleaned wall can cut the Cl density by 40% and the TiN main-etch rate by a large fraction of that (the rate is not linear in n_Cl once the surface nears saturation, so the effect on rate is perhaps 15–25%). The first wafers after a clean clear late, and their endpoints come late. This is the **first-wafer effect**, and seasoning exists to remove it.

### 9.1.3 Fluorine Memory

In the plate chamber, fluorine from the SF₆ W step is stored in the wall (as YOF, WOₓFᵧ, and SiOₓFᵧ) and released during the following HBr/Cl₂ SiGe step. Fluorine etches SiGe spontaneously; a few percent of F in the SiGe step raises the lateral etch and changes the plate-edge profile. The memory decays within seconds to tens of seconds after the W step, so its effect falls mainly on the start of the SiGe main etch, at the top of the SiGe sidewall.

---

## 9.2 Module 1: Keeping a TiN Chamber Steady

### 9.2.1 What Deposits

```
SNS chamber deposits (illustrative):
  TiClₓOᵧ    from TiCl₄ that oxidizes on the wall (O from the window, from
             O-containing wall films, from BCl₃ impurities)
  BₓClᵧ      from the BT and ME steps
  Growth     ≈ 0.5–2 nm per wafer on the liner near the wafer plane
```

### 9.2.2 Cleaning Ti From a Wall

TiF₄ sublimes only at 284 °C, so a fluorine clean leaves Ti deposits behind as a TiF₄ skin. The waferless auto-clean (WAC) for a TiN chamber therefore uses chlorine:

```
Module 1 WAC (reference, after every wafer):
  Cl₂/BCl₃ 10 s, 600 W source, no bias    removes TiClₓOᵧ as TiCl₄
  O₂ 5 s                                  re-oxidizes the surface to a
                                          reproducible state
Season (after each wet clean or > 2 h idle):
  5 dummy TiN-coated wafers through the full recipe
```

### 9.2.3 Idle Time

A chamber that sits idle loses adsorbed chlorine from its wall and gains water from any residual leak. The first wafer after idle then sees a wall with higher γ and different oxygen content. The reference rule is that any idle longer than 2 hours triggers a short season (one or two dummy wafers); idle longer than 12 hours triggers the full five-wafer season.

---

## 9.3 Module 2: Five Chemistries on One Wall

The plate chamber's wall, described in Chapter 7, carries a layered deposit from every step. Its memories cross steps within a wafer and cross wafers:

```
Wall memory in the plate chamber (illustrative):
  Memory                    Source step   Affects            Effect
  ──────────────────────────────────────────────────────────────────────────
  F release                 W             SiGe ME (start)    lateral etch up;
                                                             top-of-sidewall bow
  Br/O-rich SiOₓBrᵧ         SiGe          HK step            Cl recombination
                                                             changes; HK rate
  B deposits                HK            next wafer's W     F consumed by B
                                                             (BF₃): W rate −3 to
                                                             −5% on first wafer
  Zr/Al deposits            HK            all steps;         sputtered back as
                                                             metal contamination;
                                                             flakes
  C deposits                BARC, resist  HK step            C getters O; HK rate
                                                             up slightly
```

### 9.3.1 Per-Wafer Clean for Module 2

```
Module 2 WAC (reference, after every wafer; see Chapter 7 for order):
  BCl₃/Cl₂ 20 s    removes Zr, Al
  O₂ 10 s          removes C
  NF₃/O₂ 15 s      removes Si, B, W
  Cl₂ 5 s          resets the wall to a chlorinated state before the next
                   wafer's BARC and W steps
```

The final chlorine step matters: without it, the next wafer starts on a fluorinated wall, and its BARC open and W step see extra fluorine.

---

## 9.4 Metal Contamination

### 9.4.1 Why Metals Matter in a Capacitor Module

The capacitor module lies above the transistors but below the back-end. Wafers from it later see anneals at 400–450 °C (forming gas, plate activation, ILD densification). At these temperatures, Cu, Ni, and Fe diffuse rapidly through silicon. In the storage-node junction, each of these introduces deep levels that raise junction leakage. Retention-time tails in DRAM are among the most metal-sensitive specifications in the semiconductor industry.

```
Metal contamination limits (reference, TXRF on monitor wafers, atoms/cm²):
  Front side, after module 1 or 2
    Fe, Ni, Cu                     ≤ 5 × 10⁹
    Cr, Zn                         ≤ 1 × 10¹⁰
    Ti (module 1: on SiN monitor)  ≤ 1 × 10¹¹ (process metal)
    Zr (module 2: on SiN monitor)  ≤ 1 × 10¹³ (residue spec, Chapter 1)
    Y, Al (chamber materials)      ≤ 1 × 10¹⁰
  Back side
    Fe, Ni, Cu                     ≤ 5 × 10¹⁰
    Zr, Ti, W, Ge                  ≤ 1 × 10¹¹
```

### 9.4.2 Sources

```
Contaminant    Source                               Path to the wafer
──────────────────────────────────────────────────────────────────────────────
Fe, Ni, Cr     HCl corrosion of stainless gas lines  gas phase; particles
               (moisture in BCl₃ or HBr lines)
Cu             contaminated parts; brazes            sputter from parts
Y              yttria coating erosion                sputter; flakes
Al             alumina parts attacked by BCl₃        AlCl₃ vapor
Zr             HK wall deposits                      sputter-back; flakes;
                                                     backside via chuck
W, Ge          plate wall deposits                   sputter-back
Ti             module 1 wall                         sputter-back (process
                                                     metal; front side OK)
```

The most dangerous sources are the quiet ones: an HBr line that has absorbed moisture produces Fe and Ni at levels that change no etch rate but raise retention failures weeks later.

### 9.4.3 Backside and Cross-Tool Contamination

The chuck surface accumulates deposits from the wafers it holds, including Zr from the plate etch. The wafer backside picks them up and carries them to the next tool: an ILD deposition, an anneal furnace. A furnace that receives Zr-contaminated backsides passes Zr to other wafers. Backside TXRF after the plate etch, and chuck cleaning at each PM, close this path.

---

## 9.5 Particles and Defects

### 9.5.1 Particles in Module 1

A particle that lands on the field TiN before or during the etch-back shadows the TiN beneath it. When the field clears everywhere else, the TiN under the particle remains, connecting every pillar it touched:

```
Pillars shorted by a particle of diameter D (masked area π D²/4):
  pillars per µm² = 577

  D = 50 nm:   masked 0.0020 µm² → ≈ 1 pillar + the TiN around it touching
                its neighbours → a pair or triple
  D = 100 nm:  0.0079 µm² → ≈ 5 pillars shorted together
  D = 200 nm:  0.031 µm² → ≈ 18 pillars
  D = 500 nm:  0.20 µm² → ≈ 113 pillars
```

A small cluster is repairable with a spare row or column; a cluster of more than about 20 cells spread over several rows and columns may exceed the local repair resource. The particle specification for module 1 is therefore tight, and particles larger than about 100 nm are the most important defect of the module:

```
Module 1 particle specification (reference):
  Adders > 45 nm on the etch-back      ≤ 5 per wafer (monitor wafer)
  Probability an adder lands on array  ≈ 0.45
  Expected masked clusters per wafer   ≈ 2 (≈ 0.002 per die): small
```

Particles that arrive after the etch-back (during unloading, transfer, or the post-etch treatment) do not mask anything and are removed by the following clean.

### 9.5.2 Particles in Module 2

In the plate etch, a particle that lands on the open area before the HK step can mask ZAZ: a high-k island. One that lands before the W step masks W, SiGe, TiN, and ZAZ: a stack island. Islands larger than the periphery contacts open contacts; islands of W and SiGe can bridge contacts. The plate etch's particle specification is similar to module 1's, with an extra emphasis on flakes from the HK wall deposits.

### 9.5.3 Flakes

```
Flake sources (illustrative):
  Wall deposits exceeding a critical thickness (stress) → spall
  ZrF₄ skins left by a wrong-order clean (Chapter 7)
  BCl₃ hydrolysis particles (boric acid) after a line leak
  Edge-ring and focus-ring deposits disturbed by ring motion
```

Flake rate rises with RF hours since the last wet clean. The wet-clean interval is set by the RF-hour count at which adders rise, typically 300–600 RF h for a plate chamber with HK, longer for module 1.

---

## 9.6 The Wafer Bevel

### 9.6.1 Films on the Bevel

Every blanket film of the capacitor module wraps over the wafer edge: CVD TiN, ALD ZAZ and TiN, LPCVD SiGe (on both sides unless stripped), and PVD W (front bevel). The bevel is not etched by the electrode etches, which see it at a steep angle and low ion flux.

```
Bevel films after the plate deposition (illustrative):
  ZAZ, TiN       on the front bevel, apex, and part of the back bevel
  SiGe           front, apex, back (until stripped)
  W              front bevel to near the apex
  Adhesion       poor on rough bevel surfaces; stress mismatched
```

### 9.6.2 Bevel Etch

A dedicated bevel-etch tool removes films from the outer 1–2 mm of the wafer with a confined plasma that touches only the edge:

```
Bevel etch steps (reference):
  After TiN fill (module 1 input)    remove TiN from the bevel
  After W strap (module 2 input)     remove W, SiGe, TiN, ZAZ from the
                                     bevel and outer 1.5 mm
```

### 9.6.3 Arcing

A conducting film on the bevel, close to the edge ring, can arc to the ring during a high-bias step. Arcs leave melted spots and splatter that lands as particles across the wafer. A wafer with W on the bevel entering the plate etch's 450 W HK step is a classic arcing risk. Bevel etch before the plate etch, and arc-detection on the bias generator (fast changes in reflected power or V_pp), are the controls.

---

## 9.7 Monitoring the Wall

```
Wall-state monitors (reference):
  Every wafer       endpoint time; post-EP slope; WAC OES (Ti and Zr
                    emission during the Cl clean fall to a floor when the
                    wall is clean)
  Daily             blanket rate monitors (TiN, SiN; W, SiGe, ZrO₂)
                    particle monitors (> 45 nm adders)
  Weekly            TXRF front and back (Fe, Ni, Cu, Zr, Y, Al)
  At PM             wall-deposit thickness at fixed coupons; chuck surface
                    cleaning; edge-ring height
```

The WAC emission is an underused signal: the time it takes for Ti or Zr emission to fall during the per-wafer clean measures how much deposit the last wafer left. A rising clean time is an early warning of a chamber whose wall is not returning to its seasoned state.

---

## Summary and Key Takeaways

1. **The wall sets the Cl density.** A freshly cleaned Y₂O₃ wall can cut n_Cl by 40% relative to a seasoned one; seasoning removes the first-wafer effect.

2. **Clean Ti and Zr with chlorine.** TiF₄ and ZrF₄ stay on the wall; chlorine first, fluorine second, chlorine last before the next wafer.

3. **Plate-chamber memories cross steps.** F from the W step bows the SiGe sidewall; B from the HK step slows the next wafer's W step.

4. **Metals matter for retention.** Fe, Ni, and Cu limits of 5 × 10⁹ cm⁻² protect junction leakage; moisture in HBr or BCl₃ lines is the quiet source.

5. **A particle in module 1 is a cluster short.** A 200 nm particle shorts about 18 pillars; > 100 nm particles are the module's most important defect.

6. **The bevel collects every film.** Bevel etch before the plate etch prevents flakes and arcs.

---

## Study Questions

1. In the radical balance of Section 9.1.2, the seasoned wall has k_w = 3.0. After a partial clean, k_w = 5.0. Compute the change in n_Cl at full TiN coverage. If the main-etch rate scales as n_Cl^0.6, by how much does the clearing time change?

2. Why would an NF₃/O₂ clean alone be a poor choice for the module 1 chamber? What would accumulate on the wall?

3. A plate chamber shows a 4% lower W rate on the first wafer of every lot. Propose a mechanism and a change to the WAC that would remove it.

4. Compute the number of pillars masked by a 300 nm particle. If each failed cell needs one spare and a row spare covers one row, how many row spares does the cluster need?

5. TXRF shows Fe at 3 × 10¹⁰ cm⁻² on module 2 monitor wafers, with no change in any etch rate. List the likely sources in order and the checks that separate them.

6. Explain how W on the bevel can produce particles across the whole wafer during the HK step.

---

**Next Chapter:** [Chapter 10: Node Separation — Field Clearing, Pillar Recess, Seam Opening & Shorts](./10-node-separation-recess-shorts.md)

---

**Chapter 9 Development Status:** Complete  
**Version:** 1.0
