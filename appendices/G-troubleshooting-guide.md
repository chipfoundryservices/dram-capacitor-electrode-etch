# Appendix G: Troubleshooting Guide

Symptom-driven guide for DRAM capacitor electrode etch excursions. For each symptom: likely causes ranked from most to least common, checks to separate them, and corrective actions. Chapter references point to the underlying physics.

---

## G.1 Node-Pair Shorts Up (Whole Wafer, Random)

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Surface oxide: long fill → SNS queue    Queue-time log; BT-to-ME onset;     Enforce ≤ 24 h; extend
   (TiO₂ islands) (Ch. 3.2.3, 10.4)        XPS O on monitor                    BT (App. C.3)
2. BT step weakened (bias drift, gas)      BT V_pp log; blanket TiOₓ removal   Restore BT; V_pp
   (Ch. 3.2.3, 5.3)                        rate                                control
3. BₓClᵧ micromasking (BCl₃ flow high,     MFC log; SEM of residue at short    Restore BCl₃; add Cl₂
   wall state) (Ch. 10.4)                  sites                               finish
4. Pits in top SiN from the hole-etch      TEM at short sites; hole-etch       Feed back to hole etch
   strip (Ch. 10.4.3)                      strip change log                    / strip
```

## G.2 Node-Pair Shorts at the Wafer Edge (Rings)

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Edge-ring wear (late edge clearing)     RF hours; post-EP slope; edge OCD   Raise ring / replace;
   (Ch. 6.4, 8.3.4)                        rim recess                          edge zone offset
2. Deeper wall saddles at the edge (top    Hole-etch edge top CD; TEM saddle   Raise OE (within 14 s);
   CD, facet) (Ch. 2.1.2, 10.2.3)          depth at edge                       feed back to hole etch
3. Fill thicker at the edge                Fill radial profile (XRF)           Feed-forward radial
   (Ch. 6.1.3)                                                                 rate tilt
```

## G.3 Cluster Shorts (5–100 Cells)

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Particles on the field before or        Particle monitors; SEM at cluster   Wet clean; check WAC;
   during SNS (Ch. 9.5.1)                  centre (composition)                transfer-module clean
2. Wall flakes (RF hours since wet         Flake composition (Ti, B)           Shorten wet-clean
   clean)                                                                      interval
3. BCl₃ hydrolysis particles (line         Boron in particles; cylinder        Leak check; purge
   moisture) (Ch. 7.5.2)                   change log                          (App. C.7)
```

## G.4 Rim Recess Out of Range

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
Too deep (> 12 nm):
1. Loading constant up (wall seasoned      ME rate on blanket vs product;      Re-season; EWMA will
   differently; fewer exposed TiN areas)   WAC clear time                      reduce OE
   (Ch. 3.4, 9.1)
2. EP late (window clouding, wall          OES line levels; reflectometer vs   Clean window; EP on
   emission) (Ch. 8.8)                     OES disagreement                    alternate line
Too shallow (< 6 nm):
1. OE shortened by EWMA after a bad        EWMA history; OCD model version     Reset loop; update OCD
   measurement / OCD model change                                              model
2. OE energy low (bias drift)              V_pp log                            Restore
```

## G.5 Cup Deep or Seam Grooves Open

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Fill thinner (dimple deeper)            Fill thickness; dimple model        Restore fill; adjust
   (Ch. 2.1.4, 10.3.1)                                                         OCD model
2. Seam Cl-rich / poorly closed (fill      TEM seam; fill pulse log            Feed back to CVD
   recipe) (Ch. 10.3.4)
3. Isotropic component up (chuck hot,      Chuck T log; lateral rate monitor   Restore T; add BCl₃ or
   Cl atom fraction high) (Ch. 10.3.3)                                         N₂ for cusp protection
