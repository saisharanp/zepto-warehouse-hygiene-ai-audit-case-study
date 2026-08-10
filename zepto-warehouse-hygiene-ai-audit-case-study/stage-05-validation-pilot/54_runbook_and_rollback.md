# Stage 5 — Shadow-Mode Runbook and Rollback

## Before each check window

1. Risk engine creates a signed task with store, due window, required route, and random prompt rules.
2. Operations confirms that the store is open, the manager is trained, and the rotating QR/NFC challenge is active.
3. Security verifies device and session controls in the release candidate.
4. QA confirms the current checklist and severity policy version.

## During the manager session

1. Manager opens the in-app task; gallery upload is unavailable.
2. App verifies device integrity, geofence, and rotating in-store QR/NFC challenge.
3. Manager follows the required route: receiving, ambient, chilled/frozen, quarantine/returns, and dispatch.
4. App issues random prompts and blocks submission until required evidence is present.
5. AI returns finding type, confidence, evidence frames, coverage, and integrity state.
6. In shadow mode, the manager receives corrective guidance but QA makes the operational decision.

## Critical finding response

1. Mark affected zone/SKU/category as `hold_pending_review`.
2. Notify store manager, licensee owner, central QA, and incident response.
3. Create remediation task with named owner and SLA.
4. Reconcile inventory, temperature logs, pest-control records, and customer orders.
5. QA reviewer decides whether to release, extend hold, recall, or escalate to the regulator.
6. Require a re-check and preserve the original evidence and decision history.

## Integrity exception response

Treat gallery selection, mock location, QR/NFC mismatch, session replay, missing route, or suspicious evidence as **incomplete**, not as a failed hygiene finding. Require a re-scan and route repeated exceptions to Security and QA review. A manager must not be able to clear their own integrity exception.

## Rollback levels

| Level | Trigger | Action |
|---|---|---|
| 1 — Threshold alert | Non-critical metric drifts or false-fail burden rises | Freeze model threshold changes; review sampled sessions within 24 hours. |
| 2 — Automation pause | Critical false-pass, evidence-staging pattern, or integrity control failure | Disable auto-pass; all sessions go to human review; retain capture only if Privacy approves. |
| 3 — Product pause | Customer-harm signal, privacy/security incident, repeated critical misclassification, or regulator objection | Stop new sessions; quarantine affected decisions; activate incident response and notify accountable leadership. |
| 4 — Full reversal | Control cannot be made safe within agreed remediation window | Remove the virtual-check decisioning path and return to approved manual/physical controls until a new gate is passed. |

## Recovery after rollback

- Preserve evidence, logs, model version, and reviewer decisions.
- Identify all stores, SKUs, and orders touched by potentially unsafe passes.
- Conduct targeted physical inspections or sampling.
- Communicate with affected customers when required by policy or law.
- Document root cause, corrective action, and re-entry threshold.
- Re-enter shadow mode before re-enabling any automation.
