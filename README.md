# 🚀 MD2TG - Markdown to Telegram MarkdownV2 Converter

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Turborepo](https://img.shields.io/badge/Built%20with-Turborepo-blueviolet)](https://turbo.build/repo)
[![Cloudflare Workers](https://img.shields.io/badge/Deployed%20on-Cloudflare-orange)](https://workers.cloudflare.com/)

A handy tool to convert standard Markdown to Telegram's MarkdownV2 format - perfect for formatting AI responses and content for Telegram!

## 🎯 Purpose

Ever tried to send AI-generated markdown content to Telegram and ended up with broken formatting? This tool solves that problem by converting standard Markdown syntax into Telegram's strict MarkdownV2 format, which requires special character escaping and specific formatting rules.

**Perfect for:**
- 🤖 Formatting AI assistant responses for Telegram bots
- 📝 Converting documentation to Telegram-friendly format
- 💬 Sharing formatted content in Telegram channels
- 🔄 Automating content delivery via n8n workflows

## ✨ Features

- **Web Interface** - Simple, beautiful UI for quick conversions
- **REST API** - Integrate into your workflows and applications
- **n8n Integration** - Ready-to-use workflow templates
- **Fast & Reliable** - Powered by Cloudflare Workers for global edge deployment
- **Open Source** - Fully transparent and community-driven

## 🏗️ Project Structure

This is a **Turborepo monorepo** containing:

```
md2tg-monorepo/
├── apps/
│   ├── web/          # Next.js web application (Cloudflare Pages)
│   └── api/          # Cloudflare Worker API
├── packages/         # Shared packages (if any)
└── turbo.json        # Turborepo configuration
```

## 🛠️ Tech Stack

- **Framework**: [Next.js 15](https://nextjs.org/) with React 19
- **Monorepo**: [Turborepo](https://turbo.build/repo)
- **Package Manager**: [Bun](https://bun.sh/)
- **Deployment**: [Cloudflare Workers & Pages](https://workers.cloudflare.com/)
- **Styling**: Tailwind CSS + DaisyUI
- **Core Library**: [telegramify-markdown](https://www.npmjs.com/package/telegramify-markdown)

## 🚀 Getting Started

### Prerequisites

- [Bun](https://bun.sh/) v1.3.0 or higher
- Node.js 20+ (for compatibility)
- Cloudflare account (for deployment)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/haotiencheng/md2tg-monorepo.git
   cd md2tg-monorepo
   ```

2. **Install dependencies**
   ```bash
   bun install
   ```

3. **Set up environment variables**
   
   For the web app (`apps/web/.env.local`):
   ```env
   NEXT_PUBLIC_API_URL=https://api.md2tg.projectstain.dev/
   ```

### Development

Run all apps in development mode:

```bash
bun run dev
```

This will start:
- Web app at `http://localhost:3000`
- API worker at `http://localhost:8787`

Run specific app:

```bash
# Web app only
cd apps/web
bun run dev

# API worker only
cd apps/api
bun run dev
```

### Building

Build all apps:

```bash
bun run build
```

Build specific app:

```bash
cd apps/web
bun run build
```

## 📦 Deployment

### Web App (Cloudflare Pages)

The web app uses [OpenNext.js for Cloudflare](https://opennext.js.org/cloudflare):

```bash
cd apps/web

# Preview locally
bun run preview

# Deploy to Cloudflare
bun run deploy
```

### API Worker

```bash
cd apps/api

# Deploy to Cloudflare Workers
wrangler deploy
```

## 🔌 Usage

### Web Interface

Visit [https://md2tg.projectstain.dev](https://md2tg.projectstain.dev) and paste your markdown content.

### API

**Endpoint**: `POST https://api.md2tg.projectstain.dev/`

**Request**:
```bash
curl -X POST https://api.md2tg.projectstain.dev/ \
  -H "Content-Type: application/json" \
  -d '{"markdown":"# Hello World\n\nThis is **bold** and this is *italic*"}'
```

**Response**:
```json
{
  "data": {
    "telegram_text": "# Hello World\n\nThis is **bold** and this is *italic*"
  }
}
```

### n8n Integration

Check out the [n8n workflow examples](https://md2tg.projectstain.dev) on the website for ready-to-use templates.

## 🤝 Contributing

Contributions are welcome! This is a fully open-source project.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is open source and available under the [MIT License](LICENSE).

## 💖 Support

If you find this tool helpful, consider supporting the development:

[![Buy Me A Coffee](https://img.shields.io/badge/Buy%20Me%20A%20Coffee-support-yellow?style=for-the-badge&logo=buy-me-a-coffee)](https://buymeacoffee.com/projectstain)

## 🔗 Links

- **Website**: [https://md2tg.projectstain.dev](https://md2tg.projectstain.dev)
- **API**: [https://api.md2tg.projectstain.dev](https://api.md2tg.projectstain.dev)
- **Author**: [projectstain.dev](https://www.projectstain.dev)

## 📚 Related

- [telegramify-markdown](https://www.npmjs.com/package/telegramify-markdown) - The core library powering this tool
- [Telegram Bot API - MarkdownV2](https://core.telegram.org/bots/api#markdownv2-style) - Official Telegram MarkdownV2 documentation

---

Built with ❤️ using Turborepo and Cloudflare
