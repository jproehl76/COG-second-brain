---
type: spec
created: 2026-09-05
status: not-yet-activated
tags: ["#cowork", "#automation", "#pending"]
---

# Cowork Routine Spec: Daily BD Digest

Not yet wired up. This is a specification for the user (or a future session with the right scheduling access) to configure, not a live routine. Nothing here has been activated or connected.

## Cadence
Daily, weekday mornings only (Monday through Friday).

## Access model
Connector-only. No local vault file access needed. This routine should run entirely against live connectors, not read or write any file in this vault.

## Connectors used
- **Zoho**: pipeline movement (stage changes, new deals, closed deals) since the last run
- **People-CRM equivalent / contact capture**: new contacts captured since the last run
- **Massive Market Data**: competitive and account signals for public companies in the pipeline
- **Apify**: private-company press releases and hiring-intent signals for private companies in the pipeline

## Output
Posted to Slack. Channel to be confirmed by the user before activation.

## Content shape
1. Pipeline movement: what changed in Zoho since the prior run
2. New contacts: anyone captured since the prior run
3. Signals: public-company news (Massive Market Data) and private-company press/hiring signals (Apify) relevant to active accounts

Apply the `no-ai-slop` collateral standard (see `bd-executive` role pack Notes and `MY-PROFILE.md` Notes) to this digest before it posts. No filler, no fake-profound framing, lead with what actually changed.

## Portability requirement
Write the eventual implementation so moving from desktop-local to a cloud-hosted routine is a configuration change (where it runs, what triggers it), not a rewrite of what it does or how it sources data. Keep the connector list and content logic identical across both.

## Open items before activation
- Confirm the target Slack channel
- Confirm the actual scheduling mechanism (this vault's session tooling could not create durable recurring automation; whatever runs this needs to be set up through the Claude app's own scheduling feature, or an equivalent the user has access to)
- Decide how "since the last run" state is tracked once a real scheduler exists
