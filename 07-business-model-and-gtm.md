# 07 — Business Model & Go-To-Market

## 1. Answering your own hardest question

> *"Who pays, if it isn't clinically proven and most of it can be Google-searched with AI mode?"*

This objection is correct and it kills the information product. It does **not** kill these four:

1. **Workflow** — people pay to save time and to look competent in front of a patient. A frontier
   LLM does not produce a printable, coded, branded treatment plan inside a clinic's workflow.
2. **Liability transfer / risk reduction** — a pharmacist or clinic buys a checked, sourced,
   audit-logged answer precisely because a chatbot answer is not defensible in an incident review.
3. **Distribution margin** — the money in this industry is in *dispensing*, not advising.
4. **Regulatory evidence work** — manufacturers pay for dossiers because a regulator demands them.

**All four are things an LLM cannot substitute for. None of them require you to be "clinically
proven" on day one.** That's the whole strategic insight.

## 2. The proof point to put in front of your co-founder, Yosin

**Fullscript**: practitioner-mediated supplement dispensing + treatment-plan workflow in the US/Canada.
Reported ~**USD 1B** trailing revenue, **100,000+** providers, 10M+ patients, and it acquired **Rupa
Health** (practitioner lab-test ordering) to complete the loop — labs in, plan out, product shipped.

Read across to your venture:
- The business is the **channel**, not the advice.
- The buyer is the **practitioner**, not the patient.
- **Nothing in that model required proving that any supplement works.** It required making it easy,
  safe and profitable for practitioners to prescribe and for patients to receive.
- **The ASEAN version does not exist.** That is your opening: a Fullscript-shaped company for TCM /
  Jamu / Ayurveda across SG-MY-ID, with a safety and evidence layer localised to ASEAN products and
  ASEAN regulators — the part Fullscript could not copy quickly even if it wanted to.

## 3. Revenue models, ranked

| # | Model | Payer | Realistic price | Timing | Verdict |
|---|---|---|---|---|---|
| 1 | **Dispensary / marketplace take-rate** on herbs & supplements ordered through the plan | Patient pays; practitioner earns; you take 8–20% GMV | GMV-linked | Month 6+ | **Primary engine** |
| 2 | **Practitioner SaaS** — intake, four-lens plan, safety check, TM2 coding, multilingual export | Practitioner/clinic | SGD 40–120 /user/mo (start lower; bundle free with dispensing) | Month 3+ | **Beachhead wedge** |
| 3 | **Safety/interaction API + EMR plugin** | Hospitals, retail pharmacy chains, telehealth apps, insurers | Per-seat or per-call; SGD 15–40k/yr pilots | Month 9+ | **Highest-credibility revenue** |
| 4 | **Manufacturer services** — evidence dossiers, interaction data for labels, BPOM Jamu→OHT→Fitofarmaka support, pharmacovigilance | Herbal/supplement manufacturers | Project fees USD 10–60k | Month 6+ | **Fastest cash, under-considered** |
| 5 | **Data / registry** — de-identified real-world TM outcomes | Manufacturers, researchers, ministries, WHO ecosystem | Licence/grant | Year 2+ | **Long-term moat** |
| 6 | **Consumer subscription** | Patients | — | — | **Do not build** |

Note the structure: **2 acquires, 1 monetises, 3 legitimises, 4 funds the build, 5 defends.**

## 4. Go-to-market motion (beachhead: SG + MY practitioners)

**Phase 0 — Design partners (months 0–3), unpaid**
- Recruit 5–10 clinics: registered TCM physicians, integrative GPs, one hospital pharmacist.
- Give them the safety checker free. Instrument every use and every override.
- Ask for one thing in return: structured outcome capture on their patients.

**Phase 1 — Paid pilot (months 3–9)**
- Convert 20–40 practitioners to paid SaaS, or to free-SaaS-with-dispensing.
- Add the dispensary with 2–3 vetted suppliers (verified registration numbers, COAs, heavy-metal and
  BKO screening — the vetting *is* the product).
- Publish the expert-panel concordance study (`04 §5`). Present at a TCM association meeting.

**Phase 2 — Institutional (months 9–24)**
- Sell the interaction/safety API into hospital pharmacy and retail pharmacy chains — framed as
  *"your patients are already taking these and you can't see it"*, never as *"buy our TCM engine"*.
- Begin HSA registration for the clinician CDS product.
- Indonesia entry via a jamu manufacturer partnership (model 4 funds the market entry).

**Channels that work here:** professional association CPD/CE sessions, TCM college partnerships,
supplier co-marketing, and clinic-owner word of mouth. Paid digital acquisition does not work for
this audience — do not budget for it.

## 5. Unit economics sketch (illustrative — replace with your own interview data)

```
Practitioner cohort assumptions
  Paying practitioners (yr 1 target)         120
  SaaS ARPU                                  SGD 60/mo   → SGD 86k ARR
  Patients per practitioner per month         60
  Attach rate to dispensary                   25%
  Average order value                        SGD 85
  Orders per attached patient per month       0.8
  → GMV/practitioner/month = 60 × .25 × .8 × 85 ≈ SGD 1,020
  → GMV (120 practitioners)                  ≈ SGD 1.47M/yr
  → Take rate 12%                            ≈ SGD 176k/yr
  Total yr-1 revenue                         ≈ SGD 260k
```

- Dispensing revenue exceeds SaaS revenue by roughly 2:1 — **which is why the SaaS should probably be
  free or near-free to drive attachment.** Charging SGD 60/mo to gate a channel worth SGD 1,020/mo of
  GMV is the classic mistake in this category.
- Cost side: 2 founders + 0.5 FTE clinical curator + paid data licences (budget USD 15–40k/yr for
  NatMed/Stockley's-class sources) + cloud. Runway need for 18 months: roughly USD 250–400k.
- **Conclusion: this is seed-fundable or even bootstrappable to first revenue. The hospital-and-
  clinical-trials version is not.**

## 6. Fundraising positioning

Investors will pattern-match "TCM + AI" to wellness fluff within ten seconds. Defuse that in the
first slide:

- Lead with **"Traditional-medicine safety and distribution infrastructure for Southeast Asia."**
  Not "AI for holistic health."
- Lead with the **harm data**: the ~2× mortality signal from treatment refusal (JAMA Oncol 2018),
  BPOM's BKO adulteration findings, heavy metals in marketed Ayurvedic products. That reframes you
  from wellness-optimist to safety-realist, which is the only credible posture here.
- Lead with **"why now"**: WHO TM Strategy 2025–2034 adopted at WHA78 (May 2025); ICD-11 Chapter 26
  TM2 dual coding rolling out with an active national programme in India; Malaysia's T&CM
  practitioner register operational since 2021. Regulation is *creating* the buyer.
- Show **Fullscript's ~USD 1B** as the comparable, then the ASEAN gap.
- Show your **golden-case-set evaluation numbers**, not a demo. You are the founder who can do this;
  it is your differentiation as a team.

**Likely investor set:** ASEAN healthtech and generalist seed funds (SG/ID/MY), regional strategic
investors (pharmacy retail chains, insurers, jamu/herbal manufacturers — a strategic angel from that
industry is worth more than money), plus non-dilutive options: Enterprise Singapore grants, health
innovation grants, and WHO/TM-ecosystem research funding for the registry work.
