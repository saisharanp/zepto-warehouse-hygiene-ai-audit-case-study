# Stage 03 — Solution Design: Verified Hygiene Check

## Service flow

```text
Risk engine schedules check
        ↓
Manager receives signed, time-bounded task
        ↓
Live in-app session: geofence + QR/NFC + device attestation
        ↓
Guided route: receiving → ambient → chilled/frozen → quarantine → dispatch
        ↓
AI checks coverage, quality, and visible control failures
        ↓
Pass / Fail-Hold / Human Review
        ↓
Remediation task + evidence + re-check
        ↓
Random physical audit calibrates and challenges the system
```

## Concept comparison

| Concept | Control value | Complexity / cost | Main risk | Decision |
|---|---|---|---|---|
| Verified phone walkthrough + AI triage | Increases check frequency and creates traceable evidence between physical inspections | Medium; uses existing manager phones plus capture, review, and audit operations | Route staging, device spoofing, and model blind spots | **Select for validation** |
| More scheduled physical inspections | Strong independent evidence and regulatory credibility | High travel, staffing, and scheduling burden | Delayed coverage and predictable inspection windows | **Retain as a control, not the sole solution** |
| Permanent CCTV / IoT sensors everywhere | Higher continuity for selected conditions | High deployment, privacy, maintenance, and integration burden | Cameras still miss concealed or non-visual risks | **Defer** |
| Self-attested checklist with photo upload | Low implementation effort | Low initial cost | Easy to stage, weak provenance, and delayed review | **Reject** |
| Customer-facing hygiene badge before calibration | Could communicate transparency | Low build effort but high trust and regulatory risk | False reassurance if the control is not validated | **Reject** |

## Service blueprint

| Blueprint layer | Trigger / touchpoint | Manager or quality action | System evidence | Failure path / owner |
|---|---|---|---|---|
| Risk and tasking | Cadence, complaint, return, temperature, pest, or prior finding creates risk | Quality configures scope and due window | `task_id`, risk reason, policy version, due time | Bad trigger or duplicate task → Product Ops |
| Manager preparation | Push notification opens a signed task | Manager reviews notice, permissions, route, and privacy controls | User/session ID, device state, notice version | Permission or device failure → Operations support |
| Verified capture | In-app camera, rotating QR/NFC, route checkpoints, random prompt | Manager records each required zone and re-scans weak evidence | GPS, challenge result, timestamps, coverage, media hashes | Missing zone, spoof signal, interrupted upload → Security + QA |
| AI triage | Media and structured records are available | AI returns finding, confidence, evidence frame, and `unknown` when uncertain | Model/policy version, token usage, finding state | Low confidence or disagreement → Human review |
| Human decision | Reviewer console shows evidence and context | QA accepts, rejects, changes severity, holds scope, or orders physical check | Reviewer ID, rationale, decision history | Critical ambiguity → Food Safety lead |
| Remediation | Hold or corrective task is created | Manager/licensee completes corrective action and attaches proof | Owner, SLA, affected scope, remediation evidence | SLA breach → Operations + licensee owner |
| Re-check and release | Corrective action is ready for verification | QA reviews re-check and releases or extends hold | Re-check ID, release authority, audit trail | Repeat failure → Independent physical audit |
| Independent challenge | Random or risk-triggered physical audit | Auditor compares site reality with virtual evidence | Audit result, disagreement class, calibration label | Staging/collusion pattern → Security + Food Safety |
| Customer/support recovery | Affected order, refund, or complaint requires action | Support communicates only approved, proportionate information | Customer-impact link, message template, incident ID | Customer harm or regulator issue → Incident response |

## Wireframe artifact

The proposed screens are shown in [Verified Hygiene Check wireframes](31_verified_hygiene_wireframes.md). The SVG is an actual low-fidelity design artifact, not a claim that a Figma file or production interface exists.

The screens trace to VHC-01 through VHC-10 and include the highest-risk states: location mismatch, incomplete coverage, interrupted upload, `unknown`, critical hold, human review, remediation, and a restrained post-validation customer view.

## Evidence integrity

- No gallery upload; capture only inside the active session.
- One-time signed task token with expiry.
- GPS/geofence plus rotating in-store QR or NFC challenge.
- Required route checkpoints, minimum dwell time, and random prompts.
- Device-integrity, mock-location, replay, and interruption detection.
- Hash each media segment and bind it to store, check, model, and policy versions.
- Manager submits and remediates; cannot override a failed verdict.
- Unannounced human audits remain mandatory.

