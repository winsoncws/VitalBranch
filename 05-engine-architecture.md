# 05 — Engine Architecture: LLM vs Knowledge Graph vs Rules

## 1. Which Architecture? The answer, up front

**Neither "LLM" nor "knowledge graph" alone. Use a four-layer architecture where the safety-critical
path is deterministic and the LLM is confined to language, never to decisions.**

The framing "what's the engine behind the server?" is the wrong first question. The right first
question is: **which outputs must be provably correct, and which merely need to be well-worded?**
Answer that, and the architecture falls out.

```
┌─────────────────────────────────────────────────────────────────┐
│ L0  INTAKE & NORMALISATION                                      │
│     lab parse → unit normalise → LOINC map → human verify step  │
│     meds → RxNorm/ATC · herbs/products → MPNS + SKU registry    │
│     conditions → ICD-11 (+ Ch.26 TM2)                           │
│     DETERMINISTIC. LLM allowed ONLY for extraction, always      │
│     followed by human confirmation before anything runs.        │
├─────────────────────────────────────────────────────────────────┤
│ L1  SAFETY GATE  ← the product's reason to exist                │
│     red flags · emergency triage · pregnancy/renal/hepatic      │
│     herb–drug edges · SKU recalls & adulteration flags          │
│     PURE RULES + GRAPH. No ML. No LLM. Fully unit-tested.       │
│     A CRITICAL trigger HARD-STOPS: escalation output only.      │
├─────────────────────────────────────────────────────────────────┤
│ L2  EVIDENCE RETRIEVAL                                          │
│     KG traversal + hybrid retrieval over the curated corpus     │
│     returns CANDIDATES, each carrying source_id + grade         │
│     Empty result set is a valid, expected outcome.              │
├─────────────────────────────────────────────────────────────────┤
│ L3  COMPOSITION & LANGUAGE                                      │
│     LLM: rank, deduplicate, explain, translate (EN/中文/हिन्दी/BM)  │
│     CONSTRAINT: may only reference candidates emitted by L2.    │
│     Post-generation validator strips any unsourced claim.       │
│     Every rendered line carries its citation.                   │
└─────────────────────────────────────────────────────────────────┘
```

**The one-sentence rule:** *the LLM may never be the reason something is recommended — only the
reason it reads well.* This is the same discipline you'd apply to a regulated ML pipeline, and it is
the difference between a system you can defend to HSA and one you can't.

## 2. Why not LLM-only

- Cannot satisfy "the clinician can independently review the basis for the recommendation" — the
  criterion that determines non-device CDS status in the US and shapes the argument elsewhere.
- Confabulates citations, dosages and interactions — all three of which are patient-safety items.
- Non-deterministic: the same case can produce different safety output across runs. Unshippable in a
  regulated context, and a nightmare for post-market investigation.
- **And commercially: it's your own objection.** If the engine is a prompt, the product is a prompt,
  and the customer can get it free. LLM-only is the version with no moat.

## 3. Why not knowledge-graph-only

- Curation cost is enormous and never finishes.
- Brittle on free-text symptoms, synonymy, and multilingual input.
- Poor at explanation and patient-facing language.
- **But the graph is where the defensibility lives** — it is the asset that compounds and that
  competitors can't prompt their way to. So: graph for truth, LLM for surface.

## 4. Replacing the fake confidence scores

