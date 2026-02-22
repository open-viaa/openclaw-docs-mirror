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

## GitHub auth bottleneck (common)
Use this exact sequence:

1. Run `gh auth login`
2. Choose: `GitHub.com` → `HTTPS` → `Yes` → `Login with a web browser`
3. Copy the one-time code shown in terminal
4. Press `Enter` in terminal (opens device page)
5. Complete approval in browser
6. Return to terminal and wait for `✓ Logged in as ...`
7. Verify with `gh auth status`

If browser says success but terminal is still waiting, login is not complete yet.
Go back to the same terminal session and finish it (do not `Ctrl+C` early).

## One-time setup required
GitHub push auth must be configured on the host machine.
Use `gh auth login` and verify with `gh auth status`.

## Quick verify
- `gh auth status`
- Manual run: `/Users/bot/github/openclaw-docs-sync/sync-docs.sh`
- Check scheduled jobs: `openclaw cron list`

## Public docs rules
- Keep docs concise and operational.
- Do not commit machine-specific sensitive details.
- Use placeholders for local paths/secrets in public docs.
