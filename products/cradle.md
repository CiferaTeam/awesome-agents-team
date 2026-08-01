# Cradle

> Desktop multi-agent orchestration command center — coordinate Claude Code, Codex, and other agent runtimes across parallel worktrees with kanban delegation and a plugin-based tool marketplace.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [cradle.wibus.ren](https://cradle.wibus.ren/) |
| **Repository** | [github.com/wibus-wee/cradle-app](https://github.com/wibus-wee/cradle-app) |
| **Status** | `Active` — 47 GitHub stars, last commit 2026-08-01 (within 24h of this entry); project self-describes as "early stages of development" |
| **Openness** | `Unknown` — repository is publicly readable on GitHub but no LICENSE file is present in the tree (verified 2026-08-01) |
| **Deployment** | `Local-first` — Electron desktop app + bundled Node runtime; companion server, web workspace, and relay daemon are optional and can run locally or on user infra |
| **First release** | Unknown — repository created 2026 (no tagged release yet) |
| **Last release / commit** | 2026-08-01 (commit `85b5f80` "fix(github): reject duplicate PR body sections (#109)") |
| **Language / Stack** | TypeScript (pnpm monorepo: Fastify server, React web, Electron desktop, CLI) + Rust (`chronicle` observability crate) |
| **License** | Unknown — no LICENSE/COPYING file in the repository root |

## What It Does

Cradle is a desktop-first control plane for running multiple AI agents in parallel. The blog post `multi-agent-orchestration` (2026-07-06) states the thesis directly: *"Run four agents on the same codebase. At the same time."* Each agent is an independent worker with its own kanban card, its own live status, and its own worktree — agents don't trip over each other because session-level worktree isolation keeps every task in its own working tree with automatic cleanup policies.

The orchestrator view replaces chat windows: kanban shows column/state for every task, session states (running / waiting / blocked) are unified, and any surface (Chat, Workspace, Diffs, Kanban) can be torn off into a standalone window. Beyond a single machine, relay pairing strings enroll remote machines (desktop at home, build machine at the office, long-running cloud instance) into the local controller as additional execution environments.

## Key Mechanisms

- **Multi-agent parallel workers**: each agent runs independently with its own task, kanban card, and live status; "you can run four Claude Codes at once, or assign different jobs to different runtimes."
- **Worktree isolation**: every task lives in its own working tree; cleanup policies reclaim them automatically based on max count / max disk usage.
- **Coordination layer**: Issues, Kanban, **agent delegation**, scheduled automation, background artifacts, session awaits, and workflow rules — agents hand off to humans only at decision/blocker/approval points.
- **Plugin marketplace** (`marketplace.json`): seven bundled plugins — `browser-use` (browser automation MCP server), `cc-switch` (provider/credential rotation), `codex-plus-plus` (Codex integration), `github-issues`, `nowledge-mem` (memory layer), `slack-conversation-bridge`, `system-info`.
- **Distributed execution via relay**: `relayd` daemon enrolls remote machines via pairing strings; LAN-only / public inbound modes and public URL configuration supported.
- **Runtime pooling**: OpenCode moved from one-process-per-session to a single shared server, warmed once at boot and reused across every session — pooling runtimes per workspace avoids repeated startup costs.
- **Observability**: `chronicle` (Rust crate) records agent activity locally for cost analytics, search, and audit; `observability/` directory ships Docker Compose for traces.
- **Session Await**: persistent sessions pause for external events (CI pipelines, human approval) and resume without losing context.

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Multi-agent with agent delegation and human-in-loop; supports Claude Code, Codex, Kimi, OpenCode, Cursor, Grok, and other provider runtimes via the Agent SDK |
| **Coordination mechanism** | Server routes messages between agents, humans, and GitHub; shared workspace state, kanban, and worktrees; plugin marketplace for tool integration |
| **Human oversight** | Humans approve at decision/blocker/approval points; active work and review stages stay visible in the workspace; agents pull humans in only when rules say so |

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | Local SQLite / filesystem (workspace, client config, sessions) + optional Postgres for self-hosted server + plugin-specific storage |
| **Data portability** | **Medium** — desktop data is local; self-hosted infra keeps all data on user infra; server protocol and database schema are open in the source tree |
| **Offline capability** | **High** — desktop CLI + daemon run locally; the web workspace and agent routing require the server (self-hosted or hosted at cradle.wibus.ren) |
| **Vendor lock-in risk** | **Low–Medium** — desktop is open code; server is open code and self-hostable; plugin marketplace is project-controlled |

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source / self-hosted | $0 | Self-host server + desktop + CLI; bring your own agent runtimes and LLM access |
| Hosted (cradle.wibus.ren) | Free tier / paid | Hosted workspace; guided setup connects machines via install script |

## Ecosystem & Integrations

- **Agent runtimes**: Claude Code, Codex (Kimi, OpenCode, Cursor, Grok providers in QA cases)
- **External services**: GitHub (issues, PRs, review), Slack bridge, browser automation
- **API / extensibility**: plugin marketplace (`marketplace.json`), MCP server support (`add-mcp` CLI command), `chronicle` event recorder
- **Distribution**: macOS / Windows / Linux installers; web workspace at [cradle.wibus.ren](https://cradle.wibus.ren/)
- **Community**: GitHub Issues and PRs at [wibus-wee/cradle-app](https://github.com/wibus-wee/cradle-app)

## Screenshots / Demo

- [Multi-agent orchestration blog post](https://github.com/wibus-wee/cradle-app/blob/main/apps/landing/blog/multi-agent-orchestration.en.md)
- [Repository README](https://github.com/wibus-wee/cradle-app)

## References

- [wibus-wee/cradle-app on GitHub](https://github.com/wibus-wee/cradle-app)
- [Multi-agent orchestration blog (English)](https://github.com/wibus-wee/cradle-app/blob/main/apps/landing/blog/multi-agent-orchestration.en.md)
- [Plugin marketplace source](https://github.com/wibus-wee/cradle-app/blob/main/marketplace.json)