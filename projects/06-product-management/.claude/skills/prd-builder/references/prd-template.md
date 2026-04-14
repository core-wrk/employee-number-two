# PRD Template — Canonical Section Structure

Internal reference used by `prd-builder`. Defines the 13 required sections of `outputs/product-requirements-document.md` and what belongs in each. Do not show this file to the founder; use it to keep the conversation structured.

## Frontmatter

```yaml
---
schema_version: 1
generated_from: [list of context files read this session]
last_updated: YYYY-MM-DD
status: draft | approved
---
```

`schema_version` must stay at `1` unless the section structure changes in a way that breaks downstream parsers (`epic-definer`, `assumption-tracker`). Bumping the version requires updating both downstream skills and the refinement notes.

## Section 1: Summary

3–5 sentences. What the product is, who it is for, why it matters now. No jargon. A reader who knows nothing about the company should understand the product in 30 seconds.

Failure mode: multi-paragraph summaries that bury the lede. Keep it tight.

## Section 2: Problem Statement

1–2 paragraphs. Grounded in ICP and discovery-call evidence. Quote specific signals where possible ("12 of 47 waitlist signups named ramp-time attribution as their top pain").

Failure mode: generic problem statements ("sales teams struggle with productivity"). Push for specificity.

## Section 3: Target Users

Primary persona and (optionally) 1–2 secondary personas. For each:

- **Role** (from `icp.md`)
- **Company shape** (size, industry, stage)
- **Buying trigger** (the moment they start looking)
- **Where they are found** (from `icp.md`'s "Where to Find Them" section)

Failure mode: listing every possible user. Keep to 1 primary + at most 2 secondary.

## Section 4: Jobs to Be Done

3–5 JTBDs, each as one sentence in the form: "A [role] at [company shape] hires this product when they need to [specific job]."

Failure mode: capability lists disguised as JTBDs ("they want reporting"). Push for the trigger and outcome.

## Section 5: Goals and Non-Goals

**Both sides populated.** At least 3 goals. At least 3 non-goals.

- **Goal format:** "By [timeframe], [measurable outcome]." Every goal ties to evidence in `icp.md`, waitlist, or discovery calls.
- **Non-goal format:** "This product will not [scope item]. [Reason.]"

Failure mode: empty non-goals section. Force at least 3.

## Section 6: Success Metrics

Table format. Every metric has:

- **Name**
- **Baseline** (current value, or "0 — new product" for greenfield)
- **Target** (12-month target)
- **Measurement method** (how it is instrumented)

At least 3 metrics. See `success-metrics-patterns.md` for product-type templates.

Failure mode: metrics without baselines ("improve activation") or targets ("increase retention"). Push for numbers.

## Section 7: User Stories by Epic

Grouped by pillar (from Phase 3 of the flow). Each pillar has 2–4 user stories.

Story format: "As a [specific role], I want to [specific action], so that [specific outcome]."

Failure mode: vague stories ("as a user, I want a good experience"). See `user-story-guide.md`.

## Section 8: Functional Requirements

Capability-level, grouped by pillar. Not UI-level.

- ✅ "The system must allow a user to link CRM opportunities to ramp cohorts."
- ❌ "The system must have a dropdown in the top-right corner."

Failure mode: drifting into UI design. That is Project 07's job.

## Section 9: Non-Functional Requirements

Covers:
- **Performance** (latency targets, throughput)
- **Security/Compliance** (SOC 2, GDPR, HIPAA as applicable)
- **Scalability** (concurrent users, data volume)
- **Availability** (uptime target)
- **Accessibility** (WCAG target)
- **Internationalization** (languages, locales)

For early-stage products, most NFRs are aspirational. Capture them anyway so they can become decisions later.

## Section 10: Assumptions and Open Questions

Table format. Every assumption has:

- **ID** (A01, A02, ... stable across PRD revisions)
- **Assumption text** (one sentence)
- **Status** (all new assumptions start as `Unvalidated`)
- **Linked scope** (which goal, pillar, user story, or requirement this assumption backs)

At least 5 assumptions. These seed `outputs/assumption-tracker.md`.

## Section 11: Risks

Bulleted list. The **#1 Risk** must be called out explicitly — the thing that, if wrong, breaks the product.

Failure mode: a flat list of risks with no ranking. Force a #1.

## Section 12: Dependencies

External dependencies: integrations, data sources, vendor APIs, regulatory approvals, partnerships. Each dependency named and its criticality noted.

## Section 13: Out of Scope

Explicit restatement of non-goals plus anything else the PRD is NOT covering in this revision. Overlap with Section 5 is fine — the point is to make non-scope unavoidable to miss.

## Appendix: Competitive Reference

Named competitors from `competitive-landscape.md`. For each:

- Competitor name
- The relevant capability they cover
- The differentiation delta (what this product does that they do not, or vice versa)

At least 2 competitors. This is the honest ground for Section 5's goals.