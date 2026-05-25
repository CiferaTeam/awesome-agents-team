# Lingtai

> Unix-style Agent OS — agents live in the filesystem, communicate by mailbox, spawn independent avatars, and grow into a self-extending network with no central scheduler and no shared state.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [lingtai.ai](https://lingtai.ai) |
| **Repository** | [github.com/Lingtai-AI/lingtai](https://github.com/Lingtai-AI/lingtai) |
| **Status** | `Active` — last commit 2026-05-25; actively developed with frequent releases |
| **Openness** | `Open source (MIT)` |
| **Deployment** | `Local-first` — TUI runs locally; agents live as directories on the local filesystem |
| **First release** | 2025 |
| **Last release / commit** | 2026-05-25 (last commit) |
| **Language / Stack** | Go 1.24+ (TUI and Portal); Python 3.11+ (kernel runtime); Bubble Tea (TUI framework) |
| **License** | MIT |

## What It Does

Lingtai is an agent operating system that treats every agent as a directory on the filesystem. Instead of orchestrating agents through code-defined DAGs or shared memory, Lingtai gives each agent its own persistent directory containing identity, memory, covenant, and mailbox. Agents communicate asynchronously by writing files to each other's inboxes — no message broker, no central controller. This architecture enables agents to spawn fully independent avatar processes that survive their creator, form a decentralized network, and scale indefinitely without a single point of failure.

## Key Mechanisms

- **Agent-as-directory**: Each agent is a self-contained directory (`/agents/<name>/`) with a manifest, heartbeat, lock file, system notes, and mailbox. The path is the identity — no abstract `agent_id`.
- **Filesystem mail system**: Agents communicate by writing JSON message files to each other's `mailbox/inbox/`. Outbox and sent directories provide delivery tracking and audit trails. The protocol is pure filesystem — no SDK, no API, no dependencies.
- **Avatar spawning**: Agents can spawn `avatar` processes that run as fully independent OS processes with their own directories and lifecycles. Avatars survive the death or shutdown of their creator. `daemon` provides ephemeral parallel workers for quick tasks.
- **Molt (rebirth)**: The `molt` mechanism compacts conversation context and restarts the agent session, allowing an agent to live indefinitely. Memory and identity survive across molts via the `covenant.md` and `pad.md` files.
- **Nineteen capabilities ("seventy-two transformations")**: Built-in skills spanning perception (vision, listen, web_search, web_read), action (file, bash, talk, compose, draw, video), cognition (psyche, codex, email), and networking (avatar, daemon).
- **Two-layer architecture**: `lingtai-kernel` provides the minimal Python runtime (BaseAgent, intrinsics, LLM protocol, mail, logging) with zero hard dependencies. `lingtai` (this repo) provides the batteries-included Go layer (TUI, Portal, recipes, skills, addons).

## Agent Architecture

- **Agent model**: Multi-agent peer network (autonomous agents as directories) + avatar/daemon spawning
- **Coordination mechanism**: Asynchronous filesystem message passing between peer agents; no central scheduler, no shared state, no vector database. Agents discover each other by path and communicate by mailbox writes.
- **Human oversight**: Humans interact through the TUI (`lingtai-tui`) or share the `.lingtai/human/` mailbox. Programming agents (Claude Code, Codex CLI, etc.) can read agent mail and send instructions via filesystem plugins. Humans define covenants and review agent outputs; the network continues even if individual agents sleep or fail.

## Data & Storage Model

- **Primary store**: Local filesystem — each agent owns its directory tree (`system/`, `mailbox/`, `logs/`). State is transparent and human-readable.
- **Data portability**: **High** — all state is plain files (Markdown, JSONL, JSON). Agents can be copied, archived, or migrated by moving directories.
- **Offline capability**: **Full** — runs entirely on local filesystem with local or remote LLM APIs. No cloud dependency for core operation.
- **Vendor lock-in risk**: **Low** — open source (MIT), model-agnostic (supports any OpenAI-compatible API), protocol is pure filesystem with no proprietary formats.

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source | $0 | Unlimited; self-build and self-host from source |

## Ecosystem & Integrations

- **LLM providers**: Anthropic, OpenAI, Google Gemini, MiniMax, DeepSeek, Grok, Qwen, GLM, Kimi, or any OpenAI-compatible API
- **Programming agent plugins**: Claude Code plugin (`Lingtai-AI/claude-code-plugin`), Codex CLI plugin (`Lingtai-AI/codex-plugin`), canonical `lingtai-skill` protocol for OpenCode, OpenClaw, Hermes, and other coding agents
- **Messaging addons**: Feishu/Lark (WebSocket long connection, no public IP needed), IMAP email, Telegram Bot API
- **MCP integration**: Supports MCP tools and servers
- **Portal**: Optional web portal (`lingtai-portal`) for browser-based management
- **Community**: GitHub Issues, GitHub Discussions, WeChat group (Chinese-speaking users)

## Screenshots / Demo

- [GitHub README (includes architecture diagram and TUI demo)](https://github.com/Lingtai-AI/lingtai)
- [lingtai.ai — full manifesto](https://lingtai.ai)

## References

- [Lingtai README (Chinese)](https://github.com/Lingtai-AI/lingtai/blob/main/README.zh.md)
- [Lingtai Kernel repository](https://github.com/Lingtai-AI/lingtai-kernel)
- [Claude Code Plugin](https://github.com/Lingtai-AI/claude-code-plugin)
- [Codex CLI Plugin](https://github.com/Lingtai-AI/codex-plugin)
- [Lingtai Skill (canonical protocol)](https://github.com/Lingtai-AI/lingtai-skill)
