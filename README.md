# OpenClaw Skills Collection

[![OpenClaw Skills](https://img.shields.io/badge/OpenClaw-Skills-blue)](https://github.com/openclaw/skills)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

Collection of OpenClaw skills built for the **OpenClaw x Moltbook Hackathon** ($30,000 USDC prize pool).

---

## 🎯 Skills

### 1. OpenClaw Proxy Configuration 🇨🇳

**Repository**: [hanpaopao001/openclaw-proxy](https://github.com/hanpaopao001/openclaw-proxy)

One-click solution for OpenClaw proxy configuration in restricted networks (China, Iran, Russia, etc.).

**Features**:
- Auto-Diagnose proxy issues
- Multi-Channel Support (Telegram, Twitter/X, GitHub, Discord, Slack)
- Smart Configuration
- Built-in Troubleshooting

**Track**: Best OpenClaw Skill

---

### 2. OpenClaw Social Bridge 🌉

**Repository**: This repository

Bridge content across platforms seamlessly.

**Features**:
- 🌉 **Cross-Platform Sync** - Twitter/X ↔ Telegram auto-forwarding
- 📝 **AI Summaries** - Auto-generate summaries for content
- 📅 **Scheduled Posts** - Bulk publish to multiple platforms
- 📊 **Analytics** - Track engagement across platforms

**Commands**:
```bash
# Auto-forward tweets to Telegram
social-bridge watch twitter --user username --telegram @channel --summarize

# Schedule posts
social-bridge schedule --platform twitter --time "2026-02-08 10:00" --content "..."

# Cross-post to multiple platforms
social-bridge crosspost --twitter --telegram --discord --content "..."
```

**Track**: Agentic Commerce OR Best OpenClaw Skill

---

## 🏆 Hackathon Info

- **Event**: OpenClaw x Moltbook Hackathon
- **Prize Pool**: $30,000 USDC
- **Deadline**: February 8, 2026, 12:00 PM PST
- **Submit**: [moltbook.com/post/b021cdea-...](https://moltbook.com/post/b021cdea-4c1a-8115-a736-9c6a1b9c1f8d)

---

## 📦 Installation

### For Proxy Skill

```bash
openclaw skill install openclaw-proxy
```

### For Social Bridge

```bash
openclaw skill install openclaw-social-bridge
```

---

## 🔧 Development

OpenClaw skills follow the standard structure:

```
skill-name/
├── SKILL.md          # Required: skill documentation
├── scripts/          # Optional: executable scripts
├── references/       # Optional: reference documentation
└── assets/           # Optional: assets for output
```

See [OpenClaw Skills Documentation](https://docs.openclaw.ai/skills) for details.

---

## 📧 Contact

- **Twitter**: [@hanpaopao008](https://x.com/hanpaopao008)
- **GitHub**: [hanpaopao001](https://github.com/hanpaopao001)
- **Moltbook**: [moltbook.com/@hanpaopao001](https://moltbook.com/@hanpaopao001)

---

## 📝 License

MIT License - Feel free to use and modify!

---

**Built with ❤️ for the OpenClaw Community**
