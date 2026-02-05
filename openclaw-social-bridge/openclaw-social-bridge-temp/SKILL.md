---
name: openclaw-social-bridge
description: Bridge content across platforms. Auto-sync tweets to Telegram, generate summaries, schedule posts, and manage cross-platform engagement. Perfect for content creators and community managers.
homepage: https://github.com/hanpaopao001/openclaw-proxy
metadata:
  openclaw:
    emoji: "🌉"
    requires:
      bins: ["curl", "jq"]
---

# OpenClaw Social Bridge

Bridge your content across platforms seamlessly.

## 🎯 What This Skill Does

```
┌─────────────────────────────────────────────────────────┐
│                    Social Bridge                        │
├─────────────────────────────────────────────────────────┤
│  Twitter/X ──► Telegram (auto-forward with summary)     │
│  Telegram ──► Twitter/X (scheduled posts)               │
│  Content ────► AI Summary + Keywords                   │
│  Posts ──────► Schedule & Bulk Publish                  │
└─────────────────────────────────────────────────────────┘
```

## 🚀 Quick Start

### 1. Auto-Forward Tweets to Telegram

```bash
# Forward specific user's tweets to Telegram
social-bridge watch twitter --user username --telegram @your_channel

# Forward with AI summary
social-bridge watch twitter --user username --telegram @your_channel --summarize

# Filter by keywords
social-bridge watch twitter --user username --telegram @your_channel --filter "AI,crypto"
```

### 2. Schedule Posts

```bash
# Schedule a tweet
social-bridge schedule --platform twitter --time "2026-02-08 10:00" --content "Hello World!"

# Schedule to multiple platforms
social-bridge schedule --platform twitter,telegram --time "2026-02-08 10:00" --content "Multi-platform post!"
```

### 3. Generate Summary

```bash
# Summarize a URL
social-bridge summarize https://example.com/article

# Summarize text
social-bridge summarize --text "Long article content..."
```

### 4. Cross-Post

```bash
# Post same content to Twitter and Telegram
social-bridge crosspost --twitter --telegram --content "Check this out!"
```

## 📋 Commands Reference

### `social-bridge watch`

Monitor and auto-forward content.

```bash
# Watch Twitter user
social-bridge watch twitter --user <username> --telegram <channel>

# Watch Telegram channel
social-bridge watch telegram --channel <channel> --twitter <username>

# Options
--summarize     # Add AI summary before forwarding
--filter        # Filter by keywords (comma-separated)
--delay         # Delay between posts (default: 60s)
--template      # Custom message template
```

### `social-bridge schedule`

Schedule future posts.

```bash
# Basic schedule
social-bridge schedule --platform twitter --time "2026-02-08 10:00" --content "..."

# Recurring posts
social-bridge schedule --platform twitter --time "0 9 * * 1-5" --content "Daily morning post!"

# View scheduled posts
social-bridge schedule --list
```

### `social-bridge summarize`

Generate AI summaries.

```bash
# From URL
social-bridge summarize https://news.ycombinator.com/item/123

# From text
social-bridge summarize --text "..."

# Options
--length short|medium|long
--format bullet|text|json
```

### `social-bridge crosspost`

Post to multiple platforms simultaneously.

```bash
# Multi-platform post
social-bridge crosspost --twitter --telegram --discord --content "..."

# With media
social-bridge crosspost --twitter --image /path/to/image.jpg --content "Image post!"
```

### `social-bridge analytics`

Track engagement.

```bash
# Get tweet analytics
social-bridge analytics twitter --tweet-id 12345

# Daily report
social-bridge analytics daily --platform twitter,telegram
```

## ⚙️ Configuration

Create `~/.openclaw/social-bridge.json`:

```json5
{
  "twitter": {
    "bearerToken": "YOUR_BEARER_TOKEN",
    "defaultReplySettings": "mentions"
  },
  "telegram": {
    "botToken": "YOUR_BOT_TOKEN",
    "defaultChatId": "@your_channel"
  },
  "default": {
    "summarize": true,
    "delay": 60,
    "template": "📢 {source}: {content}"
  }
}
```

### Twitter Setup

1. Create Twitter Developer Account
2. Create Project & App
3. Generate Bearer Token
4. Set permissions: Read, Write, Direct Message

### Telegram Setup

1. Create Bot via @BotFather
2. Get Bot Token
3. Get Channel ID (use @usernameinfobot)

## 🎨 Message Templates

Customize forwarded messages:

```bash
# Default template
social-bridge watch twitter --user username --template "{{emoji}} {{content}}"

# Variables available:
# {{content}}    Original content
# {{source}}     Source platform
# {{author}}     Author username
# {{url}}        Original URL
# {{summary}}    AI-generated summary
# {{date}}       Post date
```

## 📊 Use Cases

### Content Creator
```
✓ Automatically share YouTube videos to Twitter/Telegram
✓ Generate video summaries
✓ Schedule promotional posts
```

### Community Manager
```
✓ Track mentions across platforms
✓ Auto-reply to common questions
✓ Daily engagement reports
```

### News Aggregator
```
✓ Monitor news sources
✓ Filter by keywords (AI, crypto, etc.)
✓ Curated daily newsletter
```

### Trader/Analyst
```
✓ Track crypto/finance tweets
✓ Sentiment analysis on posts
✓ Real-time price alerts
```

## 🏆 Built for Hackathon

**OpenClaw x Moltbook Hackathon 2026**
- **Track**: Best OpenClaw Skill
- **Prize**: $30,000 USDC
- **Demo**: Show real-time Twitter → Telegram forwarding

## 🔗 Links

- GitHub: https://github.com/hanpaopao001/openclaw-proxy
- Moltbook: https://moltbook.com/@hanpaopao001

## 📝 License

MIT - Free to use and modify!

---

**Made with ❤️ for the OpenClaw Community**
