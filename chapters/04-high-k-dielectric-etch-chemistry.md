# Chapter 4: Etching High-k Dielectrics — ZrO₂, Al₂O₃ & HfO₂

## Overview

The high-k dielectric is the last film the plate etch must remove from the periphery and the hardest. ZrO₂, Al₂O₃, and HfO₂ have metal–oxygen bonds as strong as or stronger than Si–O; their fluorides do not volatilize at any temperature a wafer can tolerate in a plasma chamber; their chlorides volatilize only with help. They were chosen for the capacitor because they are stable, and that stability is exactly what makes them hard to etch.

The plate etch removes 5.5 nm of crystallized ZAZ in about a minute with a BCl₃-based chemistry in which the boron takes the oxygen and the chlorine takes the metal. This chapter develops that chemistry: its thermochemistry, the balance between etching and deposition that BCl₃ plasmas walk, the effect of crystallinity, the poor selectivity to the SiN underneath, the role of temperature, the statistics of clearing a granular film to a hundredth of a monolayer, and the wet and atomic-layer alternatives.

**Learning Objectives:**
- Explain why ZrO₂, Al₂O₃, and HfO₂ do not etch in Cl₂ alone and why BCl₃ makes their chlorination favourable
- Describe the etch–deposition transition in BCl₃ plasmas and choose an ion energy above it
- Compare etch rates of amorphous and crystalline ZrO₂ and explain grain residue
- Compute the overetch needed to clear a granular film to a given residue probability
- Weigh dry, wet, hybrid, and atomic-layer removal of high-k for the plate etch

---

## 4.1 Why High-k Is Hard to Etch

### 4.1.1 Bonds

```
Metal–oxygen bond dissociation energy (diatomic, kJ/mol, illustrative):
  B–O     806        ← stronger than any metal–oxygen bond below
  Hf–O    802
  Si–O    798
  Zr–O    766
  Ti–O    672
  Al–O    512
```

The high-k metals hold their oxygen as tightly as silicon does. Boron holds it more tightly than any of them. That is the key to the chemistry of this chapter.

### 4.1.2 Volatility of the Halides

```
Temperature at which vapor pressure reaches ≈ 1 Torr (illustrative):
  AlCl₃ (as Al₂Cl₆)    ≈ 100 °C
  ZrCl₄                ≈ 190 °C
  HfCl₄                ≈ 190 °C
  TiCl₄                ≈ −14 °C (very volatile)
  ZrF₄, HfF₄           ≈ 600 °C
  AlF₃                 ≈ 1000 °C
```

The fluorides are useless: a fluorocarbon plasma that meets ZrO₂ forms a ZrF₄ skin and stops. This is why ZrO₂ is an excellent etch stop for the periphery contact etch, and why ZrO₂ residue opens contacts (Chapter 1). The chlorides are marginal: at a wafer temperature of 60 °C, ZrCl₄ and HfCl₄ have vapor pressures of order 10⁻⁵ Torr and leave only with ion assistance. AlCl₃ is more volatile and clears more easily.

---

## 4.2 Thermochemistry

### 4.2.1 Chlorine Alone

```
ZrO₂ + 2 Cl₂ → ZrCl₄(s) + O₂             ΔH ≈ −981 + 1101 = +120 kJ/mol
HfO₂ + 2 Cl₂ → HfCl₄(s) + O₂             ΔH ≈ −990 + 1145 = +155 kJ/mol
Al₂O₃ + 3 Cl₂ → 2 AlCl₃(s) + 3/2 O₂      ΔH ≈ −1408 + 1676 = +267 kJ/mol
```

All three are endothermic. In a Cl₂ plasma, energetic ions can still sputter-assist the reaction, but the rate is low and the surface stays oxygen-rich.

### 4.2.2 BCl₃ as an Oxygen Getter

