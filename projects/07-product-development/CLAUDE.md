# Project 07 — Product Development & Engineering

## Purpose

This is where planning becomes building. You arrived here with a PRD, an epic list, and a roadmap from Project 06. This project does not write code — it produces the structured inputs that whoever *does* write the code (an AI coding agent like Claude Code, a contract engineer, or a small team) needs in order to build the right thing the first time. The quality of what ships is directly proportional to the quality of the requirements, the rigor of QA, and the discipline of UX review. Project 07 is where you enforce all three.

By the end of this project for any given epic, you will have an implementation-ready requirements document (functional, non-functional, acceptance criteria, edge cases, dependencies), a canonical tech stack reference that every downstream decision is grounded in, a QA report that tells you whether the build cleared the bar, and a UX review report that flags both heuristic violations and brand-identity drift. The cycle repeats per epic. This project is **not** where you revise the PRD (that is Project 06) and **not** where you collect user feedback on a shipped build (that is Project 08). It is specifically about the hand-off from planning to building, and the verification that the build matches the plan.

## Prerequisites

Complete **Project 06** (product management — produces `product-overview.md`, `epic-list.md`, and `roadmap.md`). The skills here load those files as ground truth. `epic-requirements-builder` will refuse to run if `epic-list.md` is missing or empty, and will tell you to run Project 06's `epic-definer` first.

**Project 03** (brand identity — produces `brand-identity.md`) is recommended but not required. `ux-design-reviewer` soft-degrades when `brand-identity.md` is missing: it still performs heuristic review but flags brand-adherence review as deferred.

## Global Context Files

**Loads:** `product-overview.md`, `founder-profile.md`, `brand-identity.md` (when available)

**Writes:** none — all outputs are project-scoped. (Project 07 does not push anything back to `global/context/`. The canonical artefacts produced here — `tech-stack.md`, epic requirements, QA reports, UX reviews — live inside this project and are read by downstream skills *within* Project 07 only.)

**Cross-project reads:** `projects/06-product-management/outputs/epic-list.md` and `projects/06-product-management/outputs/roadmap.md` are read directly by `epic-requirements-builder`.

## How This Project Works

Skills in this project fall into three groups:

1. **Setup (run once)** — `tech-stack-advisor` runs before the first epic and produces `outputs/tech-stack.md`, the canonical reference for the frontend, backend, database, auth, hosting, and third-party services the product will use. Every downstream skill reads it. Re-run only when a stack decision materially changes.
2. **Per-epic (iterate)** — `epic-requirements-builder` is the first skill per epic. It drills one epic from `epic-list.md` into a full requirements document. `qa-reviewer` and `ux-design-reviewer` run after the epic is implemented and evaluate the build against those requirements.
3. **Implementer mode** — every per-epic skill asks once at the start which implementer will be building: a coding agent (Claude Code, Cursor, etc.) or a human engineer/small team. The output format branches based on the answer. Agent mode produces context-loading briefs and machine-checkable acceptance criteria; human mode produces story-point prompts and handoff notes.

All skills are conversational. They ask you one question at a time, ground every recommendation in the global context and your tech stack, and show you a preview of any file before writing it. You always have the final say.

**Iteration is expected.** Your first epic requirements doc will miss an edge case. Your first QA report will catch something the requirements didn't anticipate. Feed those learnings back — update the requirements doc if the gap was in the plan, update the epic in Project 06 if the gap was in scope. The skills are designed to be re-run.

## Skills

| Skill | Description |
|---|---|
| `tech-stack-advisor` | Conversationally work through frontend, backend, database, auth, hosting, observability, and AI provider decisions. Produces `tech-stack.md`, the canonical stack reference read by every downstream skill |
| `epic-requirements-builder` | Take one epic from `epic-list.md` and drill it into a full requirements document — functional, non-functional, acceptance criteria, edge cases, dependencies, out-of-scope. Branches on implementer mode (coding agent vs human) |
| `qa-reviewer` | Evaluate an implementation against the matching epic requirements document. Accepts a pasted diff, PR URL content, or feature description. Produces a structured QA report with a sign-off recommendation (ship / fix-and-re-review / block) |
| `ux-design-reviewer` | Evaluate a screen, flow, or screenshot against UX heuristics and `brand-identity.md`. Produces a UX review report with specific, actionable fixes. Soft-degrades without brand identity |

