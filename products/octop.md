# Octop

> Self-hosted, multi-user AI assistant where each user runs a switchable team of expert agents, reachable through a web dashboard, CLI, and IM channels.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [octop.cloud](https://octop.cloud) |
| **Repository** | [github.com/TencentCloud/Octop](https://github.com/TencentCloud/Octop) |
| **Status** | `Active (beta)` — v1.0.2b6 (2026-10); ~8k GitHub stars |
| **Openness** | `Open source (MIT)` |
| **Deployment** | `Self-hosted` — single process on macOS/Linux/Windows; Docker Compose supported; data under `~/.octop/` |
| **First release** | 2026-07 |
| **Last release / commit** | 2026-10 (v1.0.2b6) |
| **Language / Stack** | Python 3.12+ (FastAPI), React 18 + TypeScript + Ant Design (web dashboard), native desktop clients |
| **License** | MIT |

## What It Does

Octop is an open-source, self-hosted AI assistant platform from Tencent Cloud, built for households and small teams. One process serves a web dashboard, CLI, IM channels (Feishu, DingTalk, QQ, WeChat, WeCom, Telegram, Discord), and cron automation, all sharing a single control-plane database. Each user gets multiple "experts" — specialized agents with their own workspace, model providers, channels, and schedules — and an admin can share experts and knowledge bases across the whole deployment. The design keeps every conversation, workspace, and credential on your own machine, so privacy is the default rather than a tier.

## Key Mechanisms

- **Expert model**: multiple experts per user, each with its own workspace, providers, channels, and cron; 16 MBTI persona templates plus custom system prompts
- **Expert sharing & shared pools**: publish experts within a deployment, plus a shared skill/sub-agent pool so teammates reuse proven setups instead of rebuilding
- **AgentTeams (beta)**: a coordinator expert schedules and orchestrates member experts for multi-step tasks
- **Octop Memory**: hierarchical recall with full-text search; an agent's memory migrates with its workspace
- **Knowledge base**: RAG over your documents, shareable within a deployment, grounding answers in private data
- **Connectors**: OAuth + MCP gateway extends resource boundaries; Tencent suite connectors (Docs, Meeting, News)
- **Bidirectional ACP**: inbound — Zed/OpenCode drive your Octop agent over stdio; outbound — delegate coding to OpenCode, Claude Code, Codex, or CodeBuddy behind permission gates
- **Surfaces beyond chat**: Browser AI+ (headless Chromium sessions), remote desktop control from the dashboard, and Terminal AI+ (AI-assisted shell in the browser)
- **Pluggable workspace backends**: agent files on local disk, Docker sandbox, PostgreSQL, or COS/S3 — separate from the control-plane DB
- **Security**: JWT multi-user isolation, tool approval, shell command guardrails, PII redaction
- **Single-process design**: web UI, IM, and cron all route through one in-process HarnessProcessor; state is rebuilt from the control-plane database on boot, with no external queue or broker

## Agent Architecture

- **Agent model**: Multi-agent hierarchical — per-user experts; AgentTeams (beta) adds a coordinator that schedules member experts for multi-step work
- **Coordination mechanism**: In-process coordinator dispatch; shared skill/sub-agent pools and expert market for cross-user reuse
- **Human oversight**: Tool approval, ACP permission gates, PII redaction, admin role, and per-user workspace isolation

## Data & Storage Model

- **Primary store**: Local SQLite (WAL) under `~/.octop/` by default; PostgreSQL optional. Agent workspace files live on pluggable backends (local disk, Docker sandbox, PostgreSQL, COS/S3)
- **Data portability**: Conversations, memory, and workspace files all live under one local directory; Octop Memory is designed to migrate with the workspace
- **Offline capability**: Runs fully self-hosted; model inference depends on your chosen provider endpoints (local ONNX embedding models optional)
- **Vendor lock-in risk**: **Low** — MIT license, single-machine deployment, standard SQL storage, bring-your-own model providers

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source / self-hosted | $0 | Free; bring your own model/API keys and infrastructure |
| Managed Agents (planned) | Unknown | Platform-hosted agent lifecycle, in roadmap |

## Ecosystem & Integrations

- **IM channels**: Feishu, DingTalk, QQ, WeChat, WeCom, Telegram, Discord (via Octop Gateway)
- **Coding agents (ACP)**: OpenCode, Claude Code, Codex, CodeBuddy as outbound runners; Zed/OpenCode as inbound clients
- **Extensibility**: Plugins, Connectors (OAuth + MCP), expert market, shared skill/sub-agent pools
- **Related projects**: [Octop Harness](https://github.com/TencentCloud/octop-harness) (agent runtime), [Octop Gateway](https://github.com/TencentCloud/octop-gateway) (IM bridge), [Octop Memory](https://github.com/TencentCloud/octop-memory), [Octop Browser](https://github.com/TencentCloud/octop-browser)
- **Deployment**: one-line installer, PyPI (`pip install octop`), Docker Compose, native desktop apps (Windows/macOS/Linux), FnOS NAS packages
- **Community**: [Discord](https://discord.gg/QnWdhJxq9h)

## Compared with GitIM

GitIM keeps collaboration events as plain-text Git commits across three local binaries with no server — the Git repository is both workspace and audit trail. Octop is a full self-hosted platform with a server control plane (SQLite/PostgreSQL), multi-user JWT auth, and IM channel integrations; it does not use Git as its conversation protocol. GitIM favors protocol minimalism and auditability; Octop favors a ready-to-use multi-user assistant with rich surfaces.

## Screenshots / Demo

- [GitHub README — banner and quickstart](https://github.com/TencentCloud/Octop)
- [Desktop client installers](https://github.com/TencentCloud/Octop/releases/latest)

## References

- [TencentCloud/Octop on GitHub](https://github.com/TencentCloud/Octop)
- [Octop cloud homepage](https://octop.cloud)
- [PyPI: octop](https://pypi.org/project/octop/)
- [Octop Memory](https://github.com/TencentCloud/octop-memory)
- [Octop releases](https://github.com/TencentCloud/Octop/releases)
