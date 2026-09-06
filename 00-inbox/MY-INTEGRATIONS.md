---
type: integrations
created: 2026-09-05
tags: ["#integrations", "#config", "#cog"]
---

# My Integrations

*COG checks this file before using any external service. Edit anytime.*

## Active
- **Zoho CRM**: System of record for pipeline. Queried live for account and deal status, never cached in vault files.
- **Microsoft 365**: Email and calendar history for contact research, auto-capture, and meeting prep. Provided by the account-level Microsoft 365 connector (confirmed working via a direct call), not a project-scoped registration in this vault. There is nothing to configure here for it to work.
- **Slack**: Team coordination and recurring intelligence delivery.
- **Massive Market Data**: Public-company news and SEC filings for account-level economic context.
- **Minutes**: Meeting capture and transcription only. Its own person-profile and relationship-map tools are never invoked. That job belongs to people-CRM.
- **Mnemoverse**: Cross-tool memory.
- **Apify**: Standing connector for private-company press-release monitoring and hiring-intent signals.

## Manual / On-Demand (not a standing connector)
- **Seamless.ai**: Pitch Intelligence, used as a manual research input when the user supplies it, never fetched automatically.
- **Apify company-website-intelligence actor**: Run manually on demand, output supplied by the user when relevant. Distinct from the standing Apify connector above.

## Disabled
- **GitHub**: Skipped during onboarding. Enable anytime by moving to Active section.
- **Linear**: Skipped during onboarding. Enable anytime by moving to Active section.
- **PostHog**: Skipped during onboarding. Enable anytime by moving to Active section.
- **Notion**: Skipped during onboarding. Enable anytime by moving to Active section.
- **Jira**: Skipped during onboarding. Enable anytime by moving to Active section.
- **Fireflies**: Skipped during onboarding. Enable anytime by moving to Active section.
- **ElevenLabs**: Not requested. Enable anytime by moving to Active section.

---

*Move services between Active and Disabled sections to control what COG connects to.*
