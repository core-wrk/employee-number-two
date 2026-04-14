# Willingness-to-Pay Signal Patterns

Internal reference for `feedback-synthesizer`. This section of the synthesis report is the primary input into Project 09. Get it right and pricing strategy has real data to work with; get it wrong and Project 09 is guessing.

WTP signal is often indirect. Users rarely volunteer a price cleanly. Your job is to extract the signal from what they said and present it in a structured form that Project 09 can act on.

---

## Direct price signal

If `feedback-collector` used Van Westendorp's four anchors, you have direct signal:

1. **Too expensive** — price floor respondents name as "wouldn't consider"
2. **Expensive but would still consider** — upper end of acceptable range
3. **Great deal / bargain** — lower end of acceptable range
4. **Too cheap, doubt quality** — absolute floor

Report all four as ranges (e.g., "Too expensive: $100–$250/month across respondents") with the per-respondent numbers in a table, not just averages. Average-only hides bimodal distributions that reveal two distinct pricing segments.

The **acceptable range** is the overlap between "would still consider" and "great deal." That is the range Project 09 should anchor on.

---

## Indirect price signal

Most rounds will not have clean Van Westendorp data. Extract indirect signal:

### Alternative-cost anchors

"How are users currently solving this problem, and what does that cost?"

A user who currently pays $500/month for a tool they would replace with yours has anchored WTP at something less than $500. A user whose alternative is "I just do it manually, takes 5 hours/week" has anchored at the value of those 5 hours — depends on their role and time-cost.

Report alternative costs as a table:

| Respondent | Tier | Current solution | Current cost | Implied ceiling |
|---|---|---|---|---|
| AB | A | [tool name] | $X/mo | <$X/mo |
| CD | A | manual | 5 hrs/wk | depends on role |

### Value-earliness signal

"Which users seemed willing to commit financially, even if they did not name a price?"

Signals:
- Asked unprompted about pricing or timeline to launch
- Asked about team seats, enterprise features, or contract terms
- Said something like "I'd pay for this" or "when are you charging?"
- Mentioned budget authority without prompt

Track how many of the activated cohort showed these signals — that ratio is a WTP leading indicator.

### Expansion signal

"Which users asked for features that would typically command a premium tier?"

Users who ask for SSO, audit logs, role-based permissions, or white-label are signaling they would pay for enterprise features — directly relevant to Project 09's tier structuring.

---

## Form preferences

Users often prefer specific pricing shapes. Report the distribution across respondents:

| Form | Count | Notes |
|---|---|---|
| Monthly subscription | N | |
| Annual subscription (with discount) | N | |
| Per-seat | N | |
| Usage-based | N | |
| One-time purchase | N | |
| Unsure / no preference | N | |

If one form dominates, Project 09 has a clear starting point. If the distribution is split, flag it — it may indicate the cohort contains multiple personas with different preferences.

---

## Budget authority

"Is buying this a discretionary decision, or does it require approval?"

- **Discretionary (personal card, small team budget)** — supports self-serve, lower-friction pricing
- **Manager approval** — supports per-seat pricing with small initial seats that expand
- **Procurement / enterprise approval** — supports annual contracts and sales-assisted motion

Report the breakdown. This is as important as price — a $50/month discretionary is very different from $50/month procurement-gated.

---

## Pricing objections

Capture any hesitations respondents named, even if no price was asked:

- "It would be hard to justify paying because…" — objection type
- "I'd pay for this if it also did…" — bundle expectation
- "My company won't buy this because…" — sales-cycle friction

These are Project 09's starting list of objections to address in packaging or sales motion.

---

## The Sean Ellis WTP proxy

If `feedback-collector` used the Sean Ellis question ("how disappointed if you could no longer use this?"), the "very disappointed" percentage is a WTP proxy:

- **40%+ very disappointed** — strong WTP likely across the segment
- **25–40%** — mixed; WTP will depend on segment and positioning
- **Below 25%** — weak WTP; pricing is not the problem, fit is

Report the Sean Ellis distribution alongside direct/indirect price anchors.

---

## Tier-stratified WTP

Always report WTP separately by ICP tier:

- **Tier A acceptable range:** $X–$Y
- **Tier B acceptable range:** $X–$Y
- **Tier A form preference:** [dominant form]
- **Tier B form preference:** [dominant form]

If Tier A and Tier B diverge substantially on WTP, it usually means the pricing should be set for Tier A (your true ICP) — Tier B is adjacent and may not convert at Tier A's price point.

---

## When WTP signal is absent

It is legitimate to report "No WTP signal in this round." That happens when:

- The survey did not include pricing questions
- Users were too early in the product to have formed a price opinion
- Interview conversations avoided pricing intentionally

Do not manufacture signal. Project 09 is better served by "no signal yet" than by a fabricated range. Recommend in this case: "Run `feedback-collector` with a WTP-focused survey before Project 09."

---

## Headline format for `validated-insights.md`

The distilled summary should include 1–3 sentences of WTP signal, structured as:

- **Acceptable price range (if known):** $X–$Y for Tier A, $X–$Y for Tier B
- **Dominant form preference:** [form] among Tier A
- **Budget authority:** [N%] discretionary, [N%] approval-required
- **Signal strength:** strong / moderate / weak / absent

This is what Projects 09 and 11 auto-load.
