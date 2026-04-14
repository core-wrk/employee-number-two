# Survey Question Library

Internal reference for `feedback-collector`. Question patterns grouped by learning goal. Adapt wording to the ICP's vocabulary; the patterns are starting points, not final copy.

---

## Learning Goal: Usability

Purpose: learn whether users can accomplish the core task without friction. Focuses on the onboarding flow, the first-value moment, and any confusion points.

### Core questions

1. **First-value latency (scale + free-text)** — "On a scale of 1–5, how easily were you able to [accomplish the core task] the first time you tried? What made it easy or hard?"
2. **Stuck points (free-text)** — "Was there any moment during setup or first use where you got stuck or confused? Describe what happened."
3. **Onboarding completeness (multiple choice)** — "Which of these best describes your onboarding experience? [I finished setup without help / I needed to check docs / I had to reach out / I gave up and came back later]"
4. **Task success rate (multiple choice)** — "Did you successfully [accomplish the core task] in your first session? [Yes / Partially / No / I didn't try]"
5. **Missing context (free-text)** — "Was there anything you wished the product had explained or shown you that it didn't?"
6. **Comparison to expectations (scale + free-text)** — "Based on what you expected when you signed up, how did the first experience compare? 1 = much worse, 5 = much better. Why?"

### Anti-patterns (avoid)

- "How easy is our product to use?" — too broad; cannot act on it
- "Rate our onboarding" — no anchor; respondents calibrate differently
- "Did you like the onboarding?" — binary, no reason captured

---

## Learning Goal: Value Perception

Purpose: learn whether users believe the product is solving a problem worth solving, and whether that belief is stable over time.

### Core questions

1. **Problem-solution fit (scale + free-text)** — "How well does [product] solve [specific problem from product-overview.md]? 1 = not at all, 5 = exactly what I needed. In your own words, why?"
2. **Replacement cost (free-text)** — "If [product] stopped working tomorrow, what would you do instead? What would you lose?"
3. **Sean Ellis test (multiple choice)** — "How would you feel if you could no longer use [product]? [Very disappointed / Somewhat disappointed / Not disappointed / N/A — I haven't used it enough]"
4. **Recommendation intent (scale)** — "How likely are you to recommend [product] to a peer in your role? 0–10."
5. **Why recommend / why not (free-text, follow-up to above)** — "What's the main reason for that score?"
6. **Frequency / depth signal (multiple choice)** — "How often have you been using [product]? [Daily / A few times a week / Once this week / Not since onboarding]"

### The Sean Ellis test

The "very disappointed" percentage is the most predictive signal of product-market fit. Target: 40%+ answering "very disappointed" indicates strong PMF signal. Below 40%, the product is not yet pulling its weight.

### Anti-patterns

- "Do you like [product]?" — no directional signal
- "How valuable is [product]?" — too abstract
- NPS without the follow-up "why" — unusable for synthesis

---

## Learning Goal: Willingness to Pay

Purpose: learn what users would pay for [product] and what shape the pricing should take. Direct "would you pay $X?" questions under-perform — users either flatter the founder (yes) or anchor low (no). Use indirect patterns.

### Van Westendorp Price Sensitivity Meter

Four price-anchor questions. Each is a free-text response with a currency amount. Synthesis crosses them to find the acceptable range.

1. "At what monthly price would [product] be so expensive that you would not consider buying it?" (Too expensive)
2. "At what monthly price would [product] start to feel expensive, but you would still consider it?" (Expensive / getting expensive)
3. "At what monthly price would [product] feel like a great deal — inexpensive but not so cheap you doubt the quality?" (Cheap / bargain)
4. "At what monthly price would [product] be so cheap that you would doubt its quality?" (Too cheap)

### Alternative-cost anchoring

"Today, how do you solve [problem] without [product]? What does that alternative cost you in dollars, hours, or opportunity cost per month?"

This question anchors the respondent to their current substitute's cost, which is the realistic ceiling for your pricing.

### Feature-bundle tradeoff

Present 3–4 bundles (feature set + price) and ask:

"Which of these packages would you most likely choose for your team?"

The distribution of choices reveals both price sensitivity and which features drive purchase intent.

### Commitment form

Instead of asking about willingness directly, ask about form:

"If you were paying for [product], which of these would you prefer? [Monthly subscription / Annual subscription at 20% discount / Per-seat pricing / Usage-based pricing / One-time purchase]"

### Budget authority

"Would getting [product] for your team require approval, or is it within your discretionary budget?"

This reveals the decision-making process, which changes the sales motion more than the price.

### Anti-patterns

- "Would you pay $X/month?" — yes-biases from users who like the founder; anchor-biases from users who want the product cheaper
- "What is a fair price?" — invites low-balling
- "Is [product] worth the cost?" — before a price is set, this is circular

---

## Learning Goal: Feature Gaps

Purpose: learn what users want next, and which of those wants actually reflect product-market fit (vs. wants that would fragment the product into something worse).

### Core questions

1. **Must-have missing (free-text)** — "Is there anything you consider a must-have feature that [product] doesn't yet do? What is it?"
2. **Workflow friction (free-text)** — "Walk us through how [product] fits into your current workflow. Where does it slot in cleanly, and where does it force you to leave and come back?"
3. **Expansion prompt (multiple choice)** — "If we added one of these next, which would you want most? [list of roadmap candidates from epic-list.md]"
4. **Importance ranking (ranking)** — "Rank these capabilities by how valuable they would be to you: [list of 5–7]"
5. **Out-of-product tools (free-text)** — "What other tools do you use alongside [product]? Is there a connection between them you wish existed?"
6. **Explicit deprioritization (free-text)** — "Is there anything [product] does that you don't use or don't care about? We're as interested in what to remove as what to add."

### Weighing the answers

Feature requests are noisy. Weigh them by:

- **Repetition across the cohort** — one user asking is a data point; five users asking is a pattern
- **ICP tier of the requester** — a Tier A user's request matters more than a Tier C user's
- **Coherence with the product's wedge** — requests that sharpen the wedge > requests that broaden it into a feature-parity tool

### Anti-patterns

- "What features do you want?" with no constraint — invites everything
- "Rate the importance of each feature" in isolation — respondents rate everything important
- Ranking questions longer than 7 items — cognitive load collapses the signal

---

## Segmentation questions (every survey)

Include 1–2 at the end of every survey to confirm ICP tagging for synthesis:

- **Role confirmation** — "What's your current role? (short text)"
- **Company size** — "How many people are at your company? [1–10 / 11–50 / 51–200 / 201–1000 / 1000+]"

Do not re-ask information already in `beta-user-tracker.md`. These are confirmation only.
