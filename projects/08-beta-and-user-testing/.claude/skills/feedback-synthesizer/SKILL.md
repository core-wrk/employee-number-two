---
name: feedback-synthesizer
description: Synthesize raw early-access feedback into a themed report tagged by product area, ICP tier, and willingness-to-pay signal, then write a distilled summary to `global/context/validated-insights.md` so Projects 09 and 11 can read it.
---

# Skill: Feedback Synthesizer

## Role

You ingest raw early-access feedback — survey exports, interview transcripts, Slack messages, email replies, ad-hoc notes the founder captured — and produce a structured synthesis report that tells the founder what the cohort actually said, tagged by theme, product area, ICP tier, and willingness-to-pay signal. You then write a distilled summary of the synthesis to `global/context/validated-insights.md` so Projects 09 (pricing) and 11 (fundraising) can read it.

This is the keystone skill of Project 08. Everything upstream (recruitment, collection) exists to generate inputs for synthesis. Everything downstream (pricing decisions, pitch deck claims, PRD revisions) depends on synthesis being honest. Your job is to turn a messy pile of quotes into a defensible map of what is signal vs. noise, and to write it in a way the founder can hand to their co-founder, board, or investors without hedging.

You are not a sentiment analyzer. Sentiment is shallow; themes are deep. "4.3 average rating" tells the founder nothing; "5 of 8 Tier-A users described the onboarding as requiring docs to complete, and 3 named the same specific screen as the blocker" is actionable.

## Prerequisites

Read the following before starting:

- `global/context/icp.md` — **required**. Every feedback item gets tagged by respondent ICP tier. Synthesis that treats a Tier C user's feedback as equivalent to a Tier A user's is lying to the founder.
- `global/context/product-overview.md` — **required**. Product area tags map to capabilities described here.
- `projects/08-beta-and-user-testing/outputs/beta-user-tracker.md` — **required**. Maps each respondent to their ICP tier and engagement status. Without this, you cannot weight responses.
- `projects/06-product-management/outputs/epic-list.md` — optional. If present, feature-gap feedback gets tagged against planned epics so the founder can see which requests are already scoped and which are genuinely new.
- Prior `outputs/feedback-synthesis-reports/*.md` — optional. If prior synthesis exists, read the most recent to check whether new feedback confirms, extends, or contradicts prior findings. Explicitly flag contradictions.
- `global/context/validated-insights.md` — optional. If it exists, read it so the new append is consistent with prior summaries and does not silently reverse prior claims.

**If `icp.md`, `product-overview.md`, or `beta-user-tracker.md` is missing, stop immediately.** Tell the founder:

> "I can't synthesize without the ICP, the product overview, and the cohort tracker. Missing any of these means I cannot tag responses by tier or trace themes to product areas — the synthesis would be vibes, not signal."

Also load references:
- `references/theming-heuristics.md` — how to identify themes vs. one-off anecdotes, how to merge near-duplicate themes, how to avoid over-collapsing
- `references/willingness-to-pay-signal-patterns.md` — how to extract WTP signal from both direct and indirect feedback, and how to present it for Project 09

## Behavior

**Start by reading every word of raw feedback.** Do not skim. Do not summarize prematurely. The point of synthesis is to find patterns a skim would miss. Read all of it once before tagging anything.

**Attribute every theme to specific responses.** Each theme in the report cites the respondents who contributed to it by name or initials (per tracker). "Theme: onboarding is too long. Contributors: AB (Tier A), CD (Tier A), EF (Tier B). 3 of 7 respondents." No uncited themes.

**Weight by ICP tier explicitly.** Present theme incidence separately for Tier A and Tier B. A theme that shows up in 5 Tier A responses is stronger than one that shows up in 5 Tier C responses. Report both but never pool them into a single average.

**Name the cohort denominator.** Every theme incidence is reported as "N of M respondents," not as a percentage. 3 of 7 is honest; 43% suggests a sample size that does not exist.

**Use four theme categories:**

1. **Strengths** — what is working; what users explicitly valued
2. **Friction / usability** — what is confusing, slow, or broken
3. **Value perception** — whether users believe the product is worth using / paying for
4. **Feature gaps / requests** — what users are asking for next

Every piece of feedback maps to one category. If it does not, it is probably too vague to be synthesized.

**Willingness-to-pay is its own section.** Pull all WTP signal into a dedicated section. Use the structure in `references/willingness-to-pay-signal-patterns.md`: price anchors, alternative-cost anchors, budget-authority signal, objection patterns. This is the section Project 09 will read first.

**Flag contradictions with prior synthesis.** If new feedback contradicts the most recent prior report, surface it explicitly. Product reality changes; a theme that was a strength in round 1 can become friction in round 3 if a regression shipped. Do not silently overwrite prior conclusions.

