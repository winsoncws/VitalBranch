# 06 — Data Sources & Knowledge Graph Design

Licence column legend: **Free** = open/public use · **Free-ND** = free but no-derivatives or
attribution-restricted · **Academic** = academic use only, commercial use needs negotiation ·
**Paid** = commercial licence required · **Restricted** = not licensable for a product.

> Verify every licence yourself before ingesting. Several widely-used TCM databases are academic-only
> and are routinely (and illegally) scraped into commercial products — that is a diligence landmine
> at acquisition or Series A.

## 1. Terminology & identifier backbone (build this first)

| Resource | Use | Licence |
|---|---|---|
| **ICD-11** incl. **Chapter 26 (Traditional Medicine conditions, TM1/TM2)** | Dual coding: conventional + TM pattern. The strategic one. | Free-ND (CC BY-ND) |
| **WHO International Standard Terminologies on Traditional Chinese Medicine** (2022) | Canonical English/Chinese TCM term set | Free-ND |
| **WHO International Standard Terminologies on Ayurveda / Unani / Siddha** | Same for Indian systems | Free-ND |
| **NAMASTE portal** (India, Ministry of AYUSH) | ASU morbidity codes + terminologies, mapped toward TM2 | Free |
| **SNOMED CT** | Clinical concepts; Singapore is a member territory (national release centre) | Paid/affiliate licence |
| **LOINC** | Lab result codes — essential for the intake layer | Free (registration) |
| **RxNorm** | Drug normalisation (US-centric; supplement with local formularies) | Free |
| **WHO ATC/DDD** | Drug classification | Free for non-commercial; **Paid** for commercial |
| **UMLS Metathesaurus** | Cross-vocabulary mapping | Free with licence; check redistribution terms |
| **Kew MPNS — Medicinal Plant Names Services** | **The** resolver for medicinal-plant name chaos across pharmacopoeias, trade names and traditions | Free / negotiable |
| **World Flora Online (WFO)**, **IPNI**, **GBIF** | Accepted botanical taxonomy + synonymy | Free |
| **PubChem**, **ChEBI**, **InChIKey** | Constituent chemistry | Free |

**Why MPNS matters more than it looks:** "Huang Qi" ↔ *Astragalus membranaceus* ↔ *Astragali Radix*
↔ "Radix Astragali" ↔ Indonesian/Malay trade names ↔ a BPOM-registered branded product are five
different identifiers for things that are not quite the same object. Getting this resolution layer
right is unglamorous, hard, and is a genuine moat in ASEAN because nobody has done it.

## 2. Safety & interaction sources (the core of the product)

| Resource | Use | Licence |
|---|---|---|
| **NatMed Pro / Natural Medicines** (Therapeutic Research Center) | ~1,400 evidence-based monographs, interaction checker, 300k+ commercial supplement products | **Paid** — get a quote early; this may be your fastest path to a credible v1 |
| **Stockley's Herbal Medicines Interactions** (Pharmaceutical Press / MedicinesComplete) | 200+ herbs × conventional drugs, expert-curated; licensable for integration into clinical systems | **Paid** |
| **NIH LiverTox** | Herb-induced liver injury — canonical, free, authoritative | Free |
| **MSKCC "About Herbs"** | Clinician-oriented herb monographs incl. interactions | Free (check reuse terms) |
| **NCCIH "Herbs at a Glance"** | Consumer/clinician summaries | Free |
| **EMA HMPC herbal monographs** | EU-official monographs: indication, posology, contraindications, safety. **The best free structured safety data in existence for herbs.** | Free |
| **ESCOP monographs**, **German Commission E** | Older but well-structured European monographs | Paid / mixed |
| **HEDRINE**, **PHYDGI** | Academic herb–drug interaction databases | Academic |
| **DrugBank** | Drug targets, metabolism, interactions | **Paid** for commercial |
| **FDA FAERS** | Adverse event signals incl. supplements | Free |
| **WHO VigiBase** (Uppsala Monitoring Centre) | Global pharmacovigilance incl. herbal reports | **Paid** |
| **BPOM public notices / Cek BPOM**, **HSA safety alerts**, **MY NPRA alerts** | **Product-level recalls and BKO adulteration lists — the ASEAN-specific data nobody has aggregated** | Free (scrape/agreement) |

> The last row is the most valuable line in this document. Global databases reason about *plants*;
> ASEAN harm happens at the level of *branded products*. Aggregating BPOM/HSA/NPRA product actions
> into a queryable SKU-level safety registry is a small, tractable engineering job and an asset with
> no substitute. See `08` Pivot 1.

## 3. Evidence sources

| Resource | Use | Licence |
|---|---|---|
| **PubMed / MEDLINE (E-utilities)** | Primary literature; supports automated ingestion | Free |
| **Cochrane Library** (incl. Complementary Medicine field) | Systematic reviews — the top of your evidence hierarchy | Paid for full text |
| **ClinicalTrials.gov**, **WHO ICTRP**, **ChiCTR** (China), **CTRI** (India) | Trial registries; ChiCTR/CTRI hold large volumes of TM trials invisible to Western search | Free |
| **AYUSH Research Portal**, **DHARA**, **CCRAS** publications | Ayurveda evidence | Free |
| **Farmakope Herbal Indonesia**, **BPOM OHT/Fitofarmaka lists** | Which jamu products actually have standardisation or clinical support | Free / official |
| **Chinese Pharmacopoeia**, **Japanese Kampo (JPS)**, **Ayurvedic Pharmacopoeia of India**, **USP Herbal Medicines Compendium**, **Ph. Eur.** | Identity, quality, dosage standards | Mixed, mostly **Paid** |

