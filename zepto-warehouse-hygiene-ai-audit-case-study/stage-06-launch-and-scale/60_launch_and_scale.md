# Stage 06 — Launch and Scale Plan

**Status:** Future-state plan; launch not approved or executed

## Rollout phases

1. **Readiness:** Approve checklist, retention, training, incident playbook, and thresholds.
2. **Shadow mode:** AI observes; humans decide.
3. **Human-gated operations:** AI recommends hold/pass; reviewer confirms every decision.
4. **Narrow automation:** Auto-pass only for low-risk, high-confidence, complete sessions; critical/ambiguous cases remain human-gated.
5. **Scale:** Add stores only after four consecutive weeks of threshold compliance and acceptable random physical-audit results.

## North Star

**Verified-control store-days:** store-days with complete, location-verified evidence, no unresolved critical exception, and completed remediation/re-check where required.

## Launch readiness and capacity

Do not expand the cohort until the operating system can absorb peak volume. Calculate the following with Zepto’s actual cohort, cadence, and loaded labour inputs:

```text
Daily due checks = active warehouses × checks per warehouse per day

Required manager minutes = daily due checks × median capture minutes

Required QA minutes = daily due checks × sample rate × median review minutes

Critical-response capacity = expected critical exceptions × review + containment + escalation minutes

Capacity headroom = staffed capacity − required capacity
```

The launch gate should require positive capacity headroom for normal and risk-triggered peaks, a named overflow owner, and a tested incident contact path. If QA or remediation queues exceed SLA, the system should reduce automation or pause new rollout rather than silently accumulate unresolved work.

## Customer and support communication

- Keep verification detail internal during shadow mode and human-gated pilot.
- If a customer-facing view is later approved, show last verification date, scope, freshness, and limitations.
- Never describe the check as a government certificate, microbial guarantee, or proof that no issue exists outside the recorded scope.
- For affected orders, use approved support/incident templates tied to the hold or remediation decision.
- Remove or downgrade stale verification detail when the check expires, a critical incident opens, or evidence integrity is questioned.

## Launch-readiness checklist

| Gate | Required evidence | Owner |
|---|---|---|
| Product and policy | Approved checklist, decision state model, hold/release authority | Product + Food Safety |
| Model safety | Category-level recall, false-pass, unknown, and drift report | ML + QA |
| Evidence integrity | Invalid-session tests, physical challenge results, access audit | Security |
| Operations capacity | Manager, QA, remediation, support, and incident capacity model | Operations |
| Privacy and labour | Notice, retention/deletion proof, access roles, incident path | Privacy / Legal |
| Economics | Actual ₹ inputs, pilot run-rate, audit allocation, and stop-cost | Finance / Product |
| Training | Manager, reviewer, support, and escalation training completion | Operations |
| Rollback | Automation pause, evidence preservation, affected-scope review, re-entry criteria | Incident response |

## Operating metrics and alerts

| Metric | Alert / review trigger |
|---|---|
| Check completion and lateness | Daily overdue queue or material SLA miss |
| Location/session integrity | Any critical spoof/replay or sustained suspect-session rise |
| AI/human agreement | Weekly drift by finding type, layout, device, and lighting |
| Critical false-pass rate | Any unexplained critical false pass |
| Time to contain/remediate | Critical task beyond SLA |
| Repeated finding by store/licensee | Weekly risk review and possible physical audit |
| Severe hygiene complaints | Spike or no improvement versus baseline/control |
| Worker/privacy burden | Any confirmed incident or disproportionate capture impact |

## Operating cadence

- **Daily:** critical failures, suspect sessions, open holds, overdue remediation.
- **Weekly:** store/licensee risk review, complaints, false-pass sample, AI drift.
- **Monthly:** physical-audit calibration, model review, privacy review, remediation economics.
- **Quarterly:** independent food-safety audit and customer-trust readout.

## Support and training

- Train managers on route quality, random prompts, critical findings, and containment.
- Train reviewers on unknown/ambiguous cases and evidence-based adjudication.
- Provide a remediation help path, not only punitive alerts.
- Notify support when an affected SKU or zone is held.
- Use plain-language customer communication; never call an internal check a government certificate.

## Scale guardrails

- No critical or low-confidence auto-pass.
- Human review for every integrity exception and customer-harm signal.
- Random off-cycle physical audits remain mandatory.
- Maintain sensor or physical sampling for controls video cannot prove.
- Keep a rollback path that disables auto-pass without destroying evidence.

## Stage 06 decision gate

**Decision:** Scale only after Stage 05 thresholds pass for the approved period.

**Recommendation:** Treat operational compliance, model safety, privacy, and customer outcomes as a joint launch gate.

**Evidence:** The launch plan includes completion, integrity, false-pass, remediation, privacy, support, and independent-audit guardrails.

**Open questions:** Which cohort and period will establish the launch baseline, what customer communication is legally approved, and who can stop the rollout?

**Approval request:** Approve launch planning only; authorize rollout after the Stage 05 validation evidence passes and Food Safety, Privacy, Security, Operations, and Product owners sign off.

**Stop condition:** Any unexplained critical false pass, customer-harm signal, material privacy incident, repeated staging pattern, or regulator objection.
