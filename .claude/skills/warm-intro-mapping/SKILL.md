---
name: warm-intro-mapping
description: Queries people-CRM's existing relationship data for introduction paths into a target account, before any cold outreach is considered.
roles: [bd-executive]
integrations: [people-crm]
---

# Warm Intro Mapping Skill

## Purpose

Answer one question before any outreach: is there a person already in the relationship network who can make a warm introduction into this account? Cold outreach is the last resort, not the default.

## When to Invoke

- Before prospecting or expanding into any new account
- "Do I have a warm path into [account]"
- "Who can introduce me to [account/person]"

## Process Flow

### 1. Identify the target

Resolve the target account or person clearly before searching.

### 2. Search people-CRM for connection paths

Query `05-knowledge/people/` for any profile with:
- A direct relationship to the target account (current or former employee, board member, etc.)
- A stated connection to someone at the target account (mentioned in timeline entries or collaboration notes)
- Channel-partner relevance: an Insight Enterprises contact who owns or has visibility into the target account (see the `bd-executive` role pack's Notes section for the channel-partner protocol pattern)

### 3. Present the path, or the gap

If a path exists: name the connector, the hook (why the intro is credible), and who to ask.

If no path exists: say so plainly and identify what evidence would need to exist (e.g., "no one in people-CRM has a documented connection to this account yet") rather than fabricating a plausible-sounding path.

### 4. Expected state at launch

This vault starts with an empty people-CRM. Until profiles accumulate through contact-auto-capture and bd-contact-research, this skill will correctly return "no path found" for most accounts. That is expected, not a bug. Do not manufacture a path to avoid an empty result.

## Verify

- **No fabrication:** never invent a connection that isn't evidenced by an actual people-CRM profile or timeline entry.
- **Recency check:** if a path is found, check the timeline entry's date. A connection from years ago may no longer hold; flag it as "last confirmed [date]" rather than presenting it as current.
- **Empty result is a valid result:** an empty vault returning "no warm path found" is correct behavior, not a failure to search harder.
