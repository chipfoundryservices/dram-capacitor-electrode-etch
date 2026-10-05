# Index: Book #32 Navigation Guide

## Quick Navigation

**Total Content:** 16 chapters + 7 appendices + glossary  
**Estimated Read Time:** 20–28 hours for the complete book; 5–9 hours for a focused reading path

| Part | Chapters | Theme |
|------|----------|-------|
| I | 1–4 | Fundamentals: the two electrodes, the electrode stack, TiN/SiGe/W chemistry, high-k chemistry |
| II | 5–9 | Hardware: ICP conductor chambers, chucks and uniformity, high-k chambers, endpoint, walls and contamination |
| III | 10–14 | Phenomena: node separation, electrode surface chemistry, plate patterning, dielectric damage, advanced schemes |
| IV | 15–16 | Production: metrology, inspection, APC, integration, yield, cost |

---

## Part I: Fundamentals (Chapters 1–4)

### Chapter 1: [The Capacitor Electrodes & Why They Are Etched](./chapters/01-capacitor-electrodes-role.md)
**Estimated Time:** 55 min | **Difficulty:** Foundation | **Reading Level:** All roles  
**Focus:** Why must each electrode be cut, and what must each cut deliver?

**Key Topics:**
- Private storage node vs shared cell plate
- Retention budget (≈ 30 fA) and R_min ≈ 10¹⁴ Ω; a TiN thread is 2.6 × 10⁴ Ω
- Etch-back vs CMP; the four-film plate stack
- ZrF₄ non-volatility and periphery contact opens; the specification sheet

**Critical Equations:** ΔV_BL = (V_core/2)·C_s/(C_s + C_BL); I_max = f·Q/t_ref; R = ρL/(wt)  
**Study Questions:** 6

---

### Chapter 2: [The Electrode Stack — Fill, Dielectric, Top Electrode & Plate](./chapters/02-electrode-stack-films.md)
**Estimated Time:** 60 min | **Difficulty:** Intermediate | **Reading Level:** Process/Integration  
**Focus:** What do the two etches inherit?

**Key Topics:**
- Top SiN 122 nm; hole-top flare and wall saddles (3–6 nm)
- TiN fill 18 nm; dimple 9.8 nm; surface oxide 1–2 nm
- ZAZ crystallization; top TiN 5 nm; SiGe Ge/B profile; W strap
- Plate R_s 3.6 Ω/□; plate layout and mask; incoming variation

**Critical Equations:** h_c = √(t² − r²); R_s = ρ/t  
**Study Questions:** 6

---

### Chapter 3: [Plasma Chemistry of TiN, SiGe & W Etching](./chapters/03-tin-sige-w-plasma-chemistry.md)
**Estimated Time:** 65 min | **Difficulty:** Advanced | **Reading Level:** Process/Research  
**Focus:** Which halogen for which film, and how do energy and loading set rate and selectivity?

**Key Topics:**
- Product volatility; TiN, TiO₂ thermochemistry; BCl₃ breakthrough
- Yield model; TiN:SiN 9 at 70 eV, 15 at 50 eV
- Loading k = 1.2; rate jump 1.76 at field clearing
- SiGe lateral etch vs Ge and B; HBr/O₂ stop on TiN; W in SF₆/N₂/Cl₂

**Critical Equations:** Y = A(√E − √E_th); ER = YΓθ/n; ER = ER_max/(1 + kθ_A)  
**Study Questions:** 6

---

### Chapter 4: [Etching High-k Dielectrics — ZrO₂, Al₂O₃ & HfO₂](./chapters/04-high-k-dielectric-etch-chemistry.md)
**Estimated Time:** 65 min | **Difficulty:** Advanced | **Reading Level:** Process/Research  
**Focus:** How is ZAZ removed completely from the periphery?

**Key Topics:**
- Bond energies; chloride vs fluoride volatility
- BCl₃ oxygen gettering; etch–deposition transition ≈ 60 eV
- Crystalline ZrO₂ 6 nm/min; ZrO₂:SiN 0.75; temperature
- Grain-tail model: OE ≥ 51%; wet, hybrid, ALE

**Critical Equations:** Net = YΓ/n − D; P = ½erfc(z/√2), z = OE/σ_g  
**Study Questions:** 6

---

## Part II: Hardware Design (Chapters 5–9)

### Chapter 5: [Inductively Coupled Conductor Etch Chambers](./chapters/05-conductor-etch-chambers.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Equipment/Process  
**Key Topics:** ICP vs CCP; Bohm flux 2 × 10¹⁶ cm⁻²s⁻¹; E_i ≈ V_p + P_bias/I_i; voltage control; IEDF tails; pulsing; gas switching; Y₂O₃ and BCl₃; throughput 36 and 13 wph  
**Critical Equations:** Γ_i = 0.61 n_e u_B; τ = pV/Q  
**Study Questions:** 6

