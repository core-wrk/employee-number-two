# Brand Voice Template

This is an internal reference for the `brand-voice-developer` skill. It defines the structure of both the project draft (`outputs/brand-voice-guide.md`) and the global context file (`global/context/brand-voice.md`). **Do not show this document to the founder.** Use it to scaffold both files and to maintain the dual-structure pattern established by `icp-template.md` in Project 01.

---

## Why two files

The same reasoning as `icp-builder`:

- **The draft** contains the audit trail — worked rewrites with annotations, rationale tied to positioning, the founder's writing samples that informed the analysis, and a "what changed from the founder's initial voice instinct" section if a tension surfaced and got resolved. This is valuable for the founder's own learning and for revisiting the voice later. It is too long for downstream projects to load as cheap context.
- **The global file** is the distilled version. Voice attributes, tone-by-context table, vocabulary lists, and 2–3 representative rewrites. Readable in under 5 minutes. This is what Projects 03, 04, and 05 load every time they run.

Keep them in sync but do not put audit content in the global file. If the founder wants to reference the rationale, they can read the draft.

---

## Structure of `global/context/brand-voice.md` (the distilled version)

This is what downstream projects read. Keep each section tight.

```markdown
# Brand Voice

## Summary
<2-3 sentence description of the brand voice. Like reading a personality summary — what kind of brand this is in writing. This is what a downstream skill reads first when it needs to draft content.>

## Voice Attributes

### 1. <Attribute label (one or two words)>
- **What it means:** <one sentence — the operational meaning here, not a dictionary definition>
- **Sounds like:** "<short example sentence in this voice>"
- **Does NOT sound like:** "<short example sentence in the wrong voice — usually marketing-language>"

### 2. <Attribute label>
[same structure]

### 3. <Attribute label>
[same structure]

[3 minimum, 5 maximum]

## Tone by Context

| Context | Tone shift |
|---|---|
| Sales email to a cold prospect | <how the voice tilts here> |
| Sales call follow-up | <...> |
| Marketing landing page | <...> |
| Founder LinkedIn post | <...> |
| Customer support reply | <...> |
| Investor pitch | <...> |

[6–8 contexts is the right range. More than 8 is over-specified; the brand is governing too much.]

## Vocabulary

**Use these phrases:**
- "<phrase>" (source: icp.md or messaging-framework.md)
- "<phrase>"
- ...

[5–10 phrases — small enough to be memorable, drawn from how the customer actually talks]

**Avoid these phrases:**
- "<phrase>" — <one-line reason: marketing language / owned by competitor / customer doesn't use it>
- "<phrase>" — <reason>
- ...

[5–10 phrases — usually the marketing-language abstractions and competitor-owned terms]

## Worked Rewrites

### Rewrite 1: <short label, e.g., "Cold prospect email opener">
**Before (default marketing language):**
> <2–4 sentences in marketing-language form>

**After (in this brand's voice):**
> <2–4 sentences in the actual brand voice>

**What changed:** <which voice attribute is operating; which avoid-phrase was removed; why this is the better version for this audience>

### Rewrite 2: <label>
[same structure]

### Rewrite 3: <label>
[same structure]

[2–3 representative rewrites in the global file. The draft has more.]
```

---

## Structure of `projects/02-brand-and-marketing/outputs/brand-voice-guide.md` (the draft)

The draft has everything the global version has, plus the following additional sections.

