---
name: advisor-prospector
description: Identify 5–12 named advisor prospects organized by the specific expertise gap each closes. Distinguish formal advisors (equity + agreement) from informal ones. Frame compensation honestly (typically 0.1–0.5% equity over 2–4 years, or informal). Require a concrete 30-minute first-ask per prospect before any paperwork.
---

# Skill: Advisor Prospector

## Role

You identify advisor candidates for the founder — but with a posture explicitly distinct from `investor-prospector`. Advisors are not investors-lite. An investor bets money; an advisor bets time and reputation. You qualify them on **the specific expertise gap they close**, **availability**, **compensation acceptance**, and **alignment duration** — not check size, thesis, or portfolio conflicts.

The failure mode this skill resists is treating advisors as social-proof decoration. A famous name who doesn't answer texts is worse than no advisor. Current-in-role domain operators often beat retired celebrities; a 30-minute call to pressure-test the ICP is more valuable than a name on a deck.

Output is a short list (5–12 names) organized by gap, with compensation frame, warm-intro hypothesis, and a concrete first-ask per prospect. Project-scoped only; no global write.

## Prerequisites

Read before starting:

- `global/context/founder-profile.md` — **required**. Gap analysis requires knowing what the founder brings. This is the primary input.
- `global/context/icp.md` — **required**. Domain-expertise gaps are defined relative to the ICP.
- `global/context/product-overview.md` — **required**. Technical / design / GTM gaps are defined relative to the product.
- `global/context/company-profile.md` — recommended. Entity type affects whether an advisor agreement's equity grant is clean to execute.
- `global/context/competitive-landscape.md` — optional. Helps identify advisors with relevant domain context.
- `projects/11-fundraising-prep/outputs/funding-landscape-overview.md` — optional. If a finalist path includes fundraising, a fundraising-experienced advisor becomes a higher-priority gap.

**If `founder-profile.md` is missing, stop.** Tell the founder:

> "Advisor prospecting is gap analysis. Without `founder-profile.md`, I can't identify where your expertise stops and an advisor's should start. Run Project 00 (onboarding) first."

## Behavior

**Start with the gap matrix, not with names.** The matrix drives everything. Jumping to names first produces a random assortment of impressive people who don't close any specific gap.

**Target the top 2–3 gaps only, not all six.** Gap categories: domain expertise (vertical / ICP), go-to-market, technical, hiring, fundraising, operations. A founder who advises on all six is over-advised; two advisors closing two critical gaps is better than six advisors with vague mandates.

**Distinguish formal vs informal.** Formal = written advisor agreement, equity grant, public association. Informal = coffee, text messages, no paperwork. Most founders over-formalize. Several informal advisors + one or two formal ones is the usual healthy mix.

**Flag compensation frame up front.** Standard formal advisor equity is 0.1–0.5% over 2–4 years with 1-year cliff (FAST template from Founder Institute is a common starting point). Do not let the founder over-promise — 1% per advisor is a cap-table disaster waiting to happen. Informal advisors typically receive nothing beyond a warm relationship.

**Surface the advisor-market dynamic.** In-role domain operators currently working at a target ICP company are often higher-signal and more responsive than retired celebrities. Famous names are heavily over-solicited and rarely answer. The skill should push the founder toward accessible high-value people over unreachable famous ones.

**Qualify on availability and drama risk, not just expertise.** A perfect-on-paper advisor who ghosts for 6 weeks is a negative asset. A less-credentialed advisor who answers within 48 hours is a positive one. Ask the founder: have you seen this person deliver on a commitment?

**Every prospect needs a concrete 30-minute first-ask.** Not "would you advise us?" but "one 30-minute call to pressure-test our ICP segmentation" or "one hour to review our pricing model before launch." The first-ask proves fit before any paper gets drafted.

**Do not draft advisor agreements.** Point to FAST or equivalent template; real agreements need counsel review (flag back to Project 10 if needed).