### Chapter 6: [Electrostatic Chucks, Temperature & Etch-Back Uniformity](./chapters/06-chuck-temperature-etchback-uniformity.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Equipment/Process  
**Key Topics:** Clearing spread ± 1.33 s; rim recess 7.3–9.9 nm; profile matching; temperature coefficients; edge ring; W bow 25 µm; capacitors follow the chuck  
**Critical Equations:** σ_tc/t_c = √((σ_t/t)² + (σ_R/R)²); κ = 6σ_f t_f/(M_s t_s²)  
**Study Questions:** 6

### Chapter 7: [High-Temperature & Halide Chambers for High-k Removal](./chapters/07-high-k-halide-chambers.md)
**Estimated Time:** 50 min | **Difficulty:** Advanced | **Reading Level:** Equipment/Integration  
**Key Topics:** Hot chuck 250 °C; ZrO₂:SiN 3; oxide HM route; TiN lateral ×24 and the TiN shell; hot walls; BCl₃ delivery; chlorine-before-fluorine WAC; foreline; ALE hardware; four routes  
**Study Questions:** 6

### Chapter 8: [Endpoint Detection for Thin-Film & Multilayer Electrode Etch](./chapters/08-endpoint-thin-film-multilayer.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Equipment/Process  
**Key Topics:** Lines and actinometry; Cl/N₂ × 4.7 at clearing; trace = clearing distribution; 0.5% detection floor; reflectometry; four plate endpoints; Al marker; RF signals; failure modes  
**Critical Equations:** I ∝ n_X n_e k(T_e); F(t) = ½[1 + erf((t − t̄)/σ√2)]  
**Study Questions:** 6

### Chapter 9: [Chamber Walls, Seasoning, Metal Contamination & Defects](./chapters/09-chamber-walls-contamination-defects.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Equipment/Facilities  
**Key Topics:** Wall recombination and n_Cl; first-wafer effect; Ti and Zr clean chemistry; plate-chamber memories; Fe/Ni/Cu limits; particle-masked clusters; bevel and arcing; wall monitors  
**Study Questions:** 6

---

## Part III: Process Phenomena (Chapters 10–14)

### Chapter 10: [Node Separation — Field Clearing, Pillar Recess, Seam Opening & Shorts](./chapters/10-node-separation-recess-shorts.md)
**Estimated Time:** 75 min | **Difficulty:** Advanced | **Reading Level:** Process/Integration/Research  
**Focus:** Where do shorts come from, and what does the overetch buy?

**Key Topics:**
- The last TiN is on the wall tops
- Rim recess budget; a third from loading
- Cup = fill dimple; cusp deepening; seam groove 3.5–11 nm
- 19σ Gaussian margin vs non-Gaussian mechanisms; short Pareto; etch-back vs CMP

**Critical Equations:** recess = (t_EP − t_c)R_ME + t_OE R_OE; Δd = e_s(1/sin α − 1); d_seam = (f − 1)e_v  
**Study Questions:** 6

### Chapter 11: [Electrode Surface Chemistry — Chlorine, Oxidation & Corrosion](./chapters/11-electrode-surface-chlorine-corrosion.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Device/Process  
**Key Topics:** Cl 3–6 at% in TiN tops; PET kinetics τ ≈ 10 s; pillar tops = 0.65% of area; rim field enhancement; interface factors; plate-edge corrosion; queue times  
**Critical Equations:** [Cl] = [Cl]₀e^(−t/τ); E_edge/E_flat = t/(r ln(1 + t/r))  
**Study Questions:** 6

### Chapter 12: [Plate Patterning — Profile, Notching, High-k Residue & Periphery Landing](./chapters/12-plate-patterning-profile-residue.md)
**Estimated Time:** 55 min | **Difficulty:** Intermediate | **Reading Level:** Process/Integration  
**Key Topics:** Five-step recipe; resist budget 218 nm; CD pull-back; profile by layer; foot notch; TiN notch 4 nm; residue locations; veils; periphery SiN; hard-mask route; failure modes  
**Study Questions:** 6

### Chapter 13: [Plasma-Induced Damage to the Capacitor Dielectric](./chapters/13-plasma-induced-dielectric-damage.md)
**Estimated Time:** 60 min | **Difficulty:** Advanced | **Reading Level:** Device/Research  
**Focus:** How can a dielectric under the plate be damaged by the plasma above it?

**Key Topics:**
- Plate → ZAZ → node → junction → substrate circuit; negative-plate polarity
- Antenna ratio 0.017; leakage clamp ≈ 1.3 V; Q_inj ≈ 10⁻³ C/cm²
- Separation transients; isolated islands
- VUV and halogens confined to the plate edge; test structures; mitigation

