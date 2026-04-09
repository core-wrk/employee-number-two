# Validation Evidence Rubric

This is an internal reference for the `hypothesis-refiner` skill. It defines how to classify each assumption after research as validated, directionally supported, invalidated, or still unknown. **Do not show this document to the founder.** Use it to push back on both premature certainty and premature abandonment.

---

## The Four Classifications

### Validated
Use when:
- Multiple independent research findings support the assumption
- At least one finding is rated Strong (per the signal-strength rubric in other skills)
- The findings come from more than one source type (e.g., Reddit + competitor review quotes, not just Reddit)
- There is no contradicting evidence from equally credible sources

**Rare rating.** Most assumptions do not reach Validated after a single research cycle. Validation usually requires direct customer conversations (Project 08), not just secondary research.

If the founder wants to mark an assumption Validated, check these criteria carefully. If any are missing, downgrade to Directionally Supported.

### Directionally supported
Use when:
- Some research findings support the assumption
- The findings are moderately credible but not overwhelming
- There is no strong contradicting evidence
- The founder's working belief is consistent with what was found

**This is the most common rating** after a single research cycle. It means "the available evidence is consistent with this assumption, and we are proceeding on it as a working belief while remaining open to being wrong."

Directionally supported assumptions stay in the refined hypothesis but are tagged as such. Downstream projects should treat them as live assumptions to test further, not as settled facts.

### Invalidated
Use when:
- Multiple research findings directly contradict the assumption
- At least one finding is rated Strong
- No countervailing findings support the original assumption
- The founder can see the evidence and does not dispute it

**High bar.** One weak contradicting finding is not enough to invalidate an assumption. Push back on the founder if they want to declare an assumption dead based on thin evidence — the research may have been looking in the wrong place.

Invalidated assumptions are rewritten in the refined hypothesis. The old version is preserved in the `hypothesis-validation-report.md` so the audit trail is clear.

### Still unknown
Use when:
- The research did not meaningfully touch the assumption
- The evidence is conflicting and cannot be resolved without more research
- The assumption is about customer behavior that only direct conversations will reveal

**The honest rating for many assumptions.** Most founders are uncomfortable with "still unknown" and want to pick validated or invalidated. Push back on that — honesty about what is unknown is more valuable than false certainty.

Still-unknown assumptions stay in the refined hypothesis, tagged as live questions, and are carried forward into the "Unresolved Questions" section for Project 08 (user testing) or Project 05 (sales conversations) to address.

---

## Decision Tree

For each assumption:

1. **Is there any research that bears on this at all?**
   - No → Still unknown
   - Yes → continue

2. **Is the research supporting or contradicting?**
   - Mostly supporting → continue to question 3
   - Mostly contradicting → continue to question 4
   - Mixed / both → Still unknown (or Directionally supported if the preponderance leans one way, clearly noted)

3. **How strong is the supporting evidence?**
   - Multiple findings across multiple source types, at least one Strong → Validated
   - Some findings, moderate strength → Directionally supported
   - Weak or single-source → Directionally supported with a caveat note

4. **How strong is the contradicting evidence?**
   - Multiple findings across multiple source types, at least one Strong → Invalidated
   - Some findings, moderate strength → Directionally supported (still, but with the contradiction noted) — do not invalidate on moderate evidence alone
   - Weak or single-source → Still unknown, with the contradiction flagged for further research

---

## Common Mistakes

### Mistake: Confirmation bias leads to Validated
The founder wants the assumption to be true. They see two supporting findings and declare it validated. Push back: "Two findings, both from Reddit, both from the same week — is that enough to settle this?"

### Mistake: Demoralization leads to Invalidated
The founder is tired, the research was harder than expected, and they are tempted to just kill the assumption and simplify. Push back: "The research did not find strong evidence either way — that is a 'still unknown,' not a 'no.'"

### Mistake: Confusing absence of evidence with evidence of absence
The founder searched for evidence and did not find much. That does not mean the thing is not true — it means the research did not surface it. The question is whether the research *would have surfaced it if it were true*. If yes, then absence of evidence is evidence. If no, then the assumption is still unknown.

Example: "People in this role complain about this problem" — if `reddit-researcher` scanned the right subreddits with the right queries and found nothing, that is probably evidence the complaints are not there, i.e., evidence of absence. But if the research was light, it is just absence of evidence.

### Mistake: Treating the ICP shift as an invalidation
Sometimes the research shows that the target customer is not who the founder thought, but the underlying problem is real. That is not an invalidation of the assumption "the problem is painful" — it is a refinement of the target customer. Do not invalidate the wrong assumption.

### Mistake: Treating everything as Validated because the competitor analysis showed "competitors exist"
Existence of competitors validates that the problem space is real, but not that any specific assumption about the problem, customer, or solution is correct. Be specific about which assumption each piece of evidence supports.

---

## How to Use in the Conversation

When classifying an assumption with the founder, narrate the rubric to them in plain terms. Example:

> "Looking at the evidence: we have one Strong finding from the Reddit research and two Moderate findings from the competitor gap analysis. The Strong finding is a direct quote from a RevOps person describing exactly the pain you hypothesized. The Moderate findings are user complaints about Lessonly that align with the assumption. That's enough for 'Directionally supported' — the evidence is consistent with your assumption, but it is not overwhelming. To get to 'Validated' we would need to see this come up in customer interviews, which is Project 08's job. Does that feel right?"

This narration:
- Makes the reasoning explicit
- Gives the founder a chance to push back
- Teaches the founder how to think about evidence strength
- Keeps the rating honest

Do not just announce a classification — walk through the reasoning so the founder can agree or disagree.
