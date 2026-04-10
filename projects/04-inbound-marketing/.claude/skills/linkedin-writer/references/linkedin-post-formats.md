# LinkedIn Post Formats

This is an internal reference for the `linkedin-writer` skill. It describes the four LinkedIn post formats this skill can produce, what each is good for, when each fails, and the structural pattern for each. **Do not show this document to the founder.** Use it to recommend the right format for the post's intent and to scaffold the structure.

---

## How To Use

After the founder has stated the post's intent and pillar, recommend a format. Each format has its own structure and constraints. The four formats this skill produces are:

1. **Text post** — the workhorse. ~1300 characters max. Default unless the founder has a reason to use something else.
2. **Document carousel concept** — a multi-page PDF the founder uploads as a "document post." High engagement when done well.
3. **Poll concept** — a one-question poll. Low effort, decent engagement, great for low-friction audience interaction.
4. **Repost-with-commentary** — sharing someone else's post with the founder's substantive take added.

This skill does not produce video posts. If the founder wants video, redirect to `youtube-scriptwriter` or note that LinkedIn-native video deserves its own format.

---

## Format 1: Text Post

**The default format.** 80% of the founder's LinkedIn output should be text posts.

**Structural pattern:**

```
[HOOK LINE 1 — appears in the feed before the "see more" cut]
[BLANK LINE]
[HOOK LINE 2 — also visible in feed, sharpens line 1]
[BLANK LINE]
[BODY — 3–6 short paragraphs, each separated by a blank line]
[BLANK LINE]
[CTA — one sentence inviting low-friction response]
```

**Character budget:**
- Total: ≤ 1300 characters
- Hook (lines 1–2): ≤ 200 characters (this is what shows in the feed)
- Body: ≤ 900 characters
- CTA: ≤ 200 characters

**Best for:**
- Stating a position the buyer will recognize
- Telling a short story (3–5 sentences) with a lesson
- Explaining a single concept the buyer is curious about
- Reacting to industry news or a published piece

**Common failure modes:**
- Hook is too long — first 1–2 lines should be under 200 characters total to avoid being cut off
- Wall of text without paragraph breaks (LinkedIn punishes this; readers scroll)
- Generic opening ("Excited to share...") — scrolled past instantly
- External link in the body — deprioritized; put the link in the first comment
- More than 2 hashtags — deprioritized since 2023

**Example pattern (the position post):**

```
Most sales onboarding fails because the AI feedback is generic.

Reps pass the quizzes but still don't know how to handle real objections from real buyers.

The fix isn't more content. It's grading new reps against your actual deal history — the calls that closed, the calls that didn't, the patterns that repeat.

Mindtickle, Lessonly, and Second Nature all have great features. None of them have your deal history.

The first onboarding tool that grades against the company's own deals will own this category.

Curious — does your team's onboarding actually reference the deals you've closed?
```

Hook: 56 characters. Total: 612 characters. Lots of headroom.

---

## Format 2: Document Carousel Concept

**A multi-page PDF post**, displayed as a swipeable carousel in the LinkedIn feed. Higher engagement than text posts when done well, but takes 5–10x longer to produce.

**Structural pattern:**

A carousel is 8–12 pages. Page structure:

1. **Page 1: Cover** — Title, hook, and a visual cue. The cover earns the swipe.
2. **Pages 2–3: Setup** — Frame the question or problem. Each page should make one point.
3. **Pages 4–8: Body** — One idea per page. Visual hierarchy: large headline, supporting sentence, optional image or chart.
4. **Page 9–10: Resolution** — The take, the data, the framework, the answer.
5. **Last page: CTA** — What to do, where to find more, follow-the-founder.

**Character budget per page:** 30–80 words. Carousels are skimmed, not read.

**Best for:**
- Frameworks the founder wants to make memorable
- Data that benefits from visual presentation
- Step-by-step processes
- "X reasons" or "Y rules" content where each item earns its own page

**Common failure modes:**
- Too much text per page (defeats the format)
- No visual hierarchy (every page looks the same)
- Cover page does not earn the swipe
- Last page is "Thanks for reading" instead of a real CTA

**Note:** This skill produces the *concept* — the page-by-page text and structure. The founder takes that concept to Canva, Figma, or a designer to produce the actual PDF using the brand identity from `brand-identity.md`. The skill does not produce the PDF itself.

**Example concept structure:**

