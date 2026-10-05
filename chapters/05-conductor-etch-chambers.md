# Chapter 5: Inductively Coupled Conductor Etch Chambers

## Overview

Both electrode etches run in inductively coupled conductor etch chambers, the same family of tools that etches gates, word lines, and metal lines. The reasons are the same in both modules: the films are metals and semiconductors that etch in halogens with ion assistance; the ion energies needed are low (50–150 eV); the ion fluxes needed are high; and the chemistry must switch quickly between steps. An inductively coupled plasma (ICP, or a transformer-coupled plasma, TCP) sets the plasma density with one generator and the ion energy with another, which is exactly the independence these etches need.

This chapter describes why the ICP is chosen, how its source and bias set the ion flux and energy of each step, how the bias is controlled at the low powers the overetch uses, how gas is delivered and switched for a five-step plate recipe, what the chamber is made of, and how chambers are assigned and matched across a fleet.

**Learning Objectives:**
- Justify an ICP conductor chamber for storage-node separation and plate etch
- Compute the ion flux from the plasma density and the ion energy from the bias power
- Explain the difficulty of controlling ion energy at 50 eV and the methods used
- Describe gas delivery and step transitions for a multichemistry recipe
- Choose chamber materials compatible with Cl, Br, F, and BCl₃
- Estimate throughput and set matching criteria for a fleet

---

## 5.1 Requirements

```
Module 1 — storage-node separation (reference):
  Films           TiN 18 nm (blanket) on SiN
  Ion energy      110 eV (BT), 70 eV (ME), 50 eV (OE)
  Rate            42 nm/min (ME, blanket), ± 2% (1σ) across the wafer
  Endpoint        sharp field-clearing signal, ±1 s
  Plasma time     ≈ 40 s per wafer
  Throughput      ≥ 30 wafers/h per chamber

Module 2 — cell-plate etch (reference):
  Films           W 40 / SiGe 150 / TiN 5 / ZAZ 5.5 nm under KrF resist
  Chemistries     CF₄/O₂ (BARC), SF₆/N₂/Cl₂ (W), HBr/Cl₂/O₂ (SiGe),
                  HBr/O₂ (SiGe OE), BCl₃/Cl₂ (TiN + high-k)
  Ion energy      55–150 eV
  Profile         80–88°; notch ≤ 15 nm
  Plasma time     ≈ 3.6 min per wafer
  Throughput      ≥ 12 wafers/h per chamber
```

---

## 5.2 Choosing the Plasma Source

```
Option                    Strength                           Weakness
──────────────────────────────────────────────────────────────────────────────
ICP / TCP with RF bias    Independent density (source) and   Window erosion and
(reference)               energy (bias); high density at     deposition; centre–edge
                          5–15 mTorr; low energy possible    density shape
CCP (dual frequency)      Uniform; dielectric-etch          Ion energy coupled to
                          platform                           density; hard to stay
                                                             below 100 eV at useful
                                                             flux
Microwave / ECR           Very high density, low Te          Uniformity at 300 mm;
                                                             fewer production tools
Remote / downstream       No ions: isotropic                 Not anisotropic; used
                                                             for strip and treatment
```

The decisive argument is ion energy at high flux. To etch TiN at 42 nm/min, the main etch needs about 2 × 10¹⁶ ions cm⁻² s⁻¹ (Chapter 3). A capacitively coupled plasma that produced that flux would develop a sheath of several hundred volts. An ICP produces it with a source coil and lets the bias set the energy independently, down to a few tens of volts.

---

## 5.3 Ion Flux and Ion Energy

### 5.3.1 Ion Flux From the Source

The ion flux to the wafer is set by the plasma density at the sheath edge and the Bohm velocity:

```
Γ_i = 0.61 n_e u_B,   u_B = √(kT_e / M_i)

Reference main etch (Cl₂/BCl₃/Ar, 6 mTorr, 500 W source):
  n_e ≈ 1.5 × 10¹¹ cm⁻³,  T_e ≈ 3.5 eV,  dominant ion Cl₂⁺ (M = 71 amu)
  u_B = √(3.5 × 1.6×10⁻¹⁹ / (71 × 1.66×10⁻²⁷)) = 2.2 × 10³ m/s
  Γ_i = 0.61 × 1.5×10¹¹ × 2.2×10⁵ cm/s = 2.0 × 10¹⁶ cm⁻² s⁻¹
  Ion current density J_i = eΓ_i = 3.2 mA/cm²
  Total ion current to a 300 mm wafer: 3.2 mA/cm² × 707 cm² = 2.3 A
```

