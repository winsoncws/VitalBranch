# 03 — Regulatory, Claims & Liability

> Not legal advice. This is a working map to scope counsel's brief and to price the compliance
> workplan. Get a regulatory consultant in the primary market before any launch.

## 1. The single most important principle

**Regulators classify on *intended purpose*, not on disclaimers.**
A disclaimer that contradicts your marketing does not protect you — it is evidence against you. If
the landing page says the system produces recommendations for a named individual's condition, a
footer saying "informational only" does not change the classification. This is the core problem
with the current "add a disclaimer, keep the WHO badge" approach.

Corollary: **the disclaimer and the value proposition must be compatible.** The current mock-up's
disclaimer ("not for direct patient self-care") is *correct* and is *incompatible* with a consumer
product. Pick one.

## 2. Is it a medical device? (per market)

### Singapore — likely primary market ("Not HSA-registered" is on the page)
- Governing: Health Products Act + Health Products (Medical Devices) Regulations 2010.
- Key guidance: **HSA GL-04, "Regulatory Guidelines for Software Medical Devices — A Life Cycle
  Approach"** (covers SaMD, AI/ML, cybersecurity, change-management programme), plus the MOH/HSA
  **Artificial Intelligence in Healthcare Guidelines (AIHGle)**, refreshed 2026.
- Practical read:
  - Software that *informs clinical management* for an individual patient → SaMD, risk-classified
    (commonly Class B, rising to C where it drives treatment decisions or carries serious-harm
    potential). Registration + manufacturer's/importer's licence.
  - The in-house AI-SaMD exemption applies to **public healthcare licensees developing for their own
    patients** — it does **not** cover a commercial startup. Don't plan around it.
  - Wellness/lifestyle software that does not make disease-specific statements sits outside. That
    exclusion evaporates the moment you output "HbA1c 7.2% meets diagnostic threshold for diabetes"
    — which the current build does.
- Also relevant: Traditional Chinese Medicine Practitioners Act 2000 (who may practise TCM),
  Healthcare Services Act (if you ever host a telemedicine service), and HSA rules for health
  supplements and Chinese Proprietary Medicines (listing, prohibited substances, claim limits).

### United States (only if you ever target it)
- **FDA final guidance on Clinical Decision Support Software.** Four Cures Act §3060 criteria for
  non-device CDS, of which the operative ones for you are: the software must not analyse a
  *signal/pattern/image* directly, and the clinician must be able to **independently review the
  basis** for the recommendation.
- **No CDS function intended for patients or caregivers qualifies for the non-device exclusion.**
  A consumer version is a device, full stop.
- "Independently review the basis" is the criterion that maps directly onto Finding F6 in `01`:
  **provenance is not a nice-to-have, it is the regulatory hinge.** An opaque LLM recommendation
  cannot satisfy it; a cited, sourced, rule-traceable output can.
- Tongue-image analysis = analysing an image → device territory regardless of who uses it.
- Supplements: DSHEA — structure/function claims only, with the mandatory disclaimer; disease claims
  are illegal.

### European Union
- MDR **Rule 11**: software providing information used for diagnostic/therapeutic decisions is
  generally Class IIa or higher; MDCG 2019-11 gives the qualification logic. Class IIa+ means a
  notified body — expensive and slow.
- **EU AI Act**: an AI system that is a safety component of, or is itself, a device requiring
  notified-body conformity assessment is **high-risk** → risk management, data governance, technical
  documentation, logging, human oversight, post-market monitoring.
- Botanical health claims under Regulation 1924/2006 are largely "on hold" — you cannot freely make
  efficacy claims for herbs in the EU.
- **Practical conclusion: do not target the EU for years.**

### Malaysia
- Medical Device Authority (Act 737/738) for SaMD registration.
- **Traditional and Complementary Medicine Act 2016 (Act 775)** governs T&CM *practice*; registration
  of practitioners in force since 1 March 2021 across Traditional Malay, Chinese, Indian medicine,
  homeopathy, chiropractic, osteopathy, Islamic medical practice.
- **Medicines (Advertisement and Sale) Act 1956** — advertising anything as treating a listed
  disease requires Medicine Advertisements Board approval. This is strictly enforced and is a real
  exposure for a product named "MIRACLE" making condition-specific statements.

### Indonesia
- BPOM regulates traditional medicine in three tiers: **Jamu** (empirical use) → **OHT** (Obat Herbal
  Terstandar, standardised, preclinical) → **Fitofarmaka** (clinical-trial supported). This ladder is
  a *product opportunity* (see `08`), not just a constraint.
- Kemenkes digital-health rules and the SatuSehat platform govern health-data interoperability.
- **Personal Data Protection Law (UU 27/2022)** applies to health data.
- Critical safety context: BPOM repeatedly finds pharmaceutical adulterants (**BKO — bahan kimia
  obat**) in jamu — reported findings include hundreds of adulterated products across 2020–2026 and
  ~200 positives from ~11,600 products sampled in a recent single-year sweep, with adulterants
  spanning corticosteroids, NSAIDs, anti-obesity and psychoactive agents. **Any Jamu recommendation
  engine that reasons about *plants* while consumers buy *branded products* is reasoning about the
  wrong object.** See `04 §4` and `06 §5`.

