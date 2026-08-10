# Zepto Cost Input Template — Shadow-Mode Budget Gate

**Prepared:** 2026-08-10
**Status:** Tool-ready template; no Zepto internal values have been supplied
**Owner:** Product + Finance/Procurement + Food Safety
**Related artifact:** [Cross-stage cost model](05_cost_model_and_unit_economics.md)

## Purpose

Use this template to replace planning assumptions with Zepto’s contracted rates and operating data before approving a shadow-mode budget. Every amount is intended to be entered in **Indian rupees (₹)**. Do not enter a vendor tariff without its source, effective date, billing unit, tax treatment, and free-tier or committed-use condition.

This is a request for inputs, not evidence that Zepto has approved the proposal or incurred these costs.

## How to complete it

1. Assign one named owner to every input.
2. Enter the value actually used for approval in the **Actual / approved input** column.
3. Attach a quote, invoice, contract extract, payroll table, time study, or approved internal estimate in the **Source / evidence** column.
4. Record whether the amount includes GST, other taxes, egress, backup, support, or platform overhead.
5. Mark unknown values as **TBD**, not zero.
6. Recalculate the per-scan, per-warehouse, and pilot totals after every material input changes.

## A. Scale and cadence

| Input | Unit | Actual / approved input | Source / evidence | Owner | Due date | Notes |
|---|---|---:|---|---|---|---|
| Warehouses in shadow cohort | warehouses | TBD | Cohort list / approval memo | Operations | TBD | Include city and store type |
| Target network warehouses | warehouses | TBD | Current network report | Operations | TBD | Needed for scale scenario |
| Routine checks per warehouse | checks/month | TBD | Approved SOP | Food Safety | TBD | Separate scheduled and risk-triggered checks |
| Expected completion rate | % | TBD | Baseline or pilot assumption | Analytics | TBD | Use a denominator |
| Shadow duration | weeks | TBD | Validation plan | Product | TBD | Reference plan is four weeks |
| Re-check rate | % of scans | TBD | Existing workflow or pilot assumption | QA | TBD | Include failed and incomplete sessions |

## B. Capture and evidence

| Input | Unit | Actual / approved input | Source / evidence | Owner | Due date | Notes |
|---|---|---:|---|---|---|---|
| Median walkthrough duration | minutes/scan | TBD | Device test / time study | Operations | TBD | Reference model uses 15 minutes |
| Median uploaded media size | GB/scan | TBD | Compression test | Engineering | TBD | Measure the actual encrypted upload |
| Raw-media retention | days | TBD | Privacy/Legal decision | Privacy | TBD | Include deletion verification |
| Derived finding retention | days | TBD | Privacy/Legal decision | Privacy | TBD | Findings may have a different period |
| Expected retry rate | retries/scan | TBD | Offline replay / device test | Engineering | TBD | Include failed uploads and model retries |
| Supported device mix | % by class | TBD | Device inventory | Engineering | TBD | Record low-end Android coverage |
| Connectivity failure rate | % of sessions | TBD | Network test / baseline | Engineering | TBD | Include offline recovery path |
| QR/NFC kit cost | ₹/warehouse | TBD | Procurement quote | Procurement | TBD | Include installation and replacement |
| Device or accessory cost | ₹/warehouse | TBD | Procurement quote | Procurement | TBD | Only if existing phones cannot support capture |

## C. AI and digital infrastructure

| Input | Unit | Actual / approved input | Source / evidence | Owner | Due date | Notes |
|---|---|---:|---|---|---|---|
| AI model and resolution | model / mode | TBD | Engineering design decision | ML/Engineering | TBD | Record screening and escalation models separately |
| Input tokens per scan | tokens/scan | TBD | API usage log or token count | ML/Engineering | TBD | Use actual response usage after replay |
| Output tokens per scan | tokens/scan | TBD | API usage log | ML/Engineering | TBD | Include structured output and retries |
| AI input price | ₹/1M tokens | TBD | Vendor pricing / contract | Procurement | TBD | Record effective date and plan |
| AI output price | ₹/1M tokens | TBD | Vendor pricing / contract | Procurement | TBD | Record effective date and plan |
| Model fallback rate | % of scans | TBD | Shadow-mode policy | ML/Engineering | TBD | Include premium or human-review escalation |
| Storage price | ₹/GB-month | TBD | Cloud contract | Engineering/Procurement | TBD | Include backup and replication |
| Storage request / retrieval cost | ₹/scan | TBD | Cloud contract | Engineering/Procurement | TBD | Include evidence review and exports |
| Compute cost | ₹/scan | TBD | Cloud contract / usage estimate | Engineering/Procurement | TBD | Include API, queue, and orchestration |
| Monitoring and logging | ₹/month | TBD | Cloud contract / platform budget | Engineering | TBD | Include retention and alerting |
| Notification cost | ₹/notification | TBD | Provider plan | Engineering/Procurement | TBD | Include SMS or WhatsApp fallback if used |
| Security, privacy, and penetration testing | ₹/one-time + ₹/year | TBD | Security quote / plan | Security | TBD | Keep one-time and recurring amounts separate |

## D. People and operating time

