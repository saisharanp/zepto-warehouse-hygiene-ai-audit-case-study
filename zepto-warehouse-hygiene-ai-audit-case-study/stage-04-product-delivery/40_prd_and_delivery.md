# Stage 04 — Product Delivery: PRD and Technical Contract

## Product goal

Increase the frequency and credibility of hygiene controls between physical inspections, while reducing unsafe passes and making remediation accountable.

## MVP requirements

| ID | Requirement | Acceptance criteria |
|---|---|---|
| VHC-01 | Risk-based tasking | Configure cadence, risk triggers, due window, and store cohort. |
| VHC-02 | Secure capture | Reject gallery media; record signed timestamps; detect replay/interruption. |
| VHC-03 | Store verification | Record geofence, rotating QR/NFC, and device/session metadata; GPS alone cannot pass. |
| VHC-04 | Guided coverage | Require zones, random prompts, minimum quality, and route completeness. |
| VHC-05 | Explainable AI findings | Return finding type, evidence frame, confidence, model version, and unknown state. |
| VHC-06 | Safe decisioning | Critical or low-confidence cases never auto-pass. |
| VHC-07 | Remediation | Create owner, SLA, affected scope, corrective action, and re-check. |
| VHC-08 | Audit trail | Preserve evidence hashes, verdict changes, reviewer actions, and model versions. |
| VHC-09 | Privacy | No audio by default; blur faces; restrict access; define retention and worker notice. |
| VHC-10 | Independent challenge | Sample stores for unannounced human audits; report AI/human disagreement. |

## Data contract

`check_id`, `store_id`, `licensee_id`, `task_id`, `scheduled_at`, `started_at`, `ended_at`, `device_attestation`, `location_signals`, `zone_checkpoints`, `coverage_score`, `media_hashes`, `finding_type`, `severity`, `confidence`, `model_version`, `temperature_log_reference`, `expiry_sample_reference`, `verdict`, `reviewer_id`, `remediation_id`, `recheck_id`, `retention_expiry`.

## User stories

### Manager

As a store manager, I want a guided route with clear evidence prompts so I can complete a correct check quickly.

**Acceptance:** I cannot submit if required zones are missing; the app tells me what to re-scan; I can see remediation tasks and deadlines; I cannot override the outcome.

### Quality lead

As a quality lead, I want findings ranked by severity and confidence so I can contain critical risk first.

**Acceptance:** Every finding has evidence, confidence, model/policy version, affected scope, owner, SLA, and reviewer history.

### Customer-support lead

As a support lead, I want complaint and return signals to trigger a risk-based re-check so recurring issues do not rely on manual escalation alone.

**Acceptance:** A configured complaint threshold can create a check task without exposing worker or customer personal data.

## Ownership

| Owner | Accountability |
|---|---|
| Product / Trust | Outcome, workflow, policy, customer communication |
| Food Safety / QA | Checklist, severity, adjudication, regulator interface |
| Store manager / licensee | Capture, containment, remediation |
| ML / computer vision | Model performance, drift, explainability, thresholds |
| Security | Device/session integrity and access controls |
| Privacy / Legal | Notice, lawful basis, minimisation, retention, worker review |
| Support / Incident response | Complaints, recalls, holds, escalation |

## Delivery plan

1. Policy mapping and data review.
2. Secure capture and evidence-integrity prototype.
3. Checklist and human-review console.
4. Shadow-mode model integration.
5. Offline evaluation and launch-readiness gate.

## Stage 04 decision gate

**Decision:** Proceed to validation and pilot preparation.

**Recommendation:** Do not build automatic customer-facing trust claims until VHC-01 through VHC-10 and cross-functional review are complete.

**Evidence:** The PRD defines exception paths, evidence integrity, human decision authority, ownership, and release dependencies rather than treating AI output as a safety certificate.

**Open questions:** De-identified media availability, current SOP version, location/device capabilities, privacy basis, remediation budget, and integration ownership.

**Approval request:** Approve the PRD and delivery plan for offline evaluation and shadow-mode preparation, subject to the Stage 05 entry criteria.
