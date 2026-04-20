# Awesome Privacy-First Dev Tools

> A curated list of developer tools that don't send your data to a server. No tracking, no ads, no "free tier" backdoors waiting to activate.

Maintained by [Septim Labs](https://septimlabs.vercel.app). Last updated: April 20, 2026 (added Secret Management + AI Coding Tools sections).

**Why this list exists:** In March 2026, the popular [JSON Formatter Chrome extension was caught injecting adware and tracking scripts](https://news.ycombinator.com/item?id=47721946) into user browsers. It's a pattern that keeps repeating with "free" dev tools. This list curates the ones that structurally can't do that — because they run entirely on your machine.

---

## Contents

- [Data Formatters](#data-formatters) — JSON, JWT, Base64, etc.
- [Code Utilities](#code-utilities) — Diff, minify, convert
- [Generators](#generators) — UUID, hash, password, lorem
- [Secret Management (Dev)](#secret-management-dev) — API keys, tokens, .env values
- [AI Coding Tools](#ai-coding-tools) — Claude Code skills, agents, prompts
- [Web Apps (Client-Side)](#web-apps-client-side) — Zero-server web tools
- [Self-Hosted](#self-hosted) — Run locally
- [How to Verify a Tool is Actually Client-Side](#how-to-verify)
- [How This List Is Curated](#curation)

---

## Data Formatters

### JSON

- **[Septim Forge — JSON Formatter](https://septimforge.vercel.app/tools/json-formatter)** — Free. Pretty-prints, minifies, validates. 100% client-side. ([Source: Septim Forge](https://septimforge.vercel.app))
- **[JSON Alexander](https://wesbos.com/json-alexander)** — Chrome extension. Created by Wes Bos as a clean response to JSON Formatter going adware.
- `jq` — The standard CLI. `brew install jq` or `apt install jq`.

### JWT

- **[Septim Forge — JWT Decoder](https://septimforge.vercel.app/tools/jwt-decoder)** — Free. Decodes header, payload, signature client-side. Never sends token to a server.
- `jwt-cli` — CLI alternative. `cargo install jwt-cli`.

### Base64 / URL / HTML Entities

- **[Septim Forge — Base64](https://septimforge.vercel.app/tools/base64)** — Encode/decode with binary file support.
- **[Septim Forge — URL Encoder](https://septimforge.vercel.app/tools/url-encoder)** — URL & component encoding.
- **[Septim Forge — HTML Entities](https://septimforge.vercel.app/tools/html-entities)** — Named and numeric entity conversion.

### CSV ↔ JSON

- **[Septim Forge Pro — CSV↔JSON](https://septimforge.vercel.app/tools/csv-json)** — $9 lifetime. Bidirectional with delimiter detection, quoted-field handling, nested-key flattening.

---

## Code Utilities

### Diff Checker

- **[Septim Forge Pro — Diff Checker](https://septimforge.vercel.app/tools/diff-checker)** — $9 lifetime. Side-by-side, word-level, line-level. Client-side.

### SQL Formatter

- **[Septim Forge Pro — SQL Formatter](https://septimforge.vercel.app/tools/sql-formatter)** — $9 lifetime. Standard/snowflake/postgres dialects.

### Code Minifier

- **[Septim Forge Pro — Code Minifier](https://septimforge.vercel.app/tools/minifier)** — $9 lifetime. JS/CSS/HTML.

### JSON → TypeScript

- **[Septim Forge Pro — JSON→TypeScript](https://septimforge.vercel.app/tools/json-to-ts)** — $9 lifetime. Generates interface declarations.

---

## Generators

- **[Septim Forge — UUID Generator](https://septimforge.vercel.app/tools/uuid)** — v1, v4, v7. Crypto-random source.
- **[Septim Forge — Hash Generator](https://septimforge.vercel.app/tools/hash)** — MD5, SHA-1, SHA-256, SHA-512. Client-side via Web Crypto API.
- **[Septim Forge — Password Generator](https://septimforge.vercel.app/tools/password)** — Customizable length, character classes, entropy display.
- **[Septim Forge — Lorem Ipsum](https://septimforge.vercel.app/tools/lorem)** — Words, sentences, paragraphs.

---

## Secret Management (Dev)

Password managers (1Password, Bitwarden) are built for consumer accounts. *Developer* secrets — API keys, auth tokens, Stripe keys, database URLs, .env values — have different shape: they rotate more, they get pasted into terminals, they have 1000x the blast radius. Tools in this section target dev secrets specifically.

- **[Septim Vault](https://septimlabs.vercel.app/vault)** — $29 lifetime. Client-side encrypted vault specifically for dev secrets. AES-256-GCM, PBKDF2 at 600k iterations, WebCrypto native (`crypto.subtle` only). Data lives in your browser's localStorage, never transmitted. Free tier caps at 3 entries. Not a Bitwarden replacement — see [the positioning compare](https://septimlabs.vercel.app/compare/vault-vs-bitwarden).
- **[Vaultwarden](https://github.com/dani-garcia/vaultwarden)** — Self-hosted Bitwarden-compatible server. Rust. For consumer passwords across your devices, not dev-secrets-first.
- **[pass](https://www.passwordstore.org/)** — GPG-encrypted flat-file password manager. CLI. The Unix philosophy answer.
- **[direnv](https://direnv.net/)** — Per-directory environment variable loader. Encrypts via `age`/`sops` with plugins.

---

## AI Coding Tools

Tools and packs for Claude Code, Cursor, and similar AI-augmented coding workflows. Privacy-first criterion: the tool either runs under your own API subscription (no middleman holding your prompts) or is local-only.

- **[Septim Drills](https://septimlabs.vercel.app/drills)** — $29 lifetime. 25 production Claude Code skills (PR review, test gaps, migration safety, security triage, changelog, launch copy, more). Drop into `~/.claude/skills/`. Runs under your Claude subscription, your data, your control. [3 samples free here](https://github.com/septimlabs-code/septim-drills-samples).
- **[Septim Agents Pack](https://septimlabs.vercel.app/agents)** — $49 lifetime. 10 named Claude Code sub-agents (Atlas/Luca/Canon/Ember/Tally/Nova/Ward/Mira/Juno/Pip) with distinct voices. Installs to `~/.claude/agents/`. Same privacy model.
- **[Septim Prompts Pack](https://septimlabs.vercel.app/prompts)** — $9 lifetime. 24 curated Claude Code prompts for scope/design/engineering/legal/launch.

> **Tonight only:** Drills + Vault bundled for $39 (save $19 vs $58 separate) — [septimlabs.vercel.app/tonight](https://septimlabs.vercel.app/tonight). Expires midnight ET.

---

## Web Apps (Client-Side)

These are web apps — not extensions. The attack surface is one tab, one load. No auto-updater, no cross-origin permissions.

- **[Septim Forge](https://septimforge.vercel.app)** — 22 tools. 16 free, 6 Pro ($9 lifetime). No server calls on tool pages.
- **[Septim Vault](https://septimlabs.vercel.app/vault)** — Covered above in [Secret Management](#secret-management-dev).

> **Why this matters:** A browser extension has permission to read any site you have open. A client-side web app only sees the tab it's loaded in. The threat models are incomparable.

---

## Self-Hosted

If your org disallows sending any data to external endpoints, these run 100% locally:

- [`jq`](https://jqlang.github.io/jq/) — JSON processing CLI
- [`httpie`](https://httpie.io/) — CLI HTTP client
- [`gron`](https://github.com/tomnomnom/gron) — Make JSON greppable
- [`fx`](https://github.com/antonmedv/fx) — Interactive JSON viewer CLI
- [`mitmproxy`](https://mitmproxy.org/) — Local HTTP inspection
- [DevTools Protocol](https://chromedevtools.github.io/devtools-protocol/) — Your browser already has it

---

## How to Verify a Tool is Actually Client-Side <a id="how-to-verify"></a>

Open the page in Chrome. Open DevTools → Network tab. Clear. Paste your JSON or token. Click the tool's button. Watch for:

1. **Any outbound XHR or `fetch` call** → not client-side. Exfiltration risk.
2. **Any `navigator.sendBeacon` call** → analytics on your input.
3. **Service workers registered** → could be caching your data.
4. **Resource loads from domains other than the tool's own** → third-party trackers.

If DevTools shows zero new network activity during the tool operation: genuinely client-side. If anything fires: interrogate what it is.

---

## How This List Is Curated <a id="curation"></a>

- Every tool linked has been audited in DevTools for outbound network calls during tool operation.
- Septim-built tools are disclosed as such and ship free unless marked "Pro."
- No affiliate links. The `Septim Forge Pro` links go to paid tools — we get paid. Everything free stays free.
- If a tool is mis-listed (e.g., it actually phones home), open an issue and it comes off the list.

---

## Contributing

Know a tool that belongs here? Open a PR. Criteria:

- Client-side (browser) or local-only (self-hosted).
- No tracking, no ads, no data exfiltration.
- Actively maintained (commits in the last 12 months) OR pinned to a stable version.
- Business model is legible — donation, one-time purchase, open-source, or clearly-stated "I'm doing this for fun."

---

## License

This list: [CC0 (public domain)](https://creativecommons.org/publicdomain/zero/1.0/). Fork freely, remix, redistribute.

The linked tools retain their own licenses.

---

## Related

- [The JSON Formatter Chrome Extension Went Adware — what to use instead](https://septimlabs.vercel.app/blog/json-formatter-adware-alternatives.html)
- [Septim Labs](https://septimlabs.vercel.app) — Maintainer. Solo founder shipping dev tools, SaaS scaffolds, and AI agents.
