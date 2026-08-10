# Restoring Trust in Zepto Dark Stores

## AI-assisted routine hygiene checks with verified phone walkthroughs

**Case-study type:** Product-management portfolio case study  
**Product boundary:** Zepto dark stores / warehouse operations in India  
**Status:** Proposed concept and pilot plan; no Zepto internal data, implementation, or launch is claimed  
**Prepared:** 2026-08-10

## Stage map

- [Stage 00 — Research setup](stage-00-research-setup/00_research_brief.md)
  - [Evidence and claim ledger](stage-00-research-setup/01_evidence_claim_ledger.md)
  - [Cost model and unit economics](stage-00-research-setup/05_cost_model_and_unit_economics.md)
  - [Cost input template / shadow budget gate](stage-00-research-setup/06_zepto_cost_input_template.md)
- [Stage 01 — Discovery](stage-01-discovery/10_discovery_synthesis.md)
  - [Evidence coding sheet](stage-01-discovery/11_evidence_coding_sheet.md)
- [Stage 02 — Define and prioritize](stage-02-define-and-prioritize/20_problem_and_opportunity.md)
- [Stage 03 — Solution design](stage-03-solution-design/30_verified_hygiene_check.md)
  - [Wireframes and design traceability](stage-03-solution-design/31_verified_hygiene_wireframes.md)
- [Stage 04 — Product delivery](stage-04-product-delivery/40_prd_and_delivery.md)
- [Stage 05 — Validation and pilot](stage-05-validation-and-pilot/50_validation_protocol.md)
  - [Metric dictionary and sampling plan](stage-05-validation-and-pilot/53_metric_dictionary_and_sampling_plan.md)
- [Stage 06 — Launch and scale](stage-06-launch-and-scale/60_launch_and_scale.md)
- [Stage 07 — Final handoff](stage-07-final-handoff/70_final_handoff.md)
  - [Post-launch review template](stage-07-final-handoff/71_post_launch_review_template.md)
  - [Tool-ready collaboration map](stage-07-final-handoff/72_tools_map.md)
  - [Decision log](stage-07-final-handoff/73_decision_log.md)
  - [Glossary](stage-07-final-handoff/74_glossary.md)

## Canonical decision sequence

The case study uses one gated path across the stages:

```text
Data readiness
  → Offline evaluation
  → 4-week shadow mode (AI observes; humans decide)
  → 8-week human-gated controlled pilot
  → Separate automation gate
  → Scale after four consecutive compliant weeks
```

The 20-store/eight-week shape is illustrative until Zepto provides baseline, cohort, capacity, and power/precision inputs. No stage authorises a customer-facing badge or autonomous food-safety decision by itself.

## Executive summary

