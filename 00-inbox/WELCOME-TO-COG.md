---
type: guide
created: 2026-09-05
tags: ["#welcome", "#getting-started", "#cog"]
---

# Welcome to Your COG Second Brain, Jonathan!

Your COG is now personalized and ready to use. Here's how to get started:

## Your Profile Documents

- **[[MY-PROFILE]]**: Your basic info, role pack, and workflow preferences
- **[[MY-INTERESTS]]**: Topics for your daily briefs
- **[[MY-INTEGRATIONS]]**: Your active and disabled integrations

**You can edit these files anytime.** COG reads them when you use skills, so your changes take effect immediately.

## Skills for Your Role

As a **Business Development Executive**, these skills are ordered by relevance for you:

1. **bd-intelligence**: On-demand account synthesis from live Zoho status, people-CRM history, project history, and strategic narrative. No stale cached pipeline view.
2. **bd-contact-research**: Deep pre-meeting research on a specific contact.
3. **pre-meeting-prep**: Account synthesis plus meeting-specific framing.
4. **contact-auto-capture**: Creates a people-CRM stub the moment a real interaction happens with someone new.
5. **warm-intro-mapping**: Finds the fastest path to a warm conversation before cold outreach.
6. **auto-research**: Deep strategic research for cross-domain questions.
7. **braindump**: Fast capture of deal thoughts and strategic ideas.
8. **meeting-transcript**: Turn call recordings into structured notes and follow-ups.

## Your Integrations

**Active**: Zoho CRM, Microsoft 365 (via the account-level connector), Slack, Massive Market Data, Minutes (capture/transcription only), Mnemoverse, Apify
**Manual/on-demand**: Seamless.ai, Apify company-website-intelligence actor
**Disabled**: GitHub, Linear, PostHog, Notion, Jira, Fireflies, ElevenLabs

You can change these anytime by editing [[MY-INTEGRATIONS]].

## Quick Start

### 1. Account Intelligence
Invoke bd-intelligence for any account to get a live synthesis. Pipeline status is pulled fresh from Zoho, never cached.

### 2. Capture Your Thoughts
Use the braindump skill to quickly capture deal ideas, meeting reactions, and strategic thoughts.

### 3. Before Any Outreach
Run warm-intro-mapping first. Cold outreach is the last resort, not the default. See the `bd-executive` role pack's Notes section for why.

## Starting State

This vault starts empty by design: no stored account entities, no imported people-CRM profiles, no ported automation. `05-knowledge/people/` will build up naturally through contact-auto-capture and bd-contact-research as real interactions happen. `00-inbox/PENDING-WARM-INTRO-REENTRY.md` has a punch-list of real introduction paths found in the prior vault's records, waiting for profiles to attach them to.

## Keeping COG Updated

COG separates your content from framework files. When new versions are released:
- Run `/update-cog` to check for and apply updates
- Your braindumps, profiles, and notes are **never** touched by updates

Check your current version: `cat COG-VERSION`

**Your second brain is learning about you. Let's begin!**

---

*You can archive or delete this welcome guide once you're comfortable with COG.*
