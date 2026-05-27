# AionUi

> Free, open-source, cross-platform Cowork desktop app with a built-in AI agent engine, multi-agent orchestration, and 24/7 scheduled automation. Auto-detects 20+ CLI agents.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [aionui.com](https://aionui.com/) |
| **Repository** | [github.com/iOfficeAI/AionUi](https://github.com/iOfficeAI/AionUi) |
| **Status** | `Active` — 26,812 GitHub stars; latest release v2.1.4 |
| **Openness** | `Open source (Apache-2.0)` |
| **Deployment** | `Local-first` — Electron desktop app for macOS, Windows, Linux; optional WebUI server mode |
| **First release** | 2025-08-07 |
| **Last release / commit** | 2026-05-27 (v2.1.4) |
| **Language / Stack** | TypeScript, Electron, Vite, React, Bun |
| **License** | Apache-2.0 |

## What It Does

AionUi is a cross-platform desktop application that provides a unified Cowork interface for AI agents. It includes a built-in agent engine (zero setup required) and auto-detects 20+ external CLI agents including Claude Code, Codex, Gemini CLI, OpenClaw, Hermes Agent, and more. Users can run multiple agents in parallel, delegate tasks through a Leader-Teammate orchestration model, and schedule automated tasks with cron expressions. The app also features built-in document generation (PPT, Word, Excel) via OfficeCLI skills.

## Key Mechanisms

- **Built-in agent engine** — Ships with a complete agent runtime; no CLI installation required. Works immediately after install with Google sign-in or any API key
- **Auto-detection of 20+ CLI agents** — Automatically recognizes installed CLI tools (Claude Code, Codex, Qwen Code, OpenClaw, Hermes Agent, Cursor Agent, etc.) and integrates them into a unified interface
- **Multi-agent team mode** — Leader agent receives instructions, breaks them into subtasks, and delegates to Teammate agents running in parallel via ACP (Agent Communication Protocol). Teammates share results through an async mailbox and write to a shared task board
- **24/7 scheduled automation** — Cron expressions with timezone support, fixed intervals, or one-time triggers. Tasks can bind to existing conversations or create new ones. Auto-prevents system sleep during execution
- **MCP unified management** — Configure MCP tools once, automatically sync to all agents without per-agent setup
- **21 built-in professional assistants** — Cowork, PPT Creator, Word Creator, Excel Creator, Academic Paper Writer, Financial Model Creator, UI/UX Pro Max, and more
- **Three-tier skill system** — Built-in skills (pptx, docx, xlsx, mermaid, etc.), custom skills, and Extension SDK skills. Enable/disable per conversation
- **Multi-platform access** — Desktop GUI + WebUI (LAN/cross-network/server) + Telegram / Lark / DingTalk / WeChat bots
- **YOLO / Full-Auto mode** — One-click auto-approve all agent actions for unattended execution
- **Built-in preview** — 10+ format preview panel (PDF, Word, Excel, PPT, code, Markdown, HTML, images) with version history

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Multi-agent hierarchical — built-in agent + auto-detected external CLI agents. Team mode adds Leader/Teammate delegation with parallel execution |
| **Coordination mechanism** | ACP (Agent Communication Protocol) for multi-agent coordination; Leader assigns subtasks, Teammates execute in parallel with async mailbox. MCP tools unified across all agents |
| **Human oversight** | Each agent has its own permission confirmation dialog; sidebar badge shows pending approvals. YOLO mode allows bypassing confirmations |

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | Local SQLite database; all data stored locally, nothing uploaded to external servers |
| **Data portability** | **High** — conversations and files stored locally; documents generated as editable formats (pptx, docx, xlsx) |
| **Offline capability** | Partial — local agent execution and scheduled tasks work offline; LLM API calls require internet unless using Ollama/LM Studio locally |
| **Vendor lock-in risk** | **Low** — open source (Apache-2.0), supports 30+ AI platforms including local models, multi-agent interoperability via MCP |

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source / self-hosted | $0 | Free desktop app; bring your own API keys |

## Ecosystem & Integrations

- **AI platforms**: Gemini, Claude, OpenAI, DeepSeek, Qwen, Ollama, LM Studio, and 30+ more via NewAPI gateway
- **CLI agents**: Claude Code, Codex, Gemini CLI, OpenClaw, Hermes Agent, Cursor Agent, Qwen Code, Goose AI, Augment Code, and 13+ more
- **Chat platforms**: Telegram, Lark (Feishu), DingTalk, WeChat, WeCom, Slack, Discord
- **Protocols**: MCP (Model Context Protocol), ACP (Agent Communication Protocol)
- **Skills**: pptx, docx, xlsx, pdf, mermaid, and custom skills via Extension SDK
- **Community**: Discord (English), WeChat (中文), Twitter/X
- **Install**: macOS (Homebrew `brew install aionui`), Windows, Linux

## Screenshots / Demo

- [AionUi GitHub repository — README with features and quickstart](https://github.com/iOfficeAI/AionUi)
- [Official website](https://aionui.com/)
- [YouTube reviews and demos](https://www.youtube.com/results?search_query=aionui)

## References

- [AionUi GitHub repository](https://github.com/iOfficeAI/AionUi)
- [AionUi official website](https://aionui.com/)
