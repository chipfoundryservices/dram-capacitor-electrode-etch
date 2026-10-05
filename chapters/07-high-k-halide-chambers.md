# Chapter 7: High-Temperature & Halide Chambers for High-k Removal

## Overview

The high-k step is 93 seconds of a 216-second plate recipe. It consumes a third of the resist, nearly all the SiN loss, and the tightest margin in the module: the 50% overetch that keeps ZrO₂ grains out of periphery contacts (Chapter 4). It also runs a chemistry, BCl₃/Cl₂, that coats cold surfaces with boron, condenses metal chlorides in the foreline, and leaves the chamber wall loaded with zirconium.

This chapter describes the hardware built around the high-k step: chambers with heated chucks and hot walls that raise the volatility of ZrCl₄ and AlCl₃; the hard-mask route that such chambers require; the delivery and handling of BCl₃; the cleaning rules that boron and zirconium impose; the exhaust; and hardware for atomic-layer etching. It ends with a comparison of the four ways to remove the ZAZ from the periphery.

**Learning Objectives:**
- Explain why heated chucks and hot walls speed high-k removal and what they cost
- Describe the hard-mask route and the TiN sidewall problem it creates at high temperature
- Specify BCl₃ delivery to avoid condensation and hydrolysis
- State the order in which a zirconium- and boron-coated wall must be cleaned, and why
- Compare ambient, hot, hybrid, and ALE-finished high-k routes

---

## 7.1 Why the High-k Step Gets Its Own Hardware

```
Share of the reference plate etch taken by the HK step:
  Plasma time            93 of 216 s       (43%)
  Resist consumed        78 of 222 nm      (35%)
  SiN loss               ≈ 4 of 4 nm       (≈ 100%)
  Wafer heat load        ≈ 1.1 W/cm²       (highest of any step)
  Chamber wall loading   Zr, Al, B deposits (the hardest to clean)
```

A faster, more selective high-k step shortens the module, relieves the resist budget, and reduces the ion and UV dose at the plate edge (Chapter 13). Temperature is the lever (Chapter 4, Section 4.6). The hardware question is how to apply it without destroying the mask, the TiN, or the chamber.

---

## 7.2 Heated Chucks

### 7.2.1 Construction

```
High-temperature ESC (illustrative):
  Type                  Coulombic ceramic (AlN); Johnsen–Rahbek behaviour
                        changes too much with temperature for stable clamping
  Range                 150–300 °C surface
  Heater                embedded multizone resistive heater; 2–4 zones
  Backside gas          He, 5–15 Torr
  Thermal break         low-conductance mount between the hot puck and the
                        cooled base
  Uniformity            ± 2 °C at 250 °C with plasma on
  Heat-up / cool-down   tens of minutes; temperature is not changed between
                        wafers
```

A chuck that runs at 250 °C cannot be cooled to 60 °C for a SiGe step and back in production. A hot high-k step therefore lives in its own chamber, and the wafer is transferred to it under vacuum after the W and SiGe steps.

### 7.2.2 The Hot Recipe

```
Hot HK step (illustrative):
  BCl₃ 80 / Cl₂ 20 / Ar 50 sccm, 5 mTorr, 800 W source, 200 W bias
  (E ≈ 80 eV), chuck 250 °C

  Film                Rate (nm/min)
  ───────────────────────────────────
  ZrO₂ (tetragonal)       12
  Al₂O₃                    9
  TiN (vertical)         120
  SiN                      4
  SiO₂                     2
  ZrO₂ : SiN               3.0  (vs 0.75 at 60 °C, 150 eV)

  Time to clear ZAZ       5.2/12 + 0.3/9 = 0.47 min = 28 s
  Overetch                35% (grain-level spread σ_g ≈ 5% at 250 °C)
  HK step total           ≈ 40 s (vs 93 s)
  SiN loss                ≈ 0.7 nm (vs ≈ 4 nm)
```

At 250 °C, ZrCl₄ desorbs thermally once formed, so the ions need only to break the lattice and remove oxygen. Grain-to-grain differences in clearing shrink, and the overetch needed for the residue tail falls.

---

## 7.3 The Hard-Mask Route

### 7.3.1 Why a Hard Mask

