# Preface: Cutting the Plates of Seventeen Billion Capacitors

## Why This Book Exists

The DRAM capacitor is usually described by its hole: how deep, how narrow, how straight. Books #29 and #31 of this series are about that hole, and Book #30 is about the mold around it. But a hole is not a capacitor. A capacitor is two conductors and an insulator, and the conductors have to come from somewhere. They come from films that are deposited over the whole wafer, indiscriminately, and then cut.

The cuts are easy to describe. The bottom electrode is a TiN film that fills every hole and covers everything else; the part that covers everything else must go. The top electrode is a stack of TiN, silicon-germanium, and tungsten on a high-k dielectric that wraps every pillar and covers everything else; the part over the periphery must go. Neither etch has a demanding pattern. The first has no pattern at all. The second has features a micrometre wide.

Yet both are among the most yield-sensitive etches in the DRAM flow, for reasons that have nothing to do with resolution:

1. **The bottom-electrode etch has nothing to stop on.** The plasma removes the field TiN and must stop when it reaches the top nitride. But the pillars are made of the same TiN, and they go on etching. There is no stop under them, only time. Every second of overetch recesses the tops of seventeen billion pillars.

2. **The bottom-electrode etch must leave nothing.** A thread of TiN 1 nm thick between two pillar tops is a short of about 10⁴ Ω where 10¹⁴ Ω is needed. There is no such thing as a small residue.

3. **The overetch speeds up.** When the field clears, the exposed TiN area falls from the whole wafer to the pillar tops, a fifth of it. The chlorine that the field had been consuming is now available to the pillars, which etch 76% faster than the blanket film did.

4. **The plate etch has four films and four chemistries.** Fluorine for tungsten, bromine for silicon-germanium, chlorine for titanium nitride, and boron trichloride for the high-k. Each transition is an endpoint; each missed endpoint is a residue.

5. **The last film is the hardest.** Crystallized ZrO₂ has bonds as strong as silicon dioxide and fluorides that do not volatilize below 600 °C. The plate etch must clear it so completely that none of thirty million periphery contacts per die lands on a remaining grain.

6. **The finished capacitor is under the plate etch.** All seventeen billion capacitors of a die are wired to the plate being etched. The plasma can charge it, irradiate its edges, and drive chlorine into its dielectric. The leakage specification is one femtoampere per cell.

This book treats electrode etch as **an etch defined by what it must not leave and what it must not touch**, governed by clearing statistics, loading, and the electrical tolerances of the cell, and not as a routine blanket or coarse-pattern conductor etch.

---

## Unique Aspects of DRAM Capacitor Electrode Etch

### 1. Two Modules That Bracket the Mold Etch

Storage-node separation happens while the pillars are still buried in the mold, before Book #30's support open and dip-out. The plate etch happens after the dielectric and plate deposition, when the capacitor is finished. The first shapes the surface the mold etch starts from; the second is the first plasma the finished capacitor sees.

### 2. A Blanket Etch Judged by Its Tail

A blanket etch-back with a 50% overetch removes the average film many times over. It fails only at the sites that clear last: a thick spot, a particle, a TiO₂ island, a wall saddle. The specification is set by the one site in a billion, not by the mean.

### 3. Geometry Inherited From the Fill

The TiN fill leaves a dimple about 10 nm deep over every hole, ending at the seam. The etch-back cannot remove it; it can only carry it down, or, if the etch is too isotropic, drive it into the seam. The shape of every pillar top is decided by the fill thickness and the anisotropy of the etch.

### 4. High-k Clearing as a Contact Yield Problem

High-k residue does not short anything. It is found months later, when a periphery contact etched through 1.8 µm of oxide stops dead on a grain of ZrO₂. The plate etch is the module that owns that yield loss.

### 5. Damage Without Exposure

The capacitors under the plate are covered by resist, 150 nm of SiGe, and 40 nm of W. They are still in the circuit: the plate is an antenna that connects every one of them to the plasma at the plate edge. Charging, ultraviolet light, and halogens reach the dielectric through the conductor and the edge, not through the resist.

---

## How to Read This Book

### For Process Engineers
Read Chapters 1–4 for the films and chemistry, then Chapters 10–12 for node separation and plate patterning. Use Appendix D for windows and Appendix G for excursions.

### For Equipment Engineers
Read Chapter 1, then Chapters 5–9 for chambers, chucks, high-k hardware, endpoint, and wall management. Chapter 15 covers the metrology that judges your tools.

### For Integration Engineers
Read Chapters 1–2, then Chapters 10, 12, 14, and 16. The etch-back-versus-CMP comparison and the cost model in Chapter 16 are written for you.

### For Device Engineers
Read Chapter 1, Chapter 11 for the electrode interface, Chapter 13 for dielectric damage, and Chapter 16 for yield signatures.

### For Researchers
Read Chapters 3, 4, 10, 13, and 14. The loading model of Chapter 3, the clearing statistics of Chapter 4, and the antenna model of Chapter 13 are deliberately simple and invite refinement.

---

## A Note on the Reference Process

A single reference process runs through every chapter so that numbers connect. It inherits the array of Books #29 and #30: a 1b-class 6F² cell on a 45 nm hexagonal storage-node pitch, a 1.60 µm mold, and solid TiN pillars 32/28/24 nm wide. In module 1, an 18 nm TiN field film on a 122 nm top SiN support is removed by a Cl₂/BCl₃/Ar ICP etch-back with a breakthrough, a main etch to endpoint, and a 10 s overetch at 50 eV. In module 2, a plate of W (40 nm), B-doped Si₀.₇Ge₀.₃ (150 nm), TiN (5 nm), and ZAZ (5.5 nm, EOT 0.50 nm) is etched under 500 nm of KrF resist in four chemistries, landing on the periphery SiN. All values are illustrative; the arithmetic is shown so that readers can replace them with their own.

---

## Acknowledgments

This book draws on decades of published work in conductor etching, the plasma chemistry of transition-metal nitrides and high-k oxides, plasma-induced damage, and atomic-layer etching, and on the shared experience of the engineers who have kept DRAM storage nodes separate and cell plates clean through every node.

---

**Preface Version:** 1.0  
**Last Updated:** 2026-10-05
