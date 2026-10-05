# Chapter 10: Node Separation — Field Clearing, Pillar Recess, Seam Opening & Shorts

## Overview

Storage-node separation has one job, isolating every pillar, and one by-product, the shape it leaves at the top of every pillar. Both are decided in the last ten seconds of the etch: the transition from field to pillar tops and the overetch that follows. This chapter follows the TiN surface through those seconds. It shows where the field clears last, how the rim of each pillar recesses, how the fill dimple becomes a cup in the pillar top, when that cup reaches into the seam, and which residue mechanisms survive an overetch that removes the average film many times over.

The central conclusion is that the overetch protects against the **Gaussian** part of the clearing problem, the variation of thickness and rate, and that it does so with enormous margin. The shorts that actually occur come from **non-Gaussian** mechanisms, particles, oxide islands, pits, and wall saddles, that more overetch barely helps and that must be controlled at their source.

**Learning Objectives:**
- Describe where and in what order the field TiN clears within the array
- Compute the rim recess, the cup depth, and the seam groove for a given recipe
- Explain why anisotropic etch carries the fill dimple down and isotropic etch deepens the cusp
- Rank the residue mechanisms and show which ones overetch can and cannot address
- Compute the allowed short probability per pair and build a short Pareto
- Compare etch-back and CMP for node separation on every specification line

---

## 10.1 How the Field Clears

### 10.1.1 The Surface Before Clearing

Between the holes, the TiN lies 18 nm thick on the SiN wall tops, 13 nm wide between the 32 nm hole tops. Over each hole it is only 8.2 nm above the SiN plane at the centre, in a dimple 9.8 nm deep (Chapter 2). An anisotropic etch translates this surface downward almost unchanged.

```
Sequence in the array (anisotropic main etch, reference):
  t = 0–5 s      breakthrough removes the TiOₓNᵧ skin and ≈ 2 nm of TiN
  t ≈ 14 s       dimple bottoms (cusps) reach the SiN plane: the etch is now
                 cutting into the pillar centres, although the field is
                 still ≈ 10 nm thick
  t ≈ 23 s       field over the wall tops clears (mean); the wall tops are the
                 last array TiN to go
  t ≈ 24.5 s     endpoint
  t = 24.5–34.5  overetch, pillar tops only
```

### 10.1.2 The Last TiN Is in the Worst Place

The TiN that clears last is the thin web over the SiN wall tops, between pillar tops. It is exactly the TiN whose residue is a short. There is no geometric accident here: the field over the wall tops is the thickest TiN in the array, so it clears last by construction. Any delay to it, from a particle, an oxide patch, a thicker spot, or a lower local rate, shows up directly as a node-to-node short.

### 10.1.3 The Periphery

Outside the array, the TiN lies flat on the periphery SiN and clears at the same time as the array wall tops. A periphery residue does not short storage nodes; it may short later periphery contacts if it is in a contact field. The periphery is the best place to inspect for residue because it is large and flat (Chapter 15), but a clean periphery does not prove a clean array.

---

## 10.2 The Rim Recess

### 10.2.1 Arithmetic

From Chapter 6:

```
recess(r) = (t_EP − t_c(r)) · R_ME,loaded + t_OE · R_OE,loaded

Reference: R_ME,loaded ≈ 1.0 nm/s (transition), R_OE,loaded = 0.70 nm/s,
           t_OE = 10 s, t_EP = 24.5 s, t_c = 21.6–24.2 s (3σ)
Rim recess: 7.3–9.9 nm across the wafer (mean ≈ 8.6 nm)
Within one die: ≤ 1 nm (the die is small compared with radial profiles)
```

### 10.2.2 Contributions

```
Contribution to rim recess (mean, reference)        nm
──────────────────────────────────────────────────────────
OE at blanket rate (10 s × 0.40 nm/s)               4.0
Loading jump on OE (× 1.76)                         +3.0
ME after local clearing (average 1.6 s × 1.0)       +1.6
Total                                                8.6
```

More than a third of the recess comes from loading. A recipe developed on blanket wafers and transferred to product will recess the pillars about 75% deeper in the overetch than planned.

### 10.2.3 Limits

