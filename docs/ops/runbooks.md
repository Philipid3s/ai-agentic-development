# Runbooks

## Incident: Agent Output Quality Drop

1. Freeze autonomous execution for impacted workflow.
2. Switch to human-in-the-loop approvals.
3. Inspect last 20 task traces for drift pattern.
4. Roll back recent prompt/skill/config changes.
5. Re-run benchmark eval set before restoring autonomy.

## Incident: Tool Failure or External API Outage

1. Mark workflow status as degraded.
2. Use cached or fallback provider where possible.
3. Return partial output with explicit limitations.
4. Notify owner with expected recovery window.

## Incident: High-Risk Recommendation

1. Flag as escalation-required.
2. Block side effects until human approval.
3. Attach supporting rationale and alternatives.
