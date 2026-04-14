# Check-in Cadence Playbook

Internal reference for `cs-engager`. Matches check-in timing and message type to user status. Defaults — override only when the user has signaled a different rhythm.

---

## Cadence by status

| Status | Cadence | Stage label | Message type |
|---|---|---|---|
| Invited (not yet accepted) | 3 days after invite, then 7 days | day_3 / day_7 | Nudge |
| Accepted (not yet activated) | 3 days after acceptance | day_3_accepted | Unblock |
| Activated — first week | 7 days after first use | day_7 | First-impression ask |
| Activated — second / third week | 14 days after first use | day_14 | Value-check |
| Activated — first month | 30 days after first use | day_30 | Retention + synthesis seed |
| At-risk (silent 10+ days post-activation) | Immediately | at_risk | Re-engage |
| Deferred (user explicitly said "later") | Do not contact until date passes | deferred | Honor the defer |

Cadence assumes an average early-access cohort. Enterprise users tolerate slower rhythms; consumer / prosumer users expect faster.

---

## Message types and templates

### Nudge (invited, day 3 / day 7)

Purpose: surface the invitation in case it was missed. Low-pressure.

Structure:
- Subject: "Re: [prior invitation subject]" OR "Quick nudge on early access"
- Body: 2–3 sentences. Reference the original invitation, acknowledge they may have missed it, restate the ask briefly, provide the accept link again.
- Ask: same as original invitation — one click or one reply.

Do not send more than two nudges total. After day 7 with no response, mark as Declined in the tracker.

### Unblock (accepted, day 3 post-acceptance, not activated)

Purpose: find out what is preventing them from starting to use the product.

Structure:
- Subject: "Anything blocking you on [product name]?"
- Body: reference that they accepted but have not started yet (check tracker activation data). Ask directly if anything is blocking. Offer a 10-minute onboarding call.
- Ask: reply with the blocker, or pick a time.

This is the highest-leverage check-in in the cadence. Users stuck between accept and activate are the easiest to save and the easiest to lose.

### First-impression (activated, day 7)

Purpose: collect lightweight feedback on the first-use experience while it is still fresh.

Structure:
- Subject: "Curious how your first week with [product] went"
- Body: reference their activation date. Ask one concrete question — usually about the first-value moment. Acknowledge this is informal and a reply is optional.
- Ask: one sentence on their first impression, or a 15-minute call if they have more to say.

Keep this one short. The user has been in the product for a week — they have limited patience for a survey-sized ask.

### Value-check (activated, day 14)

Purpose: learn whether the product is becoming habitual or has already fallen out of the routine.

Structure:
- Subject: "[Product] — where does it fit for you now?"
- Body: reference what they were trying to accomplish (from tracker Notes or prior conversation). Ask whether the product has become part of their routine or whether it has drifted. Honest answers welcome.
- Ask: one paragraph reply, or nothing (explicitly allow silence).

### Retention + synthesis seed (activated, day 30)

Purpose: capture 30-day perspective and seed the first formal feedback survey.

Structure:
- Subject: "One month in — what's your take?"
- Body: reference their 30 days, ask for their overall view, and mention that a short survey is coming soon. Offer a 30-minute call if they would rather talk.
- Ask: short reply, call, or wait for survey.

After this check-in, trigger `feedback-collector` if not already scheduled.

### Re-engage (at-risk)

Purpose: one honest attempt to surface what is wrong.

Structure:
- Subject: "Haven't seen you in [product] — what went wrong?"
- Body: direct, not apologetic. Name that you noticed they stopped using it. Ask what changed — was it the product, the timing, or something else. Make clear the reply is low-stakes.
- Ask: one sentence reply. No call ask here — calls feel like pressure when someone is already disengaging.

If no reply within 7 days, mark as Churned and move to the next cohort. Do not send a second re-engage — it reads as pestering.

### Honor the defer

When a user has said "get back to me in [time]," draft no message until the time passes. When it passes, the next message references their own defer: "You mentioned getting back in [timeframe] — checking in now."

---

## When to break cadence

- **User proactively reached out with feedback or a question** — reply to their message, do not send a scheduled check-in on top of it
- **User reported a bug** — handle as support, then check back in 3 days after resolution
- **User's company did something public (funding, launch, layoff)** — a short, human message acknowledging it lands much better than a cadence-driven check-in
- **Major product change or outage** — a cohort-wide communication from the founder replaces individual check-ins for that cycle

---

## Over-check signals

Stop adding check-ins when:

- The user has three unanswered messages in their thread
- The user has explicitly said "please slow down" or "I'll come back when I'm ready"
- The cohort response rate has dropped noticeably across multiple users (sign the cadence is feeling pushy to the group)

Under-checking is recoverable. Over-checking burns the relationship permanently.
