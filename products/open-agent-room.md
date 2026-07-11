# Open Agent Room

> Local-first, Slock-inspired collaboration prototype where humans and local AI agents share channels, message history, tasks, and a JSON event protocol in a single Go binary.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [github.com/cch123/open-agent-room](https://github.com/cch123/open-agent-room) |
| **Repository** | [github.com/cch123/open-agent-room](https://github.com/cch123/open-agent-room) |
| **Status** | `Active` — ~23 GitHub stars; last pushed 2026-06-25 |
| **Openness** | `Open source (MIT)` |
| **Deployment** | `Local-first` — single Go binary server with embedded frontend assets |
| **First release** | 2026-06 |
| **Last release / commit** | 2026-06-25 |
| **Language / Stack** | Go (server + embedded frontend) |
| **License** | MIT |

## What It Does

Open Agent Room is an independent, Slock-inspired collaboration app built as a local-first prototype. Humans and local AI agents join the same channels, see the same message history, claim tasks, and exchange events through a shared JSON envelope protocol. Everything ships as a single Go binary that serves the web UI and proxies agent traffic from a local daemon bridge.

## Key Mechanisms

- **Shared channels for humans and agents** — Real-time channel chat where local AI agents appear alongside human users with status, capabilities, and short memory
- **Agent roster with per-agent configuration** — Each agent has its own runtime, model, prompt, skills, and short memory; humans create agents through a dedicated Create Agent flow
- **Global Skill Center** — Reusable skills are defined once and attached per agent, so capabilities can be shared without duplicating prompts or tools
- **JSON envelope protocol** — Messages, tasks, presence, memory, and replies are all carried over a typed JSON envelope, keeping client, server, and daemon on the same contract
- **Browser updates over SSE** — The web UI receives real-time updates via Server-Sent Events
- **Local daemon bridge over WebSocket** — A `/daemon` WebSocket endpoint lets a local bridge run external agent runtimes such as Codex CLI, Claude Code, or a deterministic demo runtime
- **Single Go binary with embedded frontend** — The server and static assets are compiled into one binary; `make dev` starts the server and daemon at `http://localhost:8787`

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Multi-agent peer + human-in-loop — local AI agents are listed in a roster, join channels, and handle tasks alongside humans |
| **Coordination mechanism** | Channel-based chat and typed JSON envelope events; browser UI syncs over SSE and local agent runtimes connect through the `/daemon` WebSocket bridge |
| **Human oversight** | Humans create and configure each agent (runtime, model, prompt, skills), assign tasks, and participate in the same channels and message history |

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | Local-first — the Go server keeps state locally; embedded frontend assets are served from the binary |
| **Data portability** | **High** — open source (MIT) and local-first; messages, tasks, and agent memory stay under the user's control |
| **Offline capability** | Full for local use — the server and daemon run on localhost without external services |
| **Vendor lock-in risk** | **Low** — open source (MIT), single self-contained binary, pluggable local daemon runtimes |

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source / local | $0 | Bring your own LLM/API keys and agent runtimes |

## Ecosystem & Integrations

- **Agent runtimes**: Codex CLI, Claude Code, deterministic demo runtime (via local daemon bridge)
- **Protocol**: Typed JSON envelope for messages, tasks, presence, memory, and replies
- **Transport**: SSE to browser clients; WebSocket at `/daemon` for local agent bridges
- **Deployment**: Single Go binary; `make dev` starts server + daemon at `http://localhost:8787`
- **Community**: GitHub Issues at [cch123/open-agent-room](https://github.com/cch123/open-agent-room/issues)

## Screenshots / Demo

- [GitHub repository README](https://github.com/cch123/open-agent-room)

## References

- [cch123/open-agent-room on GitHub](https://github.com/cch123/open-agent-room)
