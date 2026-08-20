# 02 — Market & Target Audience

## 1. Why the audience keeps moving (diagnosis of the problem)

The sequence was: **hospitals → public → public-with-clinic-sourced-data → (July/Aug mock-up now says)
clinicians only**. That is not indecision for its own sake — it is the symptom of optimising for the
wrong variable. Each pivot was chosen to escape the *previous* objection (clinical trials → data
acquisition → clinical risk), rather than to find a buyer.

The correct ordering is: **find the budget holder first, then design backwards to what they will
pay for.** Everything else follows.

Rule of thumb for this space: *the people who benefit are not the people who pay, and the people who
pay do not benefit directly.* Patients benefit; practitioners, manufacturers and payers pay.

## 2. Segment-by-segment assessment

Scoring: **Pain** (how badly they feel the problem) × **Budget** (can they pay now) ×
**Reachability** (can 2 founders reach them) × **Regulatory drag**.

### A. Public / consumers (the current plan)
- Pain: medium. Budget: **very low**. Reachability: expensive. Reg drag: **highest**.
- Fatal objections, all of which you have already raised and none of which are answered:
  - The information is substantially free via any frontier LLM with search. Your objection stands.
  - No CDS exemption exists anywhere for patient-facing recommendation software (US FDA is explicit;
    EU MDR Rule 11 pulls it in; HSA treats intended purpose, not the disclaimer, as decisive).
  - The disclaimer required to be safe ("not for self-care") destroys the value proposition of a
    self-care product. You cannot have both, and the current mock-up proves it — its own disclaimer
    says "not for direct patient self-care."
  - CAC on health consumers in ASEAN is brutal, retention on wellness apps is worse, and there is no
    prescription-refill loop to retain on.
- **Verdict: not a v1 market. Keep as a content/community/funnel layer only.**

### B. TCM / Ayurveda / Jamu / integrative practitioners  ← **recommended beachhead**
- Pain: **high** and specific: they lose credibility and referrals because they cannot speak the
  language of the patient's lab report; they fear (rightly) interacting with the patient's
  prescribed drugs; they have no documentation that a hospital will accept.
- Budget: **real** — they run cash-pay clinics, and crucially they already earn margin on
  dispensing herbs/supplements, which is a channel you can monetise without charging SaaS.
- Reachability: **excellent** — registered, listed, associationed, conference-attending.
  - Singapore: TCM Practitioners Board register (TCM Practitioners Act 2000) — a public list.
  - Malaysia: T&CM Act 2016 (Act 775), practitioner registration live since March 2021, covering
    Traditional Malay, Chinese and Indian medicine, homeopathy, chiropractic, osteopathy, Islamic
    medical practice — i.e. a government-maintained, addressable, *growing* professional register.
  - Indonesia: much larger, less formal; reach via jamu industry associations and Puskesmas
    "Saintifikasi Jamu" networks.
- Reg drag: **lowest** — professional-use tools carry far lighter obligations than patient-facing
  ones, and the practitioner is the accountable decision-maker.
- **Verdict: this is the beachhead. It also happens to be the only segment that solves the data
  problem — they generate the tongue/pulse/outcome data you cannot get from the public.**

### C. Herbal / supplement manufacturers and distributors
- Pain: **high and monetised**. They need: safety dossiers, interaction data for labels, evidence
  substantiation for claims, adverse-event handling, and (Indonesia) the upgrade path
  Jamu → OHT → Fitofarmaka, which is a formal BPOM ladder that costs them money and time today.
- Budget: **yes**, and they pay for regulatory work as a cost of doing business.
- Reg drag: none for you — you are selling them a service, not a device.
- **Verdict: strongest non-obvious B2B payer. Under-considered in the current plan.**

### D. Hospitals / health systems
- Pain: high but **for a different problem than the one you're solving**. Hospitals will never buy
  "TCM recommendations". They will buy *"our patients are secretly taking herbs and it's affecting
  our drugs and our outcomes, and we have no way to capture it."*
