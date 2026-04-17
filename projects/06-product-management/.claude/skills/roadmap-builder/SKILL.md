---
name: roadmap-builder
description: Sequence a prioritized epic list into a time-phased development roadmap with milestones, dependencies, and explicit assumptions. Produces roadmap.md for execution tracking and stakeholder communication.
---

# Skill: Roadmap Builder

## Role

You take the approved epic list and sequence it into a development roadmap — a time-phased plan that shows what ships when, in what order, and with what dependencies. An early-stage roadmap is not a schedule to hit; it is a sequencing commitment that makes tradeoffs visible. It exists so the founder, a hire, and a potential investor can all look at the same document and understand what v1 is, what v1.5 adds, and what is deferred.

You do not estimate engineering velocity on the founder's behalf. You structure the sequence and surface the assumptions.

## Prerequisites

Read the following before starting:

- `projects/06-product-management/outputs/epic-list.md` — **required**.
- `projects/06-product-management/outputs/product-requirements-document.md` — **required**. Cross-check roadmap phases against PRD non-goals.
- `global/context/founder-profile.md` — optional. Solo founder vs. co-founders with hires shapes realistic cadence.
- Prior `outputs/roadmap.md` — optional on re-runs.

**If `epic-list.md` is missing, stop.** Tell the founder to run `epic-definer` first.

## Behavior

**Phase the roadmap, don't schedule it.** Use named phases ("v1 — Private Beta", "v1.5 — Public Beta", "v2 — GA Expansion") rather than calendar dates. Dates invent precision the founder does not have; phases capture sequence and dependency, which is the real commitment.

**v1 = smallest coherent shippable product.** It is defined by the P0 epics whose dependencies are satisfied inside the phase. Anything P0 that sits on a deferred dependency is a signal to re-examine priority.

**One theme per phase.** A phase with no theme is a phase that will expand. Name the theme ("v1: core onboarding + first value", "v1.5: retention") so scope decisions inside the phase are anchored.

**Make assumptions explicit.** Team size, build-vs-buy for infrastructure, time-to-first-user. These assumptions drive the sequence; surface them so the roadmap can be revised when reality diverges.

**Call out cut lines.** Every phase has a "if we hit a scope fork, cut here" annotation. This is the founder's pre-committed triage.

## Flow

### Phase 1: Read

Read the epic list, the PRD (for non-goals check), and the founder profile if present.

### Phase 2: Propose phases

Propose 3–4 phases. For each:

- **Phase name and theme**
- **Epics included** (by name from the epic list)
- **What ships at the end of this phase** (user-observable)
- **Dependencies entering the phase**
- **Key assumptions** (team, infra, third-party)
- **Cut line** (if scope slips, what gets dropped first)

### Phase 3: Review

Walk through phases with the founder. Expect revisions: an epic the founder wants earlier, a phase that tries to do too much, a cut line that feels wrong.

### Phase 4: Write

Once approved, write to `projects/06-product-management/outputs/roadmap.md`.

### Phase 5: Hand off

Tell the founder Project 06 is complete and the next project is Project 07 (product development), which reads `epic-list.md` to produce engineering specs.

## Minimum Bar

Before writing, ensure:

- Every P0 epic is placed in a phase
- Every phase has a single theme (not a grab bag)
- Dependencies between epics are respected in the sequence
- Each phase has an explicit cut line
- Assumptions are named per-phase, not hidden in prose

## Output

**Path:** `projects/06-product-management/outputs/roadmap.md`

Format: phases as H2 sections with the fields above, plus a top-of-file summary table (phase name, theme, epic count, user outcome).

## What Not To Do

- Do not invent calendar dates the founder cannot defend
- Do not stuff all P0 into v1 without checking that dependencies resolve
- Do not write phases without themes
- Do not skip cut lines — they are the reason the roadmap survives contact with reality
- Do not re-prioritize epics here; if priority needs to change, return to `epic-definer`
