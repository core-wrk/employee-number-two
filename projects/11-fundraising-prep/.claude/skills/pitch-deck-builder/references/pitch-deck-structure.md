# Pitch Deck Structure

A slide-by-slide reference for `pitch-deck-builder`. Covers the standard 12–16 slide seed/pre-seed deck with stage-specific variants and order-swap guidance.

The deck is a narrative artifact with visual support, not a feature tour. Each slide lands one claim; together they answer: "why this, why now, why you, and what are you asking for?"

---

## Slide order: the default arc

1. Title
2. Opening hook
3. Problem
4. Insight (why now)
5. Solution
6. Product (demo or wedge)
7. Business model
8. Market (TAM/SAM/SOM)
9. Competition
10. Traction
11. Go-to-market
12. Team
13. Ask / use of funds
14. (optional) Appendix

Target length: **12–16 slides in the main deck**, plus appendix. Longer decks don't get read; shorter decks leave gaps.

---

## Per-slide reference

### 1. Title

**Purpose:** name the company, tag the category, and set expectations.

**One claim:** "This is the [X] for [Y]."

**Evidence required:** none.

**Failure modes:**
- Clever taglines that obscure what the company does
- No stage / round context
- Stock imagery that could belong to any company

**Stage variants:**
- Pre-seed: include founder name + contact; round context optional
- Seed: include round stage (e.g., "seed 2026") and ideally a traction headline

---

### 2. Opening hook

**Purpose:** earn the next 10 minutes of attention.

**One claim:** "Something is changing in the world that makes this company possible *now*."

**Evidence required:** a specific trend, data point, regulatory shift, or cultural moment — not a platitude.

**Failure modes:**
- Generic macro openings ("AI is changing everything")
- Statistics without sources
- Leading with company features

**Stage variants:**
- Pre-seed: founder insight often doubles as the hook
- Seed: traction data point can be the hook ("went from $0 to $30K MRR in 90 days")

**Order swap:** Pre-seed decks with thin traction should lead with insight, not hook-as-traction. Seed+ decks with real traction can lead with that instead.

---

### 3. Problem

**Purpose:** make the pain concrete and specific to a named buyer.

**One claim:** "[Specific ICP segment] experiences [specific pain] and currently does [specific suboptimal workaround]."

**Evidence required:** founder-interview quote, named design partners describing the pain, or observable market signal.

**Failure modes:**
- Problem too generic ("small businesses need better software")
- Problem solves for investor curiosity, not buyer reality
- Claiming pain without citing a specific buyer's voice

**Stage variants:**
- Pre-seed: quote a specific target user even if not yet a customer
- Seed: quote a specific paying customer

---

### 4. Insight (why now)

**Purpose:** explain why this problem is solvable *now*, when it wasn't 3 years ago, and won't be in a year if someone else moves first.

**One claim:** "A specific change (technology, regulation, behavior, infrastructure) makes this company possible now."

**Evidence required:** the named change with dates and consequences.

**Failure modes:**
- "AI got good" as insight (too generic)
- Insight that applies to the whole category, not this specific wedge
- Timeless insight (the problem has always existed → urgency question unanswered)

**Stage variants:**
- Pre-seed: insight carries more weight; this is often the single most important slide
- Seed: insight still matters but traction can partially substitute

**Order swap:** Some decks merge problem + insight; for pre-seed it's often better to keep them separate so insight gets its own moment.

---

### 5. Solution

**Purpose:** state what you built and the *mechanism* by which it solves the problem.

**One claim:** "[Product] is [category] that works by [specific mechanism], and that changes [specific outcome]."

**Evidence required:** grounded in `product-overview.md`. Do not promise features not built.

**Failure modes:**
- Feature list instead of mechanism
- Solution that doesn't map 1:1 to the problem stated
- Overclaiming (describing a roadmap as if shipped)

---

### 6. Product (demo or wedge)

**Purpose:** prove the solution is real, not a deck.

**One claim:** "Here is the specific wedge we're shipping / have shipped."

**Evidence required:** screenshots, short demo video frame, or architecture diagram. Be specific about what's live vs. in development.

**Failure modes:**
- Product screenshots that look like generic SaaS (no specificity)
- Mocks presented as live product
- Five screens when two would do

**Stage variants:**
- Pre-seed: sometimes a concept sketch is appropriate; label as such
- Seed: must show real product; live demo often replaces this slide in meetings

---

### 7. Business model

**Purpose:** show how this makes money.

**One claim:** "We charge [who] via [mechanism] at approximately [price point]."

**Evidence required:** reference `pricing-model.md`. Cite a concrete anchor price for at least one tier.

**Failure modes:**
- "Freemium + enterprise" with no specifics
- Multiple revenue streams presented equally (investors want one primary)
- Pricing disconnected from market comparables

---

### 8. Market (TAM/SAM/SOM)

**Purpose:** show the market is large enough to matter, with a defensible number you can answer questions on.

**One claim:** "Bottoms-up SOM of ~$X in the next 3–5 years; SAM of $Y; TAM of $Z with assumptions."

**Evidence required:** see `tam-sam-som-guide.md`. Must use bottoms-up for SOM; top-down only as sanity check.

**Failure modes:**
- Copied analyst TAM ("$1.2T market per Gartner")
- Mismatched ICP-to-market (citing global market when ICP is US SMB)
- Single number without range or assumptions
- SOM that's a % of TAM with no methodology

