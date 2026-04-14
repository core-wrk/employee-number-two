# Current Bet Patterns

Internal reference used by `roadmap-builder` in Phase 2. The Current Bet is the paragraph that turns the roadmap from a backlog into a strategy.

## What a Current Bet Is

One paragraph — typically 3–5 sentences — that answers four questions:

1. **What is this roadmap optimizing for?** (The outcome, not the output.)
2. **What are you betting on to produce that outcome?** (The mechanism.)
3. **What does "the bet worked" look like in 6 months?** (The falsifiable success condition.)
4. **What is this deliberately not optimizing for?** (The protection against scope drift.)

A bet paragraph that answers all four feels like a real strategic statement. One that answers 1 and 2 but not 3 and 4 reads like a marketing blurb.

## The Shape

```
[Outcome we're trying to produce]. We're betting that [mechanism — the specific move that will produce the outcome], because [evidence / reasoning / context anchor]. In six months, the bet has worked if [falsifiable signal]. We are deliberately not [adjacent thing we're saying no to].
```

## Worked Examples

### Example 1: Early-stage B2B SaaS wedging into a market

> Our first 10 paying customers come from winning the "cohort attribution" wedge in the mid-market sales enablement segment. We're betting that shipping first-class Salesforce integration + cohort reporting in the next 8 weeks will be the thing that converts our 4 highest-tier waitlist signups into design partners, because 3 of 4 explicitly named SFDC attribution as their top unmet need in discovery. In six months, the bet has worked if we have 6+ signed design partners and at least 3 have converted to paid pilots. We are deliberately not building out reporting breadth or serving SMB — breadth is post-wedge work and SMB has the wrong pricing model for us.

**Why it works:** Specific outcome, specific mechanism, evidence anchor, concrete 6-month signal, explicit non-goal.

### Example 2: Dev tool with early traction

> We convert the current open-source usage into commercial signal by shipping the "hosted" tier with usage-based pricing. We're betting that 20% of active OSS users will convert to hosted within 90 days of launch, because the top 3 GitHub issues asking for hosted support map to a concrete painful workflow most users hit. In six months, the bet has worked if MRR has crossed $15K and we have at least 5 hosted customers paying >$500/mo. We are deliberately not building an enterprise tier yet — enterprise features fragment the product and we haven't validated that the market will pay for them.

**Why it works:** Clear conversion mechanism, quantified 6-month target, rationale for deferral.

### Example 3: Consumer product pre-launch

> We validate that our core activation loop (signup → first-value moment in <5 minutes) works for the target segment before spending on paid acquisition. We're betting that an instrumented alpha with 50 users from our waitlist will either confirm the loop or surface the specific friction breaking it, because current self-report is unreliable and we've already tried 3 landing page variations. In six months, the bet has worked if D1 retention from a cohort of 50 alpha users exceeds 40% or we've identified the one specific change that gets us there. We are deliberately not working on growth loops, referral mechanics, or social features — those are post-retention problems.

**Why it works:** Validates before scales, names the measurement, explicit premature optimization avoidance.

## Patterns to Match

Good bet paragraphs usually match one of these meta-shapes:

### Shape A: Wedge bet

"Win [specific niche] first by [specific move]. In 6 months, winning looks like [concrete signal]. We're explicitly not [broader-market ambition]."

Use when the strategy is to dominate a narrow wedge before expanding.

### Shape B: Validation bet

"Answer [specific open question] before [bigger commitment]. In 6 months, the answer is [concrete condition]. We're not doing [the bigger commitment] yet — it's gated on this validation."

Use when the near-term is about reducing uncertainty before a larger investment.

### Shape C: Conversion bet

"Convert [existing asset — waitlist, OSS users, design partners] into [commercial outcome]. In 6 months, conversion looks like [concrete metric]. We're not [growth or acquisition work] — that is downstream of conversion."

Use when there's already demand signal and the strategy is to monetize it.

### Shape D: Infrastructure bet

"Unblock [future strategic move] by building [foundational capability]. In 6 months, the infrastructure is in place if [specific technical milestone]. We're deliberately not [scaling moves] — they're gated on this foundation."

Use when the honest strategy is that the next 6 months are about enabling future velocity, not about near-term customer outcomes. Rare but valid.

## Anti-Patterns to Avoid

### Anti-pattern 1: Vision statement as bet

> "We're building the best product management tool on the market."

This is a vision, not a bet. It has no falsifiable 6-month signal and no explicit mechanism.

**Fix:** Force the specific outcome and the mechanism. "Best tool on the market" becomes "ship the top 3 most-requested features from waitlist respondents in 8 weeks; validate conversion intent."

### Anti-pattern 2: Kitchen sink

> "We're growing MRR, shipping new features, improving onboarding, winning design partners, and increasing retention."

Five bets is no bets. Pick one.

**Fix:** Ask "if you had to pick the single most important outcome, which is it?" That's the real bet. The others are supporting or deferred.

### Anti-pattern 3: Unfalsifiable signal

> "The bet has worked if we have strong momentum and clear customer love."

"Strong momentum" is not measurable. "Customer love" is not measurable.

**Fix:** Force concrete signals. "Strong momentum" becomes "MRR >$10K with positive 3-month growth trend." "Customer love" becomes "NPS >40 across 20+ respondents or 3 unsolicited referrals."

### Anti-pattern 4: No non-goal

> [Paragraph with no "we are deliberately not" clause]

Without the non-goal, the bet doesn't protect from scope creep. Every prospect conversation ends up "we could also do X."

**Fix:** Force the founder to name at least one thing being deliberately deferred. If they can't, the bet isn't real — they're hedging.

### Anti-pattern 5: Same bet across multiple runs

The `## Previous Bets` audit trail shows the same paragraph (with minor rewording) appearing 3 times in a row.

**Fix:** Either the bet is genuinely still active (the signals haven't come in yet — fine, but note it) or the bet is stale (the situation changed and the bet should evolve — rewrite).

## Writing the Paragraph in Conversation

Don't ask the founder to write the paragraph in one shot. Walk through it:

1. "What's the single most important outcome in the next 6 months?"
2. "What are you betting on to produce that outcome?"
3. "What evidence or reasoning makes you think that bet is right?"
4. "What does 'the bet worked' look like concretely?"
5. "What are you deliberately not doing?"

Then synthesize the answers into a paragraph. Show the draft. Iterate.

## Length

3–5 sentences. Longer than 5 usually means the founder is hedging — two bets in one paragraph, or qualifications that dilute the commitment. Tighten until it's one bet, clearly stated.

Shorter than 3 usually means the bet isn't specific enough — it's skipping one of the four questions (outcome, mechanism, signal, non-goal).

## When to Stop Iterating

The paragraph is done when:

- All four questions (outcome, mechanism, signal, non-goal) are visible in the text
- The founder reads it back and nods
- Reading it 30 days from now would be useful context (not just a restatement of whatever they happened to be thinking that week)

Don't perfect it. Ship a good-enough bet and revise in the next run.