# Pipeline Hygiene Rules

This is an internal reference for the `pipeline-tracker-manager` skill. It captures the operational rules for keeping the pipeline tracker healthy: when to mark stalled vs lost, how to handle silent prospects, when to revive, how to run the weekly review, and what a "healthy" pipeline looks like at this stage. **Do not show this document to the founder.** Use it to guide operational discipline without dictating — the founder always has the final call.

---

## The Core Hygiene Principle

A healthy tracker is not a big one. It is a **current** one. A pipeline with 15 prospects, all in active stages with fresh `Last Touch` dates, is healthier than a pipeline with 150 prospects where 80% are stale.

The whole point of the pipeline tracker is operational: it tells the founder what to do next. A bloated tracker obscures the signal. Ruthless hygiene (moving stalled prospects to Stalled, moving Lost prospects to Lost, not pretending a prospect is still in play when they aren't) is what keeps the signal visible.

**Rule of thumb:** If the founder cannot name what they are going to do for every prospect in the tracker next week, the tracker is too big or too stale.

---

## Stalled vs. Lost: The Decision Rule

These two terminal-ish states are often confused. The rule:

- **Stalled** = "Maybe later, but not now." The prospect went silent, but the fit might still be real. A revival touch in 4–6 weeks might work.
- **Lost** = "Not them, at least not in this context." The prospect explicitly declined, was disqualified on a call, or sits at a company that is wrong for the ICP in ways that won't change soon.

**The decision test:** If the founder is willing to try again in 2 months, it's Stalled. If the founder is not willing to try again, it's Lost.

### When to Stall (not Lost)

- Prospect went silent after a cold outreach but never explicitly declined
- Prospect replied warmly but went silent when it came time to book a meeting (they may be busy, not uninterested)
- Prospect had a meeting but said "we're not ready yet, check back in Q3"
- Prospect is a Tier A but the timing is wrong

### When to Lose (not Stall)

- Prospect explicitly said "no" or "not interested" or "we don't need this"
- A call revealed that the fit is wrong (wrong company size, wrong seniority, wrong buyer)
- The prospect replied but the reply was a disqualifier ("we already have a 5-year contract with [Competitor]")
- The prospect's LinkedIn profile shows they left the company — the person is no longer reachable in this role; they might be reachable in a new role later, which would be a fresh Prospecting entry
- The prospect is at a company named in `competitive-landscape.md` and the founder confirms they don't want to continue

### Edge Case: The No-Show

If a prospect books a meeting and no-shows, give them one chance. Send a polite "missed you, want to reschedule?" message. If they reschedule, stay in Meeting Scheduled. If they no-show again or don't reply to the reschedule, move to Stalled — not Lost — because the silence might just mean their week exploded, not that they are uninterested.

---

## The 14-Day Rule and Why It Matters

The pipeline tracker flags any prospect that has been in the same stage for 14+ days without a `Last Touch` update. This is not arbitrary — it is the decay window for cold outreach warmth.

**What happens after 14 days:**
- Cold outreach goes stale. If the prospect hasn't replied in 14 days, they probably aren't going to — a follow-up is the right move.
- Warmer stages (Replied, Meeting Scheduled) lose momentum. A prospect who replied 2 weeks ago and hasn't heard from the founder since is reverting to "cold."
- The founder loses context. Two weeks in, the founder has forgotten the details of the prospect; re-entering the conversation requires re-research.

**The 14-day rule is not about time-in-stage.** A prospect in Design Partner Conversation for 3 weeks is fine if there have been touches along the way. The rule is about **time since last touch**. No touch = no momentum = flag it.

### Response Patterns When Flagged

When the tracker surfaces a stuck prospect, the founder has four options:

1. **Send a follow-up touch** — the most common response. Run `email-drafter` with `sequence_position=follow-up-1` or `follow-up-2` depending on how many touches have already gone out.
2. **Send a "bump" via a different channel** — if the founder has only tried email, try LinkedIn DM (or vice versa). Different channel, same message.
3. **Move to Stalled** — if the founder has already sent 2+ touches with no reply, Stalled is the right call. Stop pretending it's an active prospect.
4. **Move to Lost** — if the founder is sure this one isn't coming back.

**What not to do:** Silently let the stuck prospect sit. That is what makes trackers rot.

---

## The 4-Touch Sequence Exit Criteria

The default outbound sequence is 4 touches spaced over ~3 weeks:

1. **Initial** — day 0
2. **Follow-up 1** — day 3–5
3. **Follow-up 2** — day 10
4. **Breakup** — day 21

After the breakup touch, if there is no reply, the prospect moves to **Stalled** automatically (not Lost — maybe the timing is wrong and a 2-month revival will work).

The founder should not send more than 4 touches in the initial sequence. 5+ touches cross the line from "persistent" to "annoying" and damage the sender domain reputation and personal brand.

---

## Reviving a Stalled Prospect

A Stalled prospect can be revived 4–8 weeks after stalling, but the revival touch must be **different** from the original outreach — not just a "bump" that repeats the same angle.

Good revival angles:
- A new product or feature launch that addresses something the prospect mentioned
- A new case study or customer reference that is relevant to their role or company
- A new piece of research or content that they would find valuable
- A change in the prospect's own situation (new funding, new hire, new product launch at their company)
- A referral or mutual connection introduction

Bad revival angles:
- "Just following up on my previous email"
- "Checking in to see if you had a chance to look at my earlier message"
- Re-sending the same pitch with a new subject line

When reviving, the transition is `Stalled → Contacted`, and the Notes field should capture what changed and why the founder is trying again.

---

## Handling the "Busy" Reply

A common reply pattern: "I'm slammed right now, let's talk in a few weeks" or "Interesting, but this quarter is crazy. Q3?"

This is a real reply, not a silent stall. The right move:

1. Transition the prospect from `Contacted` or `Replied` to `Stalled` with a specific revival date in the Notes field (e.g., "Revive 2026-07-01 — they asked for Q3 conversation").
2. Set a calendar reminder for the founder to re-run `pipeline-tracker-manager` on that date.
3. When the revival date arrives, the skill should surface the prospect: "[Prospect] asked for a Q3 touch back on [date] — time to re-engage."

Do not leave "Q3 busy" prospects in Contacted. They clog the flags and get confused with genuinely silent prospects.

---

## The Weekly Review Cadence

Project 05 assumes the founder runs `pipeline-tracker-manager` at least once a week. The weekly review should cover:

1. **Updates from the past week** — every prospect that changed stage, every new touch sent, every reply received
2. **Stuck prospect triage** — every prospect flagged by the 14-day rule gets a decision (follow-up, stall, or lose)
3. **Next week's actions** — the 3–5 highest-priority actions for the upcoming week
4. **Design partner candidate check** — any prospect in Design Partner Conversation stage: has the founder reviewed `design-partner-framework.md`? Is there a next meeting booked?

The founder should spend no more than 15–20 minutes on the weekly review. If it takes longer, the tracker is too big — trim it by moving stale prospects to Stalled or Lost.

---

## What A Healthy Pipeline Looks Like

At different stages of Project 05, a healthy pipeline has different shapes:

### Week 1–2 (early stage)
- 10–15 total prospects
- 70% in Prospecting, 30% in Contacted
- 0–1 Replied
- 0 Meeting Scheduled, 0 Design Partner Conversation, 0 Committed

### Week 3–4 (initial traction)
- 15–25 total prospects
- 30% Prospecting, 40% Contacted, 15% Replied, 10% Meeting Scheduled, 5% Stalled
- 0–1 Design Partner Conversation

### Week 6–8 (first design partner conversations)
- 25–40 total prospects
- Mix across all stages
- 1–3 Design Partner Conversation
- 5–10 Stalled or Lost (accumulation is normal and healthy if the fit is wrong)

### Unhealthy patterns to flag

- **Too many in Prospecting for too long** — the founder is researching but not sending outreach. Push on outreach cadence.
- **Zero Replies across 20+ Contacted** — the outreach itself is not working. Recommend re-running `email-drafter` with a different angle, or revisit `objection-handler` for missing context.
- **Many Design Partner Conversations that never reach Committed** — the framing is unclear or the asymmetric exchange is not being articulated. Recommend re-running `design-partner-advisor`.
- **Everything sitting in Stalled** — the founder is avoiding the revive-or-lose decision. Force the issue by walking through each Stalled prospect.

---

## What To Do When The Founder Resists Hygiene

Founders sometimes resist moving prospects to Stalled or Lost because it feels like giving up. Push back when:

- The founder wants to keep a prospect in Contacted for 30+ days because "they might still reply"
- The founder wants to mark a prospect Stalled instead of Lost because "they might come back" even though the prospect explicitly declined
- The founder adds new prospects faster than they move old ones through stages

The push-back language:

> "Keeping [prospect] in Contacted for 30 days without a touch is hiding a real decision. Either you're going to send them a follow-up, or you're not. If you are, let's draft it now. If you're not, let's move them to Stalled so they stop clogging your week's signal."

The tracker serves the founder's operational clarity, not the founder's optimism.
