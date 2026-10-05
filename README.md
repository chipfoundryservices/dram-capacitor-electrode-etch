# Book #32: DRAM Capacitor Electrode Etch — Storage-Node Separation and Cell-Plate Patterning for TiN Pillar Capacitors

## Overview

**Book #32** is a technical reference on **DRAM capacitor electrode etch**: the two etches that turn blanket conductor films into the electrodes of the storage capacitor. A DRAM capacitor has a private electrode and a shared one. The **storage node** (bottom electrode) belongs to one cell and holds its bit. The **cell plate** (top electrode) is common to every cell of an array block and sits at a fixed voltage. Both are deposited over the whole wafer. Both must be cut, and the two cuts could hardly be more different.

**Storage-node separation** cuts an 18 nm TiN film into about seventeen billion isolated pillars per 16 Gb die. It is a blanket etch-back with no mask and no etch stop under the pillars: the plasma removes the field TiN from the top of the nitride support, and stops when nothing conducting is left between the pillar tops. A single thread of TiN 1 nm thick between two pillars has a resistance near 10⁴ Ω where 10¹⁴ Ω is needed; it is a failed pair of cells. Every second of overetch spent making sure no thread survives also recesses the pillar tops, and it does so 76% faster than the blanket rate, because the exposed TiN area has just fallen to a fifth of the wafer.

**Cell-plate patterning** cuts a four-film stack, 40 nm of tungsten, 150 nm of boron-doped silicon-germanium, 5 nm of TiN, and 5.5 nm of crystallized ZrO₂/Al₂O₃/ZrO₂ high-k, into one island per bank, landing on the top nitride of the periphery. Each film needs its own chemistry: fluorine for W, bromine for SiGe, chlorine for TiN, and boron trichloride for the high-k, whose fluorides do not volatilize. The last nanometre of ZrO₂ matters most: any grain of it left in the periphery will stop a metal contact etched through it months later. And beneath the resist, connected to the plate being etched, are the finished capacitors of every cell, with a leakage specification of one femtoampere each.

**Seventeen billion cuts with no stop, and one cut through a dielectric that must stay perfect a micrometre away.** This book covers the chemistry, equipment, process phenomena, and production engineering of both.

---

## Intended Audience

This book is written for **semiconductor industry professionals** with working knowledge of plasma processing:

- **Process Engineers**: developing TiN etch-back recipes for storage-node separation and multistep W/SiGe/TiN/high-k plate etches; controlling field residue, pillar recess, seam opening, high-k clearing, plate-edge profile, and halogen residue
- **Equipment Engineers**: specifying inductively coupled conductor etch chambers, multizone electrostatic chucks, heated-chuck high-k chambers, and endpoint systems for thin films at low and high open area; managing wall chemistry, metal cross-contamination, and particles
- **Integration Engineers**: choosing etch-back or CMP for node separation, the plate stack and its hard mask, the plate overlap at the array edge, and the treatments that protect the electrode–dielectric interface
- **Device Engineers**: understanding how node-to-node residue, pillar-top shape, chlorine at the electrode surface, plate-edge damage, and plasma charging appear as shorts, leakage, retention tails, and periphery contact opens
- **Researchers**: studying ion-assisted etching of nitrides and high-k oxides, loading and endpoint physics of thin blanket films, charging of large-area capacitor antennas, and atomic-layer etching of electrode and dielectric materials

The material assumes Books #1–5 (plasma fundamentals), Books #6–10 (dielectric etch), and Books #11–15 (advanced plasma engineering). Book #27 (*DRAM Word-Line Conductor Etch*) covers TiN and W conductor etch in the buried word line. **Book #29 (*DRAM Capacitor Hole Etch*)** cuts the holes that the storage node fills, and **Book #30 (*DRAM Capacitor Mold Etch*)** removes the mold between storage-node separation and the plate etch; this book shares their reference array. Book #31 (*DRAM High-Aspect-Ratio Capacitor Etch*) carries the capacitor to taller molds. The companion volumes *Polysilicon Etch*, *Silicon Nitride Etch*, and *Gate Oxide Etch* cover related chemistries in more general settings.

---

## Technical Scope

### Core Concepts Covered

**Architecture & Films:**
- The private storage node and the shared cell plate; retention and the leakage budget
- The TiN fill, its field overburden, the dimple over each hole, and the hole-top flare
- The ZAZ dielectric, the TiN top electrode, the B-doped SiGe plate fill, and the W strap
- The plate layout, the array-edge overlap, and the periphery landing

