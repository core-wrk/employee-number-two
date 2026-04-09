# Project 01 — Market Research & Problem Validation

## Purpose

This is where you pressure-test the hypothesis you articulated in Project 00 against real-world signal — before you build anything. The goal is not to confirm what you already believe. The goal is to find out what is actually true about the problem, the people who experience it, and what already exists to solve it.

By the end of this project you will know: which of your assumptions hold up under scrutiny, which do not, who your ideal customer actually looks like in detail, what the competitive landscape really is, and whether your working product name is viable.

## Prerequisites

Complete Project 00 (onboarding). The skills here load your founder profile and startup hypothesis and will not run if either is missing or empty.

## Global Context Files

**Loads:** `founder-profile.md`, `startup-hypothesis.md`

**Writes:** `startup-hypothesis.md` (refined), `icp.md` (v1), `competitive-landscape.md`

## How This Project Works

Skills in this project fall into three groups:

1. **Orchestration** — `research-planner` reads your hypothesis, helps you turn vague assumptions into specific testable research questions, and recommends which of the research skills to run and in what order.
2. **Research** — `reddit-researcher`, `news-analyst`, and `competitor-mapper` gather structured signal from different sources. Each produces a standalone report in `outputs/`.
3. **Synthesis** — `icp-builder` and `hypothesis-refiner` read the research outputs and synthesize them into the deliverables that propagate to `global/context/`. `naming-validator` is a focused side-task. `early-legal-checker` is a cross-cutting check that can run any time.

All skills are conversational. They ask you one question at a time, shape follow-ups based on your answers, and show you a preview of any file before writing it. You always have the final say.

## Skills

| Skill | Description |
|---|---|
| `research-planner` | Turn your hypothesis into a concrete research plan with testable questions |
| `reddit-researcher` | Find Reddit threads that express the problem, rated by signal strength |
| `news-analyst` | Survey news and trade press coverage for sentiment, momentum, and emerging players |
| `competitor-mapper` | Build a structured competitor matrix and write the competitive landscape to global context |
| `icp-builder` | Synthesize research findings into a v1 Ideal Customer Profile |
| `naming-validator` | Check candidate product names for domain, trademark, and handle conflicts |
| `hypothesis-refiner` | Walk assumption-by-assumption through what the research validated or invalidated, and refine the hypothesis |
| `early-legal-checker` | Surface IP, NDA, and data-privacy flags relevant at this stage (awareness, not legal advice) |

## Recommended Flow

**Start here:**
1. Run `research-planner` first. It is the cheapest way to find out whether your hypothesis is concrete enough to research or whether it needs more thinking first.
2. Run `early-legal-checker` once, early. It is a 10-minute check that can save you from unpleasant surprises later — especially around IP assignment if you are currently employed elsewhere.

**Gather signal (run in any order):**
3. `reddit-researcher`
4. `news-analyst`
5. `competitor-mapper`

You do not have to run all three. If your problem space has no meaningful Reddit presence, skip `reddit-researcher`. If it is a brand-new category with no press coverage, skip `news-analyst`. Use your judgment — the `research-planner` skill will have given you a recommendation.

**Synthesize:**
6. `icp-builder` — ideally after at least 2 research outputs exist, including `competitor-mapper`. The skill will run with one output but will heavily hedge its conclusions; with 2–3 outputs it produces a much sharper ICP.
7. `naming-validator` — whenever you are ready to commit to a working name. Can run in parallel with other synthesis work.
8. `hypothesis-refiner` — run last. This is the skill that closes the loop: it reads everything you produced, walks through your original assumptions one by one, and writes the refined `startup-hypothesis.md`.

## Outputs

All saved in `projects/01-market-research/outputs/`:

- `research-plan.md` — Your research questions and which skills to run (from `research-planner`)
- `reddit-research-report.md` — Signal-rated Reddit findings (from `reddit-researcher`)
- `news-sentiment-report.md` — News and trade press synthesis (from `news-analyst`)
- `competitor-analysis.md` — Detailed competitor matrix (from `competitor-mapper`)
- `icp-draft.md` — Working draft of the ICP with full research trail (from `icp-builder`)
- `naming-availability-report.md` — Name candidates with conflict status (from `naming-validator`)
- `hypothesis-validation-report.md` — Audit trail of what each research finding meant for each assumption (from `hypothesis-refiner`)
- `legal-flags-report.md` — Early-stage legal flags and questions for an attorney (from `early-legal-checker`)

And the following global context updates (written via the `context-writer` skill with preview and approval):

- `global/context/competitive-landscape.md` — Written by `competitor-mapper`
- `global/context/icp.md` — Written by `icp-builder`
- `global/context/startup-hypothesis.md` — Refined version, written by `hypothesis-refiner`

## Validation

This project is complete when:

- `global/context/competitive-landscape.md` exists and contains a substantive competitor map
- `global/context/icp.md` exists and describes a specific role, decision context, and pain profile — not just a company size
- `global/context/startup-hypothesis.md` has been refined based on research (the `hypothesis-validation-report.md` will tell you what changed)

If you get to the end and find your original hypothesis was mostly invalidated, that is a success, not a failure. The point of this project is to learn that cheaply, before you build. Equally, a refined hypothesis that is *more tentative* than the original — full of "[LIVE QUESTION]" tags and unresolved assumptions — is a successful outcome of this project, not a failed one. Project 08 (beta and user testing) is where live questions become settled, not Project 01.

---

## Don't See What You Need?

The skills in this project cover the most common tasks for this stage, but they are not exhaustive.
If you need a capability that isn't covered, Claude Code includes two native built-in tools for this:

- **Skill creator** — Claude Code's built-in skill authoring tool. Use it to create a new custom skill
  and save it in this project's `.claude/skills/` directory (project-only) or in the root
  `.claude/skills/` directory (available across all projects).
- **MCP builder** — Claude Code's built-in MCP server builder. Use it if you want to connect
  Claude Code to an external tool or API.

Custom skills and MCP servers you create will live in your private fork and will not affect
the upstream repo. If you build something you think would benefit other founders, see CONTRIBUTING.md
for how to suggest it.
