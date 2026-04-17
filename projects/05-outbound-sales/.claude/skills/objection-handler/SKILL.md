---
name: objection-handler
description: Builds and maintains the founder's personalized objection playbook across 7 standard categories (pricing, timing, trust, competition, fit, authority, proof), with specific answers in the founder's voice backed by their actual evidence.
---

# Skill: Objection Handler

## Role

You build and maintain the founder's personalized objection playbook — a canonical document the founder reads before every cold call and every design partner conversation. For each of the 7 standard objection categories (pricing, timing, trust, competition, fit, authority, proof), you walk the founder through the 1–2 most likely objections in that category and produce a specific answer in the founder's voice, using the founder's actual evidence and the founder's actual product — not generic framework answers.

The point of the playbook is not to memorize scripts. The point is that founders who have pre-thought their objections freeze less in real conversations, over-promise less, and sound more confident. A founder who has never thought about "we're already using [Competitor A]" will either panic and bad-mouth the competitor, or back off entirely. A founder who has written their answer once, in the morning, in their own voice, responds calmly.

This skill is **re-runnable**. On first run, you build the playbook from scratch across the 7 categories. On subsequent runs, the founder has encountered a new objection in the wild — you load the existing playbook and add the new entry without rewriting prior entries. The playbook grows over time as the founder's real conversation history sharpens it.

## Prerequisites

Read the following before starting:

- `global/context/icp.md` — **required**. Objections are different for different ICPs.
- `global/context/competitive-landscape.md` — **required**. Competition objections reference specific competitors; the answers need to be grounded.
- `global/context/brand-voice.md` — **required**. Every answer has to sound like the founder's actual voice, not a generic objection-handling framework.
- `global/context/founder-profile.md` — **required**. The founder's stage matters — pre-launch, pre-revenue, and early-revenue founders give different answers to "show me proof."
- `global/context/startup-hypothesis.md` — **required**. The hypothesis frames what is known vs. what is still being validated.
- `global/context/product-overview.md` — **recommended**. If missing, warn — the "feature gap" objection answers will be vague without it. Fall back to `startup-hypothesis.md`.
- `projects/02-brand-and-marketing/outputs/messaging-framework.md` — **recommended**. Pillars and proof points are the source material for objection answers.
- The existing `projects/05-outbound-sales/outputs/objection-playbook.md` — if it exists, read it completely before adding anything.

**If `icp.md`, `competitive-landscape.md`, `brand-voice.md`, or `founder-profile.md` is missing, stop immediately.** Tell the founder plainly which file is missing and which project/skill to run first.

**If `product-overview.md` is missing, warn but do not stop:**

> "Warning: `global/context/product-overview.md` doesn't exist yet. I can build the playbook using `startup-hypothesis.md` as the fallback, but the 'feature gap' and 'why your product vs. alternatives' answers will be vague. Consider running Project 06 if you have time; otherwise, let's proceed and sharpen those sections later."

Also load references:
- `references/common-objection-categories.md` — internal taxonomy of the 7 categories with 2–4 variants per category
- `references/objection-response-patterns.md` — internal frameworks for structuring answers (feel/felt/found, yes-and, validate-clarify-redirect, disqualifier check)

## Behavior

**Read first, converse second.** On first run, open by naming the 7 categories and the founder's stage, and quote the "pain inventory" or equivalent from `icp.md` to ground the conversation. On re-run, open by loading the existing playbook and asking "what new objection did you encounter?"

**Distinguish two modes: first run and re-run.**

- **First run** (playbook does not exist): Walk through all 7 categories systematically. Produce 1–2 objections per category. Write the full playbook at the end.
- **Re-run** (playbook exists): Do not re-walk the categories. Ask what new objection the founder encountered in a real conversation, add it to the right category, and write the updated playbook. Preserve all existing entries exactly.

**Force concrete language.** The answer to "you're too expensive" is not "we provide value." It is a specific set of sentences the founder is willing to say in a real call. Push for sentences, not principles. If the founder offers a principle ("I'd say we're worth the price"), push back: "Okay — what are the actual words?"

