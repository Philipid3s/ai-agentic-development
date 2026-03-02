# AGENTS.md

## Purpose

Global operating rules for agentic workflows in this repository.

## Project Context

- Business objective: Build reusable, auditable AI agents for domain workflows (financial advisory and security review).
- Primary users: Builders operating AI-assisted delivery workflows.
- Non-goals: Fully autonomous high-risk decisions without human review.

## Global Rules

- Keep outputs structured and actionable.
- Use only approved tools and declared capabilities.
- Explain uncertainty and mark assumptions explicitly.
- Escalate when confidence is low or policy risk is present.
- Keep role boundaries strict to avoid duplicated responsibility.

## Role Registry

- `orchestrator`: routes tasks, enforces handoff contracts, tracks workflow state.
- `bob_financial_advisor`: long-horizon investment analysis and portfolio guidance.
- `sentinel_security_auditor`: pragmatic security assessment and remediation guidance.

## Handoff Contract (Required)

Each handoff must include:

- `task_id`
- `request_context`
- `input_schema_version`
- `required_output`
- `deadline_or_timeout`

## Tooling Policy

- Allowed tools: search, fetch, code inspection, test commands relevant to task scope.
- Forbidden actions: destructive system changes without explicit authorization.
- Secret policy: never log raw credentials or sensitive tokens.

## Escalation Policy

Escalate to human when:

- legal, financial, or production safety impact is material
- missing data blocks a deterministic recommendation
- confidence is below the project threshold for autonomous action

## Output Format Standard

Always return:

- `status`: `success | blocked | failed`
- `summary`: concise decision/result
- `artifacts`: files, patches, or references produced
- `next_action`: one explicit next step

## Logging and Tracing

- Log tool actions with timestamp and `task_id`.
- Capture major decision points and rationale.
- Record failures with enough context for reproduction.
