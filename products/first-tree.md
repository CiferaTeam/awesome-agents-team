# First-Tree

> Context-grounded agentic work for teams — agents work from your team's shared Context Tree, not isolated prompts.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [first-tree.ai](https://first-tree.ai/) |
| **Repository** | [github.com/agent-team-foundation/first-tree](https://github.com/agent-team-foundation/first-tree) |
| **Status** | `Active` — 103 GitHub stars, 28 forks; latest release v0.5.18 (2026-07-30) |
| **Openness** | `Open source (Apache-2.0)` |
| **Deployment** | `Self-hosted` — CLI + daemon sign local computers in; web workspace, server, and Postgres can run on your own infra or use hosted first-tree.ai |
| **First release** | 2026-03 |
| **Last release / commit** | 2026-07-30 (v0.5.18) |
| **Language / Stack** | TypeScript (pnpm monorepo: Fastify server, React web, CLI, Agent SDK) |
| **License** | Apache 2.0 |

## What It Does

First-Tree is an open-source workspace where AI agents work from a team's shared context instead of isolated prompts. At its center is the **Context Tree** — a Git-native team memory of decisions, ownership, repos, responsibilities, constraints, and prior work. Agents read it before working; useful outcomes flow back into it after work completes. The loop: *user intent → read team context → context-aware agent work → human review/control → durable outcome → updated team context*.

## Key Mechanisms

- **Context Tree**: A Git-native team memory layer for decisions, ownership, responsibilities, and constraints. Agents read it before starting; outcomes update it after finishing.
- **Persistent work streams**: Focused copilot work (deep collaboration in a persistent chat) or parallel review work (agents advance tasks and pull humans in only for decisions, blockers, approvals).
- **Web workspace**: Daily surface for chats, agents, team members, computers, GitHub, and context-backed work — active work, blocked states, and human review points stay visible.
- **CLI + daemon**: Signs a computer in and keeps local agents connected; bundled Node runtime in the macOS/Linux installer.
- **GitHub integration**: Connects code work, pull requests, and review back to the workspace; agents can report on issues with linked context in view.

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Multi-agent with human-in-loop — works with Claude Code and Codex agent runtimes |
| **Coordination mechanism** | Context Tree as shared Git-native state; server routes messages between agents, humans, and GitHub |
| **Human oversight** | Humans approve at decision/blocker/approval points; active work and review stages stay visible in the workspace |

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | Git-native Context Tree + Postgres (server); workspaces, client.yaml on the local machine |
| **Data portability** | **High** — context is Git-versioned and open (Apache-2.0); self-host keeps all data on your infra |
| **Offline capability** | **Partial** — CLI + daemon run locally, but the workspace and agent routing need the server (self-hosted or hosted) |
| **Vendor lock-in risk** | **Low–Medium** — self-hostable and open source, but the server (Fastify + Postgres) is the coordination hub |

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source / self-hosted | $0 | Self-host the server + web workspace; bring your own CLI runtimes and LLM access |
| Hosted (first-tree.ai) | Free tier / paid | Hosted production; guided setup connects computers via install script |

## Ecosystem & Integrations

- **Agent runtimes**: Claude Code, Codex (via Agent SDK `@first-tree/client`); MCP support
- **External services**: GitHub (issues, PRs, review), team members, computers
- **API / extensibility**: `first-tree` CLI (`login`, `agent`, `chat`, `org`, `daemon`, `config`, `tree`, ...), Zod-schema shared package, skill payloads in `skills/`
- **Distribution**: npm [`first-tree`](https://www.npmjs.com/package/first-tree)
- **Community**: GitHub Discussions at [agent-team-foundation/first-tree](https://github.com/agent-team-foundation/first-tree/discussions)

## Screenshots / Demo

- [Documentation / Quickstart](https://github.com/agent-team-foundation/first-tree/blob/main/docs/quickstart.md)
- [Repository README](https://github.com/agent-team-foundation/first-tree)

## References

- [agent-team-foundation/first-tree on GitHub](https://github.com/agent-team-foundation/first-tree)
- [Official documentation](https://github.com/agent-team-foundation/first-tree/tree/main/docs)
- [npm: first-tree](https://www.npmjs.com/package/first-tree)