```
ZrO₂ + 4/3 BCl₃ → ZrCl₄(s) + 2/3 B₂O₃     ΔH ≈ −981 − 849 + 1101 + 538 = −191 kJ/mol
HfO₂ + 4/3 BCl₃ → HfCl₄(s) + 2/3 B₂O₃     ΔH ≈ −990 − 849 + 1145 + 538 = −156 kJ/mol
Al₂O₃ + 2 BCl₃ → 2 AlCl₃(s) + B₂O₃        ΔH ≈ −1408 − 1274 + 1676 + 808 = −198 kJ/mol
```

With BCl₃, each reaction becomes exothermic. The boron oxide does not stay on the surface as B₂O₃ in the plasma: with Cl it forms volatile boron oxychlorides, chiefly (BOCl)₃, and BCl₂⁺ ions sputter what remains.

### 4.2.3 Gas-Phase Products

If the products are counted as gases (ZrCl₄(g), with about 110 kJ/mol of sublimation enthalpy), the ZrO₂ reaction is still exothermic by about 80 kJ/mol. The thermodynamic drive is modest; the surface needs ions to break the lattice and to remove the chloride. The etch is **ion-assisted chemical**, not spontaneous.

---

## 4.3 The BCl₃ Plasma

### 4.3.1 Species

```
BCl₃ plasma at 5 mTorr, 800 W ICP (illustrative):
  Ions        BCl₂⁺ (dominant), Cl⁺, Cl₂⁺, BCl⁺, Ar⁺ (with Ar)
  Radicals    Cl, BCl₂, BCl
  Deposits    BₓClᵧ films on surfaces with low ion flux or low energy
```

### 4.3.2 Etch versus Deposition

BCl₃ plasmas deposit a boron-chlorine film on any surface that ions do not clean fast enough. On an oxide surface, the film competes with the etch:

```
Net rate = Y(E) · Γ_i / n − D

  Y(E) = A (√E − √E_th)    ion-assisted removal (as in Chapter 3)
  D                        deposition rate of BₓClᵧ (nm/s)

For ZrO₂ in the reference HK chemistry (illustrative):
  E_th ≈ 60 eV;  A chosen so that the net rate is 6 nm/min at 150 eV
  D ≈ 1–2 nm/min, falls with higher Cl₂ fraction and higher temperature
```

```
Ion energy (eV)     ZrO₂ net rate (nm/min)     Surface
──────────────────────────────────────────────────────────────
  40                  −1 (deposition)          BₓClᵧ film grows
  70                   ≈ 1                     marginal; non-uniform
 100                   ≈ 3.5
 150 (reference)       6
 250                  ≈ 10                     SiN and resist loss high
```

Below about 60 eV the ZrO₂ surface gains a film instead of losing material. Near the transition, small differences in ion energy across the wafer, from the edge ring or from chamber wall drift, decide whether a region etches or not. The reference sits at 150 eV, well above the transition.

### 4.3.3 The Cl₂ Fraction

Adding Cl₂ to BCl₃ raises the Cl atom density and suppresses BₓClᵧ deposition, but it removes the boron that getters oxygen. The optimum for ZrO₂ is usually 15–30% Cl₂:

```
Reference HK step:
  BCl₃ 80 / Cl₂ 20 / Ar 50 sccm (Cl₂ fraction of halogen gas 20%)
  5 mTorr, 800 W source, 450 W bias (E ≈ 150 eV), ESC 60 °C
```

---

## 4.4 The Three Oxides

### 4.4.1 Rates in the Reference HK Step

```
Film                              Rate (nm/min)    Comment
──────────────────────────────────────────────────────────────────────────
ZrO₂, amorphous (as deposited)        9
ZrO₂, tetragonal (after SiGe)         6            ≈ 0.65× amorphous
Al₂O₃, amorphous                      5            AlCl₃ more volatile; strong
                                                   Al–O lattice energy
HfO₂, monoclinic                      5            (for comparison)
TiN (top electrode)                  50            clears in ≈ 6 s
SiN (PECVD top support)               8            the landing film
SiO₂ (PE-TEOS)                        5
KrF resist                           50
```

