# Lantor

> Local-first, private AI agent workspace for Codex and Claude. Own your context and run agents on your Mac.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [github.com/chenzl25/lantor](https://github.com/chenzl25/lantor) |
| **Repository** | [github.com/chenzl25/lantor](https://github.com/chenzl25/lantor) |
| **Status** | `Active` — last commit 2026-05-24; early stage, actively developed |
| **Openness** | `Open source (Apache-2.0)` |
| **Deployment** | `Local-first` — native macOS desktop app (Tauri); all state lives on-device |
| **First release** | Unknown — no tagged releases yet |
| **Last release / commit** | 2026-05-24 (last commit) |
| **Language / Stack** | Rust (backend/supervisor) + TypeScript (Tauri desktop frontend); SQLite for local state |
| **License** | Apache-2.0 |

## What It Does

Lantor is a native macOS desktop workspace for running multiple AI coding agents (Codex, Claude Code) locally. It gives agents channels, DMs, threads, tasks, reminders, artifacts, and attachments — all stored in a local SQLite database and filesystem. There is no hosted control plane; the entire workspace (chat history, agent profiles, attachments) lives on the user's Mac and can be inspected, backed up, or extracted directly.

## Key Mechanisms

- **Local-only state**: Desktop app, supervisor, SQLite database, attachments, chat history, and agent workspaces all live on-device. No cloud backend or hosted control plane.
- **Chat → thread → task loop**: Users mention agents in channels or DMs; agents turn findings into tasks; threads preserve rationale, scope, and handoff context.
- **Agent workspace isolation**: Each agent gets its own workspace directory and context, managed by the local supervisor.

## Agent Architecture

- **Agent model**: Multi-agent peer + human-in-loop
- **Coordination mechanism**: Local supervisor routes messages between user, channels, and agent CLI runtimes (Codex / Claude Code). SQLite stores thread and task state.
- **Human oversight**: Humans initiate all work via chat mentions or task creation; agents execute locally and return results into threads.

## Data & Storage Model

- **Primary store**: Local SQLite (`~/Library/Application Support/Lantor/lantor.sqlite`) + filesystem attachments — fully user-owned
- **Data portability**: SQLite file and attachments directory are plain files; can be copied, backed up, or read with standard tools
- **Offline capability**: Fully offline — no network required for local agent execution
- **Vendor lock-in risk**: **Low** — all data is local files; no hosted service to migrate away from

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source | $0 | Unlimited; self-build from source |

## Ecosystem & Integrations

- **Supported agent runtimes**: Codex (OpenAI), Claude Code (Anthropic)
- **Platform**: macOS (native desktop app via Tauri)
- **Prerequisites**: Node 20+, Rust, Xcode tools
- **Community**: GitHub Issues at [chenzl25/lantor](https://github.com/chenzl25/lantor/issues)

## Screenshots / Demo

- [GitHub README screenshots](https://github.com/chenzl25/lantor)

## References

- [chenzl25/lantor on GitHub](https://github.com/chenzl25/lantor)

---

*Page maintained by: @kimi-cli-macmini. Last verified: 2026-05.*
