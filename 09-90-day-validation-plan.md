# 09 — 90-Day Validation Plan

Purpose: convert a founder disagreement into a set of experiments with pre-agreed outcomes, so the
decision is made by data rather than by whoever argues hardest. **Write the kill criteria down and
both sign them before starting.** That is the whole point.

Total budget: **~USD 20–25k** and ~90 days of part-time founder effort.

---

## Experiment A — Practitioner demand (weeks 1–6)
**Question:** will registered practitioners pay, and for which of the four value propositions?

- 30 structured interviews: 20 registered TCM physicians (SG/MY), 5 integrative GPs, 5 Ayurveda/jamu
  practitioners. Recruit from the TCMPB register, MY T&CM Division listings, and associations.
- Script must include, in this order: current workflow → what they lose money/time/credibility on →
  show three one-page concepts (safety checker / practitioner OS + dispensary / patient handout) →
  **ask for a paid pre-order or a signed LOI**, not for an opinion.
- Never ask "would you use this". Ask "what do you use today, what did it cost, and will you put
  SGD 200 down now for early access".

**Kill criteria (pre-agreed):**
- ✅ Proceed if ≥8/30 sign an LOI **and** ≥5 pay a refundable deposit.
- ⚠️ Reshape if interest is high but payment is zero → the value is real, the packaging is wrong.
- ❌ Stop the practitioner thesis if <3 will commit anything.

---

## Experiment B — Institutional pain (weeks 2–6)
**Question:** is the herb–drug safety problem urgent enough for an institution to buy?

- 10 interviews: hospital clinical pharmacists, retail pharmacy chain clinical leads, 2 insurers,
  2 telehealth platforms.
- Ask for incidents: "when did a patient's supplement last change your management?"; "how do you
  capture supplement use at admission?"; "what would you pay to see it?"
- Probe budget owner and procurement path explicitly.

**Kill criteria:**
- ✅ Proceed if ≥3 describe concrete incidents **and** ≥1 will scope a paid pilot.
- ❌ Deprioritise Pivot 1 as a wedge if none can name an incident or a budget line.

---

## Experiment C — Can the engine be made correct? (weeks 3–10)
**Question:** can a small team build a safety layer that is measurably reliable? This is the
question only you can answer, and it is your equity justification.

- Scope deliberately small: **150 substances × 100 drugs**, plus the top 30 red-flag rules.
- Sources: EMA HMPC monographs + LiverTox + MSK About Herbs + one paid licence trial
  (NatMed Pro or Stockley's Herbal).
- Build the **golden case set**: 200 cases with expert-adjudicated expected safety output, including
  an adversarial subset (pregnancy, CKD, warfarin, transplant + St John's wort, paediatric,
  occult emergency).
- Measure and publish internally: interaction recall, red-flag sensitivity, false-alarm rate,
  and end-to-end reproducibility.

**Kill criteria:**
- ✅ Proceed if red-flag sensitivity = **1.00** on the critical set, interaction recall ≥ **0.95**
  against the reference source, and false-alarm rate is low enough that reviewers don't ignore it.
- ❌ Stop if the safety layer cannot reach those numbers on 150 substances — because it will never
  reach them on 5,000, and without them you have no product worth selling.

---

## Experiment D — Expert concordance (weeks 8–12)
**Question:** do independent clinicians consider the output safe and useful?

- 3 blinded raters (MD, registered TCM physician, pharmacist) score 50 generated outputs on:
  safety (harmful / neutral / helpful), appropriateness, and would-you-act-on-this.
- Pre-register the rubric. Report inter-rater agreement — and expect it to be imperfect; that is
  itself a finding worth publishing.

**Kill criteria:**
- ✅ Proceed if **zero** outputs are rated harmful and ≥60% are rated useful.
- ❌ Stop and redesign if any output is rated harmful by any rater. Not "iterate" — stop.

---

## Experiment E — Regulatory scoping (weeks 1–4, runs in parallel)
- One paid consultation (~USD 3–5k) with a Singapore medical-device regulatory consultant.
- Deliverables you should walk out with: a written **Intended Purpose** statement, a classification
  opinion for both the professional and consumer variants, and a costed registration pathway.
- Also: quote professional indemnity + product liability + cyber insurance for both variants.

**Decision value:** if an underwriter will not cover the consumer variant, or the classification
opinion puts it at Class C, that settles the audience debate on external authority rather than on
your word — which is worth far more to the partnership than winning the argument yourself.

---

## Experiment F — Fake-door consumer test (weeks 4–8, cheap)
- Two landing pages, small ad spend (~USD 500 each): (i) "AI health advice combining Western +
  traditional medicine"; (ii) "Scan your supplement — check it against your medications".
- Measure email capture and, better, willingness to pre-pay.

**Expected result** (state the prediction in advance so the test is honest): (ii) materially
outperforms (i). If it does, the consumer debate resolves toward Pivot 6 without anyone losing face.

---

## Budget

| Item | USD |
|---|---|
| Regulatory consultation | 3,000–5,000 |
| Data licence trial (NatMed / Stockley's) | 2,000–5,000 |
| Clinical curator / expert raters (contract hours) | 5,000–8,000 |
| Interview incentives + travel (SG/MY) | 2,000 |
| Ads for fake-door test | 1,000 |
| Cloud, tooling, misc. | 2,000 |
| **Total** | **~15,000–23,000** |

## Day-90 decision gate

| Outcome | Action |
|---|---|
| A ✅ B ✅ C ✅ D ✅ | Incorporate. Build Pivot 2 with Pivot 1 as the moat. Raise a seed on the eval data. |
| A ✅ C ✅, B ❌ | Practitioner-first only. Defer institutional sales to year 2. |
| A ❌ B ✅ | Flip to Pivot 1 as the primary product; practitioners become channel, not customer. |
| C ❌ or D ❌ | **Do not ship anything.** Either narrow the scope until the numbers pass, or stop. |
| A ❌ B ❌ | No customer exists at this price. Fall back to Pivot 3 (services) or walk away — cleanly, as friends, with the data as the reason. |

## Working agreement for the 90 days

- Neither founder unilaterally changes the target audience during the sprint. Audience changes only
  at the day-90 gate.
- No public-facing claim ships without both founders' sign-off.
- All interview notes go in a shared repo. Anecdotes don't count unless they're written down.
- Weekly 30-minute review against these criteria. No re-litigating settled decisions mid-sprint.
