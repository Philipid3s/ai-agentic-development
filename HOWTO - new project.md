# HOWTO - Start a New Project with Claude Code

## 1. Start with an Executable Vision

Before opening Claude Code, clarify in 1 page:

- **Objective** - the precise problem you're solving
- **Target users** - who this is for
- **v1 features** - no more than 5-7
- **Out of scope** - what you're NOT building in v1
- **Roadmap** - planned evolution (v2, v3)

Only then launch Claude Code.

> Claude amplifies your level of clarity. Fuzzy vision = fuzzy code.

## 2. Generate Architecture BEFORE Code

Instead of: *"Build me a project X in Node"*

Ask: *"Propose 2 possible architectures for this project, compare them, and recommend the best fit for a fast but scalable v1."*

Cover:
- Front/back separation
- Folder structure
- Database strategy
- Config/env management
- Test strategy

Claude Code produces clean scaffolds - if you force it to think first.

## 3. Create a Minimal Skeleton

Only then:
- Initialize repo
- Clear README
- Folder structure
- `.env.example`
- Linter + formatters
- Docker (if needed)

Do NOT generate business logic yet. You want a healthy foundation, not a spaghetti project generated in one shot.

## 4. Define Contracts Before Implementations

Best practice with Claude Code:

1. Define types / interfaces
2. Define endpoints
3. Define data schemas
4. Write tests
5. Implement

Ask Claude: *"Generate the TypeScript interfaces and tests first, without implementation."*

This prevents technical debt from day one.

## 5. Work in Very Small Iterations

**Bad:** *"Implement the entire login + dashboard + user management feature"*

**Good:**
1. Create login endpoint -> test
2. Add validation -> test
3. Add persistence -> test

Claude Code is more reliable on atomic tasks.

## 6. Manage Context Intelligently

Claude understands large codebases well, but:
- Don't overload with the entire repo
- Provide only the necessary files
- Ask for targeted diffs

Example: *"Here are `user.service.ts` and `user.controller.ts`. Add Zod validation properly."*

## 7. Recommended Workflow

```
Architecture discussion
  -> Minimal scaffold
    -> Tooling setup
      -> Feature 1 implementation
        -> Light refactor
          -> Next feature
```

NOT: massive generation -> 3 days of debugging.

## 8. If Your Project Is AI / Agents

Start with:
- Component diagram
- Data flow
- Clear agent definitions
- Memory strategy
- Logging strategy

Agent projects become chaotic fast if you don't frame them upfront.

## 9. Use a Standard Slash Command Flow

For team consistency, use a 3-step command sequence:

1. `/orchestrator` to route and generate typed handoff payload
2. Specialist command (`/sentinel` or `/bob`) to produce structured output
3. `/orchestrator` again for final status, risk flags, and next action

Reference:
- `docs/orchestration/command-usage.md`
- `docs/orchestration/task-trace-example.md`

---

## Suggested Documentation Structure

```
/docs
  /vision
    product.md
    roadmap.md
  /architecture
    system-design.md
    data-model.md
  /features
    feature-auth.md
    feature-payments.md
  /decisions
    ADR-001-auth-strategy.md
    ADR-002-db-choice.md
```