### India
- Ministry of AYUSH governs Ayurveda/Siddha/Unani/Homeopathy; CCRAS for research; NAMASTE portal for
  standardised terminologies; active national roadmap for **ICD-11 TM2 dual coding**.
- Drugs & Cosmetics Act (ASU provisions) for products; SaMD regulation under CDSCO is still
  immature — which cuts both ways (low barrier, low clarity).
- DPDP Act 2023 for personal data.

### China
- NMPA; TCM is fully institutionalised with its own approval pathways. Domestic competition is
  strong and entrenched. **Treat as a knowledge source and a partnership market, not a sales market.**

## 3. Claims — the fastest way to get into trouble

Retire these phrasings immediately:

| Currently on/near the site | Problem | Safer replacement |
|---|---|---|
| "WHO 2025–2034 aligned" (as a compliance-style badge) | Implies WHO endorsement; WHO name/emblem is protected and WHO endorses no products | Body text: "Designed against the objectives of the WHO Traditional Medicine Strategy 2025–2034" |
| "FHIR / CDS Hooks ready" | Not implemented; falsifiable in one meeting | "FHIR-aligned data model (integration on roadmap)" |
| "full auditability" | No audit log or rule versioning exists | Ship the audit log, then say it |
| "MIRACLE" | Implies cure; advertising-law risk (esp. MY) and credibility cost | Rename |
| Any "X% confidence" | Fabricated and constant across cases | Evidence grade + citation |
| Disease-specific supplement statements | Disease claim in US/EU/SG/MY | Cite the study; state the population; state the uncertainty |

## 4. Liability — what actually bites

- **The dominant harm is not a bad herb. It is delay or replacement of effective care.** The best
  evidence here is direct: a National Cancer Database analysis of patients with non-metastatic
  curable cancers found that those using complementary medicine were more likely to refuse at least
  one component of conventional treatment, and had roughly **twice** the mortality risk — with the
  effect mediated by treatment refusal (Johnson et al., *JAMA Oncology*, 2018). Any product that
  presents a traditional option *alongside* a conventional one, with equal visual weight and a
  fabricated confidence score, is nudging toward exactly that behaviour.
  - **Design implication:** traditional options must be framed as *adjunct*, never as *alternative*,
    and the UI must not create false equivalence between an 82%-labelled Western box and a
    70%-labelled TCM box.
- **Failure-to-escalate** — Finding F1. If the system detects a red flag and still emits a care
  plan, a plaintiff's expert will read that screen aloud in court. Fix before anything ships.
- **Herb–drug interaction harm** — warfarin, immunosuppressants (tacrolimus/ciclosporin), oncology
  agents, antiretrovirals, and anything narrow-therapeutic-index. St John's wort alone (CYP3A4/P-gp
  induction) is a well-documented cause of transplant rejection and contraceptive failure.
- **Product-level harm you cannot see from the plant name** — BKO adulteration in jamu; heavy metals
  (lead/mercury/arsenic) documented in a meaningful fraction of marketed Ayurvedic products;
  aristolochic-acid nephropathy and carcinogenicity from *Aristolochia* species; herb-induced liver
  injury (NIH LiverTox catalogues these).
- **Data breach** — special-category data, five jurisdictions, plus cross-border transfer if you
  call a hosted LLM.

**Insurance:** get professional indemnity + product liability + cyber quoted *early*, and expect
underwriters to ask exactly the questions above. If an insurer will not cover the consumer version,
that is a market signal about the consumer version.

## 5. The compliance workplan that makes the clinician version viable

This is genuinely achievable for a small team — it is the consumer version that is not.

1. **Write the Intended Purpose statement first** (one paragraph). It determines classification,
   and every marketing sentence must be consistent with it thereafter.
2. **QMS: ISO 13485**, and **IEC 62304** for software lifecycle, **ISO 14971** for risk management,
   **IEC 62366** for usability. Start lightweight but start now — retrofitting is the expensive path,
   and you already know this from your clinical-trial background.
3. **Risk file from day one**: hazard analysis with the red-flag gate, interaction miss, parse error,
   and delay-of-care as named hazards with mitigations.
4. **Clinical evaluation plan** — not a full trial. Analytical validation (does the safety layer
   correctly reproduce a reference source?) + usability + a prospective observational study with a
   design-partner clinic. This is the version of "clinical evidence" a startup can actually afford.
5. **Post-market surveillance & adverse event capture** — build the reporting channel in v1; it is
   also a data asset.
6. **Change-management programme** (HSA GL-04 supports predetermined change control) so you can ship
   updates without re-registration.

## 6. Regulatory strategy summary

| Path | Time to revenue | Cost | Recommendation |
|---|---|---|---|
| Consumer self-care app with recommendations | Fast to launch, fast to trouble | Low upfront, unbounded liability | **No** |
| Professional-use reference/safety tool (non-diagnostic, provenance-first) | **Fastest legitimate revenue** | Low–moderate | **Yes — start here** |
| Registered SaMD Class B (SG) for clinician CDS | 12–18 months | Moderate | Yes — year 2 |
| Class C / EU MDR / FDA cleared | 24–48 months | High | Only with Series A |