KrF resist flows above about 120–130 °C and decomposes above about 200 °C in a chlorine plasma, contaminating the chamber with carbon and chlorinated organics. A 250 °C step needs an inorganic mask:

```
Hard-mask route (illustrative):
  1. PE-TEOS 100 nm on the W strap (≤ 400 °C)
  2. BARC + KrF resist; expose; develop
  3. HM open: CF₄/CHF₃ (stops on W; W is etched slightly)
  4. Resist strip: O₂ downstream (oxidizes the exposed W surface to WOₓ)
  5. W etch: breakthrough of WOₓ, then SF₆/N₂/Cl₂ (ambient chamber)
  6. SiGe ME + OE: HBr/Cl₂/O₂, HBr/O₂ (ambient chamber)
  7. Vacuum transfer to the hot chamber
  8. TiN + ZAZ at 250 °C
  9. Post-etch treatment; the oxide HM stays and becomes part of the ILD
```

The oxide hard mask costs a deposition and an extra etch step, but it is not stripped afterwards: it is the first layer of the inter-layer dielectric over the plate.

### 7.3.2 The TiN Sidewall at 250 °C

Heat that helps ZrO₂ also helps chlorine attack TiN sideways. The spontaneous TiN etch has an activation energy near 0.25 eV:

```
Ratio of spontaneous rates, 250 °C vs 60 °C:
  exp[(E_a/k)(1/333 − 1/523)] = exp[2900 × 1.09×10⁻³] = exp(3.17) ≈ 24

Lateral TiN rate in BCl₃/Cl₂ (illustrative):
  60 °C:   ≈ 3 nm/min   → over 87 s exposed → ≈ 4 nm notch
  250 °C:  ≈ 70 nm/min  → over 38 s exposed → ≈ 45 nm notch
```

The hot step solves the high-k problem by creating a TiN problem: the 5 nm top electrode is undercut tens of nanometres under the SiGe at the plate edge. Three remedies are used:

```
Remedy                            How it works                  Cost
──────────────────────────────────────────────────────────────────────────────
Etch TiN cold, passivate, then    TiN in the ambient chamber;   Extra step; TiO₂ shell
transfer                          short O₂ flash grows a        must survive BCl₃ at
                                  1–2 nm TiOₓ shell on the      250 °C (BCl₃ etches TiO₂
                                  TiN sidewall                  slowly without ions)
BCl₃-rich, Cl₂-free hot step      fewer Cl atoms; BCl₃ etches   lower ZrO₂ rate; more
                                  ZrO₂ but TiN slowly without   boron deposition
                                  ions
Moderate temperature (150 °C)     lateral ×≈ 5 instead of 24;   smaller benefit: ZrO₂
                                  resist marginal               12 nm/min at 450 W
```

The common production compromise is the first: TiN is cleared at 60 °C, the sidewall is passivated, and only the ZAZ sees 250 °C.

---

## 7.4 Hot Walls and Liners

Metal chlorides that desorb from the wafer must not condense on the chamber before they reach the pump:

```
Condensation risk at chamber pressures (illustrative):
  AlCl₃      condenses below ≈ 60–80 °C at its partial pressure in the chamber
  ZrCl₄      condenses below ≈ 120–150 °C
  BₓClᵧ      deposits on surfaces below ≈ 80 °C
  TiCl₄      no condensation risk above ≈ −20 °C

Reference hot HK chamber:
  Liner      150–180 °C
  Window     ≥ 120 °C
  Lid, gas plate 120 °C
```

Hot walls reduce, but do not eliminate, wall deposits. They also change the wall's recombination of Cl atoms and therefore the Cl density at the wafer. A chamber whose liner heater has failed is a chamber whose etch rate has changed: wall temperature must be an interlocked parameter.

---

## 7.5 BCl₃ Delivery

### 7.5.1 A Low-Pressure Liquefied Gas

```
BCl₃ properties:
  Boiling point          12.5 °C
  Vapor pressure 20 °C   ≈ 1.3 atm
  Vapor pressure 30 °C   ≈ 1.8 atm
```

