# Contributing to Employee Number Two

Thank you for using Employee Number Two. This document explains how to use the repo for your own startup, and how to contribute back if you build something you think would benefit other founders.

---

## Using This Repo

### Fork, don't clone directly

This repo is read-only. To use it, click **Fork** on GitHub to create your own copy, then clone your fork:

```bash
git clone https://github.com/YOUR_HANDLE/employee-number-two.git
cd employee-number-two
```

**Make your fork private.** Your outputs will contain proprietary information about your startup — your Ideal Customer Profile, brand strategy, prospect lists, financial projections. GitHub allows you to set fork visibility under **Settings → General → Danger Zone → Change visibility**. Do this before you start generating outputs.

### Staying current with upstream changes

As the repo is refined and new projects or skills are added, you may want to pull those updates into your fork:

```bash
# Add the upstream remote (one-time setup)
git remote add upstream https://github.com/corewrk/employee-number-two.git

# Pull upstream changes into your fork
git fetch upstream
git merge upstream/main
```

Review any changes before merging, particularly if you have modified shared files like `CLAUDE.md` or global templates.

---

## Contributing Back

Employee Number Two grows through use. Founders who work through these projects often build skills, templates, or reference documents that would be valuable to others. If you've built something like that, contributions are welcome.

### Who should contribute

The best contributions come from **founders who have actively used the repo** and built something to fill a gap they encountered. Before opening a PR, you should be able to describe the specific task you used your contribution for and what the output looked like. Untested contributions — things built speculatively without being used on a real task — are unlikely to be accepted.

You do not need to be a developer. If you can write a clear SKILL.md and a useful reference document, that is sufficient.

### What makes a good contribution

**Skills** — A new skill covering a task not addressed by the existing project skills. Good candidate skills are reusable across many founders' situations, not specific to a single industry. Examples: a skill for analyzing App Store or G2 reviews as market research signals, a skill for structuring a design partner interview, a skill for drafting an advisor outreach message.

**Reference documents** — Templates, frameworks, checklists, or annotated examples that support an existing or new skill. These go in the skill's `references/` directory.

**Global templates** — Document templates that belong in `global/templates/` because multiple projects benefit from them.

**New projects** — A fully scoped project covering a stage of company-building not currently in the repo. New project proposals should include a purpose statement, a list of proposed skills, which global context files it would read and write, and a rationale for where it fits in the sequence.

**Refinements** — Improvements to existing SKILL.md files, CLAUDE.md files, or reference documents based on real observed gaps. These are often more impactful than new additions.

### What is out of scope

- Skills that require specific paid third-party subscriptions to function
- Industry-specific skills with narrow applicability
- Your personal startup outputs (your ICP, pitch deck, financial model, etc.)
- Changes to `global/context/` files — these are personal to each founder's fork
- Any contribution intended for commercial use or redistribution in a product or service

---

## How to Submit a Contribution

### 1. Build and test your contribution in your fork

Use your skill, template, or project on a real task before submitting. Document what you used it for and what the output looked like — you will need this for your PR description.

### 2. Open a Pull Request

Go to the [Employee Number Two repo on GitHub](https://github.com/corewrk/employee-number-two) and open a Pull Request from your fork's branch to `main`.

### 3. Use this PR description format

```
## What this contributes
[One paragraph: what the skill, template, or project does and what problem it solves]

## Where it lives in the repo
[File path(s): e.g., projects/01-market-research/.claude/skills/app-store-researcher/]

## Which project it belongs to
[Project number and name]

## How I tested it
[Describe the specific task you used it for and what the output looked like]

## Why other founders would find this useful
[One paragraph: the general use case, not your specific situation]
```

### 4. What happens next

All PRs are reviewed by Dr. Andrew O'Donnell. Review is not on a fixed timeline — this repo is maintained alongside active consulting work. If your contribution is accepted, it will be merged into `main` and your GitHub handle will be added to [CONTRIBUTORS.md](./CONTRIBUTORS.md). If it needs refinement, you will receive specific feedback. If it is out of scope, the PR will be closed with a brief explanation.

---

## Attribution

All accepted contributors are listed in [CONTRIBUTORS.md](./CONTRIBUTORS.md) with their GitHub handle and a brief description of what they contributed. This file is updated with each accepted PR.

---

## Licensing

By submitting a Pull Request, you confirm that:

1. You are the original author of the contribution
2. You have the right to submit it
3. You agree it will be published under the same [Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)](./LICENSE) license as the rest of the repo

> **Note on commercial rights:** A Contributor License Agreement (CLA) may be introduced in a future version of this repo as the project matures. If and when that happens, existing contributors will be notified. In the meantime, the CC BY-NC license governs all contributions.

---

## Questions

If you have a question about whether something is a good candidate for contribution before you build it, open a [GitHub Discussion](https://github.com/corewrk/employee-number-two/discussions) or reach out directly at [andrew@corewrk.com](mailto:andrew@corewrk.com).
