# Outreach Formats

This is an internal reference for the `email-drafter` skill. It is the structural rules for each format the skill produces: cold email and cold LinkedIn DM. They share the same underlying logic (read prospect, apply voice, personalize, make a specific ask) but the surface conventions differ materially. **Do not show this document to the founder.** Use it to ensure the draft matches the format's conventions.

---

## Format 1: Cold Email

### Character budget

- **Subject line:** 3–7 words ideally, 10 maximum
- **Body:** 100–150 words for initial touch; shorter for follow-ups (see `outreach-sequence-template.md`)
- **Sign-off:** 1 line, usually "—[Founder first name]" or "[Founder first name]\n[Company]"

### Subject line conventions

The subject line is its own craft. It decides whether the email gets opened at all.

**Patterns that work:**

- **Specific reference** (highest signal): "Your SDR hires at NorthStar" — references the personalization angle directly
- **Contrarian question**: "Is ramp time actually a people problem?" — names the problem and disagrees with the conventional framing
- **Short + concrete**: "Quick question about [specific thing]" — only works if genuinely specific
- **Mutual connection** (only if true): "[Connection name] mentioned you" — earns the open
- **Research or data framing**: "The pattern in 200-person SaaS onboarding"

**Patterns that do NOT work:**

- "Following up" / "Quick check-in" / "Touching base" — generic, scrolled past
- "Partnership opportunity" / "Synergies" / "Strategic partnership" — translates to sales pitch
- "Re: [original subject]" when there is no original thread
- ALL CAPS or emojis or "⚡" or "🚀" — immediately marked as mass mail
- Anything longer than 7 words — truncated in the inbox preview
- Clickbait ("You won't believe..." / "This one thing...") — destroys trust

### Body structure (initial touch)

1. **Opener line** (~15–25 words) — the personalization angle. First 1–2 sentences.
2. **Bridge line** (~15–25 words) — connect the opener to the problem. "This usually breaks down when..." or "The pattern is..."
3. **Value line** (~15–25 words) — one specific claim tied to a pillar from `messaging-framework.md`
4. **Ask line** (~15–25 words) — specific, low-friction, give a concrete time proposal if asking for a meeting

Total: 60–100 words of body + 1-line sign-off. Initial touch should rarely exceed 150 words.

### Opener conventions

- **Use the first name directly** — "Sarah," is fine. "Dear Ms. Chen" is stilted; "Hey Sarah!" is too familiar.
- **Skip "I hope this email finds you well"** — universal tell of template email.
- **Do not lead with the founder's name/company** — the opener is about the prospect, not the founder. The founder's identity comes at the sign-off.
- **Do not apologize** — "Sorry to interrupt your day" / "I know you're busy" weakens the email and the prospect doesn't care.

### Sign-off conventions

The sign-off should be short and clean. Two good patterns:

**Pattern A (minimalist):**
```
—[Founder first name]
```

**Pattern B (with company context):**
```
—[Founder first name]
[Founder title] at [Company]
```

Avoid:
- Long email signatures with every social link — overwhelms the simplicity of the email
- "Thanks in advance" — presumptuous
- "Best regards" — stilted
- "Looking forward to your reply" — the prospect hasn't agreed to reply
- Postscript lines ("P.S. ...") — can work, but rarely in initial cold email; save for follow-ups where a P.S. adding a new angle can help

### Threading (for follow-ups)

For follow-up 1 and follow-up 2:
- **Can reply to the existing thread** (keeps context, shows the sequence)
- **Can start a new thread with a new subject line** (fresher, may catch attention the original missed)

The choice depends on whether the founder believes the original was missed (new thread better) or ignored (replying to thread at least shows persistence without being annoying).

For the breakup: reply to the existing thread. It's a closing note, not a new ask.

### Email-specific anti-patterns

- **HTML formatting** — never. Use plain text. HTML-styled emails look like marketing emails and get auto-filtered.
- **Embedded images** — never in cold outreach. Adds weight, triggers filters, screams "marketing blast."
- **Calendar widgets or booking links in the initial** — don't paste a Calendly link in the first touch. Offer times manually; save the Calendly for after the prospect agrees to meet.
- **Attachments** — never in cold. Attachments from unknown senders get filtered.
- **Tracking pixels** — do not enable open tracking on cold outreach; it's low-signal for this volume and feels surveilling if the prospect's client flags it.

---

## Format 2: Cold LinkedIn DM

### Character budget

