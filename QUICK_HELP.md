# Quick Help

## GitHub CLI auth (device flow) — common bottleneck

Use this exact sequence:

1. Run `gh auth login`
2. Choose: `GitHub.com` → `HTTPS` → `Yes` → `Login with a web browser`
3. Copy the one-time code shown in terminal
4. Press `Enter` in terminal (opens device page)
5. Complete approval in browser
6. Return to terminal and wait for `✓ Logged in as ...`
7. Verify: `gh auth status`

### Most common failure

If you see browser success but terminal is still waiting, the login is not complete yet.
Go back to the same terminal session and finish it (do not `Ctrl+C` early).

## Safe docs policy (public repo)

Never commit sensitive/machine-specific details:

- absolute local paths
- tokens/keys/secrets
- private hostnames or internal infra details

Use placeholders instead:

- `<LOCAL_SYNC_DIR>`
- `<SYNC_SCRIPT_PATH>`
- `<TOKEN_NAME>`

## Mirror sync quick check

- Auth: `gh auth status`
- Manual run: `/Users/bot/github/openclaw-docs-sync/sync-docs.sh`
- Scheduler: OpenClaw cron job `github-docs-sync` (every 2d)