### 5.3.2 Ion Energy From the Bias

Almost all the bias power goes into accelerating ions across the wafer sheath:

```
P_bias ≈ I_i · V_s     →     V_s ≈ P_bias / I_i
E_i ≈ e (V_p + V_s)          (V_p ≈ 15 V, the plasma potential)

Reference settings:
  Step       Source    I_i (A)    Bias (W)    V_s (V)    E_i (eV)
  ──────────────────────────────────────────────────────────────────
  SNS BT      500 W     2.3        200         87         ≈ 100–110
  SNS ME      500 W     2.3        120         52         ≈ 70
  SNS OE      450 W     2.0         70         35         ≈ 50
  W           600 W     2.7        180         67         ≈ 85
  SiGe ME     600 W     2.7        250         93         ≈ 110
  SiGe OE     500 W     2.2         90         41         ≈ 55
  HK          800 W     3.4        450        132         ≈ 150
```

Two points follow. First, the bias power that sets 50 eV is only 70 W on a 300 mm wafer, a small fraction of the generator's range. Second, the ion energy depends on the ion current: if the source density drifts up 10%, a fixed bias power gives 10% lower sheath voltage. Fixed-power bias control is therefore ion-energy drift in disguise. The reference controls the bias by **measured peak-to-peak voltage** at the electrode for the low-energy steps.

### 5.3.3 The Ion Energy Distribution

At 13.56 MHz with a 35–50 V sheath, ions cross the sheath in a few RF cycles at most. The ion energy distribution is bimodal, with peaks separated by a large fraction of the mean energy:

```
IEDF width at 13.56 MHz (illustrative):
  Mean E_i 50 eV:  peaks near 30 and 70 eV (ΔE ≈ 40 eV)
  Mean E_i 150 eV: peaks near 110 and 190 eV (ΔE ≈ 80 eV)
```

For the overetch, the high-energy peak matters: it is the part of the distribution that etches SiN (threshold ≈ 40 eV in Cl₂). A narrower IEDF at the same mean raises the TiN:SiN selectivity further. Two methods narrow it: a higher bias frequency (27–60 MHz, at the cost of uniformity on large wafers), or a **tailored-waveform bias** that holds the sheath voltage nearly constant over the cycle. Several production platforms offer the latter for low-energy conductor steps.

---

## 5.4 Pulsing

### 5.4.1 Source Pulsing

Pulsing the source at 1–10 kHz lowers the time-averaged electron temperature, because T_e collapses in each off-phase and the plasma restarts at lower T_e. Consequences:

```
Effect of source pulsing (50% duty, 2 kHz; illustrative):
  Ion flux (time-averaged)        −45%
  Cl dissociation                 −30%
  VUV emission (Chapter 13)       −50% or more
  Charging (Chapter 13)           reduced; electrons reach surfaces in the off-phase
  Spontaneous lateral etch        reduced (lower Cl atom density)
```

### 5.4.2 Synchronized Bias Pulsing

With the bias pulsed in phase with the source, ions arrive only during the on-phase, at the set energy; during the off-phase, neutrals adsorb and the surface re-chlorinates. This brings the etch closer to a quasi-atomic-layer regime: rate falls, but selectivity, uniformity, and damage improve. The reference uses continuous-wave plasma for module 1 (throughput, endpoint simplicity) and synchronized pulsing for the HK step of module 2 (Chapter 13).

---

## 5.5 Gas Delivery and Step Transitions

### 5.5.1 Gas Box

The plate chamber needs F-, Br-, Cl-, and B-containing gases in one box:

```
Plate chamber gas lines (reference):
  SF₆, CF₄, NF₃ (clean), Cl₂, HBr, BCl₃, O₂, N₂, Ar, He
  HBr and BCl₃ lines heated (≈ 50 °C) to prevent condensation of
  impurities and hydrolysis products
  Moisture in BCl₃ < 1 ppm (BCl₃ + H₂O → B(OH)₃ + HCl; particles)
```

