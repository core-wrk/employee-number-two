# Messaging Hierarchy Template

This is an internal reference for the `messaging-architect` skill. It defines the structure of the messaging framework document and the rules for what makes a strong proof point. **Do not show this document to the founder.** Use it to scaffold the framework document and to push back when a piece of messaging is too thin.

---

## Structure of `outputs/messaging-framework.md`

This is the structure the skill writes to. Match it exactly so downstream skills (`brand-voice-developer`, and later Project 04's content skills) can rely on the same shape.

```markdown
# Messaging Framework

## Headline Value Proposition
<One sentence. Customer language. Specific enough that no named competitor in competitive-landscape.md could say the same line truthfully.>

## Message Pillars

### Pillar 1: <Pillar statement in one short sentence, customer language>
- **Anchored to:** <named gap from competitive-landscape.md OR unique attribute from positioning-statement.md>
- **Proof points:**
  - <proof point 1> — status: <VALIDATED | DIRECTIONALLY SUPPORTED | LIVE QUESTION>
  - <proof point 2> — status: <...>
- **For the buyer:** <how this lands for the buyer, in 1–2 sentences>
- **For the user:** <how this lands for the user, in 1–2 sentences>

### Pillar 2: <...>
[same structure]

### Pillar 3: <...>
[same structure]

## Vocabulary

**Use these phrases:**
- <phrase> (source: icp.md "How They Talk About the Problem")
- <phrase>
- ...

**Avoid these phrases:**
- <phrase> — <reason>
- ...

## Objection Handlers

### Objection: "<objection in the buyer's own words, in quotes>"
**Response:** <2–4 sentences>

### Objection: "<...>"
**Response:** <...>

[Minimum 5 objections. Always include integration risk and incumbent-roadmap objections if they exist as live questions in startup-hypothesis.md.]

## Live Questions Carried Forward
- <messaging element that depends on a LIVE QUESTION in startup-hypothesis.md, with the question named>
- ...
```

---

## Rules for Pillars

### Three is the right number
Two feels thin. Four blurs together. Buyers can remember three things. If the founder insists on four, ask which of the existing three is weakest and whether the fourth replaces it. Almost always the answer is yes.

### Each pillar must anchor
Every pillar must be tied to either:
- A named capability gap in `competitive-landscape.md` (e.g., "AI feedback feels generic, not deal-specific" → pillar about deal-grounding), OR
- A unique attribute from `positioning-statement.md` (e.g., "grades responses against company-specific deal outcomes" → pillar about that attribute)

If a pillar does not anchor to either, it is decoration. Cut it.

### Pillars are claims, not features
"We use AI" is not a pillar. "Trained on your actual deal history" is a pillar. The difference is that a pillar describes what the customer gets, not what the product has.

### Pillars are independent
The three pillars should not collapse into each other. If pillar 1 and pillar 2 both restate the same value from slightly different angles, one of them is redundant. Push back.

---

## Rules for Proof Points

### What counts as a proof point
- A specific customer outcome with a number ("Reps at [Company X] cut first-call confidence-rating from 4/10 to 8/10 in two weeks")
- A specific user voice from research, with attribution ("'Mindtickle's quizzes don't translate to real conversations' — G2 review, March 2025")
- A specific data point about the underlying mechanism ("Trained on 10,000+ closed-won deal transcripts per customer")
- A specific named-logo social proof ("[Customer Name] uses this for their 30-rep onboarding cohort")
- A specific founder credential or domain authority claim, when relevant
- A specific demo moment that proves a capability

### What does NOT count as a proof point
- "Customers love it"
- "Industry-leading accuracy"
- "Proven results" (without naming the result)
- "Best in class" (compared to what?)
- "Trusted by leading companies" (which? doing what?)

### Proof status is required
Every proof point must have a status:

- **VALIDATED** — Project 01 research, prior customer pilots, or direct evidence supports this
- **DIRECTIONALLY SUPPORTED** — There is signal but not conclusive evidence (e.g., the cross-tool gap exists in `competitive-landscape.md` but the founder's specific solution to it has not been tested)
- **LIVE QUESTION** — The proof is not yet in place; it depends on a hypothesis that Project 08 will test

A messaging framework with 3 LIVE QUESTION proof points and 0 VALIDATED proof points is normal at this stage. What is not OK is claiming VALIDATED when no validation exists.

### Proof point density per pillar
Aim for 2–3 proof points per pillar. One feels weak. Four starts to look like a list. If the founder cannot find 2 proof points for a pillar — even DIRECTIONALLY SUPPORTED ones — that is a sign the pillar is too far from the evidence and should be revised.

---

## Rules for Buyer-vs-User Calibration

### Why this exists
The ICP separates buyer (VP Sales Enablement / RevOps) from user (new sales rep). They care about different things:

- **Buyer:** ramp-time-as-KPI, credibility to the CRO, cost per ramped rep, board-visible metrics, integration with existing stack, retention of the existing tool budget
- **User:** Will this help me feel less lost? Will this help me close my first deal sooner? Will this be fun or tedious? Is the feedback fair?

The messaging framework must serve both audiences because the founder will end up in both kinds of conversations: pitching the buyer for budget approval, and pitching the user when reps push back on yet another training tool.

### How to calibrate
For each pillar, ask: does this pillar land the same way for buyer and user, or differently?

If the same: write one calibration line that serves both.
If different: write two calibration lines, one per audience, in their respective vocabulary.

In practice, most pillars land differently. Even when the underlying claim is the same, the framing and the vocabulary should shift.

### Common mistake
Founders default to buyer-only messaging because the buyer signs the contract. The result is messaging that fails when the rep is in the room. Force the user calibration to be at least as substantive as the buyer calibration.

---

## Rules for Vocabulary

### Use these phrases
Pull verbatim from `icp.md`'s "How They Talk About the Problem" section. The customer's own words are always more credible than the founder's invented phrases. The vocabulary section is a small list (5–10 phrases) that downstream content can lean on.

### Avoid these phrases
Three categories:

1. **Marketing-language abstractions** — "next-generation," "revolutionary," "transformative," "leverage," "synergy," "best-in-class"
2. **Generic AI language** — "AI-powered," "intelligent," "smart," "personalized" (without saying personalized to what)
3. **Phrases owned by competitors** — if Mindtickle's homepage uses "sales readiness," using the same phrase makes the founder sound like a smaller Mindtickle. Pick a different phrase.

For each phrase in the avoid list, name the reason. "AI-powered — every competitor in `competitive-landscape.md` claims this; using it makes us indistinguishable."

---

## Rules for Objection Handlers

### Required objections (always include if applicable)
1. **Integration risk** — if `startup-hypothesis.md` has a live question about whether the integration partner (Gong, Chorus, etc.) will allow the integration, this objection must be addressed honestly.
2. **Incumbent roadmap** — if `startup-hypothesis.md` names a strategic risk from an incumbent expanding into the space (e.g., Gong's expansion into AI coaching), this objection must be addressed honestly.
3. **Pricing skepticism** — almost always present. Address it with reference to the value calculation, not by lowering the price.
4. **"How is this different from [closest direct competitor]"** — usually Second Nature or Mindtickle in the example founder's case.
5. **"We already have a workaround that's good enough"** — usually shadow pairing or internal wikis.

### Length
Each handler should be 2–4 sentences. Long enough to be specific. Short enough that the founder can deliver it on a sales call without reading from notes.

### Honesty over persuasion
If an objection has a real answer that hurts ("Yes, Gong is shipping AI coaching too — our window is 12–24 months"), the response should be honest, not evasive. Founders who try to spin the unanswerable objection sound less credible than founders who acknowledge it and have a plan.

---

## Common Mistakes Across the Whole Framework

- **Generic single-message framework** — one message for everyone, no buyer/user split, no vocabulary section. Means downstream projects have to do this work themselves.
- **Pillars that float** — no anchor to gaps or attributes. Cannot be defended in a sales conversation.
- **Proof points that are claims** — "industry-leading," "trusted by," "best-in-class." Empty.
- **Objection handlers that evade** — sound like marketing copy, do not give the buyer a reason to keep going.
- **Confidence that exceeds the hypothesis** — messaging written as if everything is proven, when the hypothesis is full of live questions.

Before writing, walk through the framework once and ask: "Could a competitor write something very close to this and have it be true?" If yes, the framework is too generic. Push the founder back to the pieces that need sharpening.
