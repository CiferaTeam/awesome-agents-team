# Octos

> Rust-native, API-first Agentic OS — a single 31MB binary that turns any LLM into a multi-channel, multi-tenant intelligent assistant with zero runtime dependencies.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [octosai.org](https://www.octosai.org) |
| **Repository** | [github.com/octos-org/octos](https://github.com/octos-org/octos) |
| **Status** | `Active` — last commit 2026-05-25; actively developed with frequent releases |
| **Openness** | `Open source (Apache-2.0)` |
| **Deployment** | `Self-hosted` — single static binary; local, VPS, or cloud-and-device pair |
| **First release** | 2026-03-15 |
| **Last release / commit** | 2026-05-25 (last commit) |
| **Language / Stack** | Rust (primary); React SPA dashboard; redb embedded database |
| **License** | Apache-2.0 |

## What It Does

Octos is a backend operating system for AI agents. Instead of building a new chatbot stack for every use case, you deploy one Rust binary, connect LLM providers and messaging channels, and Octos handles routing, sessions, tools, memory, provider failover, and multi-user isolation through a web dashboard and 91 REST endpoints. It is designed as infrastructure rather than a library — multi-tenant by default, with each profile running as an isolated OS process.

## Key Mechanisms

- **Single 31MB static binary**: Zero runtime dependencies — no Python, no Docker, no pip install. Download, set an API key, and run.
- **Multi-tenant by design**: One binary serves 200+ profiles on a 16GB machine. Each profile is an isolated OS process with private memory, sessions, and data. Family Plan sub-accounts supported.
- **3-layer provider failover**: RetryProvider → ProviderChain → AdaptiveRouter, with hedge racing, lane scoring, and circuit breakers. Automatically switches providers when one goes down.
- **Multi-LLM DOT pipelines**: Define workflows as DOT graphs with per-node model selection. Dynamic parallel fan-out spawns N concurrent workers at runtime.
- **LRU tool deferral**: 30+ tools available, but only 15 loaded at once for fast LLM reasoning. Idle tools auto-evict; spawn-only tools redirect to background execution.
- **5 queue modes per session**: Followup, Collect, Steer, Interrupt, Speculative — users control agent concurrency via `/queue`.
- **3-layer memory**: Long-term entity bank (auto-injected), episodic task outcomes in redb, and session JSONL with LLM compaction. Pure Rust BM25 + HNSW hybrid search built in.
- **Native office suite**: Generates PPTX, DOCX, and XLSX via pure Rust (zip + quick-xml) with no external tools.
- **Sandbox isolation**: bwrap + sandbox-exec + Docker. `deny(unsafe_code)` workspace-wide. 67 prompt-injection tests.

## Agent Architecture

- **Agent model**: Multi-tenant single-agent-per-profile + multi-step pipeline workers (parallel fan-out)
- **Coordination mechanism**: Gateway-based message routing across 14 channels; DOT graph pipeline executor for multi-step workflows; shared bus for inter-profile communication
- **Human oversight**: Humans configure profiles, set provider chains, approve tool activations, and review outputs via the web dashboard or REST API

## Data & Storage Model

- **Primary store**: Self-hosted — redb embedded database for episodic memory; local JSONL for sessions; filesystem for agent workspaces
- **Data portability**: **High** — no external database required; single binary + config files
- **Offline capability**: Partial — local models supported; some channels (e.g., Telegram, Discord) require internet
- **Vendor lock-in risk**: **Low** — open source (Apache-2.0), 15+ LLM providers, self-hosted by design, no cloud dependency

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source / self-hosted | $0 | Self-build and self-host from source |

## Ecosystem & Integrations

- **LLM providers**: 15 built-in (Anthropic, OpenAI, Gemini, DeepSeek, OpenRouter, and more)
- **Messaging channels**: 14 native — Telegram, Discord, Slack, WhatsApp, Feishu, Email, WeCom, WeChat, Matrix, QQ Bot, Twilio, API, CLI
- **Tool suite**: 30+ tools including shell, file I/O, web search, browser, deep search, cron, memory recall/save, spawn, and skill activation
- **Memory**: Built-in BM25 + HNSW hybrid search over redb; no external vector DB required
- **Deploy options**: Single binary on ARM/x86/RISC-V; cargo install; Docker optional
- **Community**: GitHub Issues at [octos-org/octos](https://github.com/octos-org/octos/issues), [octos-hub skill registry](https://github.com/octos-org/octos-hub)

## Screenshots / Demo

- [GitHub README (includes architecture diagram and quickstart)](https://github.com/octos-org/octos)
- [octosai.org](https://www.octosai.org)

## References

- [Octos Documentation](https://github.com/octos-org/octos#documentation)
- [Octos Web Dashboard](https://github.com/octos-org/octos-web)
- [Building an AI Operating System with Octos — GOSIM Paris 2026](https://paris2026.gosim.org/zh/schedule/from-llm-apps-to-agent-systems-building-an-ai-operating-system-with-octos/)
