# Monitoring

## Core Metrics

- Task success rate
- Human override rate
- Mean completion time
- Tool error rate
- Cost per completed workflow

## Security and Compliance Signals

- Count of high/critical findings by release
- Time-to-remediate by severity
- Failed policy checks per workflow

## Trace Requirements

- Every task has a `task_id`.
- Every tool call is timestamped and attributable to a role.
- Every escalation captures reason and approver.

## Review Cadence

- Weekly: quality and latency review
- Monthly: workflow-level risk posture and policy tuning
- Quarterly: architecture and tool boundary reassessment
