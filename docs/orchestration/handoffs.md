# Handoffs

## Contract Fields

- `task_id`: stable ID for traceability
- `owner_role`: current agent/step owner
- `target_role`: next agent
- `request_context`: concise problem statement
- `inputs`: typed payload and schema version
- `output_required`: expected structure
- `constraints`: time, risk, policy limits
- `due_by`: timeout/deadline

## Handoff Example

```json
{
  "task_id": "wf-002-20260302-001",
  "owner_role": "orchestrator",
  "target_role": "sentinel_security_auditor",
  "request_context": "Audit auth endpoint changes for exploitable risks",
  "inputs": {
    "schema_version": "1.0",
    "files": ["api/auth.ts", "db/user_repo.ts"]
  },
  "output_required": "severity-ranked findings with concrete fixes",
  "constraints": {
    "max_duration_minutes": 30,
    "policy": "no speculative claims"
  },
  "due_by": "2026-03-02T16:00:00Z"
}
```
