# Personalization Variables

This is an internal reference for the `email-drafter` skill. It is a taxonomy of personalization angles ranked by signal strength, with how to find each, how to reference it without sounding stalker-y, and what separates real personalization from mail-merge-token fake personalization. **Do not show this document to the founder.** Use it to push back when the founder's "personalization" is actually just fill-in-the-blank.

---

## The Core Principle

Personalization is the single most important variable in cold outreach response rates. But most "personalized" cold emails are not personalized — they are templates with mail-merge tokens filled in. The recipient can tell the difference in 3 seconds.

**Real personalization tests:**
1. Could a mail-merge template produce this sentence? (If yes, it's not personalization.)
2. Would the recipient recognize this specific detail as something about them specifically? (If no, it's not personalization.)
3. Would the recipient think "this founder did real research on me"? (If no, it's not personalization.)

**Fake personalization** is visible from the first sentence: "Hi [Name], I saw you're the [Title] at [Company]." These cold emails convert at ~1% and most of those are nice replies from people who are too polite to ignore. They are not actual leads.

---

## The Personalization Ladder (ranked by signal strength)

### Tier 1: Specific Public Action (highest signal)

Something the prospect recently did publicly that connects to the founder's thesis:

- **A recent LinkedIn post they wrote** — quote or reference it specifically. "Your post last week about [specific point] is exactly the pattern I've been seeing with [ICP segment]."
- **A recent article they published** — reference the specific argument, not just that they published.
- **A recent talk or podcast they gave** — reference a specific point they made.
- **A recent public tweet or X post** — only if the tweet is substantive (not a retweet).
- **A comment they made on someone else's post** — this is underused and very high signal; it proves the founder is actually paying attention.

**How to find it:** Search LinkedIn activity, Google the prospect's name + "wrote" or "said", check their company's content page, check Speakerdeck or Notist for past talks.

**How to reference:** Quote the specific thing, don't summarize. "Your argument that X is less about Y and more about Z" is better than "Your article on X." Name the specific point that resonated, and say why.

**Watch out for:** Using a quote out of context in a way that misrepresents the prospect's view. Only use this angle if the founder has actually read the thing being referenced.

---

### Tier 2: Observable Buying Trigger

A public signal that the prospect's company is going through something that makes the founder's product more relevant right now:

- **Recent hiring in a relevant function** — "I noticed NorthStar hired 8 SDRs in the last 60 days" (from LinkedIn, company team page, or job posting history)
- **Recent funding round** — "Congratulations on the Series B last month" (only use if timely; funded companies get 200 cold emails in the first week so wait 2–3 weeks)
- **Recent executive hire** — "Saw that Marcus joined last month as your first Head of RevOps" (transitions create buying windows)
- **Recent product launch** — "Your launch of [product] last month" (connects the founder's product to what they're now trying to scale)
- **Company reorganization** — if publicly discussed
- **A new job posting that reveals a pain point** — "I noticed you're hiring a second Sales Enablement Manager — I'd bet the first one is drowning" (read between the lines)

**How to find it:** Crunchbase, LinkedIn company page, company team page, job boards, press releases, recent news.

**How to reference:** Connect the trigger to the problem the founder solves. The trigger is not the point; the *connection* is the point. "You just hired 8 SDRs — and the first 90 days is usually where ramp time decisions either compound or unravel."

**Watch out for:** Using the trigger as a pretext without a real connection to the founder's thesis. "Congrats on the funding!" is not personalization unless it's tied to something specific.

---

### Tier 3: Role Transition / Company Context

Something specific about the prospect's current role or the company's current context that a generic prospector would not know:

- **The prospect just joined this company** — "Your transition from [prior company] to NorthStar 4 months ago" (references their LinkedIn tenure)
- **The prospect was recently promoted** — "Your promotion to VP in September"
- **The company is in a specific stage transition** — "You're the first Head of Enablement NorthStar has had — that transition is where the playbook usually breaks"
- **The prospect's prior experience connects to the founder's thesis** — "Your time at [prior company] building the enablement function from scratch"

**How to find it:** LinkedIn profile history, company team page.

**How to reference:** Show you understand the transition they're in, not just the facts. "Going from founder-led sales to first enablement hire is usually the moment the onboarding playbook either gets formalized or falls apart."

**Watch out for:** Privacy — do not reference their prior employers in a way that implies you've been digging into their history. References should feel like "I did homework" not "I stalked you."

---

### Tier 4: Shared Community or Network

A concrete connection through a shared community, mutual contact, or shared context:

- **Mutual connection mentioned by name** — "Sarah Khan suggested I reach out" (only if true and with Sarah's permission)
- **Shared community membership** — "Saw you in the Revenue Collective discussion last week about X" (only if true and the founder is actually in that community)
- **Shared event attendance** — "I was at SaaStr Annual too, in the enablement track" (only if true)
- **Alumni / school connection** — "Noticed we both did the HBS GMP program" (only if the prospect's profile lists it)
- **Common investor, advisor, or board member** — "[Name] at [Fund] mentioned your team" (only if true)

**How to find it:** LinkedIn mutual connections, community member lists, event attendee lists, alumni directories.

**How to reference:** Establish the connection in one line, then move on. The connection is the bridge, not the whole email.

**Watch out for:**
- **Fake mutual connections** — claiming "we're both in [community]" when the founder is not is the fastest way to tank the founder's personal brand. Never.
- **Unauthorized name-drops** — always get permission from the connection before using their name.

---

### Tier 5: Inferred Pain From Role and Stage (lower signal but acceptable)

When the founder cannot find a Tier 1–4 angle, a well-inferred pain point from the role and company stage can still work — but it's the lowest-signal option and needs to be grounded in the ICP:

- "Most VPs of Sales Enablement at mid-market SaaS companies I talk to are running into [specific problem]" — only if this specific problem is named in `icp.md`
- "The pattern I see at 200-person SaaS companies is [specific observation]" — only if grounded

**How to find it:** It comes from `icp.md`, not from the prospect's public information.

**How to reference:** Name the specific pattern, not a generic category. "VPs of Enablement at mid-market struggle with ramp time" is generic. "Most VPs of Enablement I talk to at 200–400-person SaaS companies say their onboarding programs measure completion instead of time-to-quota, and that disconnect becomes obvious around month 3 of a new hire" is specific.

**Watch out for:**
- This tier is the easiest to fake. If the founder is using this tier because they couldn't find Tier 1–4, push back: "Can we find a more specific angle? Let me check `prospect-list.md` again — what's in the Notes field?"
- Only use this tier if the prospect's Tier 1–4 options were genuinely exhausted.

---

## Fake Personalization (the anti-patterns)

These are NOT personalization, even though founders often think they are:

| Fake | Why it's fake | What to replace it with |
|---|---|---|
| "Hi [First Name]" | That's a mail merge token. Every cold email uses first name. | Nothing — first name in the greeting is fine, it's just not personalization |
| "I saw you're the [Title] at [Company]" | Fill in any title and company, it works. | Reference something specific they did in that role |
| "Congrats on the role!" | Generic. | "Congrats on stepping into the VP role in September — the transition from manager-level to VP is where the hard strategic decisions start" |
| "I've been following your work closely" | Lie, unless the founder actually has | Reference one specific thing they've done |
| "I came across your profile and was impressed" | Impossible to verify, reads as flattery | Cut entirely |
| "Given your focus on enablement" | They're a VP of Sales Enablement. Obviously. | Reference the specific angle within enablement you want to talk about |
| "Companies like yours" | Generic category. | Reference something specific about *their* company |
| "As a fellow sales leader" | False mutual framing | Just make the point directly |

---

## The "Would I Know This If I'd Never Heard Of Them Before?" Test

Apply this test to every personalization sentence:

> If I swapped this sentence into a cold email to a different prospect with the same title and company size, would it still make sense?

If yes → not personalization. It's a generic template sentence masquerading as personalization.
If no → real personalization.

**Example:**
- "I saw you're the VP of Enablement at NorthStar and we help companies like yours..." → swap "NorthStar" for "MegaCorp" and it still works → **not personalization**
- "Your LinkedIn post last week about new-hire ramp time being misdiagnosed as a 'content problem' is exactly the observation I've been building around." → cannot swap prospects without breaking the reference → **real personalization**

---

## How To Find Personalization When The Prospect Has No Public Footprint

Some prospects are legitimately hard to personalize against — they don't post on LinkedIn, they don't write articles, their company doesn't make news. Options in order of preference:

1. **Use Tier 2 (observable buying trigger)** — company-level signals are easier to find than person-level.
2. **Use Tier 3 (company context)** — reference the company's stage or situation rather than the person.
3. **Use Tier 5 (inferred pain)** — grounded in the ICP, specific to the segment.
4. **Send the founder back to `prospect-researcher`** — if the row has no personalization surface, the prospect may need re-enrichment or may need to move to a lower tier (if they're not findable, maybe they're not a Tier A).

**Never** use this as a reason to fall back to fake personalization. If you can't personalize, either find a way to, or don't send.
