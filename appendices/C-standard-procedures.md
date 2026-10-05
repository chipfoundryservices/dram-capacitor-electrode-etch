# Appendix C: Standard Procedures

Step-by-step procedures for qualifying and monitoring the electrode etch modules. Each procedure lists purpose, materials, steps, and acceptance criteria. Values are illustrative.

---

## C.1 SNS Chamber Qualification

**Purpose:** Qualify a storage-node separation chamber after installation or wet clean.

**Materials:** 5 seasoning wafers (blanket TiN on SiN); blanket TiN (18 nm) and PECVD SiN monitor wafers; 3 full-structure wafers (TiN-filled capacitor arrays with VC monitor arrays).

**Steps:**
1. Run the per-wafer WAC, then 5 seasoning wafers through the full recipe (BT, ME, OE).
2. Measure blanket TiN ME and OE rates and SiN OE rate at 49 sites.
3. Run 3 structure wafers. Record BT-to-ME onset, endpoint time, inflection time, and post-endpoint slope.
4. On structure wafers: OCD rim recess and SiN thickness (13 sites); VC inspection on monitor arrays; XPS Ti on periphery pads; TEM at centre and edge (rim, cup, seam groove, rim radius).
5. Compare with the fleet reference.

**Acceptance:**
```
Blanket TiN ME rate within ± 2% of fleet mean; uniformity ≤ 2% (1σ)
SiN OE rate within ± 10% of fleet mean
Endpoint time within ± 3% of fleet mean; post-EP slope within ± 1%/s of flat
Rim recess 7–10 nm at all sites; centre–edge difference ≤ 1.5 nm
Top SiN ≥ 117 nm at all sites
Cup ≤ 12 nm; seam groove ≤ 5 nm (TEM); rim radius ≥ 5 nm
VC shorts within 2× fleet mean; no clustered shorts
```

---

## C.2 Plate Chamber Qualification

**Purpose:** Qualify a plate-etch chamber after installation or wet clean.

**Materials:** Blanket monitors (W, SiGe, TiN, ZrO₂ crystallized, SiN, resist); TXRF monitor wafers with blanket ZAZ on SiN; 3 full-stack plate wafers with scribe test structures.

**Steps:**
1. Run the chlorine-first WAC (Chapter 7) and 5 seasoning wafers with the full five-step recipe.
2. Measure blanket rates for each step film at 49 sites.
3. Run TXRF monitors through the HK step with the production overetch; measure Zr at 5 sites.
4. Run 3 plate wafers. Record each endpoint, the Al-marker time, and SiN-onset time.
5. Measure plate CD (CD-SEM), plate-edge profile (OCD and one cross-section), periphery SiN loss (ellipsometry), remaining resist thickness, and post-strip defects.
6. Compare with the fleet reference.

**Acceptance:**
```
W, SiGe, ZrO₂ blanket rates within ± 3% of fleet mean
Al-marker time within ± 4% of fleet mean
Zr on TXRF monitors ≤ 1 × 10¹³ cm⁻² at all sites (target ≤ 3 × 10¹²)
Periphery SiN loss 2–7 nm; remaining resist ≥ 250 nm
Plate-edge angle 80–88°; foot notch ≤ 5 nm; TiN notch ≤ 8 nm
No veils or Zr-containing flakes in post-strip inspection
```

---

## C.3 Breakthrough Verification After a Queue-Time Excursion

**Purpose:** Decide whether wafers that waited longer than 24 h after the TiN fill can run the standard SNS recipe.

**Steps:**
1. Measure surface oxide on a monitor that waited with the lot (XPS O 1s, Ti 2p).
2. If TiOₓNᵧ ≤ 2.0 nm: run the standard recipe; check BT-to-ME onset on the first wafer.
3. If 2.0–3.0 nm: extend BT from 5 to 8 s; run one wafer; VC and OCD before releasing the lot.
4. If > 3.0 nm: hold for engineering; consider a dilute-HF or SC1-free oxide strip.

**Acceptance:** BT-to-ME onset within 1 s of the fleet reference; VC shorts within the normal band.

---

## C.4 Edge-Ring Life Check

**Purpose:** Set the edge-ring replacement point from product data rather than RF hours alone.

**Steps:**
1. Track OCD rim recess at r = 145 mm and r = 0 on one wafer per lot (module 1); periphery SiN loss at r = 145 mm (module 2).
2. Plot the edge-minus-centre value against RF hours.
3. Adjust ring height (if motorized) when the edge rim recess falls 1.0 nm below the centre, or edge SiN loss falls 1.5 nm below the centre.
4. Replace the ring when the height range is exhausted or when edge VC shorts or edge contact-chain opens rise above 2× baseline.

---

## C.5 Plate-Edge Corrosion Inspection

**Purpose:** Release or re-treat a lot that exceeded the PET → ILD queue time (8 h).

**Steps:**
1. Inspect plate edges on 2 wafers by SEM at 9 sites for W pitting and TiN notch growth.
2. Measure Cl⁻ by ion chromatography on a sacrificial wafer from the lot.
3. If no pitting and TiN notch ≤ 10 nm: re-run H₂/N₂ treatment (20 s); proceed to ILD within 2 h.
4. If pitting or notch > 10 nm: hold; disposition by engineering (plate resistance test, ILD void risk).

---

## C.6 Antenna-Structure Evaluation

**Purpose:** Evaluate plasma-induced damage after a plate-etch recipe or hardware change.

**Steps:**
1. Process 5 wafers with the new condition and 5 with the reference through first metal.
2. Measure leakage at + 1.0 V and − 1.0 V on reference arrays, antenna arrays (10×, 100×, 1000×), late-separation structures, and polarity pairs at 49 sites.
3. Compute the antenna-minus-reference shift per site; map against radius.
4. Ramp-to-breakdown on 20 sacrificial arrays per wafer.

**Acceptance:**
```
Median leakage shift (antenna − reference) ≤ 10% at all antenna ratios
No polarity asymmetry beyond 5%
Breakdown distribution unchanged (two-sample test, p > 0.05)
```

---

## C.7 BCl₃ Cylinder Change

**Purpose:** Replace a BCl₃ cylinder without introducing moisture.

**Steps:**
1. Verify cabinet and line heater set points (cylinder 28 °C; lines ≥ 32 °C).
2. Close the cylinder valve; evacuate and cycle-purge the pigtail with dry N₂ (≥ 20 cycles).
3. Change the cylinder; helium leak-check the connection (≤ 1 × 10⁻⁹ atm·cc/s).
4. Cycle-purge again; open the cylinder; flow to the vent for 10 min.
5. Run a particle monitor wafer and a blanket ZrO₂ rate monitor before production.

**Acceptance:** particle adders within baseline; ZrO₂ rate within ± 3%.

---

**Appendix C Version:** 1.0