BCl₃ is delivered from its own liquid at little more than atmospheric pressure. A mass-flow controller needs a pressure drop; at 1.3 atm there is little to spare. The cylinder is heated to 25–30 °C in a temperature-controlled cabinet, and every line downstream is heated a few degrees warmer than the cylinder so that the gas cannot recondense in a cooler segment. A line that cools overnight in a cold sub-fab can deliver liquid slugs at start-up: the flow controller reads correctly, and the chamber receives a pulse.

### 7.5.2 Moisture

```
BCl₃ + 3 H₂O → B(OH)₃ + 3 HCl
```

Any moisture in the line, from an imperfect purge after a cylinder change or a leaking fitting, forms boric acid particles and HCl. The particles land on wafers as boron-containing defects; the HCl corrodes stainless steel and adds Fe, Cr, and Ni to the gas. Specifications: < 1 ppm H₂O in the BCl₃, helium leak checks at every cylinder change, and cycle-purging with dry N₂ before opening any BCl₃ line.

---

## 7.6 Wall Cleaning: the Order Matters

### 7.6.1 What Is on the Wall

After a few hundred plate wafers, the wall of a single-chamber plate etcher carries a layered deposit:

```
Wall deposit (illustrative, outermost last):
  BₓClᵧ / BOₓClᵧ    from the HK step
  ZrClₓOᵧ           from the HK step
  AlClₓ             from the Al₂O₃ layer
  SiOₓBrᵧ, SiOₓ     from the SiGe steps
  WOₓFᵧ             from the W step
  TiClₓ, TiOₓ       from the TiN step
  CₓFᵧ, CₓHᵧ        from the BARC step and resist erosion
```

### 7.6.2 Fluorine First Is the Wrong Order

The usual waferless auto-clean (WAC) for conductor chambers uses NF₃ or SF₆ with O₂: fluorine removes Si, W, and B as volatile fluorides and oxygen removes carbon. On a zirconium-coated wall, that fluorine forms **ZrF₄**, which does not volatilize at any wall temperature. A fluorine clean converts a removable ZrClₓ deposit into a permanent ZrF₄ skin that slowly flakes:

```
Reference WAC sequence for a plate chamber with HK (illustrative):
  1. BCl₃/Cl₂ plasma, 20–30 s: removes Zr and Al as chlorides (hot wall)
  2. O₂ plasma, 10 s: removes carbon
  3. NF₃/O₂ plasma, 20 s: removes Si, B, W
  4. Seasoning: short TiN/SiGe-like plasma to restore wall state
```

### 7.6.3 Wet Clean and Safety

At wet clean, boron and chloride deposits react with air moisture to form boric acid and HCl. Chamber opening requires purge cycles, a ventilated enclosure, and acid-resistant protective equipment. Zirconium-containing flakes are not toxic in the way some metals are, but they are a cross-contamination source for every chamber they are carried to.

---

## 7.7 Exhaust

```
Exhaust train for a high-k plate chamber (reference):
  Turbo pump          corrosion-resistant coatings; purged bearings
  Foreline            heated to ≈ 150 °C to keep AlCl₃ and ZrCl₄ in the gas
                      phase; or a cold trap that collects them deliberately
  Dry pump            heated, N₂ purged
  Abatement           wet scrubber for HCl, HBr, BCl₃ (hydrolysed), Cl₂;
                      combustion for SF₆ and CF₄ residues
```

A cold, unheated foreline fills with AlCl₃ and ZrCl₄ solids. They raise the foreline pressure, and so the chamber pressure at fixed throttle position, and they hydrolyse violently when the line is opened. Foreline pressure trend is a useful early indicator of exhaust clogging.

---

## 7.8 ALE-Capable Hardware

### 7.8.1 Plasma ALE

```
Requirements for plasma ALE of the last nanometre of ZAZ:
  Gas switching          ≤ 0.5 s (fast pulsed valves, close to the chamber)
  Bias on/off            synchronized to the gas steps within 50 ms
  Ion energy             50–70 eV window, ± 5 eV (tailored-waveform bias)
  Cycle                  BCl₃ dose 1.5 s, purge 0.5 s, Ar⁺ 2 s, purge 0.5 s
                         → ≈ 4.5 s per cycle, ≈ 0.1 nm per cycle
  In-situ monitor        ellipsometry or reflectometry on a periphery pad
```

