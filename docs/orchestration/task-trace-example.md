# Example Task Trace

## Scenario

Security review request for authentication changes before release.

## Step 1: Intake

```json
{
  "task_id": "wf-002-20260302-001",
  "owner_role": "user",
  "target_role": "orchestrator",
  "request_context": "Audit auth changes for exploitable vulnerabilities before deploy",
  "inputs": {
    "schema_version": "1.0",
    "files": ["api/auth.ts", "db/user_repo.ts", "middleware/session.ts"]
  },
  "output_required": "release recommendation with severity-ranked findings",
  "constraints": {
    "max_duration_minutes": 30,
    "policy": "no speculative claims"
  },
  "due_by": "2026-03-02T16:00:00Z"
}
```

## Step 2: Orchestrator Handoff

```json
{
  "task_id": "wf-002-20260302-001",
  "owner_role": "orchestrator",
  "target_role": "sentinel_security_auditor",
  "request_context": "Run security audit on auth path",
  "inputs": {
    "schema_version": "1.0",
    "scope": {
      "modules": ["api/auth.ts", "db/user_repo.ts", "middleware/session.ts"],
      "checks": ["authz", "input_validation", "session_handling", "error_leakage"]
    }
  },
  "output_required": "structured findings + risk posture + go/no-go signal",
  "constraints": {
    "max_duration_minutes": 25,
    "severity_focus": ["CRITICAL", "HIGH", "MEDIUM"]
  },
  "due_by": "2026-03-02T15:55:00Z"
}
```

## Step 3: Sentinel Output (Abbreviated)

```json
{
  "status": "success",
  "summary": "2 medium findings, 1 low finding; no critical exposure detected",
  "findings": [
    {
      "severity": "MEDIUM",
      "location": "api/auth.ts:88",
      "issue": "Missing brute-force protection",
      "impact": "Credential stuffing risk",
      "exploitability": "Easy",
      "fix": "Add rate limit and lockout thresholds"
    },
    {
      "severity": "MEDIUM",
      "location": "middleware/session.ts:41",
      "issue": "Session cookie missing SameSite=Strict",
      "impact": "Increased CSRF exposure",
      "exploitability": "Moderate",
      "fix": "Set SameSite=Strict and secure defaults"
    }
  ],
  "risk_posture": "Manageable Risk",
  "next_recommended_action": "Patch medium findings before production release"
}
```

## Step 4: Final Orchestrator Decision

```json
{
  "status": "blocked",
  "routing_decision": "Release blocked pending MEDIUM fixes",
  "risk_flags": ["auth hardening incomplete", "session policy gap"],
  "next_action": "Apply patches, rerun sentinel audit, then reassess release"
}
```

## Why This Example Matters

- Demonstrates stable `task_id` traceability.
- Shows typed handoffs instead of free-form prompts.
- Makes escalation and go/no-go logic auditable.
