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

## Stage 6 gate

**Decision:** Scale only after Stage 5 thresholds pass for the approved period.  
**Recommendation:** Treat operational compliance, model safety, privacy, and customer outcomes as a joint launch gate.  
**Stop condition:** Any unexplained critical false pass, customer-harm signal, material privacy incident, repeated staging pattern, or regulator objection.
