# Stage 04 — Product Delivery: PRD and Technical Contract

## Product goal

Increase the frequency and credibility of hygiene controls between physical inspections, while reducing unsafe passes and making remediation accountable.

## Product decision

Build **Verified Hygiene Check** as a human-gated control system for visible hygiene and evidence integrity. AI may triage evidence and recommend a workflow state; it must not be presented as a regulatory certificate or as proof of microbial safety.

### Primary user and decision owner

| Role | Product job | Decision authority |
|---|---|---|
| Primary: Central Quality / Food Safety lead | See which stores need intervention and make an evidence-backed containment decision | Can hold/release affected scope or order a physical check under approved policy |
| Secondary: Store manager / licensee operator | Complete a valid route and resolve corrective actions without guessing what evidence is required | Can capture, explain, and remediate; cannot override a failed or suspicious outcome |
| Supporting: QA reviewer | Adjudicate critical, ambiguous, and integrity-exception cases | Can change severity, request evidence, hold, release, or escalate |
| Supporting: Support / Incident response | Connect a hygiene event to affected orders and approved customer communication | Can activate incident and customer-support playbooks |

### Product outcomes

| Outcome | Leading measure | Guardrail |
|---|---|---|
| More complete controls between physical inspections | Due checks completed within SLA; route coverage | Manager completion time and fulfilment disruption |
| Fewer unsafe passes | Category-level critical recall; critical false-pass rate | No critical or low-confidence auto-pass |
| Faster accountable recovery | Time to contain; critical remediation closure; re-check completion | No release without authorised decision and evidence |
| More trustworthy evidence | Valid-session rate; integrity exceptions; virtual/physical disagreement | Privacy incidents, staging pattern, or regulator objection |
| Better customer confidence | Severe hygiene complaints per 10,000 relevant orders versus baseline/control | Do not expose a public trust claim before independent validation |

### Non-goals for this release

- Replace FSSAI, state food-safety, or independent physical inspection.
- Certify microbial safety, odour, allergens, concealed pests, or complete cold-chain conditions from video.
- Use facial recognition, worker productivity scoring, or unrelated model training.
- Give a manager the ability to self-approve a failed, unknown, or suspicious session.
- Publish an “AI certified” or “safe warehouse” badge before the Stage 05 and Food Safety gates pass.

## MVP scope

### In scope

- Risk-based task creation and due windows.
- Secure in-app live capture with no gallery upload.
- Layered facility/session integrity: device, location, QR/NFC, route, prompt, timestamp, and tamper-evident evidence.
- Guided coverage of receiving, ambient, chilled/frozen, quarantine/returns, and dispatch zones.
- AI triage for visible controls, image quality, route completeness, and `unknown` states.
- QA reviewer console with evidence, policy/model version, rationale, and decision history.
- Remediation, affected-scope hold, re-check, release authority, and audit trail.
- Random independent physical challenges and disagreement reporting.

### Deferred until validated

- Customer-facing verification detail.
- Narrow low-risk auto-pass for a separately approved subset.
- Automated inventory/order holds beyond the policy-approved integration.
- Broad sensor ingestion, permanent CCTV, or network-wide rollout.
- Model training on operational recordings beyond the approved data purpose.

## MVP requirements

