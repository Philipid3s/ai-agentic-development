# Command Usage Flow

Use this sequence for consistent multi-agent execution in Claude Code.

## 1) Route the task with `/orchestrator`

Prompt template:

```text
/orchestrator
Task: <what needs to be done>
Scope: <files/modules/endpoints>
Constraints: <time/policy/risk constraints>
Output: Create a typed handoff payload and select the correct target role.
```

Expected result:

- A structured routing decision
- A handoff payload with `task_id`
- Risk flags and next action

## 2) Execute domain review with specialist command

Security review path:

```text
/sentinel
Use this handoff payload:
<paste orchestrator handoff json>
Run a scoped security audit and return severity-ranked findings with fixes.
```

Financial analysis path:

```text
/bob
Use this handoff payload:
<paste orchestrator handoff json>
Provide bull/bear analysis, sizing guidance, and risk-aware recommendation.
```

Expected result:

- Structured specialist output
- Clear risk framing
- Actionable remediation or recommendation

## 3) Final decision with `/orchestrator`

Prompt template:

```text
/orchestrator
Given this specialist output:
<paste specialist result json>
Return final status, risk flags, and single next action.
```

Expected result:

- `status` set to `success | blocked | failed`
- Explicit go/no-go decision
- One concrete next step

## 4) Minimal quality gate before closure

- `task_id` unchanged from start to finish
- Output contains status, summary, artifacts, next action
- High-risk items escalated for human approval

