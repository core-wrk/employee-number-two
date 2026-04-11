# Design Partner Agreement Skeleton

This is an internal reference for the `design-partner-advisor` skill. It is the conceptual structure of a design partner agreement — **not a legal document**. The founder takes the output to a qualified attorney for legal drafting. **Do not show this document to the founder.** Use it to scaffold the agreement section of the design partner framework with the right components.

---

## Why This Is Conceptual Only

The `design-partner-advisor` skill must not produce legal language. Reasons:

1. **Legal liability.** Producing legal language creates an expectation of legal validity. Founders who sign agreements drafted by an AI face unknown enforceability problems.
2. **Jurisdictional variance.** Contract law varies significantly by jurisdiction (US state law, EU, UK, etc.). A conceptual framework works everywhere; actual legal language does not.
3. **Relationship primacy.** Design partnerships at this stage are 80% relationship and 20% contract. Trying to legal-engineer the relationship is a warning sign that the founder doesn't trust the partner (or vice versa).

The conceptual skeleton below captures the **components** a design partner agreement needs. The founder and the founder's lawyer translate these components into legal language appropriate for the founder's jurisdiction, entity structure, and risk tolerance.

---

## The 7 Components

Every design partner agreement, regardless of jurisdiction, needs these 7 components. They are the conceptual load-bearing structure.

### 1. Scope

**What it captures:**
- What product/feature/capability the partnership covers
- What use case the partner will engage with
- What is explicitly OUT of scope (to prevent scope creep)

**Conceptual template:**

> The Design Partnership covers [specific product/capability]. The Partner will engage with it in the context of [specific use case — department, workflow, team]. Out of scope: [anything the partner might expect to be included that isn't — other products, other features, other teams within their company].

**Why it matters:** Without clear scope, the partner's expectations drift. "Oh, will the partnership also cover our other tool?" becomes a constant negotiation.

### 2. Term

**What it captures:**
- How long the partnership lasts
- Renewal conditions (if any)
- What happens when the term ends

**Conceptual template:**

> The Design Partnership lasts [X months] from [start date]. At the end of the term, the relationship converts to [normal paying customer / extended partnership / ends entirely]. The Partner may exit early with [N days] notice. The Founder may exit early with [N days] notice.

**Typical term:** 6–12 months is most common. Shorter terms (3 months) don't give enough time to see real product shaping happen. Longer terms (18+ months) trap the founder into obligations that may no longer serve them.

**Why it matters:** Open-ended partnerships become permanent. A term forces both parties to evaluate whether to continue at a specific point.

### 3. IP Assignment

**What it captures:**
- Who owns the product and any improvements made during the partnership
- Who owns the partner's data
- What happens to IP if the partner suggests a feature that gets built

**Conceptual template:**

> The Founder owns the Product, including all improvements, features, and capabilities developed during the partnership, regardless of whether the Partner suggested or requested them. The Partner retains all rights to the Partner's own data, processes, and business information. The Partner grants the Founder a limited license to use anonymized learnings from the partnership in public communications.

**The key principle:** The partner does not get co-ownership of the product, even if they shaped it. Their influence is compensated by the other terms (founder attention, pricing, access), not by equity in the product itself.

**Why it matters:** Without this clause, ambiguity about "who owns the feature we built together" becomes a lawsuit waiting to happen. Name it explicitly.

### 4. Confidentiality

**What it captures:**
- What is confidential between the parties
- What can be discussed publicly
- Specific carve-outs for the founder's right to share learnings

**Conceptual template:**

> Both parties treat as confidential: product roadmap specifics, internal metrics, unreleased features, business strategy discussed in partnership meetings.
>
> Both parties may publicly share: the existence of the partnership (after [N] days from start date), aggregate learnings, general observations about the category, quotes approved by the other party.
>
> The Founder specifically retains the right to publicly discuss what was learned from the partnership in anonymized form, including in blog posts, conference talks, and investor updates, provided no specific confidential details are disclosed.

**Why it matters:** The founder's right to share learnings is the key asymmetry to preserve. A design partnership where the founder can't talk about what they learned is a drain, not a learning vehicle.

### 5. Pricing / Economic Terms

**What it captures:**
- The pricing concession offered
- The duration of the concession
- What happens at the end of the concession (transition to normal pricing)

**Conceptual template:**

> During the Partnership Term, the Partner will receive: [specific pricing — free, percentage discount, etc.]. At the end of the Partnership Term, the Partner's pricing transitions to [grandfathered design-partner rate / standard customer pricing / negotiated rate]. The Partner has [N days] to cancel without penalty if the post-partnership pricing is not acceptable.

**Typical concessions:**
- Free product during the partnership term, transitioning to a lock-in rate at a specific discount off standard pricing
- 50% discount during the term, transitioning to 20% discount permanently
- Usage-based free tier with caps, transitioning to paid at end of term

**Why it matters:** Pricing concessions without a clear transition become "free forever" by default. Partners forget and founders don't renegotiate. Force the transition explicitly.

### 6. Success Criteria (For Both Sides)

**What it captures:**
- What success looks like for the partner (specific outcomes they should see)
- What success looks like for the founder (specific learnings or product improvements)
- Mid-point check-ins to evaluate progress

**Conceptual template:**

> **Success for the Partner looks like:** [specific outcomes — e.g., "reduced new-hire ramp time by 25% within 6 months," "reduced onboarding-related support tickets by 50%," "confidence that the tool is worth paying for at full price after the partnership ends"]
>
> **Success for the Founder looks like:** [specific learnings — e.g., "validation that the core measurement approach resonates with VPs of Enablement at mid-market SaaS," "3–5 specific features built or refined based on partner input," "confidence that the ICP is correctly scoped"]
>
> Mid-point check-in at [month N]: Both parties evaluate whether the partnership is producing the intended outcomes. If not, both parties agree to either adjust the scope or end the partnership early without penalty.

**Why it matters:** Without defined success, the partnership drifts. Both sides start to wonder if it's working and neither knows how to tell.

### 7. Exit Conditions

**What it captures:**
- When either party can exit early
- What happens to the partner's data on exit
- What happens to pricing on exit
- What happens to the partner's influence/learnings on exit

**Conceptual template:**

> Either party may exit the partnership early with [N days] written notice. Reasons for early exit may include: scope change on the partner's side (acquisition, reorg, etc.), product pivot on the founder's side, fundamental disagreement about direction, failure to meet success criteria at the mid-point check-in.
>
> Upon exit: the Partner's data is [exported/deleted at Partner's choice]. The pricing reverts to [specified rate]. The Founder retains the right to use anonymized learnings from the partnership as specified in the Confidentiality section. The Partner retains the right to use the Founder's product under normal customer terms going forward (unless exit was due to breach).

