# Employee Number Two — Claude Code Root Instructions

## What This Repo Is

Employee Number Two is a structured Claude Code workspace for startup founders. It guides you through the full arc of building a company — from validating your initial idea to preparing for fundraising — using a sequence of projects, each with specialized agents and skills tailored to that stage of work.

This is not a chatbot. It is a working environment. The outputs you generate here are real deliverables: market research reports, brand voice guides, prospect lists, product requirements documents, pitch deck narratives, and financial models. They accumulate over time and build on one another.

You are the decision-maker. The agents here surface options, frameworks, and recommendations. They do not act autonomously or make irreversible choices on your behalf.

---

## How to Navigate This Repo

Work through projects in numbered order. Each project depends on outputs from the one before it.

```
00-onboarding          Start here. Sets up your global context.
01-market-research     Validate your hypothesis. Understand the problem and market.
02-brand-and-marketing Define your positioning and brand voice.
03-brand-identity      Develop your visual identity and design system direction.
04-inbound-marketing   Build your content engine and waitlist.
05-outbound-sales      Prospect, qualify, and reach out to early customers.
06-product-management  Define your product requirements and roadmap.
07-product-development Translate requirements into engineering specs. QA and UX review.
08-beta-and-testing    Recruit beta users, collect feedback, iterate.
09-pricing-packaging   Develop and validate your pricing model.
10-legal-formation     Entity selection, domain, banking, and early legal awareness.
11-fundraising-prep    Identify investors, recruit advisors, build your pitch.
12-financial-modeling  Model revenue, costs, unit economics, and runway.
```

You do not need to complete every project. If you are at a stage where you already have a brand identity, start at the project that is relevant to where you are.

---

## Global Context

The `global/context/` directory contains shared files that multiple projects read and write. These are plain markdown files. You can and should read, edit, and refine them directly.

| File | What It Contains |
|---|---|
| `founder-profile.md` | Your background, goals, and working style |
| `startup-hypothesis.md` | Your problem statement and proposed solution |
| `icp.md` | Ideal Customer Profile |
| `brand-voice.md` | Brand voice and tone guide |
| `brand-identity.md` | Colors, typography, logo direction |
| `product-overview.md` | High-level product summary and value proposition |
| `competitive-landscape.md` | Competitor map and capability gaps |
| `pricing-model.md` | Pricing and packaging decisions |
| `company-profile.md` | Legal entity, domain, structure |

Each project's `CLAUDE.md` tells you exactly which of these files it loads. No project loads more context than it needs.

---

## How Context Accumulates

1. You start a project. Its `CLAUDE.md` specifies which global context files are relevant.
2. The `context-loader` skill reads only those files into the session.
3. As you complete work, agents produce output files saved in the project's `outputs/` directory.
4. When a deliverable is ready to be shared across projects, the `context-writer` skill updates the appropriate file in `global/context/`. It shows you a preview before writing.
5. You can edit any global context file directly at any time. These are your files.

---

## Global Skills

These skills are available in every project session. You do not need to invoke them manually — they are triggered automatically when relevant, or you can call them explicitly.

| Skill | What It Does |
|---|---|
| `web-researcher` | Web search and synthesis for current information |
| `context-loader` | Loads the relevant global context files for the current project |
| `context-writer` | Writes or updates global context files with a diff preview |
| `document-formatter` | Applies consistent formatting to all output documents |
| `third-party-advisor` | Surfaces relevant third-party tools when they would amplify a task |

---

## File and Output Conventions

- All output files are markdown (`.md`) or structured text (`.json`, `.csv`) unless otherwise noted.
- Output files are saved in the `outputs/` directory within each project.
- File names use lowercase kebab-case: `icp-draft.md`, `competitor-analysis.md`.
- Global context files are updated by agents using `context-writer`. Do not rename them.
- Your personal outputs and context files are gitignored by default. See `README.md` for guidance on keeping your fork private.

---

## Third-Party Tools

No third-party subscriptions are required to use this repo. Every agent works without external tools.

When a third-party tool would meaningfully amplify what an agent can do — a CRM, prospecting database, email platform, or similar — the `third-party-advisor` skill will surface it, explain what it does, and describe what connecting it would unlock. The decision is always yours.

---

## Extending This Repo

If a project does not have a skill that covers something you need, Claude Code includes native built-in tools for creating custom skills and MCP servers. Each project's `CLAUDE.md` includes instructions for how to use them. Skills you create are saved in your fork and do not affect the upstream repo.

---

## Repo Structure Reference

```
employee-number-two/
├── CLAUDE.md                  ← You are here
├── README.md
├── CONTRIBUTING.md
├── LICENSE
├── .gitignore
├── global/
│   ├── CLAUDE.md
│   ├── context/               ← Shared context files (gitignored)
│   └── templates/             ← Reusable document templates
├── .claude/
│   └── skills/                ← Global skills
└── projects/
    ├── 00-onboarding/
    ├── 01-market-research/
    ├── 02-brand-and-marketing/
    ├── 03-brand-identity/
    ├── 04-inbound-marketing/
    ├── 05-outbound-sales/
    ├── 06-product-management/
    ├── 07-product-development/
    ├── 08-beta-and-testing/
    ├── 09-pricing-packaging/
    ├── 10-legal-formation/
    ├── 11-fundraising-prep/
    └── 12-financial-modeling/
```
