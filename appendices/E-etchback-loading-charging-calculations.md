# Appendix E: Etch-Back, Loading & Charging Calculations

Closed-form models used in this book, with the reference worked example for each. All models are deliberately simple; each lists its main assumptions.

---

## E.1 Retention Budget and Short Resistance (Ch. 1)

```
Q = C_s V_core;   I_max = f_loss Q / t_ref;   R_min = ΔV / I_allowed

Reference: C_s = 8.6 fF, V_core = 1.10 V → Q = 9.5 fC
  f_loss = 0.20, t_ref = 64 ms → I_max ≈ 30 fA
  Allowed for node-to-node path: 10 fA → R_min = 1.10 V / 10 fA = 1.1 × 10¹⁴ Ω

TiN thread R = ρ L / (w t) = 1×10⁻⁵ Ω·m × 13 nm / (5 nm × 1 nm) = 2.6 × 10⁴ Ω
```

---

## E.2 Fill Dimple and Cup (Ch. 2, 10)

```
Surface height at the hole centre after conformal fill t ≥ r:
  h_c = √(t² − r²);   dimple depth = t − √(t² − r²)

  t = 18, r = 16 nm:  h_c = 8.2 nm;  dimple = 9.8 nm
  t = 24, r = 16 nm:  dimple = 6.1 nm
  t = 15, r = 13 nm:  dimple = 7.5 nm (1d-class)

Anisotropic etch-back: cup depth = dimple depth
Cusp deepening by an isotropic component e_s at half-angle α:
  Δd = e_s (1/sin α − 1)
Wall saddle: narrowest nearest-neighbour wall at the surface
  w_s = pitch − CD − 2 w_f   (w_f = flare width per side)
  45 − 32 − 2 × 4 = 5 nm → saddle ≈ 3 nm below the triangular nodes;
  saddle deepens (≈ 6 nm) as w_s → 0 (large CD, deep facet)
  Minimum rim recess = deepest saddle on the wafer
```

---

## E.3 Ion Flux, Ion Energy, and Yield (Ch. 3, 5)

```
Γ_i = 0.61 n_e u_B;  u_B = √(kT_e/M_i)
  n_e = 1.5 × 10¹¹ cm⁻³, T_e = 3.5 eV, M = 71 amu → u_B = 2.2 km/s
  Γ_i = 2.0 × 10¹⁶ cm⁻² s⁻¹;  J_i = 3.2 mA/cm²;  I_i(300 mm) = 2.3 A

E_i ≈ e(V_p + P_bias / I_i):  120 W / 2.3 A = 52 V; + 15 V → ≈ 70 eV

Y = A(√E − √E_th);  ER = Y Γ_i θ / n
  TiN at 70 eV: Y = 0.053 × (8.37 − 5.00) = 0.18 → ER = 0.70 nm/s = 42 nm/min
```

---

## E.4 Loading and the Rate Jump (Ch. 3, 8)

```
ER(θ_A) = ER_max / (1 + k θ_A);   k = k_r A_wafer / (k_p + k_w)

Pillar-top fraction after clearing: θ_A = (π × 16² / 1734) × 0.45 = 0.21
Rate jump = (1 + k) / (1 + k θ_A) = 2.2 / 1.25 = 1.76  (k = 1.2)

OES change at clearing:
  product signal ∝ θ_A × jump = 0.21 × 1.76 = 0.37
  Cl signal ∝ jump = 1.76;   Cl/N₂ ratio ≈ 1.76 / 0.37 ≈ 4.7
```

---

## E.5 Clearing-Time Spread and Rim Recess (Ch. 6, 10)

```
σ_tc / t_c = √((σ_t/t)² + (σ_R/R)²)
  5% and 3% (3σ) → 5.8% → ± 1.33 s on 22.9 s

recess(r) = (t_EP − t_c(r)) R_ME,loaded + t_OE R_OE,loaded
  R_ME,loaded ≈ 1.0 nm/s;  R_OE,loaded = 0.40 × 1.76 = 0.70 nm/s
  fastest site:  (24.5 − 21.6) × 1.0 + 10 × 0.70 = 9.9 nm
  slowest site:  (24.5 − 24.2) × 1.0 + 10 × 0.70 = 7.3 nm

Gaussian margin at the slowest 3σ site: 3σ + 7.3 nm / 0.45 nm ≈ 19σ
```

---

## E.6 Seam Groove (Ch. 10)

