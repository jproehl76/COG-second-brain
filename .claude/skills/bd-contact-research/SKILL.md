---
name: bd-contact-research
description: Deep pre-meeting research on a specific contact from people-CRM, Microsoft 365 email/calendar history, Seamless.ai Pitch Intelligence (manual input), and the Apify website-intelligence actor (manual input).
roles: [bd-executive]
integrations: [people-crm, microsoft-365, seamless-ai, apify]
---

# BD Contact Research Skill

## Purpose

Build a complete picture of a specific person before a meeting or outreach, clearly separating what's live-verifiable from what was manually supplied.

## When to Invoke

- "Who is [name] at [company]"
- "Research [contact] before my call"
- Any request to understand a specific person, not an account as a whole (for account-level synthesis, use bd-intelligence)

## Process Flow

### 1. Check people-CRM

Look for `05-knowledge/people/<firstname-lastname>.md`. If it exists, pull the compiled truth and timeline. If it doesn't, note that this will be a first encounter (Tier 3 territory, see contact-auto-capture).

### 2. Pull Microsoft 365 interaction history

Search email and calendar for this contact: frequency of contact, most recent interaction, last topic discussed, meeting cadence. This is live data. Pull it fresh each time, don't reuse a stale summary.

### 3. Incorporate manual research inputs, clearly labeled

- **Seamless.ai Pitch Intelligence**: if the user has pasted or provided this, incorporate it, labeled "per Seamless.ai, as of [date supplied]." Never fetch this automatically. It is manual/on-demand, not a standing connector.
- **Apify company-website-intelligence actor output**: same treatment. Incorporate only what was actually provided, labeled with its source and date.

### 4. Never invoke Minutes' person-profile or relationship-map tools

Minutes is active for meeting capture and transcription only in this vault. Its own person-profile and relationship-mapping features are never called, even if technically available. That job belongs to people-CRM.

## Verify

- **Source tagging:** every fact in the output must be tagged by source (people-CRM / M365 / Seamless.ai-manual / Apify-manual). No unattributed claims.
- **Staleness labeling:** anything from a manual input is labeled with the date it was supplied, never presented as current/live.
- **No fabrication:** if an email address, title, or detail can't be found in any of the four sources, say so plainly. Never guess an email format or infer a title that isn't evidenced.
- **Confidence per claim:** follow people-CRM's own confidence convention (high/medium/low) for any claim being written back into a profile.
