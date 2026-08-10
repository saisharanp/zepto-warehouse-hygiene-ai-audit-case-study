# Stage 05 — Data Readiness and Shadow-Mode Setup

**Status:** Ready for owner input; no live data collection or pilot has been executed
**Purpose:** Convert the approved validation protocol into an executable four-week shadow-mode setup

## What this artifact does

This is the handoff from product design to validation operations. It defines the minimum evidence Zepto would need to supply, how the data should be minimised and labelled, how the shadow cohort should be selected, and what must be true before any operational pilot.

It does not claim that Zepto has supplied the data, that a model has been trained, or that any threshold has been achieved.

## Data request

| Package | Minimum contents | Acceptance criteria | Owner |
|---|---|---|---|
| Inspection media | De-identified images/video from representative stores and known hygiene findings | Original provenance retained; faces/audio redacted for general access; no unexplained edits | QA / Privacy |
| Adjudicated labels | Case ID, store layout, zone, finding type, severity, evidence frame, reviewer rationale | Two independent labels plus adjudication for disagreements | Food Safety / QA |
| Store context | Zone map, store type, city, device class, operating hours, licencee relationship | No customer address or unnecessary worker identity fields | Operations |
| Baseline operations | Check cadence, completion, complaints, returns, expiry write-offs, temperature excursions, pest tickets, holds | Time window and denominator documented; no invented baseline | Analytics / QA |
| Policy/SOP | Hygiene checklist, severity mapping, cold-chain rules, FEFO/quarantine rules, escalation authority | Versioned and approved by Food Safety and Legal | Food Safety / Legal |
| Technical controls | Device support, GPS/QR/NFC capabilities, connectivity, storage, retention, access logs | Security threat model and privacy review complete | Engineering / Security |
| Worker safeguards | Notice, access policy, retention/deletion policy, incident route | Legal, Privacy, and labour review complete | Privacy / Legal |

## Data minimisation rules

- Use stable study IDs instead of names, phone numbers, customer order IDs, or exact residential addresses.
- Keep store identity and raw media in separate access-controlled locations.
- Disable audio unless a documented safety need exists.
- Blur faces, badges, and personal screens before broad reviewer access.
- Do not use media for facial recognition, productivity scoring, or unrelated model training.
- Retain raw media only for the approved period; retain derived findings only as long as justified.
- Log every raw-media access, export, correction, and deletion.

## Labelling protocol

1. Freeze the checklist and severity definitions before labelling.
2. Assign each case a unique `case_id`; never use a customer or worker identifier.
3. Require two independent reviewers for every critical/unknown case.
4. Record the exact evidence frame or timestamp supporting each label.
5. Record `unknown` when visibility, lighting, occlusion, or sensor evidence is insufficient.
6. Adjudicate disagreements and preserve both original labels and the final rationale.
7. Split train/calibration, validation, and holdout sets by store where possible to avoid layout leakage.
8. Freeze the holdout manifest before model threshold tuning.

## Shadow cohort selection

Select the cohort only after the baseline is reviewed. The cohort should include variation in:

- store layout and size;
- ambient, chilled, frozen, and produce zones;
- camera/device class and connectivity;
- licensee/manager tenure;
- prior risk level, without excluding low-risk stores;
- operating region where legally and operationally appropriate.

Do not choose only stores that volunteer or already perform well. Record inclusion/exclusion criteria and the reason each store was selected.

## Four-week shadow setup

### Week 0 — Readiness

- Confirm checklist/policy version.
- Validate secure capture, gallery rejection, device integrity, geofence, QR/NFC challenge, and route checkpoints.
- Train managers and reviewers.
- Run synthetic replay and invalid-session tests.
- Confirm incident contacts, retention/deletion jobs, and physical-audit sampling plan.

### Weeks 1–4 — Shadow mode

- Schedule routine and risk-triggered checks according to the approved cadence.
- AI produces findings, but a human reviewer makes every operational decision.
- Do not auto-pass, publish a customer badge, or silently hold customer orders based only on model output.
- Randomly sample sessions for independent QA and physical verification.
- Log manager time, incomplete routes, integrity exceptions, model confidence, reviewer disagreement, remediation, and re-check.
- Review critical/unknown cases within the agreed SLA.

### End of Week 4 — Gate review

- Calculate category-level recall, false-pass rate, route completeness, integrity rejection, manager time, and remediation closure.
- Segment results by finding type, store layout, device, lighting, and reviewer.
- Reconcile any critical finding with inventory, temperature, pest-control, and customer-order records.
- Run a privacy/security access and deletion audit.
- Complete a go/no-go memo using the scorecard; do not substitute qualitative enthusiasm for thresholds.

## Roles during shadow mode

| Role | Responsibility |
|---|---|
| Shadow coordinator | Schedule checks, monitor completion, maintain decision log |
| Store manager | Capture the route, contain obvious issues, complete remediation |
| QA reviewer | Confirm findings, decide hold/release, adjudicate critical/unknown cases |
| Food-safety lead | Approve severity mapping and regulator/escalation path |
| ML lead | Freeze model version, report category metrics and drift |
| Security lead | Review spoof/replay/device events and access logs |
| Privacy/Legal | Approve notice, retention, access, and incident handling |
| Analytics lead | Build denominator, baseline, and matched comparison readout |

## Entry criteria

- Data request owners and delivery dates assigned.
- Current SOP and severity mapping approved.
- Holdout and synthetic replay frozen.
- Secure capture and integrity controls pass invalid-session tests.
- Reviewer training complete.
- Privacy/security controls verified.
- Food-safety owner confirms human decision authority.

## Exit criteria

Advance to a controlled operational pilot only if the Stage 5 thresholds pass, including:

- ≥95% recall for each critical category;
- ≤1% critical false-pass rate;
- 100% rejection or human review of deliberately invalid test sessions;
- ≥95% route coverage;
- ≥90% due checks completed within SLA;
- ≤15-minute median manager completion time;
- ≥95% critical remediation closure within SLA;
- no unresolved privacy/security incident or customer-harm signal.

If a non-critical threshold misses without a safety incident, continue shadow mode and revise the workflow. If a critical false pass, privacy breach, or customer-harm signal occurs, pause automation and invoke the rollback runbook.

## Stage 5.1 decision gate

**Decision:** Ready to request data and configure shadow mode; not ready to execute or claim results.

**Recommendation:** Assign named owners for each data package and complete Week 0 readiness before collecting operational scans.

**Evidence:** The July 2026 public reports support testing a more frequent and auditable control loop, but they cannot provide Zepto’s internal baseline or model labels.

**Open questions:** Data availability, retention/legal basis, store cohort, cold-chain sensor access, and remediation authority.
**Approval request:** Approve the data request and nominate the QA, Food Safety, Operations, Engineering, Security, Privacy, and Analytics owners.