### 7.8.2 Thermal ALE

Thermal ALE uses a separate, plasma-free chamber at 250–300 °C (HF dose, then a ligand-exchange reactant such as TMA, DMAC, or SiCl₄). It is isotropic, so it attacks the ZAZ edge under the TiN at the plate edge just as a wet etch does, but by a known number of ångströms per cycle.

### 7.8.3 Where ALE Fits

ALE is too slow to remove the whole ZAZ in production (about 5 minutes). Its use is the last 0.5–1 nm: after a short, ion-assisted main HK step stops before the grains begin to separate, 5–10 ALE cycles clear the grains uniformly with almost no SiN loss.

---

## 7.9 Four High-k Routes Compared

```
Route                     HK time   Extra steps          SiN loss   Notch    Residue
                                                                              tail
─────────────────────────────────────────────────────────────────────────────────────
Ambient, resist mask       93 s     none                 ≈ 4 nm     ≈ 4 nm   OE 50%;
(reference)                                                                   tightest
Hot (250 °C), oxide HM     40 s     HM dep + open;       ≈ 1 nm     ≈ 5 nm   OE 35%;
with TiN passivation                O₂ flash; transfer              (with    better
                                                                    shell)
Hybrid: dry to 1 nm,       60 s +   wet chamber;          ≈ 1 nm    wet      isotropic;
then dilute HF             wet      rinse/dry                       undercut good, but
                           30–60 s                                  of ZAZ   slow on
                                                                             tetragonal
ALE finish                 50 s +   ALE-capable          < 1 nm     ≈ 4 nm   best
                           45 s     hardware; time                           uniformity
```

Each route moves the constraint somewhere else. The ambient route is simplest and uses the most overetch. The hot route is fastest but adds a mask and a TiN sidewall problem. The hybrid route avoids ions at the end but adds a wet chamber and an edge undercut. The ALE route is the most controlled and the slowest. Chapter 16 compares their costs.

---

## Summary and Key Takeaways

1. **The HK step dominates the plate etch.** 43% of the time, 35% of the resist, nearly all the SiN loss.

2. **Heat helps the high-k and hurts the TiN.** At 250 °C ZrO₂ etches 2× faster at half the ion energy, but the spontaneous TiN lateral etch rises ≈ 24×.

3. **A hot step needs a hard mask and a TiN shell.** Oxide HM (kept as ILD), TiN cleared cold, sidewall passivated, ZAZ cleared hot.

4. **BCl₃ is a near-liquid at the cylinder.** Heat the cylinder and every line warmer than it; exclude moisture.

5. **Clean zirconium with chlorine before fluorine.** Fluorine turns ZrClₓ into permanent ZrF₄.

6. **Heat the foreline or trap it deliberately.** AlCl₃ and ZrCl₄ condense in cold lines.

---

## Study Questions

1. Compute the ratio of spontaneous TiN etch rates at 150 °C and at 60 °C for E_a = 0.25 eV. What notch would a 60 s exposure at 150 °C produce if the 60 °C lateral rate is 3 nm/min?

2. In the hot recipe, how much SiN is lost if the overetch is raised from 35% to 60%? Compare with the ambient recipe at 50%.

3. A BCl₃ cylinder cabinet is at 28 °C and one segment of the line passes through a 20 °C wall. What happens to the flow? Where would you expect particles on the wafer?

4. A technician runs the standard NF₃/O₂ WAC on a chamber that has just processed 500 plate wafers with no Cl-based clean first. Describe the wall chemistry and the defect trend you would expect over the next two weeks.

5. An ALE finishing step removes 0.10 nm per 4.5 s cycle. How many cycles and how much time are needed to clear 0.8 nm of ZrO₂ with 30% over-cycling? What throughput does a chamber that does only this finishing step achieve?

6. Draw the process flow of the hot route with TiN passivation, and mark at each step what the plate edge looks like.

---

**Next Chapter:** [Chapter 8: Endpoint Detection for Thin-Film & Multilayer Electrode Etch](./08-endpoint-thin-film-multilayer.md)

---

**Chapter 7 Development Status:** Complete  
**Version:** 1.0
