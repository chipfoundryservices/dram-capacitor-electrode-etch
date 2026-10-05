# Chapter 16: Integration, Yield & Cost of Ownership

## Overview

Each electrode etch hands its wafer to a module that depends on what it left. Storage-node separation hands Book #30 a set of recessed, cupped, chlorinated pillar tops in a 120 nm nitride support, and the support open and dip-out inherit every nanometre of that shape. The plate etch hands the back-end a plate edge, a periphery SiN surface, and a periphery cleared, or not quite cleared, of ZrO₂; the inter-layer dielectric, the plate contact, and thirty million periphery contacts per die inherit it.

This chapter follows those hand-offs, translates the defects of each module into the yield signatures they produce at wafer sort, sizes the equipment for a production fab, builds a cost-of-ownership model for both modules and their alternatives, and compares the cost of robustness with the value of the yield it protects.

**Learning Objectives:**
- Describe what storage-node separation hands to the support open and dip-out
- Describe what the plate etch hands to the ILD, the plate contact, and the periphery contacts
- Identify the bit-map and die-level yield signatures of each electrode-etch defect
- Size module 1 and module 2 equipment for a given wafer-start rate
- Build cost-of-ownership models for etch-back, CMP, and plate-etch routes
- Compare the cost of a longer high-k overetch with the value of the yield it protects

---

## 16.1 From Node Separation to the Mold Etch

```
What module 1 hands to Book #30 (reference):
  Item                    Value                        Consequence in Book #30
  ─────────────────────────────────────────────────────────────────────────────────
  Top SiN                 120 ± 3 nm                   first film of the support
                                                       open; top tie stiffness
  Pillar rim              7–10 nm below SiN surface    support-open crescents start
                                                       recessed: less TiN top loss
                                                       early in the etch
  Pillar-top cup          ≈ 10 nm                      filled by the support-open
                                                       ACL; no effect on the etch
  Seam groove             3–11 nm                      HF and fluorocarbon entry;
                                                       outgassing at dielectric ALD
                                                       (Book #30, Ch. 13)
  Surface Cl              ≤ 1 at% after PET            mostly overwritten by
                                                       support open and dip-out
  Residue                 0 per 10⁹ pairs (target)     a residue thread under the
                                                       support-open mask survives
                                                       the whole mold etch
```

The last line deserves attention. Book #30's support open and dip-out do not remove TiN: a residue thread on the SiN surface between two pillar tops survives the support open (where it is covered by the ACL mask) and the HF dip-out (which does not etch TiN), and ends up under the dielectric as a permanent short. Storage-node separation is the last chance to clear it.

---

## 16.2 From the Plate Etch to the Back-End

### 16.2.1 The ILD Over the Plate

The plate leaves a step about 200 nm high (W + SiGe + TiN + ZAZ) at its perimeter. The ILD, typically a high-density-plasma or flowable oxide followed by a CMP, must fill it without voids. A tapered plate edge (80–88°) fills cleanly; a re-entrant edge or a deep TiN notch leaves a keyhole that a later periphery contact may intersect.

### 16.2.2 The Plate Contact

The plate contact lands on the W strap through the ILD. W that corroded after the plate etch (Chapter 11) raises contact resistance; W thinned by resist pinholes in the HK step raises plate resistance. Both are detected as plate-voltage-margin failures rather than as single-cell failures.

### 16.2.3 The Periphery Contacts

```
Periphery contact etch (later module, for reference):
  Depth            ILD over the periphery + top SiN (≈ 115 nm) + periphery
                   mold (≈ 1.5 µm) + lower ILD → ≈ 1.8–2.0 µm
  Chemistry        C₄F₆/O₂/Ar; ZrO₂ is an etch stop for it
  Count            ≈ 3 × 10⁷ per die
  Failure from     ZrO₂ residue → open; W/SiGe residue → contact-to-contact
  the plate etch   short or a contact landing on a floating conductor
```

---

## 16.3 Yield Signatures

### 16.3.1 Signatures

```
Defect                     Bit-map / test signature                     Repairable?
──────────────────────────────────────────────────────────────────────────────────────
Node-to-node short         adjacent-cell pairs failing with opposite    yes (pairs)
(TiN residue, saddle,      data in the two cells; random, or rings at
pit)                       the wafer edge (saddles, ring wear)
Particle cluster short     compact cluster of 5–100 cells; random       partly (≤ ≈ 20)
Rim-corner leakage         retention tail uniformly worse; no spatial   no (population
                           pattern within the die                        shift)
Charging (phase A)         retention tail worse in a radial ring        no
Charging (phase B)         retention tail worse in specific banks       no (bank)
Cl at pillar tops /        retention tail; lot-correlated with queue    no
seam outgassing            time
Periphery contact open     die-level functional fail; column or row     mostly no
(ZrO₂ residue)             decoder or sense-amp group dead
W/SiGe residue in the      contact-to-contact short; functional fail    no
periphery
Plate resistance high      plate-bounce margin failures at speed;       no
(W corrosion)              data-pattern dependent
```

