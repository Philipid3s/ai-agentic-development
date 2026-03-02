# AGENTS.md Template

## Purpose

Global operating rules for all agents in this project.

## Project Context

- Business objective:
- Primary users:
- Non-goals:

## Global Rules

- Never execute destructive actions without explicit approval.
- Use only declared tools for each role.
- Prefer short, structured outputs over long narrative text.
- Escalate on policy ambiguity or low-confidence decisions.

## Role Registry

- `orchestrator`: routes tasks, validates handoffs, tracks workflow state.
- `researcher`: gathers evidence, cites sources, flags uncertainty.
- `executor`: performs bounded actions through approved tools.
- `reviewer`: validates outputs against quality and policy checks.

## Handoff Contract (Required)

Each handoff must include:

- `task_id`
- `current_step`
- `input_schema_version`
- `required_output`
- `deadline_or_timeout`

## Tooling Policy

- Allowed tools:
- Forbidden tools:
- Network policy:
- Secret handling policy:

## Escalation Policy

Escalate to human when:

- action has legal/financial risk
- confidence below defined threshold
- missing data blocks deterministic decision

## Output Format Standard

- Always return:
  - `status`: `success | blocked | failed`
  - `summary`: one paragraph max
  - `artifacts`: file paths or IDs
  - `next_action`: explicit single next step

## Logging and Tracing

- Log all tool calls with timestamp and task ID.
- Record decisions and rationale for non-trivial branches.
- Store failures with reproducible context.
