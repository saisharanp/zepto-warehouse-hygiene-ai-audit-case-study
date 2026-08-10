# Stage 00 — Evidence and Claim Ledger

**Status:** Reviewable evidence register; no Zepto internal evidence has been supplied
**Purpose:** Keep observed facts, interpretations, assumptions, proposals, and non-claims separate throughout the case study.

## Claim register

| ID | Claim / statement | Type | Source or basis | Confidence | Limitation / use |
|---|---|---|---|---|---|
| ECL-01 | July 2026 reporting described hygiene enforcement at multiple Zepto locations in Hyderabad. | Observed public evidence | New Indian Express, Siasat, Hyderabad Mail, South First | Medium to high by source | Location-specific reports; no network denominator |
| ECL-02 | Narsingi was reportedly directed to temporarily stop accepting orders while rectification occurred. | Observed public evidence | New Indian Express; Siasat | High / medium | Reported authority action; not evidence of duration or network prevalence |
| ECL-03 | Reported recurring categories included food on floors, dirty fixtures, waste, weak segregation, pest evidence, and missing records. | Observed public evidence | Cross-source comparison in Stage 01 | Medium | Findings were reported at specific facilities and need internal validation |
| ECL-04 | A customer complaint reportedly preceded the Mallepally inspection. | Observed public evidence | Siasat — Mallepally | Medium | Complaint is a trigger signal, not a prevalence estimate or causal proof |
| ECL-05 | FSSAI guidance supports documented food-safety management, GMP/GHP, monitoring, and periodic review. | Official guidance | FSSAI hygiene requirements and storage handbook | High | Guidance anchors checklist design; it does not establish Zepto compliance |
| ECL-06 | Licensee incentives, maintenance budgets, or accountability may contribute to control failure. | Root-cause hypothesis | Product interpretation | Low until internal validation | Do not present as a finding; validate with Zepto operational data |
| ECL-07 | A guided live scan may make checks more frequent and evidence more auditable between physical inspections. | Product hypothesis | Stage 01 synthesis and Stage 02 opportunity tree | Medium | Requires offline, shadow, and operational validation |
| ECL-08 | Video cannot prove microbial safety, concealed contamination, or continuous cold-chain conditions without other evidence. | Product boundary | Food-safety constraint and PRD policy | High | Route these controls to records, sensors, sampling, or physical inspection |
| ECL-09 | Bribery, inspection collusion, or evidence staging are integrity risks, not proven causes of the reported findings. | Non-claim | Evidence discipline decision | High | Use layered controls to reduce opportunity; do not accuse individuals or organisations |
| ECL-10 | AI inference and operating costs in the cost model are planning estimates, not Zepto’s actual contracted costs. | Explicit assumption | Stage 00 cost model | High | Replace with Finance/Procurement inputs and usage logs before approval |

## Evidence handling rules

- Treat multiple articles that repeat the same inspection statement as one underlying event unless they add independent evidence.
- Label every metric, cost, cohort size, and threshold as observed, proposed, illustrative, or `TBD`.
- Do not use public reports to estimate Zepto-wide prevalence, causal root cause, model performance, or customer impact.
- Link every decision in the [decision log](../stage-07-final-handoff/73_decision_log.md) to one or more ledger IDs.
- Re-review source freshness, regulator status, and legal assumptions before operational recording or public communication.

## Stage 00 evidence gate

**Decision:** Use the ledger as the claim-control layer for the case study.

**Recommendation:** Keep ECL-01–ECL-05 as the evidence base, ECL-06–ECL-08 as hypotheses/boundaries, and ECL-09–ECL-10 as explicit non-claims/assumptions.

**Evidence:** The public source set is directional and location-specific; the ledger prevents it from being overstated in later product stages.

**Open questions:** Which claims can be corroborated by official inspection records, and which Zepto internal datasets can validate the hypotheses?

**Approval request:** Approve the ledger as the source-of-truth for evidence labels before internal data collection.
