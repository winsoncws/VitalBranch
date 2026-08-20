# 04 — Clinical Evidence Reality Check

The point of this document is not to argue that traditional medicine "doesn't work". It is to
establish **which claims you can stand behind commercially**, because that boundary is the product.

## 1. Your co-founder's motivating observation, taken seriously

*"Modern medicine sometimes didn't help, a word-of-mouth supplement did. Unfortunately, it can't reach more people."*

Both halves deserve an honest response:

- **The plausible part:** conventional care genuinely under-serves several categories — functional GI
  disorders, chronic fatigue, non-specific musculoskeletal pain, perimenopausal symptoms, post-viral
  syndromes, mild insomnia and anxiety, and much of chronic-disease *lifestyle* management. These are
  high-prevalence, high-frustration, low-conventional-satisfaction conditions. That is a real market
  gap and it is where traditional systems have their most defensible role.
- **The part that needs discipline:** individual recovery stories are systematically unreliable —
  regression to the mean, natural history of self-limiting illness, placebo and expectancy effects,
  concurrent conventional treatment, and survivorship bias (you never hear from the people it didn't
  help). This is not a reason to dismiss the observation; it is a reason to **instrument it**.
- **The constructive reframe — and this is the strongest idea in the whole venture:**
  the reason the supplement "can't reach more people" is that **nobody records outcomes in a
  structured way.** A company that converts anecdote into structured, coded, longitudinal outcome
  data is solving exactly the problem she described — and building the only asset in this space that
  a frontier LLM cannot replicate. See [`Pivot 5`](08-pivot-options.md#pivot-5--the-real-world-outcomes-registry).

## 2. Where the evidence is comparatively strong

Treat this list as *"areas to build first because the citations exist"*, and re-verify against
current Cochrane/systematic reviews before any claim ships — evidence moves.

- Acupuncture for chronic musculoskeletal pain and chemotherapy-induced nausea/vomiting (endorsed in
  several oncology supportive-care guidelines).
- Ginger for nausea in pregnancy and post-operative nausea.
- Peppermint oil for IBS symptoms.
- Berberine and some cinnamon preparations for glycaemic parameters (moderate, heterogeneous).
- St John's wort for mild–moderate depression — **efficacy evidence is decent, and it is
  simultaneously one of the most dangerous interaction agents known** (CYP3A4/P-gp induction).
- Curcumin for osteoarthritis symptoms (mixed; bioavailability formulation-dependent).
- Artemisinin — the case study your co-founder should use in every pitch: a traditional remedy that
  went through full pharmacological characterisation and became standard of care. It shows the
  *path*, and it also shows the path runs **through** clinical evidence, not around it.

**Commercial implication:** a narrow, deeply-sourced product covering ~50–150 well-evidenced agents
is more valuable and more sellable than a broad, shallow one covering thousands.

## 3. Where the evidence does not support the product design

- **Diagnostic reliability of tongue and pulse.** Published inter-rater agreement is poor to modest:
  a TCM pulse-diagnosis study reported weighted κ ≈ 0.37 with no significant inter-rater agreement
  despite high test–retest reliability; an acupuncture pattern-differentiation study reported Light's
  κ ≈ 0.17 for correct diagnosis across six experts; Korean-medicine tongue studies found agreement
  ranging from poor (some colours) to near-perfect (specific structural signs), improving markedly
  **when a standardised photographic protocol and classification scheme were imposed**.
  - **What this means for you:** you cannot train or validate a model against a ground truth that
    experts don't agree on. Any "AI tongue diagnosis" claim will fail technical diligence on this
    point alone.
  - **What this means constructively:** the *standardisation* finding is the opportunity. A
    standardised capture protocol (fixed lighting, colour card, prescribed classification scheme) that
    demonstrably raises inter-rater agreement is a **publishable, defensible, fundable contribution**
    — and it is squarely in your ML/clinical-validation skill set. That is a far better first
    technical project than a diagnosis classifier.
- **Pulse ("palm pulse") capture.** There is no accessible consumer instrument that reliably captures
  what a TCM practitioner means by pulse quality. Devices exist in China/Taiwan; none has a validated
  cross-practitioner standard. **Drop pulse from any consumer pathway.** In the practitioner product
  it is fine — the practitioner enters their own assessment.
- **Multi-herb formulas.** Most classical formulas lack RCT-grade evidence for specific indications,
  and combination effects, batch variability and dose standardisation make extrapolation from
  single-herb studies unsound.
- **Cross-system "fusion".** There is no accepted methodology for reconciling a Western diagnosis, a
  TCM pattern, an Ayurvedic dosha assessment and a Jamu indication into a single ranked
  recommendation. The mock-up's four parallel confidence scores imply such a methodology exists. It
  does not. **Present them as four parallel lenses with independent provenance — never as a fused
  score.** (This is also the safer legal position, and it is more intellectually honest, which
  clinicians will notice and respect.)

## 4. The harm model — this is where your product's value actually lives

Ranked by expected harm:

1. **Delay / replacement of effective conventional treatment.** Johnson et al., *JAMA Oncology* 2018:
   in ~1.9M National Cancer Database patients with curable non-metastatic cancers, complementary-
   medicine users more often refused a component of conventional therapy and had ~2× mortality risk,
   mediated by refusal. **This is the harm mechanism to design against, explicitly.**
2. **Herb–drug interactions.** Highest-risk drug classes: anticoagulants (warfarin/DOACs),
   immunosuppressants (tacrolimus, ciclosporin), oncology agents, antiretrovirals, antiepileptics,
   oral contraceptives, and everything narrow-therapeutic-index. Highest-risk herbs: St John's wort,
   ginkgo, ginseng, danshen, dong quai (*Angelica sinensis*), garlic/ginger at high dose, grapefruit
   constituents.
3. **Intrinsic organ toxicity.** Herb-induced liver injury (NIH **LiverTox** is the canonical free
   reference); aristolochic-acid nephropathy and urothelial carcinoma from *Aristolochia* species —
   a documented public-health disaster, not a theoretical risk.
4. **Product-level contamination and adulteration** — the risk your competitors will ignore:
   - **Jamu/BKO:** BPOM has repeatedly found undeclared pharmaceutical adulterants in marketed jamu
     (hundreds of products over 2020–2026; roughly 200 positives from ~11,600 sampled in a recent
     annual sweep), including corticosteroids, NSAIDs, anti-obesity and psychoactive agents.
   - **Ayurvedic products:** heavy metals (lead, mercury, arsenic) have been documented in a
     substantial minority of marketed products in published US market surveys.
   - **Implication:** *the plant is not the product.* A safety engine reasoning at the species level
     is systematically blind to the dominant real-world harm in exactly the two traditions
     (Jamu, Ayurveda) your friend wants to include. **Reason at the SKU level** — brand, manufacturer,
     registration number (BPOM NIE, HSA listing, AYUSH licence), recall status.
     *This is the single most defensible data asset available to this company.*
5. **Pregnancy, paediatrics, renal and hepatic impairment** — populations where most traditional
   agents have no safety data at all. Default to "insufficient data — do not recommend", not to a
   generic caution line.

## 5. What "clinically validated" can realistically mean for a startup

You already know why the hospital plan collapsed — you've lived the trial and audit cycle. Here is
the affordable ladder, in order:

1. **Analytical validation** (weeks, ~free): does the safety layer reproduce a reference standard
   (e.g. a licensed interaction database, or an expert panel) on N test cases? Report sensitivity,
   specificity, and the miss list. *This alone is more validation than anyone else in this space has.*
2. **Expert-panel concordance** (1–2 months, low cost): 3 clinicians (MD, registered TCM physician,
   pharmacist) blind-rate 50–100 generated outputs on safety, appropriateness, and harmfulness.
   Pre-register the rubric. Publishing this is cheap credibility.
3. **Usability / human-factors study** (IEC 62366) with 10–15 practitioners.
4. **Prospective observational registry** with 2–5 design-partner clinics: structured intake,
   ICD-11 + TM2 dual coding, validated PROMs (PROMIS, EQ-5D, condition-specific), 3/6/12-month
   follow-up. This is the asset. It is also the thing that eventually makes a hospital conversation
   possible.
5. **Pragmatic RCT** — only with Series A money and an academic partner, on **one** indication.

**Do not attempt to validate "the platform".** Validate one narrow claim at a time. That is the
lesson from your medical-AI experience and it is directly transferable here.
