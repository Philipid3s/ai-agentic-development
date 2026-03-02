# Workflows

## WF-001 Financial Guidance

1. Intake user objective and constraints.
2. Route to `bob_financial_advisor`.
3. Produce structured analysis (bull, bear, sizing, entry).
4. Run policy/disclaimer check.
5. Return recommendation plus next action.

## WF-002 Security Audit

1. Intake audit scope and target artifacts.
2. Route to `sentinel_security_auditor`.
3. Execute checklist and evidence capture.
4. Produce prioritized findings and remediation plan.
5. Return risk posture and follow-up actions.

## WF-003 Combined Decision Support

1. Run domain analysis (`bob` or other specialist).
2. Run `sentinel`-style risk pass if security/compliance implications exist.
3. Orchestrator reconciles outputs and highlights tradeoffs.
4. Escalate to human for high-risk decisions.
