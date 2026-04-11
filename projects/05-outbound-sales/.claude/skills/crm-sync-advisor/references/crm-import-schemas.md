# CRM Import Schemas

This is an internal reference for the `crm-sync-advisor` skill. It is the canonical field-mapping schemas for HubSpot, Salesforce, and Airtable — the three most likely CRM destinations for early-stage founders. **Do not show this document to the founder.** Use it to produce the correct CSV headers and field values for the target CRM.

---

## HubSpot (Free and Starter)

**Target CRM:** HubSpot Free or HubSpot Starter ($15/user/month)
**Import method:** Contacts → Import → From a file (CSV)
**Import order:** Companies first, then Contacts

### contacts.csv columns

| Column Header | Required? | Source in prospect-list.md / pipeline-tracker.md | Notes |
|---|---|---|---|
| First Name | required | parsed from Name field | split on space; if single name, put in First Name |
| Last Name | required | parsed from Name field | everything after first space |
| Email | not required | Email field (empty if `[email_unknown]`) | primary dedup key in HubSpot |
| Company | required | Company field | must match an entry in companies.csv |
| Job Title | not required | Role field | |
| Phone | not required | parse from Notes if present | usually empty |
| Lifecycle Stage | not required | mapped from Stage (see below) | HubSpot enum — use exact values |
| Lead Status | not required | mapped from Stage (see below) | HubSpot enum — use exact values |
| Notes | not required | Notes + merge from pipeline-tracker | prefix pipeline data with "[Pipeline]:" |

### HubSpot Lifecycle Stage mapping

HubSpot has a fixed Lifecycle Stage enum:
```
Subscriber, Lead, Marketing Qualified Lead, Sales Qualified Lead, Opportunity, Customer, Evangelist, Other
```

Map Project 05 pipeline stages as follows:

| Project 05 Stage | HubSpot Lifecycle Stage |
|---|---|
| Prospecting | Lead |
| Contacted | Lead |
| Replied | Marketing Qualified Lead |
| Meeting Scheduled | Sales Qualified Lead |
| Design Partner Conversation | Opportunity |
| Committed | Customer |
| Lost | Other |
| Stalled | Lead |

### HubSpot Lead Status

HubSpot's default Lead Status options:
```
New, Open, In Progress, Open Deal, Unqualified, Attempted to Contact, Connected, Bad Timing
```

Map Project 05 pipeline stages:

| Project 05 Stage | HubSpot Lead Status |
|---|---|
| Prospecting | New |
| Contacted | Attempted to Contact |
| Replied | Connected |
| Meeting Scheduled | In Progress |
| Design Partner Conversation | Open Deal |
| Committed | (stage shifts to Customer, Lead Status not applicable) |
| Lost | Unqualified |
| Stalled | Bad Timing |

### companies.csv columns

| Column Header | Required? | Source | Notes |
|---|---|---|---|
| Company Name | required | from contacts | dedup natural key |
| Domain | recommended | infer from email domain | without http:// prefix, just the bare domain |
| Industry | not required | from Notes if captured | |
| Number of Employees | not required | from Notes if captured | |
| Lifecycle Stage | not required | highest stage among contacts | |

### HubSpot import gotchas

- **Duplicate detection on email:** HubSpot dedups contacts on email address. Contacts with empty email will NOT dedupe and can create multiple rows if you re-import. The first import is safe; re-imports need manual dedup.
- **Company association:** HubSpot auto-associates contacts to companies by the `Company` field in contacts.csv matching the `Company Name` in companies.csv. Must be an exact string match (case-insensitive).
- **Custom stage enum:** If the founder wants the exact Project 05 stage names (Prospecting, Contacted, etc.) preserved, they'll need to create a custom field in HubSpot. Use the Notes field to preserve the raw stage for now; they can create the custom field post-import.
- **Free tier limits:** HubSpot Free supports up to 1,000,000 contacts, so founders are fine. Paid features that are NOT in free: email sequence automation, custom reports, advanced pipeline management.

---

## Salesforce (Essentials and Sales Cloud)

**Target CRM:** Salesforce Essentials ($25/user/month) or Sales Cloud
**Import method:** Data Import Wizard (for small imports) or Data Loader (for large ones)
**Import order:** Accounts first, then Contacts and Leads

**Note:** Salesforce is usually overkill for founders at this stage. Most founders who choose Salesforce already have enterprise context or a revenue team. If the founder is undecided and asking about Salesforce, consider pushing back to HubSpot Free unless they have a specific reason.

### Salesforce data model

