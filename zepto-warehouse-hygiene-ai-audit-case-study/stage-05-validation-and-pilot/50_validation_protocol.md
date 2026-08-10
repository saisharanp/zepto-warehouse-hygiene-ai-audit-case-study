# Stage 05 — Validation and Pilot Protocol

**Product:** Verified Hygiene Check  
**Scope:** Zepto dark stores / warehouse operations  
**Status:** Proposed protocol; not executed  
**Decision requested:** Approve data preparation and shadow-mode setup

## Objective

Test whether a guided, location-verified phone walkthrough can reliably identify visible hygiene-control failures without creating unsafe auto-passes, unacceptable privacy exposure, or excessive manager workload.

This stage validates the control system—not whether Zepto is currently compliant. No live Zepto data, model output, pilot result, or customer outcome is claimed here.

Use the [metric dictionary and sampling plan](53_metric_dictionary_and_sampling_plan.md) to freeze units of analysis, denominators, label quality, cohort strata, and decision rules before evaluation.

## Inputs required before execution

1. De-identified inspection images/video and adjudicated findings from representative store layouts.
2. Current Zepto hygiene SOPs, severity definitions, cold-chain requirements, FEFO/expiry rules, and escalation policy.
3. Store metadata: zone map, operating hours, licencee/store relationships, and available temperature-log interfaces.
4. Privacy, security, labour, and legal review of capture, retention, access, and worker notice.
5. A labelled holdout set containing poor lighting, occlusion, clutter, camera shake, empty shelves, staged scenes, and incomplete routes.
6. Human reviewers trained to apply the same checklist independently.

## Evaluation design and denominator gate

- **Offline holdout:** The denominator for critical recall is adjudicated positive evidence items by finding category. Each category must meet the minimum positive-case count approved by QA/Analytics; otherwise mark the category **not evaluable**, not passed.
- **Shadow mode:** The denominator for completion and integrity metrics is every attempted session, including incomplete and rejected attempts. The denominator for counterfactual false-pass is every adjudicated critical case evaluated.
- **Controlled pilot:** The illustrative 20-store/eight-week shape is a planning example, not a powered sample size. Analytics must pre-register the cohort, comparison method, effect size, power or precision target, and minimum observation window before using complaint outcomes.
- **Customer outcomes:** Severe hygiene complaints must use relevant orders as the denominator and include baseline, comparison cohort, seasonality, affected-category scope, and confidence intervals where appropriate.
- **Decision discipline:** Process metrics can establish operational readiness; they cannot by themselves prove fewer incidents or increased customer trust.

## Hypotheses and tests

| ID | Hypothesis | Test | Pass threshold |
|---|---|---|---|
| H1 | The workflow can detect clearly visible critical findings. | Model evaluation on adjudicated holdout set, segmented by finding type. | ≥95% recall for each critical category; no category may be averaged away. |
| H2 | The system avoids unsafe pass recommendations. | Blinded human/physical audit of counterfactual sessions that the proposed policy would classify as no-critical-issue. | Critical false-pass rate ≤1%. |
| H3 | A scan can prove facility/session integrity better than self-attestation. | Replay, gallery-upload, mock-location, QR/NFC mismatch, device-integrity, and interrupted-session tests. | 100% of deliberately invalid test cases rejected or routed to human review. |
| H4 | Managers can complete a full route without material operational burden. | Task-based shadow study with observed completion time and error logging. | Median completion time ≤15 minutes; ≥90% of due sessions within SLA. |
| H5 | Findings lead to remediation. | Shadow-to-operations replay: assign owner, SLA, hold scope, and re-check. | ≥95% of critical remediation tasks closed within SLA during pilot. |
| H6 | The workflow improves real-world control, not just documentation. | Controlled pilot against baseline/matched comparison cohort with a pre-registered denominator and analysis plan. | Exploratory directional signal only; a ≥20% reduction may be a planning aspiration after baseline and power/precision review, not an automatic launch gate. |

Thresholds are proposed go/no-go criteria, not results.

## Test sequence

### A. Checklist and label calibration