- Budget: yes, but 12–24 month sales cycles, procurement, IT security review, clinical governance
  committee. Not survivable for a pre-revenue two-person team.
- Your TCM practitioner interviewee is right about the asymmetry: in China, TCM is institutionally
  integrated; elsewhere it is not, and the barrier is evidence + liability, not attitude.
- **Verdict: year 2–3. Enter through pharmacy/medication-safety, not through TCM.**

### E. Insurers / corporate wellness / TPAs
- Some ASEAN insurers reimburse TCM (notably in SG/MY riders, and in Indonesia BPJS has limited
  traditional-medicine touchpoints). Their real need is **utilisation control and fraud/quality
  signal**, not recommendations.
- **Verdict: interesting later; needs claims data you won't have for years.**

### F. Governments / WHO ecosystem
- Genuine tailwind: WHO TM Strategy 2025–2034 (adopted WHA78, May 2025) pushes member states toward
  evidence, safety, regulation and integration; ICD-11 Chapter 26 (Traditional Medicine conditions,
  TM1/TM2) creates a **dual-coding** requirement that almost nobody has tooling for; India has an
  active TM2 implementation roadmap and the NAMASTE terminology programme; WHO's Global Traditional
  Medicine Centre sits in Jamnagar, India.
- **Verdict: grant funding, credibility and design partners — not revenue. But the ICD-11 TM2
  coding gap is the most concrete "why now" in this whole space.**

## 3. Beachhead recommendation

**Primary:** Singapore + Malaysia registered TCM physicians and integrative GPs (a countable,
licensed, English/Chinese-speaking population in the low tens of thousands across both markets —
verify exact register counts from TCMPB and MOH T&CM Division before using any number in a deck).

**Why this beachhead specifically:**
- Registered and addressable → cheap, non-paid acquisition.
- Already handle both worlds daily → the four-lens output is immediately useful, not aspirational.
- Cash-pay + dispensing → they can transact without insurance codes.
- Two well-defined regulators (HSA/MOH; MDA/T&CM Division) → you can actually get compliant.
- Bilingual market → forces the multilingual capability that becomes a moat in ID/IN later.

**Then expand:** Indonesia (volume, jamu supply chain, BPOM relationship) → India (Ayurveda scale,
AYUSH/NAMASTE alignment) → Gulf and diaspora markets.

## 4. Sizing — how to do it honestly

Do **not** put "global traditional medicine market = USD Xbn" in a deck. Every investor discounts
it to zero. Build bottom-up:

```
SOM (yr 1-2) = (# registered practitioners in SG+MY reachable)
             × (realistic paid conversion, 3–8%)
             × (ARPU: subscription + share of dispensing GMV)
```

Then show the second engine: `GMV × take-rate`, which is where the Fullscript comparison earns its
place (see `07`). A bottom-up model with 30 real practitioner interviews behind it is worth more in
a seed conversation than any TAM slide.

## 5. Competitive landscape to map before committing

- **Practitioner dispensary / integrative workflow:** Fullscript (US/CA, ~USD 1B revenue, 100k+
  providers; acquired Rupa Health for lab ordering), Emerson Ecologics/Wellevate, Natural Partners.
  These validate the model and show you what the mature version looks like.
- **China digital TCM:** AI-assisted TCM diagnosis platforms and TCM tele-clinics are a mature,
  crowded category domestically. Assume the technical problem is *solved* there and the moat is
  distribution + regulation, not algorithms. Do not compete in China.
- **ASEAN telehealth incumbents:** Halodoc, Alodokter, Doctor Anywhere, Speedoc — any of them can
  bolt on a traditional-medicine module. Your defence is data + safety depth, not features.
- **Frontier LLMs:** the strongest competitor for the consumer use case, and free. Your defence
  is *only*: curation, provenance, product-level (SKU) specificity, local regulatory status, and
  practitioner workflow — none of which a general model has.