- **Connection request note:** 300 characters MAXIMUM (LinkedIn's hard limit)
- **Direct message (after connection):** ~300–500 characters for the opening message; can be longer in follow-ups after engagement
- **No subject line** — LinkedIn DMs don't have subjects

### How LinkedIn DMs differ from cold email

LinkedIn DMs are **more conversational and less transactional** than email. The prospect is on LinkedIn, which is a social context, not a deal-flow context. The appropriate register is closer to "interesting industry person reaches out" than "vendor trying to sell something."

This affects every line:
- **Openers are softer** — you don't have the pretense of an email's subject/body structure
- **Asks are smaller** — DMs that end with "let's jump on a call" feel pushy; DMs that end with "curious if this matches your experience" feel natural
- **Formality is lower** — bullet points, numbered lists, and corporate-polish templates feel out of place on LinkedIn

### The connection request vs. the direct message

LinkedIn has two touch modes:

1. **Connection request with note** — 300 character limit, the note is what accompanies the "connect" button. The prospect sees the note before deciding whether to accept.
2. **Direct message** — only possible after the prospect accepts the connection (or if the founder has LinkedIn Premium, which allows InMail without connection).

**The decision:**

- **If the founder has InMail (Sales Navigator or Premium):** send an InMail as the initial touch. Word budget is ~600 characters for opener. Subject line exists (short, specific, like email).
- **If the founder doesn't have InMail:** the initial touch is a connection request with a note. The note has to do the whole job of a cold email in 300 characters.

### Connection request note structure (300 char limit)

With 300 characters, you can fit ~40–50 words total. The structure collapses:

1. **Personalization opener** (~10–15 words) — the single most important thing about this prospect
2. **Why connecting** (~10–15 words) — the reason, tied to a shared context or question
3. **Soft ask** (~5–10 words) — "would love to connect" / "curious if this is your experience too" / NOT "want to jump on a call"

Example (298 characters):

> "Sarah — saw your LinkedIn post last week on ramp time being misdiagnosed as a 'content problem.' That's exactly the pattern I'm building around with early SaaS enablement teams. Would love to connect and exchange notes on what you're seeing at NorthStar. —Alex"

### Direct message structure (after connection)

Once connected, the founder has more room. A good opening DM after connection:

1. **Acknowledge the connection briefly** (one line)
2. **Reference the specific reason they connected** (one line)
3. **Light ask or question** (one line)

Example (~450 characters):

> "Sarah, thanks for connecting. I wanted to follow up on the ramp-time-as-content-problem point from your post — curious how you're approaching it at NorthStar with the recent SDR hires. I've been building enablement tooling calibrated to time-to-quota instead of completion metrics. Not trying to pitch — just curious if this matches what you're seeing on the ground. Would a 15-min call next Tuesday or Thursday work, or would you prefer async notes?"

### LinkedIn-specific opener rules

- **Do NOT start with "I hope this message finds you well"** — same rule as email, even worse on LinkedIn
- **Do NOT open with "Are you the right person to talk to about..."** — insulting, and also obviously fishing
- **Do NOT open with "Congratulations on your new role!"** — unless the role is truly recent (within 2 weeks) and you have something specific to say about it
- **Do NOT open with your own company name** — "Hi, I'm Alex from [Company]" is forgivable on email; on LinkedIn it reads as a sales pitch
- **Open with the prospect** — first words should be about them, not the founder

### LinkedIn-specific ask rules

- **Asks should be lower-friction than email** — LinkedIn is a social context, not a sales context
- **"Would love to connect and learn from you"** is legitimate on LinkedIn in a way it isn't on email
- **"15 minutes on a call"** is acceptable as an ask but only after the prospect has engaged (replied or reacted)
- **"Send me a loom"** or **"async notes"** work well as lower-friction alternatives
- **Never paste a Calendly link in an opening DM** — feels transactional

### LinkedIn sequence modifications

The 4-touch sequence adapts for LinkedIn:

1. **Touch 1**: Connection request with note OR InMail
2. **Touch 2 (follow-up 1)**: If connection accepted but no reply, send a direct message with a new angle. If connection not accepted, engage with their content (react + substantive comment) as a softer re-touch.
3. **Touch 3 (follow-up 2)**: Content engagement touch — comment on a recent post with a substantive observation
4. **Touch 4 (breakup)**: Optional on LinkedIn. Often more natural to just stop DMing than to send an explicit "I'll stop reaching out" message. Use judgment.

### LinkedIn-specific anti-patterns

- **Mass connection requests with generic notes** — LinkedIn's algorithm is getting better at detecting this and will throttle the founder's account
- **Immediate pitch-after-accept** — connecting and then sending a sales pitch within seconds is the fastest way to burn the connection
- **Copy-pasted DM templates** — LinkedIn DMs are even easier to detect as templates than cold emails, because the context is social
- **Voice memos from strangers** — never on a first touch. Creepy.
- **Video DMs (Vidyard, Loom) in the first touch** — reserve for follow-ups, after rapport
- **Using the "InMail credits" language** — "I'm using one of my InMail credits to reach out" is a flex that nobody asked for

---

## Choosing Between Email And LinkedIn DM

| Prospect context | Default format |
|---|---|
| Email address is publicly available and verified | Cold email |
| Email unknown but LinkedIn profile is active | LinkedIn DM |
| Prospect is a frequent LinkedIn poster | LinkedIn DM (they live there) |
| Prospect is an infrequent LinkedIn user (sparse activity) | Cold email |
| Prospect explicitly says "email me" in LinkedIn bio | Cold email |
| Prospect is at a company with strict email filtering (financial services, healthcare) | LinkedIn DM |
| Prospect is an executive (C-level, VP at 500+ company) | Cold email — LinkedIn DMs to executives are often managed by assistants |

**When in doubt:** Ask the founder. They know their ICP's communication habits better than any rule.

**A note on multi-channel:** Sending both an email and a LinkedIn DM for the same touch is "double-tapping" and can work IF the two touches are coordinated (different angle, different format, same underlying ask) and spaced at least a day apart. Do not send identical content on both channels — it looks automated.
