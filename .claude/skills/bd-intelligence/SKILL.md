---
name: bd-intelligence
description: Synthesizes account background on demand from live Zoho pipeline status, people-CRM relationship history, project engagement history, and tagged strategic narrative. No stored account entities, nothing here is cached as a standing file.
roles: [bd-executive]
integrations: [zoho, people-crm]
---

# BD Intelligence Skill

## Purpose

Give a complete, current picture of an account by synthesizing four live sources at query time. This skill never writes a standing "account file." Per this vault's architecture, account status lives in Zoho and account background is computed fresh every time, not cached in a form that can drift from source.

## When to Invoke

- "Brief me on [account]"
- "What's the status of [account]"
- Pipeline review, deal strategy discussion, or any account-specific question

## Process Flow

### 1. Resolve the company name against Zoho

Query Zoho live for accounts matching the name given. Resolve fuzzy or partial names (e.g., "UHG" → "United Healthcare Group / Optum") against Zoho's own account records at query time. Do not use a cached alias map. If more than one plausible match exists, confirm which one with the user before proceeding.

### 2. Pull live pipeline status from Zoho

For the resolved account, pull every deal record: stage, value, probability, close date, owner, last-modified date. This is the **only** source for pipeline status. Never infer deal stage from email content, meeting notes, or any other signal. That produces exactly the kind of stage-collision bug this vault's architecture rules exist to prevent.

**Pipeline membership definition:** read Zoho's own stage picklist live and identify which stages are closed (won or lost). An account is "open pipeline" only if it has at least one deal whose stage is not in that closed set. An account with zero open deals is closed or prospect, regardless of any other signal (email volume, meeting recency, etc.).

### 3. Pull relationship history from people-CRM

For every contact in `05-knowledge/people/` linked to this account, pull their compiled truth (role, working style, collaboration notes) and relevant timeline entries.

### 4. Pull engagement history from 04-projects/

If an active or past project exists for this account, pull its overview and status.

### 5. Pull strategic narrative from 05-knowledge/

Search `05-knowledge/consolidated/`, `05-knowledge/patterns/`, and any tagged notes mentioning the account by name for strategic context (deal philosophy, competitive positioning, prior decisions).

### 6. Synthesize

Combine into a single response, organized: live pipeline status (from Zoho) → relationship context (from people-CRM) → engagement history (from projects) → strategic narrative (from knowledge notes). Do not create a file unless the user explicitly asks to save the synthesis as a note.

## Verify

Run before presenting any synthesis:

- **Zero-open-deals check:** if the synthesis is about to describe the account as "open," "in pipeline," or "active," re-confirm at least one Zoho deal record is in a non-closed stage. If not, correct the framing. The account is closed or prospect.
- **Acceptance check, NMDP:** if the resolved account is or resembles NMDP, confirm the live Zoho query returns closed status. It must never present as open pipeline in this synthesis.
- **Acceptance check, Lucem Health:** confirm classification matches whatever Zoho's live stage is for Lucem Health at query time. Do not assume a fixed status from memory or a prior conversation.
- **Single-writer discipline:** this skill only reads. It must never write to `deal_stage` or any other Zoho-owned field. If a downstream action needs a Zoho update, tell the user to make it in Zoho directly.
- **Name resolution sanity check:** if the resolved Zoho account name differs meaningfully from what the user typed, state the resolution explicitly ("Resolved to [X] in Zoho") rather than silently substituting it.
