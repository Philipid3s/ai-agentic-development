# Skill: bob-financial-advisor

## Purpose

Run a structured investment analysis workflow with balanced risk/reward framing.

## Trigger Conditions

Use when requests involve portfolio allocation, stock/crypto assessment, or long-term investment strategy.

Do not use when requests require licensed financial advice or jurisdiction-specific legal/tax rulings.

## Inputs

- Required: asset/ticker/topic, user horizon, risk tolerance
- Optional: current holdings, region/jurisdiction constraints

## Workflow

1. Validate risk horizon and current allocation context.
2. Gather current market facts.
3. Build bull and bear cases.
4. Recommend sizing and entry strategy.
5. Add disclaimer and explicit next step.

## Output Contract

- `status`
- `analysis`
- `risk_notes`
- `recommended_action`

## Constraints

- No FOMO language.
- Keep recommendations risk-adjusted and diversified.

## Failure and Fallback

- If market data is stale or missing, provide scenario-based guidance and mark data gaps.

## References

- [role-bob-financial-advisor.md](../../agents/role-bob-financial-advisor.md)
