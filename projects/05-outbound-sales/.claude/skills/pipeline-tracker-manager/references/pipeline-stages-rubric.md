# Pipeline Stages Rubric

This is an internal reference for the `pipeline-tracker-manager` skill. It defines every stage in the fixed stage enum, what counts as a valid transition into and out of each stage, the typical time-in-stage, and when to flag a prospect as stuck. **Do not show this document to the founder.** Use it to validate stage transitions, push back on invalid ones, and decide when to surface stuck prospects.

---

## The Fixed Stage Enum

The pipeline tracker uses exactly 8 stages. Not 7, not 9. Do not invent custom stages. If the founder wants a stage that does not fit, map their intent onto the closest existing stage and use the Notes field for qualifying detail.

```
Prospecting → Contacted → Replied → Meeting Scheduled → Design Partner Conversation → Committed
                                                                                     ↘
                                                                                        Lost / Stalled
```

Lost and Stalled are terminal-ish states. Stalled can be revived; Lost is effectively permanent unless the prospect's context materially changes.

---

## Stage Definitions

### 1. Prospecting

**What it means:** The prospect exists in `prospect-list.md` but no outreach has been sent yet. This is the default starting stage for every new prospect.

**Valid transitions into Prospecting:** Only from adding a new prospect (no prior stage). Never from another stage — you do not move a prospect "back to Prospecting."

**Valid transitions out of Prospecting:**
- → Contacted (normal — initial outreach sent)
- → Lost (rare — founder decides the prospect is a disqualifier before even contacting)
- → (nothing else is valid from Prospecting)

**Typical time in stage:** 1–7 days. Prospects should not sit in Prospecting for more than 2 weeks — if they do, the founder either needs to send outreach or move them to Lost.

**Stuck threshold:** 14 days. A prospect sitting in Prospecting for 14+ days without a `Last Touch` is flagged. The founder should either draft outreach or move to Lost.

---

### 2. Contacted

**What it means:** Initial outreach has been sent and the prospect has not yet replied. The `Last Touch` date is the date the outreach was sent. The Notes field should reference the outreach draft filename from `outputs/outreach-drafts/`.

**Valid transitions into Contacted:**
- ← Prospecting (normal — outreach just went out)
- ← Stalled (valid — a stalled prospect got re-engaged with a new touch)

**Valid transitions out of Contacted:**
- → Replied (normal — prospect responded)
- → Stalled (normal — 14+ days without reply, founder is moving on for now)
- → Lost (valid — founder decided the prospect is not worth pursuing further)
- → Meeting Scheduled (unusual — skips Replied stage, happens when the outreach directly proposed a meeting slot and the prospect accepted without a separate reply step)

**Typical time in stage:** 3–14 days. Cold outreach replies usually come within a week if they come at all.

**Stuck threshold:** 14 days. A prospect sitting in Contacted for 14+ days without a reply is either going to become a follow-up (run `email-drafter` with sequence_position=follow-up-1) or is becoming Stalled.

---

### 3. Replied

**What it means:** The prospect has responded to the outreach. The response can be positive ("sure, let's talk"), neutral ("tell me more"), or negative ("not interested"). The Notes field should capture the gist of the reply.

**Valid transitions into Replied:**
- ← Contacted (normal)

**Valid transitions out of Replied:**
- → Meeting Scheduled (normal — the reply led to booking a call)
- → Lost (normal — the reply was a clear "no" or a disqualifier)
- → Contacted (valid — the founder responded to the reply with more information and is waiting for the next round)
- → Stalled (valid — the prospect replied once and then went silent when the founder tried to book a meeting)

**Typical time in stage:** 1–10 days. Replies should convert to meetings quickly if they are going to; otherwise they decay.

**Stuck threshold:** 10 days (tighter than Contacted because a replying prospect is warmer and decay is faster).

---

### 4. Meeting Scheduled

**What it means:** A call is on the calendar. The Notes field should capture the date and what the prospect wants to talk about.

**Valid transitions into Meeting Scheduled:**
- ← Replied (normal)
- ← Contacted (unusual but valid — outreach that directly proposed a slot)
- ← Design Partner Conversation (valid — founder scheduled a follow-up meeting in an ongoing conversation)

**Valid transitions out of Meeting Scheduled:**
- → Design Partner Conversation (normal — the meeting happened and the founder is now actively in a co-development framing conversation)
- → Lost (normal — the meeting happened and revealed the fit is wrong, or the prospect no-showed)
- → Replied (valid — the meeting happened but was purely exploratory and the prospect needs to consult others before a second meeting)
- → Committed (rare — prospect agreed to a design partnership on the first meeting)

**Typical time in stage:** 1–14 days (however long until the scheduled meeting happens).

**Stuck threshold:** 21 days. A meeting scheduled more than 3 weeks out is a flag — either reschedule is coming or the prospect is slipping. Surface it to the founder.

**Special handling:** When a prospect enters Meeting Scheduled, the next_action should always be "Run `pre-call-brief-builder` the day before the call."

---

### 5. Design Partner Conversation

**What it means:** The prospect is actively in a multi-meeting conversation about becoming a design partner. This is not "we had one call." It is "we're in a sequence of conversations working toward a potential design partnership." The Notes field should capture what has been discussed so far and what the open questions are.

**Valid transitions into Design Partner Conversation:**
- ← Meeting Scheduled (normal — the first substantive meeting happened and it went well enough to continue)