GPS or geotagging alone cannot prove that a scan is genuine. The layered bundle reduces—but does not eliminate—the opportunity for staging, spoofing, collusion, or delayed inspection.

## AI decision policy

| Outcome | Trigger | Action |
|---|---|---|
| Pass | Complete and valid session, no critical finding, high confidence, reconciled temperature/expiry evidence | Keep store operational; schedule next check; sample for audit |
| Fail / Hold | High-confidence critical finding such as pest evidence, visible contamination, stagnant water near food, expiry mix, or confirmed cold-chain breach | Quarantine affected scope; notify QA and manager; human review/escalation |
| Human review | Low coverage, poor lighting, model disagreement, ambiguous expiry text, or integrity exception | No green status; reviewer decides or orders physical check |

AI recommends workflow state; it is not the final regulatory authority.

During offline evaluation, shadow mode, and the initial human-gated pilot, **Pass** is only an AI recommendation presented to an authorised reviewer. No autonomous release or customer-facing trust claim is enabled. Narrow low-risk automation is a later gate, not an MVP assumption.

## MVP checklist

| Control | Evidence | Severity |
|---|---|---|
| Floors and drains | Wide shot and wall-floor close-up | Critical if food is exposed to stagnant water; major otherwise |
| Pest evidence | Corners, under racks, pest stations | Critical if confirmed |
| Product placement | Racks/pallets; no food on wet/dirty floor | Major |
| Expiry segregation | FEFO, quarantine cage, random sample | Critical if expired saleable stock is mixed |
| Cold storage | Displayed temperature plus trusted log | Critical when confirmed excursion affects safety |
| Product condition | Random sample for damage, fungus, leaks | Critical if visible contamination |
| Personnel hygiene | Handwash/PPE/headgear where applicable | Major/minor by process |
| Records | Licence, cleaning, pest control, corrective actions | Major |

## Trust experience

Do not publish an unqualified “AI certified” badge. After validation, use constrained language such as: “Storage controls last verified [date]. Verification covers visible hygiene controls and operating records; it is not a government food-safety certificate.”

## Key design risks

- Camera route can be staged or incomplete.
- AI cannot see concealed contamination or prove microbiological safety.
- Temperature requires trusted sensor/log data.
- Worker faces, voices, and sensitive layout may be captured.
- Overly punitive workflows may encourage avoidance or falsification.

## Experiment plan

| Hypothesis | Smallest credible test | Primary measure | Decision rule |
|---|---|---|---|
| Managers can complete the route without unacceptable operational burden | Moderated task test across supported device classes and store layouts | Median completion time, incomplete-route rate, help requests | Simplify route or change cadence if the proposed workload threshold misses |
| Layered integrity signals make a submitted session more trustworthy than self-attestation | Synthetic replay plus invalid-session challenge set | Invalid-session rejection or human-review rate; false acceptance by control | No automation if any high-risk invalid case is accepted without review |
| AI can identify visible critical controls after policy and label calibration | Frozen, store-split holdout with category-level labels | Recall, false-pass rate, unknown rate, calibration | Keep human review and narrow scope if any critical category misses |
| Findings create real containment and remediation | Workflow replay with QA, Operations, and Food Safety owners | Assignment completeness, hold accuracy, SLA closure, re-check evidence | Do not expand if the workflow produces alerts without accountable closure |
| A restrained verification detail can improve confidence without overclaiming | Comprehension test comparing neutral verification copy with badge language | Understanding of scope, limitations, and freshness | Do not expose customer-facing messaging if users infer a safety guarantee |

## Stage 03 decision gate

**Decision:** Proceed to product delivery specification.

**Recommendation:** Build the smallest safe workflow: live capture, layered integrity, visible-risk triage, human gating, remediation, and random audit.

**Evidence:** The design directly addresses inspection gaps and evidence staging while preserving human, physical, and regulatory oversight.

**Open questions:** Exact policy mapping, retention period, device support, and hold/recall authority.

**Approval request:** Approve the Verified Hygiene Check concept for PRD and technical-contract definition, subject to Privacy, Security, and Food Safety review.
