# Chapter 2: The Electrode Stack — Fill, Dielectric, Top Electrode & Plate

## Overview

The two electrode etches act on films that other modules have built, and almost every property of those films shows up in the etch. The thickness of the field TiN sets the etch-back time, and its uniformity sets the overetch. The shape of the TiN surface over each filled hole sets the shape of the pillar top. The surface oxide on the TiN sets the incubation of the etch. In the plate stack, the crystallinity of the ZrO₂ sets its etch rate, the germanium content and boron doping of the plate fill set its lateral etch, and the tungsten grain structure sets its roughness and residue. This chapter describes the incoming films as the etches see them.

**Learning Objectives:**
- Describe the TiN fill and its field overburden, and compute the depth of the dimple over each filled hole
- Explain the hole-top flare, the wall saddle it creates, and how it can join neighbouring pillar tops
- Describe the ZAZ dielectric, the top-electrode TiN, the SiGe plate fill, and the W strap, and the property of each that matters to the plate etch
- Compute the sheet resistance of the plate and the contribution of each layer
- List the incoming variations each etch must absorb

---

## 2.1 The Incoming Surface at Storage-Node Separation

### 2.1.1 The Top Support After the Hole Etch

The top silicon nitride support was deposited as part of the mold (Book #29). The hole etch, the mask strip, and the post-etch clean consume part of it. The storage-node separation starts with:

```
Top SiN at the start of module 1 (reference):
  Thickness                 122 nm (± 3 nm, 3σ across the wafer)
  Composition               PECVD SiNₓ, N/Si ≈ 1.15, 8–12 at% H
  Stress                    ≈ +300 MPa (tensile), chosen with the middle support
                            to hold the forest flat (Book #30, Chapter 11)
  Hole top CD               32 nm (± 1.5 nm, 3σ)
  Wall between hole tops    45 − 32 = 13 nm (nominal)
```

### 2.1.2 The Hole-Top Flare and the Wall Saddle

The top of each hole is not a sharp corner. During the hole etch, the faceting of the mask and the nitride at the top of the hole leave a chamfer, or flare, a few nanometres deep. In a hexagonal array the SiN between holes is not uniform: it is widest at the triangular nodes between three holes and narrowest on the line joining two nearest neighbours. On that narrow wall, the flares of the two holes nearly meet, and the faceting rounds the wall top down below the level of the triangular nodes. Every nearest-neighbour wall therefore carries a shallow **saddle**:

```
Hole-top flare and wall saddle (illustrative):
  Flare at each hole top               ≈ 3 nm deep, ≈ 4 nm wide
  Narrowest wall, 5 nm below the top   45 − 32 = 13 nm
  Narrowest wall at the surface        13 − 2 × 4 = 5 nm
  Saddle depth below the triangular
  nodes                                ≈ 3 nm (nominal); up to ≈ 6 nm where
                                       the top CD is large or the facet is
                                       deep (typically at the wafer edge)
```

TiN fills the saddle during the fill, and the TiN lying in it sits deeper than the rest of the field. Because the etch-back front moves down uniformly, the saddle TiN clears only when the front has passed below the saddle bottom, and by then the pillar rims on either side have been recessed by the same amount. Unless the rims are recessed below the saddle bottom, the two pillars stay connected by TiN lying in it. This sets the **lower limit of the pillar recess**: the rim recess must exceed the deepest saddle on the wafer, about 5–6 nm in the reference.

### 2.1.3 The TiN Fill

```
TiN fill (reference):
  Process                   pulsed CVD, TiCl₄ + NH₃, 580 °C
  Thickness on the field    18.0 nm (± 0.9 nm, 3σ ≈ ± 5%)
  Top hole radius           16 nm → fill closes when ≥ 16 nm is deposited
  Grain structure           columnar on the field, ≈ 8–12 nm grains;
                            radial in the pillar, meeting at a central seam
  Density                   ≈ 5.0–5.2 g/cm³ (bulk 5.4)
  Residual Cl               ≈ 0.5 at% in the bulk; 1–3 at% at the seam
  Resistivity               ≈ 150–200 µΩ·cm on the field
  Young's modulus           ≈ 400 GPa
```

### 2.1.4 The Dimple Over Each Hole

Because the fill is conformal, the TiN surface over each hole is lower than the field. The fill grows from every point of the surface at the same rate. Above a hole of radius r, after a deposit t ≥ r, the surface at the hole centre lies at the height where spheres of radius t centred on the hole's top corners meet:

```
Height of the TiN surface at the hole centre, above the SiN top:
  h_c = √(t² − r²)

Reference: t = 18 nm, r = 16 nm
  h_c = √(324 − 256) = √68 = 8.2 nm
  Dimple depth = t − h_c = 18 − 8.2 = 9.8 nm

Thicker fill, t = 24 nm:
  h_c = √(576 − 256) = 17.9 nm → dimple 6.1 nm
```

The reference fill has a dimple nearly 10 nm deep over every hole. Its bottom is a cusp that leads directly into the seam. Chapter 10 shows that an anisotropic etch-back carries the dimple down into the pillar top, while an isotropic etch deepens the cusp and opens the seam. The dimple is the single most important geometric feature of the storage-node separation.

### 2.1.5 Surface Oxide

Between the fill and the etch-back the wafer is exposed to clean-room air for a queue time of hours to a day. TiN oxidizes at the surface:

```
TiN surface after air exposure (illustrative):
  TiOₓNᵧ layer              1.0–1.5 nm after 4 h; 2.0 nm after 48 h
  Composition               TiO₂-like at the surface, grading to TiN
  Effect on the etch        Cl₂ alone does not etch TiO₂ (Chapter 3);
                            a breakthrough step is needed
```

A variable queue time is a variable incubation time. Chapter 6 and Chapter 15 return to it.

---

## 2.2 The Periphery and the Wafer Edge at Module 1

Outside the array, the field TiN lies flat on the top SiN of the periphery mold. There are no holes and no dimples. The etch-back clears it at the same rate as the field in the array, and the periphery is where residue is easiest to inspect, because there is a large flat area of SiN to examine (Chapter 15).

At the wafer bevel, the CVD TiN wraps over the edge onto the bevel and partly onto the backside. The etch-back reaches the top bevel but not the backside. Bevel TiN is removed by a separate bevel etch or wet edge clean, because TiN left there flakes during later thermal steps.

---

## 2.3 The Dielectric

### 2.3.1 ZAZ

After the mold etch, the dielectric is grown by ALD on every surface: the outside of every pillar, both faces of each support, the bottom stop, the periphery top SiN, and the scribe.

```
Dielectric (reference):
  Stack                     ZrO₂ 2.6 nm / Al₂O₃ 0.3 nm / ZrO₂ 2.6 nm ("ZAZ")
  Total physical            5.5 nm
  EOT                       0.50 nm (k_eff ≈ 43; tetragonal ZrO₂ on TiN)
  ALD                       Zr precursor (CpZr-type) + O₃, 280 °C;
                            TMA + O₃ for Al₂O₃
  Crystallinity             amorphous as deposited; partly tetragonal after
                            the TiN top electrode (400 °C) and fully after the
                            SiGe plate (425 °C, ≈ 1 h)
  Breakdown field           ≈ 4.5 MV/cm → V_bd ≈ 2.5 V
  Leakage                   ≈ 1 fA per cell (median) at 1.0 V after plate
```

### 2.3.2 What Crystallinity Does to the Etch

The plate etch sees the dielectric after it has crystallized. Crystalline tetragonal ZrO₂ is denser than amorphous ZrO₂ and etches more slowly in halogen plasmas, by about 0.6–0.8×. Its grain boundaries etch faster than the grains. The result is that the last nanometre of a crystalline film clears unevenly, leaving isolated grains as islands (Chapter 12). The Al₂O₃ insertion layer stays amorphous; at 0.3 nm it is less than two monolayers and clears quickly.

### 2.3.3 Dielectric Away From the Array

On the periphery top SiN, the same 5.5 nm ZAZ lies flat. It has no function there. The plate etch must remove it completely.

---

## 2.4 The Top Electrode

```
Top electrode (reference):
  Process                   ALD TiN, TiCl₄ + NH₃, 400 °C
  Thickness                 5.0 nm on the field (± 0.3 nm)
  Inside the forest         closes the gaps: 17 − 2 × 5.5 = 6 nm before the
                            top electrode; closed at ≈ 3 nm per side, with a
                            seam at the centre of each gap
  Resistivity               ≈ 250 µΩ·cm (thin, fine-grained)
  Cl                        ≈ 1 at%
  Role at the plate etch    5 nm of TiN between SiGe and ZAZ; the SiGe
                            overetch must stop on it; it must then be removed
                            from the periphery together with the ZAZ
```

The top electrode sets the work function and the interface chemistry on the plate side of the dielectric. Its thickness is not chosen for conduction: the SiGe and W carry the current.

---

## 2.5 The Plate Fill

### 2.5.1 Why Silicon-Germanium

The space above the top electrode must be filled with a conductor that can enter the support openings (50 nm wide, narrowed by dielectric and top electrode to about 29 nm) and cover the array top, at a temperature low enough that the ZAZ and the TiN interface are not degraded:

```
Plate-fill requirements:
  Deposition temperature    ≤ 450 °C (ZAZ leakage, TiN oxidation at the interface)
  Conformality              fills 29 nm openings 120 nm deep in the top support
  Conductivity              enough with a W strap above it
  Stress                    low; must not tilt the edge pillars (Book #30, Ch. 16)
```

Boron-doped polycrystalline Si₁₋ₓGeₓ meets these. Germanium lowers the deposition and crystallization temperature of the film; boron activates during deposition without a separate anneal.

```
SiGe plate fill (reference):
  Composition               Si₀.₇Ge₀.₃, B ≈ 3 × 10²⁰ cm⁻³
  Process                   LPCVD batch furnace, SiH₄ + GeH₄ + BCl₃, 425 °C
  Thickness above the top
  support                   150 nm (± 4%, 3σ)
  Grain size                30–60 nm, columnar
  Resistivity               ≈ 2 mΩ·cm
  Stress                    ≈ −100 to +100 MPa
```

### 2.5.2 Composition and the Etch

The germanium fraction and the boron concentration are not uniform through the film. Ge tends to be higher at the start of a batch deposition and near the wafer edge; boron segregates to grain boundaries. Both matter to the plate etch: Ge–Ge and Si–Ge bonds are weaker than Si–Si bonds, so Ge-rich regions etch faster laterally in chlorine (Chapter 3). A Ge-rich layer at the bottom of the SiGe, next to the TiN, produces a **notch** at the foot of the plate edge (Chapter 12).

### 2.5.3 The Batch Furnace and the Backside

LPCVD deposits SiGe on both sides of the wafer and on the bevel. The backside SiGe must be stripped before the wafer returns to an electrostatic chuck, because a doped semiconductor film on the backside changes the chucking force and can contaminate the chuck. The reference strips it with a backside wet etch before the W deposition.

---

## 2.6 The W Strap

```
W strap (reference):
  Process                   PVD W, with a 2–3 nm WNₓ glue layer (counted in
                            the 40 nm)
  Thickness                 40 nm (± 3%)
  Resistivity               ≈ 15 µΩ·cm (thin PVD, α-W)
  Stress                    ≈ +1.0 GPa (tensile); set by sputter pressure
  Grain size                ≈ 20–30 nm
  Surface roughness         ≈ 1.0–1.5 nm RMS
```

### 2.6.1 Plate Sheet Resistance

```
Sheet resistance:
  W:     R_s = ρ/t = 15×10⁻⁸ Ω·m / 40×10⁻⁹ m = 3.75 Ω/□
  SiGe:  R_s = 2×10⁻⁵ Ω·m / 150×10⁻⁹ m = 133 Ω/□
  TiN:   R_s = 2.5×10⁻⁶ Ω·m / 5×10⁻⁹ m = 500 Ω/□
  Parallel: 1 / (1/3.75 + 1/133 + 1/500) = 3.6 Ω/□
```

The W carries almost all the current. Without it, the plate would be about 100 Ω/□. Plate resistance matters because every sensing event couples charge into the plate; a resistive plate "bounces" locally and reduces the sense signal of neighbouring cells. The W strap is what makes the plate etch a four-material etch rather than a three-material one.

---

## 2.7 The Plate Mask

### 2.7.1 Layout

```
Plate layout (reference):
  One plate island per bank (32 islands per 16 Gb die)
  Island size               ≈ 1.1 × 1.2 mm (cell area plus sense-amp and
                            sub-word-line strips it bridges over)
  Overlap beyond the last
  dummy row                 1.5 µm on the periphery top SiN
  Space between islands     ≥ 3 µm
  Minimum feature           ≈ 1 µm (plate contact landing tabs)
  Covered fraction          ≈ 55% of the wafer; open ≈ 45%
```

### 2.7.2 Mask Stack

```
Plate mask (reference):
  BARC                      organic, 60 nm (suppresses W reflection at 248 nm)
  Resist                    KrF, 500 nm
  CD control                ± 50 nm on 1 µm features (coarse layer)
  Overlay                   ± 60 nm to the array
```

The plate pattern is coarse, so a KrF resist directly on BARC is enough. The resist budget is set by the etch, not by the lithography: four etch steps remove about 250 nm of resist (Chapter 12). An oxide hard mask, which allows a hotter chuck for the high-k step, is an option treated in Chapter 7.

---

## 2.8 Incoming Variation

```
Module 1 (storage-node separation) inherits:
  Field TiN thickness                ± 5% (3σ)    → clearing time ± 5%
  Surface oxide (queue time)         1.0–2.0 nm   → incubation 2–6 s
  Hole top CD                        ± 1.5 nm     → dimple depth, saddle depth
  Wall-saddle depth                  3–6 nm       → minimum recess
  Top SiN thickness                  ± 3 nm       → carried to Book #30

Module 2 (plate etch) inherits:
  W thickness                        ± 3%
  SiGe thickness                     ± 4%         → largest clearing-time spread
  SiGe Ge fraction                   ± 2% absolute → lateral etch, notch
  Top-electrode TiN                  ± 0.3 nm
  ZAZ thickness                      ± 0.2 nm; crystallinity varies with the
                                     SiGe furnace position
  Wafer bow (W stress)               up to 80 µm   → chucking, edge uniformity
```

Each item is absorbed by an overetch, by an endpoint, or by feed-forward control. Chapter 15 shows which.

---

## Summary and Key Takeaways

1. **The field TiN is 18 nm, and its surface is not flat.** The fill leaves a dimple about 10 nm deep over every hole, ending in a cusp at the seam.

2. **Wall saddles set the minimum recess.** Hole-top flares round the narrow nearest-neighbour walls into saddles 3–6 nm deep; TiN lies in them, and the pillars must be recessed below it.

3. **The surface oxide needs a breakthrough.** A queue-time-dependent TiOₓNᵧ layer of 1–2 nm sets the incubation.

4. **The plate stack is four films.** W (40 nm) carries the current; SiGe (150 nm) fills; TiN (5 nm) is the electrode; ZAZ (5.5 nm, crystallized) is the dielectric that must be removed from the periphery.

5. **Composition matters to the profile.** Ge-rich SiGe at the TiN interface notches; crystalline ZrO₂ clears unevenly.

---

## Study Questions

1. Compute the dimple depth over a hole of 35 nm top CD with an 18 nm fill. What fill thickness gives the reference dimple of 9.8 nm for this CD?

2. Two neighbouring holes have top CDs of 34 nm and 35 nm, and each has a flare 4 nm wide. What is the narrowest wall width at the surface? If the saddle depth grows as that width shrinks, as in Section 2.1.2, why would you expect the deepest saddles at the wafer edge?

3. Recompute the plate sheet resistance if the W is reduced to 30 nm and its resistivity rises to 18 µΩ·cm. What fraction of the current now flows in the SiGe?

4. The support openings are 50 nm wide. After 5.5 nm of ZAZ and 5 nm of TiN on each side, what is the opening the SiGe must fill? What is its aspect ratio in the 120 nm top support?

5. A wafer waits 48 h instead of 4 h between the TiN fill and the etch-back. Using Section 2.1.5, by how much does the surface oxide thicken, and what would happen to a recipe that uses only Cl₂ with no breakthrough step?

6. Explain why the plate etch is easier lithographically but harder chemically than the capacitor hole etch.

---

**Next Chapter:** [Chapter 3: Plasma Chemistry of TiN, SiGe & W Etching](./03-tin-sige-w-plasma-chemistry.md)

---

**Chapter 2 Development Status:** Complete  
**Version:** 1.0
