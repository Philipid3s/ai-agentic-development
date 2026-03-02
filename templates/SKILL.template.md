# SKILL.md Template

## Skill Name

<skill-name>

## Purpose

What this skill does and when to use it.

## Trigger Conditions

Use this skill when:

- condition 1
- condition 2

Do not use this skill when:

- exclusion 1

## Inputs

- Required:
  - `input_a`:
  - `input_b`:
- Optional:
  - `input_c`:

## Workflow

1. Validate required inputs.
2. Load only minimum required references.
3. Execute deterministic steps in order.
4. Produce structured output.
5. Run final quality checks.

## Output Contract

Return:

- `status`
- `result`
- `evidence`
- `next_recommended_action`

## Dependencies

- scripts:
  - `scripts/<helper>.ps1`
- templates:
  - `templates/<output>.md`
- references:
  - `references/<doc>.md`

## Constraints

- Time limits:
- Cost limits:
- Safety/policy limits:

## Failure and Fallback

If blocked:

1. Report exact blocker.
2. Provide best partial output.
3. Suggest smallest unblocking action.

## Quality Checklist

- Trigger matched correctly.
- Inputs validated.
- Output schema respected.
- Evidence included.
- No policy violations.