### 4.4.2 Clearing the ZAZ

```
Reference clearing time (centre of the wafer):
  TiN 5.0 nm at 50 nm/min        6 s
  ZrO₂ 2.6 nm at 6 nm/min        26 s
  Al₂O₃ 0.3 nm at 5 nm/min        4 s
  ZrO₂ 2.6 nm at 6 nm/min        26 s
  Total to clear (nominal)       62 s
  Overetch 50%                   31 s → total HK step ≈ 93 s

SiN loss during overetch:        31 s × 8 nm/min = 4.1 nm (nominal)
Worst site (thick ZAZ, slow rate): SiN loss ≈ 2–3 nm; best site ≈ 6–7 nm
```

### 4.4.3 Crystallinity and Grains

The tetragonal ZrO₂ grains after the SiGe anneal are 10–30 nm across, about as wide as the film is thick times five. Grain boundaries are slightly less dense and etch faster. As the etch front approaches the Al₂O₃ insertion layer and then the SiN, the remaining film becomes discontinuous: boundaries open first, leaving grain centres as islands 0.5–1.5 nm thick. The last of these clear well after the average film has gone.

---

## 4.5 Selectivity

### 4.5.1 To the Landing SiN

In BCl₃/Cl₂ at 150 eV, SiN etches faster than crystalline ZrO₂. The selectivity is **below 1**:

```
ZrO₂ : SiN ≈ 6 : 8 = 0.75
```

This is tolerable because the ZAZ is only 5.5 nm thick and the SiN is 120 nm thick. Every second of overetch costs about 0.13 nm of SiN. The SiN loss specification (≤ 15 nm) allows an overetch of more than 100 s; the reference uses 31 s. The constraint on overetch is not SiN loss but resist budget, TiN notching at the plate edge (Chapter 12), and the dielectric damage that ions and ultraviolet light may cause at the plate edge (Chapter 13).

### 4.5.2 Boron on SiN

Part of the reason SiN etches in BCl₃ is that boron does not getter nitrogen as well as it getters oxygen, but Cl and ions remove silicon readily. The surface left on the SiN carries boron and chlorine at a few atomic percent. It must be removed before the inter-layer dielectric is deposited, or it outgasses and degrades adhesion (Chapter 11).

### 4.5.3 To Resist

At 150 eV, the resist erodes at about 50 nm/min, so the 93 s HK step costs about 78 nm of resist. That is the largest single item in the resist budget of Chapter 12.

---

## 4.6 Temperature

### 4.6.1 Volatility and Rate

The chlorides of Zr and Hf become volatile with temperature. Raising the wafer temperature lowers the energy the ions must supply and raises the etch rate:

```
ZrO₂ (tetragonal) in BCl₃/Cl₂, 450 W bias (illustrative):
  Wafer T (°C)     Rate (nm/min)     E_th (eV)
  ──────────────────────────────────────────────
    60               6                 60
   150              12                 40
   250              20                 25
```

At 250 °C the etch can run at ion energies of 60–80 eV, where SiN etches slowly in BCl₃ and the selectivity ZrO₂:SiN rises above 2.

### 4.6.2 The Cost

A resist mask does not survive above about 120 °C. A hot high-k step needs an inorganic hard mask (oxide or SiN) patterned first. That adds a deposition and an etch step to the module but allows the ZAZ to be cleared with a lower ion dose. Chapter 7 describes the chambers; Chapter 12 compares the two routes.

---

## 4.7 Clearing Statistics

### 4.7.1 How Clean Is Clean

The residue specification is Zr ≤ 1 × 10¹³ atoms/cm², about 1.2% of one monolayer (Chapter 1). But the real test is the periphery contact etch: a contact fails if any ZrO₂ island larger than a few nanometres lies at its bottom. The probability of a residual grain must be low enough that the number of contacts that land on one is far below one per die.

### 4.7.2 A Simple Model