**Why it matters:** Clean exits are what make future partnerships possible. A partnership that ends badly damages the founder's reputation; one that ends cleanly (even early) can become a case study or a reference.

---

## Length Guidance

**The full conceptual agreement skeleton should be 1–2 pages.** In a markdown file, this is maybe 500–1000 words total, with each of the 7 sections being 3–5 sentences plus a specific value for each blank.

**Signs the skeleton is too long:**
- More than 5 clauses per section
- Sub-sub-sections (1.1.1, 1.1.2, etc.)
- Attempts to cover every possible edge case
- Jurisdictional language ("the Parties hereby agree", "notwithstanding the foregoing")

**Signs the skeleton is too short:**
- Any of the 7 components is missing
- Scope is vague ("the product")
- Term is open-ended
- Exit conditions are not specified

1–2 pages is the sweet spot. It's enough to be useful for conversation alignment; short enough to not feel like legal ceremony.

---

## The "Take To A Lawyer" Disclaimer

The output must include this disclaimer prominently:

> **IMPORTANT:** This is a conceptual framework, not a legal document. Take this to a qualified attorney for legal drafting before using it in any binding way. This framework is designed to align expectations between the founder and a potential design partner in a conversation; it does not protect either party legally until it has been reviewed and drafted into a legally enforceable agreement by an attorney.

This disclaimer must appear:
1. In the output file's frontmatter or first section
2. At the top of the "Conceptual Agreement Skeleton" section
3. Again at the bottom of the skeleton before the "Exit Conditions" section

Redundancy here is appropriate — the founder is going to share this framework with prospects in a conversation, and the disclaimer needs to survive copy-paste.
