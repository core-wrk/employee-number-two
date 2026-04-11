# Lead Qualification Rubric

This is an internal reference for the `prospect-researcher` skill. It is the A/B/C/D tier rubric used to qualify every outbound prospect against the ICP, with worked examples calibrated to the example ICP (VP Sales Enablement at 100–500 person B2B SaaS companies). **Do not show this document to the founder.** Use it to make tier judgments consistent across runs and to push back when the founder wants to over-qualify or under-qualify a prospect.

---

## Why The Tiers Matter

The tier is the load-bearing judgment in `prospect-list.md`. It determines which prospects the founder prioritizes this week, which ones flow into `email-drafter` next, and which ones `pipeline-tracker-manager` flags as stuck if they sit without movement.

This rubric **matches the A/B/C/D rubric used by `waitlist-manager`** on purpose — Project 08's eventual `beta-recruiter` will read both `waitlist-tracker.md` and `pipeline-tracker.md` and should apply the same tiering logic across both. Keep the rubrics aligned. If you need to change one, change the other (and update both sets of dev notes).

The important difference between outbound prospects and waitlist signups: waitlist signups self-select (they signed up because something resonated), so the baseline fit is already slightly elevated. Outbound prospects have not opted in — they are cold. That means the bar for Tier A is actually **higher** for outbound than for waitlist, because the only reason to spend a founder's 45 minutes per prospect on research and outreach is that the match is confident.

---

## The Four Tiers

### Tier A — Exact ICP Match, Confident

**Definition:** Every key ICP attribute matches and there is at least one observable buying trigger. This is a prospect worth a 45-minute personalized outreach investment.

**Required matches against `icp.md`:**
- **Role:** Exactly matches the buyer role named in the ICP (or a clear synonym — "VP Enablement" matches "VP Sales Enablement"; "Director of Revenue Operations" matches "Director of RevOps")
- **Company size:** Within the named employee-count range
- **Industry/vertical:** Matches the ICP's named verticals
- **Geography:** Matches (or the ICP does not specify geography)
- **At least one observable buying trigger:** Recent funding, recent related hire (SDRs, AEs, RevOps), public statement about the problem, competitor churn signal, job posting that names the problem, or a team page that shows recent growth in the relevant function

**Operational meaning:** First-priority for outreach. `email-drafter` should produce an initial touch within the week. `pipeline-tracker-manager` starts them in the Prospecting stage.

**Worked example:**
> Sarah Chen, VP of Sales Enablement at NorthStar SaaS (212 employees, B2B SaaS, San Francisco). LinkedIn profile confirms role and tenure (joined 8 months ago). NorthStar's LinkedIn page shows they hired 8 new SDRs in the last 60 days. NorthStar uses [Competitor A] based on a G2 review from 4 months ago.
>
> **Tier: A**
> **Why:** Role matches exactly. Company size matches (212, in range). Industry matches (B2B SaaS). Explicit buying trigger (recent SDR hiring surge). Bonus signal: currently using a competitor, meaning they have an active budget for tools in this category.
> **Next Action:** Draft initial outreach via `email-drafter`.

---

### Tier B — Adjacent Fit

**Definition:** Most ICP attributes match but one or two are off, or the buying trigger is missing. Worth prospecting but not top priority.

**Common patterns:**
- Right role, wrong company size (Director of Sales Enablement at a 700-person company — adjacent to mid-market but technically enterprise)
- Right industry, adjacent role (Head of RevOps at a B2B SaaS company — touches the enablement function but is not the named buyer)
- Right size and industry, right role, no observable buying trigger (the prospect looks perfect on paper but there is no signal that something is making them shop right now)
- Right buyer, wrong geography (the ICP specifies US primary; the prospect is in Canada or Western Europe)

**Operational meaning:** Second-priority for outreach. Draft outreach after the Tier A queue is clear, or use a lighter-touch opening (LinkedIn DM rather than full personalized email) to test interest.

**Worked example:**
> Marcus Rivera, Director of RevOps at GrowthCo (340 employees, B2B SaaS, Austin). LinkedIn profile confirms role. No recent funding or hiring surge visible. GrowthCo's stack is not publicly known.
>
> **Tier: B**
> **Why:** Adjacent role (RevOps is a technical buyer or influencer, not the VP Sales Enablement economic buyer). Company size matches. Industry matches. No observable buying trigger.
> **Next Action:** Draft a lighter-touch LinkedIn DM rather than a full email — aim to open a conversation, not close a meeting.

---

### Tier C — Plausible But Stretched

**Definition:** One or two ICP attributes are off in ways that materially matter (wrong seniority, wrong stage, adjacent vertical). Worth tracking but not the primary focus of outreach.

**Common patterns:**
- Right role at a much smaller or much larger company (VP Sales Enablement at a 4,500-person enterprise, or at a 40-person seed-stage startup — the tool fit changes substantially at those scales)
- Adjacent industry (B2B services rather than SaaS — partially relevant but the buying patterns are different)
- Right industry, lower seniority (Sales Enablement Manager instead of VP/Director — influencer, not decision-maker)
- Founder or CEO at a small/mid B2B SaaS company where there is no VP Sales Enablement yet and the founder themselves is playing that role