Treat the local clearing time of each grain as normally distributed around the mean clearing time t_c, with relative standard deviation σ_g from grain-to-grain differences in thickness, orientation, and boundary density. A grain is left if the step ends before its local clearing time:

```
P(grain left) = ½ erfc(z/√2),  z = OE / σ_g     (OE as a fraction of t_c)

Reference: σ_g ≈ 8% (grain level, after wafer-level variation is removed)

Contacts:
  Periphery contacts per die      ≈ 3 × 10⁷
  Contact bottom area             40 × 40 nm = 1600 nm²
  Grains under each contact       ≈ 4 (at 20 nm grain size)
  Grains under all contacts       ≈ 1.2 × 10⁸ per die

Target: < 0.01 contacts opened per die by residue
  P(grain left) < 0.01 / 1.2×10⁸ = 8 × 10⁻¹¹
  z ≥ 6.4 → OE ≥ 6.4 × 8% = 51% (on the grain distribution alone)
```

Wafer-level non-uniformity of the clearing time adds to the grain distribution. With ± 5% (3σ) across the wafer, the total overetch at the slowest site must be about 55%. The reference 50% overetch sits just below this requirement: on the grain distribution alone it gives z = 6.25, P ≈ 2 × 10⁻¹⁰, and about 0.02 residue-affected contacts per die, which meets the target only because not every affected contact is fatal (Chapter 16), and only while edge tuning keeps the slowest sites within ± 3% of the centre (Chapter 6). This is the tightest margin in the module, and it is why production plate etches often run more overetch than this model asks for.

### 4.7.3 Why Tails, Not Means

A process that leaves an average of 0.01 monolayer of Zr but clears every grain is acceptable. A process that leaves no average residue but leaves one grain in 10⁹ is not. Surface analysis measures averages (Chapter 15); contact yield measures the tail. Clearing must be designed against the tail.

---

## 4.8 Wet and Hybrid Removal

### 4.8.1 Wet Chemistries

```
Wet etch of high-k (illustrative, 25 °C):
  Film                       Dilute HF (0.5%)     Hot H₃PO₄ (160 °C)
  ──────────────────────────────────────────────────────────────────
  Al₂O₃ (amorphous)           ≈ 3 nm/min          fast
  ZrO₂ amorphous              ≈ 2 nm/min          ≈ 3 nm/min
  ZrO₂ tetragonal             ≈ 0.1–0.3 nm/min    ≈ 1 nm/min
  PECVD SiN                   ≈ 2 nm/min          ≈ 5 nm/min
  TiN                         < 0.1 nm/min        slow
  W                           < 0.1 nm/min        attacked
```

Crystalline ZrO₂ resists dilute HF. Hot phosphoric acid etches it but etches SiN faster. Neither is a good stand-alone removal for crystallized ZAZ on SiN.

### 4.8.2 Hybrid

A hybrid route ends the dry step with a thin layer of ZAZ remaining (about 1 nm), then removes it in a short wet step. The dry step then needs no overetch on SiN, and the wet step's isotropy removes the islands. The risk is lateral: the wet chemistry attacks the ZAZ edge under the TiN at the plate edge, and a wet undercut of the dielectric at the edge of a capacitor plate is a leakage path. In the reference, the plate edge lies 1.5 µm outside the last dummy row, so the undercut does not reach active cells, but it does leave a void that the inter-layer dielectric must fill.

### 4.8.3 Damage by the Etchant Is Not Damage by the Plasma

The wet route avoids the ions and ultraviolet light of an extended dry overetch. For a process limited by dielectric damage at the plate edge (Chapter 13), the hybrid is attractive; for a process limited by throughput or by void-free fill at the plate edge, it is not.

---

## 4.9 Residues

```
Residues after the HK step (illustrative):
  BₓClᵧ / BOₓClᵧ on SiN        ≈ 0.5 nm; hygroscopic; removed by O₂/H₂O
                                plasma or a water rinse
  Zr redeposition on the
  resist sidewall              sputtered ZrClₓ condenses on the resist and
                                the plate sidewall; after strip it can stand
                                as a thin "veil" along the plate edge
  Zr on the chamber wall       ZrClₓ deposits accumulate and transfer to
                                later wafers (Chapter 9)
  Cl in the SiN surface         2–5 at%
```