1. Map every checklist item to the applicable SOP and food-safety requirement.
2. Define critical, major, minor, incomplete, and unknown states.
3. Have at least three trained reviewers label the same calibration set independently.
4. Adjudicate disagreements and record the reason for the final label.
5. Freeze the test set before model evaluation.

### B. Offline model evaluation

Run the model on a labelled holdout set. Report precision, recall, false-pass rate, false-fail rate, coverage score, and confidence calibration separately for:

- pest evidence;
- visible contamination/fungal growth;
- stagnant water or food exposure;
- food directly on floor / missing pallets;
- food/non-food segregation;
- expiry/quarantine evidence;
- cold-storage display and log reconciliation;
- route completeness and image quality;
- evidence-integrity failures.

The model must be allowed to return **unknown**. Unknown is safer than a forced pass when the frame is blurred, occluded, too dark, or ambiguous.

### C. Shadow mode

For a proposed four-week period, managers complete real scans in a documented mixed cohort covering store layout, risk level, device, connectivity, manager tenure, and operating context. Volunteer participation may be used only where necessary and must be recorded as a sampling limitation. AI produces findings, but the QA reviewer makes every operational decision. A separate reviewer samples sessions for route coverage, integrity, and false negatives. Physical spot checks are unannounced to the store team where legally and operationally appropriate.

No autonomous pass is enabled in shadow mode. Evaluate the counterfactual AI recommendation against adjudicated findings so the critical false-pass gate remains measurable without turning the pilot into an unapproved safety decision system.

Shadow mode must log:

- scheduled, started, and completed timestamps;
- store and licencee identifiers;
- location, QR/NFC, device-integrity, and session signals;
- zone coverage and random prompts;
- AI findings, confidence, and model version;
- human finding, rationale, and final adjudication;
- remediation task, owner, SLA, and re-check;
- privacy/security exception and retention expiry.

### D. Pilot readiness review

Advance to a controlled operational pilot only when:

- H1–H4 pass;
- all critical false passes are explained and below threshold;
- QA, Food Safety, Security, Privacy, and Legal have signed the checklist and data handling plan;
- the incident and rollback runbook has an owner and tested contact path;
- licensee/store managers have training and a remediation budget;
- customer communication and affected-SKU hold rules are approved.

### E. Controlled operational pilot

Run the approved eight-week human-gated pilot only after the offline and four-week shadow gates pass. The illustrative 20-store/two-checks-per-week shape must be resized using the baseline, capacity model, comparison design, and a pre-registered power or precision assessment. Human reviewers make every operational decision; this phase does not enable autonomous pass or a customer-facing badge.

## Evaluation rules

- Count findings at the issue level, not only at the session level.
- Report performance by store layout, camera/device class, lighting, and finding category.
- Keep the test set and threshold definitions fixed before looking at results.
- Do not tune thresholds against the final holdout set.
- A high aggregate accuracy score cannot offset a critical false pass.
- Any regulator, customer-harm, or privacy incident pauses the evaluation while investigated.
- AI output is a workflow recommendation; regulatory findings and final safety decisions remain with authorised humans and authorities.

## Data and privacy controls

- Capture video/audio only when required; default to no audio.
- Blur faces and personal identifiers before general QA access.
- Restrict raw media access to a named, approved team.
- Store evidence only for the approved retention period; retain derived audit facts longer only if justified.
- Do not use the recordings for worker performance scoring or facial recognition.
- Maintain a data inventory, access log, deletion job, incident process, and worker notice.

## Stage 05 decision gate

**Decision:** Proceed to data preparation and shadow-mode setup; do not claim a product pilot or launch.  
**Recommendation:** Approve the protocol, synthetic replay, and scorecard as the working validation package.  
**Evidence:** July 2026 reporting describes recurring hygiene-control findings across multiple Hyderabad Zepto locations, but there is no internal performance data for the proposed AI workflow.  
**Open questions:** What real labelled media exists? Which findings require sensors or physical sampling? What are the current check cadence, baseline complaint rate, and remediation SLAs?  
**Approval request:** Approve collection of the required de-identified inputs and the four-week shadow-mode setup.
