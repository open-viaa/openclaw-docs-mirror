# Docs Mirror Automation

## Why we did this
We want a docs-first workflow based on official OpenClaw source, not random web advice.
This mirror keeps our reference docs fresh and reduces conflicting guidance.

## What this does
- Pulls latest docs from `openclaw/openclaw`
- Syncs selected docs content into our mirror flow
- Pushes updates to this repo on branch `docs-sync`
- Runs automatically every 2 days via OpenClaw cron
- Sends status updates to Telegram

## Automation details
- Local path: `/Users/bot/github/openclaw-docs-sync`
- Script: `sync-docs.sh`
- Scheduler: OpenClaw cron job `github-docs-sync` (every 2d)

## One-time setup required
GitHub push auth must be configured on the host machine (PAT over HTTPS or SSH key).
Without auth, sync runs but push fails.

## Troubleshooting
If sync fails with:
`fatal: could not read Username for 'https://github.com': Device not configured`
then configure GitHub credentials on the host and test:
`/Users/bot/github/openclaw-docs-sync/sync-docs.sh`
