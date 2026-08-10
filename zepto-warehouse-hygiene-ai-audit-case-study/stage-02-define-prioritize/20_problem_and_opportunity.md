# Stage 02 — Define and Prioritize

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

## Prioritization

Illustrative scores only; they are assumptions for selecting a pilot, not observed business metrics.

| Option | Impact | Confidence | Effort | Decision |
|---|---:|---:|---:|---|
| Routine verified phone walkthrough + AI triage | 5 | 3 | 3 | Select for validation |
| Increase scheduled physical inspections only | 4 | 4 | 5 | Keep as independent control |
| Permanent CCTV / IoT sensors everywhere | 4 | 2 | 5 | Defer; high cost and privacy burden |
| Public hygiene badge without new control loop | 2 | 2 | 1 | Reject; false reassurance risk |

## Selected opportunity

Build **Verified Hygiene Check**: a risk-based, in-app live walkthrough that captures multiple location/session signals, checks route completeness, uses AI to flag visible issues, creates containment/remediation work, and routes critical or ambiguous cases to human review.

## Non-goals

- Replace FSSAI or state food-safety inspection.
- Certify microbiological safety, allergens, smell, or sealed-package contents from video.
- Use facial recognition or worker surveillance.
- Treat GPS metadata as proof by itself.
- Launch a customer-facing “safe warehouse” badge before independent validation.

## Stage 2 gate

**Decision:** Proceed to solution design.  
**Recommendation:** Validate a small, evidence-integrity-first workflow before investing in sensors or a public trust badge.  
**Evidence:** The opportunity addresses the recurring control categories while preserving physical and regulatory checks.  
**Rejected alternatives:** Inspection-only, sensors everywhere, and badge-only approaches.
