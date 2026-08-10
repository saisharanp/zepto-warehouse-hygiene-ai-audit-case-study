# Stage 01 — Evidence Coding Sheet

**Status:** Structured public-evidence sample; not a prevalence dataset
**Purpose:** Make the discovery synthesis reproducible by coding each underlying report or complaint signal consistently.

## Coding schema

| Field | Allowed values / guidance |
|---|---|
| `evidence_id` | Stable code, linked to the evidence ledger |
| `inspection_date` / `published_date` | Use the reported date; mark unknown rather than infer |
| `facility` / `city` | Facility named by the source; no network extrapolation |
| `journey_step` | Receiving, storage, picking, delivery, recovery, governance |
| `issue_type` | Floor/storage, pest, waste, segregation, infrastructure, records, cold-chain, complaint trigger |
| `reported_severity` | Reported by source, official score, or `not assessed`; do not invent product severity |
| `sentiment` | Concern, urgency, neutral, recovery |
| `source_confidence` | High, medium, low using the Stage 00 rubric |
| `evidence_type` | Official action, contemporaneous report, complaint signal, interpretation |
| `limitation` | What the item cannot establish |

## Coded public-evidence sample

| Evidence ID | Date | Facility / city | Journey step | Issue type | Reported severity | Sentiment | Confidence | Limitation |
|---|---|---|---|---|---|---|---|---|
| ECL-02 | Jul 2026 | Narsingi / Hyderabad | Governance, storage | Order halt, food on ground, waste, segregation, fixtures | Official action reported; product severity pending SOP mapping | Urgency | High / medium | Does not establish duration or wider prevalence |
| ECL-03A | Jul 2026 | Malkajgiri / Hyderabad | Storage, governance | Food on floor, flies, damaged flooring, waste, co-storage, missing records | Reported 67% assessment; severity mapping pending | Concern / urgency | Medium | Media account; no underlying inspection pack |
| ECL-03B | Jun 30 inspection, published Jul 2026 | Mallepally / Hyderabad | Storage, governance | Cockroach and rodent evidence | Official finding reported; product severity pending SOP mapping | Concern / urgency | Medium | Does not estimate pest prevalence across Zepto |
| ECL-04 | Jun 2026 trigger, published Jul 2026 | Mallepally / Hyderabad | Recovery / governance | Customer complaint preceded inspection | Trigger signal | Concern | Medium | Complaint is not causal proof or a denominator |

## Synthesis rules

- Deduplicate ECL-02/ECL-03 items when multiple publishers describe the same inspection.
- Keep `reported_severity` separate from the product’s critical/major/minor policy until Food Safety maps the finding.
- Do not calculate issue rates from this sheet; it is a discovery sample without a store, order, or inspection denominator.
- Add internal rows only when provenance, date range, denominator, access basis, and reviewer are recorded.

## Stage 01 discovery gate

**Decision:** Use the coded sheet to support themes and research requests, not prevalence claims.

**Recommendation:** Join this sample to de-identified internal complaints, inspections, pest tickets, temperature excursions, expiry write-offs, and remediation records before estimating frequency.

**Evidence:** The sample captures repeated issue categories across named locations while preserving source and denominator limitations.

**Open questions:** Which categories recur in internal data, how are they currently severity-rated, and what is the baseline time-to-remediation?

**Approval request:** Approve the coding schema and internal-data request before quantitative prioritization.