The current evidence base is the previous calendar month, **July 2026**. Multiple reports described hygiene enforcement at Zepto stores in Hyderabad. On July 9, Cyberabad Municipal Corporation officials directed a Narsingi Zepto facility to temporarily stop accepting orders while it cleaned and rectified reported issues including dirty racks, floors, walls and ceilings, food bags stored directly on the ground, food waste, weak food/non-food segregation, and an improperly positioned pest-control unit. [New Indian Express](https://www.newindianexpress.com/amp/story/cities/hyderabad/2026/Jul/10/zepto-told-to-halt-orders-over-hygiene-lapses), [Siasat](https://www.siasat.com/zepto-facility-in-narsingi-raided-fifth-inspection-in-3-weeks-3504787)

July reporting also described a July 7 Malkajgiri inspection that found food stored on the floor, damaged flooring, heavy housefly infestation, poor waste disposal, food/non-food co-storage, and missing pest-control and medical-fitness records; the store was reported to have scored 67% on a hygiene assessment. A July 1 report on a June 30 Mallepally inspection described cockroach and rodent infestation. These are reported findings at specific locations, not proof that every Zepto store has the same condition. [Hyderabad Mail](https://hyderabadmail.com/zepto-malkajgiri-food-safety-inspection-hygiene-lapses/), [South First](https://thesouthfirst.com/telangana/cockroaches-rodents-found-at-zepto-store-rotten-chicken-hygiene-violations-found-in-hyderabad/)

The product opportunity is not to claim that one video can certify food safety. It is to make hygiene controls more frequent, harder to falsify, easier to remediate, and auditable between physical inspections.

I recommend a **Verified Hygiene Check** workflow:

1. The store manager receives a risk-based check notification.
2. The manager opens a locked Zepto operations flow that cannot accept gallery uploads.
3. The phone records a guided, live walkthrough of every required zone, including random challenge prompts.
4. The app captures time, device integrity, geofence, an in-store QR/NFC challenge, route coverage, and a cryptographic evidence hash.
5. AI checks video quality and visible hygiene signals, then returns a **no-critical-issue recommendation, fail/hold recommendation, or human-review state** with evidence frames and confidence; only an authorised human can release a hold.
6. Critical failures pause affected inventory or food operations and create an accountable remediation task.
7. Random independent human checks calibrate the model and reduce the opportunity for collusion or staged scans.

This should be positioned as a **control and trust system**, not a regulatory certificate. AI can make the control loop faster and more consistent; it cannot remove the need for human judgment, regulatory inspections, physical sampling, or sensor data.

### AI cost per scan — ₹ planning model

Using the reference 15-minute walkthrough and public Gemini tariff assumptions, AI inference is estimated at:

| AI mode | Reference AI inference cost / scan | Intended use |
|---|---:|---|
| Gemini 2.5 Flash-Lite, low-resolution screening | **₹0.91** | Default first-pass triage |
| Gemini 2.5 Flash, default-resolution escalation | **₹8.04** | Higher-detail review when needed |

These are AI inference costs only—not Zepto’s actual contracted rate or the total cost of a hygiene check. The reference model estimates approximately **₹60.35 per scan before independent physical-audit allocation** and **₹252.66 per scan with the illustrative audit allocation** after manager time, QA review, exception reserve, storage, connectivity, tags, infrastructure, and audit costs. Replace the planning inputs with Zepto Finance/Procurement and usage-log data before approval. See the [Stage 00 cost model](stage-00-research-setup/05_cost_model_and_unit_economics.md).

## What is known vs. what is proposed

| Type | Statement |
|---|---|
| Observed public evidence | July 2026 reporting described hygiene enforcement at multiple Zepto locations in Hyderabad, including Narsingi, Malkajgiri, and Mallepally. |
| Observed public evidence | The Narsingi facility was reportedly directed to temporarily stop accepting customer orders until cleaning and rectification were completed. |
| Observed public evidence | A customer complaint preceded the Mallepally inspection reported by Siasat; this is a trigger signal, not evidence of prevalence across Zepto. |
| Interpretation | Surprise inspections can find problems at a point in time, but the public record does not establish how long each condition existed or how often each store was internally checked. |
| Root-cause hypothesis | Licensee incentives, maintenance budgets, and accountability may not be aligned; July reporting alone cannot establish the cause and Zepto must validate it internally. |
| Proposal | Add routine, location-verified virtual checks with AI triage, human escalation, and random physical audits. |
| Non-claim | This proposal does not prove that bribery occurred, that all Zepto warehouses have the same issue, or that AI alone can guarantee hygiene. |

## Stage 00 — Research setup

### Research question

How might Zepto detect and remediate visible warehouse-hygiene failures earlier, while producing trustworthy evidence that a check occurred at the correct facility and reducing dependence on infrequent or predictable physical inspections?

### Target users and stakeholders

| User | Job to be done | Current risk |
|---|---|---|
| Customer | Buy food and household goods without wondering whether storage conditions were safe. | A single bad order can generalise into distrust of the whole dark-store network. |
| Store manager | Keep the site compliant without losing operating time. | Manual checks may be rushed, delayed, or treated as paperwork. |
| Licensee / warehouse operator | Run a clean, productive store and avoid shutdowns. | Maintenance cost and commercial incentives may compete with hygiene work. |
| Zepto central quality team | See emerging risk across many stores and intervene early. | Periodic inspection data is sparse and hard to compare. |
| Regulator / auditor | Inspect against applicable legal and safety requirements. | Company-generated evidence cannot replace independent authority. |

### Evidence-quality rubric

- **High:** official regulator document or contemporaneous report quoting a named authority.
- **Medium:** reputable reporting that corroborates an official action or company statement.
- **Low:** user-generated allegation or social post; useful for signal discovery, not prevalence.

Public reports are directional. They do not provide the denominator of orders, stores, inspections, or affected products.

### Source log

| Source | Date | Evidence captured | Confidence |
|---|---:|---|---|
| [New Indian Express](https://www.newindianexpress.com/amp/story/cities/hyderabad/2026/Jul/10/zepto-told-to-halt-orders-over-hygiene-lapses) | Jul 10, 2026 | CMC reportedly directed Narsingi to halt orders temporarily; dirty fixtures/floors, food on ground, waste, weak segregation, unclean air curtains, and pest-unit positioning. | High/medium |
| [Siasat — Narsingi](https://www.siasat.com/zepto-facility-in-narsingi-raided-fifth-inspection-in-3-weeks-3504787/) | Jul 10, 2026 | Reported fifth Zepto inspection in three Hyderabad weeks and details attributed to CMC, including lack of pallets and missing licence evidence. | Medium |
| [Hyderabad Mail — Malkajgiri](https://hyderabadmail.com/zepto-malkajgiri-food-safety-inspection-hygiene-lapses/) | Jul 8, 2026 | July 7 inspection report: food on floor, houseflies, damaged flooring, poor waste disposal, co-storage, missing records, and a reported 67% hygiene score. | Medium |
| [South First — Mallepally](https://thesouthfirst.com/telangana/cockroaches-rodents-found-at-zepto-store-rotten-chicken-hygiene-violations-found-in-hyderabad/) | Jul 1, 2026 | Reported June 30 H-FAST inspection finding evidence of cockroach and rodent infestation at a Mallepally store. | Medium |
| [Siasat — Mallepally](https://www.siasat.com/cockroach-rodent-infestation-at-another-zepto-store-in-hyderabad-3499401/) | Jul 1, 2026 | Reported customer-complaint trigger and official comments about infestation; allegations remain subject to the authorities’ process. | Medium |
| [FSSAI hygiene requirements](https://fssai.gov.in/cms/hygiene-requirements.php) | Current guidance | Licensed FBOs must maintain a documented FSMS plan and follow Schedule 4 GMP/GHP requirements for storage and distribution. | High |
| [FSSAI safe storage and distribution handbook](https://fostacold.fssai.gov.in/fostac/doc/Food%20Safety%20training%20manual%20storage%2C%20transportation%20v2%20-%20June%2014%2C%202017%20with%20checklist.pdf) | Guidance | Controls should identify hazards, monitor controls, and review them periodically across storage and distribution. | High |

## Stage 01 — Discovery

### Evidence-backed problem themes

1. **The July reports show repeated categories of control failure.** Across reported Hyderabad locations, recurring themes were dirty racks/floors/fixtures, food stored on the ground, waste, weak food/non-food segregation, pest evidence, and missing or poorly displayed records.
2. **A stop-order is a lagging control.** The Narsingi action demonstrates that enforcement can stop customer orders, but it does not tell customers how long the conditions existed or whether similar drift is developing between inspections.
3. **Complaints can be the first signal.** The Mallepally report says a customer complaint preceded the raid. A product system should make complaints risk triggers, not wait for them to become the only detection channel.
4. **Evidence provenance matters.** Reports about multiple sites are stronger than a single anecdote, but they still remain media accounts of specific inspections. A trustworthy system needs a durable record of finding, remediation, re-check, and decision—not just a green status.
5. **The operating model is part of the product problem.** A camera workflow will not repair drains, replace shelving, enforce FEFO, or fund pest control. The system must connect detection to owner, budget, SLA, and consequence.

### Journey pain points

| Moment | Customer-facing failure | Operational gap | Product opportunity |
|---|---|---|---|
| Stock received | A damaged, expired, or contaminated item enters saleable stock. | Intake and expiry controls may be inconsistent. | Link scan findings to receiving, batch, and inventory quarantine. |
| Storage | Food sits near water, on dirty floors, or outside temperature controls. | Central team lacks frequent visual evidence. | Guided zone walkthrough plus temperature-log reconciliation. |
| Picking | Worker selects an item from a compromised zone. | A store can remain orderable while remediation is pending. | Hold affected SKU/zone or food category on critical failure. |
| Delivery | Customer receives a product that looks unsafe. | Complaint is the first alert. | Use complaints and returns as risk triggers for an unscheduled check. |
| Recovery | Refund resolves money, not confidence. | No visible proof that root cause was fixed. | Remediation timeline, independent re-check, and transparent internal audit trail. |

### Sample limitation

The source set is a small public evidence base centred on one reported facility and one customer complaint. It supports prioritising investigation, not estimating Zepto-wide failure rates. Before build, Zepto should join internal data on expiry write-offs, temperature excursions, pest-control tickets, customer complaints, refunds, and prior inspection outcomes.

## Stage 02 — Define and prioritize

### Problem statement

Zepto customers need confidence that food and household products were stored hygienically, but central operations may discover failures only through a periodic physical inspection, a regulator visit, or a customer complaint. Managers need a low-friction way to prove the current state of a facility, and the central quality team needs evidence that is frequent, complete, and difficult to stage.

### Jobs to be done

- **Customer:** “When I order food from a dark store, help me believe it was handled safely, so I can use quick commerce without anxiety.”
- **Store manager:** “When a hygiene check is due, help me complete the right scan quickly and fix what is wrong, so the store stays compliant and operational.”
- **Quality lead:** “When risk changes at a store, show me reliable evidence and give me a clear action, so I can intervene before customers or regulators discover the issue.”

### Opportunity-solution tree

**Desired outcome:** fewer severe hygiene exceptions reach customers and more customers trust Zepto’s food handling.

→ Increase check frequency between physical inspections  
→ Verify that the check occurred at the correct facility  
→ Improve detection of visible hygiene and storage risks  
→ Close remediation with ownership and evidence  
→ Preserve independent oversight and customer transparency

**Recommended opportunity:** verified routine virtual checks with AI triage and risk-triggered human inspection.

### Opportunity prioritization

The primary opportunity is to increase check frequency, verify evidence provenance, detect visible risks earlier, and close remediation between physical inspections. Customer confidence is a downstream outcome, not the MVP control.

### RICE prioritization

The qualitative screen in [Stage 02](stage-02-define-and-prioritize/20_problem_and_opportunity.md) selects Verified Hygiene Check for validation. Formal RICE remains gated on Zepto inputs:

```text
RICE score = Reach × Impact × Confidence ÷ Effort
```

Reach must use an approved store-check or store-week denominator; Impact must map to fewer severe hygiene exceptions; Confidence must link to the evidence ledger; Effort must use cross-functional person-months. The current RICE table is intentionally `TBD` because public reporting does not provide Zepto’s cohort denominator or delivery effort. This prevents false precision before the pilot budget and baseline are approved.

### Non-goals

- Replace FSSAI or state FDA inspection and enforcement.
- Certify microbiological safety, odour, allergens, or sealed-package contents from video.
- Use facial recognition or worker surveillance.
- Publish a green badge before the control is independently calibrated.
- Treat GPS metadata as proof of truthfulness by itself.

## Stage 03 — Solution design

### Core flow

```text
Risk engine schedules check
        ↓
Manager receives signed, time-bounded task
        ↓
In-app live session: GPS + QR/NFC + device attestation
        ↓
Guided route: receiving → ambient → chilled/frozen → returns/quarantine → dispatch
        ↓
AI checks coverage, image quality, and visible control failures
        ↓
AI recommendation: no-critical-issue / fail-hold / human review
        ↓
Remediation task + evidence + re-check
        ↓
Random physical audit calibrates and challenges the system
```

### What the phone scan should prove

- The correct store was visited at the claimed time.
- The required zones were covered with sufficient visibility.
- The recording was captured in-session, not uploaded from a gallery.
- The evidence has not been edited after capture.
- Visible controls appear compliant or have an explainable exception.

### What the phone scan cannot prove alone

- Microbial contamination or foodborne illness risk.
- Actual temperature throughout the cold chain without trusted sensor/log data.
- The absence of pests in concealed areas.
- That a manager did not stage or clean only the camera route.
- That a location signal was not spoofed.

### Anti-fraud and evidence integrity

Use layered signals because every individual signal can fail:

1. **No gallery upload:** capture only from the in-app camera session.
2. **One-time challenge:** signed task token expires after a short window.
3. **Location proof:** GPS/geofence plus a rotating QR or NFC tag physically installed inside the store; reconcile with device time and network signals.
4. **Coverage proof:** required route checkpoints, minimum dwell time, camera movement, and random prompts such as “show the lower shelf in chilled zone.”
5. **Device integrity:** detect rooted/jailbroken devices, mock location, replayed video, and session interruption; route suspicious cases to human review.
6. **Tamper-evident record:** hash each segment, bind it to store/check/model versions, and preserve an append-only audit log.
7. **Separation of duties:** the manager can submit evidence and remediate, but cannot override a failed verdict. A quality reviewer or independent auditor handles appeals.
8. **Random physical sampling:** select stores and time windows outside the normal schedule. This is the main deterrent against staging and collusion.

The design reduces the opportunity for bribery or delayed inspections; it does not prove that bribery is impossible or that remote evidence is automatically truthful.

### AI decision policy

| Outcome | Trigger | Operational action | Human role |
|---|---|---|---|
| **No-critical-issue recommendation** | Complete route, valid location/session evidence, no critical finding, high model confidence, and reconciled temperature/expiry records. | Present evidence to an authorised reviewer; no release from AI output alone. | Confirm scope, records, and decision rationale. |
| **Fail / Hold** | High-confidence critical finding: visible contamination/fungal growth, pest evidence, food near stagnant water, expired stock mixed with saleable stock, or a confirmed cold-chain breach. | Quarantine affected SKUs/zone; pause relevant food operations if policy requires; notify quality lead and manager. | Review within SLA; regulatory escalation where required. |
| **Human review** | Low coverage, poor lighting, model disagreement, suspected spoofing, ambiguous expiry text, or manager appeal. | Do not expose a green status; risk-based temporary restriction. | Quality reviewer decides and may order a physical visit. |

AI should recommend and trigger workflow states; the final regulatory decision remains with the authorised human/regulatory process.

### Minimum checklist for the MVP

| Control | Evidence requested | Severity |
|---|---|---|
| Floors and drains | Wide shot of floor, drains, and wall-floor junctions | Critical if food is exposed to stagnant water; major otherwise |
| Pest evidence | Random close-ups of corners, under-rack areas, and pest-control stations | Critical if visible infestation/evidence is confirmed |
| Product placement | Racks/pallets, no food directly on wet/dirty floor | Major |
| Expiry and segregation | FEFO labels, quarantine cage, close-up of random sample | Critical if expired saleable stock is mixed with fresh stock |
| Cold storage | Displayed temperature plus system/log reconciliation | Critical when a confirmed excursion affects safety |
| Product condition | Random sample for visible damage/fungal growth/leaks | Critical if visible contamination is confirmed |
| Personnel hygiene | Handwash/PPE/headgear where applicable | Major/minor depending on food process |
| Licence and records | Current licence, cleaning log, pest-control log, corrective-action history | Major |

FSSAI’s published hygiene requirements and storage handbook should anchor the checklist; Zepto’s food-safety and legal teams must map each item to the applicable current regulation and local SOP.

### Trust experience

Do not launch with an unqualified “safe warehouse” badge. After the pilot passes independent validation, expose a restrained trust signal such as:

> “Storage controls last verified: [date]. Verification covers visible hygiene controls and operating records; it is not a government food-safety certificate.”

If a critical failure affects customer orders, Zepto should have a batch/zone traceability process, pause affected stock, and communicate proportionately. A refund alone is not a trust repair strategy.

## Stage 04 — Product delivery

### MVP requirements

| ID | Requirement | Acceptance criteria |
|---|---|---|
| VHC-01 | Risk-based tasking | Quality team can configure cadence, risk triggers, due window, and store cohort. |
| VHC-02 | Secure capture | Session rejects gallery media, records signed timestamps, and detects interruption/replay signals. |
| VHC-03 | Store verification | Session records geofence, rotating in-store QR/NFC challenge, and device/session metadata; GPS alone cannot pass a check. |
| VHC-04 | Guided coverage | Manager cannot complete without required zones, random prompts, and minimum media quality. |
| VHC-05 | AI findings | Model returns finding type, evidence frame, confidence, model version, and unknown/ambiguous state. |
| VHC-06 | Safe decisioning | Critical or low-confidence cases never auto-pass; fail/hold rules are configurable by food-safety policy. |
| VHC-07 | Remediation | Every failure creates owner, SLA, affected zone/SKU scope, corrective action, and re-check requirement. |
| VHC-08 | Audit trail | All verdict changes, reviewer actions, evidence hashes, and model versions are immutable and exportable. |
| VHC-09 | Privacy | Faces/audio are not needed; blur faces, avoid audio by default, restrict access, define retention, and provide worker notice. |
| VHC-10 | Independent challenge | System samples stores for unannounced human audits and reports AI/human disagreement. |

In the MVP, a no-critical-issue AI recommendation is not a release decision. `Verified-no-critical-issue` requires an authorised human decision after evidence, scope, and required records are reviewed.

### Key data contract

`check_id`, `store_id`, `licensee_id`, `task_id`, `scheduled_at`, `started_at`, `ended_at`, `device_attestation`, `location_signals`, `zone_checkpoints`, `coverage_score`, `media_hashes`, `finding_type`, `severity`, `confidence`, `model_version`, `temperature_log_reference`, `expiry_sample_reference`, `verdict`, `reviewer_id`, `remediation_id`, `recheck_id`, `retention_expiry`.

### Delivery ownership

| Owner | Accountability |
|---|---|
| Product / Trust | Outcomes, policy, workflow, customer communication |
| Food safety / QA | Checklist, severity, human adjudication, regulator interface |
| Store manager / licensee | Capture, immediate containment, remediation |
| ML / computer vision | Model, calibration, drift, explainability, safe thresholds |
| Security | Device/session integrity, anti-spoofing, access controls |
| Privacy / Legal | Data minimisation, worker notice, retention, applicable DPDP and labour review |
| Support / Incident response | Customer complaints, recalls, order holds, escalation |

### Privacy and worker safeguards

A live warehouse recording may capture workers, faces, voices, labels, personal devices, and commercially sensitive layout. Apply purpose limitation, data minimisation, access controls, short retention, automatic redaction, and a clear worker notice. The Digital Personal Data Protection Act requires processing to be tied to a lawful purpose and consent/notice conditions; Legal should confirm the applicable basis and implementation before pilot. [MeitY: DPDP Act 2023](https://www.meity.gov.in/writereaddata/files/Digital%20Personal%20Data%20Protection%20Act%202023.pdf)

## Stage 05 — Validation and pilot

### Riskiest assumptions

1. Phone video can cover enough of a store to detect important visible risks.
2. The anti-spoofing bundle makes remote checks more reliable than a self-attested checklist.
3. Managers can complete the workflow without materially harming fulfilment speed.
4. AI can achieve safety-grade recall for clearly visible critical findings.
5. Detection leads to timely remediation rather than a new layer of ignored alerts.
6. Customers respond to credible hygiene evidence, not just a marketing badge.

### Proposed validation sequence

**Stage A — Offline model evaluation:** use a labelled set of real, de-identified inspection frames plus clearly labelled synthetic edge cases. Include occlusion, low light, clutter, camera shake, and staged scenes. Measure recall separately for every critical finding; do not average away a weak category.

**Stage B — Shadow mode:** run for 4 weeks in a documented mixed cohort covering layouts, risk levels, devices, connectivity, and operating contexts. Volunteer participation may be used only where necessary and must be labelled as a source of bias. AI produces findings, but human reviewers make all operational decisions. Compare model findings with blinded human review and physical spot checks.

**Stage C — Controlled pilot:** expand only if shadow-mode safety thresholds pass. Example pilot shape—clearly illustrative, to be sized after baseline—is 20 stores, 8 weeks, two routine checks per week, risk-triggered checks, and a matched comparison cohort. This shape is not powered by itself to prove a 20% complaint reduction; Analytics must pre-register the denominator, comparison method, and power/precision assessment.

### Pre-declared pilot thresholds

These are proposed go/no-go thresholds, not achieved results:

| Measure | Pilot threshold | If missed |
|---|---:|---|
| Recall on clearly visible critical findings | ≥95% on the frozen holdout and shadow challenge sample, by category | No auto-pass; retrain or narrow scope |
| Critical false-pass rate in blinded human/physical audit | ≤1% | Disable automation and investigate |
| Valid session coverage | ≥95% of required zones | Treat as incomplete; require re-scan |
| Suspected spoof/integrity exception rate | <3% of sessions, with all high-risk cases reviewed | Tighten device/location controls |
| Due checks completed within SLA | ≥90% | Adjust cadence, staffing, or manager workflow |
| Critical remediation closed within SLA | ≥95% | Escalate licensee/quality ownership; no scale |
| Manager median completion time | ≤15 minutes | Simplify route or change cadence |
| Severe hygiene complaints | Exploratory directional signal versus baseline/matched cohort; ≥20% is a planning aspiration only after power/precision review | Do not claim trust impact; continue diagnosis |

### Rollback criteria

Immediately disable auto-pass and revert to human review if there is a critical false pass, a customer harm signal plausibly linked to an unchecked store, material privacy/security leakage, systematic model drift, regulator objection, or repeated evidence-staging pattern. Keep capture only if it remains useful and lawful.

## Stage 06 — Launch and scale

### Rollout phases

1. **Data readiness:** approve checklist, data handling, cohort, cost inputs, training, incident playbook, and thresholds.
2. **Offline evaluation:** run the frozen holdout and invalid-session challenge set; no operational decisions or customer claim.
3. **Shadow mode:** run for four weeks; model observes and humans decide.
4. **Human-gated controlled pilot:** run the approved eight-week pilot with reviewer confirmation for every operational decision.
5. **Automation gate:** consider auto-pass only for a separately approved low-risk, high-confidence, complete-session subset after the safety, integrity, workload, privacy, and physical-audit gates pass; all critical and ambiguous cases remain human-gated.
6. **Scale:** add stores only after the human-gated pilot, then four consecutive weeks of threshold compliance and an acceptable random physical-audit result.

### North Star and guardrails

**North Star:** verified-control store-days—store-days with complete, location-verified evidence, no unresolved critical exception, and a completed remediation/re-check path where required.

Track:

- check completion and lateness;
- route and location-integrity pass rate;
- AI/human agreement by finding type;
- critical false-pass and false-fail rate;
- time to contain and time to remediate;
- repeated finding rate by store/licensee;
- customer severe hygiene complaints per 10,000 relevant orders;
- refunds, replacements, recalls, and affected-SKU holds;
- worker time burden and privacy incidents.

Do not optimise for “green checks.” A system that increases pass rate by making the model or checklist less sensitive is failing its purpose.

### Operating cadence

- Daily: critical failures, suspect sessions, open holds, overdue remediations.
- Weekly: store/licensee risk review, complaint linkage, false-pass audit sample.
- Monthly: model drift, physical-audit calibration, privacy review, remediation economics.
- Quarterly: external or independent food-safety audit and customer trust readout.

## Stage 07 — Final handoff

### Recommendation

Proceed to offline evaluation and a shadow-mode pilot of **Verified Hygiene Check**, with three non-negotiable guardrails:

1. AI is not the final regulatory authority.
2. GPS/geotagging is one signal in a layered chain of custody, not proof by itself.
3. Critical or ambiguous findings never auto-pass; random physical audits remain mandatory.

The product should be funded alongside basic hygiene controls—cleaning, pest control, shelving, cold-chain instrumentation, FEFO segregation, training, and remediation budgets. Otherwise it risks becoming a sophisticated way to document an unchanged operational problem.

### Expected customer value

If the pilot works, customers should experience fewer severe hygiene failures and faster, more credible recovery when one occurs. Zepto can rebuild trust by showing that its controls are frequent, traceable, independently challenged, and connected to corrective action—not by publishing an unqualified “AI certified” label.

### What remains unknown

- Zepto’s current inspection cadence, compliance baseline, and dark-store exception rate.
- Whether the July 2026 Hyderabad findings were isolated, concentrated in one operating region, or representative of a wider network issue.
- Which controls require sensors or physical sampling rather than video.
- Whether licensee economics or operating training is a material root cause.
- Customer willingness to use a hygiene-verification signal.

### Next decision gate

Approve a 4-week offline/shadow evaluation after Zepto supplies de-identified inspection examples, internal complaint/temperature/expiry data, applicable SOPs, and Legal/QA/privacy review. Advance to a controlled operational pilot only if the pre-declared safety and evidence-integrity thresholds are met.

## Portfolio narrative

I reframed a high-emotion hygiene problem as a systems problem: the customer needs confidence, the manager needs a workable control, and the quality team needs evidence that is frequent and difficult to fake. I selected a small, testable intervention—verified phone walkthroughs with AI triage—while keeping human and regulatory oversight in the loop. The key product insight is that trust is rebuilt by an auditable prevention-and-remediation system, not by a badge or a one-time inspection.

## Validation package

- [Offline and shadow-mode validation protocol](stage-05-validation-and-pilot/50_validation_protocol.md)
- [Synthetic case replay](stage-05-validation-and-pilot/51_synthetic_case_replay.csv)
- [Pilot scorecard](stage-05-validation-and-pilot/52_pilot_scorecard.md)
- [Metric dictionary and sampling plan](stage-05-validation-and-pilot/53_metric_dictionary_and_sampling_plan.md)
- [Runbook and rollback](stage-05-validation-and-pilot/54_runbook_and_rollback.md)
- [Data readiness and shadow setup](stage-05-validation-and-pilot/56_data_readiness_and_shadow_setup.md)
- [Validation and pilot approval gate](stage-05-validation-and-pilot/55_validation_and_pilot_approval_gate.md)
