# 10 — Co-founder Terms, Roles & Your Personal Risk

This file is about you, not the product. In healthcare specifically, the founder who owns the
clinical-risk surface carries exposure that does not show up on a cap table.

## 1. Your personal exposure

- **Professional reputation.** You come from medical AI with clinical-trial and audit experience.
  That is precisely the credential that makes the venture credible — and it is the credential that
  gets damaged if the company ships an unvalidated recommendation engine with fabricated confidence
  scores. Your name on it is doing real work; price it accordingly.
- **Employment conflict — check this first, before anything else.** You currently work at a medical
  AI startup. Review, in writing:
  - IP assignment clause — does it capture inventions made on your own time in an adjacent field?
  - Moonlighting/outside-activity clause — does it require disclosure or consent?
  - Non-compete / non-solicit — scope, duration, and whether "healthcare AI" is broad enough to cover
    this.
  - **Do not use employer hardware, accounts, LLM keys, datasets, or time.** Keep a clean provenance
    record for everything you build. This is the kind of thing that surfaces at Series A diligence or
    at acquisition, years later, and it is trivially avoidable now.
- **Personal liability.** Directors of a company giving health-adjacent advice can be personally
  exposed in some scenarios. Incorporate properly (Pte Ltd / Sdn Bhd), get D&O cover, and never let
  the company operate as an unincorporated partnership even for "just the pilot".

## 2. Roles — make these explicit before equity

| Domain | Decision owner | Notes |
|---|---|---|
| Vision, fundraising, partnerships, commercial | Your co-founder | Yosin's strength; don't dilute it |
| Architecture, data, evaluation, security | You | Your strength |
| **Clinical claims, safety logic, marketing copy that touches health** | **You (veto)** | Non-negotiable |
| Regulatory strategy | Shared, with external counsel | Neither of you is qualified alone |
| Clinical content correctness | Contracted clinician(s) | Must be a named, paid role from day one |

**The veto is the single most important term you will negotiate.** In this business the failure mode
is not "we built the wrong feature", it is "we said something we couldn't substantiate". The person
who understands substantiation must be able to stop a sentence from shipping. If she resists this,
that resistance *is* your answer about the partnership.

Frame it as protecting her, not constraining her: a regulatory or press incident lands hardest on
the CEO.

## 3. Equity — practical guidance

- **Split ranges by scenario**, assuming both full-time from incorporation:
  - She has the idea, the vision, is CEO, and raises → 55/45 or 60/40 in her favour is fair.
  - You build the entire product and carry the clinical-risk expertise → 50/50 is entirely defensible.
  - You stay part-time while employed elsewhere → your split should reflect that, and should
    **step up on a written trigger** (e.g. resigning to go full-time), not on a promise.
- **Always: 4-year vesting, 1-year cliff, for both founders, from the date full-time work starts.**
  No exceptions for the person who "had the idea earlier". The idea is worth very little; the four
  years are worth everything.
- **Acceleration** on change of control (single-trigger for founders is common; double-trigger is
  more investor-friendly).
- **IP assignment agreements signed by both founders on day one**, covering everything already built
  — including the Base44 prototype, the brand, the domain, and any data collected so far.
- **Founder departure terms written up front**: what happens to shares, to the codebase, to the data,
  to the customer relationships. Write it while you like each other.
- **Reserve 10–15% option pool** for the clinical advisors you will need — they will want equity, and
  discovering you have none to give is an avoidable problem.

## 4. Written agreements before incorporation

1. Founders' agreement: equity, vesting, roles, **decision rights and the clinical veto**, deadlock
   resolution, departure terms.
2. IP assignment from both founders.
3. **Written kill criteria and pivot triggers** (copy them from `09`). This is unusual and it is the
   highest-value thing on this list: it means a future pivot is a pre-agreed protocol rather than a
   fight about whose judgement was better.
4. A one-page **Intended Purpose statement** for the product (from `03 §5`) that both founders sign.
   Every marketing sentence must be consistent with it. This one page prevents most of the claims
   problems in `01` from ever recurring.

## 5. How to have the conversation

Your position is strong and easy to state badly. Some framing that keeps it constructive:

- **Lead with what's right.** The observation is real; the timing (WHO strategy, ICD-11 TM2) is
  genuinely good; the prototype shows instincts most people get wrong — `candidate_for_review`,
  clinician-in-the-loop, the governance strip, the red-flag concept. Say all of that first, and mean
  it.
- **Bring artefacts, not opinions.** Open the mock-up, load the "Red flag" scenario, and let her read
  the screen that says "STOP and seek emergency care" directly above "30-min fasted walk before
  breakfast". That single screen makes the clinical-risk argument better than any amount of
  discussion, and it makes it about the product rather than about her judgement.
- **Separate "the plan won't work" from "this specific claim can't ship."** You are not qualified to
  predict the market — she may well see something you don't. You *are* qualified to say that a
  fabricated confidence score and an ungated red flag cannot ship. Stay on that ground and you will
  never be wrong.
- **Trade, don't block.** "I'll build the safety layer and the evaluation harness in 8 weeks. In
  exchange, we hold the consumer launch until Experiment E comes back." Founders accept constraints
  attached to delivery far more easily than constraints attached to nothing.
- **Set the pivot up as hers.** Present Pivots 1 and 2 as *sequencing* her vision, not replacing it —
  because that is literally what they are. The four-lens integrative platform still exists at the end
  of the road; you are arguing about which door to enter through.

## 6. Signals to watch over the next 90 days

**Green — she is a good co-founder for you:**
- Engages with the mock-up findings on the merits, and fixes the red-flag gate quickly.
- Agrees to written kill criteria without needing to be talked into it.
- Actively wants a clinician on the team rather than treating it as overhead.
- Changes the marketing copy when you explain the claims exposure.

**Amber:**
- Agrees in conversation, but the landing page stays unchanged three weeks later.
- Answers clinical-risk questions with "we'll add a disclaimer" more than once.
- Keeps expanding scope (a fifth tradition, a new country) before the first one is validated.

**Red — do not incorporate:**
- Refuses your veto on clinical claims.
- Ships an efficacy claim or "WHO-aligned" badge after being shown why it's a problem.
- Treats your regulated-ML experience as pessimism rather than as the asset you were recruited for.
- Wants you to build before the audience question is settled.

## 7. A closing note on the disagreement itself

You wrote that you wouldn't say her plan *can't* work — that's the right posture, and it's worth
holding onto. Long-horizon founders are often right about direction and wrong about sequence. The
useful contribution you can make is not "this is too risky"; it's **"here is the same vision,
resequenced so that we survive long enough to reach it."**

That is a co-founder's contribution. The other version is just an engineer saying no.