## Recommended Flow

**Setup (once per product):**
1. **`tech-stack-advisor`** — run this before the first epic. Expect 45–90 minutes. Produces `outputs/tech-stack.md`. Re-run only when a stack decision materially changes (e.g., swapping databases, changing auth providers).

**Per epic (in order):**
2. **`epic-requirements-builder`** — first skill per epic. Pick one epic from `epic-list.md` and drill it. Expect 30–60 minutes per epic. Produces `outputs/epic-requirements/epic-NN-requirements.md`.
3. **Implementation happens outside this project** — you hand the requirements doc to your coding agent or engineer. Come back when there is something to review.
4. **`qa-reviewer`** — after the build is done. Paste the diff (agent mode) or build notes (human mode). Produces `outputs/qa-reports/epic-NN-qa-<date>.md`.
5. **`ux-design-reviewer`** — if the epic shipped anything with a UI. Describe the screen or paste a screenshot. Produces `outputs/ux-review-reports/epic-NN-ux-<date>.md`.

If the QA or UX reports recommend changes, fix them and re-run the corresponding reviewer — do not sign off on a partial pass.

## Outputs

All saved in `projects/07-product-development/outputs/`:

- `tech-stack.md` — Canonical stack reference (from `tech-stack-advisor`)
- `epic-requirements/epic-NN-requirements.md` — Per-epic requirements documents (from `epic-requirements-builder`)
- `qa-reports/epic-NN-qa-<YYYY-MM-DD>.md` — QA review reports (from `qa-reviewer`)
- `ux-review-reports/epic-NN-ux-<YYYY-MM-DD>.md` — UX review reports (from `ux-design-reviewer`)

This project does not write to `global/context/`. Everything stays project-scoped.

## Validation

This project is in a workable state when:

- `tech-stack.md` exists and names specific frontend, backend, database, auth, hosting, and AI provider choices (not just categories).
- At least one `epic-NN-requirements.md` exists and contains functional requirements, non-functional requirements, acceptance criteria (numbered), edge cases, dependencies, and an implementer-mode section (Coding Agent Brief or Engineering Handoff).
- For each implemented epic, a matching QA report exists with a sign-off recommendation and specific line references to requirements that passed or failed.
- For each implemented epic with UI work, a matching UX report exists citing at least one heuristic and one brand-adherence check (or an explicit deferred-brand-review note).

A good Project 07 outcome is one where every shipped epic has a paper trail: the requirements, the QA, and the UX review. When something breaks in production three months later, you want to be able to look back and see what was specified, what was tested, and what was reviewed. Thin requirements and skipped reviews are the fastest way to ship bugs and brand drift into the product.

**Note on scope:** This project does not write code, run builds, or execute tests. Claude Code can do all of those directly when invoked in a code repo — but the skills here are for the *founder's* planning and review workspace, not the engineering repo. Keep the engineering work in whatever repo your product lives in; keep the review artefacts here.

---

## Don't See What You Need?

The skills in this project cover the most common tasks for this stage, but they are not exhaustive.
If you need a capability that isn't covered, Claude Code includes two native built-in tools for this:

- **Skill creator** — Claude Code's built-in skill authoring tool. Use it to create a new custom skill
  and save it in this project's `.claude/skills/` directory (project-only) or in the root
  `.claude/skills/` directory (available across all projects).
- **MCP builder** — Claude Code's built-in MCP server builder. Use it if you want to connect
  Claude Code to an external tool or API. This is an advanced option most relevant when you want
  to integrate a project tracker (Linear, Jira), a version-control host (GitHub, GitLab), or an
  observability platform directly into the project.

Custom skills and MCP servers you create will live in your private fork and will not affect
the upstream repo. If you build something you think would benefit other founders, see CONTRIBUTING.md
for how to suggest it.