The veil is the high-k analogue of the classic aluminium-etch fence: a thin wall of non-volatile material that stood against the resist and is left free-standing when the resist goes. It can fall over and lie on the periphery as a ZrO₂-containing flake. Chapter 12 shows how to prevent it.

---

## 4.10 Atomic-Layer Etching

Atomic-layer etching (ALE) separates the surface modification from the removal:

```
Plasma ALE of ZrO₂ (illustrative):
  Step 1  BCl₃ adsorption (no bias), 2 s → chlorinated, borated surface
  Step 2  Ar⁺ at 50–70 eV, 3 s → removes ≈ 0.1 nm per cycle
  Self-limiting: removal per cycle constant over ≈ 20 eV of energy

Thermal ALE of ZrO₂ / HfO₂ (illustrative):
  Step 1  HF → ZrF₄ surface layer
  Step 2  ligand exchange with TMA, DMAC, or SiCl₄ → volatile products
  Temperature 250–300 °C; ≈ 0.05–0.1 nm per cycle; isotropic
```

At 0.1 nm per cycle and 5 s per cycle, clearing 5.5 nm takes about 5 minutes. ALE is too slow to remove the whole ZAZ in production, but it is attractive as a finishing step for the last nanometre, where it clears grains uniformly with almost no SiN loss and no high-energy ion dose. Chapter 14 returns to it.

---

## Summary and Key Takeaways

1. **High-k bonds are as strong as Si–O; their fluorides do not volatilize.** Only chlorides, with ion assistance, are practical at 60 °C.

2. **BCl₃ makes chlorination exothermic.** The B–O bond is stronger than any metal–oxygen bond in the stack.

3. **BCl₃ deposits below about 60 eV.** The reference etches at 150 eV, well above the etch–deposition transition.

4. **Selectivity to SiN is below 1.** It is tolerable because ZAZ is 5.5 nm and the SiN is 120 nm; the overetch is limited by resist, notching, and damage, not SiN.

5. **Clearing is a tail problem.** Grain-level statistics require about 50% overetch to keep ZrO₂ residue out of 3 × 10⁷ periphery contacts.

6. **Hot, wet, and atomic-layer options exist.** Each trades throughput, mask complexity, or lateral attack against ion dose and residue.

---

## Study Questions

1. Compute ΔH for HfO₂ + 2 Cl₂ → HfCl₄ + O₂ and HfO₂ + 4/3 BCl₃ → HfCl₄ + 2/3 B₂O₃ from the enthalpies in Section 4.2. Which bond-energy fact explains the difference?

2. The bias power drifts down so that the ion energy falls from 150 to 90 eV. Using the table in Section 4.3.2, estimate the new ZrO₂ rate and the time to clear 5.5 nm. What happens at the wafer edge if the edge ion energy is 20 eV lower than the centre?

3. Recompute the overetch needed in Section 4.7.2 if σ_g is 10% and the number of periphery contacts doubles.

4. A hot-chuck route clears ZrO₂ at 20 nm/min with SiN at 6 nm/min. Compute the HK step time with 50% overetch and the SiN loss. What extra process steps does the route need?

5. A hybrid route leaves 1.0 nm of ZrO₂ after the dry step and removes it with 0.5% HF. How long is the wet step if the remaining ZrO₂ is tetragonal? How much SiN is lost, and how far does the wet step undercut the ZAZ at the plate edge?

6. Explain why surface analysis that reports Zr at 5 × 10¹² atoms/cm² does not prove that the periphery contacts will open.

---

**Next Chapter:** [Chapter 5: Inductively Coupled Conductor Etch Chambers](./05-conductor-etch-chambers.md)

---

**Chapter 4 Development Status:** Complete  
**Version:** 1.0
