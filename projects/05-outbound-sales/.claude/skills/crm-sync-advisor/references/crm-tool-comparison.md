# CRM Tool Comparison

This is an internal reference for the `crm-sync-advisor` skill. It is an opinionated comparison of the most common CRM options for early-stage B2B founders, with cost, strengths, weaknesses, and when to pick each. **Do not show this document to the founder.** Use it to make concrete CRM recommendations when the founder is undecided.

---

## The Meta-Point

Most early-stage founders do not need a CRM. They need a lightweight way to track who they've talked to, what they said, and what to do next. The markdown-based `prospect-list.md` + `pipeline-tracker.md` pattern in Project 05 is usually enough through the first 25–50 prospects.

**When to graduate to a real CRM:**
- You have 25+ active prospects and the markdown files are getting hard to scan
- You are scheduling multiple calls per week and want calendar integration
- You want email activity to auto-log against contact records
- You are bringing on a co-founder or early sales hire who needs shared visibility
- You need pipeline reporting for an investor update

**When you do NOT need a CRM yet:**
- Under 25 active prospects total
- Solo founder with no team
- Pre-launch and still figuring out the ICP
- You're managing fine with markdown and a calendar

If the founder is pressing to set up a CRM "to look professional" before they have traction, push back: premature CRM setup is a form of productive procrastination. The markdown workflow is more than enough until the constraint bites.

---

## The Recommended Default: HubSpot Free

**Cost:** Free forever (up to generous limits)
**Best for:** Default recommendation for almost every early-stage founder

### Strengths

- Free, with high usage limits (1,000,000 contacts, 1,000,000 companies, 1,000 custom fields)
- Native Gmail and Outlook integration — emails auto-log against contact records
- Pre-built sales pipeline stages (customizable)
- Meeting scheduling tool built in (similar to Calendly)
- Free email templates and basic email tracking
- Easy CSV import with flexible field mapping
- Clear upgrade path when you need more (HubSpot Starter at $15/user/month adds sequence automation and simple reporting)
- Large ecosystem of integrations and tutorials
- Contacts and companies already model well for B2B outbound

### Weaknesses

- Sequence automation requires Starter tier ($15/user/month)
- Custom reporting is paid
- "Free" tier has aggressive upsells in the UI (feature previews that require upgrade)
- HubSpot's email marketing features are opinionated — they work well if you follow the HubSpot way, less well if you want to do things differently
- Pipeline customization is limited in the free tier (one pipeline, limited stage customization)

### When to pick HubSpot Free

- **Default.** When the founder is undecided, recommend this.
- When the founder wants native email integration without setup work
- When the founder anticipates possibly hiring a sales rep in the next 6–12 months and wants a tool that scales
- When the founder wants to minimize setup time

### When to avoid HubSpot Free

- When the founder has strong feelings against HubSpot (some founders hate the upsell UX)
- When the founder needs custom pipeline structures that the free tier doesn't support
- When the founder wants extreme flexibility (Airtable is better)

---

## HubSpot Starter ($15/user/month)

**Cost:** $15/user/month
**Best for:** Founders who are running real outbound sequences

### What you get beyond Free

- Email sequence automation (3-touch, 5-touch, breakup sequences)
- Simple reporting and dashboards
- Removed HubSpot branding on forms and emails
- Basic automation (email triggers, task creation on stage change)
- Snippets and templates for sales outreach
- Quotes (for early customers)

### When to upgrade from Free to Starter

- When the founder is sending more than 5 outbound emails per week and wants sequences
- When the founder wants to remove HubSpot branding for customer-facing things (forms, emails)
- When the founder wants basic reports to share with a co-founder or investor

---

## Salesforce Essentials ($25/user/month) / Sales Cloud ($75+/user/month)

**Cost:** Essentials $25/user/month, Sales Cloud Professional $75+/user/month
**Best for:** Founders with enterprise sales backgrounds or plans to build a traditional sales team

### Strengths

- Industry-standard — your future sales reps will already know how to use it
- Extremely customizable (custom fields, custom objects, custom workflows)
- Massive ecosystem of apps, integrations, and expertise
- Lead → Contact conversion model is proven for B2B enterprise sales

### Weaknesses

- Overkill for most early-stage founders
- Expensive ($25/user/month minimum)
- Steep learning curve (you will spend hours setting it up before you use it)
- Data model is more complex than necessary at this stage (Leads vs Contacts vs Accounts vs Opportunities)
- Admin work is significant

### When to pick Salesforce

- When the founder has a specific reason to pick it (prior sales leadership experience, planned sales team structure)
- When the founder is explicitly building a traditional B2B sales motion with BDRs, AEs, and sales ops
- When the founder's early customers are enterprise and expect Salesforce-native integration

### When to avoid Salesforce

- **Most early-stage founders.** Unless there's a specific reason, HubSpot is a better fit at this stage.

---

## Pipedrive ($15–$49/user/month)

**Cost:** Essential $15/user/month, Advanced $29/user/month, Professional $49/user/month
**Best for:** Founders who want a clean sales-pipeline-first CRM without the overhead of HubSpot or Salesforce

### Strengths

