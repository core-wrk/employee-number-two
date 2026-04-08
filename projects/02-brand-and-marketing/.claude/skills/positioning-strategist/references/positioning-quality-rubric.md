# Positioning Quality Rubric

This is an internal reference for the `positioning-strategist` skill. It defines what Strong vs. Weak looks like for each piece of a positioning statement, with examples drawn from the example founder's domain (sales onboarding for B2B SaaS) so the patterns are concrete. **Do not show this document to the founder.** Use it to pressure-test each piece of the positioning before writing the final document.

---

## How to use this rubric

For each piece of the positioning, compare the founder's answer against the Strong and Weak descriptions. If the answer is in the Weak column, do **not** silently rewrite it. Name the specific reason it is Weak and ask a question that would move it to Strong. The founder learns most when they fix the weakness themselves.

If a piece is genuinely between Strong and Weak — e.g., it has a Strong shape but a Weak proof — call out which part is the issue.

---

## Piece 1: Competitive Alternatives

### Strong
- Includes 5+ alternatives across direct competitors, indirect competitors, and workarounds
- Workarounds are named explicitly (spreadsheet, manual process, doing nothing, internal tooling)
- Each alternative is grounded in `competitive-landscape.md`, not invented
- The founder can articulate why each alternative is the wrong choice for the target customer — even the workarounds

**Example (Strong):** "Customers today use Mindtickle for content libraries, Second Nature for AI role-play, Gong's expanding coaching features for call review, internal Notion wikis for product knowledge, and shadow pairing with senior reps for everything else. The most common state is some combination of two or three of these, none of which actually moves ramp time."

### Weak
- 2–3 obvious incumbents only
- Workarounds excluded
- "Nothing like this exists" framing
- Alternatives the founder feels emotionally dismissive of, without naming why a specific customer would dismiss them

**Example (Weak):** "Mindtickle and Lessonly. They're old and clunky."

### Push back when
- The founder names fewer than 5 alternatives → "What do customers do today *before* they buy any tool?"
- The founder excludes workarounds → "In `competitive-landscape.md`, shadow pairing with senior reps is named as the most common workaround. Should that be in the alternatives list? It is what most companies actually do."
- The founder dismisses an alternative without naming why a specific customer would dismiss it → "Why would a VP of Sales Enablement not just buy more Mindtickle seats? What does the research in `competitive-landscape.md` say about that decision?"

---

## Piece 2: Unique Attributes

### Strong
- Each attribute is specific enough that a customer could verify whether the product actually does it
- Each attribute is something *no* alternative in the alternatives list also does (or does materially worse)
- Each attribute is grounded in either a real product capability or an explicit live question for Project 08 to validate
- Attributes use the customer's vocabulary, not marketing language

**Example (Strong):** "Grades rep responses against the company's own historical closed-won and closed-lost deal outcomes from their CRM, rather than against generic objection-handling content."

### Weak
- "AI-powered" or "data-driven" or "intelligent"
- "Easy to use" / "intuitive" / "modern"
- "Personalized" without specifying what the personalization is anchored in
- Attributes that 3+ alternatives would also claim

**Example (Weak):** "AI-powered sales coaching that's personalized for each rep."

### Push back when
- The founder uses "AI" as the differentiating attribute → "Mindtickle, Second Nature, and Gong are all AI-powered. Could any of them say what you just said? If yes, what is the specific AI capability you have that they do not?"
- The founder claims a unique attribute without specifying it → "When you say 'personalized,' personalized to what? Tied to what data?"
- The founder claims the attribute as if it is built when it is still hypothetical → "Is this attribute already implemented, or is it part of the live question in `startup-hypothesis.md`? It needs to be marked accordingly in the positioning."

---

## Piece 3: Value (and Proof)

### Strong
- Each unique attribute is paired with a specific customer benefit (not a vendor-side claim)
- The benefit is stated in terms the customer would recognize: a KPI, a job done, a pain removed
- Each value claim has an explicit proof status: VALIDATED, DIRECTIONALLY SUPPORTED, or LIVE QUESTION
- The proof references either Project 01 research outputs or the live questions tracked in `startup-hypothesis.md`

**Example (Strong):**
> Attribute: Grades responses against the company's own historical deal outcomes.
> Value: Cuts time to first deal because the rep is being trained on what actually works at this specific company.
> Proof: DIRECTIONALLY SUPPORTED — `competitive-landscape.md` shows cross-tool user complaints that "AI feedback feels generic, not tied to our deals," confirming the gap is real. Whether this specific implementation closes the gap is a LIVE QUESTION for Project 08.

### Weak
- Value stated as a vendor capability ("we deliver insights")
- Value stated without proof
- Proof claimed as VALIDATED when it has not actually been validated
- Generic outcomes like "increased revenue" or "better team alignment" without a mechanism

**Example (Weak):** "Helps reps ramp faster by leveraging AI insights." (No proof, vendor-language, no mechanism)

### Push back when
- The proof is "we believe so" → "What in Project 01 research supports that, and what is still a live question?"
- The value is stated as a vendor capability → "Restate that from the customer's perspective. What does the customer get?"
- The proof is claimed as VALIDATED but the research did not validate it → "I do not see that in `competitive-landscape.md` or `icp.md`. Where is the validation coming from? If it is the founder's intuition, that should be marked as DIRECTIONALLY SUPPORTED at most."

