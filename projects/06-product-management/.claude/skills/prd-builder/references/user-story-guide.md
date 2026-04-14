# User Story Guide

Internal reference used by `prd-builder` for Phase 6. User stories must be specific enough that `epic-definer` can parse them into epics without additional clarification.

## Canonical Format

> As a **[specific role]**, I want to **[specific action]**, so that **[specific outcome]**.

All three slots must be filled with specifics.

## Specificity Tests

Apply these three tests to every story before accepting it into the PRD.

### Test 1: Role specificity

Is the role specific enough that you could picture one person at a specific company shape?

- ✅ "As a VP Sales Enablement at a 200-person SaaS company with 30+ quota-carrying reps"
- ❌ "As a user"
- ❌ "As a customer"
- ❌ "As a manager"

Generic roles produce generic stories. Pull from the ICP.

### Test 2: Action specificity

Can you describe what the system does in a single verb phrase without ambiguity?

- ✅ "I want to link each CRM opportunity to a ramp-cohort ID"
- ❌ "I want to track my team's performance"
- ❌ "I want better reporting"

If the action is vague, the resulting epic will be vague too.

### Test 3: Outcome specificity

Does the outcome describe a real, measurable change in the buyer's world?

- ✅ "so that I can report month-over-month ramp velocity by cohort to the CRO"
- ❌ "so that I can be more productive"
- ❌ "so that everything is easier"

Outcomes that could be pasted into any product's story are outcomes that provide no information.

## Grouping by Pillar

Stories must be grouped under the pillars established in Phase 3 of the flow. Each pillar should have 2–4 stories. If a pillar has 0 stories, the pillar is aspirational and should either get stories or be cut. If a pillar has 8+ stories, it is probably two pillars in disguise.

## Story ID Convention

Stories get IDs of the form `US-<pillar#>-<story#>` (e.g., `US-1-3` for the third story under pillar 1). IDs must be stable across PRD revisions so `epic-definer` can link epics back to stories.

## Common Failure Modes

| Failure | Example | Fix |
|---|---|---|
| "I want a dashboard" | "As a manager, I want a dashboard" | Reframe as outcome: what do they do with it? |
| Bundled stories | "I want to create, edit, delete, and share reports" | Split into separate stories |
| Implementation detail | "I want a red button that..." | Strip UI detail; keep capability |
| Missing trigger | "I want notifications" | When? What triggers the need? |
| Passive outcomes | "so that things are better" | Force a specific, named change |

## Relationship to Functional Requirements

A user story is the **why**. A functional requirement is the **what**. The story says "As a VP Sales Enablement, I want to link CRM opportunities to ramp cohorts, so that I can report cohort velocity to the CRO." The functional requirement says "The system must expose a ramp-cohort ID field on every opportunity record and allow bulk assignment via CSV import."

The PRD needs both. Stories go in Section 7; requirements go in Section 8.

## Relationship to Epics

`epic-definer` will cluster related stories into epics. Typically 3–6 stories per epic. Stories that don't cluster cleanly are either (a) their own small epic, or (b) misplaced and should move to a different pillar.

Keep the pillar → story → epic chain intact. Every epic should trace back to named stories; every story should map to exactly one epic.