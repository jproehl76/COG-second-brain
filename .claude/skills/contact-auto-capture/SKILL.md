---
name: contact-auto-capture
description: Reads Microsoft 365/Outlook and creates a people-CRM Tier 3 stub the moment a real, individual interaction happens with a new person. Never triggers on bulk import.
roles: [bd-executive]
integrations: [microsoft-365, people-crm]
---

# Contact Auto-Capture Skill

## Purpose

Make sure a new contact never falls through the cracks, using this vault's existing people-CRM tiered-enrichment mechanism (`05-knowledge/people/README.md`) rather than inventing a new one.

## When to Invoke

- After processing an email thread, calendar invite, or meeting that surfaces a person not yet in `05-knowledge/people/`
- Not invoked as a standalone bulk scan, see Trigger Discipline below

## Trigger Discipline (critical)

This skill fires on **one genuine, individual interaction**: a real email exchange or calendar invite involving a specific named person at a known or new account. That single mention is sufficient. It satisfies people-CRM's own Tier 3 threshold (1 mention in a meeting or brief → name, role, one-line context; see `05-knowledge/people/README.md`).

It must **never** trigger from a bulk import, a mailing-list scan, or a mass CC list. If a batch of M365 data is being processed and many new names appear at once with no individual interaction evidence behind each one, do not auto-create stubs for all of them. That is bulk import, explicitly out of scope.

## Process Flow

### 1. Confirm this is a real interaction, not bulk noise

A direct email exchange, a calendar invite with the person as an attendee, or an explicit mention in meeting content, tied to one person. A person appearing only as one of dozens of CC'd addresses on a distribution email does not qualify.

### 2. Check for an existing profile

Look for `05-knowledge/people/<firstname-lastname>.md`. If it exists, this isn't a new-contact case. Hand off to bd-contact-research or the standard people-CRM update path instead.

### 3. Create the Tier 3 stub

Use `06-templates/people-profile-template.md`. Fill only what Tier 3 requires: name, role (if known), one-line context, and a single timeline entry citing the source interaction with a date and confidence level.

### 4. Do not over-fill

Do not populate Executive Snapshot, Working Style, Strengths, or Collaboration Notes from a single mention. That's Tier 2/Tier 1 territory per people-CRM's own escalation rules. Let it build naturally.

## Verify

- **Bulk-import guard:** before creating any stub, confirm the triggering event was one individual interaction, not a batch scan. If unsure, don't create the stub. Flag it for manual review instead.
- **No duplicate creation:** confirm no existing profile file (including near-miss name variants) already covers this person before creating a new one. This vault's prior history had duplicate-entity problems from exactly this kind of miss.
- **Citation present:** the created stub must have a source citation on its timeline entry in the standard format (`[Source: [[path]] | YYYY-MM-DD | confidence: level]`). No citation, no stub.
- **Single-writer discipline:** this skill only creates new Tier 3 stubs. It does not modify existing Tier 2/Tier 1 profiles. That's a different, evidence-driven update path.