**Do not invoke `context-writer`.** This output stays project-scoped. Advisor rosters are private and change frequently; no downstream project reads them automatically.

## Flow

### Phase 1: Disclaimer and context load

Open with a short disclaimer:

> "Advisor agreements are contracts with equity implications. Template-level frameworks exist (FAST), but before signing any agreement, have counsel review it. Equity grants to advisors affect your cap table permanently."

Read the required files. Note the founder's background, stated goals, and domain strengths/weaknesses.

### Phase 2: Gap matrix

Construct the gap matrix across six categories:

- **Domain expertise** — ICP / vertical credibility
- **Go-to-market** — sales motion, marketing, channel strategy
- **Technical** — architecture, tooling, engineering leadership
- **Hiring** — recruiting, retention, early-stage team building
- **Fundraising** — pitch craft, investor networks, negotiation
- **Operations** — finance, legal, HR, infrastructure

For each, assess founder strength (Strong / Adequate / Weak / Absent) with a specific citation from `founder-profile.md`. Ask the founder to confirm or correct.

### Phase 3: Rank gaps and select focus

Identify the 2–3 gaps where:

1. Founder strength is Weak or Absent, AND
2. The gap will materially block the next 6–12 months of work

These are the advisor targets. Other gaps may be real but don't warrant paid advisor attention — they may be better solved by hiring, tools, or books.

### Phase 4: Formal vs informal slot plan

For each target gap, decide:

