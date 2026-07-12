# Herdr

> Rust-native terminal agent multiplexer: run, detach, reattach, and watch many AI coding agents from one keyboard-and-mouse TUI.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [herdr.dev](https://herdr.dev) |
| **Repository** | [github.com/ogulcancelik/herdr](https://github.com/ogulcancelik/herdr) |
| **Status** | `Active` — ~15,555 GitHub stars; latest release v0.7.3 (2026-07-07) |
| **Openness** | `Open source (AGPL-3.0-or-later)` — commercial licenses also available |
| **Deployment** | `Local-first` — single Rust binary; sessions persist and reattach over SSH |
| **First release** | 2026-03 |
| **Last release / commit** | 2026-07-07 (v0.7.3) |
| **Language / Stack** | Rust — single binary, no Electron |
| **License** | AGPL-3.0-or-later (open source); commercial licensing available |

## What It Does

Herdr is a terminal-native agent multiplexer. It wraps multiple AI coding agents (and ordinary terminal sessions) in a single text user interface so a developer can see every agent's state at a glance, detach from a running session, and reattach later — even from another machine over SSH. Agents can also drive Herdr themselves through a pure socket API, turning the terminal into a persistent, observable workspace for both humans and autonomous tools.

## Key Mechanisms

- **Every agent at a glance** — A terminal UI shows blocked, working, and done states with live terminal views for each session.
- **Detach and reattach** — Sessions survive local restarts and can be reattached over SSH, similar to a terminal multiplexer for agent work.
- **Socket API for agents** — Agents can interact with Herdr through a pure socket API, enabling automation and orchestration without a graphical interface.
- **Keyboard + mouse control** — Navigate and manage sessions with both keyboard shortcuts and mouse input.
- **Plugins / marketplace** — Extensible plugin system for adding capabilities and sharing extensions.
- **Single Rust binary** — Distributed as one self-contained binary; no Electron or heavy runtime dependencies.

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Multi-agent peer — multiple terminal/agent sessions run side by side in one TUI; agents can also control Herdr via the socket API |
| **Coordination mechanism** | Terminal multiplexer-style sessions with persistent state and a socket API; humans observe state visually while agents can read/write via sockets |
| **Human oversight** | Human stays in the terminal loop: live views, keyboard/mouse control, attach/detach, and direct session management |

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | Local terminal sessions and persisted session state on the user's machine or self-hosted server |
| **Data portability** | **High** — open source (AGPL-3.0-or-later); sessions are local terminal state under user control |
| **Offline capability** | Full for local use; SSH reattach enables remote access without requiring a cloud coordination service |
| **Vendor lock-in risk** | **Low** — open source, single self-contained binary, local session persistence, and no required cloud backend |

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source / self-hosted | $0 | AGPL-3.0-or-later; bring your own LLM/API keys and agent runtimes |
| Commercial license | Contact | Available for organizations that need a non-AGPL license |

## Ecosystem & Integrations

- **Install methods**: `curl -fsSL https://herdr.dev/install.sh | sh`, `brew install herdr`, and other package managers listed on the site
- **Agent runtimes**: Works with Claude Code, Codex, and other terminal-based coding agents via multiplexed terminal sessions
- **API / extensibility**: Pure socket API for agent-driven control; plugin marketplace
- **Deployment**: Local terminal / self-hosted; sessions persist and reattach over SSH
- **Docs**: [herdr.dev/docs/](https://herdr.dev/docs/)
- **Community**: GitHub Issues at [ogulcancelik/herdr](https://github.com/ogulcancelik/herdr/issues)

## Screenshots / Demo

- [Homepage](https://herdr.dev)
- [GitHub repository README](https://github.com/ogulcancelik/herdr)
- [Documentation](https://herdr.dev/docs/)

## References

- [ogulcancelik/herdr on GitHub](https://github.com/ogulcancelik/herdr)
- [Herdr releases](https://github.com/ogulcancelik/herdr/releases)
- [Herdr documentation](https://herdr.dev/docs/)
- [Herdr homepage](https://herdr.dev)
