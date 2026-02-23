# Issue: Rotate Telegram bot token safely

## Goal
Rotate token without losing local session context.

## Important

- Rotating token does **not** wipe local OpenClaw memory/history.
- It only invalidates old bot token and reconnects Telegram.

## Steps

1) In Telegram @BotFather:
- `/revoke` (pick bot)
- `/token` (get new token)

2) Same terminal:
```bash
openclaw config set channels.telegram.botToken "PASTE_NEW_TOKEN_HERE"
openclaw gateway restart
openclaw status
```

3) Verify in status:
- Telegram `State: OK`