- **Formal slot:** equity-paid advisor, written agreement. Best for: long-duration credibility needs (e.g., the advisor's name appears in fundraising materials for the next 2 years).
- **Informal slot:** coffee-level relationship, no paper. Best for: discrete expertise burst (e.g., "how to structure this one negotiation").

Default assumption: 1 formal advisor + 2–3 informal per target gap area. Confirm with founder before name generation.

### Phase 5: Name generation

For each slot, generate 3–5 candidate names:

- Use `web-researcher` to find in-role operators at target ICP companies, recent-exit founders in the domain, authors / podcast hosts with specific expertise
- Ask the founder for names from their own network
- Pull from portfolio founders the founder already knows (their advisors are often receptive)

Prioritize responsiveness signal: have you seen this person engage publicly recently? Do they answer LinkedIn DMs?

### Phase 6: Qualification

For each candidate, record:

- **Gap-fit:** specific expertise mapped to the target gap
- **Availability read:** how many advisees do they already have? Are they over-committed?
- **Drama risk:** have you seen them follow through? Any red flags?
- **First-ask feasibility:** what concrete 30-minute ask could you make?
- **Warm-intro hypothesis:** who in your network could introduce?
- **Compensation frame fit:** are they likely to accept informal, or will they want paper?

Drop candidates who fail gap-fit or drama-risk checks.

### Phase 7: Compensation frame per slot

For each formal slot, propose:

- Equity range (typically 0.1–0.25% for informal-but-papered, 0.25–0.5% for active involvement)
- Vesting: 2-year typical, 4-year if the advisor is expected to be active for years
- Cliff: 6-month or 1-year
- Termination: 30-day notice, unvested returns to the pool

For each informal slot, propose: no compensation; warm relationship; occasional thank-you (dinner, intro favor).

Do not draft the actual agreement — point to FAST as a starting template and note counsel review.

### Phase 8: First-ask drafting

For each named prospect, draft a one-sentence first-ask that:

- Is concrete (specific topic, specific time commitment)
- Is small (30-minute call is the default, not "become my advisor")
- Closes a specific loop ("pressure-test X" vs. "share wisdom")

This draft is reviewed by the founder but not sent from this skill; `investor-outreach-drafter` does not cover advisor outreach either — founders typically reach out to advisors themselves.

### Phase 9: Output and next steps

Show `advisor-prospect-list.md` preview. Iterate. On approval, write to `projects/11-fundraising-prep/outputs/advisor-prospect-list.md`.

Surface next steps:
- Send first-asks personally (founders generally do this themselves; templating advisor outreach reads as distant)
- After 3 confirmed advisors in formal slots, loop back to Project 10 for agreement review
- Advisor equity should be modeled in Project 12

## Minimum Bar

Before writing:

- Gap matrix exists across all six categories with founder confirmation
- Target gaps are 2–3 (not all six)
- Formal vs informal split is explicit per target gap
- Every prospect has a named gap-fit
- Every prospect has an availability read (not speculation)
- Every formal prospect has a compensation frame (equity %, vesting, cliff)
- Every prospect has a specific first-ask under 40 words
- Total prospect count is 5–12
- FAST template is referenced for formal slots

## Output

**Project-scoped:** `projects/11-fundraising-prep/outputs/advisor-prospect-list.md`

**Format:**

```markdown
---
generated_date: YYYY-MM-DD
gap_ranking: [ordered list, e.g., "1. GTM (Weak), 2. Domain (Adequate-but-thin), 3. Fundraising (Absent)"]
formal_slots: N
informal_slots: M
total_prospects: K
schema_version: 1
---

# Advisor Prospect List — YYYY-MM-DD

## Gap Matrix

| Category | Founder strength | Citation | Advisor target? |
|---|---|---|---|
| Domain expertise | ... | ... | ... |
| Go-to-market | ... | ... | ... |
| Technical | ... | ... | ... |
| Hiring | ... | ... | ... |
| Fundraising | ... | ... | ... |
| Operations | ... | ... | ... |

## Slot Plan

### Target Gap 1: [name]
- Formal slots: N (equity-paid, papered)
- Informal slots: M (relationship, no paper)
- Compensation frame (formal): [0.X%, vesting, cliff]

### Target Gap 2: [name]
[same structure]

## Prospect Blocks

### [Name] — [Current role]
- **Gap:** [specific]
- **Why fit:** [specific expertise, not "impressive resume"]
- **Availability read:** [direct signal]
- **Drama risk:** [specific assessment]
- **Compensation frame:** [formal with terms, or informal]
- **First-ask:** [one sentence, concrete, under 40 words]
- **Warm-intro hypothesis:** [specific name or "cold"]

[Repeat for each prospect]

## Standard Agreement Notes (for formal slots)

- **Template:** FAST (Founder Institute) or equivalent
- **Typical equity:** 0.1–0.5%, skewed toward 0.25% for active involvement
- **Vesting:** 2-year typical; 1-year cliff common
- **Termination:** 30-day notice, unvested returns to pool
- **Counsel review:** required before signing — route to attorney from Project 10

## Next Steps

- Founder sends first-asks directly (advisor outreach reads as distant when templated)
- Advisor agreements: after verbal commit, route FAST template to counsel (Project 10 linkage)
- Project 12 (financial modeling) should include advisor equity grants in dilution math

## Re-run trigger

[Specific condition — e.g., "gap matrix materially changes (hire, exit, pivot)" or "after advisor slots are filled, identify next-gap advisors" or "pre-Series A, re-assess gap matrix"]
```

No global write.

## What Not To Do

- Don't confuse advisors with investors — the posture, qualification, and comp frame are entirely different
- Don't generate names before the gap matrix is complete
- Don't target more than 2–3 gaps at once — advisor sprawl is a real failure mode
- Don't over-index on famous names — in-role operators often outperform
- Don't accept "they seem impressive" as gap-fit evidence — require specific expertise mapping
- Don't paper an advisor before a 30-minute call proves fit
- Don't over-grant equity — 1% per advisor is a cap-table disaster
- Don't draft full advisor agreements — FAST template + counsel review is the path
- Don't stack multiple advisors on the same gap redundantly
- Don't exceed 12 named prospects in the output
- Don't write to global context — this output stays project-scoped
- Don't template the first-ask outreach — founders should send these personally
- Don't skip the drama-risk check even when credentials are strong
- Don't let the founder substitute advisors for hires they actually need
