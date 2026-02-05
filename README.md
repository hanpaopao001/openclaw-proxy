# OpenClaw Proxy Configuration Skill

[![OpenClaw Skill](https://img.shields.io/badge/OpenClaw-Skill-blue)](https://github.com/openclaw/skills)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

One-click solution for OpenClaw proxy configuration in restricted networks (China, Iran, Russia, etc.).

## 🎯 Features

- **Auto-Diagnose** - One command to detect all proxy issues
- **Multi-Channel Support** - Telegram, Twitter/X, GitHub, Discord, Slack, and more
- **Smart Configuration** - Auto-detect and apply best proxy settings
- **Troubleshooting** - Built-in diagnostics and fixes

## 📦 Installation

1. Download the skill file (coming soon)
2. Place in your OpenClaw skills directory
3. Restart OpenClaw

Or install via CLI:

```bash
openclaw skill install openclaw-proxy
```

## 🚀 Quick Start

### Auto-Configure (Recommended)

```bash
# Detect and fix all proxy issues
proxy-setup --auto

# Verify configuration
proxy-validate --full
```

### Channel-Specific

```bash
# Fix Telegram only
telegram-proxy-fix --token YOUR_BOT_TOKEN --proxy http://127.0.0.1:7897

# Configure GitHub
github-proxy-setup --token YOUR_GH_TOKEN

# Configure Twitter/X
twitter-proxy-setup --bearer YOUR_BEARER_TOKEN
```

## 📋 Supported Channels

| Channel | Status | Proxy Type |
|---------|--------|------------|
| Telegram | ✅ Tested | HTTP only |
| Twitter/X | ✅ Tested | HTTP |
| GitHub | ✅ Tested | HTTP |
| Discord | ⚠️ Beta | HTTP |
| Slack | ⚠️ Beta | HTTP |

## 🔧 Configuration

### Required OpenClaw Config

```json5
{
  "channels": {
    "telegram": {
      "enabled": true,
      "botToken": "YOUR_BOT_TOKEN",
      "proxy": "http://127.0.0.1:7897",
      "network": {
        "autoSelectFamily": false
      }
    }
  }
}
```

### Common Proxy Addresses

| Tool | HTTP | SOCKS5 |
|------|------|--------|
| Clash | `http://127.0.0.1:7897` | `socks5://127.0.0.1:7890` |
| V2Ray | `http://127.0.0.1:10809` | `socks5://127.0.0.1:10808` |
| Surge | `http://127.0.0.1:6152` | `socks5://127.0.0.1:6153` |

## 🏆 Hackathon

This skill was built for the **OpenClaw x Moltbook Hackathon** ($30,000 USDC prize pool).

**Track:** Best OpenClaw Skill

## 📝 License

MIT License - feel free to use and modify!

## 🤝 Contributing

Pull requests welcome! Especially for:
- New channel support
- More proxy tools
- Better documentation

## 📧 Contact

Created by [@hanpaopao008](https://x.com/hanpaopao008)

---

**Note:** This skill solves real connectivity issues for OpenClaw users in restricted networks. Built with ❤️ and experience debugging Telegram proxy problems.