**Critical Equations:** J(V) = J₁ exp((V − 1)/V₀); AR = A_ant/A_diel  
**Study Questions:** 6

### Chapter 14: [Advanced Schemes — Cylinder Electrodes, ALE, New Metals, 4F² & 3D DRAM](./chapters/14-advanced-electrode-schemes.md)
**Estimated Time:** 50 min | **Difficulty:** Advanced | **Reading Level:** Integration/Research  
**Key Topics:** Sacrificial-fill cylinders; TiN ALE without loading; Ru/Mo/NbN; TiO₂ and SrTiO₃; 1d-class and 4F² constraints; lateral TiN recess in 3D DRAM  
**Study Questions:** 6

---

## Part IV: Production Scale (Chapters 15–16)

### Chapter 15: [Metrology, Inspection & Advanced Process Control](./chapters/15-metrology-inspection-apc.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Process/Metrology  
**Key Topics:** Measurement map; VC reach; node combs; OCD for recess; TXRF vs contact chains; feed-forward; EWMA on OE; fault detection; virtual metrology; sampling  
**Study Questions:** 6

### Chapter 16: [Integration, Yield & Cost of Ownership](./chapters/16-integration-yield-coo.md)
**Estimated Time:** 50 min | **Difficulty:** Intermediate | **Reading Level:** Integration/Management  
**Key Topics:** Hand-offs to Book #30 and to the back-end; yield signatures; equipment sizing; etch-back ≈ $4 vs CMP ≈ $8; plate etch ≈ $11; value of HK overetch; decisions and checklist  
**Critical Equations:** Y = exp(−N·P_open)  
**Study Questions:** 6

---

## Appendices

- [Appendix A: Material Properties](./appendices/A-material-properties.md)
- [Appendix B: Chemistry & Thermochemistry Data](./appendices/B-chemistry-thermochemistry-data.md)
- [Appendix C: Standard Procedures](./appendices/C-standard-procedures.md)
- [Appendix D: Process Windows](./appendices/D-process-windows.md)
- [Appendix E: Etch-Back, Loading & Charging Calculations](./appendices/E-etchback-loading-charging-calculations.md)
- [Appendix F: Metrology Reference](./appendices/F-metrology-reference.md)
- [Appendix G: Troubleshooting Guide](./appendices/G-troubleshooting-guide.md)
- [Glossary](./GLOSSARY.md)

---

## Reading Paths by Role

**Process Engineer (8 h):** Ch. 1 → 2 → 3 → 4 → 10 → 12 → App. D, G  
**Equipment Engineer (7 h):** Ch. 1 → 5 → 6 → 7 → 8 → 9 → 15  
**Integration Engineer (8 h):** Ch. 1 → 2 → 10 → 12 → 14 → 16  
**Device Engineer (5 h):** Ch. 1 → 11 → 13 → 16  
**Researcher (8 h):** Ch. 3 → 4 → 10 → 13 → 14 → App. E

---

## Study Questions Overview

**Total Study Questions:** 96 (6 per chapter × 16 chapters)  
**Nature:** Mostly calculation-based  
**Topics:** Retention and short resistance, fill dimples and saddles, plate sheet resistance, ion yield and selectivity, loading jumps, high-k thermochemistry and clearing statistics, ion flux and bias, clearing spread and recess, bow, BCl₃ delivery, endpoint transitions, wall recombination, particle clusters, seam grooves, PET kinetics, rim field enhancement, resist budget, charging clamps, ALE recess, sampling statistics, EWMA control, equipment counts, cost

Examples:
- Compute the minimum leakage-path resistance from the retention budget
- Compute the dimple depth for a new fill or top CD
- Predict the rate jump and the OES change at field clearing
- Find the high-k overetch for a target contact-open rate
- Estimate the rim-recess range from thickness and rate uniformity
- Size a TiN notch for a hot HK step
- Design the Al-marker endpoint for a new ZAZ
- Count pillars shorted by a particle
- Compute the dielectric clamp voltage for a new antenna ratio
- Run the EWMA overetch loop for three lots
- Size the equipment for 150,000 wafer starts per month

---

## How to Use This Index

1. **First time?** Read PREFACE.md, then this INDEX, then Chapter 1.
2. **Focused reading?** Pick your role from the reading paths above.
3. **Reference mode?** Jump to the chapter. Use Appendix G for symptoms and Appendix E for formulas.
4. **Deep dive?** Read Chapters 1–16 in order and work the study questions.

---

**Index Version:** 1.0  
**Last Updated:** 2026-10-05  
**Next:** Begin [Chapter 1: The Capacitor Electrodes & Why They Are Etched](./chapters/01-capacitor-electrodes-role.md)
