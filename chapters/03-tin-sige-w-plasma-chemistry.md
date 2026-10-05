# Chapter 3: Plasma Chemistry of TiN, SiGe & W Etching

## Overview

The electrode etches remove three conductors: titanium nitride (both modules), boron-doped silicon-germanium, and tungsten (module 2). Each has a natural chemistry. TiN etches in chlorine because TiCl₄ is volatile at room temperature. SiGe etches in chlorine or bromine, with germanium speeding the reaction and boron slowing the spontaneous part of it. W etches fastest in fluorine, because WF₆ boils at 17 °C. The art of electrode etch lies in using each chemistry where it is needed and stopping it where it is not: on SiN at the end of storage-node separation, on TiN at the end of the SiGe step, and on SiGe at the end of the W step.

This chapter develops the surface chemistry, the role of ion energy in rate and selectivity, the loading effect that governs the storage-node overetch, and the passivation mechanisms that shape the plate edge. The high-k dielectric, which needs a different chemistry, is the subject of Chapter 4.

**Learning Objectives:**
- Explain the thermochemistry of TiN, TiO₂, Si, Ge, and W etching in chlorine, bromine, and fluorine
- Use an ion-enhanced yield model to predict rate and selectivity versus ion energy
- Derive the loading equation and compute the rate jump on the pillar tops after the field clears
- Explain why germanium increases, and boron decreases, the lateral etch of SiGe
- Describe the passivation that protects each sidewall of the plate edge

---

## 3.1 Etch Products and Their Volatility

The first question for any etch is whether the product leaves the surface. The second is whether it leaves without help.

```
Etch products (normal boiling or sublimation point, illustrative):
  Product     T_b (°C)    Vapor pressure at 25 °C    Comment
  ──────────────────────────────────────────────────────────────────────────
  TiCl₄       136         ≈ 10 Torr                  volatile; main TiN product
  TiBr₄       230         ≈ 0.01 Torr                weakly volatile
  TiF₄        284 (sub)   ≪ 10⁻³ Torr                not volatile at 60 °C
  SiCl₄        58         ≈ 240 Torr                 volatile
  SiBr₄       153         ≈ 4 Torr                   volatile
  SiF₄        −86         gas                        very volatile
  GeCl₄        87         ≈ 75 Torr                  volatile
  GeBr₄       186         ≈ 0.3 Torr                 volatile enough
  WF₆          17         gas                        very volatile
  WOCl₄       228         ≈ 0.01 Torr                weakly volatile
  WCl₆        347         ≪ 10⁻³ Torr                not volatile at 60 °C
  BCl₃         13         gas                        gas; O-getter
  NCl₃         71         ≈ 150 Torr                 minor N product; unstable
```

TiN therefore etches in chlorine, not in fluorine or bromine. W etches in fluorine, or in chlorine with oxygen (as WOCl₄), but not in pure chlorine at room temperature. Si and Ge etch in all three halogens. These facts set the chemistry of every step.

---

## 3.2 TiN in Chlorine

### 3.2.1 Thermochemistry

```
TiN(s) + 2 Cl₂ → TiCl₄(g) + ½ N₂          ΔH ≈ −763 − (−338) = −425 kJ/mol
TiO₂(s) + 2 Cl₂ → TiCl₄(g) + O₂           ΔH ≈ −763 − (−944) = +181 kJ/mol
TiO₂(s) + 4/3 BCl₃ → TiCl₄(g) + 2/3 B₂O₃  ΔH ≈ −763 − 849 + 944 + 538
                                             = −130 kJ/mol
```

TiN chlorination is strongly favourable; TiO₂ chlorination is not, unless something takes the oxygen. BCl₃ does: it turns the oxygen into boron oxide or volatile boron oxychloride, (BOCl)₃. This is why every TiN etch begins with a **breakthrough** step rich in BCl₃, or with enough ion energy to sputter the surface oxide.

### 3.2.2 Mechanism