| Input | Unit | Actual / approved input | Source / evidence | Owner | Due date | Notes |
|---|---|---:|---|---|---|---|
| Manager loaded cost | ₹/hour | TBD | Finance payroll table | Finance | TBD | Include benefits and applicable overhead |
| Manager capture and correction time | minutes/scan | TBD | Time study | Operations | TBD | Include failed or incomplete route handling |
| QA loaded cost | ₹/hour | TBD | Finance payroll table | Finance | TBD | Include benefits and applicable overhead |
| QA sampling rate | % of scans | TBD | QA policy | QA | TBD | Critical/unknown cases may be 100% reviewed |
| QA review time | minutes/review | TBD | Time study | QA | TBD | Separate routine and critical review |
| Food Safety loaded cost | ₹/hour | TBD | Finance payroll table | Finance | TBD | Include adjudication and escalation |
| Engineering support | ₹/month | TBD | Team allocation | Engineering | TBD | Include on-call and incident response |
| Privacy/Legal review | ₹/one-time + ₹/month | TBD | Team allocation | Legal/Privacy | TBD | Include worker notice and retention review |
| Training cost | ₹/warehouse + ₹/session | TBD | Training plan / vendor quote | Operations | TBD | Include manager backfill time |
| Remediation reserve | ₹/critical exception | TBD | Operations estimate | Food Safety | TBD | Cleaning, pest control, shelving, or disposal |

## E. Independent control and audit

| Input | Unit | Actual / approved input | Source / evidence | Owner | Due date | Notes |
|---|---|---:|---|---|---|---|
| Independent physical audit cost | ₹/audit | TBD | Vendor quote / internal cost | Procurement | TBD | Include travel, sampling, and lab costs |
| Independent audit cadence | audits/warehouse/quarter | TBD | Food Safety policy | Food Safety | TBD | Keep random audits in the control design |
| Physical audit coverage | % of warehouses/quarter | TBD | Sampling plan | QA | TBD | Include high-risk oversampling |
| Regulatory or certification fee | ₹/year | TBD | Regulatory / certification source | Legal/Food Safety | TBD | Do not assume video replaces inspection |
| External incident investigation | ₹/incident | TBD | Vendor quote / incident plan | Food Safety | TBD | Include surge capacity |

## F. One-time product and rollout cost

| Input | Unit | Actual / approved input | Source / evidence | Owner | Due date | Notes |
|---|---|---:|---|---|---|---|
| Discovery and policy design | ₹/one-time | TBD | Team estimate / vendor quote | Product | TBD | Include Food Safety and Legal workshops |
| UX and service design | ₹/one-time | TBD | Team estimate / vendor quote | Product/Design | TBD | Include accessibility and multilingual support |
| Mobile capture build | ₹/one-time | TBD | Engineering estimate | Engineering | TBD | Include device-integrity and gallery rejection |
| Backend and reviewer console | ₹/one-time | TBD | Engineering estimate | Engineering | TBD | Include audit log and evidence access |
| Integrations | ₹/one-time | TBD | Engineering estimate | Engineering | TBD | Inventory hold, ticketing, identity, notification |
| Data preparation and labelling | ₹/one-time | TBD | Reviewer estimate | QA/ML | TBD | Include double labelling and adjudication |
| Pilot training and deployment | ₹/one-time | TBD | Rollout plan | Operations | TBD | Include travel and backfill if applicable |
| Contingency | % of one-time cost | TBD | Finance policy | Finance | TBD | State the approved percentage and basis |

## Calculation sheet

Use the following formulas after the inputs are approved:

```text
AI cost / scan
= input tokens / 1,000,000 × AI input price
  + output tokens / 1,000,000 × AI output price
  + fallback / retry allocation

Digital cost / scan
= AI cost + storage + compute + requests + notifications
  + mobile data + QR/NFC amortisation

People cost / scan
= manager minutes / 60 × manager loaded cost
  + QA sampling rate × QA minutes / 60 × QA loaded cost
  + exception rate × exception minutes / 60 × applicable loaded cost

Independent-control allocation / scan
= physical audit cost × audits per quarter
  / (routine checks per warehouse per quarter)

Run-rate cost / scan
= digital cost + people cost + remediation reserve
  + independent-control allocation

Pilot cash budget
= one-time product and rollout cost
  + warehouses in cohort × setup cost / warehouse
  + warehouses in cohort × checks per month × shadow months × run-rate cost / scan
  + fixed platform cost for the shadow period

Fully loaded cost / scan
= run-rate cost / scan
  + one-time product and rollout cost
    / expected lifetime scans
  + fixed platform cost / expected scans
```

## Minimum approval checks

Before a shadow-mode budget is approved, Finance/Procurement and the accountable Food Safety owner should confirm:

- every non-zero amount has a source and effective date;
- all values are in ₹ and tax treatment is explicit;
- actual video size, token usage, retries, and manager time are measured or clearly labelled as assumptions;
- one-time, fixed monthly, per-scan, per-warehouse, and per-incident costs are separated;
- physical audits remain funded as an independent control;
- remediation, privacy/security, support, and incident costs are not omitted;
- the budget has a named owner, cohort size, cadence, stop condition, and contingency;
- a change in model, media duration, retention, or cohort size triggers recalculation;
- the budget does not depend on an unapproved customer-facing hygiene claim.

## Stage 0.1 cost gate

**Decision:** Do not finalise the shadow-mode budget until this template is populated and signed off.

**Recommendation:** Use the existing rupee model only as a planning baseline. Replace every internal placeholder with Zepto’s evidence-backed input, then approve a four-week shadow budget with a separate one-time build line and operating line.

**Evidence:** Public vendor pricing can anchor the digital-cost range, but Zepto’s actual cost is dominated by private labour, audit, remediation, platform, and rollout inputs.

**Open questions:** Who owns the budget, which warehouses form the cohort, what vendor contracts apply, and what threshold would cause the team to pause or redesign the workflow?

**Approval request:** Assign the Finance/Procurement, Operations, Food Safety, Engineering, QA, Security, Privacy, and Analytics owners and return the completed input sheet before shadow-mode execution.
