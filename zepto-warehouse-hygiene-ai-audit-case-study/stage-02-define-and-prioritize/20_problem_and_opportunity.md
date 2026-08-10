# Stage 02 — Define and Prioritize

Decision rationale is recorded in the [Stage 07 decision log](../stage-07-final-handoff/73_decision_log.md); the evidence basis is controlled by the [claim ledger](../stage-00-research-setup/01_evidence_claim_ledger.md).

## Problem statement

Zepto customers need confidence that food and household products were stored hygienically, but central operations may discover failures only through a surprise inspection, a regulator visit, or a customer complaint. Managers need a practical way to show the current state of a facility; quality teams need evidence that is frequent, complete, and difficult to stage.

## Jobs to be done

- **Customer:** When I order food from a dark store, help me believe it was handled safely so I can use quick commerce without anxiety.
- **Store manager:** When a check is due, help me complete the right scan quickly and fix what is wrong so the store stays compliant and operational.
- **Quality lead:** When risk changes at a store, show me reliable evidence and give me a clear action so I can intervene before harm or enforcement.

## Opportunity-solution tree

**Desired outcome:** Fewer severe hygiene exceptions reach customers and more customers trust Zepto’s food handling.

→ Increase check frequency between physical inspections  
→ Verify the check occurred at the correct facility  
→ Detect visible hygiene and storage risks earlier  
→ Close remediation with ownership and evidence  
→ Preserve independent oversight and transparency

## Opportunity prioritization

Prioritize the outcome gaps before comparing solution concepts. The source set supports investigating these gaps, but not estimating their network-wide frequency.

| Opportunity | User / outcome served | Evidence basis | Priority decision |
|---|---|---|---|
| Increase check frequency between physical inspections | Quality lead can intervene earlier; customers face fewer severe exceptions | ECL-01–ECL-04; inspection and complaint signals are point-in-time | Primary opportunity |
| Verify that a check occurred at the correct facility | Quality and Security can trust the provenance of an internal check | ECL-07 plus evidence-staging risk | Primary opportunity |
| Detect visible hygiene/storage risks earlier | Manager and QA can contain risk before it reaches picking or delivery | ECL-03; visible control categories recur in reports | Primary opportunity |
| Close remediation with ownership and evidence | Operations can show that a finding was fixed, not just recorded | Stage 01 journey analysis; internal SLA still unknown | Required enabler |
| Improve customer confidence | Customer receives credible recovery and restrained verification detail | Hypothesis only; no customer baseline | Downstream outcome, not the MVP control |

## Qualitative pre-RICE solution screen

This is a directional screen used while Reach and Effort inputs are unavailable. Impact, confidence, and effort use an assumed 1–5 scale; higher impact/confidence and lower effort are better. It is not a RICE score and must not be presented as one.

| Option | Impact | Confidence | Effort | Decision |
|---|---:|---:|---:|---|
| Routine verified phone walkthrough + AI triage | 5/5 | 3/5 | 3/5 | Select for validation |
| Increase scheduled physical inspections only | 4/5 | 4/5 | 5/5 | Keep as independent control |
| Permanent CCTV / IoT sensors everywhere | 4/5 | 2/5 | 5/5 | Defer; high cost and privacy burden |
| Self-attested checklist with photo upload | 2/5 | 3/5 | 1/5 | Reject; weak provenance |
| Public hygiene badge without new control loop | 2/5 | 2/5 | 1/5 | Reject; false reassurance risk |

## RICE prioritization

Use RICE to compare solution investment after the qualitative screen:

```text
RICE score = Reach × Impact × Confidence ÷ Effort
```

| Input | Definition for this case study | Required evidence |
|---|---|---|
| Reach | Number of store-checks or store-weeks affected during the agreed decision period; use one unit consistently across options | Approved cohort, cadence, and rollout window |
| Impact | 0.25 = minimal, 0.5 = low, 1 = medium, 2 = high, 3 = massive effect on fewer severe hygiene exceptions | Food Safety/Product outcome mapping |
| Confidence | 0–100% confidence that the impact and reach assumptions are credible; use the evidence ledger, not model confidence | Evidence IDs, internal baseline, or experiment evidence |
| Effort | Person-months across Product, Engineering, ML, QA, Security, Operations, Privacy/Legal, and rollout | Team estimates with dependencies and capacity |

The current public evidence does not supply a defensible Reach denominator or Zepto effort estimate. Therefore, the table below is intentionally not scored yet:

| Option | Reach | Impact | Confidence | Effort | RICE score | Current decision |
|---|---:|---:|---:|---:|---:|---|
| Routine verified phone walkthrough + AI triage | TBD | TBD | TBD | TBD | Not calculable | Select for offline/shadow validation |
| Increase scheduled physical inspections only | TBD | TBD | TBD | TBD | Not calculable | Retain as independent control |
| Permanent CCTV / IoT sensors everywhere | TBD | TBD | TBD | TBD | Not calculable | Defer pending cost/privacy evidence |
| Self-attested checklist with photo upload | TBD | TBD | TBD | TBD | Not calculable | Reject on provenance risk |
| Public hygiene badge without new control loop | TBD | TBD | TBD | TBD | Not calculable | Reject until control is validated |

Do not invent RICE numbers to create false precision. Populate the table after Zepto confirms the pilot cohort, expected check cadence, cross-functional effort, and outcome baseline. Until then, the recommendation is based on the qualitative screen and the evidence ledger.

## Selected opportunity

Build **Verified Hygiene Check**: a risk-based, in-app live walkthrough that captures multiple location/session signals, checks route completeness, uses AI to flag visible issues, creates containment/remediation work, and routes critical or ambiguous cases to human review.

## Non-goals

- Replace FSSAI or state food-safety inspection.
- Certify microbiological safety, allergens, smell, or sealed-package contents from video.
- Use facial recognition or worker surveillance.
- Treat GPS metadata as proof by itself.
- Launch a customer-facing “safe warehouse” badge before independent validation.

## Stage 02 decision gate

**Decision:** Proceed to solution design.

**Recommendation:** Validate a small, evidence-integrity-first workflow before investing in sensors or a public trust badge; populate the RICE inputs before committing to build or scale.

**Evidence:** The opportunity addresses the recurring control categories while preserving physical and regulatory checks.

**Open questions:** Which visible controls can be evaluated reliably by phone video, which require sensors or physical sampling, who owns containment authority, and what are the approved Reach and Effort inputs for RICE?

**Approval request:** Approve Verified Hygiene Check as the selected opportunity and carry the rejected inspection-only, sensors-everywhere, and badge-only alternatives into the decision log.
