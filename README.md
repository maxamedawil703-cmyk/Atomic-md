# ⚛️ Atomic-md

[![Repository](https://img.shields.io/badge/GitHub-Atomic--md-blue)](https://github.com/maxamedawil703-cmyk/Atomic-md)

**Atomic-md** is a professional, self-hosted WhatsApp Multi-Device bot built with [Baileys](https://github.com/WhiskeySockets/Baileys). All commands run locally with a clean, modular architecture — no remote code execution.

**Official repository:** [github.com/maxamedawil703-cmyk/Atomic-md](https://github.com/maxamedawil703-cmyk/Atomic-md)

## Features

- ⚛️ Professional modular plugin system
- 📱 QR code pairing (no session service required)
- 👥 Group management (kick, promote, demote, tagall)
- 🎨 Sticker creation from images/videos
- 🔒 Owner commands (ban, mode toggle)
- 🚫 Anti-link protection for groups
- ☁️ Deploy-ready for Heroku, Render, Railway, VPS

## Quick Start

### 1. Prerequisites

- Node.js 18 or higher
- A phone number for WhatsApp pairing

### 2. Install

```bash
git clone https://github.com/maxamedawil703-cmyk/Atomic-md.git
cd Atomic-md
npm install
```

### 3. Configure

Copy the example environment file and edit it:

```bash
cp set.env.example set.env
```

Edit `set.env`:

```env
OWNER_NUMBER=252637824865
PREFIX=.
BOT_NAME=Atomic-md
OWNER_NAME=𝗦ԩĕ𝗶𝗸𝗵 ᤂ𝗗𝗿𝗶𝗲𝗻𖣔ꠋꠋꠋꠋꠋꠋꠋꠋꠋꠋꠋꠋꠋꠋꠋꠋꠋꠋꠋꠋꠋꠋꠋꠋꠋꠋꠋꠋꠋꠋꠋ
PUBLIC_MODE=yes
```

### 4. Run

```bash
npm start
```

Scan the QR code printed in your terminal with WhatsApp → **Linked Devices**.

## Commands

| Command | Description |
|---------|-------------|
| `.menu` | Show command list |
| `.alive` | Bot status |
| `.ping` | Check latency |
| `.sticker` | Image → sticker (reply) |
| `.take pack author` | Custom sticker (reply) |
| `.kick @user` | Remove group member |
| `.promote @user` | Promote to admin |
| `.demote @user` | Demote admin |
| `.tagall` | Mention all members |
| `.groupinfo` | Group details |
| `.mode public/private` | Toggle access (owner) |
| `.ban @user` | Ban user (owner) |
| `.unban @user` | Unban user (owner) |

## Project Structure

```
Atomic-md/
├── index.js          # Entry point
├── config.js         # Environment config
├── commands/         # Plugin commands
│   ├── general/
│   ├── group/
│   ├── media/
│   └── owner/
├── lib/              # Core libraries
├── events/           # Event handlers
├── auth/             # Session storage (auto-generated)
└── data/             # JSON database
```

## Adding Commands

Create a file in `commands/<category>/yourcommand.js`:

```js
module.exports = {
  name: 'hello',
  description: 'Say hello',
  ownerOnly: false,   // optional
  groupOnly: false,   // optional
  run: async ({ sock, msg, args, config }) => {
    await sock.sendMessage(msg.key.remoteJid, {
      text: `Hello from ${config.botName}!`,
    }, { quoted: msg });
  },
};
```

## Deploy

### Heroku

1. Fork this repo
2. Create a Heroku app
3. Set environment variables from `set.env.example`
4. Deploy — the `Procfile` starts the bot automatically

### VPS / Local

```bash
npm install
npm start
```

Use `pm2` for production:

```bash
npm install -g pm2
pm2 start index.js --name Atomic-md
```

## Why Atomic-md?

| Feature | Description |
|---------|-------------|
| Local commands | All plugins run on your server — no remote `eval()` |
| Lean stack | Focused dependencies, fast installs |
| Atomic-md brand | Fully yours to customize and deploy |
| Plugin system | Transparent, easy-to-extend command loader |

## License

MIT License — use freely and build on it.

## Disclaimer

This bot uses the unofficial WhatsApp Web API. Use responsibly and follow WhatsApp's Terms of Service. The developers are not responsible for any account restrictions.
