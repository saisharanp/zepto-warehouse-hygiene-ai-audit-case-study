# Stage 05 — Validation Metric Dictionary and Sampling Plan

**Status:** Proposed measurement design; no results populated
**Purpose:** Define the unit of analysis, sampling logic, label quality, and metric calculations before the shadow evaluation begins
**Related artifacts:** [Validation protocol](50_validation_protocol.md), [pilot scorecard](52_pilot_scorecard.md)

## Measurement principles

- Measure safety-critical categories separately; aggregate accuracy cannot hide a weak category.
- Keep holdout data, threshold definitions, and decision rules frozen before reviewing final results.
- Report both operational performance and evidence-integrity performance.
- Separate model output from the authorised human decision.
- Treat `unknown`, incomplete, and suspicious sessions as observable outcomes, not missing data.
- Do not claim complaint reduction without a documented denominator and a baseline or comparison cohort.
- During shadow mode, measure the counterfactual AI recommendation separately from the human decision; no autonomous pass is enabled.

## Unit of analysis

| Unit | Definition | Used for |
|---|---|---|
| Evidence item | A labelled finding opportunity at a frame, timestamp, zone, or structured record | Category recall, precision, false-pass analysis |
| Session | One submitted or attempted verified walkthrough | Completion, integrity, route coverage, manager time |
| Critical decision | One authorised hold/release/physical-check decision for an affected scope | Critical false-pass and decision safety |
| Remediation task | One corrective action with owner, SLA, and required re-check | Closure and time-to-contain |
| Store-day | One store operating day with a complete verified control and no unresolved critical issue | North Star and cost-to-outcome |
| Relevant order | An order containing the affected category or originating from the affected store/time window, as defined by Analytics | Complaint and customer-outcome rates |

## Metric definitions

| Metric | Formula | Required segmentation | Decision use |
|---|---|---|---|
| Critical finding recall | True critical findings detected / all adjudicated critical findings present | Finding category, layout, device, lighting, store | Must pass per category before any automation |
| Critical false-pass rate | Critical cases receiving a no-critical-issue AI recommendation / all adjudicated critical cases evaluated | Finding category, reviewer, store risk | Any unexplained breach pauses automation |
| False-fail rate | Non-critical or clean cases incorrectly held / all clean or non-critical cases evaluated | Store, manager, category, lighting | Controls manager burden and operational disruption |
| Unknown rate | Sessions or findings returned as unknown / sessions or findings evaluated | Category, device, quality, model version | High unknown may require better capture or narrower scope |
| Route coverage | Required checkpoints completed with acceptable quality / required checkpoints | Zone, store layout, device, network state | Determines whether a session is complete |
| Integrity review rate | Sessions routed to integrity review / attempted sessions | Failure type, device, location, store | Detects spoofing, broken controls, or excess friction |
| Due-check SLA | Due sessions completed within configured window / due sessions | Store, region, shift, manager tenure | Measures operational adoption |
| Manager completion time | Median and p95 start-to-submit time for valid sessions | Device, layout, connectivity, manager | Sets workload and staffing decisions |
| Time to contain | Median time from critical detection to approved hold/containment | Finding category, store, shift | Safety response metric |
| Critical remediation closure | Critical tasks closed with valid re-check within SLA / critical tasks due | Store, licensee, category | Determines whether detection produces action |
| Virtual/physical disagreement | Material finding or verdict disagreement / matched virtual/physical checks | Finding category, auditor, store risk | Calibrates trust and sampling |
| Severe hygiene complaint rate | Relevant severe complaints / 10,000 relevant orders | Store, category, cohort, period | Customer outcome; never use without baseline/control |
| Privacy incident rate | Confirmed privacy incidents / sessions or raw-media accesses | Incident type, role, surface | Zero-tolerance safety gate |
| Cost per verified-control store-day | Total program cost / verified-control store-days | Cohort, month, rollout phase | Business case and scale gate |

## Sampling plan

### Offline labelled holdout

- Split by store, not only by frame, to reduce layout leakage.
- Include ambient, chilled, frozen, produce, quarantine, dispatch, and records evidence where applicable.
- Stratify by device class, lighting, occlusion, clutter, camera motion, connectivity, and known finding category.
- Include clean controls and hard negatives so the model is not rewarded for flagging every cluttered frame.
- Include deliberately staged/incomplete examples only as a separate integrity challenge set; do not mix them into hygiene prevalence estimates.
- Do not accept a category-level safety result when the category has too few adjudicated positive examples; add evidence or mark the gate as not evaluable.

### Shadow cohort

Select stores after reviewing baseline data and document inclusion/exclusion reasons. Ensure variation in:

- store size and layout;
- risk level, including low-risk stores;
- device and connectivity;
- manager/licensee tenure;
- operating region and shift;
- prior complaints, holds, and physical-audit history.

Do not rely only on volunteers. If volunteer participation is necessary, label the bias and add risk-triggered or randomly selected stores where legally and operationally appropriate.

### Human label quality

- Three reviewers independently label the calibration set.
- Two independent reviewers label every critical or unknown case.
- Preserve original labels, final adjudication, evidence frame, rationale, and reviewer role.
- Report category-level agreement and disagreement reasons before model threshold tuning.
- If agreement is weak, revise the policy/checklist before interpreting model performance.

### Denominator and sample-size gate

| Measure | Required denominator | Readiness rule |
|---|---|---|
| Critical recall | Adjudicated positive evidence items by finding category | QA/Analytics sets a minimum positive-case count before holdout freeze; below-minimum categories are not evaluable |
| Critical false-pass | All adjudicated critical cases for which the AI would recommend no critical issue | Include counterfactual recommendations even while human review controls the decision |
| Route coverage | All required checkpoints for every attempted session | Count missing, skipped, rejected, and re-scanned checkpoints explicitly |
| Integrity | All attempted sessions, including rejected or incomplete attempts | Report by failure type, device, connectivity, store, and cohort |
| Severe complaints | Relevant severe complaints / relevant orders × 10,000 | Require baseline, comparison cohort, time window, category scope, and uncertainty estimate before causal interpretation |
| Cost per verified-control store-day | Total program cost / qualifying store-days | Include one-time, fixed, people, infrastructure, audit, remediation, privacy/security, and incident costs |

The illustrative 20-store/eight-week pilot shape is not automatically powered to detect a 20% complaint reduction. Analytics must complete an effect-size and power/precision assessment—or explicitly label the result directional—before customer-outcome claims are made.

## Decision rules

1. A critical category below the recall threshold is a fail even if aggregate recall passes.
2. Any unexplained critical false pass, customer-harm signal, or material privacy incident pauses automation.
3. A high false-fail or unknown rate triggers workflow/model refinement, not threshold loosening without review.
4. Complaint trends are directional until baseline, comparison cohort, seasonality, and order denominator are established.
5. Metrics must be exported with model version, policy version, cohort manifest, and data-freeze date.

## Required evidence package

- Frozen cohort and holdout manifests.
- Label guide, reviewer calibration, and adjudication report.
- Confusion matrix by critical category.
- Integrity-challenge results.
- Metric export with denominators and segmentation fields.
- Manager time-on-task and completion report.
- Remediation and re-check export.
- Privacy/access/deletion audit.
- Signed go/no-go decision log.
