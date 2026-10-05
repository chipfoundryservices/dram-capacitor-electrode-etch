# Chapter 1: The Capacitor Electrodes & Why They Are Etched

## Overview

A DRAM storage capacitor has two electrodes. The **bottom electrode**, or storage node, is private to each cell: it is wired through a landing pad to the drain of that cell's access transistor and holds the bit. The **top electrode**, or cell plate, is shared: one continuous conductor wraps every capacitor in a block of the array and is held at a fixed voltage. Both electrodes are deposited as blanket films that cover the whole wafer, and both must be cut. The bottom electrode must be cut into seventeen billion separate pieces, one per cell, without leaving a single conducting thread between neighbours. The top electrode must be cut into a few dozen large islands, one per array block, removed cleanly from everything else, without damaging the 5.5 nm dielectric it covers.

These two cuts are the **capacitor electrode etches**. The first, **storage-node separation** (SNS), is a blanket etch-back of titanium nitride that stops when the TiN between the pillar tops is gone. The second, **cell-plate patterning**, is a masked etch through a stack of tungsten, boron-doped silicon-germanium, titanium nitride, and a zirconia-based high-k dielectric, landing on a silicon nitride surface in the periphery. This chapter explains why each cut is needed, where it sits in the capacitor module, what it costs if it goes wrong, and the specification sheet that the rest of the book works against.

**Learning Objectives:**
- Describe the two electrodes of a pillar capacitor and the role of each in the cell
- Explain why the bottom electrode must be separated and the top electrode patterned
- Compute the leakage that a conducting residue between two storage nodes would cause, and compare it with the retention budget
- Place the two electrode etches in the capacitor module flow, before and after Book #30's mold etch
- List the specification of each etch and the failure that each line protects against

---

## 1.1 Two Electrodes, Two Different Jobs

### 1.1.1 The Cell

```
1T1C cell (reference):

   Bit line ──┤ access transistor ├── landing pad ── storage node (TiN pillar)
                    │                                       │
                word line                            high-k dielectric
                                                            │
                                                  cell plate (TiN / SiGe / W)
                                                            │
                                                   V_plate = V_core/2 = 0.55 V
```

The storage node is charged to 0 V or V_core = 1.10 V through the access transistor. The plate sits at half that, so the dielectric sees at most ±0.55 V in operation. When the word line opens, the storage node shares its charge with the bit line:

```
ΔV_BL = (V_core/2) · C_s / (C_s + C_BL)
      = 0.55 × 8.6 / (8.6 + 40) = 97 mV       (reference C_s = 8.6 fF)
```

