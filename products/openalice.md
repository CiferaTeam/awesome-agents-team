# OpenAlice

> Your one-person Wall Street. A locally runnable AI trading agent covering equities, crypto, commodities, forex, and macro — from research through position entry, ongoing management, to exit.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [github.com/TraderAlice/OpenAlice](https://github.com/TraderAlice/OpenAlice) |
| **Repository** | [github.com/TraderAlice/OpenAlice](https://github.com/TraderAlice/OpenAlice) |
| **Status** | `Active` — 4,251 GitHub stars; Grand Prize winner at Monad Rebel in Paradise AI Hackathon (March 2026) |
| **Openness** | `Open source (AGPL-3.0)` |
| **Deployment** | `Self-hosted` — runs from source (Node.js 22+, pnpm 10+) or Docker; macOS DMG and Windows installer in flight |
| **First release** | 2026-02-18 (repository created) |
| **Last release / commit** | 2026-05-25 |
| **Language / Stack** | TypeScript (Node.js 22+, pnpm 10+, Turborepo); React Web UI; Docker support |
| **License** | AGPL-3.0 |

## What It Does

OpenAlice is a full-lifecycle AI trading agent that runs entirely on your own machine. It unifies research, strategy formulation, execution, and risk management into a single transparent workspace where every agent behavior is defined in human-readable Markdown and structured JSON. Unlike cloud-based trading bots, OpenAlice keeps private keys and account data local — the agent operates through native broker integrations but never outsources custody.

Users interact with Alice through multiple surfaces — a Web UI for chat and portfolio dashboards, Telegram for mobile trading panels, or an MCP server that exposes OpenAlice's tool surface to external agents. The core execution model is a **Workspace**: a per-task directory + git repo + persistent terminal session running a native agent CLI (Claude Code, Codex, or shell), with OpenAlice's MCP tools plumbed in. This gives the AI native prompt caching, native TUI rendering, and full access to the trading domain without protocol shims.

## Key Mechanisms

- **Unified Trading Account (UTA)** — Each UTA wraps a broker connection (CCXT, Alpaca, Interactive Brokers), operation history, guard pipeline, and snapshot scheduler into a self-contained workspace. AI and the frontend interact with UTAs exclusively; brokers are internal implementation details
- **Trading-as-Git** — Orders are staged, committed with a message, and pushed to execute. Push runs guards, dispatches to the broker, snapshots account state, and records a commit with an 8-char hash. Full history is reviewable like `git log` / `git show`
- **Guard pipeline** — Pre-execution safety checks (max position size, cooldown between trades, symbol whitelist) configured per account. Guards enforce limits before orders reach the broker
- **Workspace-centric execution** — A per-task directory + git repo + persistent terminal session running the user's chosen agent CLI. OpenAlice plumbs two MCP servers (global + workspace-scoped) into `.mcp.json`, giving the agent full tool access with native prompt cache and rendering
- **Inbox push channel** — Agents inside a workspace call `inbox_push` to surface documents (rendered live from workspace files) plus markdown commentary. Users read in a dedicated Inbox tab and click to jump back into the workspace session
- **Multi-provider AI** — Claude (Agent SDK with OAuth or API key) or Vercel AI SDK (Anthropic, OpenAI, Google), switchable at runtime without restart
- **Scheduling layer** — Typed append-only event log + cron engine with heartbeat patterns (periodic timer with active-hours filtering and dedup window) and planned webhook support
- **Templates & satellite repos** — Workspace templates bootstrap new capabilities (research toolkit, backtest harness) from satellite repos, keeping the main codebase small and ecosystem contributions uncoupled
- **Evolution mode** — Optional permission escalation giving Alice full project access including Bash, enabling self-modification

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Single AI agent with domain-specific tool surfaces (Trading, Market Data, Analysis, News) operating inside workspace-resident CLI sessions. Multiple UTAs act like independent repositories |
| **Coordination mechanism** | Built-in orchestration for trading workflows (UTA lifecycle, Guard pipeline, workspace scheduling). MCP-based tool exposure for external integration. Global ToolCenter registers domain tools; WorkspaceToolCenter holds per-workspace factories. AgentCenter + ProviderRouter route AI calls to the active backend |
| **Human oversight** | Explicit approval before trade execution; guard pipeline enforces automated safety limits; users can intervene in any workspace session or via Inbox replies |
| **Multi-agent protocol** | **No built-in multi-agent** — OpenAlice is a single-agent system. MCP server exposes its tools to external agents/orchestrators; internal execution routes through workspace CLI sessions with `.mcp.json` plumbing |

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | Local filesystem — all state (config, workspaces, credentials, logs) lives on disk under `~/.openalice/`. Docker mode uses a named volume (`openalice-data`) |
| **Data portability** | **High** — workspaces are git repos; config is JSON with Zod validation; trading history is versioned per UTA. No external SaaS dependency for core operation |
| **Offline capability** | Partial — local scheduling and workspace execution work offline, but LLM API calls and broker connections require internet |
| **Vendor lock-in risk** | **Low** — open source (AGPL-3.0), self-hosted by design, multi-provider AI support, broker-agnostic UTA abstraction |

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source / self-hosted | $0 | Self-build and self-host; bring your own broker accounts and AI provider credentials |

## Ecosystem & Integrations

- **Brokers**: CCXT (multi-exchange), Alpaca (US equities), Interactive Brokers, Longbridge, Bybit
- **AI providers**: Claude Code (Agent SDK, OAuth), Anthropic API, OpenAI, Google (via Vercel AI SDK)
- **Market data**: TypeScript-native OpenBB engine with unified cross-asset symbol search and technical indicators
- **News**: Background RSS collection with archive search
- **Connectors**: Web UI (chat, portfolio dashboards), Telegram bot, MCP Ask
- **Deployment**: Source (`pnpm dev`), Docker Compose (bundles `claude` and `codex` CLIs), upcoming macOS DMG and Windows installer
- **Community**: Discord (English), QQ group (中文); DeepWiki for codebase Q&A

## Screenshots / Demo

- [OpenAlice GitHub repository — README with architecture diagram and quickstart](https://github.com/TraderAlice/OpenAlice)
- [Monad Rebel in Paradise AI Hackathon — OpenAlice Grand Prize announcement](https://m.theblockbeats.info/en/news/61702)

## References

- [OpenAlice GitHub repository](https://github.com/TraderAlice/OpenAlice)
- [Monad Rebel in Paradise AI Hackathon — 11 winning projects overview](https://m.theblockbeats.info/en/news/61702)
- [TechFlowPost — Kimi, Zhipu, and Doubao at Monad hackathon](https://m.techflowpost.com/en-US/article/30844)
- [AInvest — Monad hosts AI hackathon to advance on-chain AI integration](https://www.ainvest.com/news/monad-hosts-ai-hackathon-advance-chain-ai-integration-2603/)
