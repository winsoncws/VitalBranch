# 08 — Pivot Options, Ranked

Each option is scored on: **Time to revenue · Regulatory drag · Defensibility · Fit with the
existing vision · Capital required.** All six preserve your co-founder's core intent — making
traditional medicine safer and more reachable. None require abandoning it.

---

## Pivot 1 ⭐ — "The interaction and adulteration layer for ASEAN"
**Positioning:** *"Your patients are already taking jamu, TCM and supplements. You can't see it, and
it's affecting your drugs. We make it visible and safe."*

- **Product:** herb/supplement × drug interaction checking at the **SKU level** (BPOM NIE, HSA CPM
  listing, NPRA MAL number), with recall and BKO-adulteration history, contraindications by
  population, and hard red-flag gating. API + web + EMR plugin.
- **Buyer:** hospital pharmacy, retail pharmacy chains, telehealth platforms, insurers, clinics.
- **Why it wins:** it inverts the sales problem. Hospitals will never buy "TCM recommendations" —
  the practitioner you interviewed told you exactly why — but every one of them has an
  unmanaged herb–drug problem *today*. You sell into an existing anxiety, not a new belief.
- **Regulatory drag:** low. Reference/safety information for professionals, not a treatment
  recommendation. Cleanest possible intended-purpose statement.
- **Defensibility:** high — the ASEAN SKU-level safety registry ([`06 §5`](06-data-sources-and-knowledge-graph.md#5-the-data-asset-you-should-build-yourself)) does not exist anywhere.
- **Time to revenue:** 6–9 months. **Capital:** low.
- **Preserves the vision?** Yes — it is the credibility beachhead that earns the right to do the
  recommendation layer later, from inside the institutions.

---

## Pivot 2 ⭐ — "Fullscript for ASEAN traditional medicine"
**Positioning:** the operating system + dispensary for integrative practitioners.

- **Product:** practitioner workflow (structured intake → four-lens plan → safety check → ICD-11+TM2
  coded record → multilingual patient handout) plus a vetted dispensary with take-rate.
- **Buyer:** registered TCM physicians, integrative GPs, Ayurvedic and jamu practitioners.
- **Why it wins:** proven model at ~USD 1B revenue in North America; absent in ASEAN; monetises
  without requiring proof of efficacy; and the practitioner supplies the tongue/pulse/outcome data
  the consumer plan could never obtain.
- **Regulatory drag:** low–medium (professional use; the dispensary carries product-side compliance).
- **Defensibility:** medium initially, high once supply relationships and the outcomes registry lock in.
- **Time to revenue:** 3–6 months. **Capital:** low–medium.
- **Preserves the vision?** Fully. This is the four-lens product — just sold to the person who can
  legally act on it.

**Pivots 1 and 2 share ~80% of the engineering.** Build 1 as the credibility asset, sell 2 as the
business. That combination is the recommendation.

---

## Pivot 3 — "Regulatory and evidence services for herbal manufacturers"
- **Product:** evidence dossiers, systematic-review-as-a-service, interaction data for labels,
  pharmacovigilance, and BPOM **Jamu → OHT → Fitofarmaka** upgrade support.
- **Buyer:** herbal/supplement/jamu manufacturers.
- **Why it wins:** cash-generative from month 2–3, no clinical-risk exposure, and it funds the
  knowledge graph you need anyway — you get paid to build your own asset.
- **Risk:** it is a services business; it will consume founder time and can quietly become the whole
  company. Cap it deliberately (e.g. ≤30% of founder hours) and treat it as non-dilutive funding.
- **Time to revenue:** 2–4 months. **Capital:** minimal.

---

## Pivot 4 — "The ICD-11 TM2 coding and documentation layer"
- **Product:** the tool that lets a traditional-medicine encounter be recorded in a form a health
  system, ministry or insurer can actually use — dual-coded conventional + TM2, exportable to FHIR.
- **Buyer:** ministries, clinic chains, insurers, research bodies; grant-fundable.
- **Why it's interesting:** WHO's TM Strategy 2025–2034 and the ICD-11 TM2 rollout are *creating* a
  mandate that almost nobody has tooling for; India has an active national implementation roadmap.
  Being early here is a durable, standards-anchored position.
- **Risk:** government sales cycles; adoption timing is not in your control.
- **Best used as:** a feature inside Pivots 1/2 and a grant/credibility engine — not as a standalone
  company for a two-person team.

---

## Pivot 5 — "The real-world outcomes registry"
- **Product:** structured, longitudinal, dual-coded outcome capture across integrative clinics, with
  validated PROMs. Sell/licence the de-identified evidence base.
- **Why it matters:** this is the *direct* answer to your co-founder's founding observation. The
  reason the word-of-mouth cure can't reach more people is that no one records it in a form that
  travels. This turns anecdote into evidence, at scale, as a business.
- **Risk:** slow; needs Pivot 2's distribution to exist first.
- **Best used as:** the year-2+ moat, instrumented from day one inside Pivot 2.

---

## Pivot 6 — Consumer, done safely (the version that isn't a liability)
If the consumer instinct is non-negotiable, the only defensible shape is:

- **Not** a recommendation engine. Instead: **"What am I actually taking?"** — scan a supplement or
  jamu box, get the resolved ingredients, the registration status, recall/adulteration history, and
  an interaction check against the user's medication list. Output is *"discuss with your doctor /
  do not take with X"*, never *"take Y for Z"*.
- Regulatory posture: information about products the user already possesses, plus a safety warning.
  Far outside the recommendation trap — though note that any patient-facing CDS in the US is a device
  regardless, so scope it to ASEAN.
- Monetisation: free; it's the funnel that routes users to practitioners in Pivot 2's network.
- **This is the only consumer product I would put my name on.**

---

## Ranked recommendation

| Rank | Pivot | Role |
|---|---|---|
| 1 | **Pivot 2** — practitioner OS + dispensary | The business |
| 2 | **Pivot 1** — ASEAN safety/interaction layer | The wedge and the moat |
| 3 | **Pivot 3** — manufacturer services | Non-dilutive funding |
| 4 | **Pivot 5** — outcomes registry | Instrument now, monetise year 2+ |
| 5 | **Pivot 4** — TM2 coding | Feature + grants + credibility |
| 6 | **Pivot 6** — consumer scanner | Funnel only, never the product |

## What gets dropped, and how to say it

- **Consumer diagnosis and recommendation** → replaced by Pivot 6's scanner.
- **Tongue/pulse capture by the public** → replaced by practitioner-entered assessment, plus a
  standardised-capture research protocol ([`04 §3`](04-clinical-evidence-reality.md#3-where-the-evidence-does-not-support-the-product-design)) that is publishable and fundable.
- **Hospital as first customer** → hospitals enter via pharmacy safety ([Pivot 1](#pivot-1---the-interaction-and-adulteration-layer-for-asean)) in year 2, which is
  a *better* door into the same building.
- **The fused four-lens score** → four parallel, separately-sourced lenses. Same screen, honest maths.

Framed this way, nothing your co-founder cares about is lost. The sequence changes, the customer
changes, and the claim gets narrower — which is what makes it fundable.
