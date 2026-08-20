# 01 — Mock-up Teardown (miracle-in19aug.base44.app)

Observed live on **2026-08-20**, engine self-reports `v1.2.0`. Everything below is reproducible;
no interpretation is presented as fact without the observation that produced it.

## 1. What it actually is, technically

- **Fully client-side.** The network log during a full `recommend()` run shows only:
  the HTML, one JS bundle, one CSS bundle, the Base44 badge script, and Base44's own
  analytics/settings endpoints. **No inference call, no API call, no backend of any kind.**
- Therefore the "engine" is hard-coded branching logic shipped in the browser bundle.
- **Consequence:** the mock-up demonstrates *desired output shape*. It demonstrates nothing about
  feasibility of the engine, and the LLM-vs-KG question remains completely open. That is fine for a
  mock-up — but it must not be described to investors, clinicians or partners as a working engine.

## 2. Positioning as currently written on the page

Verbatim from the live site:

- "MIRACLE is a **clinician-in-the-loop decision-support layer** that unifies Western medicine,
  Traditional Chinese Medicine, Ayurveda and Jamu — with ranked evidence, herb–drug safety checks,
  and full auditability."
- Badges: "FHIR / CDS Hooks ready" · "**WHO 2025–2034 aligned**" · "Clinician-in-the-loop, never autonomous"
- Governance strip: "Rules-based CDS · **Not HSA-registered** · Not clinically validated for patient care"
- "Prototype decision-support tool for **qualified clinician review only**. Not for autonomous
  diagnosis, prescribing, emergency use, or **direct patient self-care**."

**This is a clinician product.** It is not the consumer product described in the plan. The strategy
and the artefact are pointing in opposite directions — resolve this before anything else.

Also note "Not HSA-registered" → the team is anchoring to **Singapore** regulation. That should be
made explicit and deliberate, because it determines the entire regulatory workplan (see `03`).

## 3. Findings — ranked by severity

### F1 (CRITICAL) — Red flags do not gate the output
Running the built-in **"Red flag"** scenario produced these alerts:

> ⚠ HbA1c >11% — hyperglycaemic crisis risk · ⚠ Fasting glucose >300 mg/dL — possible DKA/HHS;
> STOP and seek emergency care · ⚠ eGFR <20 — severe CKD · ⚠ Creatinine >3.5 · ⚠ Systolic BP >180 —
> hypertensive crisis · ⚠ **Chest pain reported — rule out ACS** · ⚠ **Neurological symptoms — rule out stroke/TIA**

…and then, **on the same screen**, still emitted the full four-lens output plus a "Daily Care Plan"
containing **"30-min fasted walk or tai chi before breakfast"**, "Gentle yoga or qigong 20 min",
and herbal formula recommendations (Liu Wei Di Huang Wan, Huang Lian Jie Du Tang, Si Jun Zi Tang).

- Recommending a fasted walk to a patient with possible ACS/stroke and DKA is the exact failure
  mode that ends companies. The alert text even says "STOP" — and the software does not stop.
- **Required fix:** red flags must be a *hard gate*, not a banner. On any critical trigger the
  system emits **only** the escalation instruction. No patterns, no formulas, no care plan.
  This is a single architectural decision and it should be non-negotiable from v0.

### F2 (CRITICAL) — Confidence scores are fabricated and constant
Two clinically unrelated cases (the `+Warfarin` scenario and the `Red flag` scenario) both returned
**identical** confidences: Western 82%, TCM 70%, Ayurveda 65%, Jamu 66%.

- These are decorative numbers. Any clinician, auditor or technical diligence will find this in
  under five minutes, and it will retroactively discredit everything else on the page.
- **Required fix:** delete numeric confidence entirely. Replace with an evidence-grade label tied to
  a citation — e.g. `Evidence: RCT/meta-analysis` · `Observational` · `Traditional use only —
  no controlled evidence`. Grades are honest, defensible, and more useful to a clinician than a
  fake percentage. See `05 §4`.

### F3 (HIGH) — Safety warnings do not suppress or substitute the recommendation
In the `+Warfarin` case the engine raised `HIGH — Increased bleeding risk with
anticoagulants/antiplatelets. Monitor INR closely.` and then still recommended **Ba Zhen Tang**
(Eight Treasure Decoction, which contains *Angelica sinensis* / Dang Gui — a coumarin-containing
herb with documented warfarin-interaction concern) and **Huang Qi** (Astragalus).

- The warning is generic and floating: it is not bound to a specific herb–drug pair, and it does not
  change the recommendation set.
- **Required fix:** interactions must be edge-level (`herb X` × `drug Y` × `severity` × `mechanism`
  × `source`), and a HIGH edge must *remove* the offending item from the recommendation set and,
  where possible, propose a substitute — not merely annotate it.

