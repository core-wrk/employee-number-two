# Roadmap Sequencing Principles

Internal reference used by `roadmap-builder`. Rules for what belongs in Now vs. Next vs. Later and how to force the right conversation.

## The Three Buckets

### Now (0–6 weeks)

Things actively being worked or starting imminently.

**Criteria for Now:**
- Priority is P0 or P1
- All dependencies are Shipped, In Progress, or also in Now
- Fits inside current team capacity (see `capacity-calibration-guide.md`)
- The founder can name the "why now" — what makes this urgent in the current window

**Red flags for Now:**
- RICE score lower than something in Next (suggests sequencing is driven by preference, not evidence)
- No named dependency into Now from the Current Bet (the bet names one thing and Now is doing another)
- Effort + effort of other Now epics exceeds capacity

### Next (6–16 weeks)

Things that should happen after Now but before Later. Each has a named **trigger** — the condition that, when met, promotes it to Now.

**Criteria for Next:**
- Priority is P0, P1, or high-RICE P2
- Dependencies are either in Now or clearly sequenced before
- Trigger is concrete and observable ("E04 ships," "3 beta users confirm the workflow," "funding close announced")

**Red flags for Next:**
- "Trigger" is vague ("when we're ready," "when it makes sense")
- Same epic has been in Next across 3+ re-runs with no progress on its trigger — probably should go to Later or be cut
- Many Next epics share the same trigger (if 5 epics all wait for "funding close," they're all really one contingent decision — flag it)

### Later (beyond 16 weeks)

Things that are not current bets but the founder doesn't want to cut. Each has an **open question** — the thing that would need to be answered before commitment is possible.

**Criteria for Later:**
- Priority is typically P2 or P3, or P0/P1 with significant uncertainty
- Open question is specific ("will the ICP broaden to include SMB?", "will SOC 2 be required at scale?", "will we build or buy the integration layer?")
- The open question is genuinely hard — if it could be answered in 30 days, the epic probably belongs in Next

**Red flags for Later:**
- No open question — just vague "someday" energy. Force a cut to Not Doing or a commitment to Next.
- Open question is something you could just ask a customer (in which case ask, don't defer)
- The epic has been in Later for 3+ re-runs with the same open question — probably a Not Doing in disguise

## Dependency Rules

Dependencies flow backward in time through the roadmap:

- Shipped → anywhere (already satisfied)
- In Progress → anywhere
- Now → dependents can be in Now (later in order) or Next
- Next → dependents can be in Next or Later
- Later → dependents can be in Later only

If a dependency violates the flow (e.g., Now epic depends on Later epic), one of three things is wrong:

1. The dependency is mis-labeled (not really a dependency)
2. The dependent's bucket is wrong (should be Later, not Now)
3. The dependency's bucket is wrong (should be Now, not Later)

Surface the violation; let the founder decide.

## Priority Rules

Within a bucket, sequence by priority then RICE score:

- P0s before P1s before P2s before P3s
- Within same priority, higher RICE score first
- Dependencies override priority order (a P1 that blocks a P0 ships before the P0)

## Capacity as the Enforcer

Capacity is the constraint that keeps Now honest. See `capacity-calibration-guide.md` for team-size mappings.

Typical capacity:
- Solo founder: 1 epic in parallel (with effort fitting in 6 weeks)
- 2-person team: 1–2 in parallel
- 3–4-person team: 2–3 in parallel
- Larger teams: scale up, but watch for coordination overhead

If Now has more epics than capacity allows, the founder is lying to themselves about what will happen. Force the cut.

## The Not Doing Discipline

Not Doing is where the roadmap protects itself from prospect-driven scope creep. The founder will have conversations with prospects who ask for things; without a Not Doing section, every conversation becomes a debate about whether to add the thing. With one, the answer is either (a) "it's in Later — here's what needs to be true first," or (b) "it's in Not Doing — here's why."

**What belongs in Not Doing:**
- Epics with `Status=Cut` from `epic-list.md` (automatic import)
- Capabilities the founder has explicitly decided against (with rationale)
- Adjacencies that are tempting but off-strategy (e.g., "serving SMB" when ICP is mid-market)

**Format:** Each entry is one line naming the capability plus a one-line rationale. Example:

> - **SMB self-serve signup flow:** Our ICP is mid-market with sales-assist motion; SMB would fragment GTM attention and the pricing model isn't yet designed for it.

**Minimum count:** at least 1. If the founder has nothing to put in Not Doing, they haven't said no to anything yet — that itself is a scope problem.

## Current Bet Must Dominate

The Current Bet paragraph is the filter. For each epic in Now, ask: "Does shipping this advance the bet?"

If the answer is "no, but…" — the epic is probably misplaced. Either:
- The bet is wrong (rewrite the Current Bet)
- The epic's priority is wrong (demote it)
- The epic belongs in Next or Later
- The epic is tactical maintenance that doesn't advance a bet but is necessary — capture as "infrastructure" or "platform" in Notes, but still keep it to ≤1 of these in Now

**Rule:** at least 80% of Now effort should directly advance the Current Bet. If less, the bet is not really the bet.

## Re-Run Triggers

Re-run `roadmap-builder` when:

1. Any Now epic ships (free up capacity, promote from Next)
2. Any assumption affecting Now epics is invalidated (back-pressure from `assumption-tracker`)
3. 4 weeks have passed since last run (time-based default)
4. External forcing function: funding close, key hire, major customer signed, design partner churned

Do not re-run on every small change. The roadmap's value is stability within a cadence; over-revising erodes it.

## Evolution Across Runs

Previous Bets are an audit trail. They show:

- How the thesis evolved (or didn't)
- When major pivots happened
- What earlier hypotheses were right or wrong

Future-self and investors benefit from this trail. Founders who run without an audit trail forget why they made earlier choices and re-litigate settled decisions.

## Anti-Patterns

- **Roadmap as wishlist.** 20 epics in Now, nothing shipped. Cut ruthlessly.
- **Roadmap as sales deck.** Now/Next/Later as "to impress prospects," not as actual sequencing. Keep this file internal; produce a prospect-facing view separately if needed.
- **Roadmap as Jira replacement.** This file is not a ticket tracker. Day-to-day work goes in `epic-list.md` and Project 07 artifacts. The roadmap is the strategic view.
- **Roadmap without review cadence.** If nobody re-runs `roadmap-builder`, the file decays. The review cadence is not optional.
- **Dates as commitments.** Dates turn the roadmap into a promise. Now/Next/Later keeps the honesty.