| ID | Priority | Requirement | Testable acceptance criteria |
|---|---|---|---|
| VHC-01 | P0 | Risk-based tasking | Given an approved cadence, risk trigger, store cohort, and policy version, when a task is created, then the system stores the trigger, due window, required route, owner, and escalation SLA. Duplicate tasks must be idempotent. |
| VHC-02 | P0 | Secure capture | Given a valid task, when the manager starts capture, then gallery selection is unavailable, the session receives a signed start event, and interruption/replay attempts are recorded and routed to the configured outcome. |
| VHC-03 | P0 | Facility/session verification | Given a manager inside a store, when the session is started, then geofence, rotating QR/NFC, device/session signals, and task identity are reconciled; GPS alone cannot produce a valid session. |
| VHC-04 | P0 | Guided coverage | Given a required route, when a zone is captured, then the app records the zone checkpoint, quality result, timestamp, prompt response, and coverage status; missing or insufficient evidence blocks submission or creates an explicit human-review state. |
| VHC-05 | P0 | Explainable AI triage | Given valid media and structured records, when analysis completes, then each finding contains category, severity suggestion, evidence frame/timestamp, confidence, `unknown` eligibility, model version, policy version, and processing status. |
| VHC-06 | P0 | Safe decisioning | Given a critical, low-confidence, ambiguous, or integrity-exception case, when a decision is requested, then the system cannot auto-pass it and must route it to an authorised reviewer or physical-check path. |
| VHC-07 | P0 | Remediation and re-check | Given a hold or corrective action, when a reviewer saves the decision, then the system creates affected scope, owner, SLA, corrective action, containment status, and re-check requirements; release requires authorised approval. |
| VHC-08 | P0 | Audit trail | Given any evidence, model, reviewer, verdict, hold, release, or deletion event, then the system preserves a time-ordered audit record with actor, reason, policy/model version, and evidence references subject to retention policy. |
| VHC-09 | P0 | Privacy and worker safeguards | Given capture is enabled, then audio is off by default, notice and lawful basis are recorded, raw access is role-restricted, faces/personal screens are redacted for broad review, and deletion is verifiable. |
| VHC-10 | P1 | Independent challenge | Given an approved sampling plan, when a store/session is selected, then the system creates an unannounced human or physical challenge task and reports virtual/physical disagreement by finding category and store context. |

## Data contract

### Required check record

| Field group | Required fields | Rule |
|---|---|---|
| Identity | `check_id`, `task_id`, `store_id`, `study_store_id`, `licensee_id` | Use study IDs for validation exports; keep identity mapping access-controlled |
| Task | `scheduled_at`, `due_at`, `trigger_type`, `risk_reason`, `policy_version` | Task creation is idempotent and time-bounded |
| Session | `started_at`, `ended_at`, `device_attestation`, `location_signals`, `challenge_result`, `session_integrity_state` | GPS alone cannot establish validity |
| Coverage | `zone_checkpoints`, `prompt_events`, `coverage_score`, `quality_state`, `route_version` | Record missing, skipped, and re-scanned zones explicitly |
| Evidence | `media_manifest`, `media_hashes`, `frame_timestamps`, `audio_state`, `redaction_state`, `retention_expiry` | Raw media and derived findings have separate access and retention rules |
| AI | `finding_type`, `severity_suggestion`, `confidence`, `unknown_reason`, `model_version`, `processing_status` | AI output is a recommendation, not the final regulatory verdict |
| Human decision | `verdict`, `reviewer_id`, `reviewer_rationale`, `decision_at`, `hold_scope`, `escalation_type` | Critical/ambiguous/integrity cases require authorised review |
| Context | `temperature_log_reference`, `expiry_sample_reference`, `inventory_scope_reference`, `complaint_trigger_reference` | Video-only claims must not be used where sensor, inventory, or physical evidence is required |
| Recovery | `remediation_id`, `recheck_id`, `release_authority`, `release_at` | A hold cannot close without a re-check or approved exception |

### State model

```text
Tasked
  → Started
  → Integrity verified / Integrity exception
  → Capturing
  → Submitted / Incomplete
  → AI triage
  → Human review (critical, unknown, low confidence, disagreement, or suspicious session)
  → Verified-no-critical-issue / Hold-pending-review / Physical-check-required
  → Remediation
  → Re-check
  → Released / Hold-extended / Escalated
```

`unknown`, `incomplete`, and `integrity exception` are first-class states. They must never be coerced into `Verified-no-critical-issue` to improve completion metrics.

### Event contract

Every event includes `event_id`, `event_name`, `occurred_at`, `actor_role`, `check_id`, `task_id`, `store_id` or study-store ID, `policy_version`, and a privacy-safe correlation ID.

