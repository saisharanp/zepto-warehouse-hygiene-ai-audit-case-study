# Stage 07 — Product Decision Log

**Status:** Proposed decision record; no operational approvals are claimed
**Purpose:** Preserve why the product direction was selected, which evidence supports it, and what must be true before the next gate.

| ID | Stage | Decision | Evidence / rationale | Owner | Status / next gate |
|---|---|---|---|---|---|
| D-01 | 00–01 | Bound the evidence to location-specific July 2026 reports. | ECL-01–ECL-05; no network denominator | Product + Food Safety | Locked; validate with internal data |
| D-02 | 02 | Select Verified Hygiene Check for validation, while retaining physical audits. | Qualitative screen plus RICE input gate; recurring control categories | Product + Operations | Selected; formal RICE requires cohort/effort inputs |
| D-03 | 03–04 | Use AI for visible-control triage and recommendations, not autonomous regulatory release. | ECL-07–ECL-08; human decision rights and safety policy | Food Safety + Product | Locked for MVP |
| D-04 | 03–06 | Keep random, off-cycle physical audits as an independent challenge. | Remote evidence can be staged and cannot prove all risks | Food Safety + Security | Mandatory control |
| D-05 | 00, 04, 06 | Use cost per verified-control store-day as the economic gate. | Stage 00 cost model; AI cost is only one line | Finance + Product | Inputs `TBD`; required before scale |
| D-06 | 05–06 | Use the sequence: data readiness → offline evaluation → 4-week shadow → 8-week human-gated pilot → automation gate → scale. | Safety, integrity, workload, privacy, and cost gates | Product + Food Safety | Proposed; not executed |
| D-07 | 03, 06–07 | Keep customer-facing verification detail deferred until independent validation. | Avoid false reassurance and uncalibrated trust claims | Product + Legal | Deferred |
| D-08 | 03 | Use the existing editable SVG as the current low-fidelity design source. | User decision; no Figma/production UI claim | Product + Design | Current source; usability testing pending |

## Decision hygiene

- Every material change must record the prior decision, new evidence, owner, and re-entry or rollback criterion.
- A proposed threshold is not a result; a planning cost is not an actual invoice; a public report is not a prevalence estimate.
- A decision cannot advance to launch if a safety, integrity, privacy, workload, or cost gate is unresolved.

## Stage 07 decision-log gate

**Decision:** Use this log as the cross-stage decision source of truth.

**Recommendation:** Link stage artifacts and live work items to decision IDs rather than repeating rationale in isolated documents.

**Evidence:** The log makes the conditional product recommendation and its dependencies explicit.

**Open questions:** Named approvers, Zepto data access, and final RICE inputs remain outstanding.

**Approval request:** Approve the log structure for implementation planning and future post-pilot updates.
