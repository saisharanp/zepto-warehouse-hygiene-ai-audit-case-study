# Stage 07 — Final Handoff

## Executive readout

July 2026 reporting described hygiene enforcement at multiple Zepto stores in Hyderabad, including food on floors, dirty fixtures, waste, pest evidence, weak segregation, missing records, and a temporary order halt at Narsingi. The reports are location-specific and do not establish Zepto-wide prevalence.

The recommended response is **Verified Hygiene Check**: a risk-based live phone walkthrough with layered location/session integrity, AI triage of visible controls, human escalation, accountable remediation, and random physical audits.

## Final product decision

**Proceed to offline evaluation and shadow-mode validation. Do not launch a customer-facing badge or autonomous food-safety decision.**

The system should rebuild trust through frequent, traceable, independently challenged controls—not through a marketing claim. It must be funded alongside cleaning, pest control, shelving, cold-chain instrumentation, FEFO segregation, training, and remediation budgets.

## Agreed product position

| Decision | Position carried into implementation |
|---|---|
| Evidence claim | July 2026 reports support investigation of a credible, location-specific problem; they do not establish Zepto-wide prevalence or root cause. |
| Prioritization | Qualitative pre-RICE screening selects Verified Hygiene Check for validation; formal RICE remains `TBD` until Reach, Impact, Confidence, and Effort inputs are sourced. |
| Product boundary | Zepto dark-store/warehouse operations; the MVP covers visible, auditable controls and routes non-visual risks to records, sensors, sampling, or physical inspection. |
| AI authority | AI triages evidence and recommends `pass`, `fail/hold`, or `unknown`; an authorised human owns hold/release. |
| Integrity claim | GPS, QR/NFC, device checks, route prompts, hashes, and random audits reduce fraud opportunity; none proves bribery or staging is impossible. |
| Pilot design | Data readiness → offline evaluation → four-week shadow mode → eight-week human-gated controlled pilot → separate automation gate → scale; the 20-store/eight-week shape is illustrative and not automatically powered for customer-outcome claims. |
| Economic gate | Use cost per verified-control store-day; all Zepto-internal labour, audit, cloud, remediation, and build inputs remain `TBD` until sourced. |
| Customer communication | Keep verification internal through validation and human-gated pilot; defer any restrained customer view until independent validation. |
| Design artifact | Existing editable SVG wireframes are the working low-fidelity source for now; they are not a Figma file or production UI. |

Safety, evidence integrity, privacy, workload capacity, and cost are joint gates. Cost optimisation cannot weaken the critical false-pass or human-oversight controls.

## AI cost readout

The reference implementation estimates AI inference at **₹0.91 per 15-minute low-resolution screening scan** or **₹8.04 per default-resolution escalation scan**. These are planning estimates from public tariff and token assumptions, not Zepto’s actual contracted costs. The broader reference check cost is approximately **₹60.35 before independent-audit allocation** and **₹252.66 with the illustrative audit allocation**. Scale approval must use metered usage and Zepto Finance/Procurement inputs.

## What is known

- July 2026 reports describe multiple hygiene findings at specific Hyderabad Zepto locations.
- The proposed workflow directly addresses inspection frequency, evidence provenance, detection, and remediation ownership.
- Human and regulatory oversight remains necessary.

## What remains hypothetical

- AI recall, false-pass rate, manager completion time, and complaint reduction.
- Zepto’s current inspection cadence, internal baseline, and licensee root causes.
- Customer response to a restrained verification signal.
- The cohort size, comparison design, and power/precision needed for any complaint-reduction claim.

## Artifact index

| Stage | Artifact |
|---|---|
| 00 Research setup | [Research brief](../stage-00-research-setup/00_research_brief.md), [evidence and claim ledger](../stage-00-research-setup/01_evidence_claim_ledger.md), [cost model and unit economics](../stage-00-research-setup/05_cost_model_and_unit_economics.md), [cost input template](../stage-00-research-setup/06_zepto_cost_input_template.md) |
| 01 Discovery | [Discovery synthesis](../stage-01-discovery/10_discovery_synthesis.md), [evidence coding sheet](../stage-01-discovery/11_evidence_coding_sheet.md) |
| 02 Define and prioritize | [Problem and opportunity](../stage-02-define-and-prioritize/20_problem_and_opportunity.md) |
| 03 Solution design | [Verified Hygiene Check](../stage-03-solution-design/30_verified_hygiene_check.md), [wireframes and design traceability](../stage-03-solution-design/31_verified_hygiene_wireframes.md) |
| 04 Product delivery | [PRD and technical contract](../stage-04-product-delivery/40_prd_and_delivery.md) |
| 05 Validation and pilot | [Validation protocol](../stage-05-validation-and-pilot/50_validation_protocol.md), [synthetic replay](../stage-05-validation-and-pilot/51_synthetic_case_replay.csv), [scorecard](../stage-05-validation-and-pilot/52_pilot_scorecard.md), [metric dictionary and sampling plan](../stage-05-validation-and-pilot/53_metric_dictionary_and_sampling_plan.md), [runbook](../stage-05-validation-and-pilot/54_runbook_and_rollback.md), [data readiness](../stage-05-validation-and-pilot/56_data_readiness_and_shadow_setup.md), [approval gate](../stage-05-validation-and-pilot/55_validation_and_pilot_approval_gate.md) |
| 06 Launch and scale | [Launch and scale plan](../stage-06-launch-and-scale/60_launch_and_scale.md) |
| 07 Final handoff | This readout, [post-launch review template](71_post_launch_review_template.md), [tool-ready collaboration map](72_tools_map.md), [decision log](73_decision_log.md), [glossary](74_glossary.md) |

## Portfolio narrative

I reframed a high-emotion hygiene problem as a systems problem: customers need confidence, managers need a workable control, and quality teams need evidence that is frequent and difficult to fake. I selected a small, testable intervention—verified phone walkthroughs with AI triage—while keeping human and regulatory oversight in the loop. Trust is rebuilt by an auditable prevention-and-remediation system, not by a badge or a one-time inspection.

## Stage 07 decision gate

**Decision:** Handoff is complete as a proposed, evidence-led product case study; operational launch remains gated.

**Recommendation:** Approve collection of de-identified inspection media, current SOPs, internal complaint/temperature/expiry data, and Privacy/Legal/QA review before controlled operational testing.

**Evidence:** Stages 00–07 have reviewable artifacts, explicit assumptions, decision gates, validation thresholds, rollback criteria, and a final product recommendation. The case study does not claim Zepto implementation, live model performance, actual cost savings, or customer-trust improvement.

**Open questions:** Whether Zepto can provide the required data and owners, whether the model passes the pre-declared safety thresholds, and whether the operating economics support the workflow.

**Approval request:** Approve the handoff package and advance to a controlled operational pilot only if the safety, evidence-integrity, privacy, workload, and cost gates pass.
