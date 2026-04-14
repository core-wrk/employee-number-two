# Invitation Email Patterns

Internal reference for `beta-recruiter`. Use as the structural template for every early-access invitation. Every draft must hit every element — but the copy should read like the founder wrote it personally, not like a template.

---

## Structure

Every invitation has five elements in order:

1. **Subject line** — specific, not generic. Mentions their context or the thing they signed up for.
2. **Personalization anchor** — opening sentence references something concrete from the waitlist signup.
3. **The offer** — what they get access to, described in one or two sentences using `product-overview.md` language.
4. **The ask** — what is asked of them in return. Explicit, bounded, low-friction.
5. **The accept** — one click or one reply. Never two.

## Subject line patterns

Good:
- "Early access — [product name] for [role]"
- "[Name], the [product category] you signed up for"
- "Your early-access invite to [product name]"

Bad:
- "You're invited!" (generic, looks like a marketing blast)
- "Quick favor" (vague, feels like a cold ask)
- "Re: [product name]" (fake reply thread, erodes trust)

Subject should survive inbox preview without the body — the recipient should know who it is from and what it is about.

## Opener patterns

The opener references a specific detail from the waitlist signup. If the waitlist has no usable detail, the entry should be flagged for enrichment before invitation, not drafted against.

Examples:
- "You signed up for [product] back in [month] — I noticed you mentioned [specific pain point from the note]. We just opened early access and I wanted you to be one of the first in."
- "When you joined the waitlist you said you were looking for [use case]. That's exactly what I've been building, and I'd love for you to try it before we go wider."
- "I saw your note about [specific detail] when you signed up. We're now inviting a small group of early-access users and your context is exactly the one I want to learn from."

## Offer patterns

One or two sentences. Describe the product in `product-overview.md` language, not marketing fluff. Name one concrete capability the recipient will immediately find useful.

Examples:
- "You'll get access to [product] — [one-line description from product-overview.md]. In the first session you'll be able to [specific capability]."
- "Early access includes [specific scope — full product / core feature only / limited by X]. No paywall during the access period."

## Ask patterns

The ask is what differentiates an invitation from a marketing email. Name it explicitly. Keep it bounded.

Strong asks:
- "One 30-minute call in the first two weeks so I can watch you use it and learn what's broken."
- "A short survey at the 30-day mark — five questions, should take under five minutes."
- "Just your honest feedback whenever you hit something frustrating. No formal commitment."

Weak asks (avoid):
- "Your feedback" (too vague)
- "A few hours of your time" (too heavy, feels open-ended)
- "To be a design partner" (heavy commitment language; reframe as early access)

Match the ask to the cohort's learning goal. If the goal is onboarding usability, a watch-along call is the right ask. If the goal is value perception over time, a 30-day survey is better.

## Accept patterns

One action. Never two. Never "reply and then schedule and then we'll send you a link."

Strong:
- "Click here to activate your account: [link]"
- "Reply 'in' and I'll send your login by end of day."
- "Pick a time on my calendar and I'll walk you through setup: [link]"

Friction that kills acceptance:
- NDAs or legal docs before access
- Multi-step scheduling flows
- Requesting payment info "just in case"

If the founder has a business reason for any of these, surface it explicitly — but the invitation copy itself should hide it until after accept.

## Close and signature

Sign with the founder's real name and role (pull from `founder-profile.md`). A one-line P.S. mentioning the founder's availability or a second reason to act can lift conversion but is optional.

## Length guidance

Target 80–150 words for the body. Longer invitations feel formal and get skimmed. Shorter invitations feel generic.

## What not to include

- Feature lists longer than two items
- Marketing superlatives ("revolutionary", "game-changing")
- Roadmap promises ("we'll be adding X, Y, Z next quarter")
- Pricing talk (this is early access; pricing is Project 09's job)
- Social proof the recipient cannot verify ("500 companies signed up" — irrelevant to this recipient)
- Anything that sounds like the user is doing the founder a favor by accepting (they are, but the email should not feel transactional)
