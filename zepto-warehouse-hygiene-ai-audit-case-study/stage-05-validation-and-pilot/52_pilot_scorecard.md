# Stage 05 — Validation and Pilot Scorecard

**Status:** Blank operating template; no results populated  
**Owner:** Zepto Trust / Food Safety lead, with Product as coordinator

Definitions, denominators, sampling logic, and evidence requirements are specified in the [metric dictionary and sampling plan](53_metric_dictionary_and_sampling_plan.md).

## Proposed cohort

The example design below is illustrative and must be sized after baseline review:

- four-week shadow period;
- limited volunteer store cohort across more than one layout and operating context;
- two routine checks per week plus risk-triggered checks;
- matched comparison cohort for operational outcomes where feasible;
- human reviewer confirms every operational decision during shadow mode.

## Gate scorecard

| Metric | Definition | Target | Actual | Status | Evidence / owner |
|---|---|---:|---:|---|---|
| Critical finding recall | Critical findings detected / critical findings present | ≥95% by category | — | Not run | ML + QA |
| Critical false-pass rate | Critical cases auto-passed / critical cases evaluated | ≤1% | — | Not run | QA |
| Invalid-session rejection | Invalid gallery/location/device/replay cases rejected or reviewed | 100% in test set | — | Not run | Security |
| Complete route coverage | Sessions meeting all required zone checkpoints | ≥95% | — | Not run | Product Ops |
| Suspect-session rate | Sessions flagged for integrity review | <3% with all high-risk reviewed | — | Not run | Security |
| Due checks within SLA | Completed due checks within configured window | ≥90% | — | Not run | Operations |
| Median manager completion time | Start-to-submit time for valid full route | ≤15 minutes | — | Not run | Product |
| Critical remediation within SLA | Closed critical tasks / critical tasks due | ≥95% | — | Not run | QA / licensee |
| AI-human agreement | Matching final finding class on sampled sessions | Baseline first; improve by iteration | — | Not run | ML + QA |
| Severe hygiene complaints | Complaints per 10,000 relevant orders vs baseline/control | Directional reduction; target ≥20% after 8 weeks | — | Not run | Support / Analytics |
| Worker privacy incidents | Confirmed incidents involving capture/access/retention | 0 | — | Not run | Privacy |

## Decision rules

### Proceed to controlled pilot

- Critical recall and false-pass thresholds pass by category.
- No unresolved privacy/security incident.
- Manager burden and completion thresholds pass.
- Remediation ownership and containment controls work in replay.
- QA and Food Safety approve the policy mapping.

### Continue shadow mode

- No safety-critical failure, but a non-critical threshold misses.
- Model performance is uneven by layout, lighting, device, or finding type.
- Manager burden or evidence completeness requires workflow changes.

### Stop / rollback

- Any unexplained critical false pass.
- A customer-harm event plausibly linked to an unchecked or incorrectly passed store.
- Material exposure of worker/customer personal data.
- Repeat evidence staging, spoofing, or tampering.
- Regulator, Legal, Privacy, or Food Safety owner withdraws approval.

## Required evidence attachments

- Frozen test-set manifest and label agreement report.
- Confusion matrix by critical finding type.
- Invalid-session test report.
- Human-review disagreement log.
- Manager usability/time-on-task summary.
- Remediation and re-check export.
- Privacy/security review and deletion verification.
- Go/no-go decision log.
