# Signal Strength Rubric

This is an internal reference for the `reddit-researcher` skill. It defines how to rate each Reddit finding by signal strength. **Do not show this document to the founder.** Use it to assign a rating — Strong, Moderate, Weak, or Noise — to every thread you surface.

---

## The Four Ratings

### Strong
Use when **at least 3 of the 5** indicators below are present:

- The post describes a **specific, concrete pain** — not a general complaint ("onboarding new reps takes 2 months and the content is all outdated" rather than "training is hard")
- The post is **less than 12 months old** (or from the window defined in the research plan)
- There is **engagement**: multiple commenters agreeing, sharing similar experiences, or proposing workarounds. High comment count matters more than high upvotes.
- The user **volunteered the pain unprompted** — they were not responding to a vendor survey, product launch, or AskReddit thread
- The user **describes a current workaround** and why it is inadequate (this is gold — it means they are already paying a cost)

A single Strong finding can carry a report. Strong findings deserve a direct quote and a "Why this matters" note tying them to the founder's hypothesis.

---

### Moderate
Use when the finding is real but weaker — typically 1 or 2 Strong indicators, or the thread is older, or the pain is somewhat general, or there is no comment engagement.

Moderate findings are worth including in the report but do not deserve the same attention as Strong findings. List them in a condensed format: thread link, brief description, one-sentence relevance note.

---

### Weak
Use when the thread mentions the topic but the pain is not clear, the thread is old (>18 months for fast-moving domains), or the user is the only one engaged with the complaint.

Weak findings are listed at the end of the report as one-line entries. They are included for completeness but the founder should not weight them heavily.

---

### Noise — drop from the report
Use when the thread is:

- Off-topic despite matching keywords
- Posted by a vendor, affiliate, or bot (check the poster's history if the post feels promotional)
- A generic question with no pain or frustration attached ("what is the best X?" with no context on why)
- Satire, memes, or humor that don't reflect real pain
- A year or more old on a topic where the landscape has clearly moved on
- Clearly brigaded (artificially upvoted/downvoted with suspicious comment patterns)

**Drop Noise findings entirely.** Do not include them in the report. The signal-to-noise ratio of the report matters more than comprehensiveness.

---

## Indicator Reference

These are the five indicators used to determine Strong vs. Moderate:

| Indicator | What to look for | Why it matters |
|---|---|---|
| **Specificity** | Named workflows, tools, role titles, dollar amounts, time estimates | Vague complaints generalize poorly; specific ones are evidence |
| **Recency** | <12 months old for most domains; <6 months for fast-moving tech | Stale signal may not reflect current reality |
| **Engagement** | Multiple comments with "same," "this," "I've had the same problem" | One person's complaint is an anecdote; five is a pattern |
| **Unprompted** | Organic posts, not responses to "what do you hate about X?" threads | Prompted complaints are lower quality — people invent pain when asked |
| **Workaround cost** | User describes what they do today and why it is painful | Workarounds are proof of willingness to pay — they are already paying in time |

---

## Common Mistakes

- **Don't rate by upvote count alone.** A viral post with 5000 upvotes and no engaged comments is less useful than a 40-upvote post with 30 substantive replies. Engagement beats reach.
- **Don't overrate vendor-adjacent communities.** Subreddits where vendors and users mix (r/salesforce, r/hubspot) can be brigaded by people with a stake in the answer. Be more skeptical of findings from these communities.
- **Don't undercount qualitative richness.** A single well-written post from a real practitioner can be Strong even without high engagement, if the specificity and workaround-cost indicators are clearly present.
- **Don't conflate volume with signal.** Finding 50 weak threads is worse than finding 5 strong ones. Quality filter aggressively.

---

## Special Case: Absence of Signal

If you search thoroughly and find very few or no relevant threads, that is itself a finding — report it. Possible interpretations:

- The target customer does not use Reddit (common for enterprise buyers, C-suite roles, certain professions)
- The pain is too niche to generate public discussion
- The pain is real but people do not complain about it publicly (sensitive topics, regulated industries)
- The pain does not actually exist and the founder's hypothesis needs rethinking

Do not interpret absence of signal as validation that the problem is not real. Interpret it as: "Reddit is not the right source for this question — try user interviews, industry forums, or other channels instead." Put that conclusion in the "Gaps" section of the report.