### 16.3.2 Which Defects Are Most Expensive

The node shorts that dominate the defect count of module 1 are mostly repairable. The periphery opens that come from module 2 are rare but **not** repairable: one open contact in a sense-amplifier strip or a decoder can disable a whole array block or the die. The cost per occurrence is therefore far higher for high-k residue than for TiN residue.

```
Yield model for periphery opens (illustrative):
  Y_periphery = exp(−N_contacts × P_open)
  N_contacts = 3 × 10⁷ per die
  Reference P_open ≈ 4 grains × 2 × 10⁻¹⁰ = 8 × 10⁻¹⁰ per contact
  (Chapter 4 grain model at 50% overetch, z = 6.25)
  → expected opens per die ≈ 0.024 → Y ≈ 97.6%

Edge dies with a worn ring (P_open 10× higher):
  expected opens ≈ 0.24 → Y ≈ 79% on those dies
```

Not every open is fatal; some fall in redundant or non-critical structures. The model overstates the loss by a factor of perhaps 2–5, but its shape, a steep edge loss from a small change in the HK overetch margin, is what yield engineers see.

---

## 16.4 Equipment Sizing

```
Fab assumption: 100,000 wafer starts per month at this layer
  Wafer rate = 100,000 / (30 × 24) ≈ 139 wafers/h
  Equipment availability ≈ 85%

Module 1 (SNS etch-back):
  Mainframe: 3 SNS chambers + 1 PET chamber ≈ 100 wafers/h (Chapter 5)
  Mainframes = 139 / (100 × 0.85) = 1.6 → 2

Module 2 (plate etch):
  Mainframe: 4 plate chambers + 2 strip/PET ≈ 50 wafers/h
  Mainframes = 139 / (50 × 0.85) = 3.3 → 4

CMP alternative to module 1 (for comparison):
  Polisher with integrated clean ≈ 60 wafers/h
  Tools = 139 / (60 × 0.85) = 2.7 → 3
```

---

## 16.5 Cost of Ownership

### 16.5.1 Module 1

```
SNS etch-back, per wafer (illustrative, full loading):
  Depreciation   mainframe $10 M over 5 years, 100 wph × 8760 h × 0.85
                 = 7.4 × 10⁵ wafers/yr → $2.0 M/yr ÷ 7.4 × 10⁵   $2.70
  Consumables    edge rings, liners, windows                       $0.40
  Gases, power   Cl₂, BCl₃, Ar, H₂/N₂; RF and chiller             $0.30
  Maintenance    PM labour and parts                               $0.30
  Metrology      OCD, VC, particle (allocated)                     $0.50
  Total                                                            ≈ $4.20

CMP alternative, per wafer:
  Depreciation   $6 M over 5 years, 60 wph → 4.5 × 10⁵ wafers/yr   $2.70
  Slurry, pads, conditioner disks                                   $3.50
  Post-CMP clean chemicals                                          $0.80
  Maintenance                                                       $0.40
  Metrology                                                         $0.50
  Total                                                            ≈ $7.90
```

The etch-back costs about half as much as CMP per wafer. It also leaves 15–20 nm more top SiN, which in some designs allows the top support to be deposited thinner, saving deposition cost and mold height. CMP's advantages, planarity, removal of saddle and pit TiN, are paid for in consumables.

### 16.5.2 Module 2

```
Plate etch, per wafer (illustrative, resist route, full loading):
  Depreciation   mainframe $14 M over 5 years, 50 wph × 8760 × 0.85
                 = 3.7 × 10⁵ wafers/yr → $2.8 M/yr ÷ 3.7 × 10⁵    $7.50
  Consumables    rings, liners, HK-coated parts                    $1.20
  Gases, power   BCl₃, HBr, SF₆, Cl₂; RF                            $0.60
  Maintenance    including chlorine-first wet cleans               $0.60
  Metrology      CD-SEM, OCD, ellipsometry, TXRF (allocated)       $0.80
  Total etch                                                       ≈ $10.70
  Plate lithography (KrF layer, for reference)                     ≈ $8
  Module total                                                     ≈ $19
```

### 16.5.3 Alternatives

```
Route                          Δ cost per wafer     Main benefit
─────────────────────────────────────────────────────────────────────────────
Hot HK with oxide hard mask    + $2 to + $3         HK step 93 → 40 s; SiN loss
(HM dep, HM open, hot chamber;                      4 → 1 nm; no veils; smaller
faster HK step offsets part)                        residue tail
Hybrid wet finish              + $1.5               no ions at the end; isotropic
                                                    grain removal
ALE finish (+ 45 s)            + $2                 most uniform clearing; least
                                                    SiN loss
HK overetch 50% → 60%          + $0.3               residue tail × 10⁻³ to 10⁻⁴
(+ 9 s, ≈ 4% throughput)
```

---

## 16.6 The Value of Yield

```
Wafer value (illustrative):
  860 good-die candidates × $3.0 per 16 Gb die ≈ $2,600 per wafer
  1% die yield ≈ $26 per wafer
```

