# Appendix D: Process Windows

Reference windows for the electrode etch modules. "Target" is the reference process; "window" is the range within which the specification of Chapter 1 is met with the other parameters at target. All values are illustrative starting points for a design of experiments.

---

## D.1 Storage-Node Separation

```
Parameter                 Target              Window             Limited by
─────────────────────────────────────────────────────────────────────────────────────────
BT time                   5 s                 4–8 s              TiO₂ islands (low) /
                                                                 recess, SiN (high)
BT bias                   200 W (≈ 110 eV)    150–250 W          oxide clearing / SiN
ME Cl₂ / BCl₃             50 / 25 sccm        BCl₃ 15–35         BₓClᵧ masks (high) /
                                                                 cusp protection (low)
ME bias                   120 W (≈ 70 eV)     100–150 W          rate (low) / SiN
                                                                 selectivity (high)
ME pressure               6 mTorr             5–8 mTorr          uniformity
Endpoint                  derivative < 5%     —                  —
                          after inflection
OE time                   10 s                7–14 s             saddles, edge (low) /
                                                                 recess > 15 nm (high)
OE bias                   70 W (≈ 50 eV)      55–90 W            TiO₂ islands (low) /
                                                                 SiN loss (high)
Chuck temperature         60 °C               40–70 °C           seam groove, cup (high)
Fill thickness (input)    18 nm               17–22 nm           cup ≤ 12 nm (low) /
                                                                 ME time (high)
Queue time fill → SNS     ≤ 24 h              ≤ 48 h with BT     surface oxide
                                              extension
PET (H₂/N₂, 200 °C)       30 s                ≥ 20 s             Cl ≤ 1 at%
```

---

## D.2 Plate Etch

```
Parameter                 Target              Window             Limited by
─────────────────────────────────────────────────────────────────────────────────────────
Resist thickness          500 nm              ≥ 450 nm           ≥ 150 nm remaining
BARC open time            20 s                EP + 20%           BARC residue / resist
W overetch                25%                 15–40%             W islands (low) /
                                                                 SiGe loss (high, minor)
SiGe ME Cl₂ fraction      25%                 15–30%             rate (low) / foot notch
                                                                 (high)
SiGe ME O₂/HBr            3%                  2–5%               bowing (low) / grass
                                                                 (high)
SiGe OE time              25 s                20–40 s            SiGe residue (low) /
                                                                 TiN loss (high, minor)
HK bias                   450 W (≈ 150 eV)    350–550 W          deposition transition
                                                                 (low) / SiN, resist (high)
HK Cl₂ fraction           20%                 15–35%             BₓClᵧ (low) / O
                                                                 gettering (high)
HK overetch               50% of Al-marker    45–70%             residue tail (low) /
                          prediction                             notch, SiN, resist (high)
Chuck temperature         60 °C               50–70 °C           ZrO₂ rate (low) / SiGe
                                                                 lateral, TiN notch (high)
Plate overlap (design)    1.5 µm              ≥ 1.0 µm           UV, halogen, wet undercut
Queue time PET → ILD      ≤ 8 h               —                  W corrosion, TiN notch
```

---

## D.3 Hot HK Route (Oxide Hard Mask)

```
Parameter                 Target              Window             Limited by
─────────────────────────────────────────────────────────────────────────────────────────
Chuck temperature         250 °C              200–280 °C         ZrO₂ rate (low) / TiN
                                                                 shell integrity (high)
HK bias                   200 W (≈ 80 eV)     150–300 W          rate / SiN
HK overetch               35%                 30–50%             residue tail / SiN
TiN sidewall shell        O₂ flash 3 s        2–5 s              shell thickness 1–2 nm
Liner temperature         165 °C              150–180 °C         ZrCl₄ condensation
Foreline temperature      150 °C              ≥ 130 °C           AlCl₃, ZrCl₄ deposits
```

---

## D.4 Sensitivities (per unit change, at target)

```
Change                              Rim recess   SiN loss   Notch      Residue risk
──────────────────────────────────────────────────────────────────────────────────────
SNS OE +1 s                         +0.7 nm      +0.03 nm   —          ↓ (saddles, edge)
SNS loading constant k +0.1         +0.25 nm     —          —          —
Fill +1 nm                          0            0          —          cup −0.7 nm
HK OE +10%                          —            +0.8 nm    +0.3 nm    ↓↓ (×10⁻² to 10⁻³)
HK bias −50 W                       —            −0.6 nm    —          ↑ (near transition)
Plate chuck +5 °C                   —            —          +0.5 nm    ↓ (ZrO₂ rate +4%)
                                                            (TiN),
                                                            +15% foot
```

---

**Appendix D Version:** 1.0
