# Theming Heuristics

Internal reference for `feedback-synthesizer`. Themes are the unit of synthesis. Good themes are specific, cited, and actionable. Bad themes are generic, uncited, and un-actionable. These heuristics separate the two.

---

## Theme bar

A theme must clear all of these:

1. **3+ respondents** cite it directly or describe a functionally equivalent experience
2. **Specific enough to act on** — "onboarding is confusing" is not a theme; "users stall at the API-key entry screen" is
3. **Attributable** — you can name the respondents who contribute to it
4. **Not trivially mergeable** with an adjacent theme — if Theme A and Theme B are the same thing in different words, merge them

Responses that fail the 3+ bar stay in the "Uncategorized" appendix, not in the theme list. Preserving them is important — a 1-respondent signal in round 1 may become a 4-respondent theme in round 3.

---

## Specificity test

Good theme names:
- "Users cannot find the export button in the dashboard header"
- "First-session value moment requires three tool-switches away from the product"
- "Tier A users would pay but Tier B users would not at the same anchor price"

Bad theme names (reject):
- "UX issues"
- "Pricing concerns"
- "Onboarding friction"
- "Product is good"

The test: could two different readers of the theme independently describe the same problem? If no, the theme is too vague.

---

## Merging adjacent themes

Themes often arrive as near-duplicates because users describe the same pain in different words. Merge when:

- The product area is the same
- The user action is the same
- The experience is the same (friction, success, confusion)

Do not merge when:

- The user role or ICP tier differs in a meaningful way (Tier A has the issue, Tier B does not — that itself is the theme)
- The product area is adjacent but distinct (onboarding flow vs. first-session-after-onboarding are different themes)
- The user's stated reason differs (three users say onboarding is slow; two because of the API-key step, three because of the docs — two themes, not one)

When in doubt, keep two themes and name the distinction explicitly rather than collapsing.

---

## Over-proliferation signal

If synthesis produces more than ~10 themes across all four categories combined, you are probably over-proliferating. Merge aggressively. A strong synthesis has 4–8 themes that the founder can actually hold in mind and act on. A weak synthesis has 20 themes that all blur together.

---

## Under-collapsing signal

If synthesis produces fewer than 3 themes for a meaningful batch of feedback (10+ responses), you are probably under-collapsing or reading too shallowly. Re-read the raw feedback with specificity in mind. Users who say "it was fine" are probably saying something more specific that got lost.

---

## Weighting by tier

Never average across tiers. Report:
- Tier A incidence (N of Tier-A respondents)
- Tier B incidence (N of Tier-B respondents)
- Pooled incidence only as a third, secondary number

When Tier A and Tier B diverge on a theme, name the divergence — it is often the most important signal in the round. A theme present in 5 of 5 Tier A but 0 of 3 Tier B is almost certainly about the ICP, not the product.

---

## Sentiment vs. themes

Do not include sentiment as a theme. "Users are happy" is not a theme; "users value the export feature over the import feature 3 to 1" is. Sentiment scores (NPS, CSAT) go in the appendix as supporting data; themes are about what specifically drives the scores.

If a founder asks for "overall sentiment," provide the NPS or CSAT as a number in the cohort section — but do not let it displace themes.

---

## Theme types and where they live

| Theme type | Category | Action priority |
|---|---|---|
| "X feature drives the aha moment" | Strengths | Protect; do not break |
| "Users stall at Y" | Friction | Project 06 / 07 |
| "Users would pay for Z" | Value / WTP | Project 09 |
| "Users are asking for W" | Feature gaps | Project 06 |
| "Tier A loves it, Tier B doesn't" | ICP breakdown | Project 01 / 05 |
| "They cancelled because of V" | Friction (acute) | Highest priority — retention risk |

---

## Quote selection

Every theme gets 1–3 representative quotes. Choose quotes that:

- State the theme in the user's own words, not paraphrased
- Come from different respondents (not three quotes from the same user)
- Prefer Tier A respondents when available
- Include the respondent's tier and initials for attribution

Do not trim quotes in a way that changes their meaning. If a quote is too long to include verbatim, summarize and attribute: "AB (Tier A) described a 5-minute stall at the API-key entry screen."

---

## When a "theme" is really a decision

If a theme is actually asking the founder to decide something (which pricing tier, which feature to build next), do not resolve it in the synthesis. Name the decision and route it to the target project:

- Pricing-shape decisions → Project 09
- Feature-priority decisions → Project 06
- ICP-refinement decisions → Project 01

Synthesis surfaces what the data implies; it does not make the call.
