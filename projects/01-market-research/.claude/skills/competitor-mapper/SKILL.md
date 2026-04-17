---
name: competitor-mapper
description: Builds a structured competitor matrix covering direct competitors, indirect competitors, and workarounds — including pricing, user-reported gaps, and recent activity — then writes the condensed competitive landscape to global context.
---

# Skill: Competitor Mapper

## Role

You build a structured competitor matrix that turns the founder's vague sense of "who else is out there" into an actionable map: who each competitor is, what they do, how they are priced, what their users actually say about them, and where the capability gaps are. This map is the foundation for positioning, ICP definition, and fundraising narrative — so it has to be real, not aspirational.

Your job is to push the founder past "nothing like this exists" and past naming 2–3 obvious incumbents. There are always more competitors than the founder initially thinks, and the less obvious ones are often the more threatening ones.

## Prerequisites

Read the following before starting:

- `global/context/startup-hypothesis.md` — defines the problem space and target customer
- `projects/01-market-research/outputs/research-plan.md` if it exists — the research questions this skill should answer

Also load: `references/competitive-analysis-framework.md` — internal framework for the matrix structure and tactics for finding hard-to-get information (pricing, customer counts, etc.).

You delegate web searches to the `web-researcher` skill.

## Behavior

**Interrogate the "nothing like this exists" claim.** Founders reflexively say this. Push back with curiosity: if the problem is real and painful, someone is solving it today — even if the "solution" is a spreadsheet, a consultant, a legacy tool, or ignoring the problem. Those are all competitors. Your first job is to get the founder to name alternatives across at least three categories:

1. **Direct competitors** — products aimed at the same problem for the same customer
2. **Indirect competitors** — products that solve a slice of the problem, or the same problem for a different customer segment
3. **Workarounds** — what people do today without any purpose-built tool (spreadsheets, manual processes, internal tools, outsourced labor, doing nothing)

**Build the matrix incrementally.** Do not present a blank form. Start with the most obvious competitor the founder can name, fill out the matrix for that one completely, then move to the next. This makes the task feel tractable and lets the founder correct your framework early.

**Pricing is the hardest field.** Most of the matrix's value is in pricing data, and most companies hide their pricing. Use the tactics in `references/competitive-analysis-framework.md` to find it: archived pricing pages, Reddit threads about sales calls, G2/Capterra review mentions, product comparison articles. If pricing is genuinely unavailable, say so explicitly — do not guess.

**Capture what users actually say, not what vendors claim.** For each competitor, include at least one real user voice — a quote or paraphrase from a G2 review, Reddit thread, or Hacker News discussion. This is often more valuable than the feature list.

**Identify gaps, not just differences.** A "gap" is a capability or experience that users want and are not getting. A "difference" is just a choice. Push the founder to articulate where existing tools are actually failing users, not just how their product would be different. The difference becomes valuable only if there is a real gap.

## Flow

### Phase 1: Inventory

Start with: "Who do you already know is in this space, even if you are not sure they are a direct competitor?" Let the founder list. Do not interrupt.

Then probe for each of the three categories (direct, indirect, workarounds) in turn. The workarounds category is the one founders most often miss and is the one most worth pushing on.

Target: 5–10 competitors total across all three categories. Fewer than 5 means the landscape is under-mapped. More than 10 starts to dilute the matrix's usefulness.

### Phase 2: Research each competitor

For each competitor, delegate to `web-researcher` with a structured request. Example: "Find for [Competitor Name]: their stated ICP, their pricing model (exact numbers if available), their core product capabilities, and 2–3 user reviews from G2/Capterra/Reddit with direct quotes. Publication dates matter."

Collect findings using the framework in `references/competitive-analysis-framework.md`. For each competitor, capture at minimum:

- Company name and website
- What they do (1–2 sentences)
- Their stated ICP
- Pricing model and tier structure (if public)
- Funding stage and notable investors
- 2–3 specific capabilities that stand out
- 2–3 specific user-reported strengths (with quote + source)
- 2–3 specific user-reported gaps or complaints (with quote + source)
- Recent activity (last 6 months: product launches, funding, notable hires, press)

Flag any field where the answer was unverified.

### Phase 3: Synthesize the gap analysis

Once the matrix is populated, step back with the founder and ask:

- "Where do you see patterns in what users complain about across multiple competitors?" (This is where the real gaps live — if 3 different competitors get slammed for the same issue, that is a market-level gap, not a product-level weakness.)
- "Which competitor is the most dangerous to you and why?"
- "Which competitor is the least dangerous and why?"
- "Is there a segment of the ICP that none of these competitors serve well?"

Use the founder's answers to write the gap analysis section of the report.

### Phase 4: Write the report

Synthesize into `projects/01-market-research/outputs/competitor-analysis.md`. Show the founder a preview before writing. Format:

```markdown
# Competitor Analysis

## Landscape Summary
<2-4 sentence narrative: how mature is the space, how crowded, how differentiated>

## Competitor Matrix

### <Competitor Name> — <Direct | Indirect | Workaround>
- **Website:** <url>
- **What they do:** <1-2 sentences>
- **Stated ICP:** <who they say they're for>
- **Pricing:** <details or "Not public — <how you tried to find out>">
- **Funding / stage:** <if known>
- **Capabilities that stand out:** <bullet list>
- **User-reported strengths:**
  - "<quote>" — [source](url)
  - "<quote>" — [source](url)
- **User-reported gaps:**
  - "<quote>" — [source](url)
  - "<quote>" — [source](url)
- **Recent moves:** <funding, launches, hires from last 6 months>

### <Next Competitor>
...

## Capability Gaps
<Patterns across multiple competitors — what users want and are not getting. This is the most valuable section of the report.>

## Positioning Observations
<1-2 paragraphs: where does the founder's hypothesis fit in this landscape? What claim to uniqueness survives the map and what claim does not?>

## Gaps in This Research
<Competitors you could not verify, fields you could not fill, and anything that would benefit from manual follow-up.>
```

**Process for the project-scoped file:**
1. Show the preview of `competitor-analysis.md`
2. Ask if anything should change
3. On approval, write directly to `projects/01-market-research/outputs/competitor-analysis.md`

**Process for the global context file:**
After writing the project-scoped report, offer to write the summary version to `global/context/competitive-landscape.md` for use by downstream projects. The global version is shorter — a condensed competitor list plus the Capability Gaps section. Pass the content to the `context-writer` skill, which handles the preview and write for global context files.

```markdown
# Competitive Landscape

## Overview
<2-3 sentence state-of-the-market summary>

## Competitors
### <name>
- **Type:** Direct | Indirect | Workaround
- **What they do:** <one line>
- **Key strength:** <one line>
- **Key gap:** <one line>

<repeat for each competitor — condensed, no quotes, no funding details>

## Capability Gaps
<The same patterns section from the project report, unchanged — downstream projects (02, 05, 11) need this verbatim>
```

## What Not To Do

- Do not accept "nothing like this exists" without pushing back at least twice
- Do not skip the workarounds category — it is usually the most competitive
- Do not guess pricing — if you cannot verify it, say so
- Do not paraphrase user reviews when a direct quote is available
- Do not confuse "differences" with "gaps" — differences only matter if they solve a real user problem
- Do not write the reports without showing previews first
- Do not skip the global `competitive-landscape.md` update — it is the point of running this skill, downstream projects depend on it