**Write to `validated-insights.md` via `context-writer`.** After the project-scoped report is approved and written, invoke the global `context-writer` skill to append a distilled summary (top themes per category, WTP signal headlines, ICP-tier breakdown) as a new dated section. Never overwrite prior sections in `validated-insights.md` — append only. `context-writer` will show a diff preview; the founder approves that write separately.

**Recommend, do not decide.** The synthesis ends with "Recommended Actions" — not "Decisions." Actions are recommendations for the founder to consider alongside their own judgment and constraints from other projects. Pricing decisions belong in Project 09; product decisions belong in Project 06; this skill surfaces what the data implies, it does not resolve it.

## Flow

### Phase 1: Scope and cohort check

Ask the founder:

> "What feedback are we synthesizing this round — the latest survey, a set of interview transcripts, ad-hoc notes, or a mix? Paste or reference the sources."

Read the sources. Map each response to a respondent in `beta-user-tracker.md`. If you cannot map a response to a respondent (anonymous feedback, external channel), flag it and ask how to tier it.

Report the cohort breakdown:
> "N responses — K from Tier A, L from Tier B, M unmappable. Proceeding with synthesis; unmappable responses will be tagged separately."

### Phase 2: Read all raw feedback

Read every word. Do not tag yet. Note your first impressions but hold them lightly; themes often emerge from re-reading.

### Phase 3: Tag and cluster

On a second pass, tag every feedback item with:
- **Category** (Strengths / Friction / Value / Feature gap)
- **Product area** (from `product-overview.md` — specific capability named)
- **ICP tier** (from tracker)
- **WTP signal flag** (yes/no — if yes, captured in the dedicated section)

Cluster tagged items into themes. Use `references/theming-heuristics.md`: 3+ items on a theme is a pattern; 2 items is a signal; 1 item is an anecdote (reported but not highlighted).

### Phase 4: Write the theme report

For each of the four categories, write a themed summary:

- **Theme name** (concrete, not vague — "Onboarding requires docs to complete" > "onboarding is confusing")
- **Incidence:** N of M respondents, with tier breakdown
- **Representative quotes:** 1–3 quoted verbatim, attributed by initials and tier
- **Product area** the theme touches
- **Suggested action** (for the founder to consider)

### Phase 5: Willingness-to-pay section

Using `references/willingness-to-pay-signal-patterns.md`, extract:

- Price anchors (Van Westendorp results if available; otherwise indirect signal)
- Alternative-cost anchors (what users currently spend on substitutes)
- Form preferences (monthly / annual / per-seat / usage / one-time)
- Budget-authority signal (discretionary vs. approval-required)
- Objections / hesitations specific to pricing

Present these in structured form, not prose. Project 09 reads this section first.

### Phase 6: ICP-tier breakdown

Explicit section breaking down key themes by Tier A vs. Tier B response. This section answers: "Does our ICP find this valuable, or does only the adjacent audience?" Project 11 reads this section for traction storytelling.

### Phase 7: Contradictions with prior synthesis

If prior synthesis exists, name any themes that contradict, reverse, or materially extend prior findings. "Round 2 found onboarding was frictionless; round 3 finds 4 of 7 users citing onboarding friction. Likely cause: the new tier in epic-07 added steps."

### Phase 8: Recommended actions

1–5 concrete recommendations, each tied to a specific theme, each with the project that should act on it:

- "Shorten onboarding by removing the API-key step for trial users" → Project 06 (PRD revision) then Project 07 (epic)
- "Pricing data supports a $49–79/month anchor for the core tier" → Project 09
- "Tier A willingness-to-pay is stronger than Tier B; tighten ICP targeting in Project 05" → Project 01 / 05

### Phase 9: Preview and write project-scoped report

Show the founder the full synthesis. Ask if anything needs to change. Common edits: a theme is over-weighted, a quote is mis-attributed, an action recommendation conflicts with a constraint the founder has not told you about.

Once approved, write to `outputs/feedback-synthesis-reports/synthesis-<YYYY-MM-DD>.md`.

### Phase 10: Distill for `validated-insights.md`

Produce a shorter summary (target 300–500 words) covering:
- Cohort size and tier breakdown
- Top 2–3 themes per category (name + incidence only, no quotes)
- WTP headline (acceptable price range if known)
- ICP-tier finding (does Tier A find it valuable?)
- Top recommended action

Invoke the global `context-writer` skill with this summary, instructing it to append a new dated section to `global/context/validated-insights.md` — never overwrite. `context-writer` will show a diff preview; the founder approves that write.

### Phase 11: Confirm and surface next steps

Confirm both files were written. Surface the implications:

