# PRD Anti-Patterns

Internal reference used by `prd-builder`. Catalogs the common failure modes in PRDs and how to surface them during the conversation. The skill should actively look for these patterns and push back when it sees them.

## 1. Feature Soup

**Symptom:** Section 8 (Functional Requirements) reads like a Jira backlog — 40 bullets, no grouping, no priority, no tie to user stories.

**Why it happens:** Founder is writing down everything prospects have ever asked for.

**Fix:** Force grouping by pillar. Every functional requirement must trace to a user story in Section 7. Orphan requirements get cut or moved to an "Ideas Not in Scope" appendix.

## 2. No Non-Goals

**Symptom:** Section 5's "Non-Goals" subsection is empty or lists things like "we won't be slow."

**Why it happens:** Writing down a non-goal feels like closing a door.

**Fix:** Apply the non-goal force from `scope-gate-rubric.md`. For every goal, demand a paired non-goal. Surface common non-goals (SMB, mobile, self-serve, i18n) to prime the pump.

## 3. Metrics Without Baselines

**Symptom:** "Increase activation." "Improve retention." "Grow MRR."

**Why it happens:** Founder is in strategic mode, hasn't operationalized.

**Fix:** Apply the instrumentation check from `success-metrics-patterns.md`. Every metric needs a number today and a target number in 12 months. If the number today is unknown, instrument it before accepting the metric.

## 4. JTBD Masquerading as Capability List

**Symptom:** Section 4 reads: "Users want reporting. Users want integrations. Users want a dashboard."

**Why it happens:** Founder is describing what the product has, not what the buyer is trying to do.

**Fix:** Reframe every capability as a JTBD. "When [buyer] at [company shape] needs to [specific situation], they hire this product to [specific outcome]."

## 5. Hidden #1 Risk

**Symptom:** Section 11 has a flat list of 8 risks with no ranking.

**Why it happens:** Founder doesn't want to call out the biggest risk because it makes the product sound fragile.

**Fix:** Force a ranking. Ask: "If you had to pick the one thing that, if wrong, breaks the product — which is it?" That is the #1 risk. Name it explicitly at the top of Section 11.

## 6. Assumptions Written as Facts

**Symptom:** Section 2 or 4 contains statements like "Buyers need this because they currently do X manually" — with no evidence link.

**Why it happens:** Founder has an intuition and is stating it as truth.

**Fix:** Every statement in the PRD that isn't directly sourced from `icp.md`, `competitive-landscape.md`, waitlist data, or discovery calls becomes an assumption in Section 10. Rewrite the PRD body to say "We believe" or "Discovery calls suggest" for unverified claims.

## 7. Pillar Inflation

**Symptom:** The PRD has 8+ pillars in Section 7.

**Why it happens:** Every feature area gets its own pillar.

**Fix:** Collapse to 3–5 pillars. Pillars are capability categories, not features. If two pillars have overlapping stories, they are one pillar. If a pillar has 0 stories, it is aspirational and gets cut.

## 8. NFR Aspiration Wall

**Symptom:** Section 9 reads: "SOC 2 compliance. HIPAA. 99.99% uptime. <50ms p99 latency. WCAG AAA. 40 languages."

**Why it happens:** Founder copied NFRs from an enterprise RFP.

**Fix:** Ask which NFRs are real for the current stage and which are aspirational. Keep the real ones as requirements; move the aspirational ones to a "Future NFRs" subsection so they are captured but not implied to be in scope.

## 9. Competitor Invisibility

**Symptom:** Appendix (Competitive Reference) is empty or generic ("competitors exist, we're better").

**Why it happens:** Founder is avoiding the comparison because the differentiation is thin.

**Fix:** Name at least 2 competitors from `competitive-landscape.md`. For each, write the one-line delta. If the founder can't articulate the delta, that is a critical finding that belongs in Section 10 as a top-3 assumption.

## 10. User Story Generics

**Symptom:** "As a user, I want a better experience, so that I'm happier."

**Why it happens:** Founder is writing stories without a specific persona in mind.

**Fix:** Apply `user-story-guide.md`'s three specificity tests. Role, action, and outcome all specific, or the story gets rewritten.

## 11. 6-Month-Scope, 18-Month-Math

**Symptom:** The PRD has 5 P0 goals, 6 pillars, 22 user stories — and the founder says "we'll ship this in 6 months."

**Why it happens:** Founder is conflating ambition with plan.

**Fix:** Surface the gap explicitly. "A PRD at this scope is 12–18 months of engineering for a team of 3. Either the scope cuts in half, or the timeline doubles, or the team grows. Which is it?" Make the trade-off visible, then have them choose.

## 12. Missing Assumption–Scope Links

**Symptom:** Section 10 has assumptions but they don't link to goals, stories, or requirements.

**Why it happens:** Assumptions were collected at the end rather than surfaced as scope decisions happened.

**Fix:** Every assumption must have a "Linked Scope" column entry. Rework Phase 9 of the flow — assumptions get captured *during* scope decisions, not after.

## 13. Product-Overview Drift

**Symptom:** The product-overview's headline value prop doesn't match the PRD's Section 1 summary.

**Why it happens:** The overview was written as an afterthought.

**Fix:** The overview is extracted from the PRD, not written separately. If they diverge, the PRD is the source of truth — rewrite the overview. If the founder pushes back, revisit the PRD summary.

## 14. Stage Inflation

**Symptom:** Overview Section 8 says "beta" but the product has no users.

**Why it happens:** Founder wants to sound further along than they are.

**Fix:** Apply the honest stage definitions:
- **pre-alpha:** No working product; design partner conversations only
- **alpha:** Working product, <5 friendly users giving feedback
- **beta:** Working product, 5–50 paying or paid-pilot users
- **GA:** Generally available, self-serve or sales-assist motion live

If the current state doesn't match the founder's label, use the honest one. Overbooked stage labels mislead downstream projects.

## 15. The Perfect-PRD Trap

**Symptom:** Founder keeps refining; PRD goes through 5 revisions in 2 weeks; nothing downstream moves.

**Why it happens:** PRD becomes a procrastination artifact.

**Fix:** After Phase 11, tell the founder the PRD is a living document and `assumption-tracker.md` is where ongoing discoveries land. Ship the v1 PRD as "draft" status and move on. Good PRDs get revised after contact with reality, not before.