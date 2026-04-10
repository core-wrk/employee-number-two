# Employee Number Two

**A Claude Code workspace for startup founders.**

---

## The Problem This Solves

Most founders don't fail because they had a bad idea. They fail because they worked on the wrong things in the wrong order — building before validating, pitching before positioning, hiring before understanding unit economics.

The frameworks for doing this right exist. What's been missing is a practical, working implementation of those frameworks that a founder can actually use — not read about, not attend a workshop on, but use, every day, as they build.

Employee Number Two is that implementation.

This repo was created by [Dr. Andrew O'Donnell, PhD](https://www.linkedin.com/in/andrewodonnell/), founder of [Core Wrk, LLC](https://www.corewrk.com), out of the work done helping early-stage founders get structured, move faster, and avoid the most common and costly mistakes. The methodology behind it is drawn from proven startup frameworks and refined through direct consulting work with founders across industries.

The goal of making it publicly available is simple: give every founder access to the same structured thinking that used to require a consultant in the room.

---

## What It Is

Employee Number Two is a [Claude Code](https://claude.ai/code) repository — a collection of AI agents, skills, and structured context files organized into twelve projects that mirror the real progression of building a startup.

Each project covers a distinct stage:

| Project | Stage |
|---|---|
| 00 — Onboarding | Set up your workspace and global context |
| 01 — Market Research | Validate your hypothesis, map the market, identify your customer |
| 02 — Brand & Marketing Strategy | Define your positioning and brand voice |
| 03 — Brand Identity | Develop your visual identity direction |
| 04 — Inbound Marketing | Build your content engine and waitlist |
| 05 — Outbound Sales | Prospect, qualify, and reach early customers |
| 06 — Product Management | Write your product requirements and roadmap |
| 07 — Product Development | Translate requirements into engineering specs |
| 08 — Beta Testing | Recruit users, collect structured feedback, iterate |
| 09 — Pricing & Packaging | Develop and validate your pricing model |
| 10 — Legal & Formation | Entity selection, domain, banking |
| 11 — Fundraising Prep | Identify investors, build your pitch |
| 12 — Financial Modeling | Model revenue, costs, unit economics, runway |

Projects are designed to be worked through in sequence. Each one builds on outputs from the one before it. A shared global context layer carries key information — your Ideal Customer Profile, brand voice, product overview, competitive landscape — across projects automatically, so you never have to repeat yourself.

---

## What You Actually Get

Every project produces real, usable deliverables:

- Market research and competitive analysis reports
- Ideal Customer Profile documents
- Brand voice guide and visual identity brief
- Content calendar and channel-specific copy drafts
- Qualified prospect lists and personalized outreach emails
- Pre-call research briefs
- Product requirements documents and epic specifications
- Beta recruitment and feedback synthesis reports
- Pricing strategy documents
- Entity selection analysis and early legal checklist
- Investor prospect list, pitch deck narrative, and TAM/SAM/SOM analysis
- Financial model with revenue scenarios, unit economics, and runway projections

All outputs are plain markdown or structured text files. Human-readable, version-controllable, and yours.

---

## Prerequisites

- [Claude Code](https://claude.ai/code) installed and authenticated
- A GitHub account
- Comfort with a terminal and a text editor (or your favorite IDE)
- A startup idea, or at least a problem you want to explore

No other subscriptions or tools are required. When a third-party tool would meaningfully amplify what an agent can do, the repo will tell you about it — but nothing is required to get started.

---

## Getting Started

### 1. Fork this repo

Click **Fork** at the top right of the repo page. This creates your own copy of the repo under your GitHub account.

> **Use a private fork.** The outputs you generate here — your ICP, brand strategy, prospect lists, financial model — are proprietary to your startup. Make your fork private in GitHub Settings before you start working. The repo's `.gitignore` is configured to exclude output and context files as a safety net, but a private fork is the right practice.

### 2. Clone your fork

```bash
git clone https://github.com/YOUR_HANDLE/employee-number-two.git
cd employee-number-two
```

### 3. Open Claude Code from the repo root

```bash
claude
```

### 4. Start with Project 00

```bash
cd projects/00-onboarding
claude
```

Project 00 walks you through filling in your global context and understanding how the repo works before you start generating outputs.

---

## How the Repo Works

### Global Context

A set of shared markdown files in `global/context/` carries key information across all projects. These files are written by agents as you complete work, and you can edit them directly at any time. Think of them as the institutional memory of your startup — always current, always accessible to whichever project needs them.

### Projects

Each project lives in its own subdirectory with its own `CLAUDE.md`, a set of specialized skills, and an `outputs/` directory. Opening Claude Code from within a project directory gives you access to that project's skills and context automatically.

### Skills

Skills are specialized instruction sets that tell Claude Code how to perform specific tasks — researching Reddit threads, drafting personalized outreach emails, building a competitor matrix, writing an epic requirements document. Each project ships with the skills most relevant to that stage. If you need something a project doesn't cover, Claude Code's native skill builder lets you create custom skills and save them to your fork.

---

## Extending the Repo

Employee Number Two is intentionally not exhaustive. Every founder's situation is different, and the projects and skills here cover the most common needs — not every possible one.

If you build a skill, template, or project that you think would benefit other founders, see [CONTRIBUTING.md](./CONTRIBUTING.md) for how to suggest it. Contributions are reviewed and, where appropriate, incorporated into the main repo.

---

## License

This project is licensed under [Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)](./LICENSE).

You are free to use, adapt, and share this work for non-commercial purposes as long as you give appropriate credit to Dr. Andrew O'Donnell and Core Wrk, LLC. Commercial use — including building a product or service on top of this framework — requires explicit written permission from Core Wrk, LLC. Contact [andrew@corewrk.com](mailto:andrew@corewrk.com) for licensing inquiries.

---

## Working With Core Wrk

Employee Number Two exists because the methodology behind it works — and because access to structured thinking shouldn't require a retainer.

That said, if you're at a stage where you want a thought partner, an experienced set of eyes on your strategy, or direct support working through any of these projects, that's what [Core Wrk](https://www.corewrk.com) is for.

[www.corewrk.com](https://www.corewrk.com) · [andrew@corewrk.com](mailto:andrew@corewrk.com)

---

## Acknowledgments

Built with [Claude Code](https://claude.ai/code) by Anthropic.

Structured around proven startup frameworks developed and refined through the academic and practitioner communities focused on disciplined company-building.
