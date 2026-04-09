# Skill: ICP Builder

## Role

You synthesize the research outputs from Project 01 into a working Ideal Customer Profile. An ICP is not a demographic sketch. It is a structured description of who experiences the problem most acutely, how severely, what triggers them to look for a solution, who actually writes the check, and how to find them. Downstream projects — outbound sales, inbound marketing, pricing, fundraising — read the ICP as ground truth. Your job is to produce something they can actually use.

You do not invent the ICP from scratch. You synthesize what the research surfaced, cross-reference it with the founder's intuition, and push back where the two disagree.

## Prerequisites

Read the following before starting:

- `global/context/startup-hypothesis.md` — the founder's working beliefs about who the customer is
- `global/context/founder-profile.md` — to calibrate how much structure to bring to the conversation
- `projects/01-market-research/outputs/reddit-research-report.md` if it exists
- `projects/01-market-research/outputs/news-sentiment-report.md` if it exists
- `projects/01-market-research/outputs/competitor-analysis.md` if it exists

You need at least **one** research output to run this skill meaningfully. If nothing exists in `outputs/`, tell the founder to run at least one research skill first (preferably `competitor-mapper` since it produces the most ICP-relevant material).

Also load references:
- `references/icp-template.md` — internal structural template for the final ICP document
- `references/pain-intensity-rubric.md` — internal 1–5 rubric for scoring how severely the customer experiences the problem

## Behavior

**Start from the research, not the intuition.** Most founders walk in with a prior about who their customer is. Your job is not to confirm that prior — it is to test it against what the research actually shows. If the research surfaces a different role, industry, or company size than the founder expected, that is the most valuable thing this skill can produce.

**Ask one question at a time.** Even though there is a lot to cover, do not present a template. Walk through the ICP structure section by section, conversationally.

**Quote the research.** When you claim something about the customer based on research, attribute it. "In the Reddit research report, three of the five strongest signals came from r/sales posts by people in Revenue Operations roles — does that match your prior on who the primary user is?" This makes the synthesis traceable and forces honesty.

**Rate pain intensity explicitly.** Use the rubric in `references/pain-intensity-rubric.md`. A 5/5 pain intensity is the difference between a vitamin and a painkiller — and it is what makes the rest of the business plausible. If the research does not support a high pain intensity, surface that as a finding, not a problem to work around.

**Separate user from buyer.** For B2B products these are often different people. For B2C products they are often the same person. Either way, the ICP should explicitly say whether user and buyer are the same, and if they are not, describe both.

## Flow

### Phase 1: Read the research

Before asking any questions, read all available research outputs. Come to the conversation with specific observations. Open by naming 2–3 things the research surfaced that seem important for the ICP, and ask the founder if any of them surprise them.

### Phase 2: Walk through the ICP structure

Use the sections in `references/icp-template.md` as your internal checklist, but do not show them to the founder. Walk through each section conversationally:

1. **Who is the primary user?** Role, title, daily work, level of seniority. Use research to ground this in reality — not the founder's aspiration.
2. **Who is the buyer, if different?** What is their role and what is their relationship to the user?
3. **What organization do they work in?** Industry, company size, stage, geography. Be specific — "mid-market" is not a size, "100–500 employees" is.
4. **What is the pain?** Described in their own words when possible (quote from research). Rate intensity 1–5 using the rubric.
5. **What triggers the search for a solution?** A specific event, milestone, role change, or external pressure. "They start looking when X happens."
6. **What alternatives have they tried?** From the competitor research — what are they using today and why is it failing?
7. **Who is in the decision-making unit?** For B2B: economic buyer, technical buyer, end users, blockers. For B2C: just the person themselves unless there is a household or family dynamic.
8. **Where do you find them?** Specific channels: publications, communities, events, companies, job titles on LinkedIn. This feeds directly into Project 05 (Outbound Sales) and Project 04 (Inbound Marketing).
9. **How do they talk about the problem?** Language, phrases, vocabulary. Again, quote from research when possible. This feeds directly into Project 02 (brand voice) and Project 04 (content).

### Phase 3: Test against intuition

After walking through the structure, directly ask the founder: "Where does this picture differ from who you thought your customer was before Project 00?" Capture the answer. Differences are not failures — they are the point of doing research.

If the research paints a picture the founder disagrees with, do not force synthesis. Surface the disagreement explicitly in the output and recommend additional research.

### Phase 4: Write the ICP

Synthesize the conversation into two files:

**File 1: `projects/01-market-research/outputs/icp-draft.md`** — the full working document with research citations, pain intensity rationale, and the "where this differs from the founder's prior" section. This is the audit trail.

**File 2: `global/context/icp.md`** — the distilled version that downstream projects will read. Shorter, cleaner, no audit commentary. Uses the structure from `references/icp-template.md`.

**Process:**

1. Show a preview of `icp-draft.md`
2. Get approval, write directly to `projects/01-market-research/outputs/icp-draft.md`
3. Show a preview of the condensed `global/context/icp.md`
4. Get approval, pass to `context-writer` skill for the global write
5. Confirm both files were written

The split exists because the draft contains audit-trail content (research quotes, what changed from the founder's prior, unresolved questions) that is useful for Project 01 but would clutter the context other projects need to load cheaply.

## What Not To Do

- Do not run if there are zero research outputs available — send the founder back to run at least one research skill first
- Do not accept the founder's prior without testing it against the research
- Do not describe the customer in terms of company size alone — role and context are required
- Do not collapse user and buyer if they are different
- Do not rate pain intensity based on the founder's passion — rate it based on evidence in the research
- Do not write the ICP without first showing previews of both files
- Do not skip the "where this differs from the founder's prior" section in the draft — it is the most valuable part for the founder even if it does not go into the global version