The etch of TiN in a chlorine plasma proceeds in four steps:

```
1. Cl atoms adsorb on Ti sites, forming TiClₓ (x = 1–3) at the surface
2. Ions break Ti–N bonds and mix Cl into the top 1–2 nm
3. TiCl₄ forms and desorbs; this step is ion-assisted below ≈ 100 °C
4. Nitrogen leaves as N₂ (recombined at the surface) and in small part as
   NClₓ; it is the slower half of the reaction at low ion energy
```

At room temperature and without ions, Cl₂ etches TiN very slowly (≈ 0.5 nm/min at 60 °C). With ions of 50–100 eV, the rate rises to tens of nanometres per minute. The **spontaneous** part of the etch is the part that proceeds sideways. It is small but not zero, and it is what deepens the dimple cusp in storage-node separation (Chapter 10).

### 3.2.3 The Surface Oxide

The 1–2 nm TiOₓNᵧ layer that forms in air (Chapter 2) is the first film the etch meets:

```
Breakthrough step (reference):
  BCl₃ 60 / Cl₂ 10 / Ar 50 sccm, 5 mTorr, 500 W source, 200 W bias
  Ion energy ≈ 110 eV; duration 5 s
  Removes ≈ 1.5 nm TiOₓNᵧ plus ≈ 2 nm TiN
Without breakthrough (Cl₂/Ar main etch only):
  Incubation 10–30 s, non-uniform; local delays leave islands of TiN
  that clear late or not at all
```

An incubation that varies from point to point is a clearing time that varies from point to point. It is a residue risk in a blanket etch with no pattern to self-align it.

---

## 3.3 Ion Energy, Yield & Selectivity

### 3.3.1 The Yield Model

In the ion-assisted regime, the number of film units removed per incident ion is

```
Y(E) = A · (√E − √E_th)      for E > E_th

ER = Y(E) · Γ_i · θ / n

  Γ_i   ion flux (cm⁻² s⁻¹)
  θ     fraction of surface sites saturated with Cl (≤ 1)
  n     film unit density (cm⁻³)
```

```
Reference constants (illustrative, Cl₂/Ar-based plasma):
  Film     n (cm⁻³)        E_th (eV)     A
  ─────────────────────────────────────────────
  TiN      5.1 × 10²²       25           0.053
  SiN      4.4 × 10²²       40           0.012
  SiO₂     2.3 × 10²²       50           0.020
```

Checking the reference main etch: E ≈ 70 eV, Γ_i ≈ 2.0 × 10¹⁶ cm⁻² s⁻¹, θ ≈ 1:

```
Y_TiN = 0.053 × (√70 − √25) = 0.053 × (8.37 − 5.00) = 0.18
ER_TiN = 0.18 × 2.0×10¹⁶ / 5.1×10²² = 7.0×10⁻⁸ cm/s = 0.70 nm/s = 42 nm/min

Y_SiN = 0.012 × (8.37 − 6.32) = 0.025
ER_SiN = 0.025 × 2.0×10¹⁶ / 4.4×10²² = 1.1×10⁻⁸ cm/s ≈ 0.11 nm/s

(BCl₃-derived BClₓ deposition on SiN lowers its effective θ to ≈ 0.7:
 ER_SiN ≈ 0.08 nm/s = 4.7 nm/min)

Selectivity TiN:SiN ≈ 42 / 4.7 ≈ 9
```

### 3.3.2 Lower Energy, Higher Selectivity

Because the threshold for SiN is higher than for TiN, lowering the ion energy cuts the SiN rate faster than the TiN rate:

```
Ion energy        TiN rate      SiN rate      Selectivity    Use
(eV)              (nm/min)      (nm/min)      TiN:SiN
──────────────────────────────────────────────────────────────────────
110 (BT)          ≈ 75          ≈ 12          6              breakthrough
 70 (ME)            42           4.7          9              main etch
 50 (OE)            24           1.6          15             overetch
 35                 10           ≈ 0          > 50           too slow; θ, N
                                                             removal limit
```