Delete numeric confidence (Finding F2 in [`01`](01-mockup-teardown.md#f2-critical--confidence-scores-are-fabricated-and-constant)). Ship this instead — every recommendation carries:

```json
{
  "claim": "Astragalus membranaceus may support ... ",
  "evidence_grade": "B",
  "evidence_basis": "2 RCTs, n=180, moderate risk of bias",
  "sources": ["PMID:12345678", "EMA-HMPC-monograph-XXXX"],
  "traditional_basis": "Yu Ping Feng San — classical formula, Wei Qi deficiency",
  "safety_flags": ["interacts:warfarin:HIGH", "avoid:pregnancy"],
  "jurisdictional_status": { "SG": "listed CPM", "ID": "OHT", "MY": "registered" },
  "last_reviewed": "2026-08-01",
  "reviewed_by": "reviewer_id"
}
```

Grade scale (adapt GRADE, don't invent one):
- **A** — systematic review / multiple RCTs, consistent
- **B** — ≥1 RCT or strong observational
- **C** — mechanistic, preclinical, or small/low-quality human studies
- **D** — **traditional use only; no controlled human evidence**

Grade D is not a failure state — it is a *feature*. Saying "this is traditional use only" plainly is
what buys credibility with the clinician audience, and it is what distinguishes you from every
supplement marketing site.

## 5. The four-lens output — how to do it honestly

- Never fuse into a single score. Present four **independent, separately-sourced** columns.
- Mark each explicitly as **adjunct**, never **alternative** (see the delay-of-care harm model in
  [`04 §4`](04-clinical-evidence-reality.md#4-the-harm-model--this-is-where-your-products-value-actually-lives)).
- Show conflicts rather than resolving them silently: *"TCM pattern suggests warming tonics; renal
  function contraindicates X"*. Surfacing tension is genuine clinical value; hiding it is a hazard.
- Allow — and visibly demonstrate — the empty answer: *"No traditional-medicine adjunct with
  acceptable evidence and safety profile applies to this case."*

## 6. Evaluation — the part you own

This is the area where your background is worth the most equity, and it should be built before the
feature set expands.

- **Golden case set:** 200–500 de-identified cases with expert-adjudicated expected safety output.
  Build it before the engine, not after.
- **Safety-layer metrics that matter:** recall on known interactions (target ≥0.95 on the reference
  set — misses are the harm), red-flag sensitivity (target 1.0 on the critical set), and false-alarm
  rate (a system that flags everything gets ignored — alert fatigue is a real clinical failure mode).
- **Regression suite on every rule change**, with the rule base versioned and diffable. HSA GL-04's
  change-management programme effectively expects this anyway.
- **Adversarial/red-team set:** pregnancy + herb, CKD + nephrotoxic herb, warfarin + coumarin herb,
  transplant + St John's wort, paediatric dosing, occult emergency presentations.
- **Human-in-the-loop telemetry:** log every practitioner override. Override patterns are your
  highest-value training signal *and* your post-market surveillance evidence *and* your product
  roadmap — one instrumentation decision serving three purposes. Build it in v1.

## 7. Build sequencing (what to actually write first)

1. **Terminology/ID resolution service** — herbs (MPNS/WFO), drugs (RxNorm/ATC), labs (LOINC),
   conditions (ICD-11 + TM2), products (national registration numbers). Boring, unglamorous, and the
   thing everything else depends on. Nobody in this space has done it well for ASEAN.
2. **Safety gate** — red flags + interaction edges + population contraindications. Pure functions,
   exhaustively tested.
3. **Evidence store** with provenance and review workflow (including *who* reviewed and *when*).
4. **Retrieval + composition**, LLM-assisted, validator-constrained.
5. **Practitioner workflow** — intake, TM2 coding, plan export, follow-up capture.
6. Only then: any image/tongue work, and only as a *standardised capture protocol* study (see [`04 §3`](04-clinical-evidence-reality.md#3-where-the-evidence-does-not-support-the-product-design)).

## 8. Practical stack notes

- Graph store: PostgreSQL with a normalised relational schema will carry you further than you expect;
  move to Neo4j/RDF only when multi-hop traversal genuinely becomes the bottleneck. Don't buy a graph
  database to sound like a knowledge-graph company.
- Ontology/terminology serving: consider a FHIR terminology server (e.g. an open-source
  implementation) so `ValueSet`/`ConceptMap` are native — this is what makes "FHIR-ready" true later.
- LLM: any frontier model behind an abstraction layer; assume you will swap it. **Check the data
  processing terms and residency** before any patient data touches it (see [`03 §2`](03-regulatory-and-liability.md#2-is-it-a-medical-device-per-market) on cross-border
  transfer) — for SG/ID/IN this may force an in-region or self-hosted deployment.
- Everything user-visible must be reproducible from `{input_hash, ruleset_version, corpus_version,
  model_version}`. That tuple is your audit trail, and it is the thing that will make a hospital
  security review survivable.
