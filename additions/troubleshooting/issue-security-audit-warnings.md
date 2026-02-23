# Issue: Security audit warnings

## Current baseline (local Mac mini)

Expected acceptable warning for local-only setup:
- `gateway.trusted_proxies_missing` (informational unless using reverse proxy)

## Important fixes

### 1) Credentials permissions (high priority)
```bash
chmod 700 ~/.openclaw/credentials
ls -ld ~/.openclaw/credentials
```
Expected: `drwx------`

### 2) Ineffective denyCommands entries
If audit warns that `gateway.nodes.denyCommands` entries are ineffective, remove invalid entries from config, then restart:
```bash
openclaw gateway restart
openclaw security audit --deep
```

## Optional hardening

### Disable elevated tools
```bash
openclaw config set tools.elevated.enabled false --json
openclaw gateway restart
openclaw security audit --deep
```

Expected info line: `tools.elevated: disabled`

### Keep local-only bind
```bash
openclaw config set gateway.bind loopback
openclaw gateway restart
openclaw gateway status
```
Expected: `Gateway: bind=loopback (127.0.0.1)`