Every cost item in Section 16.5 is small against a percent of yield. The arithmetic favours robustness wherever robustness is cheap:

```
HK overetch from 50% to 60%:
  Cost       ≈ $0.3 per wafer (throughput)
  Grain-tail z = OE/σ_g:  6.25 → 7.5
  P(grain left): 2 × 10⁻¹⁰ → 3 × 10⁻¹⁴ (normal-tail model)
  Opens per die: ≈ 0.024 → ≈ 4 × 10⁻⁶
  Yield protected ≈ 2.4% by the model, ≈ 0.5–1% after correcting for the
  fraction of opens that are fatal (more at the wafer edge)
  ≈ $13–26 per wafer
  Costs not in dollars: + 1.2 nm SiN, + 0.5 nm TiN notch, + 9 s of phase-C
  plasma (minor charging), − 8 nm resist (still ≥ 270 nm left)
```

The trade is overwhelmingly favourable, and it explains why production plate etches often run more overetch than the clearing model alone would require. The limits are the non-monetary costs: resist budget, TiN notch, SiN loss, and the plate-edge exposure, each of which has a ceiling. The same logic does not apply to the storage-node overetch, where extra time buys little against the non-Gaussian residue mechanisms (Chapter 10) and costs recess directly.

---

## 16.7 Decisions

```
Decision                       Choose                       When
──────────────────────────────────────────────────────────────────────────────
Node separation route          dry etch-back                top-support thickness is
                                                            a mechanical design
                                                            variable; cost; SiN budget
                               CMP (or CMP touch + etch-    hole-top wall saddles and
                               back)                        SiN pits dominate shorts
High-k removal                 ambient dry, resist          default; lowest complexity
                               hot dry, oxide HM            residue tail or veils limit
                                                            yield; SiN budget tight
                               hybrid wet                   damage at plate edge limits;
                                                            overlap large
                               ALE finish                   most demanding clearing;
                                                            capacity available
Plate overlap                  ≥ 1.0–1.5 µm                 always, unless area forces
                                                            less; then audit UV,
                                                            halogens, wet undercut
```

### 16.7.1 New-Product Checklist

```
For a new array or plate stack, re-derive:
  □ Fill dimple depth from fill thickness and top CD (Ch. 2, 10)
  □ Wall width and wall-saddle depth → minimum rim recess (Ch. 2, 10)
  □ Pillar-top fraction and loading jump → overetch recess (Ch. 3, 10)
  □ Rim radius and its field enhancement (Ch. 11)
  □ Plate stack clearing times, resist budget, endpoints (Ch. 8, 12)
  □ High-k chemistry and residue tail; contact count per die (Ch. 4, 12)
  □ Antenna ratio and leakage clamp; separation phase (Ch. 13)
  □ Plate overlap vs UV, halogen, wet penetration (Ch. 13)
  □ Queue times (Ch. 11)
  □ Test structures: combs, chains, antenna arrays, polarity pairs (Ch. 13, 15)
```

---

## Summary and Key Takeaways

1. **Module 1 is the last chance to clear TiN.** Book #30 removes no TiN; a thread left on the wall tops becomes a permanent short.

2. **Module 2's worst defect is the rarest.** A ZrO₂ grain under a periphery contact can kill a die; node shorts are mostly repairable.

3. **Equipment: 2 SNS mainframes and 4 plate mainframes per 100k wafers/month.** The plate etch is the capacity driver.

4. **Etch-back costs about $4 per wafer, CMP about $8.** The plate etch costs about $11, plus $8 of lithography.

5. **A percent of yield is worth about $26 per wafer.** Extra HK overetch at $0.3 per wafer is overwhelmingly worth it, up to the non-monetary limits.

6. **The same logic fails for the SNS overetch.** Its residue tail is not Gaussian, and its cost is recess.

---

## Study Questions

1. A residue thread of TiN is left between two pillar tops. Trace it through the support open, the mask strip, the HF dip-out, the dielectric ALD, and the plate deposition. At which step, if any, could it be removed?

2. Using the yield model of Section 16.3.2, compute the die yield for P_open = 1 × 10⁻⁹ per contact and 3 × 10⁷ contacts per die. What wafer value does the loss represent?

3. The fab expands to 150,000 wafer starts per month. How many SNS and plate mainframes are needed? If the hot HK route raises plate mainframe throughput from 50 to 65 wafers/h, how many plate mainframes does it save?

4. Recompute the CMP cost per wafer if slurry and pad costs fall by 30%. Is etch-back still cheaper?

5. Extend the value-of-yield calculation in Section 16.6 to an HK overetch of 70%. What new costs appear, and at what overetch does one of them reach its specification limit?

6. A product team proposes reducing the plate overlap from 1.5 µm to 0.4 µm to save die area. Write the list of checks from this book they must complete before the change is approved.

---

**Back to:** [README](../README.md) | [INDEX](../INDEX.md)

---

**Chapter 16 Development Status:** Complete  
**Version:** 1.0