```
d_seam = (f − 1) e_v,exposed
  e_v ≈ 2 (BT) + 14 (ME) + 7 (OE, loaded) ≈ 23 nm
  f = 1.15 → 3.5 nm;   f = 1.5 → 11 nm
```

---

## E.7 Grain-Tail Overetch (Ch. 4, 16)

```
P(grain left) = ½ erfc(z/√2);   z = OE / σ_g

Grains under periphery contacts: 3 × 10⁷ contacts × 4 grains = 1.2 × 10⁸ per die
Target 0.01 affected contacts per die → P < 8 × 10⁻¹¹ → z ≥ 6.4
  σ_g = 8% → OE ≥ 51%
At OE = 50%: z = 6.25, P = 2 × 10⁻¹⁰ → ≈ 0.024 affected contacts per die
At OE = 60%: z = 7.5,  P = 3 × 10⁻¹⁴ → ≈ 4 × 10⁻⁶ per die

Yield: Y = exp(−N_contacts × P_open);  P_open = 4 × P(grain left)
```

---

## E.8 Plate Charging (Ch. 13)

```
Antenna ratio (phase A):  A_ant / A_diel = (0.45 × 707) / 1.8×10⁴ = 0.017

Dielectric leakage: J(V) = J₁ exp((V − 1.0)/V₀)
  J₁ = 8 × 10⁻⁷ A/cm² (1 fA per 1.24 × 10⁻⁹ cm² cell), V₀ = 0.12 V
  Total I(V) = J(V) × 1.8 × 10⁴ cm²
  I = 0.2 A at V ≈ 1.3 V   → clamp, given ≈ 0.1–0.3 A available net current

Injected charge: Q = J t ≈ 1 × 10⁻⁵ A/cm² × 100 s = 1 × 10⁻³ C/cm²
  vs Q_bd ≈ 0.5–5 C/cm² → 0.02–0.2%

Phase C antenna (isolated island):
  sidewall 4.6 mm × 200 nm = 9 × 10⁻⁴ cm²;  dielectric 0.67 cm² → 1.4 × 10⁻³

Polarity: plate negative → node junction forward-biased → full ΔV on dielectric
```

---

## E.9 Rim Field Enhancement (Ch. 11)

```
E_edge / E_flat = t / (r ln(1 + t/r))     (cylindrical edge, dielectric t)
  t = 5.5 nm:  r = 2 → 2.1;  r = 5 → 1.5;  r = 10 → 1.25
```

---

## E.10 Wafer Bow (Ch. 6)

```
κ = 6 σ_f t_f / (M_s t_s²);  b = κ r² / 2
  W strap 1.0 GPa × 40 nm; M_s = 180 GPa; t_s = 775 µm
  κ = 2.2 × 10⁻³ m⁻¹;  b(150 mm) = 25 µm
```

---

## E.11 Post-Etch Treatment Kinetics (Ch. 11)

```
[Cl](t) = [Cl]₀ exp(−t/τ);  τ ≈ 10 s at 200 °C;  τ ×2 per −40 °C
  5 → 1 at%: t = τ ln 5 = 16 s
```

---

## E.12 Residence Time (Ch. 5)

```
τ = pV/Q;  1 sccm = 0.0127 Torr·L/s
  40 L, 8 mTorr, 200 sccm → τ = 0.32 / 2.53 = 0.13 s
```

---

## E.13 Resist Budget and Pull-Back (Ch. 12)

```
Loss = Σ (step time × resist rate) = 50 + 38 + 47 + 8 + 75 = 218 nm
Remaining = 500 − 218 = 282 nm (≥ 150 nm required)
Lateral pull-back ≈ 0.15 × 218 = 33 nm per edge → CD −65 nm
```

---

## E.14 Particle-Masked Short Clusters (Ch. 9)

```
Pillars masked by a particle of diameter D: N = 577 µm⁻² × π D² / 4
  D = 100 nm → 4.5;  200 nm → 18;  500 nm → 113
```

---

## E.15 Equipment and Cost (Ch. 16)

```
Mainframes = wafer rate / (throughput × availability)
  139 wph / (100 × 0.85) = 1.6 → 2 (module 1)
  139 wph / (50 × 0.85) = 3.3 → 4 (module 2)

Depreciation per wafer = (capex / years) / (wph × 8760 × availability)
  $10 M / 5 / (100 × 8760 × 0.85) = $2.70  (module 1)
  $14 M / 5 / (50 × 8760 × 0.85) = $7.50   (module 2)

Value of 1% yield ≈ 0.01 × 860 die × $3 ≈ $26 per wafer
```

---

**Appendix E Version:** 1.0