**Etch Chemistry:**
- TiN in chlorine: thermochemistry, breakthrough of the surface oxide, ion-assisted yield, selectivity to SiN
- Loading and the rate jump at field clearing
- SiGe in HBr/Cl₂/O₂: germanium, boron, and lateral etch; the TiN stop
- W in SF₆/N₂/Cl₂; grain-boundary roughness
- High-k in BCl₃/Cl₂: oxygen gettering, the etch–deposition transition, crystallinity, temperature, and clearing statistics

**Equipment Design:**
- Inductively coupled conductor etch chambers at low ion energy
- Multizone electrostatic chucks and etch-back uniformity
- Heated-chuck chambers and hard-mask routes for high-k
- Endpoint detection for thin films and multilayer stacks
- Wall chemistry, seasoning, metal cross-contamination, and defects

**Process Phenomena:**
- Field clearing, pillar recess, the pillar-top cup, seam opening, and node-to-node shorts
- Chlorine at the electrode surface, oxidation, corrosion, and the dielectric interface
- Plate-edge profile, notching, high-k residue, veils, and periphery landing
- Plasma charging, ultraviolet damage, and edge damage to the capacitor dielectric
- Advanced schemes: cylinder electrodes, atomic-layer etch, new electrode metals, 4F² and 3D DRAM

**Production Integration:**
- Metrology and inspection for residue, recess, high-k clearing, and the plate edge
- Electrical monitors: node combs, capacitor arrays, antenna structures, periphery contact chains
- Yield signatures, throughput, and cost of ownership; etch-back versus CMP

### Technology Context

- **Device architectures:** 6F² buried-channel DRAM from the 1x to the 1c generation (DDR5, LPDDR5X, HBM core dies); 4F² vertical-channel and 3D DRAM as emerging forms
- **Capacitor structures:** single-sided solid TiN pillar capacitors with a top and middle nitride support (primary focus); cylinder and double-sided electrodes; W-strapped SiGe plates
- **Process sequence:** Storage-node separation follows the TiN fill of the capacitor holes and precedes the support-open and mold etch of Book #30. The plate etch follows the high-k ALD, the TiN top electrode, the SiGe fill, and the W strap, and precedes the inter-layer dielectric and the periphery contacts
- **Manufacturing scale:** 300 mm wafers; one storage-node etch-back (about 1 min of plasma) and one plate etch (about 4 min of plasma) per wafer

---

## Book Organization

### Part I: Fundamentals (4 Chapters)

**Chapter 1: The Capacitor Electrodes & Why They Are Etched**
- The private storage node and the shared plate
- Why any residue between storage nodes is a short
- Why the plate must be removed from the periphery, and why high-k residue opens contacts
- Where the two electrode etches sit, and their specification sheet

**Chapter 2: The Electrode Stack — Fill, Dielectric, Top Electrode & Plate**
- The top support, the hole-top flare, and the TiN fill
- The dimple over each filled hole; the surface oxide
- ZAZ, top-electrode TiN, B-doped SiGe, and the W strap
- The plate mask and the incoming variations

**Chapter 3: Plasma Chemistry of TiN, SiGe & W Etching**
- Product volatility and thermochemistry
- Ion-enhanced yield, selectivity, and the breakthrough step
- Loading and the rate jump at field clearing
- Lateral etch of SiGe; passivation of each sidewall; halogen uptake

**Chapter 4: Etching High-k Dielectrics — ZrO₂, Al₂O₃ & HfO₂**
- Bond strengths and halide volatility
- BCl₃ as an oxygen getter; the etch–deposition transition
- Crystallinity, selectivity, temperature, and clearing statistics
- Wet, hybrid, and atomic-layer removal

### Part II: Hardware Design (5 Chapters)

**Chapter 5: Inductively Coupled Conductor Etch Chambers**
- Why ICP/TCP for electrode etch
- Source and bias at low ion energy; bias pulsing
- Gas delivery and fast step changes
- Chamber choice for module 1 and module 2

**Chapter 6: Electrostatic Chucks, Temperature & Etch-Back Uniformity**
- Multizone temperature and its effect on rate and lateral etch
- Edge rings, edge ion energy, and the wafer edge
- Clearing-time uniformity and the overetch it requires
- Wafer bow from the W strap

**Chapter 7: High-Temperature & Halide Chambers for High-k Removal**
- Heated chucks to 250 °C
- BCl₃ delivery, moisture, and boron deposits
- Hard-mask routes; split-chamber plate etch
- ALE-capable hardware

**Chapter 8: Endpoint Detection for Thin-Film & Multilayer Electrode Etch**
- Optical emission at field clearing
- Multilayer endpoint for W → SiGe → TiN → ZAZ
- Interferometry and reflectometry
- Signal-to-noise, open area, and endpoint failure modes

