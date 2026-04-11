# Pre-Call Brief Template

This is an internal reference for the `pre-call-brief-builder` skill. It is the canonical structure for a pre-call brief, with content guidance per section and worked examples. **Do not show this document to the founder.** Use it to ensure every brief has the same shape and load-bearing sections.

---

## Why A Template Exists

Pre-call briefs are high-stakes, time-bounded artifacts. The founder reads them the night before the call (often) or the morning of (sometimes). They need to be scannable, complete, and ruthless about cutting out everything that isn't useful.

The template enforces:
1. **Consistent section order** — the founder's eye goes to the same place every time
2. **Sparse talking points, dense discovery questions** — enforcing the "validation not pitch" behavior structurally
3. **Explicit success definition** — the one section founders most want to skip
4. **Post-call update placeholder** — the bridge back to the pipeline tracker

---

## Section-By-Section Content Guide

### Section 1: Call Context

**Purpose:** Quick orientation. The founder scans this first and knows what they are walking into.

**Content:**
- Date and time with timezone (explicit, not ambiguous)
- Length in minutes
- Format (Zoom / phone / in-person)
- Call number in the relationship (1st, 2nd, 3rd...)
- Summary of prior touches pulled from `pipeline-tracker.md` (1–3 bullets)

**Content length:** ~5 bullet points or less

**Failure mode:** Leaving out the call number. The founder's approach to a 2nd call is different from a 1st call (more specific, more assumed context, more direct) and the brief should reflect that.

---

### Section 2: Company Snapshot

**Purpose:** Remind the founder what the company does and what's going on with them right now. This is the "I don't need to ask basic facts on the call" prep.

**Content:**
- 3–5 bullet points with citations
- What the company does (1 bullet)
- Size / stage / funding (1 bullet)
- What's happening right now — recent hires, recent funding, recent product launches, recent public statements (1–2 bullets)
- Competitor / tool stack signals from public sources (1 bullet if available)

**Content length:** 3–5 bullets; never more than 7

**Failure mode:** Inventing facts. Every bullet needs a citation. If the founder didn't approve a web search (or the search returned nothing), say so explicitly: "Web search not performed — bullets from the founder's prior knowledge only."

---

### Section 3: Role Context

**Purpose:** The prospect as an individual, not just an org chart position. What does THIS person do? What's their background? How long have they been in this role? What did they do before?

**Content:**
- 2–3 sentences
- Current role and approximate tenure
- Prior role / company (1 sentence)
- Anything specific from their public activity (LinkedIn posts, talks, articles)

**Content length:** 2–3 sentences maximum

**Failure mode:** Treating this section as "basic LinkedIn info" — that's the company snapshot. Role context should reveal something about the individual that makes them a real human, not just a title.

---

### Section 4: Inferred Pain (from ICP)

**Purpose:** Prime the founder with the pain points most likely relevant to this prospect. This is NOT the founder's product pitch — it's the founder's hypothesis about what the prospect is struggling with, grounded in the ICP's pain inventory.

**Content:**
- Top 3 pain points, ranked by likely relevance to this prospect
- Each cited to a specific section of `icp.md`
- Each connected to something specific about this prospect's context (company stage, role, recent signals)

**Content length:** 3 pain points, each 1–2 sentences

**Example:**

> 1. **Ramp time measurement gap** (from `icp.md` "Pain Inventory" section) — NorthStar just hired 8 SDRs, which means ramp time is actively top-of-mind; the fact that they're using [Competitor A] based on a G2 review suggests they have tooling but may be measuring the wrong metric.
> 2. **Content sprawl without outcome connection** (from `icp.md` "Pain Inventory") — Common pain for VP Enablement at 200-person SaaS; Sarah's LinkedIn post last week explicitly referenced this framing.
> 3. **Manager-enablement disconnect** (from `icp.md` "Pain Inventory") — Less directly evidenced but likely given company stage.

**Failure mode:** Inventing pain points not grounded in the ICP. Every pain needs a citation. If the ICP doesn't cover a pain the founder wants to name on the call, the ICP itself may need updating — but the brief is not the place to do that.