The capacitance comes from the outer surface of the TiN pillar, 28 nm wide on average and exposed over 1410 nm of height, covered by a dielectric of EOT 0.50 nm (Book #30, Chapter 1).

### 1.1.2 Private and Shared

The two electrodes differ in one essential way:

```
                       Storage node (bottom)          Cell plate (top)
──────────────────────────────────────────────────────────────────────────────
Count per 16 Gb die    1.7 × 10¹⁰                     a few tens (one per bank
                                                      or array block)
Size                   28 nm × 1.6 µm pillar          ≈ 1 mm² island
Voltage                0 or 1.10 V (the bit)          0.55 V (fixed)
Must be isolated from  every other storage node       the periphery and the
                                                      other plate islands
Film when deposited    18 nm TiN over the whole       5 nm TiN + 150 nm SiGe
                       wafer                          + 40 nm W over the whole
                                                      wafer, on 5.5 nm high-k
Cut by                 blanket etch-back (no mask)    masked plate etch
                       or CMP
```

The storage nodes must be **many and separate**. The plate must be **one and continuous** within its island, and absent everywhere else.

---

## 1.2 Why the Bottom Electrode Must Be Separated

### 1.2.1 From One Film to Seventeen Billion Pillars

The bottom electrode is TiN deposited by pulsed CVD into the capacitor holes of Book #29. Deposition is conformal: TiN grows on the hole wall and on the top surface of the mold at the same time. To fill a hole 32 nm wide at the top, at least 16 nm must be deposited; the reference deposits 18 nm. When the fill is done, every hole is plugged with TiN and the whole wafer is covered by an 18 nm TiN sheet that joins every pillar to every other.

```
After TiN fill (cross-section, not to scale):

   ═══════════════════════════════════════════   ← field TiN, 18 nm, continuous
   ▓▓▓▓▓█▓▓▓▓▓█▓▓▓▓▓█▓▓▓▓▓█▓▓▓▓▓█▓▓▓▓▓█▓▓▓▓▓    ← top SiN support, 122 nm
   ░░░░░█░░░░░█░░░░░█░░░░░█░░░░░█░░░░░█░░░░░    ← upper oxide, 650 nm
   ▓▓▓▓▓█▓▓▓▓▓█▓▓▓▓▓█▓▓▓▓▓█▓▓▓▓▓█▓▓▓▓▓█▓▓▓▓▓    ← middle SiN, 50 nm
   ░░░░░█░░░░░█░░░░░█░░░░░█░░░░░█░░░░░█░░░░░    ← BPSG, 760 nm
   ▓▓▓▓▓█▓▓▓▓▓█▓▓▓▓▓█▓▓▓▓▓█▓▓▓▓▓█▓▓▓▓▓█▓▓▓▓▓    ← bottom SiN, 20 nm
        ■     ■     ■     ■     ■     ■          ← landing pads
        █ = TiN pillar (32 nm top, 24 nm bottom)
```

Until the field TiN is removed, the array is one capacitor plate shorted to every landing pad. Storage-node separation removes the field TiN from the top of the top support, leaving each pillar isolated, its top a few nanometres below the SiN surface.

### 1.2.2 How Little Conduction Is Too Much

A storage node holding a "1" has 0.55 V across its dielectric and up to 1.10 V of difference to a neighbour holding a "0". Its charge must last the refresh interval. The retention budget sets how much leakage current a node may suffer:

```
Stored charge:        Q = C_s · V_core = 8.6 fF × 1.10 V = 9.5 fC
Allowed loss:         about 20% of Q before the sense margin is gone → 1.9 fC
Refresh interval:     64 ms (at 85 °C; 32 ms above)
Allowed leakage:      I_max = 1.9 fC / 0.064 s ≈ 30 fA (all paths, worst cell)
```

The total of junction leakage, transistor sub-threshold leakage, and dielectric leakage must stay below about 30 fA in the weakest cells. A parasitic path between two storage nodes adds to that. The resistance it must exceed:

```
R_min = ΔV / I_budget = 1.10 V / 10 fA ≈ 1.1 × 10¹⁴ Ω   (if the path may take a third of the budget)
```

Compare this with a thread of TiN left on the SiN surface between two pillar tops:

```
TiN residue: 1 nm thick, 5 nm wide, 13 nm long (the top gap between pillars)
ρ(TiN, very thin, oxidized) ≈ 1000 µΩ·cm = 1 × 10⁻⁵ Ω·m (pessimistic)
R = ρ L / (w t) = 1×10⁻⁵ × 13×10⁻⁹ / (5×10⁻⁹ × 1×10⁻⁹) = 2.6 × 10⁴ Ω
```

The thread is ten orders of magnitude too conductive. **Any continuous conducting residue between two pillar tops is a hard short.** There is no partial credit: a residue is either broken or it is a failed pair of cells. Even a fully oxidized TiOₓ residue, with resistivity many orders higher, can supply femtoamperes through trap-assisted conduction at 1 V over a 13 nm gap. Storage-node separation is judged by the absence of residue, not by its thickness.

### 1.2.3 The Two Routes

There are two ways to remove the field TiN:

```
Route                  How it works                     Typical consequence
──────────────────────────────────────────────────────────────────────────────
CMP                    Polish TiN, stop on the top SiN  Flat pillar tops; 15–20 nm
(Book #30 reference)   support; buff                    of SiN consumed; slurry
                                                        residue; scratches
Dry etch-back          Blanket Cl-based plasma etch;    < 1 nm SiN lost; pillar tops
(this book's           no mask; endpoint when the field recessed 5–12 nm; seam can
reference)             clears; timed overetch           open at the top; Cl residue
```

Both are in production. CMP was the classic choice when the electrode was a cylinder liner protected by a sacrificial fill. Etch-back is preferred when the top support is thin, when its thickness sets pillar stiffness (Book #30, Chapter 11), or when the mold stack cannot afford CMP stress. This book uses the etch-back route as its reference and compares it with CMP throughout.

---

## 1.3 Why the Top Electrode Must Be Patterned

### 1.3.1 The Plate Stack

After the mold etch of Book #30 has freed the pillars, the capacitor is completed by three blanket depositions:

```
Plate stack (reference, deposited on the free-standing pillar forest):
  1. ZAZ high-k (ZrO₂/Al₂O₃/ZrO₂), ALD, 5.5 nm physical, EOT 0.50 nm
  2. Top electrode TiN, ALD, 5 nm on the field (closes the 6 nm gaps between
     coated pillars)
  3. Plate fill: B-doped poly-Si₀.₇Ge₀.₃, LPCVD 425 °C, 150 nm above the top
     support (fills the support openings and the space above the array)
  4. Plate strap: W, 40 nm PVD, for low sheet resistance
```

All four films cover the whole wafer: the array, the periphery, the scribe lines, and the bevel. The array needs them; nothing else does.

### 1.3.2 What the Plate Etch Must Do

The plate etch removes the stack everywhere outside the array islands:

```
Reasons to remove the plate outside the array:
  1. Periphery contacts must pass through the region later. W and SiGe would short
     them; ZrO₂ would stop their etch (ZrF₄ does not volatilize).
  2. Each bank's plate must be separate so that a plate defect in one bank can be
     isolated and so that plate voltage can be driven and monitored per block.
  3. The plate must not reach the scribe, bevel, or alignment marks.
  4. Removing the plate leaves a defined edge on which the inter-layer dielectric
     and the plate contact are built.
```

The plate etch is a masked etch with a coarse pattern: minimum features of about 1 µm, open area about 45% of the wafer. Its difficulty is not resolution but **the stack**: four materials with four different chemistries, the last of which, the high-k, is one of the hardest films in the fab to etch and one of the most important to leave undamaged beneath the plate.

### 1.3.3 Why High-k Residue Matters

The ZrO₂ left on the periphery after an incomplete plate etch does not conduct, so it does not short anything. It does something worse for yield. The periphery metal contacts, etched later through about 1.8 µm of oxide and nitride with fluorocarbon plasma, cannot pass through ZrO₂, because ZrF₄ is not volatile below several hundred degrees:

```
Volatility (illustrative):
  ZrCl₄   sublimes at 331 °C at 1 atm; usable vapor pressure in a plasma at
          60–200 °C wafer temperature with ion assistance
  ZrF₄    sublimes at ≈ 900 °C; effectively non-volatile in an oxide etch
```

A ZrO₂ island 1 nm thick, larger than a contact, under a periphery contact is an **open contact**. A die has tens of millions of periphery contacts. Chapter 12 shows that high-k residue must be cleared to below a hundredth of a monolayer, and Chapter 4 explains why that is hard.

---

## 1.4 Where the Electrode Etches Sit

### 1.4.1 The Capacitor Module

```
Capacitor module flow (reference):
   1. Mold deposition (SiN / BPSG / SiN / PE-TEOS / SiN)              (Book #29)
   2. ACL hard mask, honeycomb patterning, mask open                  (Book #29)
   3. Capacitor hole etch                                             (Books #29, #31)
   4. Strip, clean
   5. TiN bottom electrode pulsed CVD (fill, 18 nm on the field)
  ─────────────────────── this book, module 1 ───────────────────────────────
   6. Storage-node separation: TiN etch-back, post-etch treatment, clean
  ───────────────────────────────────────────────────────────────────────────
   7. Support-open mask, support-open etch                            (Book #30)
   8. Mold dip-out, rinse, dry                                        (Book #30)
   9. High-k dielectric ALD (ZAZ, 5.5 nm)
  10. Top electrode TiN ALD (5 nm)
  11. Plate fill: B-doped SiGe (150 nm above the array)
  12. Plate strap: W (40 nm)
  ─────────────────────── this book, module 2 ───────────────────────────────
  13. Plate mask: BARC + KrF resist
  14. Cell-plate etch: W → SiGe → TiN → ZAZ, landing on top SiN
  15. Strip, post-etch treatment, clean
  ───────────────────────────────────────────────────────────────────────────
  16. Inter-layer dielectric over the plate; periphery contacts; plate contact
```

The two electrode etches bracket the mold etch. Storage-node separation comes before the support open, so its result is the starting surface of Book #30. The plate etch comes after the dielectric and top electrode, so it is the first plasma the finished capacitor sees.

### 1.4.2 Geometry at the Two Etches

```
At storage-node separation:                At plate etch:
  Surface: 18 nm TiN on 122 nm SiN           Surface: 40 nm W / 150 nm SiGe /
  Topography: planar, with a fill dimple      5 nm TiN / 5.5 nm ZAZ on 120 nm
    ≈ 10 nm deep above each hole               SiN (periphery); planar at the
  Pattern: none (blanket)                      plate edge
  Exposed TiN after clearing: pillar tops,   Pattern: plate islands, ≈ 55% of
    46% of the array area at 32 nm             the wafer covered, 45% open
    top diameter                             Minimum feature ≈ 1 µm
  Below: a mold full of oxide; the pillars   Below the plate: the finished
    are still buried                           capacitors of every cell
```

### 1.4.3 The Array Edge

The array is not the whole die. In the reference, the cell array, with its dummy rows, occupies about 45% of the wafer area. At the array edge the mold continues into the periphery, where it has no holes (Book #30, Chapter 11). For the storage-node separation, the periphery is simply SiN covered by TiN that must be removed; the clearing there is the same as between pillars. For the plate etch, the plate extends **1.5 µm** beyond the last row of dummy pillars and ends on the periphery top SiN. The plate edge therefore never lies over active cells.

---

## 1.5 The Specification Sheet

```
Module 1 — storage-node separation (reference, illustrative):
  Field TiN residue on top SiN               none (no Ti above XPS detection in
                                             periphery pads; 0 node-to-node
                                             shorts per 10⁹ pairs)
  Pillar rim recess below SiN surface        5–15 nm (target 8 nm)
  Recess range within a die                  ≤ 4 nm
  Pillar-top cup (centre below rim)          ≤ 12 nm; no open seam below it
  Top SiN loss                               ≤ 2 nm (remaining 120 ± 3 nm)
  Cl on TiN surface after treatment          ≤ 1 at% (XPS)
  Particles added (> 30 nm)                  ≤ 10 per wafer

Module 2 — cell-plate etch:
  Plate edge placement                       ± 100 nm of design
  Plate edge profile                         80–88°; no footing > 20 nm
  W, SiGe, TiN residue outside the plate     none (no stringers, no islands)
  High-k residue outside the plate           Zr ≤ 1 × 10¹³ atoms/cm² (TXRF)
  Top SiN loss in periphery                  ≤ 15 nm
  TiN notch at the plate edge                ≤ 15 nm lateral
  Charging voltage across the dielectric     ≤ 1.5 V during the etch (antenna
                                             test structures)
  Cell leakage after plate etch              ≤ 10% above unetched reference at
                                             ± 1.0 V
  Plate sheet resistance                     ≤ 4 Ω/□ (W-strapped)

Electrical (end of capacitor module):
  C_s                                        ≥ 8.3 fF (mean 8.6 fF)
  Node-to-node shorts                        within repair budget (≤ 20 pairs/die)
  Plate-to-node leakage at 1.0 V             ≤ 1 fA per cell (median)
  Periphery contact opens from high-k        0 per die
```

Each line corresponds to a chapter. Two deserve emphasis now. The **residue** lines are absolute: one TiN thread is a failed pair, and one ZrO₂ island is an open contact. The **dielectric** lines measure damage to a film that the plate etch never intends to touch, under the plate, many micrometres from where the plasma acts. Chapter 13 explains how it can still be hurt.

---

## 1.6 What Makes Electrode Etch Different

1. **Thin films, absolute clearing.** The films are 5–40 nm thick (150 nm for SiGe). The etch is short; the endpoint must be sharp; and the result is judged by what is left, not by what is removed.

2. **No etch stop for the pillar.** During storage-node separation the pillar TiN is the same film as the field TiN. Once the field clears, the pillars recess at an accelerating rate (Chapter 10). The overetch buys residue margin with recess.

3. **Metal and high-k chemistries.** The etch products, TiCl₄, WF₆, SiCl₄, GeCl₄, ZrCl₄, AlCl₃, range from very volatile to barely volatile. Walls coat; chambers drift; contamination crosses from one wafer to the next (Chapter 9).

4. **The finished capacitor is under the plate etch.** Seventeen billion capacitors per die are connected to the plate being etched. Charging, ultraviolet light, and halogen penetration at the plate edge can each degrade a dielectric whose leakage specification is one femtoampere per cell.

5. **Two modules, one capacitor.** The recess left by module 1 shapes the support open of Book #30; the TiN surface left by module 1 is the interface on which the dielectric grows; the plate etch of module 2 must not undo any of it.

---

## Summary and Key Takeaways

1. **Two electrodes, two cuts.** The storage node is cut into 1.7 × 10¹⁰ isolated pillars by a blanket etch-back; the plate is cut into a few dozen islands by a masked multilayer etch.

2. **A residue is a short.** A TiN thread of 2.6 × 10⁴ Ω between pillar tops is ten orders of magnitude below the 10¹⁴ Ω needed to protect retention.

3. **Etch-back trades residue for recess.** There is no stop under the pillar; every second of overetch recesses the pillar tops.

4. **High-k residue opens periphery contacts.** ZrF₄ is not volatile; the plate etch must clear ZrO₂ to a hundredth of a monolayer.

5. **The plate etch acts on finished capacitors.** Its specification includes the dielectric it does not etch.

---

## Study Questions

1. Using the retention arithmetic of Section 1.2.2, find the minimum resistance of a node-to-node leakage path if it may take half of a 30 fA budget at 85 °C and the refresh interval is halved to 32 ms. Does the conclusion about TiN residue change?

2. A TiN residue is fully oxidized to TiO₂ with an effective resistivity of 10⁸ Ω·cm. With the dimensions of Section 1.2.2, compute its resistance. Is it a short?

3. The field TiN is 18 nm and the top hole diameter is 32 nm. What is the minimum fill thickness that closes the hole? If the hole top CD rises to 35 nm, what fill thickness is needed, and how much more field TiN must the etch-back remove?

4. The plate covers 55% of the wafer. Estimate the area of high-k removed per wafer and, from Section 1.3.3, the number of Zr atoms per square centimetre in one monolayer of ZrO₂ (density 5.68 g/cm³, molar mass 123.2 g/mol, monolayer ≈ 0.3 nm). What fraction of a monolayer is the residue specification of 1 × 10¹³ cm⁻²?

5. List three reasons the plate edge is placed over the periphery rather than over the outermost row of active cells.

6. A die has 1.7 × 10¹⁰ storage nodes and can repair 20 failed pairs from node-to-node shorts. What short probability per neighbouring pair is allowed? (Each pillar has six neighbours; count each pair once.)

---

**Next Chapter:** [Chapter 2: The Electrode Stack — Fill, Dielectric, Top Electrode & Plate](./02-electrode-stack-films.md)

---

**Chapter 1 Development Status:** Complete  
**Version:** 1.0
