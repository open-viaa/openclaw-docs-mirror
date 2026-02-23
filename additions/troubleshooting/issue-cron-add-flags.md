# Issue: `openclaw cron add` flag errors

## Symptoms

- `unknown option '--schedule'`
- `Main jobs require --system-event (systemEvent)`

## Correct command (main session weekly check)

```bash
openclaw cron add --name "healthcheck:security-audit" --cron "0 9 * * 1" --tz "Asia/Bangkok" --session main --system-event "Run weekly security check: openclaw security audit --deep && openclaw update status. Summarize warnings and changes."
```

Verify:
```bash
openclaw cron list
```

## Notes

- Use `--cron`, not `--schedule`.
- For `--session main`, use `--system-event` (not `--message`).