---

### Section 5: Top 3 Objections to Expect

**Purpose:** Prime the founder for the 3 objections most likely to come up in this call specifically. Not a generic list — calibrated to this prospect's role, stage, and context.

**Content:**
- 3 named objections
- Each linked to `objection-playbook.md` section if it exists
- Short recommendation to review the playbook entries before the call

**Content length:** 3 items, 1 line each

**Example:**

> 1. **"We're already using [Competitor A]"** — see `objection-playbook.md` > Competition > Objection 2
> 2. **"I'd need to talk to my VP Sales first"** — see `objection-playbook.md` > Authority > Objection 1
> 3. **"This isn't the right time — we're in Q1 planning"** — see `objection-playbook.md` > Timing > Objection 1
>
> **Recommendation:** Review these 3 playbook entries before the call.

**Failure mode:** Generic objection lists ("you'll probably hear the usual pricing/timing/trust stuff"). The whole point is to make the prep concrete.

---

### Section 6: Discovery Questions

**Purpose:** The heart of the brief. The questions the founder plans to ask, calibrated to the call length and covering multiple categories.

**Content:**
- Questions calibrated to call length (3 / 5–7 / 8–12)
- Organized by category (Pain Validation / Workaround Discovery / Willingness-to-Pay Signal / Buying Authority / Trigger Event)
- Each question drawn from or inspired by `discovery-question-bank.md`, customized to the specific prospect's context

**Content length:** Matches call length budget

**Failure mode:** Questions that sound like a survey, not a conversation. Good discovery questions feel natural in a conversation. Bad ones feel like the founder is reading from a script. The test: "Would I ask this question in a normal industry conversation?"

---

### Section 7: Talking Points

**Purpose:** The SMALL number of things the founder wants to make sure they say. Not a pitch. A few specific framings or claims to test.

**Content:**
- 1–3 talking points maximum
- Each is "the thing I want to make sure I say" — a specific framing, a distinction, a claim worth testing
- Each 1 sentence

**Content length:** 1 for 15-min, 2 for 30-min, 3 for 60-min

**Example:**

> 1. The distinction between "completion metrics" and "time-to-quota metrics" — I want to see if this framing lands with Sarah.
> 2. The 90-day-is-where-ramp-compounds observation — specifically relevant to her SDR hires.

**Failure mode:** Treating this as "pitch bullet points." If the founder wants 8 talking points, push back: that's a demo, not a discovery call.

---

### Section 8: What Success Looks Like

**Purpose:** Force the founder to articulate what they are trying to LEARN from this call, not what they are trying to SELL. The most important section in the brief.

**Content:**
- 1–3 specific learning outcomes
- Explicit "this call is NOT about closing" reminder
- Optional: the fallback success criterion if the primary one is not reachable

**Content length:** 3–5 lines

**Example:**

> - Leave the call knowing whether "time-to-quota" or a different metric is what Sarah actually cares about
> - Leave the call knowing who else at NorthStar would need to be involved in a tool decision
> - Leave the call knowing whether NorthStar has a budget for this in the next 6 months
>
> **This call is NOT about:** closing a deal, signing a contract, or getting Sarah to commit to a trial. It is about learning whether the pain is real and how Sarah describes it.

**Failure mode:** Founder wants to write "I want Sarah to sign up for the pilot." Push back: at this stage, the learning is more valuable than the commitment. If Sarah explicitly asks to sign up, great — but that is a bonus, not the goal.

---

### Section 9: Post-Call Update

**Purpose:** Placeholder the founder fills in after the call. Becomes input to `pipeline-tracker-manager` on the next update run.

**Content:**
- Stage transition placeholder
- "What was learned" bullet list placeholder
- "Quotes to remember" placeholder (feeds ICP refinement)
- "Objections encountered" placeholder (feeds objection-playbook updates)
- Next action placeholder

**Content length:** ~5 bullets, all empty until the founder fills them in

**Failure mode:** Skipping this section entirely. It is the bridge back to the operational workflow and the feedback loop that sharpens every other skill in the project.