### F4 (HIGH) — Output appears templated rather than input-driven
The line *"Wei Qi (defensive Qi) deficiency: lymphopenia reflects reduced immune function"* appeared
in **both** scenarios. Several care-plan bullets were byte-identical across cases.

- If the demo is inspected by anyone technical, this reads as "the output is a fixed script".
- It also signals a design trap: an engine that always produces five patterns and five formulas,
  regardless of input, is not decision support — it is a horoscope. **Empty output must be an
  allowed, and common, result.**

### F5 (HIGH) — Claims on the landing page that cannot be substantiated
- **"FHIR / CDS Hooks ready"** — nothing in the build implements FHIR or CDS Hooks. A hospital IT
  buyer will ask for the CapabilityStatement and the hook definitions in the first meeting. Remove
  until it's real; "FHIR-compatible data model (roadmap)" is defensible, "ready" is not.
- **"WHO 2025–2034 aligned"** — the WHO Traditional Medicine Strategy 2025–2034 was adopted at
  WHA78 in May 2025, so the reference is real. But a badge stating alignment, styled as a
  certification tick next to a regulatory strip, reads as endorsement. WHO's name/emblem use is
  protected and WHO does not endorse products. Reword to a factual sentence in body copy, e.g.
  *"Designed against the objectives of the WHO Traditional Medicine Strategy 2025–2034"*, and never
  place it in a badge row with compliance ticks.
- **"full auditability"** — there is no audit log, no versioning of the rule base, no citation on
  any output line. See F6.

### F6 (HIGH) — Zero provenance
Not one recommendation on the page carries a citation, source ID, or evidence grade. For a product
whose entire pitch is "one evidence layer", this is the central gap.

- **Required fix:** every emitted line carries `{claim, source_id, source_type, evidence_grade,
  last_reviewed, reviewer}`. If a line cannot carry that payload, it cannot be emitted. This single
  rule will shrink the output by ~70% — and that shrunken output is the actual product.

### F7 (MEDIUM-HIGH) — Data-protection design
- "Remove patient identifiers before upload" is an instruction, not a control — and there is a
  **"Patient ID"** field on the very same form, plus lab-report PDF upload (labs contain NRIC/name
  in the header) and **"Email this report (free) → Send Report"**.
- Emailing a health report is an unencrypted disclosure of special-category data. Under Singapore
  PDPA / Malaysia PDPA / Indonesia UU 27/2022 / India DPDP 2023 / GDPR this needs a lawful basis,
  consent record, retention policy, and (for cross-border LLM calls) a transfer mechanism.
- **Required fix:** no email delivery of clinical content; authenticated download only. And decide
  now whether you will ever hold identifiers — "de-identified only" is a genuine strategic
  simplification worth taking for v1.

### F8 (MEDIUM) — Lab parsing from PDF/image is a patient-safety surface
Mis-parsing eGFR or HbA1c silently changes the output. The build does have a "verify the values"
step — **that is the correct instinct and should be strengthened**, not removed: show the parsed
value next to the source snippet, and require explicit confirmation per field before `recommend()`
unlocks.

### F9 (MEDIUM) — The name
"MIRACLE" on a health product implies cure. In Malaysia, medicine advertising is controlled under
the Medicines (Advertisement and Sale) Act 1956 with mandatory Medicine Advertisements Board
approval; in Singapore, health-product advertising rules prohibit claims to treat/prevent disease.
Beyond legality: it is the single fastest way to lose a clinician audience. Rename.

## 4. What is genuinely good and should be kept

Give your co-founder full credit for these — they are non-obvious and several teams get them wrong:

- **"status = candidate_for_review"** as the output type. That framing is exactly right.
- **Clinician-in-the-loop, never autonomous** as an explicit product principle.
- The **red-flag concept existing at all** at mock-up stage (the gating bug is fixable; the instinct
  is the valuable part).
- **Verify-parsed-values** step before running.
- The **explicit governance strip** admitting non-registration and non-validation. Most founders
  hide this; showing it builds trust with clinicians.
- The **four-lens side-by-side layout** is a genuinely good demo artefact and a differentiated UI.
- **Multi-language output** (EN / 中文 / हिन्दी / BM) — correct for the region, and a real moat
  component nobody in Western digital health is building.

## 5. Immediate fix list (before this is shown to any clinician or investor)

1. Hard-gate red flags — critical alert suppresses all downstream output.
2. Delete numeric confidence; replace with evidence grades.
3. Bind every safety warning to a specific herb–drug pair, and make HIGH remove the item.
4. Add a citation/source line to every recommendation, or delete the recommendation.
5. Remove "FHIR / CDS Hooks ready" and the "WHO aligned" badge.
6. Remove "Email this report".
7. Allow — and demonstrate — a case where the correct output is "no traditional-medicine
   recommendation is appropriate here."
8. Rename the product.
