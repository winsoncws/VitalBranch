# 00 — Executive Summary & Verdict

## 1. The honest verdict

- **The underlying observation is correct and commercially significant.** Large populations in
  ASEAN and South Asia already use traditional medicine *concurrently* with Western medicine, and
  mostly do it invisibly — they don't tell their doctor. That invisibility is a genuine, unowned
  problem with real clinical cost.
- **The current product framing is the weakest expression of that observation.** "Four traditions,
  one engine, produces a recommendation" is simultaneously:
  - the hardest thing to validate (four evidence bases, none of them mutually commensurable),
  - the hardest thing to sell (nobody's budget line says "integrative recommendations"),
  - the hardest thing to defend legally (recommendation = the regulated act),
  - and the easiest thing to replicate (a competent prompt over a frontier LLM gets 80% there,
    which is exactly the objection you already raised).
- **There is a real company adjacent to it.** Reframe from *"we tell you what to take"* to
  *"we make what you are already taking safe, documented, and reimbursable."* Safety, provenance,
  coding and distribution are boring, buyable, and defensible. Recommendation is not. Read [here](plain_english.md#01) for layman explanation.
- **Verdict: co-found it only on a rewritten thesis.** Not "no". The founder instinct is good, the
  market timing (WHO TM Strategy 2025–2034, ICD-11 TM2 rollout) is genuinely favourable, and your
  regulated-ML background is exactly the missing piece. But joining on the *current* thesis means
  you personally absorb the clinical-risk exposure of a product whose value proposition is
  "recommendations we cannot substantiate.". Read [here](plain_english.md#05) for more about WHO TM Strategy & ICD-11 in layman terms.

## 2. The five decisions that determine everything

Everything else is downstream of these. Get written answers before equity is discussed.

1. **Clinician-facing or consumer-facing? Pick one, permanently.**
   The plan has moved hospital → public → clinic-mediated in a few months, and the live mock-up now
   says *"for qualified clinician review only… not for direct patient self-care."* That directly
   contradicts the consumer plan. This is the single largest unresolved item and it changes the
   regulatory class, the architecture, the GTM and the cap table. See [`02`](02-market-and-audience.md) and [`03`](03-regulatory-and-liability.md).
2. **Is the output a recommendation, or a safety/evidence retrieval?**
   Recommendation → medical device in most target markets, and no CDS exemption at all if it is
   patient-facing (US FDA final CDS guidance is explicit on this). Retrieval with provenance →
   far lighter path. See [`03`](03-regulatory-and-liability.md).
3. **Who pays, and can they pay before clinical validation exists?**
   Only two payers can: (a) integrative/T&CM practitioners buying workflow + dispensing margin,
   (b) herbal/supplement manufacturers buying regulatory and pharmacovigilance evidence work.
   Hospitals and insurers cannot, for years. Consumers will not. See [`07`](07-business-model-and-gtm.md).
4. **What is the defensible asset in 24 months?**
   Not the LLM. Not the UI. Candidates: a curated, provenance-tracked herb–drug safety graph for
   ASEAN products (incl. Jamu SKUs); or a structured outcomes registry that no one else has. Pick
   one and instrument for it from day one. See [`05`](05-engine-architecture.md), [`06`](06-data-sources-and-knowledge-graph.md).
5. **Who holds veto over clinical claims and marketing copy?**
   If it isn't you, do not join. This is where the company gets killed, and it is unrecoverable
   once a regulator or a journalist has a screenshot. See [`10`](10-cofounder-terms-and-risks.md).

## 3. Risk scorecard (current thesis)

| Risk | Severity | Why |
|---|---|---|
| Target-customer ambiguity | **Critical** | Target audience  pivoted from hospital to public and back to clinician; mock-up contradicts the stated plan. |
| Clinical/liability exposure | **Critical** | Prototype emits herbal recommendations *through* emergency red flags (from [August mockup](https://miracle-in19aug.base44.app/)). |
| Regulatory classification | **High** | Consumer recommendation engine = device; "WHO aligned" badge is a claims problem. |
| Willingness to pay | **High** | Unanswered. Public will not pay if it is `Google-able`. |
| Defensibility | **High** | No proprietary data, no proprietary distribution, no proprietary evidence. |
| Evidence availability | **Medium-High** | Tongue/pulse inter-rater reliability is poor (κ≈0.17–0.37 in published studies); can't build ground truth on it. |
| Team | **Medium** | Complementary (entrepreneur + regulated-ML) but no clinical/regulatory principal. |
| Market timing | **Favourable** | WHO TM Strategy adopted May 2025; ICD-11 TM2 rollout creates a coding mandate tailwind. |
| Founder-market fit | **Favourable** | Yosin's visionary thinker and your clinical-trial/audit scar tissue is the scarce skill in this space. |

## 4. Opus4 comment

I believe the observation. I don't yet believe the product. Here are three experiments costing 
~USD 20k over 90 days whose outcomes decide the shape of the company. I'll build the prototype 
for all three. If they come back positive I'm in with both feet; if they come back negative we 
pivot to the version the data supports — and I've already written that version down.


## 5. Opus4 recommendation in one paragraph

Kill "MIRACLE" as a name (a healthcare product literally named "miracle" is an advertising-law and
credibility liability in every market on your list). Drop the consumer track to a content funnel.
Build **one thing**: an ASEAN-specific herb/supplement–drug interaction and contraindication layer
with hard red-flag gating and per-claim provenance, wrapped in a structured intake that dual-codes
to ICD-11 (conventional + TM2). Sell it first to integrative/TCM clinics as workflow + dispensary
(the Fullscript model — that company reached ~USD 1B revenue on practitioner-mediated supplement
distribution, which is your proof that the *channel*, not the *advice*, is the business), and
second to hospital pharmacy as risk reduction. The four-tradition "recommendation" becomes a
downstream feature once you own the data — not the opening claim.

## 6. Go / no-go conditions for any co-founders

**Join if all of these are true:**
- Thesis rewritten to a clinician/practitioner-mediated safety + workflow product.
- You hold written veto on clinical claims, safety logic, and public marketing copy.
- A licensed clinician (MD + a registered TCM physician) is on the founding team or advisory board
  with real, paid, contracted hours — not a logo.
- Written kill criteria and pivot triggers agreed *before* incorporation.

**Walk away if:**
- The consumer self-care product ships with "WHO aligned" or any efficacy claim.
- Fabricated confidence scores survive into any customer-facing build.
- "We'll add the disclaimer" is the standing answer to clinical-risk questions.