```
PAGE 1 (Cover):
Headline: "5 things RevOps leaders are wrong about onboarding"
Subhead: "Based on 30 conversations with VP-level RevOps in 2026"
Visual cue: Bold typography on brand background

PAGE 2 (Setup):
"Most onboarding programs measure the wrong thing."
"They measure quiz completion. The reps your CRO actually wants are the ones who can run a deal."

PAGE 3 (Item 1):
"#1 — Quizzes are a comfort metric."
"They make the program look productive. They predict nothing about real deal performance."

[Pages 4–7 follow the same pattern, one item per page]

PAGE 8 (Resolution):
"The metric that actually predicts ramp time: how the rep handled their first 5 real-deal objections."
"Everything else is theater."

PAGE 9 (CTA):
"We're building a tool that grades reps against your actual deal history."
"Waitlist link in the first comment."
"Follow [founder name] for more on this."
```

---

## Format 3: Poll Concept

**A one-question LinkedIn poll** with 2–4 options. Low effort, decent engagement, great for low-friction audience interaction.

**Structural pattern:**

```
[CONTEXT — 1–3 sentences setting up the question]

[QUESTION — short, specific, answerable with one of the options]

[OPTIONS — 2–4 choices, each ≤ 30 characters]

[CTA in the post body — invite people to explain their answer in the comments]
```

**Best for:**
- Validating an assumption about the buyer
- Surfacing data that becomes the seed for a future post or report
- Driving comment engagement (people who answer a poll often explain why in the comments)
- Building a soft proof point ("78% of VP Sales Enablement leaders say their onboarding tool doesn't reference real deal history")

**Common failure modes:**
- Asking a question that has only one credible answer (no real spread → no real signal)
- Using LinkedIn's default "Other" option without thinking through what it implies
- Forgetting to ask for explanations in the post body (the comments are where the value is)
- Running a poll with no plan to share the results

**Example concept:**

```
CONTEXT:
"Quick question for sales leaders.
When you onboard a new rep, what's the FIRST thing you measure to know if they're ramping?"

QUESTION:
"What's your day-one ramp metric?"

OPTIONS (≤ 30 chars each):
1. Quiz completion
2. Shadowed call count
3. First-deal cycle time
4. Manager gut feel

POST BODY CTA:
"Curious about the spread. If you have a different answer, tell me in the comments — I'll share the results next week."
```

**Important:** This skill does not actually post the poll. It produces the concept — the founder posts it natively in LinkedIn's poll UI.

---

## Format 4: Repost-with-Commentary

**Sharing someone else's post** with the founder's substantive take added on top. Lower-effort than original content; high-leverage when the original post is from someone the founder respects or wants to engage with.

**Structural pattern:**

```
[FOUNDER'S TAKE — 2–4 paragraphs of substantive commentary, NOT a vague endorsement]

[BLANK LINE]

[Optional: a question or challenge to the original author]

[Then the LinkedIn UI inserts the reshared post below]
```

**Best for:**
- Engaging with a post by an analyst, competitor founder, or industry voice the founder wants to be in dialog with
- Adding nuance to a claim the founder partially agrees with
- Disagreeing with a take in a way that does not punch down (named disagreement is often better than original content for engagement, if done well)
- Getting on the radar of the original author and their audience

**Common failure modes:**
- Vague endorsement ("Great take by [name]!") — adds no value, reads as cheap
- Disagreeing rudely or punching down — reputation cost is high
- Reposting without reading the original carefully (the founder will get caught)
- Reposting your own content as if it were someone else's (do not)

**Example:**

```
[Founder's take]

This is the right framing of the problem — most enablement tools mistake content delivery for skill development.

Where I'd push back: the answer isn't smaller content libraries. It's content that's tied to actual deals. A quiz on objection-handling teaches a rep to pass a quiz. Reviewing a real lost deal teaches them why your specific buyers stall.

The hardest part isn't the content. It's the data plumbing between the content tool and the CRM.

Curious if you've seen anyone solve this end-to-end — I haven't, which is why we're building one.

[LinkedIn UI inserts the reshared post here]
```

**Important:** The skill produces the founder's take. The founder pastes it into LinkedIn's UI and uses LinkedIn's reshare feature to attach the original post. The skill needs the URL or text of the original post from the founder before drafting.

---

## Format Selection Rules

If the founder asks "which format should I use?", the answer is almost always **text post**. Default to text post unless one of these conditions is true:

| Condition | Recommended format |
|---|---|
| The founder has a memorable framework or process that benefits from visual hierarchy | Document carousel |
| The founder wants to validate an assumption with the audience and seed a future post | Poll concept |
| Someone the founder respects just published something the founder has a real take on | Repost-with-commentary |
| Default | Text post |

Do not let the founder use document carousel as the default just because they have higher engagement — the production cost is 5–10x and the founder will not sustain it.