(The OE rate includes a lower flux at the lower source power of the overetch step.)

Below about 35 eV, TiN etching becomes limited by nitrogen removal and by residual oxide, and rate and uniformity both suffer. The reference therefore etches at 70 eV until the field clears and finishes at 50 eV.

### 3.3.3 Oxide

SiO₂ has the highest threshold and the strongest bonds of the three films. In the storage-node separation it is not exposed. In the plate etch it is exposed only if the top SiN has been breached; with 120 nm of SiN, it never is.

---

## 3.4 Loading

### 3.4.1 Where Loading Comes From

In a blanket etch, every square centimetre of exposed TiN consumes Cl atoms. If the reactor cannot supply Cl faster than the wafer consumes it, the Cl density falls as the exposed area rises:

```
Balance of Cl atoms in the reactor:
  generation G = loss to pumping + loss to walls + consumption by the wafer
  G = n_Cl (k_p + k_w) + n_Cl · k_r · A_exp

  n_Cl = G / (k_p + k_w + k_r A_exp)

With θ ∝ n_Cl (below saturation), the etch rate
  ER(θ_A) = ER_max / (1 + k · θ_A)

  θ_A   fraction of the wafer area that is exposed TiN
  k     k_r A_wafer / (k_p + k_w), the loading constant
```

### 3.4.2 The Reference Loading Constant

```
Reference main etch: k ≈ 1.2 (measured with blanket and patterned wafers)
  Full TiN coverage (θ_A = 1):    ER = ER_max / 2.2
  After the field clears:         only the pillar tops are TiN
    θ_A = (π × 16² / 1734) × 0.45 = 0.464 × 0.45 = 0.21
    ER = ER_max / (1 + 1.2 × 0.21) = ER_max / 1.25

  Rate jump on the pillar tops = 2.2 / 1.25 = 1.76
```

The moment the field clears, the remaining TiN, the pillar tops, etches 76% faster than the blanket film did. The reference overetch was measured on blanket wafers at 24 nm/min; on product wafers, the pillar tops recess at about 42 nm/min during the same step. A process engineer who sets the overetch from blanket rates will recess the pillars almost twice as deep as planned.

### 3.4.3 The Endpoint Signal Comes From the Same Physics

The rate jump has a useful side effect. When the field clears, the TiCl₄ production falls by the ratio of exposed areas (corrected for the rate jump), and the Cl density rises. Both are seen in optical emission:

```
At field clearing:
  TiCl₄ production ∝ θ_A · ER  → falls to 0.21 × 1.76 = 0.37 of its value
  Cl density                   → rises by 1.76×
Optical emission (Chapter 8):
  Ti* and TiCl* lines fall; Cl* (837.6 nm) and Cl₂* rise; N₂* (337 nm) falls
```

### 3.4.4 Local Loading Is Weak

The pattern at storage-node separation is fine and uniform: every square micrometre of array has the same pillar density. The Cl diffusion length at 6 mTorr is centimetres. The difference between array (46% TiN after clearing) and periphery (0%) is felt across the wafer only through the global loading constant, not as a local effect within a die. This is not true at the plate etch, where islands of 1 mm are separated by large open areas, and where SiGe and W loading are larger (Chapter 12).

---

## 3.5 SiGe in Chlorine and Bromine

### 3.5.1 Thermochemistry and Spontaneous Etching

```
Si(s) + 2 Cl₂ → SiCl₄(g)        ΔH ≈ −663 kJ/mol
Ge(s) + 2 Cl₂ → GeCl₄(g)        ΔH ≈ −496 kJ/mol
Bond energies:  Si–Si 3.3 eV,  Si–Ge 3.1 eV,  Ge–Ge 2.8 eV
```

