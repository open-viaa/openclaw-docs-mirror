# OpenClaw Memory System (Operational Pattern)

This is a practical memory layout for persistent assistant continuity across sessions.

## Goals

- Preserve important context across restarts
- Keep daily logs lightweight
- Distill durable decisions into one long-term file
- Avoid leaking sensitive details in shared/public contexts

## Recommended file layout

- `memory/YYYY-MM-DD.md` → daily running notes (raw timeline)
- `MEMORY.md` → curated long-term memory (preferences, decisions, stable rules)
- `AGENTS.md` → behavior/process rules for the assistant
- `SOUL.md` → tone/persona guidance
- `USER.md` → user profile and working preferences
- `HEARTBEAT.md` → periodic maintenance checklist

## What goes where

### Daily file: `memory/YYYY-MM-DD.md`
Use for:
- actions completed
- command outcomes
- short-term tasks and status
- day-specific events

Keep it append-only and concise.

### Long-term file: `MEMORY.md`
Use for:
- durable preferences
- recurring workflow rules
- strategic decisions
- lessons learned that should persist

Avoid putting one-off noise here.

## Weekly maintenance pattern

1. Review last few daily files
2. Promote only durable items into `MEMORY.md`
3. Remove stale or superseded long-term notes
4. Keep entries short and searchable

## Safety rules

- Do not store secrets/tokens/passwords
- Redact personal hostnames/IPs in public repos
- In group/public contexts, avoid loading private long-term memory unless explicitly intended

## Why this works

- Daily files capture reality
- Long-term memory captures policy
- Separation prevents memory bloat and keeps retrieval fast