**Chapter 9: Chamber Walls, Seasoning, Metal Contamination & Defects**
- TiClₓ, BₓClᵧ, WOₓ, and ZrClₓ wall deposits
- Seasoning and waferless auto-clean
- Cross-contamination of Ti, W, Ge, and Zr
- Particles, flakes, and the bevel

### Part III: Process Phenomena (5 Chapters)

**Chapter 10: Node Separation — Field Clearing, Pillar Recess, Seam Opening & Shorts**
- How the field clears and where it clears last
- Recess on the pillar rim and the cup at its centre
- Anisotropy, the dimple, and the seam
- Residue mechanisms, short statistics, and etch-back versus CMP

**Chapter 11: Electrode Surface Chemistry — Chlorine, Oxidation & Corrosion**
- Cl in the TiN surface after etch-back; post-etch treatments
- What the support open and dip-out do with it
- Corrosion of TiN and W after the plate etch
- The electrode–dielectric interface and leakage

**Chapter 12: Plate Patterning — Profile, Notching, High-k Residue & Periphery Landing**
- The four-step etch and the resist budget
- Profile, footing, and the SiGe notch
- High-k clearing, grain residue, and veils
- Landing on the periphery SiN; the hard-mask route

**Chapter 13: Plasma-Induced Damage to the Capacitor Dielectric**
- The plate as an antenna
- Charging during the etch and at clearing
- Ultraviolet and halogen damage at the plate edge
- Leakage, TDDB, and test structures

**Chapter 14: Advanced Schemes — Cylinder Electrodes, ALE, New Metals, 4F² & 3D DRAM**
- Cylinder and double-sided electrodes with a sacrificial fill
- Atomic-layer etch of TiN and high-k
- Mo, Ru, and NbN electrodes; TiO₂- and SrTiO₃-class dielectrics
- Electrode separation for vertical and lateral capacitors

### Part IV: Production Scale (2 Chapters)

**Chapter 15: Metrology, Inspection & Advanced Process Control**
- Residue detection: voltage contrast, XPS, TXRF
- Recess, cup, and plate-edge metrology
- Electrical monitors
- Feed-forward and feedback control

**Chapter 16: Integration, Yield & Cost of Ownership**
- From node separation to the support open; from the plate to the periphery contacts
- Yield signatures of each electrode etch
- Throughput and cost of ownership
- Etch-back versus CMP; dry versus hybrid high-k removal

---

## Key Technical Themes

1. **Absence is the specification.** A TiN thread between pillars is a short; a ZrO₂ grain under a contact is an open. Both etches are judged by what is not there.
2. **No stop under the pillar.** Storage-node separation has a stop under the field (SiN) but none under the pillar tops. Overetch converts residue margin into recess.
3. **Loading accelerates the overetch.** When the field clears, the exposed TiN area drops to 21% of the wafer and the pillar tops etch 1.76× faster than the blanket film.
4. **The dimple becomes the pillar top.** The fill leaves a 10 nm dimple over each hole; anisotropic etch carries it down, isotropic etch drives it into the seam.
5. **Four films, four chemistries.** F for W, Br for SiGe, Cl for TiN, BCl₃ for high-k; each transition is an endpoint, and each endpoint failure is a residue.
6. **The capacitor is under the etch.** The plate etch must not charge, irradiate, or poison a 5.5 nm dielectric whose leakage is one femtoampere per cell.

---

## Cross-References to Prior Books

**Related Books in the Series:**

- **Books #1–5** (Plasma Physics & Chemistry Fundamentals): sheaths, ion energy, radical generation
- **Books #6–10** (Dielectric Etch & Fluorocarbon Chemistry): fluorocarbon chemistry relevant to the BARC open and the later periphery contacts
- **Books #11–15** (Advanced Plasma Engineering): RF delivery, chucks, endpoint, chamber matching
- **Book #27** (DRAM Word-Line Conductor Etch): TiN and W etch in the buried word line
- **Book #29** (DRAM Capacitor Hole Etch): the holes, the mold, and the reference array
- **Book #30** (DRAM Capacitor Mold Etch): the support open and dip-out between this book's two modules
- **Book #31** (DRAM High-Aspect-Ratio Capacitor Etch): taller capacitors and their electrodes
- **Companion volumes:** *Polysilicon Etch* (Si and SiGe gate etch chemistry), *Silicon Nitride Etch*, *Gate Oxide Etch* (high-k gate dielectric removal), *Aluminum Metal Etch* (fences, veils, and corrosion)

Book #29 cut the holes and Book #30 freed the pillars. This book separates the pillars before the mold comes out, and wraps them afterwards in a plate that stops where it should.

---

## File Organization

