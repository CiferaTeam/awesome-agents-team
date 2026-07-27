# botmux

> Bridge Feishu/Lark to AI coding CLIs — each DM, group, or topic spawns its own live-streaming CLI session.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [deepcoldy.github.io/botmux](https://deepcoldy.github.io/botmux/) |
| **Repository** | [github.com/deepcoldy/botmux](https://github.com/deepcoldy/botmux) |
| **Status** | `Active` — 794 GitHub stars, 143 forks; latest release v3.5.2 (2026-07-26) |
| **Openness** | `Open source (MIT)` |
| **Deployment** | `Self-hosted` — Node.js daemon that connects a Feishu/Lark bot to local CLI runtimes |
| **First release** | 2026-03 |
| **Last release / commit** | 2026-07-26 (v3.5.2) |
| **Language / Stack** | TypeScript (Node.js ≥22), pnpm, pm2; node-pty, tmux, React dashboard |
| **License** | MIT |

## What It Does

botmux runs a daemon that listens to Feishu/Lark messages and spawns an isolated AI coding CLI process for every new conversation. Output is streamed back as live-updating Feishu cards and an interactive web terminal, so a team can control Claude Code, Codex, Gemini, OpenCode, and 20+ other CLI agents from chat — including from mobile — without replacing the agents' native runtimes.

## Key Mechanisms

- **One conversation, one CLI process**: Each DM, group mention, or topic gets its own node-pty/tmux session, preserving the CLI's native memory, hooks, plan mode, MCP tools, and `/` commands.
- **Live-streaming Feishu cards**: Every turn produces a card that mirrors the terminal output, with controls to show/hide output, scroll, restart, close, or take over the session.
- **Multi-bot @mention routing**: Multiple bots backed by different CLIs can coexist in the same group; @mention routes the request to the chosen agent.
- **Interactive web terminal**: A browser or mobile terminal attaches to the underlying process, with shortcuts for Esc, Ctrl+C, and arrow keys.
- **Session adopt and relay**: A running local tmux session can be adopted from a phone with `/adopt`, and `/relay` moves an entire session — process and memory intact — to another chat.
- **Scheduled tasks and webhooks**: Natural-language cron jobs, external webhook triggers, and API-driven task dispatch.

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Multi-agent peer (one process per conversation/bot) + human-in-loop |
| **Coordination mechanism** | Feishu/Lark events → daemon router → CLI adapter; output streams back to chat cards and web terminal |
| **Human oversight** | Humans trigger agents via DMs/groups, watch live cards, interrupt sessions, adopt via web terminal, and configure allowlists and sandboxing |

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | Local filesystem for workspaces, tmux pane state, and `bots.json` / `.env` configuration; Feishu/Lark messages are transient |
| **Data portability** | **High** — agent workspaces and config are plain local files; source is open (MIT) |
| **Offline capability** | **Partial** — the daemon and CLI run locally, but messaging requires Feishu/Lark connectivity and (for webhook mode) public ingress |
| **Vendor lock-in risk** | **Low–Medium** — adapters are open and CLI runtimes are swappable, but messaging is currently tied to Feishu/Lark |

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source / self-hosted | $0 | Self-host the Node.js daemon; bring your own Feishu/Lark app credentials, LLM API keys, and CLI runtimes |

## Ecosystem & Integrations

- **Platform**: Feishu / Lark; Node.js ≥22; pnpm 9.5; pm2 process management
- **Agent runtimes**: 20+ adapters including Claude Code, Codex, Gemini, OpenCode, Cursor, antigravity, Copilot, Grok, Kimi, Kiro, Aiden, COCO (TRAE), Hermes, Mira, riff (cloud), and others ([registry.ts](https://github.com/deepcoldy/botmux/blob/master/src/adapters/cli/registry.ts))
- **API / extensibility**: `bots.json` adapter configuration, webhook triggers, API task triggers, scheduled jobs, and role profiles
- **Distribution**: npm [`botmux`](https://www.npmjs.com/package/botmux)
- **Community**: GitHub Issues at [deepcoldy/botmux](https://github.com/deepcoldy/botmux/issues)

## Screenshots / Demo

- [Documentation site](https://deepcoldy.github.io/botmux/)
- [Effect showcase (Lark wiki)](https://bytedance.larkoffice.com/wiki/UBOXwH01CixfxfkqxUpcKgvQnsg)
- [Repository README](https://github.com/deepcoldy/botmux)

## References

- [deepcoldy/botmux on GitHub](https://github.com/deepcoldy/botmux)
- [Official documentation](https://deepcoldy.github.io/botmux/)
- [npm: botmux](https://www.npmjs.com/package/botmux)
- [Feishu/Lark showcase wiki](https://bytedance.larkoffice.com/wiki/UBOXwH01CixfxfkqxUpcKgvQnsg)