```

## G.6 Retention Tail Worse After Module 1 Change

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Rim radius sharper (OE energy, PET)     TEM rim radius (≥ 5 nm)             Restore OE; verify PET
   (Ch. 11.3.3)
2. Cl at pillar tops / seam (PET short,    XPS Cl on monitor; PET log; air     Restore PET; vacuum
   air exposure before PET) (Ch. 11.2)     break events                        transfer
3. Metal contamination (Fe, Ni, Cu)        TXRF / VPD-ICPMS; gas line          Replace line / purifier
   (Ch. 9.4)                               moisture
```

## G.7 Periphery Contact Opens (ZrO₂ Residue)

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. HK overetch margin lost at the edge     Edge SiN loss; ring RF hours;       Ring height / replace;
   (ring) (Ch. 6.4, 12.6)                  contact-chain radial map            edge zone +3–5 °C
2. ZrO₂ rate drift (wall, bias)            Al-marker time trend; blanket       Re-season; confirm OE
   (Ch. 4.3, 8.5.4)                        ZrO₂ rate                           follows Al marker
3. Al marker not detected → timed step     EP logs                             Restore marker line;
   (Ch. 8.8)                                                                   window clean
4. ZAZ more crystalline (SiGe furnace      Furnace position; XRD               Increase OE to 60%
   change) (Ch. 2.3.2, 4.4.3)                                                  (App. D)
5. Veils / Zr flakes (Ch. 12.7)            Post-strip inspection; flake EDX    Raise late Cl₂; strip
                                                                               sequence; megasonic
```

## G.8 Plate-Edge Profile Problems

```
Symptom / cause                            Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
SiGe bow at top: F memory (Ch. 9.1.3)      WAC final Cl₂ step present?         Add/extend Cl₂ reset
Foot notch: Ge-rich bottom; high Cl₂ in    SIMS Ge profile; ME Cl₂ MFC         Lower Cl₂ at end of
ME (Ch. 12.4)                                                                  ME; chuck −5 °C
TiN notch > 10 nm: long HK; hot chuck;     HK time; chuck T; queue PET → ILD   Restore; enforce 8 h
corrosion (Ch. 12.5, 11.5)
SiGe pips: W islands (Ch. 3.6)             W EP time; W OE; W grain size       Extend W OE to 30%
Footing / ZAZ foot: HK under-etch at       HK time vs Al marker                Confirm OE fraction
the edge
```

## G.9 Cell Leakage Shift After Plate Etch (Antenna Arrays)

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Plasma non-uniformity (coil, gas)       Radial ring in leakage map;         Re-tune coil ratio;
   → phase-A charging (Ch. 13.3)           polarity pairs                      pulse source/bias
2. Slow, uneven TiN clearing in HK         Bank-level pattern; late-           Ensure uniform SiGe OE;
   → phase-B transients (Ch. 13.4)         separation structure                HK TiN rate
3. ESC sequence change (voltage steps      Recipe/sequence log                 Restore sequence
   with plasma on) (Ch. 6.6)
4. Plate overlap reduced (layout)          Edge-proximity arrays               Restore ≥ 1 µm
   (Ch. 13.6, 13.7)
```

## G.10 Plate Resistance High

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. W corrosion (queue PET → ILD)           Queue log; SEM pitting (App. C.5)   Re-treat; enforce 8 h
2. W thinned via resist pinholes in HK     Remaining resist; HK time           Raise resist / reduce
   (Ch. 12.2)                                                                  HK time
3. W deposition change                     R_s on blanket monitors             Feed back to PVD
```

## G.11 First-Wafer Effect / Lot-Start Drift

```
Likely causes                              Checks                              Actions
─────────────────────────────────────────────────────────────────────────────────────────────
1. Idle > 2 h without season (Ch. 9.2.3)   Idle log; EP time of wafer 1        Season rule
2. WAC leaves fluorinated or bare wall     WAC recipe; final Cl₂ step          Restore WAC sequence
   (Ch. 9.3.1)
3. B on the wall slows next W step         W EP time wafer 1 vs 2              Extend NF₃/O₂ step
   (Ch. 9.3)
```

---

**Appendix G Version:** 1.0
