# Hermes Agent

> Self-improving AI agent framework with a closed learning loop — it gets better at recurring tasks by autonomously generating and iterating skills from its own execution history.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [hermes-agent.nousresearch.com](https://hermes-agent.nousresearch.com) |
| **Repository** | [github.com/NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent) |
| **Status** | `Active` — last commit 2026-05-25; rapidly evolving with large community |
| **Openness** | `Open source (MIT)` |
| **Deployment** | `Self-hosted` — Docker or manual install on VPS, local machine, or serverless (Modal) |
| **First release** | 2025-07-22 |
| **Last release / commit** | 2026-05-25 (last commit) |
| **Language / Stack** | Python + Node.js; gateway process with modular skill system |
| **License** | MIT |

## What It Does

Hermes Agent is an open-source autonomous AI agent framework built by Nous Research. Its defining feature is a closed learning loop: after completing complex tasks, it automatically extracts successful strategies into structured skill documents, stores them in persistent memory, and retrieves + refines them on subsequent runs. Unlike traditional agents that reset every session, Hermes progressively improves at recurring workflows without manual tuning. It runs as a backend service exposing an OpenAI API-compatible endpoint, with native frontends including Telegram, Discord, Slack, WhatsApp, CLI, and Open WebUI.

## Key Mechanisms

- **Closed learning loop**: Auto-generates structured skill documents after complex task completions. No manual curation — the agent captures what worked and stores it for reuse.
- **Self-iterating skills**: When the agent discovers a better method for a known task, it overwrites the existing skill document. Skills evolve through execution, not configuration.
- **Two-layer memory**: MEMORY.md for persistent long-term context plus SQLite with full-text search over complete conversation and task history for fast retrieval.
- **40+ bundled skills**: Pre-installed skills covering MLOps, GitHub workflows, research, systematic debugging, test-driven development, and more. Supports the open agentskills.io format.
- **5-layer security**: User auth, command approval gates, container isolation, credential filtering, and injection scanning — all enabled by default.
- **OpenAI API-compatible server**: Exposes a standard chat completions endpoint. Connect Open WebUI, custom frontends, or any OpenAI-compatible client directly.
- **Subagent delegation**: Spawn isolated subagents for parallel workstreams via `delegate_task`, enabling concurrent execution.
- **Built-in cron scheduler**: Schedule recurring tasks with delivery to any connected platform.

## Agent Architecture

- **Agent model**: Single long-lived agent with skill library + parallel subagent spawning
- **Coordination mechanism**: Gateway-based message routing (Telegram, Discord, Slack, Email, WhatsApp); OpenAI-compatible API server for programmatic access; skill-driven task routing
- **Human oversight**: Humans configure channels, approve command gates, review generated skills, and manage credentials; configurable automation levels per skill

## Data & Storage Model

- **Primary store**: Self-hosted — SQLite for conversation history with FTS5 search; MEMORY.md for persistent long-term context; local filesystem for skill documents
- **Data portability**: **High** — skills are plain documents; memory is local files; no proprietary cloud required
- **Offline capability**: Partial — local models supported; messaging channels require internet
- **Vendor lock-in risk**: **Low** — open source (MIT), model-agnostic, self-hosted by design, standard OpenAI-compatible API

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source / self-hosted | $0 | Self-build and self-host; bring your own model API keys |
| VPS hosting | ~$5–20/mo | Minimal VPS runs the full stack; model API costs extra |

## Ecosystem & Integrations

- **LLM providers**: 200+ models via OpenRouter, Nous Portal, OpenAI, Anthropic, DeepSeek, and any OpenAI-compatible endpoint
- **Messaging platforms**: Telegram, Discord, Slack, WhatsApp, Signal, Email
- **Skills ecosystem**: 652 skills across four registries (72 built-in, 59 optional, 521 community); MCP servers supported
- **Memory integration**: Honcho dialectic user modeling for personalized responses
- **Deploy options**: Docker, manual install, Modal serverless, managed hosting via third parties
- **Community**: GitHub Issues at [NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent/issues)

## Screenshots / Demo

- [GitHub README (includes quickstart and architecture overview)](https://github.com/NousResearch/hermes-agent)
- [hermes-ccc — Hermes Agent Framework for Claude Code](https://github.com/NousResearch/hermes-ccc)

## References

- [Hermes Agent — Self-Evolving AI Agent Framework](https://agentskillshub.dev/skills/hermes-agent/)
- [What Is the Hermes Agent? — Plain-English Guide](https://openclawlaunch.com/guides/what-is-hermes-agent)
- [Hermes Agent: NousResearch's Self-Improving Open-Source Agent Framework](https://clauday.com/article/367ef753-e84f-4d23-ae7f-e87d4e0a55a9)
