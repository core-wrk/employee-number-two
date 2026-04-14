# Retention Risk Signals

Internal reference for `cs-engager`. How to read `beta-user-tracker.md` state for disengagement patterns before they become churn. Each signal has a tier weight and a recommended response.

---

## Status-based signals

### Invited, no acceptance after 7 days
- **Tier A:** moderate risk. One more nudge, then mark Declined.
- **Tier B:** low risk. Mark Declined after the second nudge.
- **Response:** Nudge (see cadence playbook). No more than two total.

### Accepted, not activated after 5+ days
- **Tier A:** high risk. Users who accept but never start are almost always stuck on a specific friction point.
- **Tier B:** moderate risk.
- **Response:** Unblock message. Offer a short onboarding call. If no reply after 3 days, mark as at-risk.

### Activated, silent 10+ days after first use
- **Tier A:** high risk. Silent Tier A users are the single highest-priority retention attention.
- **Tier B:** moderate risk.
- **Response:** Re-engage message. One attempt only.

### Activated, last session >14 days ago with no prior engagement
- **Tier A:** very high risk. Move to `at-risk` status immediately.
- **Tier B:** high risk.
- **Response:** Re-engage. Consider a direct phone call instead of email for Tier A.

---

## Behavior-based signals

These require the tracker's Notes field to have meaningful entries. If Notes are sparse, cross-reference with product analytics if available.

### Opened the product but took no action
Activation event fired, but core task never attempted. User is stuck or disinterested.
- **Response:** Unblock-style message focused on the specific capability they did not try.

### Completed the core task once, never returned
The "try once, abandon" pattern. Product failed the value-delivery test on first use.
- **Response:** Value-check message. Ask specifically what was missing or what they expected that did not happen.

### Asked a question and did not get a timely response
Rare but catastrophic. If the tracker shows a question that the founder did not reply to within 48 hours, this user is on the way out.
- **Response:** Direct apology + answer, then re-engage. Do not pretend the delay did not happen.

### Explicitly deferred but deferral has lapsed
User said "get back to me in 2 weeks," and 3 weeks have passed. The deferral was likely a polite decline.
- **Response:** One gentle message referencing their own deferral. If no reply, mark Declined.

### Mentioned a competitor or substitute in prior conversation
User has signaled they are actively evaluating alternatives. The retention window is narrow.
- **Response:** Value-check with emphasis on the specific differentiator that matters to them. Consider accelerating the onboarding-to-value motion.

---

## Cohort-level signals

These are patterns across multiple users, not individual signals.

### More than 40% of activated users silent for 10+ days
The cohort is disengaging, not individual users. The check-in cadence or the product's early-week experience is likely the cause.
- **Response:** Pause individual check-ins. Escalate to the founder: "Something is off at the cohort level — consider re-running `feedback-synthesizer` on what feedback you have, or re-examining the onboarding flow."

### Response rate on check-ins dropping across cycles
Cycle 1 got 70% replies, cycle 2 got 40%, cycle 3 got 20%. The cadence is wearing out the cohort.
- **Response:** Stretch the cadence. Move from 14-day to 21-day for activated users. Tighten individualization.

### Multiple users reporting the same blocker
If 3+ users flag the same issue in check-in replies, do not continue drafting individual check-ins referencing it. Escalate to `feedback-synthesizer` immediately — this is theme-quality signal.

---

## False-risk patterns

Not every silence is churn. Avoid escalating when:

- The user is known to be on vacation, in a launch, or otherwise temporarily unavailable (check Notes)
- The product's natural rhythm is weekly or less frequent (a project-management tool user may legitimately not log in for 5 days)
- The user has already provided recent feedback that led to a product change they are waiting on

When in doubt, send the check-in with low-pressure phrasing and let the user signal their state. Do not pre-flag them as at-risk in the tracker until they have actually failed to respond.

---

## Escalation matrix

For each signal, the response escalates along this ladder:

1. **Individualized check-in** (standard response)
2. **Direct phone call** (Tier A, high-risk signals only)
3. **Mark at-risk in tracker** (visible to founder's next session)
4. **Offer to pause their early-access participation gracefully** (if the user is clearly uninterested; preserves the relationship for later)
5. **Mark Churned** (final state; the user is out of the cohort)

Never skip steps for Tier A. Tier B can compress steps 1–3.

---

## Tracker-writing discipline

When surfacing risk to the founder:
- Name the specific signal ("14 days silent after activation"), not the vague concern ("might be at risk")
- Name the tier and the recommended response level
- Update the tracker Notes with the observation and the date

Silent risk in the tracker does not help the founder. Named, dated risk does.
