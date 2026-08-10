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

## Stage 03 decision gate

**Decision:** Proceed to product delivery specification.

**Recommendation:** Build the smallest safe workflow: live capture, layered integrity, visible-risk triage, human gating, remediation, and random audit.

**Evidence:** The design directly addresses inspection gaps and evidence staging while preserving human, physical, and regulatory oversight.

**Open questions:** Exact policy mapping, retention period, device support, and hold/recall authority.

**Approval request:** Approve the Verified Hygiene Check concept for PRD and technical-contract definition, subject to Privacy, Security, and Food Safety review.