The reaction with Ge releases less energy but needs less energy to start, because the Ge–Ge bond is weaker. In practice Cl atoms etch Ge **spontaneously** at room temperature with a reaction probability of order 10⁻³, while undoped or p-type Si reacts with a probability two orders lower. In Si₁₋ₓGeₓ, the spontaneous rate rises steeply with x:

```
Spontaneous (lateral) etch rate in a Cl-rich plasma, 60 °C (illustrative):
  Si (p⁺)          < 0.5 nm/min
  Si₀.₈Ge₀.₂ (p⁺)   ≈ 2 nm/min
  Si₀.₇Ge₀.₃ (p⁺)   ≈ 5 nm/min
  Si₀.₆Ge₀.₄ (p⁺)   ≈ 12 nm/min
```

### 3.5.2 Boron

Heavy n-type doping speeds the spontaneous Cl etch of silicon by moving the Fermi level up and making charge transfer to adsorbed Cl easier. Heavy p-type doping does the opposite. The reference SiGe is B-doped at 3 × 10²⁰ cm⁻³, which suppresses the Si part of the spontaneous etch but not the Ge part. The plate fill's lateral etch is therefore set mainly by its germanium content.

### 3.5.3 Bromine

Bromine atoms are larger, less reactive, and do not etch Si or Ge spontaneously to any useful degree at room temperature. HBr-based chemistry is therefore highly anisotropic: the etch proceeds only where ions strike. The cost is rate:

```
SiGe main etch (reference): HBr 150 / Cl₂ 50 / O₂ 5 sccm, 10 mTorr,
  600 W source, 250 W bias (E ≈ 110 eV)
  SiGe rate                180 nm/min
  Lateral (spontaneous)    ≈ 1.5 nm/min (Cl fraction 25%)
  Selectivity SiGe:TiN     ≈ 8
  Selectivity SiGe:resist  ≈ 3

SiGe overetch (reference): HBr 200 / O₂ 6 / He 100 sccm, 15 mTorr,
  500 W source, 90 W bias (E ≈ 55 eV)
  SiGe rate                60 nm/min
  Lateral                  ≈ 0.5 nm/min
  TiN rate                 ≈ 1.5 nm/min → selectivity ≈ 40
  SiN rate                 ≈ 1 nm/min
```

### 3.5.4 Why the Overetch Stops on TiN

TiN in HBr/O₂ forms a surface layer of TiOₓ and TiBrₓ. TiBr₄ is far less volatile than TiCl₄, and the oxide needs a getter it does not get. The TiN surface "passivates" and etches only by low-energy sputtering. This is the basis of the SiGe overetch's high selectivity to the top electrode: the 5 nm TiN acts as the etch stop for 150 nm of SiGe.

### 3.5.5 Oxygen and Sidewall Passivation

The small O₂ addition oxidizes SiBrₓ products that redeposit on the sidewall into a SiOₓBrᵧ film about 1–2 nm thick. That film protects the SiGe sidewall against the spontaneous etch. Too little O₂ leaves the sidewall bare and the profile bows; too much O₂ oxidizes the etch front and leaves micro-masking residue ("grass"). The reference O₂/HBr ratio of 3% is a typical compromise.

---

## 3.6 W in Fluorine

### 3.6.1 Chemistry

```
W(s) + 3 F₂ → WF₆(g)            ΔH ≈ −1722 kJ/mol
W main etch (reference): SF₆ 40 / N₂ 20 / Cl₂ 30 / Ar 50 sccm, 8 mTorr,
  600 W source, 180 W bias (E ≈ 85 eV)
  W rate                   200 nm/min
  SiGe rate                ≈ 300 nm/min (F etches Si and Ge spontaneously)
  Resist rate              ≈ 150 nm/min
```

Fluorine etches W spontaneously, so a pure SF₆ etch is isotropic. **Nitrogen** forms a thin WNₓ layer on the sidewall that slows the lateral etch; **chlorine** dilutes the fluorine and forms a less reactive WClₓFᵧ surface. Together they bring the W profile to 85–88°.

### 3.6.2 No Stop on SiGe

