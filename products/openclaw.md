# OpenClaw

> Autonomous AI agent framework for system-level task execution — connects LLMs to real-world surfaces like shell commands, file systems, browsers, and messaging platforms with persistent memory and a heartbeat runtime.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [openclaw.ai](https://openclaw.ai) |
| **Repository** | [github.com/OpenClaw/OpenClaw](https://github.com/OpenClaw/OpenClaw) |
| **Status** | `Active` — last commit 2026-05-25; largest open-source agent community on GitHub |
| **Openness** | `Open source (MIT)` |
| **Deployment** | `Self-hosted` — Node.js runtime; local machine, VPS, or Docker |
| **First release** | 2025-11-24 |
| **Last release / commit** | 2026-05-25 (last commit) |
| **Language / Stack** | TypeScript (Node.js 20+); npm-based; ~430K LOC |
| **License** | MIT |

## What It Does

OpenClaw is an open-source autonomous AI agent framework that connects large language model inference to real-world execution surfaces: shell command execution, file system access, browser automation, Docker container management, and a wide array of third-party messaging platforms. Unlike reactive chatbots, it operates on a continuous heartbeat, proactively executing multi-step workflows, managing files, and browsing the web autonomously. It is designed as a 24/7 autonomous digital worker rather than a conversational assistant.

## Key Mechanisms

- **System-level agency**: Direct OS integration — reads/writes files, executes shell commands, runs Python and Node.js scripts, automates browsers, and manages Docker containers.
- **Continuous heartbeat runtime**: Operates autonomously on a heartbeat loop rather than waiting for prompts, enabling proactive task execution and monitoring.
- **SOUL.md configuration**: Define agent personality, capabilities, and constraints via a declarative configuration file, enabling highly specialized assistants.
- **Persistent semantic memory**: Markdown-based long-term storage combined with vector search, allowing agents to remember context across sessions.
- **Multi-model engine**: Native support for Claude, GPT, Gemini, DeepSeek, and local models via Ollama, with intelligent routing and fallback logic.
- **WebSocket gateway**: Central hub connecting 20+ messaging channels including Telegram, Discord, Slack, and WhatsApp for real-time bidirectional communication.
- **Skill marketplace**: 1,600+ community-verified skills across categories like data extraction, social media management, and RAG pipeline orchestration.
- **Plugin & skills system**: Modular plugin architecture with cryptographically signed skills, enabling extensible agent capabilities.

## Agent Architecture

- **Agent model**: Single persistent agent with skill library + plugin-based capability extension
- **Coordination mechanism**: Gateway-centric architecture with channel system, agent runtime, and memory system; WebSocket hub routes messages across 20+ platforms; SOUL.md template engine drives personality and capabilities
- **Human oversight**: Humans configure SOUL.md profiles, approve skill installations, review autonomous actions, and set API/provider limits via environment variables

## Data & Storage Model

- **Primary store**: Self-hosted — Markdown-based semantic memory + vector index; local filesystem for agent workspaces; SQLite for structured data
- **Data portability**: **High** — memory is local Markdown and vector files; configurations are plain text
- **Offline capability**: Partial — local models via Ollama supported; messaging channels require internet
- **Vendor lock-in risk**: **Low** — open source (MIT), multi-model support, self-hosted by design, no proprietary cloud dependency

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source / self-hosted | $0 | Self-build and self-host; bring your own model API keys |
| Managed hosting (OneClaw) | From ~$9.99/mo | Managed cloud deployment of the same open-source runtime |

## Ecosystem & Integrations

- **LLM providers**: Anthropic Claude, OpenAI GPT, Google Gemini, DeepSeek, and local models via Ollama
- **Messaging channels**: 20+ including Telegram, Discord, Slack, WhatsApp, and custom API
- **Tool access**: Shell execution, file system, browser automation, Docker management, MCP-compatible tools, and 1,600+ community skills
- **Deploy options**: Node.js 20+ on macOS, Linux, Windows (WSL2); Docker Compose; managed hosting via OneClaw
- **Related projects**: OneClaw (managed hosting platform), OpenClaw Launch, Copaw (community fork)
- **Community**: 180K+ Discord members, 450K+ Reddit members, active GitHub Discussions

## Screenshots / Demo

- [GitHub README (includes architecture diagram and quickstart)](https://github.com/OpenClaw/OpenClaw)
- [OpenClaw AI on GitHub — Explained](https://www.oneclaw.net/blog/openclaw-ai-github)

## References

- [A Security Analysis of the OpenClaw AI Agent Framework](https://arxiv.org/html/2603.27517v2)
- [OpenClaw: The Rise of an Open-Source AI Agent Framework](https://www.clawbot.blog/blog/openclaw-the-rise-of-an-open-source-ai-agent-framework-april-2026-update/)
- [OpenClaw Documentation](https://docs.openclaw.ai/)
