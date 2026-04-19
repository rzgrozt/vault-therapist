# Vault Therapist

> AI-powered vault analyst for Obsidian. Find orphan notes, detect contradictions, surface knowledge gaps, and get a weekly insight report on your second brain.

Vault Therapist reads the notes in your vault and runs four AI-powered analyses designed for knowledge workers, researchers, and long-time note-takers whose vaults have grown faster than their memory of them.

![Obsidian 1.4+](https://img.shields.io/badge/Obsidian-1.4%2B-7c3aed)
![Desktop only](https://img.shields.io/badge/platform-desktop-informational)
![License: BUSL-1.1](https://img.shields.io/badge/license-BUSL--1.1-blue)

---

## Features

- **Orphan finder** — notes with no inbound or outbound links, plus AI-suggested connections to the rest of your vault.
- **Contradiction detector** — finds pairs of notes that make conflicting claims, with a confidence score and a plain-English explanation.
- **Knowledge gap finder** — scans clusters of notes around a topic and highlights what's missing or underdeveloped.
- **Weekly insight report** — themes, patterns, and recommendations across your vault, generated on demand.
- **Four AI providers** — Ollama (100% local), OpenAI, Anthropic, OpenRouter. Your notes never go anywhere you don't authorize.
- **Embedding-powered similarity** — once, then cached. Large vaults process incrementally.

## Data privacy & network use

> **Disclosure** (required by Obsidian's developer policy):
> 
> Vault Therapist makes outbound network requests to:
> 
> 1. **The AI provider you configure** (Ollama/OpenAI/Anthropic/OpenRouter) — to run analyses. Your note content is sent to this provider. If you pick Ollama running on `localhost`, nothing leaves your machine.
> 2. **`api.vaulttherapist.com`** — only to validate your license key and report activation status. No note content is ever sent here.
> 
> A paid license is required for full access. A 3-day trial is included — no account, no credit card.

Read the full privacy policy: https://vaulttherapist.com/privacy

## AI Disclaimer

Vault Therapist uses AI models to generate suggestions and analysis results. All AI output should be treated as suggestions, not authoritative conclusions. Always verify recommendations against your actual notes before making changes to your vault.

## Install

Once accepted to the Obsidian community plugin directory:

1. **Settings → Community plugins → Browse**, search "Vault Therapist", install, enable.

Until then, or for beta access:

1. Download `main.js`, `manifest.json`, and `styles.css` from the [latest release](https://github.com/vaulttherapist/vault-therapist/releases).
2. Drop them into `<vault>/.obsidian/plugins/vault-therapist/`.
3. Enable in Settings → Community plugins.

## AI provider setup

Pick whichever matches your priorities (cost, privacy, model quality). You can switch at any time.

### Ollama (local, free, fully private)

Best for privacy-first users. Slower on consumer hardware; cost is $0.

1. Install Ollama from https://ollama.com/download.
2. Pull a chat model and an embedding model:
   
   ```
   ollama pull gemma3:4b
   ollama pull nomic-embed-text
   ```
3. Make sure Ollama is running (`ollama serve`, or the tray app).
4. In Vault Therapist settings, pick **Ollama**, leave endpoint as `http://localhost:11434`.
5. Hit **Test connection**. Done.

### OpenAI

Best quality/speed balance. Pay-as-you-go.

1. Create an API key at https://platform.openai.com/api-keys.
2. In settings, pick **OpenAI**, paste the key, set model (default `gpt-4o`).
3. Test connection.

### Anthropic (Claude)

Strong reasoning; good for contradiction detection.

1. Create an API key at https://console.anthropic.com/settings/keys.
2. In settings, pick **Anthropic**, paste the key, set model (default `claude-4-5-haiku`).
3. Test connection.

### OpenRouter

Single account, dozens of models (including free tiers).

1. Create an API key at https://openrouter.ai/keys.
2. In settings, pick **OpenRouter**, paste the key, set model (default `google/gemma-4-31b-it:free`).
3. Test connection.

### Google Gemini

 Google's in-house model family. Fast and cost-effective.

1. Get an API key from https://aistudio.google.com/app/apikey.
2. In settings, pick **Google Gemini**, paste the key, set model (default `gemini-2.0-flash`).
3. Test connection.

### LMStudio (local)

 Run LLMs locally on your machine with a polished app. No API key needed — just start the local server.

1. Download LM Studio from https://lmstudio.ai/download.
2. Open LM Studio and load a model (e.g. Llama 3.2, Mistral).
3. Click **Start Server** (the local API icon on the left sidebar).
4. In Vault Therapist settings, pick **LMStudio**, set Base URL to `http://localhost:1234` (default), enter the model name exactly as shown in LM Studio.
5. Test connection.

> **Note**: Embeddings depend on the loaded model — not all models support embeddings. The plugin will probe automatically on first use and disable embeddings if the model doesn't support them.

## Pricing

|              | Trial           | Lifetime license                |
| ------------ | --------------- | ------------------------------- |
| **Price**    | Free, no signup | **$15 one-time**                |
| **Duration** | 3 days          | Forever, all future updates     |
| **Features** | All             | All                             |
| **Vaults**   | Unlimited       | Unlimited                       |
| **Devices**  | This install    | Activations across your devices |

Buy: https://vaulttherapist.lemonsqueezy.com

## FAQ

**Does my note content leave my machine?**
Only if you pick a cloud AI provider. With Ollama, nothing ever leaves your machine. With OpenAI/Anthropic/OpenRouter, the notes being analyzed are sent to that provider under their terms. The Vault Therapist license server only ever sees your license key — never your notes.

**Which provider should I pick?**

- Privacy > everything: **Ollama** or **LMStudio**.
- Best general results for the price: **OpenAI** (`gpt-4o`).
- Best for subtle contradictions: **Anthropic** (`claude-4-5-haiku`).
- Want to try many models on one bill, including free tiers: **OpenRouter**.
- Fast, cheap, Google's model family: **Google Gemini**.
- Want to run everything locally with a GUI: **LMStudio**.

**What happens when the trial expires?**
Analyses are gated, but the plugin keeps loading cleanly. Settings stay accessible so you can enter a license. No features crash, no data is lost, and you can uninstall without side effects.

**What about refunds?**
14-day no-questions-asked refund via Lemon Squeezy. Reply to the purchase email.

**Why does the plugin call `api.vaulttherapist.com`?**
Only to verify your license key after activation and, occasionally, to confirm it's still valid. If the backend is unreachable, Vault Therapist falls back to a 24-hour offline grace window so a flaky connection never locks you out mid-session.

**Is source code available?**
The plugin source is in this repo under the Business Source License 1.1 (BUSL-1.1). You can read, modify, and use it for non-production purposes; production use requires a commercial license. The code automatically converts to Apache 2.0 on the Change Date (2030-04-15), or four years after each version's release — whichever comes first. The license backend is proprietary.

**Can I use it on mobile?**
Not yet — desktop only for now (`isDesktopOnly: true`). Mobile support is on the roadmap once embedding performance on-device is acceptable.

## License

Business Source License 1.1 (BUSL-1.1). Converts to Apache License 2.0 on 2030-04-15 (or four years after each version's release, whichever comes first). Non-production use is free; production use requires a commercial license — see `LICENSE` for terms and contact support@vaulttherapist.com for licensing.

## Support

- Bugs / feature requests: https://github.com/rzgrozt/vault-therapist/issues
- Email: support@vaulttherapist.com
