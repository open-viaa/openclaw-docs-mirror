# Issue: Gateway service not loaded / not installed

## Symptoms

- `Service: LaunchAgent (not loaded)`
- `Service unit not found`
- `Could not find service "ai.openclaw.gateway"`

## Fix (same terminal)

```bash
openclaw gateway install
openclaw gateway start
openclaw gateway status
```

## Expected

- `Service: LaunchAgent (loaded)`
- `Runtime: running`
- `RPC probe: ok`

## If runtime looks "stopped" but probe is ok

Wait a few seconds and run:
```bash
openclaw gateway status
```
Transient status can happen right after restart.
