# Stage 07 — Tool-Ready Collaboration Map

**Status:** Import-ready artifact; no external project-management board or dashboard has been created

## Recommended system of record

Use GitHub Issues/Projects, Jira, Linear, or the organisation’s approved equivalent for execution. The artifacts in this repository are the source proposal; the live tool should hold owners, dates, status, approvals, and links to restricted evidence.

## Workstream map

| Workstream | Suggested tool object | Owner | Definition of ready | Definition of done |
|---|---|---|---|---|
| Research and internal-data request | Epic / project | Product + Analytics | Data owners, legal basis, sources, due dates | Approved evidence pack and limitations log |
| Policy and checklist mapping | Epic + decision log | Food Safety | Current SOP and severity owner | Versioned policy with escalation authority |
| Capture and integrity | Epic + technical tasks | Engineering + Security | Device matrix and threat model | Invalid-session tests pass or are explicitly gated |
| Reviewer console and remediation | Epic + UX/engineering tasks | Product + QA | Wireframes and state model approved | Human decisions, holds, re-checks, and audit trail work |
| AI evaluation | Experiment / dataset record | ML + QA | Frozen labels, holdout, metric dictionary | Category-level report and signed decision |
| Shadow operations | Pilot project | Operations | Cohort, training, capacity, rollback contacts | Scorecard completed with go/no-go decision |
| Privacy and worker safeguards | Compliance workstream | Privacy / Legal | Notice, retention, access, deletion plan | Review signed and audit evidence retained |
| Launch and support | Release checklist | Operations + Support | Capacity, messaging, incident playbook | Rollout gate passed and support trained |

## Required fields for each live work item

`work_item_id`, `stage`, `workstream`, `owner`, `approver`, `status`, `priority`, `rice_reach`, `rice_impact`, `rice_confidence`, `rice_effort`, `rice_score`, `decision_id`, `evidence_claim_id`, `decision_needed`, `dependency`, `risk`, `target_date`, `evidence_link`, `policy_version`, `cost_impact`, `rollback_trigger`, `last_reviewed_at`.

## Dashboard views

- **Executive:** stage, decision, owner, top risk, cost gate, next approval.
- **Operations:** due checks, incomplete sessions, critical holds, overdue remediation, QA capacity.
- **Safety:** recall, false-pass, unknown, physical disagreement, incidents, rollback state.
- **Privacy/Security:** raw-media access, deletion completion, integrity exceptions, incidents.
- **Finance:** one-time spend, run-rate, audit allocation, remediation reserve, cost per verified-control store-day.
