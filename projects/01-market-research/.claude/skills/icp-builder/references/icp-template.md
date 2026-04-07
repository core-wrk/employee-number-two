# ICP Template

This is an internal reference for the `icp-builder` skill. It defines the structure of the ICP document and the content expected in each section. **Do not show this document to the founder.** Use it to scaffold the synthesis and ensure every section is filled.

---

## Structure of `global/context/icp.md`

The final file that goes into global context uses this structure. Keep each section tight — the whole file should be readable in under 5 minutes by a downstream skill that loads it as context.

```markdown
# Ideal Customer Profile

## Summary
<2-3 sentence description of the ICP. Role + context + core pain. This is what a downstream skill reads first.>

## Primary User
- **Role / title:** <specific title, not category>
- **Seniority:** <IC / manager / director / VP / C-suite>
- **Daily work:** <what they actually do day-to-day — not what their job description says>
- **Tools they already use:** <the stack they work inside>

## Buyer (if different from user)
- **Role:** <who writes the check>
- **Relationship to user:** <how the user and buyer interact; who influences whom>
- **What they care about:** <the criteria the buyer uses to evaluate purchases>

## Organization
- **Industry / vertical:** <specific>
- **Size:** <employee count range, revenue range if relevant>
- **Stage / maturity:** <startup / growth / enterprise>
- **Geography:** <where they're located or where they operate>

## The Pain
<2-4 sentence description of the pain, quoted from research where possible. Name the specific situation where the pain occurs and how often.>

**Pain intensity: <1-5>**
<One-sentence justification referencing the pain-intensity-rubric.md>

## Buying Triggers
<Specific events or milestones that make them start looking for a solution. Examples: new hire in a role, regulatory deadline, hitting a scale threshold, failing an audit.>

## Current Alternatives
<What they use today to cope with the pain. Reference `global/context/competitive-landscape.md` for the full matrix — this section is a 1-paragraph summary of what the customer specifically uses.>

## Decision-Making Unit
For B2B:
- **Economic buyer:** <who approves the budget>
- **Technical buyer:** <who evaluates feasibility and fit>
- **End users:** <who actually uses it day-to-day>
- **Blockers:** <who can say no even without official veto — often security, procurement, legal>

For B2C:
- Usually just the individual; call out any household, family, or peer influence if relevant.

## Where to Find Them
- **Communities:** <specific subreddits, Slack groups, Discord servers, LinkedIn groups>
- **Publications:** <what they read>
- **Events:** <conferences, meetups>
- **Job titles for outbound:** <3-5 specific titles to use in prospect searches>
- **Companies (if relevant):** <named companies that represent the ICP>

## How They Talk About the Problem
<5-10 phrases the target customer actually uses, pulled from Reddit/G2/forum research. These feed brand voice and content.>

## Unresolved Questions
<Anything still unknown that additional research would clarify. Keep short.>
```

---

## Structure of `projects/01-market-research/outputs/icp-draft.md`

The draft version has everything the global version has, plus:

### Additional section: Research Trail
For each major claim in the ICP, cite the research finding that supports it. Example:

```markdown
## Research Trail

- **Pain intensity rated 4/5:** Supported by 3 strong signals in reddit-research-report.md (r/sales threads dated within last 6 months, quote: "..."), cross-referenced with 2 user-reported complaints in competitor-analysis.md (Lessonly reviews on G2).
- **Primary user identified as RevOps rather than Sales Manager:** Differs from founder's original hypothesis. Supported by: 5 of 7 strong signals came from posts self-identified as RevOps; in competitor-analysis, the clearest capability gaps were articulated by RevOps roles, not sales managers.
- **Pricing sensitivity at $500/seat/month ceiling:** From competitor-analysis — Mindtickle and Lessonly both had complaints about price above this threshold in G2 reviews.
```

### Additional section: What Changed From the Founder's Prior
One paragraph per change:

```markdown
## What Changed From the Founder's Prior

**Primary user shifted from "Sales Manager" to "VP of RevOps."**
The original hypothesis assumed the user would be a line-level sales manager, and the buyer would be a VP of Sales. Research showed that sales managers rarely complain publicly about this problem in the ways that suggest they are actively looking for a tool. The roles that do are in RevOps, where the pain is measurable (ramp time as a KPI) and the budget is discretionary. The founder agreed this matches what they have seen in their own network.

**Pain intensity lower than assumed (4/5 rather than 5/5).**
The founder expected this to be a "hair on fire" problem. Research showed it is real and painful but rarely described with the urgency of a 5/5. Most companies are coping with workarounds, not actively shopping. This has implications for sales cycle length and trigger events.

...
```

This section is the most valuable part of `icp-draft.md` for the founder's own learning. Even though it does not propagate to downstream projects, it is what makes Project 01 worth running.

---

## Rules for Synthesis

- **Do not invent specificity.** If the research does not name a specific industry, say "various B2B SaaS" — do not guess "mid-market fintech" to make the ICP feel sharper than it is.
- **Quote research verbatim when it is strong.** A direct quote from a Reddit post or G2 review is more valuable than a paraphrase.
- **Distinguish evidence strength.** Claims backed by multiple Strong-rated findings should be stated confidently. Claims backed by a single Moderate finding should be hedged ("likely," "appears to," "suggests").
- **Resist making the ICP too broad.** "Mid-market SaaS companies" is not an ICP. "VP of RevOps at mid-market SaaS companies (100–500 employees) in the US who are measuring time-to-productivity for new sales hires" is an ICP.
- **Resist making the ICP too narrow.** If the research only supports a specific customer profile, commit to it. If the founder wants to serve "both SMB and enterprise," the research rarely supports both — pick the one the research supports and note the other as an expansion opportunity.