```
Lower limit: 5 nm
  Wall saddles up to ≈ 6 nm deep (Chapter 2) must be cleared at the rim;
  the rim of a pillar next to a saddle sees the saddle TiN connect to its
  neighbour unless recessed below the saddle bottom. With 7.3 nm at the
  thinnest-recess site, the margin is ≈ 1.3 nm at the worst saddle.

Upper limit: 15 nm
  The top support collar clamps the pillar over its 120 nm thickness
  (Book #30, Chapter 11). Recess shortens the clamp and leaves a pocket
  above the pillar that the support-open mask must fill and that the
  support-open plasma sees as a deeper TiN crescent.
```

---

## 10.3 The Cup and the Seam

### 10.3.1 Anisotropic Transfer of the Dimple

An ideal anisotropic etch moves every point of the surface straight down at the same rate. The dimple is carried into the pillar top unchanged:

```
Pillar top after etch-back (ideal anisotropic):
  Rim                 8.6 nm below the SiN surface
  Centre (cusp)       8.6 + 9.8 = 18.4 nm below the SiN surface
  Cup depth           9.8 nm (equal to the fill dimple)
```

The cup depth is fixed by the fill, not by the etch. To make it shallower, deposit more TiN (24 nm → 6.1 nm cup) or planarize before etching. The specification of Chapter 1 (cup ≤ 12 nm) allows the reference fill but not a thinner one: with a 17 nm fill on a 32 nm hole, the cup would be 17 − √(289 − 256) = 11.3 nm, near the limit.

### 10.3.2 Ion-Angle Effects

The ion-assisted yield rises with the angle of incidence up to about 60° and falls beyond it. The sloped walls of the dimple therefore etch somewhat faster than the flat field. The effect facets the cup into a cone but does not remove the cusp at its bottom, where the slopes meet.

### 10.3.3 Isotropic Component and the Cusp

Real etches have a spontaneous component that moves surfaces along their normals (Chapter 3). At a concave V-shaped cusp with half-angle α, the faces each recede by e_s, the spontaneous etch, and the vertex recedes faster:

```
Extra deepening of a V cusp per unit isotropic etch:
  Δd = e_s (1/sin α − 1)

Example: cusp half-angle α = 20°, e_s = 0.5 nm (≈ 1 nm/min over 30 s)
  Δd = 0.5 × (2.92 − 1) = 1.0 nm
α = 10°: Δd = 0.5 × (5.76 − 1) = 2.4 nm
```

At the very bottom of the cusp, α approaches zero: the cusp continues into the seam.

### 10.3.4 The Seam

The seam is the plane where the fill fronts met. If it closed well, it is a grain boundary with more chlorine and less density than the bulk, and it etches faster. If it closed poorly near the top, it is a slit. Either way, the etch follows it:

```
Seam groove below the cup bottom:
  d_seam = (f − 1) · e_v,exposed

  f          seam-to-bulk rate ratio
  e_v        vertical TiN removed at the cusp while the seam is exposed;
             the seam starts at the cusp, so it is exposed throughout:
             ≈ 2 nm (BT) + 14 nm (ME) + 7 nm (OE, loaded) ≈ 23 nm

  Well-closed seam,  f ≈ 1.15:   d_seam ≈ 3.5 nm (a nick)
  Cl-rich seam,      f ≈ 1.5:    d_seam ≈ 11 nm
  Slit seam (keyhole near the top): open; the etch enters it isotropically
```

