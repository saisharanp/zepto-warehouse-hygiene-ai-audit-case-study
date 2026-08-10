# Stage 00 — Research Setup: Zepto Warehouse Hygiene

**Product boundary:** Zepto dark stores / warehouse operations in India  
**Evidence window:** Previous calendar month, July 2026  
**Status:** Evidence-led proposal; no Zepto internal data or live study claimed

Use the [evidence and claim ledger](01_evidence_claim_ledger.md) as the source-of-truth for claim type, confidence, limitation, and non-claim handling.

## Opportunity frame

July 2026 reporting described hygiene enforcement at multiple Zepto locations in Hyderabad. Narsingi was reportedly directed to temporarily stop accepting orders while it cleaned and rectified issues; Malkajgiri reporting described food stored on floors, houseflies, poor waste disposal, co-storage, missing records, and a 67% hygiene score; Mallepally reporting described cockroach and rodent evidence.

These are reports about specific inspections, not proof of a network-wide failure. The product question is whether Zepto can make hygiene checks more frequent, harder to falsify, easier to remediate, and auditable between physical inspections.

## Research question

How might Zepto detect and remediate visible warehouse-hygiene failures earlier, while producing trustworthy evidence that a check occurred at the correct facility and reducing dependence on infrequent or predictable physical inspections?

## Target users

| User | Job | Need |
|---|---|---|
| Customer | Buy food without worrying about storage conditions | Credible, non-misleading trust signal and fast recovery |
| Store manager | Keep the site compliant without losing operating time | Guided scan, clear findings, practical remediation |
| Quality / food-safety lead | Intervene before customers or regulators discover a problem | Comparable evidence, risk prioritisation, escalation |
| Licensee | Operate a clean, productive store | Clear accountability, SLAs, and remediation support |
| Regulator / auditor | Enforce applicable food-safety requirements | Independent evidence and auditable company controls |

## Source-selection rules

- Prioritise July 2026 reporting of named municipal or food-safety inspections.
- Use multiple publishers for corroboration, while treating syndicated or repeated reports as one underlying event where appropriate.
- Separate official findings, journalistic summaries, user complaints, inference, and product proposal.
- Do not convert anecdotes into prevalence.
- Use FSSAI guidance for checklist design, not as evidence that Zepto passed or failed a specific control.

## Evidence rubric

- **High:** official regulator document or contemporaneous report quoting a named authority.
- **Medium:** reputable reporting corroborating an official action or inspection.
- **Low:** user-generated allegation; useful for discovery, not prevalence.

## Source plan

| Source | Date | Use |
|---|---:|---|
| [New Indian Express](https://www.newindianexpress.com/amp/story/cities/hyderabad/2026/Jul/10/zepto-told-to-halt-orders-over-hygiene-lapses) | Jul 10, 2026 | Narsingi stop-order and reported hygiene findings |
| [Siasat — Narsingi](https://www.siasat.com/zepto-facility-in-narsingi-raided-fifth-inspection-in-3-weeks-3504787/) | Jul 10, 2026 | CMC observations and reported inspection cluster |
| [Hyderabad Mail — Malkajgiri](https://hyderabadmail.com/zepto-malkajgiri-food-safety-inspection-hygiene-lapses/) | Jul 8, 2026 | Malkajgiri findings and reported hygiene score |
| [South First — Mallepally](https://thesouthfirst.com/telangana/cockroaches-rodents-found-at-zepto-store-rotten-chicken-hygiene-violations-found-in-hyderabad/) | Jul 1, 2026 | Mallepally pest evidence |
| [Siasat — Mallepally](https://www.siasat.com/cockroach-rodent-infestation-at-another-zepto-store-in-hyderabad-3499401/) | Jul 1, 2026 | Complaint-trigger context and official comments |
| [FSSAI hygiene requirements](https://fssai.gov.in/cms/hygiene-requirements.php) | Current guidance | FSMS, GMP/GHP and Schedule 4 checklist context |

## Capture schema

`source`, `published_date`, `inspection_date`, `city`, `store_or_facility`, `authority`, `reported_finding`, `evidence_type`, `severity`, `sentiment`, `confidence`, `customer_or_operational_implication`, `source_url`, `notes_on_limitations`.

## Assumptions and risks

| Assumption / risk | Why it matters | Mitigation |
|---|---|---|
| Public reports may omit context or later corrections | Avoids overclaiming | Use “reported” language and validate with internal records |
| A phone scan can be incomplete or staged | Weakens evidence integrity | Route checkpoints, random prompts, anti-spoofing, human sampling |
| AI may miss or hallucinate hygiene findings | Safety risk | Unknown state, category-level recall thresholds, no critical auto-pass |
| Recording captures workers and sensitive layout | Privacy and labour risk | No audio by default, blur, minimisation, retention and access controls |
| Detection without remediation creates paperwork | No operational improvement | Named owner, hold scope, SLA, budget, re-check |

## Stage 00 decision gate

**Decision:** Proceed to discovery synthesis and problem definition.

**Recommendation:** Focus on a verified routine virtual check as a control-system opportunity, not an AI certification product.

**Evidence:** July 2026 public reports and FSSAI guidance justify investigating a more frequent, auditable hygiene-control loop; they do not establish Zepto-wide prevalence.

**Open questions:** Zepto’s current cadence, baseline exception rate, inspection media, remediation SLAs, and legal basis for recording.

**Approval request:** Approve discovery synthesis and request internal Zepto data plus cross-functional review before validation.