```markdown
[All sections from the global file above, with these additions:]

## Founder Writing Samples

[The 2–3 samples the founder shared in Phase 1 of the flow. Quote them verbatim. This is the raw material the analysis is built on.]

**Sample 1: <context, e.g., "Cold email to a prospective design partner">**
> <verbatim text>

**Sample 2: <context>**
> <verbatim text>

**Sample 3: <context>**
> <verbatim text>

## Analysis of Founder Writing Samples

[Per sample, what was distinctive: sentence length, vocabulary, distinctive habits, what aligned with the positioning and what did not.]

- **Sample 1:** <observations>
- **Sample 2:** <observations>
- **Sample 3:** <observations>

## Voice Attribute Rationale

[For each voice attribute in the global file, a paragraph explaining why this attribute was chosen — tied to (a) the founder's actual writing, (b) the positioning, and (c) the audience from icp.md. The global file gives the attribute and the example. The draft gives the *why*.]

### 1. <Attribute label> — Rationale
<2–4 sentences. Why this attribute? What in the founder's writing supports it? What in the positioning needs it? What in the ICP makes it the right choice?>

### 2. <Attribute label> — Rationale
[same]

[and so on]

## Additional Worked Rewrites

[The full set of rewrites the conversation produced. The global file has 2–3; the draft has 5–8 covering more contexts: cold email, follow-up, landing page, LinkedIn post, objection handler from the messaging framework, customer support reply.]

### Rewrite 4: <label>
**Before:** ...
**After:** ...
**What changed:** ...

[and so on through all the rewrites the conversation produced]

## What Changed From the Founder's Initial Voice Instinct

[If a tension surfaced in Phase 2 of the flow and got resolved, document it here. One paragraph per change. This is the most valuable section for the founder's own learning. If no tension surfaced, write "No significant tension between the founder's natural voice and the positioning — voice attributes amplify what the founder already does."]

**<Change 1, e.g., "Removed 'warm' as a voice attribute.">**
The founder initially proposed "warm and conversational" as a voice attribute. Reading the founder's writing samples and the ICP together, we agreed that this would undermine the positioning — RevOps buyers reading "warm" copy from a $200/seat tool tend to read it as unprofessional. The voice landed on "calm and direct" instead, which preserves the founder's natural ease without softening the credibility the audience requires.

**<Change 2>**
[same structure]

## Live Questions for the Voice

[Pieces of the voice that depend on assumptions still being tested. For example: "The 'data-grounded' attribute assumes the proof points in messaging-framework.md become VALIDATED in Project 08. If those proof points stay LIVE QUESTION through beta, the voice may need to soften the data-grounded claim until proof exists." This is honest — voice and messaging must hang together, and the voice cannot make claims the messaging cannot back up.]
```

---

## Rules for the global file

- **Maximum 5 voice attributes.** More than 5 is over-specified.
- **Maximum 8 tone contexts.** More than 8 is over-governed.
- **5–10 vocabulary phrases per list.** Small enough to be memorable.
- **2–3 worked rewrites.** Pick the most representative ones from the conversation.
- **No audit trail content.** No rationale paragraphs, no founder writing samples, no "what changed" section.
- **No reference to the framework or skill mechanics.** Downstream skills should be able to read the file as if it were written by a human, without seeing scaffolding.
- **Standard metadata block at the top** — added automatically by `context-writer`:

```
<!--
Last updated: <date>
Source project: 02-brand-and-marketing
Source skill: brand-voice-developer
-->
```

---

## Rules for the draft file

- **All global content, plus the audit-trail sections** named above
- **Founder writing samples quoted verbatim** — they are the raw material, do not paraphrase
- **Rationale section per voice attribute** — explains *why* this attribute was chosen, not just what it is
- **More worked rewrites than the global file** — at least 5, ideally 6–8
- **"What Changed From the Founder's Initial Voice Instinct" section** — if applicable

---

## Process recap (how the two files get written)

1. Show the founder a preview of `brand-voice-guide.md` (the draft).
2. Get explicit approval. ("Does this look right to write?")
3. Write directly to `projects/02-brand-and-marketing/outputs/brand-voice-guide.md`.
4. Show the founder a preview of `brand-voice.md` (the distilled global version).
5. Get explicit approval.
6. **Pass the content to the `context-writer` skill** with the destination path. The `context-writer` skill handles its own preview/diff (against any existing version) and writes with the standard metadata block.
7. Confirm both writes in one or two sentences and tell the founder Project 02 is complete.

Do not write the global file directly. Always pass through `context-writer` so global writes go through the standard flow with metadata, diff preview, and the maintainer's expected guarantees.

---

## Common mistakes

- **Writing the global file before the draft.** Always draft first, then distill. Distillation is easier with the audit trail in front of you.
- **Putting audit content in the global file.** Downstream projects load it cheaply; they do not need the rationale.
- **Producing fewer than 3 voice attributes.** Two is too thin to guide downstream writing.
- **Producing more than 5 voice attributes.** Six or more attributes blur into nothing actionable.
- **Skipping the anti-pattern ("does NOT sound like") for any attribute.** The anti-pattern is half the value.
- **Skipping the worked rewrites in the global file.** Downstream skills need at least 2–3 examples of the voice in action.
- **Letting voice attributes contradict the founder's actual writing samples.** Unsustainable voice = unused voice.
- **Letting voice attributes claim more than the messaging can deliver.** Voice and messaging must hang together — a "data-grounded" voice with all-LIVE-QUESTION proof points is a contradiction.
