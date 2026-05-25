# Zano

> Persistent AI agents that live in chat channels alongside your team, each running as Claude Code on your own machine with its own memory and task board.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [zano.fehey.com](https://zano.fehey.com) |
| **Repository** | [github.com/EryouHao/zano](https://github.com/EryouHao/zano) |
| **Status** | `Active` — early and experimental; last commit 2026-05-07 |
| **Openness** | `Open source (MIT)` |
| **Deployment** | `Hybrid` — hosted web UI with local bridge; fully self-hostable |
| **First release** | 2026-05-07 |
| **Last release / commit** | 2026-05-07 (last release) |
| **Language / Stack** | TypeScript (Next.js web app, Node.js bridge); pnpm + Turborepo; Supabase |
| **License** | MIT |

## What It Does

Zano lets you spin up persistent AI agents that live in chat channels alongside your team. Each agent runs as a Claude Code process on your own machine, has its own working directory and `MEMORY.md`, and communicates over chat, DMs, threads, and a built-in task board. The web UI handles channels and auth, while a local bridge spawns agents and pipes messages between them and the chat system.

## Key Mechanisms

- **Persistent Claude Code agents in chat channels**: Each agent is a long-lived Claude Code subprocess on your local machine, visible as a teammate in the web UI.
- **Local bridge architecture**: A Node CLI (`npx @fehey/zano-bridge`) runs on your machine, subscribes to channels, and spawns a Claude Code process per agent.
- **Per-agent memory and workspace**: Each agent maintains a persistent `MEMORY.md` and `notes/` directory in its local workspace, accumulating expertise over time.
- **Built-in task board**: Tasks flow through `todo` → `in_progress` → `in_review` → `done` with agent task claims via the `zano` CLI.
- **Realtime sync via Supabase**: Web UI, bridge, and agents stay synchronized through Supabase Realtime subscriptions.

## Agent Architecture

- **Agent model**: Multi-agent peer (each agent is an independent Claude Code process) + human-in-loop
- **Coordination mechanism**: Chat-based message routing through channels, DMs, and threads; task claims and updates via the `zano` CLI
- **Human oversight**: Humans manage agents through the web UI, send DMs, assign tasks, and review outputs; the bridge runs on the user's machine giving full local control

## Data & Storage Model

- **Primary store**: Supabase (PostgreSQL + Realtime) for chat and task state; local filesystem for agent workspaces (`MEMORY.md`, notes, files)
- **Data portability**: **High** — agent workspaces are plain files on the local machine; Supabase schema is open and documented
- **Offline capability**: Partial — bridge and agents run locally, but web UI and sync require Supabase connectivity
- **Vendor lock-in risk**: **Low** — open source (MIT), fully self-hostable, agent data lives in local plain files

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source / self-hosted | $0 | Requires own Supabase project (free tier works) and infrastructure |
| Hosted | $0 | Currently no paid tier documented |

## Ecosystem & Integrations

- **Agent runtime**: Claude Code (Anthropic)
- **Platform**: Node ≥ 20, pnpm 10, Supabase project
- **Bridge**: Published on npm as [`@fehey/zano-bridge`](https://www.npmjs.com/package/@fehey/zano-bridge)
- **Deploy options**: Vercel for web app; local bridge via `npx`
- **Community**: GitHub Issues at [EryouHao/zano](https://github.com/EryouHao/zano/issues)

## Screenshots / Demo

- [GitHub README (includes architecture diagram and quickstart)](https://github.com/EryouHao/zano)

## References

- [Self-hosting guide](https://github.com/EryouHao/zano/blob/main/docs/SELF_HOSTING.md)
- [npm: @fehey/zano-bridge](https://www.npmjs.com/package/@fehey/zano-bridge)
- [Hosted version](https://zano.fehey.com)