---

## Worked Example (30-minute call)

```markdown
---
prospect_slug: sarah-chen-northstar
prospect_name: Sarah Chen
prospect_company: NorthStar SaaS
call_date: 2026-04-15
call_time: 10:00 PT
call_length_minutes: 30
call_format: zoom
call_number: 1st
status: pre-call
---

# Pre-Call Brief — Sarah Chen at NorthStar SaaS — 2026-04-15

## Call Context
- **Date/time:** April 15, 2026, 10:00 PT
- **Length:** 30 minutes
- **Format:** Zoom
- **Number:** 1st call with Sarah
- **Prior touches:** Initial cold email sent 4/3 referencing her LinkedIn post on ramp-time-as-content-problem; follow-up 1 sent 4/8 with a new angle on time-to-quota measurement; Sarah replied 4/10 saying "this is a real problem for us right now, happy to chat"

## Company Snapshot
- NorthStar SaaS — B2B sales enablement platform for mid-market (212 employees, Series B, San Francisco) [LinkedIn company page, Crunchbase]
- Hired 8 new SDRs in the last 60 days [Sarah's LinkedIn post 3/28]
- Recently launched "playbook library" feature [NorthStar blog 3/15]
- Appears to use [Competitor A] internally based on G2 review from 4 months ago [G2 review page]

## Role Context
Sarah has been VP of Sales Enablement at NorthStar for 8 months. Prior role was Director of Enablement at a 400-person SaaS company. Active on LinkedIn with 2–3 posts per week, specifically focused on measuring enablement outcomes (not just activity).

## Inferred Pain (from ICP)
1. **Ramp time measurement gap** — NorthStar just hired 8 SDRs, so ramp is actively top-of-mind. Her LinkedIn activity suggests she already frames it as a measurement problem, not a content problem.
2. **Content sprawl without outcome connection** — Common pain for VP Enablement at this scale; Sarah's post last week explicitly named this framing.
3. **Manager-enablement disconnect** — Likely given company stage but less directly evidenced.

## Top 3 Objections to Expect
1. **"We're already using [Competitor A]"** — see `objection-playbook.md` > Competition > Objection 2
2. **"I'd need to talk to my VP Sales first"** — see `objection-playbook.md` > Authority > Objection 1
3. **"This isn't the right time — we're in Q2 planning"** — see `objection-playbook.md` > Timing > Objection 1

**Recommendation:** Review these 3 playbook entries before the call.

## Discovery Questions

### Pain Validation
1. "Walk me through the last time you had a new SDR start — what does their first 90 days actually look like today?"
2. "When you think about your current enablement setup, what's the thing that frustrates you most?"

### Workaround Discovery
3. "How are you measuring whether your onboarding program is working right now?"

### Willingness-to-Pay Signal
4. "If you could snap your fingers and have one thing change about how new reps ramp at NorthStar, what would it be?"

### Buying Authority
5. "When you evaluate a new tool in this space, walk me through who's typically involved in that decision at NorthStar."

### Trigger Event
6. "You mentioned this is a real problem 'right now' — what made it urgent this month?"

## Talking Points (use sparingly)
1. The "completion metrics vs time-to-quota" distinction — I want to see if this framing lands with her specifically.
2. The 90-day-is-where-ramp-compounds observation, directly tied to her SDR hires.

## What Success Looks Like
- Leave the call knowing whether "time-to-quota" or a different metric is what Sarah actually cares about
- Leave the call knowing who else at NorthStar would need to be involved in a tool decision
- Leave the call knowing whether she sees enough pain to have a second conversation

**This call is NOT about:** closing a deal, signing a contract, or getting Sarah to commit to a pilot. It is about learning whether the pain is real and how Sarah describes it.

---

## Post-Call Update

- **Stage transition:** [from Meeting Scheduled to ?]
- **What was learned:** [fill in]
- **Quotes to remember:** [fill in]
- **Objections encountered:** [fill in]
- **Next action:** [fill in]
```

This example is dense and concrete. Every section has specific, citable content. The brief could be scanned in 2 minutes the night before the call.