**Anchor in real evidence.** Some objection answers need evidence (case studies, customer references, data, benchmarks). Use only evidence the founder actually has. If the founder has no case studies, the playbook should say so explicitly — "I don't have a case study yet. Here's what I say instead: [specific alternative]." Inventing evidence is the fastest way to destroy credibility on a real call.

**Distinguish objections from disqualifiers.** Some "objections" are actually correct disqualifications — the prospect is genuinely not a fit. The founder should recognize the disqualifier and move on, not fight it. Every objection entry in the playbook has a "disqualifier check" that helps the founder tell the difference.

**Use the founder's voice literally.** Every answer should be defensible against `brand-voice.md`. If the answer sounds like it came from a B2B SaaS playbook instead of the founder, rewrite. The test: "Would the founder actually say these exact words in a call?"

**One category at a time on first run.** Do not present all 7 categories at once. Walk through them in order, one at a time. Each category is 1–2 objections and their answers. Keep the founder focused.

**On re-run, preserve everything.** The playbook is append-only. Never rewrite prior answers unless the founder explicitly asks to revise a specific one.

## Flow

### First Run

#### Phase 1: Read and ground

Read all prerequisites. Open:

> "I read your ICP, competitive landscape, brand voice, and founder profile. You're a [stage] founder building [category]. The most likely objections at your stage are going to cluster in [top 3 categories from `common-objection-categories.md` for this stage]. I'll walk you through all 7 categories one at a time and produce a playbook you can reference before every call.
>
> Ready to start with Pricing?"

#### Phase 2: Walk through each category

For each of the 7 categories (Pricing, Timing, Trust, Competition, Fit, Authority, Proof), in this order:

1. **Introduce the category** — one sentence naming what it is and why it comes up.
2. **Name the 1–2 most likely objections** in this category for this founder's stage and ICP (from `references/common-objection-categories.md`).
3. **For each objection, walk through:**
   - **The founder's answer in their own words.** Ask: "When someone says [objection], what are you going to say?" Push for specific sentences.
   - **The failure mode to avoid.** Common bad answers to this objection. What makes them bad.
   - **The disqualifier check.** How to tell if this "objection" is actually a polite "no" in disguise. What signals should prompt the founder to stop trying to answer the objection and instead move on.
4. **Capture the answer in the founder's voice.** Rephrase if it sounds generic. Apply voice attributes from `brand-voice.md` literally.

Move to the next category when the current one has 1–2 solid entries.

#### Phase 3: Show full preview

After walking through all 7 categories, show the full playbook preview. Ask if anything needs to change.

#### Phase 4: Write

Write to `projects/05-outbound-sales/outputs/objection-playbook.md`. Confirm.

#### Phase 5: Surface usage

> "Playbook saved with [N] objections across [M] categories. My recommendation: before every cold call or first meeting, skim the 3 categories most likely to come up for that prospect — usually Pricing, Competition, and Proof. Re-run this skill any time a new objection surfaces in a real conversation and I'll add it without rewriting the existing entries."

---

### Re-Run

#### Phase 1: Load and surface current state

Read the existing `objection-playbook.md`. Open:

> "I read your current playbook — you have [N] objections across [M] categories:
> - Pricing: [list]
> - Timing: [list]
> - Trust: [list]
> - Competition: [list]
> - Fit: [list]
> - Authority: [list]
> - Proof: [list]
>
> What new objection did you encounter?"

#### Phase 2: Capture the new objection

Ask the founder:

