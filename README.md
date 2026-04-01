<h1 align="center">KlowCode</h1>

<p align="center">
  <b>The AI coding agent that works for you — not Anthropic.</b><br/>
  No telemetry. No guardrails. No phone-home. All 54 experimental features unlocked.<br/>
  One command. Full power.
</p>

<p align="center">
  <a href="#-quick-install"><img src="https://img.shields.io/badge/install-one--liner-blue?style=flat-square" alt="Install" /></a>
  <a href="https://github.com/Ahilan-1/klowcode/stargazers"><img src="https://img.shields.io/github/stars/Ahilan-1/klowcode?style=flat-square&color=yellow" alt="Stars" /></a>
  <a href="https://github.com/Ahilan-1/klowcode/issues"><img src="https://img.shields.io/github/issues/Ahilan-1/klowcode?style=flat-square" alt="Issues" /></a>
  <a href="FEATURES.md"><img src="https://img.shields.io/badge/features-54%20unlocked-orange?style=flat-square" alt="Feature Flags" /></a>
  <a href="#-ipfs-mirror"><img src="https://img.shields.io/badge/IPFS-mirrored-teal?style=flat-square" alt="IPFS" /></a>
  <img src="https://img.shields.io/badge/platform-macOS%20%7C%20Linux%20%7C%20WSL-lightgrey?style=flat-square" alt="Platform" />
</p>

---

> **KlowCode** is a fully unlocked, privacy-first build of the Claude Code CLI.
> It speaks to Claude (and 4 other model providers) directly — with zero surveillance, zero artificial restrictions, and every experimental feature Anthropic ships but doesn't let you use.

---

## What makes KlowCode different

| | Official Claude Code | **KlowCode** |
|---|:---:|:---:|
| Telemetry / analytics | ✅ always on | ❌ stripped |
| Session fingerprinting | ✅ | ❌ |
| Prompt-level guardrails | ✅ injected | ❌ removed |
| Experimental features | 0 of 54 | **54 of 54** |
| Voice input | locked | ✅ |
| UltraThink / UltraPlan | locked | ✅ |
| Multi-agent orchestration | locked | ✅ |
| IDE bridge (VS Code / JetBrains) | locked | ✅ |
| Works without Claude subscription | ❌ | ✅ (5 providers) |

---

## ⚡ Quick Install

### Recommended — All Platforms (macOS / Linux / Windows)