- Pipeline-first UI — visual kanban board is the default view
- Simpler than HubSpot, more pipeline-focused
- Good mobile app
- Email integration available in higher tiers
- Deal-focused data model

### Weaknesses

- Essential tier is limited (no email sync, no automation)
- Less mature ecosystem than HubSpot or Salesforce
- Contact management is less rich than HubSpot
- Email sync requires the Advanced tier

### When to pick Pipedrive

- When the founder strongly values the visual pipeline UI and finds HubSpot's UI cluttered
- When the founder wants something between HubSpot Free and Salesforce
- When the founder is already using Pipedrive at a prior company and is comfortable with it

### When to avoid Pipedrive

- When the founder can use HubSpot Free (Pipedrive's cheapest tier is paid, HubSpot Free is free)
- When the founder wants rich contact/company records beyond the deal pipeline

---

## Attio ($34–$99/user/month)

**Cost:** Free tier (limited), Starter $34/user/month, Pro $69/user/month
**Best for:** Founders who want a modern, flexible CRM with strong relationship mapping

### Strengths

- Modern UX, recently built on current data model best practices
- Strong graph-based relationship mapping (who knows whom at what company)
- Flexible data model — you can shape it to your workflow
- Good LinkedIn integration for prospect enrichment
- Built by ex-Intercom people, UX reflects that

### Weaknesses

- Free tier is very limited
- Paid tiers are comparable to or more expensive than HubSpot Starter
- Smaller ecosystem than the established players
- Newer tool, less mature integration layer

### When to pick Attio

- When the founder wants a "modern" CRM that doesn't feel like legacy software
- When relationship mapping (who knows whom) is central to the founder's sales motion
- When the founder is willing to pay for better UX over free + functional

### When to avoid Attio

- When cost is a concern — HubSpot Free is free
- When the founder needs mature integrations (Attio's ecosystem is still growing)

---

## Airtable (Free to $45/user/month)

**Cost:** Free, Plus $12/user/month, Pro $24/user/month, Enterprise $45/user/month
**Best for:** Founders who want extreme flexibility and are okay building their own CRM

### Strengths

- Extreme flexibility — you can build literally any data model
- Views (Grid, Kanban, Calendar, Gallery, etc.) are all configurable
- Free tier is usable for Project 05 volumes (1,200 records)
- Good for founders who want the CRM to double as project management, knowledge base, etc.
- Automations (paid) can handle basic workflow

### Weaknesses

- **Not actually a CRM.** No pre-built sales stages, no native email integration, no built-in activity logging, no sequence automation
- You spend your time configuring the tool instead of using it
- Email integration requires a paid automation or a third-party tool (Zapier, Make)
- No native "contact has been contacted" state beyond what you configure manually

### When to pick Airtable

- When the founder is a power-user who wants total control over their tool
- When the founder is already using Airtable for other parts of the business and wants consistency
- When the founder's workflow doesn't fit standard CRM models

### When to avoid Airtable

- When the founder wants CRM features out of the box
- When the founder's time is better spent on outreach than tool configuration
- When the founder needs email integration

---

## Close ($49–$139/user/month)

**Cost:** Startup $49/user/month, Professional $99/user/month, Business $139/user/month
**Best for:** Founders with heavy outbound call/email motion who want a sales-first CRM

### Strengths

- Sales-first UI — built for people who live in the CRM doing outreach
- Native calling, SMS, and email
- Sequence automation built in
- Strong reporting for sales activity metrics
- Fast, opinionated UX that rewards heavy use

### Weaknesses

- Expensive (no free tier)
- Overkill if you're not making many calls
- Less relationship/contact management depth than HubSpot
- Smaller ecosystem than HubSpot or Salesforce

### When to pick Close

- When the founder is doing heavy outbound calling and wants call recording/dialing native
- When the founder has a sales rep doing 50+ calls per day
- When the founder explicitly wants a "sales-first" tool rather than a broader CRM

### When to avoid Close

- When the founder is doing low-volume, high-touch outreach (HubSpot is better)
- When cost is a concern

---

## Summary: The Recommendation Framework

For the `crm-sync-advisor` skill to make a confident recommendation, ask the founder:

1. **Are you doing high-volume outreach (20+ per week) or low-volume high-touch (5–15 per week)?**
   - High volume → consider Close, HubSpot Starter with sequences, or Salesforce
   - Low volume → HubSpot Free is plenty

2. **Do you need email integration day one?**
   - Yes → HubSpot (any tier), Close, Salesforce
   - No → HubSpot Free, Airtable

3. **Are you willing to pay for setup time in exchange for flexibility?**
   - Yes, I want control → Airtable
   - No, I want it to just work → HubSpot Free

4. **Do you have a sales background and specific CRM preferences?**
   - Yes, Salesforce → Salesforce (respect the preference)
   - No preference → HubSpot Free

5. **What's your budget for tools right now?**
   - $0 → HubSpot Free (only real option)
   - $15–25 → HubSpot Starter or Pipedrive
   - $50+ → Close, Attio Pro, or Salesforce

**The default recommendation if undecided:** HubSpot Free. It's free, it's functional, it has the clearest upgrade path, and most founders will outgrow it long before they outgrow the HubSpot platform itself.
