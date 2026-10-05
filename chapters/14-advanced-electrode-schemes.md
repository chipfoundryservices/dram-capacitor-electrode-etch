# Chapter 14: Advanced Schemes — Cylinder Electrodes, ALE, New Metals, 4F² & 3D DRAM

## Overview

The reference process of this book is a single-sided solid TiN pillar with a ZAZ dielectric and a W-strapped SiGe plate. It is the dominant 6F² capacitor of its generation, but it is neither the first nor the last. Older and some current products use cylinder electrodes, which need a sacrificial fill to protect their insides during node separation. Atomic-layer etching changes the arithmetic of recess and of high-k clearing. Higher-k dielectrics bring new electrode metals with new etch chemistries. Taller capacitors (Book #31), 4F² vertical-channel cells, and 3D DRAM with lateral capacitors each move the electrode etches in a different direction; in 3D DRAM, node separation stops being a blanket etch-back and becomes a lateral recess etch across a hundred tiers.

This chapter surveys these schemes and, for each, identifies which of the problems of Chapters 10–13 become harder, which become easier, and which are replaced by new ones.

**Learning Objectives:**
- Describe node separation for cylinder electrodes with a sacrificial fill and its failure modes
- Explain how atomic-layer etching removes the loading effect from the storage-node overetch
- Choose etch chemistries for Ru, Mo, and NbN electrodes and for TiO₂- and SrTiO₃-class dielectrics
- Recompute the dimple, web, and saddle constraints for a 1d-class array
- Describe lateral electrode separation in 3D DRAM and why it resembles a recess etch

---

## 14.1 Cylinder Electrodes

### 14.1.1 The Structure

In a cylinder capacitor, the TiN lines the hole instead of filling it:

```
Cylinder electrode (illustrative, larger-pitch array):
  Hole top CD           50 nm
  TiN liner             6 nm (field and sidewall)
  Inner opening         50 − 12 = 38 nm
  Capacitor area        inner surface (one-sided cylinder, mold kept)
                        or inner + outer (double-sided, mold removed)
```

### 14.1.2 Node Separation With a Sacrificial Fill

An etch-back of the field TiN cannot be done with the cylinders open: the plasma would etch the TiN inside the top of every cylinder. The cylinders are first filled:

```
Cylinder node separation (illustrative):
  1. TiN liner (6 nm)
  2. Sacrificial fill: spin-on carbon (SOC) or photoresist, or a low-temperature
     oxide, filling every cylinder and covering the field
  3. Fill etch-back: O₂-based (SOC) or fluorocarbon (oxide), endpointed when
     the field TiN is exposed; the fill stays inside the cylinders
  4. TiN etch-back: Cl₂/BCl₃, as in module 1, clearing the field TiN
  5. Fill strip: O₂ ash (SOC) or HF (oxide; also starts the mold dip-out)
```

### 14.1.3 What Changes

```
Issue                      Pillar (reference)          Cylinder with fill
────────────────────────────────────────────────────────────────────────────
Dimple / cup               10 nm cup from fill dimple  none (fill planarizes)
Rim recess                 field-clear + OE, loaded    set by the fill recess:
                                                        TiN above the fill top
                                                        is etched
Fill recess control        —                           fill top must stay
                                                        within ≈ 5–10 nm of the
                                                        SiN top: a deeper fill
                                                        recess etches the liner
                                                        inside and costs area
Residue                    field TiN on wall tops      same; plus fill residue
                                                        masking field TiN
Seam                       exposed at the cusp         none (no seam in a liner)
Capacitance cost           none (top is inside the     inner area lost above the
                           support)                    fill top
```

The cylinder trades the pillar's cup and seam for a second etch-back (the fill) whose depth controls capacitance. A fill recessed 20 nm below the SiN top exposes 20 nm of liner inside every cylinder to the TiN etch; that TiN is lost from the capacitor.

---

## 14.2 Atomic-Layer Etching of TiN

### 14.2.1 Why ALE Helps Node Separation

The recess problem of Chapter 10 has two parts: the clearing-time spread (from deposition and rate non-uniformity) and the loading jump (1.76× after the field clears). ALE attacks both. Its removal per cycle is set by a self-limiting surface reaction, not by the radical density, so it has **no loading**; and it is uniform across the wafer to the extent that the self-limiting step saturates everywhere.

```
TiN ALE options (illustrative):
  Plasma ALE    Cl₂ adsorption (no bias) → Ar⁺ 40–60 eV removal
                ≈ 0.2–0.4 nm/cycle, ≈ 4 s/cycle
  Oxidation-    O₂ or O₃ oxidizes ≈ 0.5–1 nm of TiN to TiO₂ → BCl₃ or
  based ALE     HF removes the oxide (thermal or low-energy plasma)
                ≈ 0.3–0.6 nm/cycle, ≈ 10 s/cycle
```

### 14.2.2 A Hybrid Recipe

```
Hybrid node separation (illustrative):
  Main etch (continuous)   remove 14 nm of the 16 nm after BT: stop before
                           any site clears (timed from feed-forward thickness)
  ALE                      14 cycles × 0.4 nm = 5.6 nm: clears the remaining
                           2.0 ± 1.0 nm (thickness and main-etch rate spread)
                           and recesses by the excess
  Rim recess               5.6 − (2.0 ± 1.0) = 2.6–4.6 nm across the wafer;
                           no loading jump
  Time                     + 56 s of ALE − 10 s of OE ≈ + 45 s vs the reference
```

The ALE route delivers a shallower, loading-free rim recess of 3–5 nm. Its range (± 1 nm) is still set by the incoming thickness spread, which a self-limiting etch does not see; feed-forward of the fill thickness (Chapter 15) is what narrows it further. Two cautions: ALE does not remove the non-Gaussian residue mechanisms of Chapter 10 any better than the continuous etch, and it does not change the cup, which is still the fill dimple. If the flare saddles are deeper than the ALE recess, ALE makes saddle shorts worse, not better.

---

## 14.3 New Electrode Metals and Dielectrics

### 14.3.1 Why They Change

As EOT approaches 0.4 nm, ZrO₂-based stacks run out of room. Higher-k dielectrics (rutile TiO₂, k ≈ 80–100; SrTiO₃, k > 100; doped HfO₂/ZrO₂ near a ferroelectric or antiferroelectric phase boundary) bring their own electrode requirements: rutile TiO₂ needs a template such as RuO₂ or Ru; SrTiO₃ needs a noble or oxide electrode that tolerates oxidizing deposition; lower leakage needs a higher work function than TiN.

### 14.3.2 Electrode Etch Chemistries

```
Electrode   Volatile product          Chemistry                  Issues
────────────────────────────────────────────────────────────────────────────────
TiN         TiCl₄ (136 °C)            Cl₂/BCl₃                    reference
Ru          RuO₄ (≈ 40 °C)            O₂ with Cl₂ (10–20%)        O₂-rich plasma erodes
                                                                  resist; RuO₂ residue
                                                                  if O-starved; RuO₄
                                                                  toxic and redeposits
                                                                  as RuO₂ on cool
                                                                  surfaces
Mo / MoN    MoF₆ (34 °C),             SF₆ or NF₃; or Cl₂/O₂       easy; selectivity to
            MoOCl₄ (≈ 160 °C)                                     SiN in F chemistry
                                                                  is poor
NbN         NbCl₅ (248 °C),           Cl₂/BCl₃ or SF₆, ion-       weakly volatile at
            NbF₅ (234 °C)             assisted                    60 °C; heated chuck
                                                                  helps
W           WF₆ (17 °C)               SF₆/N₂/Cl₂                  reference strap
```

Ru is the most different. Its etch is an oxidation: RuO₄ forms only with abundant oxygen, and Cl helps by forming volatile oxychlorides and keeping the surface from passivating as RuO₂. A Ru storage-node etch-back would run in an O₂/Cl₂ plasma, with no BCl₃ (which would getter the oxygen the reaction needs).

### 14.3.3 Dielectric Etch in the Plate Step

```
Dielectric        Chloride volatility           Plate-etch consequence
────────────────────────────────────────────────────────────────────────────
ZrO₂ (ZAZ)        ZrCl₄, marginal                reference: BCl₃/Cl₂, 50% OE
HfO₂/ZrO₂ (HZO)   HfCl₄ ≈ ZrCl₄                  as reference
TiO₂ (rutile)     TiCl₄, volatile                easier than ZrO₂ in BCl₃/Cl₂
SrTiO₃            SrCl₂ non-volatile (mp 874 °C) Sr residue cannot be removed
                                                 by dry etch at practical
                                                 temperatures; wet clean (dilute
                                                 HCl-based) required, with its
                                                 undercut risk
Nb₂O₅, Ta₂O₅      NbCl₅, TaCl₅, weakly volatile  ion-assisted; heated chuck
```

SrTiO₃ illustrates a general point: any dielectric containing an alkaline-earth element (Sr, Ba) leaves a non-volatile residue in halogen plasmas. The plate etch for such a dielectric must end with a wet step, and the plate overlap must absorb the wet undercut.

---

## 14.4 Taller Capacitors

Book #31 carries the capacitor to a 1d-class array on a 37 nm pitch with 26 nm top CDs and a 2.1 µm mold. The electrode etches change as follows:

```
Item                          1b reference (45 nm)     1d (37 nm, Book #31)
────────────────────────────────────────────────────────────────────────────
Cell area (hexagonal)         1734 nm²                 (√3/2) × 37² = 1186 nm²
Top CD                        32 nm                    26 nm
Fill (≥ r + 2 nm)             18 nm                    15 nm
Dimple depth t − √(t² − r²)   18 − 8.2 = 9.8 nm        15 − √(225 − 169)
                                                       = 15 − 7.5 = 7.5 nm
Wall between hole tops        13 nm                    11 nm
Pillar-top fraction           0.464                    π × 13² / 1186 = 0.448
Flare-saddle risk             saddles where flares     higher: an 11 nm wall
                              meet (> 38 nm at top)    closes with 3 nm flares
                                                       on a 28 nm top
Minimum rim recess            ≈ 5 nm                   ≈ 6–7 nm
Plate dielectric area/wafer   1.8 × 10⁴ cm²            ≈ 3.5 × 10⁴ cm²
                                                       (more cells, taller)
Phase-A clamp voltage         ≈ 1.3 V                  slightly lower (more
                                                       dielectric per antenna)
```

The web between pillar tops narrows, flare saddles become more likely, and the minimum recess rises. The plate etch is little changed; its dielectric area grows, which helps the charging clamp.

---

## 14.5 4F² Vertical-Channel DRAM

In a 4F² cell with a vertical-channel transistor, the storage node lands directly on the top of the transistor pillar, and the capacitor array sits on a square or near-square lattice:

```
4F² array (illustrative):
  F = 15 nm, cell area 4F² = 900 nm², square pitch 30 nm
  Hole top CD ≈ 20 nm; wall ≈ 10 nm
  Fill ≥ 12 nm; dimple ≈ 12 − √(144 − 100) = 12 − 6.6 = 5.4 nm
  Pillar-top fraction π × 10² / 900 = 0.35
```

Node separation is the same process at a finer scale: the web is 10 nm, saddles more likely, the cup smaller. The new risk is below: the storage node lands on the transistor's top contact, and a deep rim recess or seam groove brings the etch closer to that contact if the capacitor is short. In 4F² designs with a capacitor directly on the channel, the bottom stop and the landing structure must be designed so that the node-separation overetch, which has no stop under the pillar, cannot reach the transistor.

---

## 14.6 3D DRAM: Lateral Electrode Separation

### 14.6.1 The Structure

In 3D DRAM, cells are stacked in tiers, and each capacitor lies horizontally in its tier, reached from a vertical hole or slit that runs through the whole stack. The bottom electrode is deposited into lateral cavities from that vertical opening:

```
Lateral capacitor, schematic (one tier):

    vertical opening │ TiN │ dielectric │ plate │ ... toward the transistor
                     │═════│            │       │
                     │     ↑ TiN deposited on every surface, including the
                     │       face of the vertical opening, connecting tiers
```

The TiN covers the cavity walls of every tier and the sidewall of the vertical opening, connecting all tiers together. Node separation now means removing the TiN from the vertical sidewall and recessing it a few nanometres into each tier, so that the electrodes of different tiers and different cells are isolated.

### 14.6.2 A Recess Etch, Not an Etch-Back

```
Lateral TiN separation (illustrative):
  Tiers                    100
  Vertical opening         ≈ 6 µm deep, aspect ratio ≈ 50
  Required recess          10–20 nm into each tier, ± 1.5 nm across all tiers
  Candidate chemistries    isotropic: wet (H₂O₂-based, SC1-type, 1–3 nm/min);
                           radical Cl at elevated temperature; thermal ALE
                           (O₃ oxidation + HF or BCl₃, ≈ 0.2–0.5 nm/cycle)
```

The physics changes completely. The etch must be isotropic, because it acts sideways. It is transport-limited along a 50:1 opening, so the top tiers see more etchant than the bottom: a continuous isotropic etch recesses the top tiers more. A self-limiting process, thermal ALE or a cyclic oxidation-and-removal, recesses each tier by the same amount per cycle regardless of position, provided each half-cycle is given time to saturate at the bottom. The problems of this book's module 1, loading and clearing tails, become the problems of the companion volume *Recess Etch*, and the word-line replacement recess of 3D NAND is the nearest industrial precedent.

### 14.6.3 The Plate in 3D DRAM

The plate in a lateral capacitor fills the remaining cavity and is common to many cells; its separation between blocks is again a lateral or slit-defined cut. The high-k inside the cavities is never exposed to a plate etch except at the opening, so the residue problem moves to the vertical opening's sidewall, where ZrO₂ left behind blocks later fill or contacts.

---

## 14.7 Summary Table

```
Scheme                  Gets harder                    Gets easier
─────────────────────────────────────────────────────────────────────────────
Cylinder + fill         fill recess sets capacitance;   no cup, no seam
                        two etch-backs
ALE node separation     throughput; saddle margin      loading jump; overetch
                        if recess too small            rate spread
Ru / Mo / NbN           new chemistry; Ru toxicity;    Mo easy; TiO₂ etches
electrodes; TiO₂,       SrTiO₃ residue needs wet       more easily than ZrO₂
SrTiO₃ dielectrics
Taller (1d)             narrower web; saddles;         plate charging clamp
                        higher minimum recess
4F² vertical channel    finer web; no stop near the    smaller cup
                        transistor contact
3D DRAM lateral         isotropic recess across 100    no blanket field clear;
                        tiers; transport-limited       no loading jump
```

---

## Summary and Key Takeaways

1. **Cylinders trade the cup for a fill.** The fill recess decides how much inner TiN is lost to the etch-back.

2. **ALE removes loading.** Recess becomes cycles × removal per cycle; it does not fix particles, oxide islands, or saddles.

3. **New metals, new halides.** Ru etches as RuO₄ in O₂/Cl₂; Mo as MoF₆; NbN only with ion help. SrTiO₃ leaves Sr residue that only wet chemistry removes.

4. **Taller arrays narrow the web.** At 37 nm pitch, the wall is 11 nm and the minimum rim recess rises to 6–7 nm.

5. **4F² puts the transistor near the overetch.** With no stop under the pillar, the capacitor's bottom structure must absorb the recess.

6. **3D DRAM turns node separation into a lateral recess.** Isotropic, transport-limited, best done self-limited.

---

## Study Questions

1. A cylinder process fills with SOC and etches the fill back to 12 nm below the SiN top at one site. With a 6 nm TiN liner in a 50 nm hole and a capacitor height of 1.2 µm, what fraction of the inner capacitor area is lost at that site?

2. Design a hybrid main-etch-plus-ALE node separation for a 15 nm fill with ± 4% thickness variation, a main etch at 0.70 nm/s, and ALE at 0.35 nm/cycle. How many cycles give a rim recess of 4 ± 1 nm?

3. Why would BCl₃ be a poor additive in a Ru etch-back, and what gas mix would you start from?

4. Recompute the dimple depth, pillar-top fraction, and wall width for a 4F² array with a 28 nm square pitch, an 18 nm top CD, and an 11 nm fill.

5. In a 3D DRAM lateral recess, a continuous isotropic etch recesses the top tier by 15 nm and the bottom tier by 9 nm. Explain the cause. How would a self-limiting cyclic process change the result, and what must each half-cycle's duration satisfy?

6. A plate dielectric of SrTiO₃ is proposed. Describe the changes to the plate etch module, including the wet step, the plate overlap, and the residue monitors.

---

**Next Chapter:** [Chapter 15: Metrology, Inspection & Advanced Process Control](./15-metrology-inspection-apc.md)

---

**Chapter 14 Development Status:** Complete  
**Version:** 1.0