### 5.5.2 Residence Time and Transitions

```
Chamber residence time:
  τ = p V / Q
  V ≈ 40 L, p = 8 mTorr, Q = 200 sccm = 2.5 Torr·L/s
  τ = 0.008 × 40 / 2.5 = 0.13 s
```

The chamber volume exchanges in a fraction of a second. The transition time between steps is set instead by the gas lines, the mass-flow controllers' settling, the pressure servo, and the matching networks: about 2–3 s per step. During each transition, the reference holds the source on at reduced power and the bias off, so that no uncontrolled etch occurs while the chemistry is mixed.

### 5.5.3 Wall Memory

The chamber wall stores halogens. After an SF₆ step, fluorine released from the wall during the next HBr/Cl₂ step raises the spontaneous etch of SiGe. After a BCl₃ step, boron deposits on the wall consume F in the next wafer's W step. These are wafer-to-wafer and step-to-step memories; Chapter 9 treats them.

---

## 5.6 Centre–Edge Control

### 5.6.1 Source Coil

ICP density is naturally peaked or ring-shaped depending on the coil and the pressure. Production chambers use two or more coil zones, or a coil with adjustable current split, to flatten the ion flux:

```
Reference SNS chamber:
  Two-zone coil, inner:outer current ratio adjustable 0.6–1.4
  Ion flux uniformity ± 2% (1σ) to 147 mm radius
  TiN ME rate uniformity ± 2% (1σ)
```

### 5.6.2 Gas Injection

Centre and side gas injection, with independent splits, tune the radical distribution. For a loading-dominated etch such as storage-node separation, the radical supply matters as much as the ion flux: if the centre is starved of Cl, the centre clears last.

### 5.6.3 The Edge

The wafer edge sees the edge ring, the plasma boundary, and a different gas flow. Chapter 6 covers the edge in detail.

---

## 5.7 Chamber Materials

```
Material            Exposure                    Behaviour
───────────────────────────────────────────────────────────────────────────
Y₂O₃ coating        Cl, Br, F, BCl₃             resistant; forms YOF/YF₃ skin
(walls, liner)                                  under F; low particle when dense
                                                (aerosol- or PVD-deposited)
Al₂O₃ (ceramic)     Cl, BCl₃                    attacked by BCl₃ (AlCl₃ volatile);
                                                Al contamination; avoided where
                                                exposed to the plasma
Quartz window       Cl, Br                      OK; etched by F and BCl₃;
                                                SiOₓ and B deposits
Y₂O₃- or Al₂O₃-     window of TCP               coated windows reduce erosion
coated dielectric
window
SiC / Si edge ring  all                         consumable; erosion changes edge
                                                ion energy (Chapter 6)
Anodized Al         Cl                          not used in the plasma region
```

BCl₃ is the material constraint that conductor chambers for high-k etch face and gate-etch chambers often do not: it attacks alumina, and boron deposits on every cool surface. Chambers that run BCl₃ use yttria-coated parts and heated liners.

---

## 5.8 Chamber Allocation

### 5.8.1 Module 1

Storage-node separation uses only Cl₂, BCl₃, and Ar, and etches only TiN. It runs in a dedicated conductor chamber whose wall is kept in a TiClₓ-seasoned state (Chapter 9). Mixing it with F-based or high-k work in the same chamber raises drift and contamination risk.

### 5.8.2 Module 2

The plate etch can run in one chamber with all five steps, or be split:

```
Option                         Advantages                    Drawbacks
──────────────────────────────────────────────────────────────────────────────
Single chamber (reference)     One transfer; simple flow;    F, Br, Cl, B memory in one
                               endpoint-to-endpoint          wall; longest wet-clean
                               continuity                    interval sensitivity
Split: W + SiGe in chamber A;  Each wall sees fewer          Vacuum transfer between
TiN + HK in chamber B          chemistries; chamber B can    chambers; Cl-covered
                               be heated (Chapter 7)         surfaces held in vacuum
                                                             (no air break)
```

