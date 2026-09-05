---
name: pre-meeting-prep
description: Combines bd-intelligence's account synthesis with meeting-specific framing, who's in the room, what's on the agenda, and what matters this time.
roles: [bd-executive]
integrations: [zoho, people-crm, microsoft-365]
---

# Pre-Meeting Prep Skill

## Purpose

Turn account-level synthesis into a meeting-ready brief: not just "what's true about this account" but "what matters for this specific conversation."

## When to Invoke

- "Prep me for my meeting with [account/person]"
- "What do I need to know before [meeting]"
- Any calendar-triggered or explicitly requested pre-meeting prep

## Process Flow

### 1. Identify the meeting

Pull meeting details from the calendar (Microsoft 365) if a specific meeting is referenced: attendees, stated agenda/subject, time.

### 2. Run bd-intelligence for the account

Get the live account synthesis (Zoho pipeline status, people-CRM relationship history, project engagement history, strategic narrative). Do not duplicate that skill's logic here. Invoke it.

### 3. Run bd-contact-research for each named attendee

For every attendee who is a real contact (not an internal Inspire11/Insight colleague), pull their individual research so the brief covers people, not just the account in the abstract.

### 4. Frame for this specific meeting

Layer the account and contact synthesis with meeting-specific framing:
- What's the stated or likely agenda
- What changed since the last interaction with this account/contact (from people-CRM timeline and Zoho's last-modified data)
- What warm-intro or channel-partner context is relevant if new people are in the room (invoke warm-intro-mapping if attendees are unfamiliar)
- What open threads or unresolved questions exist (from people-CRM's Open Threads section)

### 5. Present as a meeting brief, not an account file

This is a point-in-time briefing for the user, not a new standing document. Only save it if the user explicitly asks.

## Verify

- **No stale pipeline framing:** confirm the Zoho-derived pipeline status in this brief matches what bd-intelligence's own Verify step would produce. Don't let meeting framing override or soften a correctly-identified closed/prospect status.
- **Attendee coverage check:** confirm every external attendee named on the calendar invite was actually looked up, not skipped.
- **Distinguish fact from prep suggestion:** meeting framing (agenda guesses, suggested talking points) must be clearly separated from sourced facts (Zoho status, people-CRM history) so the user isn't left unsure what's verified versus suggested.
