# YouTube Script Template

This is an internal reference for the `youtube-scriptwriter` skill. It is the structural skeleton for the script output, with the cue conventions used throughout. **Do not show this document to the founder.** Use it as the canonical structure for the script files you write.

---

## Why The Template Is Structured This Way

YouTube scripts have to do four things at once:

1. **Read aloud naturally** — the founder is going to speak the lines, not read them silently. Sentences should be short, vary in pace, and avoid tongue-twister consonant clusters.
2. **Cue the visuals** — the editor (or the founder editing themselves) needs to know what should be on screen during each line. The template uses `[VISUAL]`, `[B-ROLL]`, `[ON CAMERA]`, `[SCREEN SHARE]`, and `[GRAPHIC]` cues inline.
3. **Hit timing targets** — each chapter has an approximate timestamp so the founder knows whether they are pacing correctly during filming.
4. **Survive the algorithm** — the cold open and the first 30 seconds are weighted disproportionately because YouTube's retention curve is brutal in those windows.

The template below enforces all four. Do not omit sections.

---

## Cue Conventions

Use these cues inline in the script to mark visual changes:

| Cue | Meaning |
|---|---|
| `[ON CAMERA]` | The founder is speaking directly to camera, no other visual. Default. |
| `[SCREEN SHARE]` | A screen recording or app demo is on screen, founder voiceover continues |
| `[B-ROLL]` | A non-talking-head shot (office, product, customer environment) plays under the voiceover |
| `[GRAPHIC: description]` | A text overlay, chart, or illustration appears |
| `[CUT TO: description]` | A hard cut to a new scene |
| `[ZOOM IN]` / `[ZOOM OUT]` | Camera or framing shift for emphasis |
| `[PAUSE]` | A deliberate beat in the speech (1–2 seconds of silence) |

The founder uses these to brief themselves, the editor, or both. Do not use cues that require an editing complexity the founder cannot deliver — keep cues realistic for a one-person production setup unless the founder explicitly has more resources.

---

## Section Structure

### 1. Frontmatter

YAML metadata at the top of the file: slug, video_type, target_query (if search-intent), estimated_runtime, pillar, draft_date, status.

### 2. Title Options (3 alternates)

Three title alternatives, each ≤ 70 characters. The founder picks at upload time. Title is the second-most-important element after the thumbnail.

### 3. Thumbnail Concept Options (3 alternates)

Three thumbnail concepts described in words (focal element, dominant color, overlay text). The founder takes the description to a designer or thumbnail tool. The skill does not produce the actual image.

### 4. The Promise

The single sentence that tells the viewer what they will walk away with. Spoken aloud after the cold open.

### 5. Cold Open (0:00–0:15)

The first 5–15 seconds of the video. This plays in the YouTube preview when someone hovers over the thumbnail, and it determines whether they click or move on.

A good cold open:
- States the specific outcome of the video in one sentence
- Shows visual proof if possible
- Avoids "Hey guys, welcome back to the channel"
- Avoids long intros or sponsor reads

Format:
```
[Spoken line]
[VISUAL: what is on screen]
```

### 6. Hook / Promise Restatement (0:15–0:30)

After the cold open, restate the promise explicitly:

> "In the next 8 minutes I'll show you the three patterns I see in every failed sales onboarding program, and the one cheap test you can run this week to figure out which one is killing your ramp time."

This is the moment where the algorithm rewards explicit value framing. The first 30 seconds of the video determine retention; this section locks in the viewer's commitment to keep watching.

### 7. Chapter Sections (3–5 chapters)

Each chapter has:
- **Chapter title** — 4–8 words, will appear in YouTube's chapter UI
- **Approximate timestamp** — when the chapter starts
- **Spoken script** — the actual lines, written for spoken delivery
- **Visual cues** inline with the script

Chapter sections should be roughly equal in length. A 6-minute video with 3 chapters has chapters around 90 seconds each. A 10-minute video with 5 chapters has chapters around 100 seconds each.

### 8. CTA (last 30–45 seconds)

A single specific call to action. Avoid the "like, subscribe, hit the bell" trifecta. Pick one of:

- **Subscribe** — only if the video earned it
- **Click the link in the description** — for waitlist signups, blog posts, or follow-up resources
- **Watch the next video** — for end-screen transitions
- **Comment with a specific question** — for engagement and algorithm signal

End the spoken script with the CTA. Then add the end screen cue.

### 9. End Screen (last 10–20 seconds)

The end screen plays during the last 10–20 seconds of the video. It should include:
- 2 video link elements (next video + related video)
- 1 subscribe element

The script should hold for the end screen with relevant visuals or a "thanks for watching" beat — but not with new content, since most viewers click the end screen elements before the speech finishes.

### 10. Description

The description goes into YouTube's description field at upload time. Format:

```
[Paragraph 1: what the video covers, written to be skimmable and to include the search query if search-intent]

[Paragraph 2: who the video is for and what they will walk away with]

[Link to waitlist or follow-up resource — keep this in the first 1–2 lines if possible since YouTube only shows the first 150 characters in the preview]

---

Chapters:
0:00 — Cold open
0:30 — [Chapter 1 title]
X:XX — [Chapter 2 title]
[continue]

Resources mentioned:
- [Link 1]
- [Link 2]
```

The chapters block enables YouTube's chapter UI in the timeline. Without it, the chapters do not show.

### 11. Tags

5 tags. Tags are deprioritized by YouTube but still help with niche queries. Use specific tags, not generic ones (`sales onboarding tools` not `sales`, `RevOps benchmarks` not `business`).

### 12. Voice Attribution Note (internal)

A note at the bottom showing which voice attributes were emphasized and which ICP vocabulary phrases were used verbatim. Internal only — does not get published.

---

## Spoken-Friendly Writing

YouTube scripts are not blog posts read aloud. The script should be written for the spoken voice:

- **Short sentences.** Long sentences lose the listener. Break them at natural breath points.
- **Repeat the key idea.** Spoken communication tolerates repetition that written communication does not. Saying the same idea twice with different framing is normal.
- **Vary pace.** Mix short punchy sentences with longer exploratory ones. Monotone pacing puts viewers to sleep.
- **Avoid tongue-twisters.** Read the draft aloud (mentally or actually) to catch consonant clusters that will trip the founder up.
- **Use contractions.** "Don't" not "do not." Spoken English uses contractions.
- **Avoid bullet points.** Bullet points work in writing because the eye can scan them. They do not work in speech because the listener cannot see them.

---

## Pacing Targets

| Runtime | Word count | Approximate cold open length | Number of chapters |
|---|---|---|---|
| 4 minutes | 600–750 | 10 sec | 3 |
| 6 minutes | 900–1100 | 12 sec | 3–4 |
| 8 minutes | 1200–1500 | 12 sec | 4 |
| 10 minutes | 1500–1900 | 15 sec | 4–5 |
| 12 minutes | 1800–2300 | 15 sec | 5 |

These assume a normal speaking pace of ~150 words per minute. Faster speakers can run longer scripts; slower speakers need shorter ones. The founder should know their own pace.