---

## Piece 4: Customers Who Care

### Strong
- A specific segment, narrower than the addressable market
- Anchored in `icp.md` — references the role, the situation, and the trigger
- Names *why* this segment cares more than other segments
- Acknowledges that some segments do not care, and is willing to deprioritize them

**Example (Strong):** "VPs of Sales Enablement at 100–500 person B2B SaaS companies that have already bought Gong or Chorus, where ramp time is on the CRO's 2026 OKR list. They care because the existing tools have already failed them once, and the board is now measuring them on the metric. RevOps directors at the same companies are a secondary segment with similar but slightly different motivations."

### Weak
- "Mid-market B2B SaaS companies"
- "Sales leaders"
- "Anyone who wants to ramp reps faster"
- The entire ICP, restated

**Example (Weak):** "Mid-market SaaS sales teams."

### Push back when
- The answer is the entire ICP → "The ICP describes who can plausibly buy. Who *cares enough* to switch from their current alternative? That is usually narrower."
- The answer is a company size → "Company size is not a reason to care. What situation makes this segment care more than the next segment?"
- The founder will not narrow → "Trying to serve too many segments at once is the most common positioning failure. Which segment does the research in `icp.md` support most clearly?"

---

## Piece 5: Market Category

### Strong
- A category the customer already understands
- A category that puts the product against the right competitors (not the wrong ones)
- The choice is made deliberately, with at least one alternative category considered and rejected with a reason
- The reference price for the category is appropriate to what the product can charge

**Example (Strong):** "Category: 'Deal-grounded sales onboarding,' positioned within the broader sales enablement category but explicitly differentiated from content-library tools. Considered alternatives: 'AI sales coaching' (rejected because Second Nature owns the role-play interpretation and the founder's product is not a role-play tool); 'sales call analytics' (rejected because that puts the product against Gong on Gong's home turf instead of next to it)."

### Weak
- The most obvious category, picked without considering alternatives
- A category that puts the product against the wrong competitors
- A category invented from whole cloth that the customer would not recognize
- A category whose reference price is wrong for the product (e.g., positioning a $200/seat/month product in a category where the reference price is $20/seat/month)

**Example (Weak):** "Sales enablement." (Picked because it is the obvious category. Puts the product against Mindtickle on Mindtickle's home turf, where Mindtickle has the largest content library and the founder has nothing comparable. Wrong category.)

### Push back when
- The founder picks the obvious category without considering one tier up or one tier sideways → "What other category could this live in? Why is the one you picked better?"
- The category puts the product against an incumbent the founder cannot win against on that dimension → "If the customer puts you in 'sales enablement,' they will compare you to Mindtickle's content library — and you do not have one. Is there a category that frames the comparison differently?"
- The category is invented → "Who else is in this category? If the answer is 'no one,' you are inventing a category — that is a Crossing the Chasm move and needs to be a deliberate strategic choice."

---

## "Not For" Question

This is not one of Dunford's 5 Pieces, but it is required by the `positioning-strategist` skill output. Apply the rubric:

### Strong
- At least two specific exclusions: usually a customer segment AND a use case
- Exclusions named with a reason — "we are not for X because we cannot serve Y constraint that X requires"
- Exclusions the founder is willing to actually live by, not aspirational

**Example (Strong):** "Not for: (1) early-stage startups under 50 employees — they are not yet hiring sales reps in cohorts large enough to justify a tool. (2) Pure inbound, no-rep PLG companies — there are no rep conversations to grade against. (3) Companies that do not use Gong or Chorus — the integration is the mechanism, not an option."

### Weak
- "We're not for everyone" (meaningless)
- "Enterprise customers" (without saying why or what makes enterprise wrong)
- The founder cannot name a specific exclusion

### Push back when
- The founder cannot name a single exclusion → "If you cannot name who this is not for, you have not taken a position — you have described a category."
- The founder names an exclusion that contradicts the customer-who-cares answer → Reconcile the contradiction before writing.

---

## Common Mistakes Across All Pieces

- **Confusing "differentiation" with "positioning."** Differentiation is one ingredient. Positioning is the strategic choice about who the differentiation is *for* and what category it is in. A long list of differences does not add up to a position.
- **Writing the positioning statement to sound impressive instead of to be true.** A positioning statement is an internal alignment document. Marketing copy comes later. If the founder is writing for an imaginary VC, the statement will drift away from the research.
- **Skipping live questions.** Most early-stage positioning has 1–2 pieces that are not yet proven. Marking them as LIVE QUESTION is honest and forwards them to Project 08 for validation. Hiding them creates a false sense of certainty.
- **Picking the easiest answer to the "not for" question.** Saying "not for Fortune 500" when the real exclusion should be "not for companies without Gong or Chorus" is a sign the founder is avoiding the harder strategic call.

---

## Final test before writing

Before writing the positioning statement, ask yourself: "Could a competitor named in `competitive-landscape.md` write the same statement and have it be true of them?"

If yes, the positioning is not a position — it is a category description. Do not write it. Push the founder back to the piece that is too generic.