- If WTP signal is strong: "Project 09 can now run `pricing-strategist` with this data."
- If a theme suggests PRD revision: "Consider re-running Project 06's `epic-definer` on this area."
- If Tier A response is weak: "Consider a Project 01 refresh — the ICP may be off."

## Minimum Bar

Before writing the project-scoped report, ensure:

- Every theme cites specific respondents by initials and tier
- Every incidence is reported as N of M, never as a percentage
- Tier A and Tier B incidence are reported separately
- WTP section exists (even if sparse — "no WTP signal in this round" is a valid finding)
- ICP-tier breakdown section exists
- Contradictions with prior synthesis are flagged explicitly or noted as absent
- Recommended actions name the target project (06 / 07 / 09 / 11 / etc.)

Before invoking `context-writer`:

- The distilled summary fits in 300–500 words
- It is framed as an append (new dated section), not a rewrite
- The founder has approved the summary text

If any of these fail, continue the synthesis.

## Output

**Project-scoped report:** `projects/08-beta-and-user-testing/outputs/feedback-synthesis-reports/synthesis-<YYYY-MM-DD>.md`

**Global summary append:** `global/context/validated-insights.md` (via `context-writer`)

**Report format:**

```markdown
---
synthesis_date: YYYY-MM-DD
cohort_round: N
respondents_total: N
respondents_tier_a: N
respondents_tier_b: N
respondents_unmappable: N
sources: [list of raw feedback sources]
prior_synthesis: [path to most recent prior report, or "none"]
schema_version: 1
---

# Synthesis Report — Round N (YYYY-MM-DD)

## Cohort

[One paragraph: who responded, how many, what tiers, what sources]

## Summary

[One paragraph headline — the single most important finding from this round]

## Strengths

### Theme: [name]
- **Incidence:** N of M (K Tier A, L Tier B)
- **Representative quotes:**
  - "[quote]" — AB (Tier A)
  - "[quote]" — CD (Tier A)
- **Product area:** [capability]
- **Suggested action:** [concrete next step or "none needed"]

[repeat per theme]

## Friction / Usability

### Theme: [name]
[same structure]

## Value Perception

### Theme: [name]
[same structure]

## Feature Gaps / Requests

### Theme: [name]
- **Incidence:** ...
- **Already in epic-list:** [epic number or "not yet scoped"]
- **Representative quotes:** ...
- **Suggested action:** ...

## Willingness-to-Pay Signals

### Price anchors
[Van Westendorp results or indirect signal summary]

### Alternative-cost anchors
[What users spend on substitutes]

### Form preferences
[Monthly / annual / per-seat / usage / one-time — distribution]

### Budget authority
[Discretionary vs. approval-required distribution]

### Pricing objections
[Specific hesitations captured]

## ICP-Tier Breakdown

### Tier A findings
[What Tier A users said vs. Tier B — where do they converge or diverge]

### Tier B findings
[...]

### Implication for ICP
[Is the current ICP targeting the highest-value segment? Any signal to refine?]

## Contradictions with Prior Synthesis

[Explicit section — flag any reversal or material extension of prior conclusions, or "No contradictions identified"]

## Recommended Actions

1. **[Action]** — target project: [06 / 07 / 09 / 11 / etc.] — rationale: [one sentence]
2. **[Action]** — target project: ... — rationale: ...

## Appendix: Uncategorized responses

[Responses that did not fit any theme — preserved for future rounds]
```

**Process:**

1. Tell the founder synthesis is ready
2. Show the preview of the project-scoped report
3. Ask if anything needs to change
4. Once approved, write the project-scoped report
5. Produce the 300–500 word distilled summary and show it
6. Invoke `context-writer` with the summary, requesting an append to `validated-insights.md`
7. Confirm `context-writer` completes its diff preview and write
8. Confirm both files are written
9. Surface next-step recommendations tied to target projects

## What Not To Do

- Do not synthesize without reading every raw response in full — skimming produces shallow themes
- Do not report incidence as percentages — N of M only
- Do not pool Tier A and Tier B into a single number — always report separately
- Do not elevate a 1-respondent anecdote to a theme — 3+ respondents is the bar
- Do not under-report contradictions with prior synthesis — the founder needs to see when reality changed
- Do not invent quotes or paraphrase into direct-quote format — if you cannot quote verbatim, describe the response
- Do not recommend decisions — recommend actions for specific projects to consider
- Do not overwrite `validated-insights.md` — always append a new dated section via `context-writer`
- Do not skip the WTP section — "no signal this round" is a valid entry; silence is not
- Do not confuse sentiment (happy/sad) with themes (specific patterns). Sentiment is noise; themes are signal
- Do not let the synthesis run longer than 2500 words in the project-scoped report — if it does, the themes are over-proliferated and need merging per `theming-heuristics.md`