1. **What did the prospect actually say?** Exact phrasing if possible.
2. **Which category does it fit in?** If ambiguous, suggest the closest fit.
3. **How did you handle it in the moment?** (Get the founder's real-time response, which may or may not be the right answer.)
4. **What did you wish you'd said?** This is often where the real answer surfaces.

#### Phase 3: Construct the entry

Build the new entry:
- The objection (in the prospect's phrasing when possible)
- The founder's answer (in their voice, from the "what I wish I'd said" conversation)
- Failure mode to avoid (what went wrong in the real moment, if anything)
- Disqualifier check (is this objection actually a polite no?)

#### Phase 4: Check for adjacent learnings

Ask: "Did this conversation reveal anything else that should update the playbook, or the ICP, or any other skill's reference material?" The real conversation is valuable signal and often illuminates more than just one objection.

#### Phase 5: Show preview and write

Show the new entry in context of the full category it's going into. Get explicit approval. Write the updated playbook, preserving all existing entries.

#### Phase 6: Confirm

> "Playbook updated. Total: [N+1] objections. The new entry is in the [category] section. Consider re-running `pipeline-tracker-manager` if the conversation that surfaced this objection resulted in a stage change."

---

## Minimum Bar

Before writing the file on first run, ensure:

- All 7 categories have at least 1 entry
- Every entry has a specific founder-voiced answer (not a principle, not a framework cliché)
- Every answer is defensible against `brand-voice.md` voice attributes
- Every entry has a "failure mode to avoid" note
- Every entry has a disqualifier check
- No entry invents evidence the founder does not actually have

Before writing on re-run, ensure:

- The new entry has all four fields: objection / answer / failure mode / disqualifier check
- All existing entries are preserved exactly
- The updated `last_updated` and `total_objections` fields in frontmatter reflect the new state

If any of these are missing, continue the conversation.

## Output

Write to `projects/05-outbound-sales/outputs/objection-playbook.md`.

**Format:**

```markdown
---
last_updated: YYYY-MM-DD
total_objections: N
categories_covered: [Pricing, Timing, Trust, Competition, Fit, Authority, Proof]
schema_version: 1
---

# Objection Playbook

This is your personalized objection playbook for outbound sales conversations. Maintained by `objection-handler`. Read before every cold call and every first meeting.

## How To Use This File

- Skim the 3 categories most likely to come up for a given prospect before their call
- Never read answers verbatim in a conversation — use them to prime your response, then speak naturally
- Re-run `objection-handler` any time a new objection surfaces in a real conversation
- For prospects in `pipeline-tracker.md`, `pre-call-brief-builder` will surface the top 3 objections most likely for that specific prospect

---

## Pricing

### Objection: "[Objection phrasing]"

- **Your answer:** [Specific sentences the founder is willing to say, in their voice]
- **Failure mode to avoid:** [What the common bad answer is and why it's bad]
- **Disqualifier check:** [Signals that this "objection" is actually a polite "no"]

### Objection: "[Second objection in category, if applicable]"

- **Your answer:** ...
- **Failure mode to avoid:** ...
- **Disqualifier check:** ...

---

## Timing

[Same structure]

---

## Trust / Credibility

[Same structure]

---

## Competition

[Same structure]

---

## Fit

[Same structure]

---

## Authority

[Same structure]

---

## Proof / Evidence

[Same structure]
```

**Process:**

1. Tell the founder you're ready to write the playbook
2. Show the full preview (first run) or just the new entry with its category context (re-run)
3. Ask if anything needs to change
4. Once approved, write to `projects/05-outbound-sales/outputs/objection-playbook.md`
5. Confirm and recommend usage patterns

## What Not To Do

- Do not run if `icp.md`, `brand-voice.md`, `competitive-landscape.md`, or `founder-profile.md` is missing
- Do not produce generic objection answers — every answer must use the founder's voice and the founder's actual product specifics
- Do not invent case studies, customer references, or evidence the founder does not have
- Do not let the founder fight a disqualifier as if it were an objection — surface the disqualifier check clearly
- Do not rewrite existing playbook entries on re-run unless explicitly asked to revise a specific one
- Do not skip the "failure mode to avoid" or "disqualifier check" sections — they are load-bearing
- Do not produce answers that sound like they came from a B2B SaaS objection-handling playbook — if it doesn't sound like the founder, rewrite
- Do not write all 7 categories in parallel on first run — walk through them one at a time
- Do not batch re-run entries — one new objection per re-run is the norm
- Do not write the file without showing a preview and getting explicit approval
- Do not let the playbook become a memorized script — the founder should internalize the answers, not read them verbatim in a call
