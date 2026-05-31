# OpenHanako

> Free, open-source personal AI agent desktop app with memory, personality, and multi-agent collaboration. Designed for non-coders with a full GUI.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [github.com/liliMozi/openhanako](https://github.com/liliMozi/openhanako) |
| **Repository** | [github.com/liliMozi/openhanako](https://github.com/liliMozi/openhanako) |
| **Status** | `Active` — 4,271 GitHub stars; latest release v0.252.2 |
| **Openness** | `Open source (Apache-2.0)` |
| **Deployment** | `Local-first` — Electron desktop app for macOS, Windows, Linux; optional LAN/WebUI server mode |
| **First release** | 2026-04-29 |
| **Last release / commit** | 2026-05-30 (v0.252.2) |
| **Language / Stack** | JavaScript, TypeScript, Electron 38, React 19, Vite 7, Hono, better-sqlite3 |
| **License** | Apache-2.0 |

## What It Does

OpenHanako (branded as HanaAgent) is a personal AI agent desktop application designed to bridge the gap between everyday computer users and powerful AI agent capabilities. Unlike CLI-first coding agents, it provides a full graphical interface where users can create multiple agents with distinct memories and personalities, operate their computer, browse the web, read/write files, execute code, and manage schedules — all through natural conversation. Multiple agents can collaborate via channel group chats or task delegation.

## Key Mechanisms

- **Persistent memory system** — Combines mainstream memory approaches with custom enhancements; agents remember past conversations and context across sessions
- **Personality engine** — Agents are shaped by personality templates and custom profile files; each agent has unique speech patterns and behavioral logic. Agents are self-contained folders, easy to back up and migrate
- **Desk workspace** — Each agent has a personal desk for files and notes ("笺"); agents actively read desk contents and execute tasks. Supports drag-and-drop, file preview, and workspace file-tree change monitoring
- **Multi-agent collaboration** — Create multiple agents with independent memories, personalities, and scheduled tasks. Agents communicate via channel group chats or delegate tasks to each other
- **SKILLS ecosystem** — Built-in compatibility with community SKILLS; agents can auto-install skills from GitHub or write new ones. Strict skill audit enabled by default
- **Role cards & skill bundles** — Agents export/import as local-first role-card zips (personality, avatar, optional memory, skills). Skill bundles can be grouped, dragged, batch-enabled, and exported as standalone zips
- **Scheduled tasks & heartbeat** — Cron-based automation plus periodic desk file change monitoring. Lightweight reminders and plugin actions can be scheduled independently of agent execution
- **Security sandbox** — Dual-layer isolation: app-level PathGuard (4-tier access control) + OS-level sandbox (macOS Seatbelt / Linux Bubblewrap / Windows restricted token). Read-only system access by default; write/delete restricted to work and data directories
- **Plugin system** — Convention-over-configuration plugin architecture. Plugins can contribute tools, skills, commands, agent templates, HTTP routes, event hooks, LLM providers, pages, sidebar widgets, config schemas, and background tasks. Two-tier permission model (restricted / full-access)
- **Multi-platform bridge** — Single agent can simultaneously connect to Telegram, Feishu, QQ, and WeChat bots for remote computer operation. Bridge messages carry platform context; notifications route back to the originating platform
- **Mobile PWA & LAN frontend** — HanaAgent Server hosts a `/mobile/` PWA for phone access via device access key or local account. Desktop clients can also connect via LAN URL + access key
- **Full-screen media viewer** — Dark-overlay preview for images, SVG, and videos with zoom, pan, keyboard shortcuts, and adjacent-media navigation

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Multi-agent peer — each agent has independent memory, personality, and scheduled tasks. Agents collaborate via channels or task delegation |
| **Coordination mechanism** | Hub-based event bus for background tasks, channel routing, agent-to-agent communication, and DM routing. Session-layer facade coordinates Manager services (Agent, Session, Model, Skill, Channel, Bridge, Plugin) |
| **Human oversight** | Security sandbox with configurable PathGuard levels; humans approve skill installations, set sandbox permissions, and control model/provider access via setup wizard |

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | Local better-sqlite3 database (WAL mode); all data stored locally under `~/.hanako`. Nothing uploaded to external servers by default |
| **Data portability** | **High** — agents exportable as role-card zips; skill bundles exportable as standalone zips. All files local-first |
| **Offline capability** | Partial — local agent execution and scheduled tasks work offline; LLM API calls require internet unless using Ollama/LM Studio locally |
| **Vendor lock-in risk** | **Low** — open source (Apache-2.0), supports OpenAI-compatible, Anthropic, OAuth, and Ollama local models |

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source / self-hosted | $0 | Free desktop app; bring your own API keys |

## Ecosystem & Integrations

- **AI platforms**: OpenAI-compatible, Anthropic, OAuth providers, Ollama, LM Studio and other local models
- **Chat platforms**: Telegram, Feishu (Lark), DingTalk, WeChat, WeCom, QQ
- **Protocols**: Custom agent communication via Hub event bus; plugin-based extensibility
- **Skills**: Built-in + community SKILLS from GitHub + custom skills written by agents
- **Platform support**: macOS (Apple Silicon / Intel, signed & notarized), Windows (Beta), Linux (AppImage / deb)
- **Languages**: Chinese, English, Japanese, Korean, Traditional Chinese
- **Install**: macOS (download `.dmg`), Windows (download `.exe`), Linux (download `.AppImage` or `.deb`)

## Screenshots / Demo

- [OpenHanako GitHub repository — README with features and quickstart](https://github.com/liliMozi/openhanako)
- [Latest releases](https://github.com/liliMozi/openhanako/releases)

## References

- [OpenHanako GitHub repository](https://github.com/liliMozi/openhanako)
- [Plugin development guide](https://github.com/liliMozi/openhanako/blob/main/PLUGINS.md)
- [Security policy](https://github.com/liliMozi/openhanako/blob/main/SECURITY.md)
