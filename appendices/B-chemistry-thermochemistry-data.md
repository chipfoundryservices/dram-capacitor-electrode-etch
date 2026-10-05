# Appendix B: Chemistry & Thermochemistry Data

Reaction enthalpies, product volatilities, bond energies, rate constants, and emission lines used in the chemistry chapters. Values are rounded literature-class values for illustration; use evaluated data for design work.

---

## B.1 Standard Enthalpies of Formation (kJ/mol, 298 K)

```
Species         ΔH_f        Species          ΔH_f
──────────────────────────────────────────────────────
TiN(s)          −338        BCl₃(g)          −404
TiO₂(s)         −944        B₂O₃(s)          −1274
TiCl₄(g)        −763        SiCl₄(g)         −663
ZrO₂(s)         −1101       GeCl₄(g)         −496
ZrCl₄(s)        −981        WF₆(g)           −1722
ZrCl₄(g)        ≈ −870      AlCl₃(s)         −704
HfO₂(s)         −1145       Al₂O₃(s)         −1676
HfCl₄(s)        −990        Cl₂, F₂, O₂, N₂  0
```

---

## B.2 Key Reactions

```
Reaction                                          ΔH (kJ/mol)   Comment
─────────────────────────────────────────────────────────────────────────────
TiN + 2 Cl₂ → TiCl₄(g) + ½ N₂                     −425          main TiN etch
TiO₂ + 2 Cl₂ → TiCl₄(g) + O₂                      +181          needs getter
TiO₂ + 4/3 BCl₃ → TiCl₄(g) + 2/3 B₂O₃             −130          breakthrough
ZrO₂ + 2 Cl₂ → ZrCl₄(s) + O₂                      +120          does not proceed
ZrO₂ + 4/3 BCl₃ → ZrCl₄(s) + 2/3 B₂O₃             −191          HK step
ZrO₂ + 4/3 BCl₃ → ZrCl₄(g) + 2/3 B₂O₃             ≈ −80         gas-phase product
HfO₂ + 2 Cl₂ → HfCl₄(s) + O₂                      +155
HfO₂ + 4/3 BCl₃ → HfCl₄(s) + 2/3 B₂O₃             −156
Al₂O₃ + 3 Cl₂ → 2 AlCl₃(s) + 3/2 O₂               +267
Al₂O₃ + 2 BCl₃ → 2 AlCl₃(s) + B₂O₃                −198
Si + 2 Cl₂ → SiCl₄(g)                             −663
Ge + 2 Cl₂ → GeCl₄(g)                             −496
W + 3 F₂ → WF₆(g)                                 −1722
BCl₃ + 3 H₂O → B(OH)₃ + 3 HCl                    exothermic    line moisture;
                                                                particles
```

---

## B.3 Volatility of Products

```
Product      Normal b.p. / sub. (°C)   T for ≈ 1 Torr (°C)   p at 25 °C (Torr)
──────────────────────────────────────────────────────────────────────────────
TiCl₄        136                        ≈ −14                 ≈ 10
TiBr₄        230                        ≈ 100                 ≈ 0.01
TiF₄         284 (sub.)                 ≈ 150                 ≪ 10⁻³
SiCl₄        58                         ≈ −63                 ≈ 240
SiBr₄        153                        ≈ 5                   ≈ 4
SiF₄         −86 (sub.)                 —                     gas
GeCl₄        87                         ≈ −45                 ≈ 75
GeBr₄        186                        ≈ 55                  ≈ 0.3
WF₆          17                         —                     gas
WOCl₄        228                        ≈ 100                 ≈ 0.01
WCl₆         347                        ≈ 200                 ≪ 10⁻³
ZrCl₄        331 (sub.)                 ≈ 190                 ≈ 10⁻⁵ (60 °C)
HfCl₄        317 (sub.)                 ≈ 190                 ≈ 10⁻⁵ (60 °C)
ZrF₄, HfF₄   ≈ 900 (sub.)               ≈ 600                 negligible
AlCl₃        180 (sub.)                 ≈ 100                 ≈ 10⁻³
AlF₃         1276 (sub.)                ≈ 1000                negligible
BCl₃         12.5                       —                     gas (1.3 atm at 20 °C)
RuO₄         ≈ 40                       ≈ −10                 ≈ 10
MoF₆         34                         —                     gas
MoOCl₄       ≈ 160                      ≈ 50                  ≈ 0.1
NbCl₅        248                        ≈ 120                 ≪ 10⁻²
NbF₅         234                        ≈ 90                  ≪ 10⁻²
SrCl₂        mp 874, b.p. 1250          —                     negligible
```