| Event | Required properties | Primary consumer |
|---|---|---|
| `task_created` | Trigger, risk reason, due window, route version | Operations / Analytics |
| `session_started` | Notice version, device state, location/challenge state | Security / Privacy |
| `zone_completed` | Zone, prompt, quality, coverage, retry count | Product Ops |
| `session_submitted` | Completeness, integrity state, media manifest | QA / ML |
| `ai_triage_completed` | Model version, findings, confidence, unknown reason, latency | ML / QA |
| `reviewer_decision_saved` | Verdict, rationale, reviewer role, hold scope | Food Safety / Audit |
| `remediation_created` | Owner, SLA, corrective action, affected scope | Operations |
| `recheck_completed` | Evidence, decision, release authority, disagreement | QA / Food Safety |
| `privacy_or_integrity_exception` | Exception type, severity, action, escalation | Privacy / Security |

Do not place worker names, customer identifiers, raw location trails, or raw media in analytics events.

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

### QA / Food Safety reviewer

As a QA or Food Safety reviewer, I want the evidence, AI rationale, policy version, and operational context in one review surface so I can make a defensible hold, release, or escalation decision.

**Acceptance:** I can see the original evidence, timestamps, route completeness, temperature/expiry references, prior decisions, and remediation history; critical decisions require a rationale and cannot be saved without an authorised role.

### Security / Privacy lead

As a Security or Privacy lead, I want integrity, access, retention, and worker-notice events to be observable so I can investigate misuse without exposing raw media broadly.

**Acceptance:** I can query access, export, deletion, mock-location, replay, challenge, and policy-version events by case; raw-media access is role-restricted and every export is logged.

## Permissions and decision rights

| Action | Manager / licensee | QA reviewer | Food Safety lead | Security / Privacy | Support |
|---|---|---|---|---|---|
| Start and submit capture | Yes | No | No | No | No |
| Add remediation evidence | Yes | Yes | Yes | No | No |
| Change severity or verdict | No | Yes | Yes for policy-defined critical scope | No | No |
| Place affected scope on hold | No, may contain locally | Yes within policy | Yes / escalate | No | No |
| Release a critical hold | No | Yes if authorised | Yes | No | No |
| View raw media | Limited to own submitted evidence | Approved cases only | Approved cases only | Incident access | No by default |
| Request physical inspection | No | Yes | Yes | Yes for integrity incident | Yes via trigger |
| Export evidence | No | Approved export | Approved export | Incident/legal basis | No |

## Non-functional requirements

| Area | Requirement | Evidence before release |
|---|---|---|
| Reliability | Capture must support resumable upload or a clearly documented recovery path for supported connectivity conditions; interrupted sessions cannot silently submit. | Device/network test report and retry telemetry |
| Security | Encrypt media in transit and at rest, use least-privilege access, sign task/session events, and detect replay/mock location where the device platform supports it. | Threat model, penetration/security review, invalid-session report |
| Privacy | Audio off by default; purpose limitation, notice, redaction, retention, deletion, access log, and incident route are implemented before operational recording. | Privacy/Legal approval and deletion verification |
| Accessibility | Touch targets, contrast, labels, status text, and error recovery meet the approved accessibility baseline; no status depends on colour alone. | Accessibility review on supported devices |
| Localization | Manager prompts and remediation guidance support the approved operating languages; policy terms remain unambiguous after translation. | Language review and task usability test |
| Observability | Every state transition has a correlation ID, timestamp, owner, and alert route; model/policy changes are versioned. | Event replay and dashboard verification |
| Data lifecycle | Raw media, derived findings, and audit facts have separate retention and deletion rules. | Data inventory, access audit, deletion job output |

Candidate performance and availability targets should be set after the device/connectivity baseline is measured; the team must not invent a target that the lowest supported device cannot meet.

## Dependencies and delivery risks

