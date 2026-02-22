# Docs Mirror Automation

## Why we did this
We want a docs-first workflow based on official OpenClaw source, not random web advice.
This mirror keeps our reference docs fresh and reduces conflicting guidance.

## What this does
- Pulls latest docs from `openclaw/openclaw`
- Pushes updates to this mirror repo
- Runs automatically every 2 days via **OpenClaw cron**
- Sends status updates after runs

## Scheduler (current)
- **System:** OpenClaw `cron` (not heartbeat)
- **Job name:** `github-docs-sync`
- **Cadence:** every `2d`
- **Mode:** isolated scheduled run

## One-time setup required
GitHub push auth must be configured on the host machine.
Use `gh auth login` and verify with `gh auth status`.

## Quick verify
- `gh auth status`
- Manual run: `/Users/bot/github/openclaw-docs-sync/sync-docs.sh`
- Check scheduled jobs: `openclaw cron list`

## Notes
- Do not commit machine-specific sensitive details to this public repo.
- Use placeholders in public docs for local paths and secrets.