### 5.8.3 Post-Etch Treatment

Both modules finish with a post-etch treatment in a downstream (remote) plasma chamber on the same mainframe, to strip resist (module 2) and remove halogens from the surface before air exposure (Chapter 11).

---

## 5.9 Throughput and Matching

### 5.9.1 Throughput

```
Module 1:
  Plasma time        BT 5 + ME ≈ 25 + OE 10 + transitions 6 = 46 s
  Overhead           transfer, pump-down, chuck, dechuck ≈ 55 s
  Per wafer          ≈ 100 s → 36 wafers/h per chamber
  Mainframe          3 SNS chambers + 1 PET chamber → ≈ 100 wafers/h

Module 2:
  Plasma time        BARC 20 + W 15 + SiGe ME 48 + SiGe OE 25 + HK 93
                     + transitions 15 = 216 s
  Overhead           ≈ 60 s
  Per wafer          ≈ 276 s → 13 wafers/h per chamber
  Mainframe          4 plate chambers + 2 strip/PET → ≈ 50 wafers/h
```

### 5.9.2 Matching

```
Fleet matching criteria (reference, illustrative):
  Module 1
    Blanket TiN ME rate              ± 2% of fleet mean
    Blanket SiN OE rate              ± 10%
    Endpoint time (product)          ± 3%
    Rim recess (product)             ± 1.5 nm of fleet mean
  Module 2
    W, SiGe, ZrO₂ blanket rates      ± 3%
    HK step SiN loss                 ± 1.5 nm
    Plate-edge profile               ± 2°
    Zr residue (TXRF monitor)        below 1 × 10¹³ cm⁻² on every chamber
```

The most sensitive matching parameter in module 1 is the endpoint time on product wafers, because it integrates the incoming film, the breakthrough, the rate, and the loading. In module 2 it is the ZrO₂ rate, because the HK overetch is the tightest margin in the book (Chapter 4).

---

## Summary and Key Takeaways

1. **ICP separates flux from energy.** 2 × 10¹⁶ ions cm⁻² s⁻¹ at 50–150 eV is out of reach for a CCP and routine for an ICP.

2. **Bias power is not ion energy.** E_i ≈ V_p + P_bias/I_i; at 70 W, a 10% density drift is a 10% energy drift. Control low-energy steps by voltage.

3. **The IEDF tail sets selectivity.** At 13.56 MHz the 50 eV step has ions near 70 eV; tailored waveforms and higher frequencies narrow it.

4. **Transitions take seconds, not residence times.** τ = 0.13 s; transitions take 2–3 s; hold bias off while gases change.

5. **BCl₃ sets the materials.** Yttria-coated parts, heated liners and lines, no exposed alumina.

6. **Module 1 is fast; module 2 is not.** About 36 wafers/h per SNS chamber versus 13 per plate chamber.

---

## Study Questions

1. Compute the ion flux and ion current to a 300 mm wafer for n_e = 2.5 × 10¹¹ cm⁻³ and T_e = 3.0 eV with Ar⁺ (40 amu) as the dominant ion.

2. The SNS OE runs at 70 W bias with 2.0 A of ion current. The source density drifts up by 15%. With fixed bias power, what is the new ion energy? With fixed sheath voltage, what is the new bias power?

3. Using the yield model of Chapter 3, estimate the SiN rate contributed by the 70 eV peak of a bimodal IEDF with half its ions at 30 eV and half at 70 eV, and compare it with a monoenergetic 50 eV beam.

4. A plate chamber has 40 L volume, 10 mTorr, and 300 sccm total flow. Compute the residence time. Why does the step transition still take 2–3 s?

5. A chamber's alumina window cover is replaced by an uncoated one. Which step attacks it, what product forms, and what contamination would you look for on the wafers?

6. Module 2 must deliver 50 wafers/h. How many plate chambers are needed if the HK overetch is raised from 50% to 70%? What does the extra time cost in resist?

---

**Next Chapter:** [Chapter 6: Electrostatic Chucks, Temperature & Etch-Back Uniformity](./06-chuck-temperature-etchback-uniformity.md)

---

**Chapter 5 Development Status:** Complete  
**Version:** 1.0
