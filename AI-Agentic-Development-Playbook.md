# AI Agentic Development Playbook

This repository can be your operating manual for building, running, and scaling AI-agentic projects.

## 1) Core Principles

- Keep orchestration explicit: write down agent roles, tool boundaries, and handoff rules.
- Start from workflows, not models: map business process first, then assign agents.
- Optimize for observability: every agent action should leave a trace.
- Favor deterministic contracts: typed inputs/outputs beat free-form prompts.
- Keep loops bounded: retries, escalation, and stop conditions must be defined.

## 2) Recommended File Set

Use this minimum structure for each new project:

```text
/docs
  /agents
    AGENTS.md                    # global rules, behavior, guardrails
    role-<name>.md               # one file per agent role
  /skills
    <skill-name>/SKILL.md        # reusable workflow skill definition
  /orchestration
    workflows.md                 # workflow map + step ownership
    handoffs.md                  # handoff contracts between agents
  /ops
    runbooks.md                  # incidents, retries, fallback paths
    monitoring.md                # logs, traces, quality metrics
  /product
    goals.md                     # business outcomes + KPI mapping
    scope-v1.md                  # in/out scope to control complexity
```

## 3) Agent Definition Best Practice

Every agent definition should include:

- Mission: one clear responsibility.
- Inputs: data sources and expected schema.
- Tools: allowed tools only, with intent and limits.
- Decision policy: how it chooses actions.
- Output contract: strict format with examples.
- Failure policy: retry rules, fallback, and escalation path.

If two agents can do the same decision step, boundaries are not clear enough.

## 4) Skill Design Best Practice

A strong skill package includes:

- `SKILL.md`: intent, triggers, workflow, constraints.
- `templates/`: reusable prompts, payload schemas, report formats.
- `scripts/`: helper scripts for repeatable actions.
- `references/`: minimal links/docs needed to execute correctly.

Skill quality checks:

- Trigger conditions are explicit and testable.
- Workflow can run without hidden assumptions.
- Inputs/outputs are machine-readable where possible.
- Safe fallback exists when dependencies fail.

## 5) Orchestration Guidelines

- Use a coordinator only when needed; avoid central bottlenecks.
- Keep handoffs typed and minimal (no full-context dumping).
- Prefer event-driven state updates over long prompt chains.
- Track workflow state in durable storage, not only prompt context.
- Add idempotency keys for tool-calling steps.

## 6) Governance and Safety

Define policy files early:

- Access matrix: who can call which external systems.
- Data handling: PII/PHI rules, retention, redaction.
- Escalation policy: what requires human approval.
- Audit policy: what logs are mandatory for compliance.

## 7) Evaluation and Quality

Run 3 evaluation layers:

- Unit evals: single-agent behavior against fixed cases.
- Workflow evals: multi-agent end-to-end scenarios.
- Production evals: drift, latency, cost, and failure rate.

Track at least:

- Task success rate
- Human override rate
- Mean completion time
- Tool error rate
- Cost per completed workflow

## 8) Rollout Strategy

- Phase 1: shadow mode (no real side effects).
- Phase 2: human-in-the-loop approvals.
- Phase 3: scoped autonomy on low-risk workflows.
- Phase 4: broader autonomy with continuous monitoring.

## 9) Suggested Next Step in This Repo

- Keep this playbook as your root reference.
- Use template files in `/templates` for every new project.
- Expand with domain-specific skills once base workflow is stable.