Salesforce uses a different data model than HubSpot:
- **Lead** — an unqualified prospect (before they've been "converted" to a Contact)
- **Contact** — a qualified person who belongs to an Account
- **Account** — the company (equivalent to HubSpot's Company)
- **Opportunity** — a potential deal

For Project 05 export, most prospects should go in as **Leads**, not Contacts, because they have not been qualified through a Salesforce sales motion yet. Contacts are for post-qualification.

### leads.csv columns (use instead of contacts.csv for Salesforce)

| Column Header | Required? | Source | Notes |
|---|---|---|---|
| First Name | required | parsed from Name | |
| Last Name | required | parsed from Name | |
| Email | required | Email field | Salesforce validates email format on import |
| Company | required | Company field | used for account matching post-conversion |
| Title | not required | Role field | |
| Phone | not required | from Notes | |
| Lead Source | not required | Source field (LinkedIn, G2, Referral, etc.) | Salesforce enum |
| Status | not required | mapped from Stage (see below) | Salesforce Lead Status enum |
| Rating | not required | mapped from ICP Tier | Tier A → Hot, Tier B → Warm, Tier C → Cold |
| Description | not required | Notes + pipeline data | |

### Salesforce Lead Status mapping

Salesforce default Lead Status enum:
```
Open - Not Contacted, Working - Contacted, Closed - Converted, Closed - Not Converted
```

Map Project 05 stages:

| Project 05 Stage | Salesforce Lead Status |
|---|---|
| Prospecting | Open - Not Contacted |
| Contacted | Working - Contacted |
| Replied | Working - Contacted |
| Meeting Scheduled | Working - Contacted |
| Design Partner Conversation | Working - Contacted |
| Committed | Closed - Converted |
| Lost | Closed - Not Converted |
| Stalled | Open - Not Contacted |

### accounts.csv columns (companies)

| Column Header | Required? | Source | Notes |
|---|---|---|---|
| Account Name | required | from prospects | |
| Website | recommended | infer from email domain | |
| Industry | not required | from Notes | |
| Number of Employees | not required | from Notes | Salesforce expects integer |
| Type | not required | always "Prospect" at this stage | |

### Salesforce import gotchas

- **Email required for Leads:** Salesforce requires an email on the Lead object. Contacts with `[email_unknown]` will fail the import. Handle by either (a) excluding those prospects from the Salesforce export, or (b) using a placeholder email format like `unknown+sarah-chen-northstar@prospect-list.local` that the founder can update later.
- **Lead vs Contact:** Unlike HubSpot, Salesforce distinguishes Leads (unqualified) from Contacts (qualified and associated with an Account). For an outbound export at this stage, use Leads.
- **Data Import Wizard vs. Data Loader:** Data Import Wizard handles up to 50,000 records and is simpler. Data Loader is for larger imports or more complex field mapping. For Project 05 exports (typically under 100 prospects), use Data Import Wizard.
- **Rating field:** Salesforce has a "Rating" field with enum values Hot / Warm / Cold. Map ICP Tier A → Hot, Tier B → Warm, Tier C → Cold. This gives the founder a native sorting option post-import.

---

## Airtable

**Target "CRM":** Airtable (not technically a CRM, but commonly used as one)
**Import method:** CSV import into an Airtable base
**Import order:** Companies table first, then Contacts table (linked by record ID)

**Note:** Airtable is not a real CRM. It's a database with a spreadsheet UI. Founders who pick Airtable are usually doing so for flexibility, not for sales workflow. It has no built-in sales sequence features, no email integration without a paid automation, and no pipeline UI out of the box. Warn the founder if they're picking Airtable expecting CRM features.

### contacts table columns

| Column Header | Field Type | Source | Notes |
|---|---|---|---|
| Name | Single line text | Name | |
| Email | Email | Email field | empty if unknown |
| Company | Link to Companies | Company name | links to Companies table by name |
| Role | Single line text | Role | |
| Source | Single line text | Source field | |
| Stage | Single select | Stage from pipeline-tracker | custom enum matching Project 05 stages |
| Last Touch | Date | from pipeline-tracker | ISO date format |
| Next Action | Single line text | from pipeline-tracker | |
| ICP Tier | Single select | A/B/C/D | custom enum |
| Notes | Long text | merged notes | |

### companies table columns

| Column Header | Field Type | Source | Notes |
|---|---|---|---|
| Company Name | Single line text (primary) | dedup from contacts | primary key |
| Domain | URL | infer from email | |
| Industry | Single line text | from Notes | |
| Number of Employees | Number | from Notes | |
| Contact Count | Rollup from Contacts table | auto-calculated | |
| Highest Stage | Rollup from Contacts table | auto-calculated (MAX over stages) | |

### Airtable import gotchas

- **Linking fields require two imports:** Import companies first, then import contacts — and you'll need to set up the "Company" column in contacts as a Link field pointing to the Companies table. Airtable handles this during CSV import if you match on Company Name.
- **Custom stage enum:** Unlike HubSpot and Salesforce, Airtable has no predefined sales stages. You'll need to create Single Select fields with custom options. Project 05 stages can be used exactly as-is: `Prospecting | Contacted | Replied | Meeting Scheduled | Design Partner Conversation | Committed | Lost | Stalled`.
- **Free tier limits:** Airtable Free supports 1,200 records per base and 2GB attachment storage. More than enough for Project 05 export sizes.
- **No native email integration:** To send email from Airtable and log it in the contact's record, you need an Airtable Automation (paid) or a third-party integration like Zapier or Make. Warn the founder.

---

## Choosing Between Them (For The Founder)

| Criterion | HubSpot Free | Salesforce Essentials | Airtable |
|---|---|---|---|
| Cost | Free | $25/user/month | Free (up to limits) |
| Sales stages | Pre-built, customizable | Pre-built, customizable | DIY |
| Email integration | Native (Gmail, Outlook) | Native (Gmail, Outlook) | Paid automation required |
| Pipeline view | Native | Native | DIY |
| Sequences / automation | Paid (Starter tier) | Native | Paid automation required |
| Complexity | Low | Medium-High | Medium |
| Migration cost when outgrowing | Low (stay on HubSpot) | Low (stay on Salesforce) | High (must migrate to real CRM) |
| **Best for** | **Default for this stage** | Enterprise-mindset founders | Flexibility-first founders |

---

## Fallback For Other CRMs (Pipedrive, Attio, Close, Copper, etc.)

If the founder wants a CRM not in the above list, use a **generic CRM schema** and document it in the README:

### generic contacts.csv columns

```
First Name, Last Name, Email, Company, Job Title, Stage, Source, Notes
```

### generic companies.csv columns

```
Company Name, Domain, Industry, Employees, Stage
```

Most CRMs accept this format for import and allow the founder to map fields during the import flow. Note in the README that field mapping is CRM-specific and the founder should check the target CRM's import documentation.
