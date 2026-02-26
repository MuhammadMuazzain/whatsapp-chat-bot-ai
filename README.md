# WhatsApp AI Bot 🤖

A modular, production-ready WhatsApp chatbot that connects to multiple AI providers for text generation, image generation, and intelligent conversation — all through a single WhatsApp interface.

> **Author**: Muhammad Muazzain — [muhammadmuazzain07@gmail.com](mailto:muhammadmuazzain07@gmail.com)

---

## What It Does

Send a message on WhatsApp and get back AI-powered responses — text, images, or custom workflows — using whichever AI provider you configure. Supports multiple models simultaneously, switchable by command.

Built on the [Baileys](https://github.com/WhiskeySockets/Baileys) library for WhatsApp Web automation, with a clean TypeScript architecture designed to be extended with new providers, commands, and integrations.

---

## Supported Models

| Model | Provider | Type | Command |
|-------|----------|------|---------|
| ChatGPT | OpenAI | Text → Text | `!chatgpt` |
| Gemini | Google | Text → Text | `!gemini` |
| Gemini Vision | Google | Image → Text | *(automatic)* |
| DALL·E 2 & 3 | OpenAI | Text → Image | `!dalle` |
| Flux | Hugging Face | Text → Image | `!flux` |
| Stability AI | Stability AI | Text → Image | `!stability` |
| Ollama | Open Source | Text → Text | `!ollama` |
| Custom | Any OpenAI-compatible | Text → Text | `!wa` |

---

## Quick Start

### 1. Clone the repo

```bash
git clone https://github.com/MuhammadMuazzain/whatsapp-ai-bot.git
cd whatsapp-ai-bot
```

### 2. Get your API keys

- [Gemini API Key](https://makersuite.google.com/app/apikey)
- [OpenAI API Key](https://platform.openai.com/api-keys)
- [Hugging Face API Key](https://huggingface.co/settings/tokens)
- [Stability AI API Key](https://platform.stability.ai/)

### 3. Configure environment

```bash
cp .env.example .env
# Edit .env and add your API keys
```

### 4. Run

```bash
npm run start
```

Scan the QR code with WhatsApp and you're live.

---

## Configuration

All config lives in `src/whatsapp-ai.config.ts`. Default commands:

| Command | Provider |
|---------|----------|
| `!gemini` | Google Gemini |
| `!chatgpt` | OpenAI ChatGPT |
| `!dalle` | OpenAI DALL·E |
| `!flux` | Hugging Face Flux |
| `!stability` | Stability AI |
| `!ollama` | Local Ollama |

---

## Architecture

```
src/
├── whatsapp-ai.config.ts   # Central configuration
├── providers/              # One file per AI provider
├── handlers/               # Message routing and command parsing
├── utils/                  # Shared utilities
└── index.ts                # Entry point
```

Each provider is isolated — adding a new one means creating a single file and registering a command. The system is designed to plug in any OpenAI-compatible API or external data source as a custom provider without touching core logic.

---

## Extending with New Providers

1. Create a new provider file in `src/providers/`
2. Implement the standard provider interface
3. Register the command in `whatsapp-ai.config.ts`

This makes it straightforward to add product search APIs, e-commerce integrations, webhooks, or any external data source as a WhatsApp command — without modifying existing functionality.

---

## Deployment

**Local:** follow Quick Start above.

**Cloud (GitHub Codespaces):** open in Codespace, run `npm run start`, scan QR.

**VPS (persistent uptime):**

```bash
npm install -g pm2
pm2 start npm --name "whatsapp-bot" -- run start
pm2 save
```

---

## Disclaimer

This bot uses [Baileys](https://github.com/WhiskeySockets/Baileys) to interface with WhatsApp Web. WhatsApp does not officially support third-party bots — use a dedicated number, not your personal account. API costs are charged per request by the respective providers (OpenAI, Stability AI, etc.).

For production use cases requiring higher reliability and official support, the architecture can be migrated to the [WhatsApp Business API](https://developers.facebook.com/docs/whatsapp/cloud-api/).

---

## Contact

**Muhammad Muazzain**
[muhammadmuazzain07@gmail.com](mailto:muhammadmuazzain07@gmail.com)

---

## License

MIT
