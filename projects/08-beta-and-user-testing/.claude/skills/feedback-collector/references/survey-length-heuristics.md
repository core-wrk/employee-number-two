# Survey Length Heuristics

Internal reference for `feedback-collector`. Length is the single biggest determinant of completion rate. Longer surveys feel thorough to the founder and get abandoned by the user. These heuristics are defaults — override only with explicit founder rationale.

---

## Length by distribution channel

| Channel | Max questions | Target completion time | Notes |
|---|---|---|---|
| In-product prompt | 2–3 | Under 60 seconds | Respondents are mid-task; anything more and they dismiss |
| Email body (inline) | 3–5 | Under 2 minutes | Respondents answer without leaving the inbox |
| Email link to form (Google Forms / Tally / Typeform) | 8–12 | 3–5 minutes | The click-through cost is already paid |
| 1:1 interview transcript (structured) | 10–15 | 30–45 minutes | Longest acceptable format; use sparingly |
| Exit / cohort-wrap survey | 10–15 | 5–7 minutes | Users who reached the wrap are already invested |

Exceeding these thresholds drops completion rates sharply. The data you do not collect because the user abandoned is worse than the data you would have collected with a shorter survey.

---

## Length by cohort size

Smaller cohorts can tolerate longer, more qualitative surveys because each response is higher-leverage. Larger cohorts need shorter surveys because synthesis becomes harder if each response has many open-ended fields.

- **Cohort of 5–10 users:** longer qualitative survey is fine; free-text is the point
- **Cohort of 10–25 users:** balance — scale questions with targeted free-text follow-ups
- **Cohort of 25+ users:** scale questions dominate; free-text only on 2–3 key questions

---

## Length by learning goal

Some goals are inherently shorter:

- **Usability** — 4–6 questions is plenty; you only need to cover onboarding, first-value, stuck points, and one open-ended
- **Value perception** — 5–7 questions; Sean Ellis + replacement cost + NPS-with-why is often the whole survey
- **Willingness-to-pay** — 4–6 questions; Van Westendorp's four anchors plus one context question
- **Feature gaps** — 5–8 questions; ranking + workflow + deprioritization

Combining goals into one survey multiplies the length. Prefer two shorter surveys at different moments.

---

## When to split into multiple surveys

Signs the founder is trying to pack too much in:

- Total proposed questions exceed the channel limit
- Multiple learning goals are named ("I want to learn usability *and* value *and* pricing")
- Questions cross lifecycle moments (some only make sense at day 7, others at day 30)

In each case, split and sequence. Two short surveys at two moments produce better synthesis than one long survey with 40% drop-off mid-flow.

---

## Question-type weighting

Not all question types have the same cognitive cost:

| Type | Relative cost | Max per survey |
|---|---|---|
| Scale 1–5 / 1–10 | Low | Up to 6–8 |
| Multiple choice (single-select, ≤5 options) | Low | Up to 4–5 |
| Short text (one sentence) | Medium | Up to 3–4 |
| Long text (paragraph) | High | Max 2–3 |
| Ranking (5–7 items) | High | Max 1 |
| Matrix / grid | Very high | Avoid — breaks on mobile |

If a draft survey is too long, convert long-text to short-text first, and scale-without-follow-up to the long-text in its place.

---

## Red flags

Cut or rework the survey if:

- More than 3 long-text questions
- Any matrix / grid questions
- Any question whose answer the synthesis cannot use
- Any question that duplicates information already in `beta-user-tracker.md`
- Intro copy longer than three sentences (users skim the intro; long intros cue abandonment)
- A "any other feedback?" question at the end that is the only free-text field — indicates the core questions were not asking the right things