```
dram-capacitor-electrode-etch/
├── README.md            ← You are here
├── PREFACE.md
├── INDEX.md
├── GLOSSARY.md
│
├── chapters/
│   ├── 01-capacitor-electrodes-role.md
│   ├── 02-electrode-stack-films.md
│   ├── 03-tin-sige-w-plasma-chemistry.md
│   ├── 04-high-k-dielectric-etch-chemistry.md
│   ├── 05-conductor-etch-chambers.md
│   ├── 06-chuck-temperature-etchback-uniformity.md
│   ├── 07-high-k-halide-chambers.md
│   ├── 08-endpoint-thin-film-multilayer.md
│   ├── 09-chamber-walls-contamination-defects.md
│   ├── 10-node-separation-recess-shorts.md
│   ├── 11-electrode-surface-chlorine-corrosion.md
│   ├── 12-plate-patterning-profile-residue.md
│   ├── 13-plasma-induced-dielectric-damage.md
│   ├── 14-advanced-electrode-schemes.md
│   ├── 15-metrology-inspection-apc.md
│   └── 16-integration-yield-coo.md
│
└── appendices/
    ├── A-material-properties.md
    ├── B-chemistry-thermochemistry-data.md
    ├── C-standard-procedures.md
    ├── D-process-windows.md
    ├── E-etchback-loading-charging-calculations.md
    ├── F-metrology-reference.md
    └── G-troubleshooting-guide.md
```

---

## Constraints & Scope

### What This Book Covers
✅ Dry TiN etch-back for storage-node separation of single-sided TiN pillar capacitors in 6F² DRAM (primary focus), with CMP as the comparison  
✅ Multistep W/SiGe/TiN/high-k cell-plate etch landing on the periphery SiN  
✅ Etch chemistry, chambers, endpoint, and wall management for both  
✅ Residue, recess, profile, halogen, and dielectric-damage phenomena  
✅ Cylinder electrodes, atomic-layer etch, new electrode materials, 4F² and 3D DRAM  
✅ Metrology, electrical monitors, yield, and cost of ownership  

### What This Book Does NOT Cover
❌ The capacitor hole etch (see Books #29 and #31) or the mold etch (see Book #30)  
❌ TiN, high-k, SiGe, and W deposition chemistry in detail  
❌ CMP consumables and polishing mechanics, except as comparison  
❌ The periphery contact etch itself, except as the customer of high-k clearing  
❌ Vendor-specific recipes or proprietary tool parameters  

### A Note on Numbers
Numbers in this book come from established thermochemistry and plasma–surface models, published etch-rate data and literature trends, and representative production practice. Worked examples use **illustrative values** chosen to show the method, and the arithmetic is written out so readers can substitute their own data. A single **reference process** is used across chapters so that examples connect. It inherits the array of Books #29 and #30: a 1b-class 6F² cell (F = 17 nm, cell area 1734 nm²) on a 45 nm hexagonal storage-node pitch, a 1.60 µm mold, and solid TiN pillars 32/28/24 nm wide (top/average/bottom) that give C_s = 8.6 fF. **Module 1** removes an 18 nm pulsed-CVD TiN field film from a 122 nm top SiN support by a Cl₂/BCl₃/Ar ICP etch-back (breakthrough 5 s, main etch to endpoint at 42 nm/min, overetch 10 s at 50 eV), leaving pillar rims recessed 8 nm and SiN at 120 nm. **Module 2** etches a plate of 40 nm W, 150 nm B-doped Si₀.₇Ge₀.₃, 5 nm TiN, and 5.5 nm ZAZ (EOT 0.50 nm) under 500 nm KrF resist, in four steps (SF₆/N₂/Cl₂; HBr/Cl₂/O₂ then HBr/O₂; BCl₃/Cl₂ at 150 eV with 50% overetch), landing on the periphery top SiN with 4 nm loss. The plate covers 55% of the wafer in 32 islands per die. Treat recipe values as starting points for a design of experiments, never as qualified process conditions.

---

## Development Status

**Book #32 Foundation:** Complete  
**Part I (Chapters 1–4):** Complete  
**Part II (Chapters 5–9):** Complete  
**Part III (Chapters 10–14):** Complete  
**Part IV (Chapters 15–16):** In progress  
**Back Matter (Appendices A–G, Glossary):** Planned  

---

## Next Steps

1. **Read [PREFACE.md](./PREFACE.md)** for the motivation and reading guidance
2. **Read [INDEX.md](./INDEX.md)** for the detailed chapter outline and reading paths by role
3. **Begin [Chapter 1](./chapters/01-capacitor-electrodes-role.md)**: The Capacitor Electrodes & Why They Are Etched

---

**Book #32 Version:** 1.0  
**Last Updated:** 2026-10-05  
**Series:** ChipFoundryServices Technical Series