> Requires [Bun](https://bun.sh) >= 1.3.11. Install it first if you don't have it:
> - **macOS / Linux**: `curl -fsSL https://bun.sh/install | bash`
> - **Windows**: `powershell -c "irm bun.sh/install.ps1 | iex"`

```bash
git clone https://github.com/Ahilan-1/klowcode.git
cd klowcode
bun install
bun run build:dev:full
./cli-dev        # macOS / Linux
./cli-dev.exe   # Windows
```

This builds with **all 54 experimental features unlocked**.

### macOS / Linux — One-liner

```bash
curl -fsSL https://raw.githubusercontent.com/Ahilan-1/klowcode/main/install.sh | bash
```

Automatically installs Bun if needed, clones, builds, and puts `klowcode` on your PATH.

---

Then:

```bash
klowcode          # launch the interactive REPL
klowcode /login   # authenticate with your provider
```

---

## Table of Contents

- [What makes KlowCode different](#what-makes-klowcode-different)
- [Quick Install](#-quick-install)
- [Model Providers](#-model-providers)
- [Unlocked Features](#-unlocked-features)
- [Build from Source](#-build-from-source)
- [Usage](#-usage)
- [Project Structure](#-project-structure)
- [Tech Stack](#-tech-stack)
- [IPFS Mirror](#-ipfs-mirror)
- [Contributing](#-contributing)
- [License](#-license)

---

## 🔌 Model Providers

KlowCode works with **five providers** out of the box. Switch with an environment variable — no code changes needed.

| Provider | Env Variable | Auth |
|---|---|---|
| **Anthropic** (default) | — | `ANTHROPIC_API_KEY` or `/login` OAuth |
| **OpenAI Codex** | `CLAUDE_CODE_USE_OPENAI=1` | OpenAI OAuth |
| **AWS Bedrock** | `CLAUDE_CODE_USE_BEDROCK=1` | AWS credentials |
| **Google Vertex AI** | `CLAUDE_CODE_USE_VERTEX=1` | `gcloud` ADC |
| **Anthropic Foundry** | `CLAUDE_CODE_USE_FOUNDRY=1` | `ANTHROPIC_FOUNDRY_API_KEY` |

### Anthropic (default)

| Model | ID |
|---|---|
| Claude Opus 4.6 | `claude-opus-4-6` |
| Claude Sonnet 4.6 | `claude-sonnet-4-6` |
| Claude Haiku 4.5 | `claude-haiku-4-5` |

```bash
export ANTHROPIC_API_KEY="sk-ant-..."
klowcode
```

### OpenAI Codex

| Model | ID |
|---|---|
| GPT-5.3 Codex (recommended) | `gpt-5.3-codex` |
| GPT-5.4 | `gpt-5.4` |
| GPT-5.4 Mini | `gpt-5.4-mini` |

```bash
export CLAUDE_CODE_USE_OPENAI=1
klowcode
```

### AWS Bedrock

```bash
export CLAUDE_CODE_USE_BEDROCK=1
export AWS_REGION="us-east-1"
klowcode
```

Uses standard AWS credentials (`~/.aws/config`, env vars, or IAM role). Models are mapped to Bedrock ARN format automatically.

### Google Cloud Vertex AI

```bash
export CLAUDE_CODE_USE_VERTEX=1
klowcode
```

Uses `gcloud` Application Default Credentials (`gcloud auth application-default login`).

### Anthropic Foundry

```bash
export CLAUDE_CODE_USE_FOUNDRY=1
export ANTHROPIC_FOUNDRY_API_KEY="..."
klowcode
```

---

## 🔓 Unlocked Features

The official Claude Code release ships with 88 feature flags — nearly all disabled. KlowCode enables every one of the **54 that compile cleanly**. See [FEATURES.md](FEATURES.md) for the full audit.

### Interaction & UI

| Flag | What you get |
|---|---|
| `ULTRATHINK` | Deep reasoning mode — type `ultrathink` in any prompt to massively boost thinking effort |
| `ULTRAPLAN` | Remote multi-agent planning via Opus-class models |
| `VOICE_MODE` | Push-to-talk voice input and live dictation |
| `TOKEN_BUDGET` | Real-time token usage tracking and budget warnings |
| `HISTORY_PICKER` | Interactive fuzzy search over your prompt history |
| `MESSAGE_ACTIONS` | Per-message action menu in the REPL |
| `QUICK_SEARCH` | Instant prompt quick-search |
| `SHOT_STATS` | Per-session shot distribution stats |

### Agents, Memory & Planning

| Flag | What you get |
|---|---|
| `BUILTIN_EXPLORE_PLAN_AGENTS` | Built-in Explore and Plan agent presets |
| `VERIFICATION_AGENT` | Auto-verifies task completion with a second-pass agent |
| `AGENT_TRIGGERS` | Local cron-style triggers for background automation |
| `AGENT_TRIGGERS_REMOTE` | Remote trigger support |
| `EXTRACT_MEMORIES` | Automatic memory extraction after each query |
| `COMPACTION_REMINDERS` | Smart reminders when approaching context limits |
| `CACHED_MICROCOMPACT` | Cached microcompaction to speed up long sessions |
| `TEAMMEM` | Shared team-memory files with watcher hooks |

### Tools & Infrastructure

| Flag | What you get |
|---|---|
| `BRIDGE_MODE` | Full IDE remote-control bridge for VS Code and JetBrains |
| `BASH_CLASSIFIER` | AI-assisted bash permission decisions |
| `PROMPT_CACHE_BREAK_DETECTION` | Detects cache breaks in compaction flows |

---

## 🛠 Build from Source

### Requirements

- [Bun](https://bun.sh) >= 1.3.11
- macOS or Linux (Windows via WSL)

```bash
# Install Bun
curl -fsSL https://bun.sh/install | bash

# Clone and build
git clone https://github.com/Ahilan-1/klowcode.git
cd klowcode
bun install
bun run build:dev:full   # recommended: all 54 features unlocked
./cli-dev
```

### Build Variants

| Command | Output | Features |
|---|---|---|
| `bun run build` | `./cli` | Stable only |
| `bun run build:dev` | `./cli-dev` | Stable + dev stamp |
| `bun run build:dev:full` | `./cli-dev` | **All 54 experimental flags** |
| `bun run compile` | `./dist/cli` | Compiled standalone |

### Cherry-pick Specific Flags

```bash
# Enable only UltraPlan + UltraThink
bun run ./scripts/build.ts --feature=ULTRAPLAN --feature=ULTRATHINK

# Start from the dev build and add one flag
bun run ./scripts/build.ts --dev --feature=BRIDGE_MODE
```

---

## 💻 Usage

```bash
# Interactive REPL
./cli-dev

# One-shot mode (non-interactive)
./cli-dev -p "refactor this file to use async/await"

# Pick a specific model
./cli-dev --model claude-opus-4-6

# OAuth login (for Claude.ai subscribers)
./cli-dev /login

# Run directly from source
bun run dev
```

### Environment Variables

| Variable | Purpose |
|---|---|
| `ANTHROPIC_API_KEY` | Anthropic API key |
| `ANTHROPIC_AUTH_TOKEN` | Auth token (alternative to API key) |
| `ANTHROPIC_MODEL` | Override default model |
| `ANTHROPIC_BASE_URL` | Custom API endpoint |
| `ANTHROPIC_DEFAULT_OPUS_MODEL` | Custom Opus model ID |
| `ANTHROPIC_DEFAULT_SONNET_MODEL` | Custom Sonnet model ID |
| `ANTHROPIC_DEFAULT_HAIKU_MODEL` | Custom Haiku model ID |
| `CLAUDE_CODE_OAUTH_TOKEN` | Pass OAuth token via environment |
| `CLAUDE_CODE_USE_OPENAI` | Switch to OpenAI Codex provider |
| `CLAUDE_CODE_USE_BEDROCK` | Switch to AWS Bedrock provider |
| `CLAUDE_CODE_USE_VERTEX` | Switch to Google Vertex AI |
| `CLAUDE_CODE_USE_FOUNDRY` | Switch to Anthropic Foundry |

---

## 📁 Project Structure

```
scripts/
  build.ts                # Build script + feature flag bundler

src/
  entrypoints/cli.tsx     # CLI entrypoint
  commands.ts             # Slash command registry
  tools.ts                # Agent tool registry
  QueryEngine.ts          # LLM query pipeline
  screens/REPL.tsx        # Main interactive UI (Ink/React)

  commands/               # /slash command implementations
  tools/                  # Agent tool implementations (Bash, Read, Edit, etc.)
  components/             # Terminal UI components (Ink/React)
  hooks/                  # React hooks
  services/
    api/                  # API client + provider adapters
    oauth/                # OAuth flows (Anthropic + OpenAI)
  state/                  # App state store
  utils/                  # Shared utilities
    model/                # Model configs, provider routing, validation
  skills/                 # Skill system
  plugins/                # Plugin system
  bridge/                 # IDE bridge (VS Code / JetBrains)
  voice/                  # Voice input
  tasks/                  # Background task management
```

---

## 🧰 Tech Stack

| Layer | Technology |
|---|---|
| Runtime | [Bun](https://bun.sh) |
| Language | TypeScript |
| Terminal UI | React + [Ink](https://github.com/vadimdemedes/ink) |
| CLI Parsing | [Commander.js](https://github.com/tj/commander.js) |
| Schema Validation | Zod v4 |
| Code Search | ripgrep (bundled) |
| Protocols | MCP, LSP |
| AI APIs | Anthropic, OpenAI Codex, AWS Bedrock, Google Vertex AI, Anthropic Foundry |

---

## 📡 IPFS Mirror

This repository is permanently pinned on IPFS via Filecoin. If it gets taken down, the code survives.

| | |
|---|---|
| **CID** | `bafybeiegvef3dt24n2znnnmzcud2vxat7y7rl5ikz7y7yoglxappim54bm` |
| **Gateway** | https://w3s.link/ipfs/bafybeiegvef3dt24n2znnnmzcud2vxat7y7rl5ikz7y7yoglxappim54bm |

---

## 🤝 Contributing

PRs are welcome. The highest-value contribution right now is restoring the **34 broken feature flags** — many are close to compiling and just need a small wrapper or missing asset. Check the reconstruction notes in [FEATURES.md](FEATURES.md) before starting.

```bash
git checkout -b feat/restore-FLAG_NAME
# make your changes
git commit -m 'feat: restore FLAG_NAME'
git push origin feat/restore-FLAG_NAME
# open a Pull Request
```

---

## ⭐ If this helped you

Star the repo. Share it. That's the only growth mechanism here.

---

## 📄 License

The original Claude Code source is the property of Anthropic, exposed through their npm distribution on March 31, 2026. KlowCode applies modifications on top of that public snapshot. Use at your own discretion.
