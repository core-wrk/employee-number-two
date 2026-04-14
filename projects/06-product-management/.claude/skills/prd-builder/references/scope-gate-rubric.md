# Scope Gate Rubric

Internal reference used by `prd-builder` for Phase 4 (scope negotiation). Use this when the founder is trying to make everything P0 or refusing to name non-goals.

## The Core Problem

Founders chronically over-scope. The reasons are predictable:

- **Optionality bias.** Keeping a goal in the PRD feels like keeping options open. Cutting it feels like closing a door.
- **Stakeholder echo.** Every prospect asks for something different; all of them end up in the PRD.
- **Fear of the non-goal.** Writing down a non-goal means the founder has to defend it later.
- **Competitor anxiety.** Competitors have feature X, so the PRD "can't be smaller than" the competitive set.

A PRD where everything is P0 is a PRD that cannot be built. The scope gate is the conversation that forces real priority.

## The 3-Goal Cap (Default)

Early-stage PRDs should have **no more than 3 P0 goals**. More than that usually indicates:

1. Some "goals" are actually tactics (outputs, not outcomes)
2. Two goals are secretly the same goal
3. The founder is optimizing for optionality, not execution

If the founder insists on more than 3 P0 goals, apply the pressure below before accepting.

## Pressure Test 1: The Next-6-Months Test

Ask the founder:

> "In the next 6 months, if you could only hit one of these goals, which one? If hitting that one goal was a clear success, which of the others would still matter?"

This usually collapses the list from 6 to 2–3. The goals that survive are the real P0s. The goals that fall out are usually P1s that the founder was inflating.

## Pressure Test 2: The Non-Goal Force

Ask the founder:

> "For every goal you have, name the adjacent goal you're NOT going to pursue. If you can't name the non-goal, the goal isn't real — it's just undifferentiated ambition."

Every P0 goal should have a paired non-goal. If the founder cannot name the non-goal, the goal itself is suspect.

## Pressure Test 3: The Evidence Test

Ask the founder:

> "Where in `icp.md`, the waitlist tracker, or your discovery-call notes is the evidence that this goal matters to the buyer? Quote something specific."

Goals without named evidence are hypotheses the founder has not tested. They become assumptions, not goals. Move them to Section 10.

## Pressure Test 4: The Competitive Honesty Test

Ask the founder:

> "If [Competitor A] already does this, why is this a P0 for us rather than a table-stakes feature we match in v2?"

Table-stakes features are not differentiating goals. They belong in functional requirements, not in Section 5 goals. The P0 goals should be the things this product does that no competitor does — the honest differentiation.

## When to Walk the Founder Back to Projects 01–05

If more than 2 of these pressure tests fail, the scope conversation is premature. Push the founder back:

- If ICP evidence is thin → run `icp-builder` again with discovery-call data
- If competitive differentiation is unclear → run `competitive-landscape-mapper` again
- If waitlist is empty → run Project 04's inbound skills first
- If the founder hasn't done discovery calls → run Project 05's `prospect-researcher` and `pre-call-brief-builder` before returning

A PRD built on speculation is a PRD that gets thrown out in 3 months. Force the upstream work.

## Phrasing the Pushback

When you push back on scope, do it in the founder's language, not in criticism:

- ❌ "That's too many P0s."
- ✅ "I can write a PRD with 6 P0s, but `epic-definer` will turn those into 18 epics, and you won't ship them all in 6 months. Before we write that, let's pressure-test which 2–3 are non-negotiable."

The founder should feel the conversation is helping them think, not graded against them.

## Non-Goal Catalyst List

Common non-goals for early-stage B2B SaaS. Surface these if the founder is stuck:

- "Serving SMB customers" (if ICP is mid-market)
- "Building a mobile app" (if buyer works in spreadsheets)
- "Replacing [incumbent system]" (usually integrate, don't replace)
- "Supporting self-serve signup" (if sales-assist is the motion)
- "Competing on feature breadth" (differentiation is usually depth)
- "Internationalizing" (most pre-Series A products stay English/US)

## Accepting More Than 3 P0 Goals

Sometimes the founder is right — there are genuinely 4 P0 goals because the product is a two-sided marketplace, or because the PRD is covering two distinct personas. Accept it **only** if:

1. Every P0 has a named piece of evidence from ICP/waitlist/discovery
2. Every P0 has a paired non-goal
3. The founder has acknowledged that 4 P0s means a 9–12 month execution window, not a 6-month one
4. The risk of under-shipping is captured in Section 11

Otherwise: push back. The cost of a bad scope decision at PRD time is months of wasted engineering.