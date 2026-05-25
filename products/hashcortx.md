# HashCortX

> Local-first, open-source AI desktop application combining multi-provider chat, autonomous coding, multi-agent swarms, financial analysis, and security scanning in a single 8.9 MB native macOS app.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [hashcortx.com](https://hashcortx.com) |
| **Repository** | [github.com/Hash-7777/HashCortX](https://github.com/Hash-7777/HashCortX) |
| **Status** | `Active` — v2.0.0 released May 2026; last commit 2026-05-24 |
| **Openness** | `Open source (MIT)` |
| **Deployment** | `Local-first` — native macOS desktop app; no cloud backend |
| **First release** | 2026-05-16 (repo creation) — v2.0.0 first public release |
| **Last release / commit** | 2026-05-24 (last commit) |
| **Language / Stack** | Tauri v2 (Rust backend + native webview), vanilla JavaScript frontend |
| **License** | MIT |

## What It Does

HashCortX is a local-first AI desktop workspace that packs 11 specialized modes into one tiny native app. It includes multi-provider chat, an autonomous coding agent (HashCoder), multi-agent swarms with automatic provider failover, financial document analysis, security scanning, 3D planning, and a no-code custom agent builder — all without any cloud backend, telemetry, or accounts.

## Key Mechanisms

- **Eleven specialized modes**: Chats, Agents, Code, Split comparison, 3D Forge, Finance AI, Sandbox security scanner, ERP builder, Agent Swarm, Virtual OS, and Agent Maker.
- **Multi-agent swarm with failover**: Designer for multi-agent pipelines with voting, chaining, and automatic provider failover when a model rate-limits or fails mid-run.
- **Permission Guard + Audit Log**: Filesystem and shell calls from the coding agent are intercepted by a denylist-based gatekeeper before execution; every guarded action is logged.
- **Source-grounded constraints**: PubMed Agent, Drug Interaction, and Finance AI modes are constrained to never fabricate data.
- **Truly local-first**: No cloud backend, no telemetry, no analytics, no accounts. With Ollama, the app runs fully air-gapped offline.

## Agent Architecture

- **Agent model**: Single and multi-agent swarm modes; 9 pre-built specialist agents plus custom no-code agent builder
- **Coordination mechanism**: Agent Swarm mode supports voting mode, chain mode, and automatic provider failover; inter-agent coordination is pipeline-based
- **Human oversight**: Permission Guard intercepts filesystem and shell calls; humans configure denylist rules and review the Audit Log

## Data & Storage Model

- **Primary store**: Local filesystem + renderer localStorage for API keys; no server-side state
- **Data portability**: App data lives in local files; attachments and project files are standard filesystem objects
- **Offline capability**: Fully offline with Ollama; cloud providers require internet but no HashCortX intermediary server
- **Vendor lock-in risk**: **Low** — local files, MIT-licensed, no proprietary formats

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source | $0 | Unlimited; BYO API keys or use Ollama for free local inference |

## Ecosystem & Integrations

- **Platform**: macOS Apple Silicon (Intel Mac, Windows, Linux planned)
- **AI providers**: Anthropic, OpenAI, Google, Groq, Cerebras, SambaNova, DeepSeek, Moonshot, Mistral, OpenRouter, Ollama (local)
- **API / extensibility**: No-code Agent Maker for custom agents with name, icon, system prompt, and curated tool sets
- **Community**: GitHub Issues and Discussions at [Hash-7777/HashCortX](https://github.com/Hash-7777/HashCortX)

## Screenshots / Demo

- [GitHub README with feature overview](https://github.com/Hash-7777/HashCortX)

## References

- [Hash-7777/HashCortX on GitHub](https://github.com/Hash-7777/HashCortX)
- [HashCortX Wiki](https://github.com/Hash-7777/HashCortX/wiki)