| Dependency / risk | Why it matters | Mitigation / gate |
|---|---|---|
| Inventory and order-hold integration | A finding is not useful if affected stock continues to be picked. | Start with manual hold workflow; integrate only after policy and scope mapping pass |
| Temperature and cold-chain evidence | Video cannot prove continuous temperature. | Require trusted sensor/log reference or route to human/physical review |
| Device integrity capability | Root/mock-location/replay signals vary by device and OS. | Define supported-device matrix and fail-safe fallback |
| QR/NFC installation and replacement | Physical challenge can fail through damage, relocation, or stale tags. | Ownership, rotation, tamper inspection, and replacement SLA |
| Worker notice and retention | Recording may capture faces, voices, badges, and sensitive layout. | Privacy/Legal/labour sign-off before any operational capture |
| QA review capacity | Human gating can become the bottleneck during spikes. | Capacity model, queue SLA, overflow owner, and stop condition |
| Licensee incentives | Punitive-only workflows can drive avoidance or staging. | Pair alert with remediation support and independent challenge |
| Model/provider change | A model update can change recall or evidence format. | Version pinning, regression set, change log, and re-gate |

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

| Phase | Exit evidence | Decision owner |
|---|---|---|
| 1. Policy mapping and data review | Checklist/SOP mapping, label guide, data inventory, privacy basis, and hold policy | Food Safety + Privacy/Legal |
| 2. Secure capture and integrity prototype | Supported-device matrix, session state machine, invalid-session tests, upload recovery | Engineering + Security |
| 3. Checklist and human-review console | Wireframes validated, reviewer task flow, decision audit log, remediation handoff | Product + QA |
| 4. Shadow-mode model integration | Frozen model/policy versions, event contract, quality/unknown handling, queue capacity | ML + QA + Operations |
| 5. Offline evaluation and launch-readiness gate | Category metrics, scorecard, rollback test, cost sheet, training, and owner sign-off | Product + Food Safety |

## Cost-to-outcome decision

Use the Stage 00 rupee model as an input to the PRD rather than reporting AI inference alone. The launch business case must show:

```text
Cost per verified-control store-day
= total operating + audit + remediation + platform cost
  / store-days with complete evidence, no unresolved critical issue,
    and completed remediation/re-check where required
```

The budget must separate one-time build, fixed platform, manager time, QA review, physical-audit allocation, remediation reserve, privacy/security, and incident capacity. Replace all planning placeholders with Zepto Finance/Procurement inputs before scale approval.

## Release-readiness checklist

| Gate | Required evidence | Owner |
|---|---|---|
| Policy and safety | Current SOP mapping, severity policy, critical hold/release authority | Food Safety |
| UX and workload | Wireframe usability test, manager time study, accessibility/language review | Product / Operations |
| Integrity | Invalid-session test report and threat-model mitigations | Security |
| Model safety | Frozen holdout, category recall, critical false-pass, unknown and calibration report | ML / QA |
| Operations | QA capacity, escalation contacts, remediation budget, physical-audit sample | Operations / QA |
| Privacy | Notice, lawful basis, access roles, retention/deletion proof, incident process | Privacy / Legal |
| Economics | Completed ₹ input sheet, pilot cash budget, run-rate, and stop-cost | Finance / Product |
| Rollback | Tested automation pause, evidence preservation, targeted physical-check path | Incident response |

## Stage 04 decision gate

**Decision:** Proceed to validation and pilot preparation.

**Recommendation:** Do not build automatic customer-facing trust claims until VHC-01 through VHC-10 and cross-functional review are complete.

**Evidence:** The PRD defines exception paths, evidence integrity, human decision authority, ownership, and release dependencies rather than treating AI output as a safety certificate.

**Open questions:** De-identified media availability, current SOP version, location/device capabilities, privacy basis, remediation budget, and integration ownership.

**Approval request:** Approve the PRD and delivery plan for offline evaluation and shadow-mode preparation, subject to the Stage 05 entry criteria.
