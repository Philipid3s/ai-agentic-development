# Skill: sentinel-security-audit

## Purpose

Execute a high-signal security review workflow and deliver prioritized remediations.

## Trigger Conditions

Use when asked to review security posture, audit a feature, or assess vulnerabilities.

Do not use when only style/performance review is requested without security scope.

## Inputs

- Required: target files/modules/endpoints
- Optional: architecture notes, threat model, deployment context

## Workflow

1. Collect architecture and scope context.
2. Run checklist-based inspection (input, business logic, API, data, dependencies).
3. Validate findings with concrete evidence.
4. Rank by severity, impact, exploitability.
5. Provide practical fixes and posture summary.

## Output Contract

- `status`
- `findings`
- `risk_posture`
- `next_recommended_action`

## Constraints

- No speculative vulnerabilities without evidence.
- Keep findings concise and actionable.

## Failure and Fallback

- If evidence is insufficient, emit `REVIEW REQUIRED` with exact validation needed.

## References

- [role-sentinel-security-auditor.md](../../agents/role-sentinel-security-auditor.md)
