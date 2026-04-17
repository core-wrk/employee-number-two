# Structural Smoke Test Report — 2026-04-14

Executed per plan [glittery-wishing-blum.md](/Users/andrewodonnell/.claude/plans/glittery-wishing-blum.md) (Option D — structural, no skill invocations).

## Per-project inventory

| # | Project | CLAUDE.md | Skill dirs | SKILL.md files | Status |
|---|---|---|---|---|---|
| 00 | onboarding | Y | 6 | 6 | OK |
| 01 | market-research | Y | 8 | 8 | OK |
| 02 | brand-and-marketing | Y | 3 | 3 | OK |
| 03 | brand-identity | Y | 4 | 4 | OK |
| 04 | inbound-marketing | Y | 9 | 9 | OK |
| 05 | outbound-sales | Y | 7 | 7 | OK |
| 06 | product-management | Y | 3 | **0** | **FAIL** |
| 07 | product-development | Y | 4 | 4 | OK |
| 08 | beta-and-user-testing | Y | 4 | 4 | OK |
| 09 | pricing-and-packaging | Y | 2 | 2 | OK |
| 10 | legal-and-company-formation | Y | 4 | 4 | OK |
| 11 | fundraising-prep | Y | 5 | 5 | OK |
| 12 | financial-modeling | Y | 4 | 4 | OK |

**Global skills (`.claude/skills/`):** 5 dirs, only 2 have SKILL.md — `context-writer`, `web-researcher`. Missing: `context-loader`, `document-formatter`, `third-party-advisor`.

## Regressions

### REG-1: Project 06 has no invokable skills (blocker)
`projects/06-product-management/.claude/skills/` contains `prd-builder/`, `epic-definer/`, `roadmap-builder/` — each has a `references/` subdir but **no `SKILL.md`**. These skills are not invokable. Project 06 is the linchpin for `product-overview.md`, which Projects 07, 09, 11, 12 all read. Without it, the whole downstream arc breaks.

- [projects/06-product-management/.claude/skills/prd-builder/](projects/06-product-management/.claude/skills/prd-builder/)
- [projects/06-product-management/.claude/skills/epic-definer/](projects/06-product-management/.claude/skills/epic-definer/)
- [projects/06-product-management/.claude/skills/roadmap-builder/](projects/06-product-management/.claude/skills/roadmap-builder/)

### REG-2: 3 of 5 global skills missing SKILL.md
Empty dirs at:
- [.claude/skills/context-loader/](.claude/skills/context-loader/)
- [.claude/skills/document-formatter/](.claude/skills/document-formatter/)
- [.claude/skills/third-party-advisor/](.claude/skills/third-party-advisor/)

Root `CLAUDE.md` advertises these as always-available globals. Every project's CLAUDE.md references `context-loader` / `context-writer` in its onboarding flow.

### REG-3: 47 of 62 SKILL.md files lack YAML frontmatter
Only projects 09, 10, 11, 12 (the most recently built) ship `name:` / `description:` frontmatter. The other 47 files start directly with `# Skill: X`. Claude Code's skill registry falls back to the H1 header, producing generic descriptions like "Skill: Reddit Researcher" — which means **automatic skill triggering is weak**: the triage layer has no semantic text to match the user's request against.

Evidence: compare the descriptions shown in this session's skill list:
- `pricing-strategist` → "Survey viable pricing strategies against the founder's ICP..." (has frontmatter)
- `reddit-researcher` → "Skill: Reddit Researcher" (no frontmatter)

Affects every skill in projects 00–08 plus both existing global skills.

## Verified wiring (all PASS)

- 04 → 08: `beta-recruiter` references `waitlist-tracker`
- 06 → 07: `epic-requirements-builder` references `epic-list`
- 08 → 09: `pricing-strategist` references `validated-insights`
- 09 → 12: `revenue-modeler` references `pricing-model`
- 11 → 12: `scenario-planner` references `investor-prospect-list`
- 01 → 11: `investor-prospector` references `competitive-landscape`
- 02 → 11: `investor-outreach-drafter` references `brand-voice`

All cross-project text references resolve. The wiring design is intact; the gaps are in skill definition files, not in how projects reference each other.

## Global context state (informational)

Present: `founder-profile.md`, `startup-hypothesis.md`, `icp.md`, `competitive-landscape.md`

Not yet created (normal if corresponding projects haven't been run): `brand-voice.md`, `brand-identity.md`, `product-overview.md`, `pricing-model.md`, `company-profile.md`, `validated-insights.md`

## Recommended fixes (in priority order)

1. **Generate SKILL.md for all 3 Project 06 skills** — unblocks the critical path through 07/09/11/12.
2. **Generate SKILL.md for 3 missing global skills** (`context-loader`, `document-formatter`, `third-party-advisor`) — root CLAUDE.md promises them.
3. **Backfill YAML frontmatter on 47 legacy SKILL.md files** — mechanical change; copy the pattern from any Project 09–12 skill. Produces reliable auto-invocation.

## Summary

- **11 of 13 projects** structurally ready to run
- **Project 06 is broken** (blocker — blocks downstream arc)
- **3 global skills missing** (documented but unimplemented)
- **47 skills have degraded auto-triggering** (functional but weak)
- **All cross-project wiring references are intact**