**Language note:** a large fraction of the primary TCM evidence is Chinese-language (CNKI, Wanfang)
and Ayurveda evidence is partly Hindi/Sanskrit-adjacent. Multilingual ingestion is real technical
work *and* a real barrier to entry — lean into it rather than avoiding it.

## 4. TCM systems-biology databases — use with caution

TCMSP · SymMap · HERB / HERB 2.0 · BATMAN-TCM 2.0 · ETCM v2 · TCMBank · TCM-ID

- Mostly **Academic** licence. Several explicitly prohibit commercial use.
- Quality is uneven; network-pharmacology target predictions are hypothesis-generating, **not**
  clinical evidence, and should never surface to a clinician as justification.
- Useful for research and for herb–constituent–target mapping in a *research* product. Do not build
  the safety layer on them.

## 5. The data asset you should build yourself

Nothing above covers these, and each is defensible:

1. **ASEAN SKU registry** — branded traditional-medicine and supplement products with: registration
   number (BPOM NIE / HSA CPM listing / MY NPRA MAL number), manufacturer, declared composition,
   label claims, recall/adulteration history, and a link to the resolved plant taxa.
2. **Standardised tongue-capture protocol + dataset** — fixed lighting, colour reference card,
   prescribed classification scheme, multi-rater labels with published agreement statistics. The
   literature shows standardisation improves agreement; being the group that *publishes* that
   protocol is credibility you cannot buy.
3. **Practitioner override log** — what your users reject and why. Unique, compounding, and it is
   simultaneously your training signal, your post-market surveillance, and your roadmap.
4. **Structured outcomes registry** — ICD-11 + TM2 dual-coded, validated PROMs, longitudinal.
   This is the asset that converts your co-founder's ["word-of-mouth cure"](04-clinical-evidence-reality.md#1-your-co-founders-motivating-observation-taken-seriously) observation into evidence.

## 6. Knowledge-graph schema (starting point)

**Nodes**
```
Substance          (taxon_id, mpns_id, pharmaceutical_name, tradition[], part_used)
Preparation        (formula_id, name_zh/sa/id, components[], ratio, classical_source)
Product/SKU        (reg_no, jurisdiction, manufacturer, declared_composition[], status)
Constituent        (pubchem_cid, inchikey)
Drug               (rxnorm, atc, inn)
Condition          (icd11_code, tm2_code, snomed_id)
TMPattern          (tradition, term_id, who_ist_ref)         # zang-fu, dosha, etc.
LabAnalyte         (loinc)
PopulationFlag     (pregnancy | paediatric | ckd_stage | hepatic | elderly | allergy)
EvidenceItem       (pmid|doi|monograph_id, design, n, risk_of_bias, grade)
Jurisdiction       (SG | MY | ID | IN | ...)
```

**Edges — every edge carries `{source_id, evidence_grade, last_reviewed, reviewer_id, version}`**
```
Substance      -[:HAS_CONSTITUENT]->        Constituent
Preparation    -[:CONTAINS]->               Substance
Product        -[:DECLARES]->               Substance|Preparation
Product        -[:HAS_SAFETY_ACTION]->      {recall|BKO_adulteration|heavy_metal}   # ASEAN-specific
Substance      -[:INTERACTS_WITH {severity, mechanism, onset, management}]-> Drug
Substance      -[:CONTRAINDICATED_IN]->     PopulationFlag
Substance      -[:INDICATED_FOR {grade}]->  Condition
Substance      -[:TRADITIONAL_USE_FOR]->    TMPattern            # explicitly NOT an efficacy edge
TMPattern      -[:CORRELATES_WITH {strength}]-> Condition        # weak by construction — label it
LabAnalyte     -[:TRIGGERS]->               RedFlagRule
Substance      -[:REGULATORY_STATUS]->      Jurisdiction
```

**Two schema decisions that matter more than they look:**
- `INDICATED_FOR` and `TRADITIONAL_USE_FOR` must be **separate edge types**. Collapsing them is how
  traditional-use claims silently become efficacy claims — the exact failure the mock-up has today.
- `CORRELATES_WITH` between TM patterns and ICD conditions should be labelled with strength and
  provenance and treated as weak by default. It is the join everyone wants and the join least
  supported by evidence.

## 7. Ingestion & curation workflow

1. Automated ingest (PubMed, registries, regulator notices) → staging.
2. LLM-assisted extraction into the schema — **proposal only, never auto-published**.
3. Human expert review queue: a registered TCM physician, a pharmacist, and an MD, each with a scope.
4. Publish with `reviewer_id`, `review_date`, `corpus_version`.
5. Scheduled re-review (12-month expiry on every safety edge — a stale interaction edge is a hazard).
6. Full change log; every published output reproducible from its corpus version.

**Budget reality:** curation is the dominant recurring cost of this business, roughly 0.5–1 FTE
clinical curator per ~500 well-curated substances per year, plus the paid licences above. Model it
explicitly — it is the line item that most integrative-health startups discover too late.