The W step is not selective to SiGe: SF₆ etches SiGe faster than W. The step therefore relies on a sharp endpoint (the F* line at 704 nm rises as W clears, Chapter 8) and a short overetch. The SiGe below is 150 nm thick and absorbs 10–20 nm of loss without consequence. What matters is that the W clears everywhere before the chemistry changes, because HBr/Cl₂ does not etch W at a useful rate: a W island left at the end of the W step becomes a micromask for the SiGe below it.

### 3.6.3 Grain Boundaries

PVD W has columnar grains with boundaries running through the film. Fluorine attacks boundaries slightly faster. At the end of the W step the remaining W is thinnest at the boundaries and thickest at the grain centres, roughening the SiGe surface by 2–3 nm. That roughness is transferred down through the SiGe etch and appears as plate-edge roughness and occasionally as SiGe "pips" at the foot.

---

## 3.7 Halogen Uptake & Residues

Every step leaves halogen in the surface of what remains:

```
Halogen in the surface after etch (illustrative, XPS):
  TiN after Cl₂ etch-back        Cl 3–6 at% in the top 2 nm
  SiGe sidewall after HBr        Br 2–4 at%; SiOₓBrᵧ film
  W sidewall after SF₆/Cl₂       F and Cl 1–3 at%
  SiN surface after BCl₃         B and Cl 2–5 at%
```

In air, chlorine and bromine absorbed in metal surfaces hydrolyse to HCl and HBr, which attack the metal underneath. On TiN this grows a Cl-rich oxide; on W it pits. On the storage-node TiN after module 1, residual Cl is also carried into the support-open and dip-out of Book #30 and ends at the interface of the dielectric. Chapter 11 treats removal and passivation.

---

## Summary and Key Takeaways

1. **Volatility chooses the halogen.** TiN in Cl (TiCl₄), W in F (WF₆), SiGe in Br/Cl.

2. **Oxide needs a getter.** TiO₂ chlorination is endothermic; BCl₃ makes it exothermic. Every TiN etch begins with a breakthrough.

3. **Lower energy, higher selectivity.** TiN:SiN rises from 9 at 70 eV to 15 at 50 eV because the SiN threshold is higher.

4. **Loading speeds the overetch.** When the field clears, the exposed TiN area falls to 21% of the wafer, and the pillar tops etch 1.76× faster than the blanket rate.

5. **Germanium drives the lateral etch; bromine stops it.** HBr/O₂ also passivates TiN, which makes the SiGe overetch stop on the top electrode.

6. **W is not selective to SiGe.** The W step needs a sharp endpoint; any W island becomes a micromask.

---

## Study Questions

1. Using the yield model of Section 3.3.1, compute the TiN and SiN rates and the selectivity at 90 eV with the reference flux. Is the trend with energy what you expect?

2. The loading constant is 1.5 instead of 1.2. Compute the rate jump at field clearing. If the overetch is 10 s at a blanket rate of 24 nm/min, how much deeper do the pillars recess than with k = 1.2?

3. Why does the endpoint signal at field clearing fall to only about 37% of its value, rather than to zero?

4. A new SiGe supplier delivers Si₀.₆Ge₀.₄ instead of Si₀.₇Ge₀.₃. Using Section 3.5.1, estimate the change in lateral etch during a 50 s main etch with 25% Cl. What sidewall change do you expect?

5. A tool's TiN breakthrough step is accidentally skipped. Describe what happens in the main etch and what defect appears after storage-node separation.

6. The W step has a 25% overetch at the SiGe rate of 300 nm/min. How much SiGe is lost? What happens if the W step ends 2 s early at a site where 3 nm of W remains?

---

**Next Chapter:** [Chapter 4: Etching High-k Dielectrics — ZrO₂, Al₂O₃ & HfO₂](./04-high-k-dielectric-etch-chemistry.md)

---

**Chapter 3 Development Status:** Complete  
**Version:** 1.0