**Operational meaning:** Not priority outreach. Add to the list so the founder has visibility, but do not spend 45 minutes per prospect on personalized drafting. If the founder wants to reach out, use a short, curious LinkedIn DM — "I noticed you're running X without a head of enablement, is that deliberate?"

**Worked example:**
> Jamie Park, Sales Enablement Manager at MegaCorp (4,800 employees, enterprise software, Seattle).
>
> **Tier: C**
> **Why:** Role is enablement-adjacent but seniority is below VP/Director. Company size is way out of the mid-market range — enterprise buying motion is different from mid-market and the product may not fit.
> **Next Action:** Hold — re-evaluate if context changes (Jamie changes roles, or enterprise becomes a future ICP segment).

---

### Tier D — Out Of ICP, Do Not Pursue

**Definition:** Wrong in ways that make the prospect not worth contacting. On the list only because the founder asked about them or because they surfaced during sourcing and needed to be evaluated.

**Common patterns:**
- Employees of companies named in `competitive-landscape.md` as competitors
- Job seekers and students ("looking for a role in sales enablement")
- Investors, analysts, or journalists (not buyers, though they might refer — track them separately if useful)
- Way out of the role (HR Manager at a manufacturing company — no realistic path to buyer)
- The founder's own team members (obviously out of scope)

**Operational meaning:** Keep in the tracker for record-keeping (so the founder does not re-research the same person later) but never draft outreach. Tier D prospects should not appear in any outreach queue.

**Worked example:**
> Alex Thompson, Content Marketing Manager at ContentCraft Inc (120 employees, marketing agency, New York).
>
> **Tier: D**
> **Why:** Wrong role entirely (content marketing is not the enablement buyer). Wrong industry (services, not SaaS). No path to fit.
> **Next Action:** None. Keep in tracker for completeness; do not re-research.

---

## Edge Cases And How To Handle Them

### Case 1: The role matches but the title is different

The ICP says "VP Sales Enablement" and the prospect's title is "Head of Revenue Enablement." Same job, different title. **Tier A.** Use the substance of the role, not the literal string. Note the title variation.

### Case 2: Company size is just above or below the range

The ICP says "100–500 employees" and the prospect's company has 550. **Tier B**, with a note. If the company is contracting (recent layoffs) or the buyer explicitly references mid-market messaging, flag and ask the founder if they want to promote to Tier A.

### Case 3: The prospect looks perfect but you cannot find an observable buying trigger

Right role, right company, right size, right industry, but nothing is publicly visible that suggests they are shopping right now. **Tier B, not Tier A.** The trigger matters — prospects without a trigger convert 3–5x worse on cold outreach. Tell the founder this explicitly.

### Case 4: The prospect is at a company using a named competitor

This is usually a **positive signal**, not a disqualifier — the company has a budget in the category and is evaluating tools. **Tier A if everything else matches.** Note the competitor in the Notes field so `email-drafter` can reference it (carefully — never attack the competitor, just acknowledge the category).

### Case 5: The prospect is the founder's existing network

Prior colleague, prior customer, friend-of-friend, someone the founder met at a conference. **Tier the prospect on their current role and company, not on the personal relationship.** If they are a Tier A by the rubric, they are a Tier A. If they are a Tier C, they are a Tier C — but the note should capture the relationship, because the outreach will be different (warm intro rather than cold email).

### Case 6: The prospect is a company with no publicly named individual

The founder identifies a target company but you cannot find the right named person. **Do not add a row yet.** Add the company to the "prospects to enrich" section of the file with a note: "Need to identify the right VP Sales Enablement at [Company] — try LinkedIn Sales Navigator or the company's team page." The founder may also have a relationship that lets them find the right name.

### Case 7: Multiple candidates at the same company

Two or three people at the same company fit the ICP in slightly different ways (VP Sales, VP Sales Enablement, Director of RevOps). Add each as a separate row. Mark one as the primary outreach target and the others as backup or secondary. **Do not outreach to multiple contacts at the same company simultaneously** — that looks like spray-and-pray. The primary-secondary structure lets the founder fall back if the primary does not reply.

### Case 8: The "founder" or "CEO" of a small company

If the company is in the ICP's size range, the founder/CEO may be the economic buyer even if there is no VP of Enablement yet. **Tier B by default** with a note. If the company is under 50 employees, Tier C — too early for the product, and the founder/CEO is too busy fundraising to buy.

---

## How To Push Back On The Founder's Tier Judgments

The founder will often want to over-qualify Tier A because they are excited. Push back when:

- The role is wrong but the founder wants to rationalize it ("but they're influential at their company")
- There is no buying trigger ("but they'd be a great fit if they knew about us")
- The company is just outside the size range and the founder wants to stretch
- The prospect is a prior colleague and the founder is conflating personal rapport with fit

The founder will also sometimes under-qualify Tier A out of self-doubt. Push back when:

- The prospect is a strong fit and the founder says "they're too senior, they won't read a cold email"
- The founder is afraid of sending to a real Tier A ("what if I waste my shot?")

The rubric is the tie-breaker. Apply it consistently, and surface the disagreement explicitly when it happens so the founder knows why you are tiering differently than they would.