**Valid transitions out of Design Partner Conversation:**
- → Committed (normal — the prospect agreed to the design partnership)
- → Lost (normal — after more conversation, the fit turned out to be wrong)
- → Meeting Scheduled (valid — a specific next meeting is on the calendar; prospect is still in active conversation)
- → Stalled (valid — the prospect has gone silent in the middle of an active conversation)

**Typical time in stage:** 2–8 weeks. Design partnership conversations take time — the asymmetric exchange (what you offer, what you ask) needs real discussion.

**Stuck threshold:** 30 days. Design partner conversations are slow-moving, so the stuck threshold is longer than earlier stages. A prospect stuck here for 30+ days without a touch is probably slipping.

**Special handling:** Whenever a prospect is in this stage, surface the `design-partner-framework.md` reference: "Make sure you've reviewed the framework before your next conversation." If `design-partner-framework.md` does not exist, surface `design-partner-advisor` as the skill to run.

---

### 6. Committed

**What it means:** The prospect has agreed to a design partnership, an early customer relationship, or a paid pilot. This is a terminal-positive stage — the outbound motion worked. The Notes field should capture the terms (hours per week from the prospect, pricing concession from the founder, scope of the engagement).

**Valid transitions into Committed:**
- ← Design Partner Conversation (normal)
- ← Meeting Scheduled (rare — one-meeting commitments happen occasionally)

**Valid transitions out of Committed:**
- → (none — Committed is terminal for Project 05 purposes)

**Typical time in stage:** Permanent. Once a prospect is Committed, they leave the outbound workflow and enter Project 08's onboarding workflow for design partners / beta users.

**Stuck threshold:** Not applicable — Committed is terminal.

**Special handling:** When a prospect hits Committed, surface the handoff to Project 08: "Time to move [prospect] into Project 08's beta / design partner onboarding workflow. Project 08 reads this tracker so the prospect will be visible there automatically."

---

### 7. Lost

**What it means:** The prospect explicitly declined, the fit turned out to be wrong after a conversation, or the founder decided to stop pursuing. The Notes field should capture the reason (this is valuable data for ICP refinement).

**Valid transitions into Lost:**
- ← Any stage

**Valid transitions out of Lost:**
- → Prospecting (valid but rare — the prospect's context materially changed, e.g., they moved to a new company that is a better fit)

**Typical time in stage:** Permanent (unless the prospect's context changes).

**Stuck threshold:** Not applicable — Lost is effectively terminal.

**Special handling:** Capture the reason in the Notes field. Over time, patterns in Lost reasons reveal ICP problems ("we keep losing because the buyer isn't senior enough" → update the ICP to raise the seniority threshold).

---

### 8. Stalled

**What it means:** The prospect went silent after initial engagement (either in Contacted or later) and the founder is setting them aside for now. Different from Lost — Stalled means "maybe later"; Lost means "not them." The Notes field should capture when they went silent and what the last attempted touch was.

**Valid transitions into Stalled:**
- ← Contacted (normal — no reply after follow-ups)
- ← Replied (normal — they replied once, then went silent)
- ← Meeting Scheduled (normal — they no-showed and did not reschedule)
- ← Design Partner Conversation (normal — they went silent mid-conversation)

**Valid transitions out of Stalled:**
- → Contacted (normal — the founder sent a revival touch and the prospect is back in the funnel)
- → Lost (normal — after 30+ days stalled, the founder decides to close the loop)

**Typical time in stage:** 30 days before deciding: revive or mark Lost.

**Stuck threshold:** 30 days. A prospect stalled for 30+ days should be moved to Lost unless the founder has a specific reason to revive.

**Special handling:** When moving a prospect into Stalled, ask the founder: "Do you want to set a date to revive this prospect (e.g., 'follow up in 4 weeks') or are you okay letting them sit?" The revival date goes in the Notes field.

---

## Invalid Transitions And How To Push Back

Some stage transitions are almost always wrong. Surface them to the founder before accepting:

- **Prospecting → Committed** — skips the entire sales cycle. Almost always means the founder is mis-categorizing or skipping steps. Push back: "You're moving [prospect] from Prospecting to Committed — did they agree to a design partnership without any conversation, or should we record the intervening stages?"
- **Prospecting → Design Partner Conversation** — same issue, skips Contacted and Meeting Scheduled. Push back.
- **Lost → Committed** — a prospect who was marked Lost and then committed should go through Prospecting → Contacted → Replied → ... again. This reflects that their context materially changed. Push back: "[Prospect] was previously marked Lost. Did something change about them? I'd recommend re-entering them at Prospecting and walking through the stages so the history is accurate."
- **Committed → anything else** — Committed is terminal. If the founder wants to move a Committed prospect, ask why: "Did the commitment fall through? If so, the right path is Committed → Lost with a note about what happened."
- **Any stage → the same stage** — not a transition, just a lateral edit. Ask what actually changed.

---

## Stuck Thresholds Summary

| Stage | Stuck Threshold | Rationale |
|---|---|---|
| Prospecting | 14 days | Outreach should happen within 2 weeks or the prospect is dead |
| Contacted | 14 days | Cold reply window is ~1 week; 14 days without reply means follow-up or stall |
| Replied | 10 days | Replies are warm; they decay fast |
| Meeting Scheduled | 21 days | Meetings scheduled 3+ weeks out are slipping |
| Design Partner Conversation | 30 days | Design partnership conversations are slow; 30 days is the patience limit |
| Committed | n/a | Terminal |
| Lost | n/a | Terminal |
| Stalled | 30 days | After 30 days stalled, decide revive or Lost |

Every Monday, walk through the tracker and flag every prospect that has exceeded its stage's stuck threshold. The point of the tracker is to surface stuck prospects so the founder can decide what to do about them.
