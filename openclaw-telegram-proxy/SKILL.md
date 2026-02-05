---
name: openclaw-telegram-proxy
description: Configure OpenClaw proxy for China users. Auto-detects and fixes proxy issues across all channels (Telegram, Twitter/X, GitHub, etc.), manages proxy rotation, and provides one-click troubleshooting for connectivity problems.
homepage: https://docs.openclaw.ai
metadata:
  openclaw:
    emoji: "🇨🇳"
    requires:
      bins: ["curl", "proxychains4"]
---

# OpenClaw Proxy Configuration Assistant

One-stop solution for OpenClaw proxy configuration in restricted networks (China, Iran, Russia, etc.).

## What This Skill Solves

OpenClaw channels often fail in restricted regions:
- Telegram: Polling doesn't use proxy by default
- Twitter/X: API rate limits and blocks
- GitHub: Connection timeouts
- Web fetch: DNS resolution failures

## Auto-Diagnose

```bash
# Run comprehensive proxy test
proxy-test

# Test specific channel
proxy-test --channel telegram
proxy-test --channel twitter
proxy-test --channel github
```

## Quick Fix Commands

### Check Proxy Status

```bash
# Test proxy connectivity
curl -x http://127.0.0.1:7897 https://api.telegram.org

# Check current IP
curl -x http://127.0.0.1:7897 ifconfig.me

# Test GitHub
curl -x http://127.0.0.1:7897 https://api.github.com
```

### Auto-Configure OpenClaw

```bash
# Detect and apply best proxy settings
proxy-setup --auto

# Configure for Telegram only
proxy-setup --channel telegram

# Configure for all channels
proxy-setup --all

# Test after configuration
proxy-verify
```

### Channel-Specific Commands

**Telegram**:
```bash
# Fix Telegram polling proxy
telegram-proxy-fix --token YOUR_BOT_TOKEN --proxy http://127.0.0.1:7897

# Verify bot is working
telegram-verify --token YOUR_BOT_TOKEN
```

**GitHub**:
```bash
# Configure GitHub proxy
github-proxy-setup --token YOUR_GH_TOKEN

# Test git operations
git-test --repo openclaw/openclaw
```

**Twitter/X**:
```bash
# Configure Twitter proxy
twitter-proxy-setup --bearer YOUR_BEARER_TOKEN

# Test API access
twitter-verify
```

## Required OpenClaw Config

```json5
{
  "channels": {
    "telegram": {
      "enabled": true,
      "botToken": "YOUR_BOT_TOKEN",
      "proxy": "http://127.0.0.1:7897",
      "network": {
        "autoSelectFamily": false  // Critical for China
      }
    },
    "twitter": {
      "enabled": true,
      "bearerToken": "YOUR_BEARER_TOKEN",
      "proxy": "http://127.0.0.1:7897"
    },
    "github": {
      "enabled": true,
      "token": "YOUR_GH_TOKEN",
      "proxy": "http://127.0.0.1:7897"
    }
  },
  "proxy": {
    "default": "http://127.0.0.1:7897",
    "fallback": ["socks5://127.0.0.1:7890"],
    "timeout": 30000,
    "retry": 3
  }
}
```

## Common Proxy Addresses

| Tool | HTTP | SOCKS5 |
|------|------|--------|
| Clash | `http://127.0.0.1:7897` | `socks5://127.0.0.1:7890` |
| V2Ray | `http://127.0.0.1:10809` | `socks5://127.0.0.1:10808` |
| Surge | `http://127.0.0.1:6152` | `socks5://127.0.0.1:6153` |
| Quantumult | `http://127.0.0.1:8199` | `socks5://127.0.0.1:8200` |

## Troubleshooting Flow

```
proxy-test
  ↓
[FAIL] → Check proxy is running
           ↓
[FAIL] → Verify proxy type (HTTP vs SOCKS5)
           ↓
[FAIL] → Test direct connectivity
           ↓
[FAIL] → Check firewall/rules
           ↓
[SOLVED] or Manual intervention required
```

## Code Fix: Telegram Polling Proxy

The problem is in `src/telegram/monitor.ts`:

```typescript
export function createTelegramRunnerOptions(
  cfg: OpenClawConfig,
  proxyFetch?: typeof fetch,  // ← Add this parameter
): RunOptions<unknown> {
  return {
    runner: {
      fetch: {
        timeout: 30,
        allowed_updates: resolveTelegramAllowedUpdates(),
        ...(proxyFetch ? { fetch: proxyFetch } : {}),  // ← Pass proxy
      },
    },
  };
}
```

## Testing & Validation

```bash
# Full validation suite
proxy-validate --full

# Quick smoke test
proxy-validate --quick

# Generate report
proxy-report --output proxy-status.json
```

## Restart OpenClaw

```bash
openclaw gateway stop
cd /home/hpp/openclaw && pnpm build
openclaw gateway run

# Monitor logs
tail -f /tmp/openclaw/openclaw-*.log | grep -i "proxy\|telegram\|error"
```

## Supported Channels

| Channel | Status | Proxy Type |
|---------|--------|------------|
| Telegram | ✅ Tested | HTTP only |
| Twitter/X | ✅ Tested | HTTP |
| GitHub | ✅ Tested | HTTP |
| Discord | ⚠️ Beta | HTTP |
| Slack | ⚠️ Beta | HTTP |
| Web Fetch | ✅ Tested | HTTP |

## Notes

- Telegram Polling requires HTTP proxy (not SOCKS5)
- Webhook mode doesn't need proxy fix
- Always set `autoSelectFamily: false` for China
- Test with `curl -x` before configuring OpenClaw
