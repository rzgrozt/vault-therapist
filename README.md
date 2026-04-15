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
   ollama pull llama3.2
   ollama pull nomic-embed-text
   ```
3. Make sure Ollama is running (`ollama serve`, or the tray app).
4. In Vault Therapist settings, pick **Ollama**, leave endpoint as `http://localhost:11434`.
5. Hit **Test connection**. Done.

### OpenAI

Best quality/speed balance. Pay-as-you-go.

1. Create an API key at https://platform.openai.com/api-keys.
2. In settings, pick **OpenAI**, paste the key, set model (default `gpt-4o-mini`).
3. Test connection.

### Anthropic (Claude)

Strong reasoning; good for contradiction detection.

1. Create an API key at https://console.anthropic.com/settings/keys.
2. In settings, pick **Anthropic**, paste the key, set model (default `claude-3-5-haiku-20241022`).
3. Test connection.

### OpenRouter

Single account, dozens of models (including free tiers).

1. Create an API key at https://openrouter.ai/keys.
2. In settings, pick **OpenRouter**, paste the key, set model (default `meta-llama/llama-3.2-3b-instruct:free`).
3. Test connection.

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

- Privacy > everything: **Ollama**.
- Best general results for the price: **OpenAI** (`gpt-4o-mini`).
- Best for subtle contradictions: **Anthropic** (`claude-3-5-haiku`).
- Want to try many models on one bill, including free tiers: **OpenRouter**.

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

## Development

```
npm install
npm run dev       # watch build
npm run build     # production build
scripts/setup-test-vault.sh ~/my-test-vault
scripts/dev-install.sh     ~/my-test-vault
```

QA against `docs/QA_CHECKLIST.md` before cutting a release.

## License

Business Source License 1.1 (BUSL-1.1). Converts to Apache License 2.0 on 2030-04-15 (or four years after each version's release, whichever comes first). Non-production use is free; production use requires a commercial license — see `LICENSE` for terms and contact support@vaulttherapist.com for licensing.

## Support

- Bugs / feature requests: https://github.com/rzgrozt/vault-therapist/issues
- Email: support@vaulttherapist.com
