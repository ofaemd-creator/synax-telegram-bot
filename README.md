<p align="center">
  <img src="assets/hero.jpg" alt="SYNAX Telegram Bot — Live @synax_compiler_bot Remote Multi-Agent Bridge" width="100%">
</p>

# 🤖 SYNAX Telegram Bot (`synax-telegram-bot`)

[![CI](https://img.shields.io/github/actions/workflow/status/ofaemd-creator/synax-telegram-bot/ci.yml?branch=main&style=for-the-badge&label=Cross-Platform_CI)](https://github.com/ofaemd-creator/synax-telegram-bot/actions)
[![Core Repo](https://img.shields.io/badge/SYNAX_Core-ofaemd--creator/synax-10b981?style=for-the-badge)](https://github.com/ofaemd-creator/synax)
[![License](https://img.shields.io/badge/License-Apache_2.0-blue?style=for-the-badge)](LICENSE)

**Zero-Dependency Telegram Bot & Remote Agent Skill** bridging **SYNAX (`.sx`)**, **Claude Code**, **OpenAI Codex**, **Google Antigravity**, and **Cursor** directly to Telegram.

---

## ✨ Features

| Command | Capability | Engine |
| :--- | :--- | :--- |
| `/status` | Inspect host CPU/SIMD (`ARM64 NEON` / `x86_64 AVX2`), active LLM backend, and workspace status | `synax.hardware` + `synax.agent` |
| `/egraph <expr>` | Run **E-Graph Equality Saturation** (`fma`, `pow2`, `pow3`, `relu` fusion) and report cycle cost reduction | `synax.egraph` |
| `/prove <expr>` | Run **Static IEEE-754 Interval Abstract Interpretation (`[lo, hi]`)** and return a SHA-256 `FormalProofCertificate` | `synax.formal_prover` |
| `/check <sx>` | Parse, type-check, and verify `.sx` kernel across **19 adversarial IEEE-754 test suites** (`0-ULP`) | `synaxc` + `synax_verifier` |
| `/run <sx>` | Execute `.sx` kernel on test vectors and report automatic `IMMUNE` (`NaN`/`Inf` -> `0.0`) recovery | `synax.sdk` |
| `/code <task>` | Dispatch the autonomous multi-turn coding agent (`list_files`, `read_file`, `edit_file`, `bash`, `sx_check`) | `synax.agent` |

---

## 🚀 Quick Start

### 1. Local CLI Test (No Token Needed)
```bash
python3 synax_telegram_bot.py --status
python3 synax_telegram_bot.py --cmd "/egraph (a * b + 1.0) + (a - a)"
python3 synax_telegram_bot.py --cmd "/prove relu(a - b)"
python3 synax_telegram_bot.py --cmd "/check relu(a - b) * 0.5"
```

### 2. Live Telegram Long-Polling Daemon
```bash
export TELEGRAM_BOT_TOKEN="<your-botfather-token>"
export TELEGRAM_ALLOWED_CHAT_IDS="<your-telegram-chat-id>"
python3 synax_telegram_bot.py --poll
```

### 3. Use as a Skill in Claude Code, OpenAI Codex & Google Antigravity
This repository includes native plugin and skill manifests:
- **Claude Code:** [`.claude-plugin/plugin.json`](.claude-plugin/plugin.json) & [`skills/synax-telegram-bot/SKILL.md`](skills/synax-telegram-bot/SKILL.md)
- **OpenAI Codex:** [`AGENTS.md`](AGENTS.md)
- **Main SYNAX Repository:** https://github.com/ofaemd-creator/synax