---

## B.4 Bond Dissociation Energies (diatomic, kJ/mol)

```
B–O   806       Si–O  798       Hf–O  802       Zr–O  766
Ti–O  672       Al–O  512       Ti–N  ≈ 476     Ti–Cl ≈ 494
Si–Si (crystal) 3.3 eV          Si–Ge 3.1 eV    Ge–Ge 2.8 eV
```

---

## B.5 Ion-Enhanced Yield Constants (Cl₂/Ar-Based Plasma)

```
Y(E) = A (√E − √E_th);   ER = Y Γ_i θ / n

Film     n (cm⁻³)        E_th (eV)    A        θ (typ.)
──────────────────────────────────────────────────────────
TiN      5.1 × 10²²       25           0.053    1.0
SiN      4.4 × 10²²       40           0.012    0.7 (BₓClᵧ)
SiO₂     2.3 × 10²²       50           0.020    0.7

ZrO₂ in BCl₃/Cl₂ (net of deposition D ≈ 1–2 nm/min):
  E_th ≈ 60 eV at 60 °C; ≈ 40 eV at 150 °C; ≈ 25 eV at 250 °C
```

---

## B.6 Reference Rates

```
Step / film                   Rate (nm/min)   Step / film                  Rate (nm/min)
───────────────────────────────────────────────────────────────────────────────────────
SNS BT, TiN                   ≈ 75            SiGe ME, SiGe                180
SNS ME, TiN (blanket)         42              SiGe ME, TiN                 ≈ 22
SNS ME, SiN                   4.7             SiGe ME, resist              60
SNS OE, TiN (blanket)         24              SiGe OE, SiGe                60
SNS OE, TiN (on product)      ≈ 42            SiGe OE, TiN                 1.5
SNS OE, SiN                   1.6             SiGe OE, SiN                 ≈ 1
W, W                          200             HK, ZrO₂ (tetragonal)        6
W, SiGe                       ≈ 300           HK, ZrO₂ (amorphous)         9
W, resist                     150             HK, Al₂O₃                    5
BARC, resist                  150             HK, TiN                      50
                                              HK, SiN                      8
                                              HK, resist                   50
                                              Hot HK (250 °C), ZrO₂        12
                                              Hot HK, SiN                  4
Lateral rates:  TiN (Cl, 60 °C) ≈ 0.5–3; SiGe(0.3) Cl-rich ≈ 5; Ge-rich (0.35) ≈ 8;
                TiN (BCl₃/Cl₂, 250 °C) ≈ 70
```

---

## B.7 Temperature Coefficients (near 60 °C)

```
Mechanism                         dR/dT (%/°C)    E_a
───────────────────────────────────────────────────────
TiN vertical (ion-assisted)       +0.2            —
TiN lateral (spontaneous Cl)      +2.5            ≈ 0.25 eV
SiGe vertical                     +0.3            —
SiGe lateral (Ge)                 +3.0            ≈ 0.3 eV
W vertical                        +0.5            —
ZrO₂ (HK)                         +0.8            —
Sidewall passivation deposition   −1 to −2        —
Cl removal by H (PET)             τ halves per +40 °C   ≈ 0.3 eV
```

---

## B.8 Optical Emission Lines

```
Species   λ (nm)               Use
──────────────────────────────────────────────────────────────────────
N₂        337.1                TiN clearing (falls); SiN onset (rises)
Ti I      399.9, 453.3, 498.2  TiN clearing (falls)
Cl I      725.7, 837.6         Cl density (rises at clearing)
Ar I      750.4, 811.5         actinometer
CO        483.5, 519.8         BARC clearing
W I       400.9, 429.5         W clearing
F I       703.7                W clearing (modest rise)
SiF       ≈ 440                SiGe exposure in SF₆
Si I      288.2                SiGe clearing
SiBr      ≈ 290–300            SiGe clearing in HBr
Ge I      265.1, 303.9         SiGe clearing (UV)
BCl       272                  BCl₃ consumption
Al I      394.4, 396.2         Al₂O₃ marker in ZAZ
Zr I      339.2, 360.1         weak
SiCl      287                  SiN onset in BCl₃
VUV       Cl 134–139; Ar 104.8, 106.7   damage sources (not monitored by
                                         standard OES)
```

---

**Appendix B Version:** 1.0