**Stage variants:**
- Pre-seed: range is acceptable; confidence may be low but assumptions must be explicit
- Seed+: tighter numbers expected; show bottoms-up math

---

### 9. Competition

**Purpose:** demonstrate you've done the work and can position honestly.

**One claim:** "Competitors exist; here's how we're differentiated on a dimension that matters to buyers."

**Evidence required:** reference `competitive-landscape.md`. Show real alternatives (including "do nothing" / "build in-house" / "spreadsheets").

**Failure modes:**
- "We have no competitors" (either false or category-dead)
- 2x2 matrices where you conveniently occupy the winning quadrant
- Ignoring incumbent alternatives (Excel, email, manual processes)
- Listing competitors without differentiation dimensions

**Stage variants:**
- Any stage: avoid dunking on named competitors; investors often know them
- Seed+: show specific win patterns (where you beat a named competitor in a deal)

---

### 10. Traction

**Purpose:** show momentum with honest evidence.

**One claim:** "Here is specific, verifiable progress since start."

**Evidence required:** see `social-proof-framing.md`. Use the evidence hierarchy (revenue > signed contracts > LOIs > paid pilots > waitlist > interviews).

**Failure modes:**
- Vanity metrics (waitlist size, downloads) without conversion
- "$2M pipeline" without methodology
- Logos without describing the actual relationship
- Charts that hide the y-axis starting point

**Stage variants:**
- Pre-seed: this slide is often thin — replace with "early signal" (interviews, design partners committed)
- Seed: paid pilots or revenue required; show trend
- Post-seed: show trajectory and retention

**Order swap:** If traction is strong, promote it earlier (after hook); if thin, keep it late.

---

### 11. Go-to-market

**Purpose:** show you know how to get to customers repeatably.

**One claim:** "Our first channel is [specific], with evidence of [CAC / conversion / other unit economics if available]."

**Evidence required:** specific acquisition motion with at least directional numbers.

**Failure modes:**
- "Content + community + paid" (three vague channels beats zero, but barely)
- Go-to-market that requires capabilities the team doesn't have
- Channel claims without evidence (e.g., "viral growth" with no viral mechanic)

**Stage variants:**
- Pre-seed: one identified channel with a hypothesis is enough; honesty about being pre-channel-validated is OK
- Seed: one channel with evidence of traction; speculation about second channel is fine

---

### 12. Team

**Purpose:** show the specific people who can execute this specific plan.

**One claim:** "This team has [specific combinations of experience] that map to [specific needs of this company]."

**Evidence required:** roles, directly relevant past work, why-this-team-for-this-problem.

**Failure modes:**
- Logo soup (lots of impressive former employers, no specific relevance)
- Over-weighting advisors (advisors belong in the appendix at most, not on the team slide)
- Missing key skill visible in the rest of the deck ("we're building enterprise SaaS but no enterprise sales experience on the team")

**Stage variants:**
- Pre-seed: often the most important slide; insight + team carries most of the weight
- Seed: traction and GTM carry more; team gets tighter treatment
- Any stage: name specific gaps and how the round closes them

---

### 13. Ask / use of funds

**Purpose:** state the specific ask and what the money buys.

**One claim:** "Raising $X to reach [specific milestone] in [specific time]."

**Evidence required:** milestone must map to the round size. Usually: get to Y ARR, ship Z, hire N.

**Failure modes:**
- Ask without specific milestone ("raising $3M for growth")
- Milestone that doesn't justify the round size
- Ambiguity about stage (pre-priced SAFE vs priced round)
- Use-of-funds pie chart with "other" > 10%

**Stage variants:**
- Pre-seed: SAFE round; cap and structure stated
- Seed: priced round often; state round size and target close date

---

### 14. Appendix (optional)

**Purpose:** pre-emptive answers to common diligence questions.

**Typical content:**
- Unit economics detail
- Cohort retention data
- Deeper competitive matrix
- Team bios (long form)
- Roadmap (but label as roadmap, not shipped)
- Traction drill-downs
- Hiring plan

Do not assume appendix will be read; the main 12–13 slides must stand alone.

---

## Order-swap decision tree

Default order above. Swap based on what's strongest:

**If traction is strong:** Title → Hook (traction-as-hook) → Problem → Insight → Solution → Product → Traction (second moment) → Market → BM → Competition → GTM → Team → Ask.

**If insight is the differentiator (typical pre-seed):** Title → Hook (insight) → Problem → Insight (expanded) → Solution → Product → Team (promoted) → Market → BM → Competition → Traction (what exists) → GTM → Ask.

**If team is the differentiator (repeat exits, rare domain):** Title → Hook → Team (promoted to slide 3) → Problem → Insight → Solution → Product → BM → Market → Competition → Traction → GTM → Ask.

**If market is contested but wedge is sharp:** Title → Hook → Problem → Insight → Solution → **Wedge** (new slide 6 — what we ship first and why that specific wedge is dominant) → Product → BM → Market → Competition → Traction → GTM → Team → Ask.

---

## General deck principles

- **One claim per slide.** If a slide carries two claims, split it.
- **Every number has a source.** No unsourced statistics.
- **No feature tours.** Investors are not buyers; feature depth belongs in the demo, not the deck.
- **Language matches `brand-voice.md`** when present. Generic VC-speak when `brand-voice.md` is absent, but flag the gap.
- **Every slide passes the "would a skeptic grant this claim?" test.** If not, weaken the claim or strengthen the evidence.
- **The deck's job is to get the next meeting.** Not to close the deal. Leave room for the conversation.
