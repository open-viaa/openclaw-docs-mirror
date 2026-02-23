# Issue: Gateway says `pairing required`

## Symptoms

- `gateway connect failed: Error: pairing required`
- `gateway closed (1008): pairing required`
- `openclaw devices ...` fails with pairing error

## Safe fix order (same terminal)

### 1) Check current state
```bash
openclaw gateway status
```
If `RPC probe: ok`, stop.

### 2) Start service
```bash
openclaw gateway start
openclaw gateway status
```

### 3) Approve latest pending device pairing
```bash
openclaw devices approve --latest
openclaw gateway status
```
Target result: `Runtime: running` + `RPC probe: ok`.

## Fallback (last resort)

Use only if steps above still fail.

```bash
openclaw gateway stop
mv ~/.openclaw/identity ~/.openclaw/identity.bak.$(date +%Y%m%d-%H%M%S)
openclaw gateway install
openclaw gateway start
openclaw gateway status
```

## Notes

- Avoid running `openclaw doctor` during active pairing recovery unless needed.
- Success condition is always `RPC probe: ok`.