A seam groove of a few nanometres is harmless. A groove of 10 nm or more, or an open slit, becomes a pocket that traps the support-open plasma's fluorocarbons, the dip-out's HF, and later the dielectric precursors (Book #30, Chapter 13). The specification "no open seam below the cup" means no gap wider than about 1 nm extending more than 5 nm below the cup bottom.

### 10.3.5 Controlling the Cup and the Seam

```
Knob                              Effect on cup / seam                  Side effect
────────────────────────────────────────────────────────────────────────────────────
Thicker fill (18 → 22 nm)         cup 9.8 → 6.9 nm                       +22% ME time;
                                                                        more Cl, cost
Lower chuck T (60 → 40 °C)        spontaneous etch −40%; seam groove     slightly lower
                                  −20–30%                               ME rate
BCl₃-rich ME                      BₓClᵧ deposits in the cusp (low ion    residue risk if
                                  flux) and protects it                  over-deposited
N₂ addition (5–10%)               nitrogen-rich surface slows the        lower rate
                                  seam etch
Lower OE time                     less seam exposure                     residue margin
Fill anneal / seam closure        f → 1.1                                CVD module
```

---

## 10.4 Residue Mechanisms

### 10.4.1 The Gaussian Part

The variation of thickness and rate is approximately Gaussian. How much margin does the overetch give against it?

```
Overetch capacity at the slowest 3σ site:
  TiN removable after EP at that site ≈ 0.3 × 1.0 + 10 × 0.70 = 7.3 nm
Thickness 3σ: 0.9 nm; equivalent clearing-time 3σ ≈ 1.3 s ≈ 1.3 nm at the
loaded ME rate

Margin beyond the mean, in units of the combined σ (≈ 0.45 nm of TiN):
  3σ (already inside t_EP) + 7.3 / 0.45 ≈ 3 + 16 ≈ 19σ
```

Nineteen standard deviations is an absurd margin against Gaussian variation. If the field were only Gaussian, a 2 s overetch would suffice. The 10 s overetch exists for the non-Gaussian mechanisms below and for the edge.

### 10.4.2 The Non-Gaussian Part

```
Mechanism                        What leaves TiN                     Helped by more OE?
────────────────────────────────────────────────────────────────────────────────────────
Particle (Ch. 9)                 masked TiN under the particle       no (masked)
TiO₂ islands (watermarks,        oxide that BT did not remove;       a little (low-rate
contaminated spots, long Q-time) TiN beneath etched late              sputter of TiO₂)
Wall saddles                     TiN in SiN saddles below the       yes, until recess
                                 triangular nodes                   exceeds saddle depth
Pits, scratches, voids in the    TiN in re-entrant pits; anisotropic partly (isotropic
SiN top surface                  etch cannot reach under overhangs   component helps)
BₓClᵧ / BOₓ micromasks           deposits on the field in the BT     no; reduce BCl₃ or
                                 or ME                               add Cl₂ clearing
TiOₓClᵧ redeposition             non-volatile fragments on the      a little
                                 wall tops
Edge (ring wear, Ch. 6)          late clearing in the outer 5 mm    yes
```

The pattern is clear. The overetch handles saddles and the edge. Everything else is handled at the source: particle control, queue-time control and a reliable breakthrough, SiN surface quality, and BCl₃ balance.

### 10.4.3 Pits and Re-Entrant Features

A pit in the SiN surface with an overhang, for example where the hole etch left a notch under the top SiN or a void at the SiN surface opened during the hole-etch strip, fills with TiN during CVD. An anisotropic etch removes the TiN above the pit's opening but not the TiN shadowed by the overhang. If the pit connects two holes, the shadowed TiN is a buried short. A short isotropic step at the end of the overetch, or a wet TiN clean (SC1-type, with care for the pillar tops), clears such features. The reference relies on the hole-etch module to keep the top SiN free of re-entrant defects.

---

## 10.5 Short Statistics

### 10.5.1 The Allowed Rate

```
Neighbour pairs per die:  1.7 × 10¹⁰ pillars × 6 neighbours / 2 = 5.1 × 10¹⁰
Repair budget for node shorts: 20 pairs per die (Chapter 1)
Allowed short probability:  20 / 5.1×10¹⁰ = 3.9 × 10⁻¹⁰ per pair
```

### 10.5.2 A Short Pareto (Illustrative)

```
Source                            Shorts per die (pairs)     Character
──────────────────────────────────────────────────────────────────────────
Particles > 50 nm                 0.05                       clusters
TiO₂ islands                      0.5                        random pairs,
                                                             higher after long Q
Wall saddles (edge dies)          1.5 (edge dies only)       rings at the wafer
                                                             edge; rows in die
Pits / re-entrant SiN             2                          random pairs
BₓClᵧ micromasks                  0.3                        random pairs
Total                             ≈ 2–4 (centre dies),       within the 20-pair
                                  ≈ 4–6 (edge dies)          budget
```

The Pareto changes when something drifts: a worn ring raises the edge saddle term, a long queue raises the oxide-island term, a hole-etch strip change raises the pit term. Chapter 15 shows how electrical combs and voltage contrast attribute shorts to their sources.

---

## 10.6 Etch-Back Versus CMP

```
Specification line             Dry etch-back (reference)      CMP (Book #30 reference)
──────────────────────────────────────────────────────────────────────────────────────
Top SiN loss                   ≈ 0.5–1 nm                     15–20 nm (stop + buff)
Pillar rim                     recessed 7–10 nm               dished 0–3 nm
Pillar centre                  cup ≈ 10 nm (fill dimple)      flat (planarized)
Seam                           exposed to etch; groove        smeared; slurry can
                               3–11 nm                        enter an open seam
Residue mechanism              particles, TiO₂ islands,       under-polish, scratches
                               pits, saddles, BₓClᵧ           filled with TiN, slurry
                                                              residue, abrasive
Wall saddles                   recess must exceed depth       CMP removes saddle TiN
                                                              only if it polishes SiN
                                                              below the saddle
Surface chemistry              Cl 3–6 at% in TiN surface      oxidized TiN; slurry
                                                              organics; metal ions
Mechanical stress on mold      none                           down-force and shear on
                                                              a 1.6 µm mold
Thickness control of top SiN   excellent (deposition-set)     ± 4 nm (polish-set)
Cost (Chapter 16)              ≈ $4 per wafer                 ≈ $8 per wafer
```

Neither route is better on every line. Etch-back wins on SiN budget, stress, cost, and thickness control of the top support, which matters when the top support is part of the mechanical design of the forest. CMP wins on planarity and on saddles and pits, which it removes by polishing the SiN itself. Some flows use both: a short CMP touch to planarize, followed by an etch-back to clear without SiN loss.

---

## 10.7 Tuning Summary

```
Knob                     Rim recess   Cup     Seam     SiN loss   Residue
─────────────────────────────────────────────────────────────────────────────
OE time +5 s             +3.5 nm      0       +        +0.1 nm    saddles, edge ↓
OE energy 50 → 60 eV     +1 nm        0       0        +0.3 nm    TiO₂ islands ↓
BT time +3 s             +0.5 nm      0       0        0          TiO₂ islands ↓
ME BCl₃ fraction +10%    0            −       −        −          BₓClᵧ masks ↑
Chuck T −20 °C           −0.5 nm      −       −−       0          pits ↑ (less
                                                                  isotropic)
Fill +4 nm               0            −3 nm   0        0          ME time +6 s
Loading k ↑ (wall state) +1–2 nm      0       +        0          —
```

---

## Summary and Key Takeaways

1. **The last TiN is on the wall tops.** The field is thickest exactly where residue is a short.

2. **Rim recess 7.3–9.9 nm; a third of it is loading.** Blanket-wafer recipes under-predict recess by about 75% in the overetch.

3. **The cup is the fill dimple.** Anisotropic etch carries 9.8 nm down; the fill thickness, not the etch, sets it.

4. **The seam follows the cusp.** Seam groove = (f − 1) × exposed etch: 3.5 nm for a good seam, 11 nm for a Cl-rich one.

5. **Overetch beats Gaussians by 19σ.** It cannot beat particles, oxide islands, pits, or micromasks; those are controlled at the source.

6. **Etch-back and CMP trade SiN and stress against planarity and pits.** Etch-back costs about half as much.

---

## Study Questions

1. Compute the cusp height above the SiN plane and the cup depth for a 20 nm fill in a 32 nm hole. With the reference endpoint and overetch, what are the rim and centre depths below the SiN surface?

2. A recipe is transferred from blanket development wafers to product with the overetch set to give 4 nm of recess at the blanket rate. What recess does product get, using the loading constant of Chapter 3?

3. The seam-to-bulk rate ratio rises from 1.15 to 1.4 after a change in the fill's TiCl₄ pulse. Compute the seam groove. What would you check in Book #30's support-open and dip-out results?

4. Explain, with the arithmetic of Section 10.4.1, why doubling the overetch does not halve the node-short rate.

5. A die shows 30 shorted pairs, all on the outer two rows of mats nearest the wafer edge. Which mechanism do you suspect, which chamber parameter do you check, and what is the fastest corrective action?

6. Fill in the etch-back-versus-CMP table for a process with a 60 nm top support instead of 120 nm. Which route would you choose and why?

---

**Next Chapter:** [Chapter 11: Electrode Surface Chemistry — Chlorine, Oxidation & Corrosion](./11-electrode-surface-chlorine-corrosion.md)

---

**Chapter 10 Development Status:** Complete  
**Version:** 1.0
