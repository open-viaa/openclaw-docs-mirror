# Docs Mirror Automation

This file explains exactly how this mirror is kept current.

## Scope

- Sync **official OpenClaw docs** into `official-docs/`
- Keep **custom operational notes** in `additions/`
- Commit and push changes to this repository

## Canonical layout

- `official-docs/` → mirrored from official OpenClaw docs
- `additions/` → VIAA-maintained content (troubleshooting + memory workflow)

## Manual sync (local machine)

```bash
cd ~/.openclaw/workspace/openclaw-docs-mirror

# Mirror official docs from local OpenClaw install
rsync -a --delete /opt/homebrew/lib/node_modules/openclaw/docs/ ./official-docs/

# (Optional) refresh troubleshooting notes from workspace source
rsync -a ~/.openclaw/workspace/troubleshooting/ ./additions/troubleshooting/

# Commit and push
git add official-docs additions README.md AUTOMATION.md
git commit -m "sync official docs + refresh additions"
git push origin main
```

## Scheduler pattern (OpenClaw cron)

Recommended job names:
- `docs-mirror:sync`
- `docs-mirror:status`

Recommended cadence:
- Sync every 1-2 days
- Status/verification daily

Before creating/editing jobs:

```bash
openclaw cron list
```

Then create or update using `openclaw cron add` / `openclaw cron edit`.

## Auth requirements

GitHub auth must be valid on host:

```bash
gh auth status
```

If not logged in:

```bash
gh auth login
```

## Troubleshooting

- Push denied: re-run `gh auth login` and verify scopes.
- No official docs found at source path: verify OpenClaw is installed and path exists.
- Too many noisy diffs: ensure `rsync --delete` is used for deterministic mirror state.

## Public repo hygiene

- Never commit secrets/tokens/private paths
- Keep additions concise and operational
- If custom advice conflicts with official docs, mark it clearly and favor official docs
