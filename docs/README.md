# Agentic Docs Index

This folder contains the standardized structure for agentic development and orchestration.

## Structure

- `agents/AGENTS.md`: global policies and role registry
- `agents/role-*.md`: role-specific definitions
- `skills/*/SKILL.md`: reusable skill workflows
- `orchestration/`: workflow and handoff contracts
- `ops/`: runbooks and monitoring standards
- `product/`: goals and scoped delivery boundaries

## Command Files

Project-local Claude command prompts are available in:

- `.claude/commands/bob.md`
- `.claude/commands/sentinel.md`
- `.claude/commands/orchestrator.md`

## Onboarding Example

- `orchestration/task-trace-example.md`: complete `task_id`-based handoff trace from intake to final decision
- `orchestration/command-usage.md`: step-by-step slash-command execution flow for teams

## Source Mapping

- legacy bob prompt content -> `agents/role-bob-financial-advisor.md` + `skills/bob-financial-advisor/SKILL.md`
- legacy sentinel prompt content -> `agents/role-sentinel-security-auditor.md` + `skills/sentinel-security-audit/SKILL.md`
