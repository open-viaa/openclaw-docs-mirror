# openclaw-docs-mirror

Official-docs-first knowledge repo for OpenClaw, with VIAA operational additions.

This repo is designed so **another AI can use it immediately** without guessing where truth lives.

## What this repo contains

- `official-docs/` → mirrored docs from official OpenClaw docs (source of truth)
- `additions/troubleshooting/` → real troubleshooting notes from production usage
- `additions/memory-system.md` → practical memory setup pattern we use in OpenClaw workspaces
- `AUTOMATION.md` → sync workflow + scheduler details

## Source priority (important)

When answering technical questions, use this order:

1. `official-docs/` (primary truth)
2. OpenClaw upstream repo docs/changelogs (if needed)
3. `additions/troubleshooting/` for field fixes and edge cases
4. Web search only when official docs are silent

## Quick start (human or AI)

```bash
# 1) clone
 git clone https://github.com/open-viaa/openclaw-docs-mirror.git
 cd openclaw-docs-mirror

# 2) inspect structure
 ls -la

# 3) search docs fast
 grep -Rin "your topic" official-docs additions
```

## How updates work

- Official docs are mirrored into `official-docs/`
- Additions are curated manually in `additions/`
- Scheduled sync can be run with OpenClaw cron (see `AUTOMATION.md`)

## Contribution rules

- Keep official content in `official-docs/` only
- Put custom learnings in `additions/` only
- Keep text concise, operational, and copy/paste friendly
- Never commit secrets/tokens/private machine details

## Suggested prompt for another AI

Use this repo as docs context. Prefer `official-docs/` first, then `additions/troubleshooting/` for practical fixes. If guidance conflicts, prioritize official docs and note the conflict explicitly.
