# Orca

> AI Development Environment for working with a fleet of parallel coding agents — run Codex, Claude Code, OpenCode, Pi (and ~30 other CLI agents) side-by-side, each in its own worktree, and fan a single prompt out across them to compare and merge.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [onorca.dev](https://www.onorca.dev/) |
| **Repository** | [github.com/stablyai/orca](https://github.com/stablyai/orca) |
| **Status** | `Active` — 42820 GitHub stars, 2984 forks; latest release v1.4.180 (2026-08-11); last push 2026-08-12 (within 24h of this entry); README describes the project as "ships daily" |
| **Openness** | `Open source (MIT)` — MIT License (Copyright (c) 2026 Lovecast Inc.); OSI-approved |
| **Deployment** | `Local-first` — desktop app (macOS, Windows, Linux) + mobile companion (iOS App Store, TestFlight, Android APK 0.0.42) + SSH Worktrees for agents on remote boxes + headless Linux server mode |
| **First release** | 2026 — pre-v1.0 lineage on GitHub Releases; project self-describes as daily-ship |
| **Last release / commit** | Last release 2026-08-11 (v1.4.180); last commit `444638d9` (2026-08-12) |
| **Language / Stack** | TypeScript + Node.js (desktop app), Swift/Kotlin/Ruby (per-platform shells), Ghostty-class WebGL terminal; CLI in `orca` binary; mobile in native iOS/Android |
| **License** | MIT (Copyright (c) 2026 Lovecast Inc.) |

## What It Does

Orca is the **ADE (Agent Development Environment)** for working with a fleet of parallel coding agents. Where a single-agent CLI forces you to choose one harness per session, Orca lets you run many simultaneously — "Run Codex, ClaudeCode, OpenCode or Pi side-by-side — each in its own worktree, tracked in one place." The orchestration primitives are real: fan a single prompt out to five agents, each running in an isolated git worktree, then compare the results and merge the winner.

The product thesis from the README: *"The AI Orchestrator for 100x builders. Run Codex, ClaudeCode, OpenCode or Pi side-by-side — each in its own worktree, tracked in one place."* Mobile is a first-class surface (companion app on iOS and Android), and SSH Worktrees push agent execution to a remote box so the laptop does not have to stay online.

## Key Mechanisms

- **Fleet of parallel agents**: any CLI agent works (Claude Code, Codex, OpenCode, Pi, Cursor, GitHub Copilot, Grok, MiMo Code, Amp, OpenClaude, Antigravity, oh-my-pi, Hermes Agent, Devin, Goose, Auggie, Autohand Code, Charm, Cline, Codebuff, Command Code, Continue, Droid, Kilocode, Kimi, Kiro, Mistral Vibe, Qwen Code, Rovo Dev, "+ any CLI agent"). Each agent runs in its own isolated git worktree, tracked in one place.
- **Parallel worktrees + fan-out**: "Fan one prompt across five agents, each in its own isolated git worktree — compare the results and merge the winner." This is the core orchestration primitive: prompt broadcast + per-agent isolation + result aggregation + user-controlled merge.
- **Mobile companion**: iOS App Store (id 6766130217), TestFlight, and Android APK 0.0.42 — "Monitor and steer your agents from your phone — get notified when an agent finishes and send follow-ups from anywhere."
- **SSH Worktrees**: run agents on a remote box with full file editing, git, and terminals — auto-reconnect and port forwarding included; the laptop does not need to stay online.
- **Orca CLI** (`orca`): "Agents drive Orca too — script every workflow with `orca worktree create`, `snapshot`, `click`, and `fill`." This is the sub-agent primitive — an agent can programmatically open worktrees, snapshot state, and drive the IDE through the CLI.
- **Terminal splits**: Ghostty-class terminals with WebGL rendering, infinite splits, and scrollback that survives restarts.
- **Design Mode**: click any UI element in a real Chromium window to send its HTML, CSS, and a cropped screenshot into an agent's prompt.
- **GitHub & Linear, native**: browse PRs, issues, and project boards in-app; open a worktree from any task without a context switch.
- **Account switcher + usage tracking**: see Claude and Codex usage and rate-limit resets, hot-swap accounts without re-logging in.
- **Computer Use**: agents can operate desktop apps and visible UI when a workflow needs real interaction.
- **Annotations on AI diffs**: drop comments on any diff line and ship them back to the agent — review, edit, and commit without leaving Orca.

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Multi-agent fleet — multiple CLI agents from different vendors run concurrently in isolated worktrees; user is the orchestrator who fans prompts out, watches each worktree, and merges the winning branch |
| **Coordination mechanism** | Orca daemon (desktop app) holds the agent/worktree registry; per-agent worktrees are isolated on the local filesystem (or remote via SSH); agents can drive Orca via the `orca` CLI to script multi-step workflows |
| **Human oversight** | Human compares the parallel worktrees, picks the winner, merges; mobile companion lets humans monitor/steer from a phone; "Notifications and unread state" — mark threads unread to come back later |

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | Local filesystem (git worktrees + per-agent state) + remote box (when SSH Worktrees are used); no central database; agent subscriptions are user-owned |
| **Data portability** | **High** — worktrees are plain git repos under the user's control; agent state is local; the project itself is MIT |
| **Offline capability** | **High** — desktop app, worktrees, and CLI all run locally; SSH Worktrees let agent execution happen on a remote box the user controls |
| **Vendor lock-in risk** | **Low** — MIT, BYO agent subscription (Codex, Claude Code, OpenCode, Pi, etc.); worktrees are plain git; mobile is a thin companion |
| **Telemetry** | Anonymous usage data (Orca version, OS, CPU arch, OS release, release channel, random local ID) collected by default; opt out via `DO_NOT_TRACK=1` or `ORCA_TELEMETRY_DISABLED=1`; no PII, no hostname, no username, no IP |

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source / self-hosted | $0 | MIT, free; install the desktop app (macOS / Windows / Linux) or run the headless server; bring your own CLI agent subscription (Codex, Claude Code, OpenCode, Pi, etc.) |
| Mobile companion | Free | iOS App Store, TestFlight, Android APK 0.0.42 — same free model |

No hosted SaaS tier is published; the official site has no `/pricing` page (returns 404), and the README states "Orca is free and open source under the MIT License." The project is YC-backed per the repo topic `yc-backed`.

## Ecosystem & Integrations

- **Agent runtimes** (advertised as "works with any CLI agent — if it runs in a terminal, it runs in Orca"): Claude Code, Codex, OpenCode, Pi, Cursor, GitHub Copilot, Grok, MiMo Code, Amp, OpenClaude, Antigravity, oh-my-pi, Hermes Agent, Devin, Goose, Auggie, Autohand Code, Charm, Cline, Codebuff, Command Code, Continue, Droid, Kilocode, Kimi, Kiro, Mistral Vibe, Qwen Code, Rovo Dev
- **VCS / project tracking**: GitHub (PRs, issues), Linear (project boards) — both browsable in-app
- **Surfaces**: desktop (macOS / Windows / Linux), mobile companion (iOS App Store / TestFlight / Android APK), headless Linux server
- **Distribution**: GitHub Releases, Homebrew Cask (`brew install --cask stablyai/orca/orca`), Arch Linux AUR (`stably-orca-bin`), direct DMG/EXE/AppImage downloads
- **Code signing**: Windows builds signed by SignPath.io (certificate by SignPath Foundation)
- **Community**: Discord (discord.gg/fzjDKHxv8Q), Twitter/X [@orca_build](https://x.com/orca_build), WeChat group 7

## Screenshots / Demo

- [README hero shot — desktop app with parallel worktrees and mobile companion in the corner](https://github.com/stablyai/orca#readme)
- [Mobile companion app showcase](https://www.onorca.dev/docs/mobile)
- [Parallel worktree orchestration](https://www.onorca.dev/docs/model/worktrees)
- [Terminal splits with WebGL scrollback](https://www.onorca.dev/docs/terminal)
- [Design Mode (embedded Chromium → agent prompt)](https://www.onorca.dev/docs/browser/design-mode)
- [Orca CLI overview (`orca worktree create`, `snapshot`, `click`, `fill`)](https://www.onorca.dev/docs/cli/overview)

## References

- [stablyai/orca on GitHub](https://github.com/stablyai/orca)
- [Official website](https://www.onorca.dev/)
- [Documentation map (`docs.onorca.dev`)](https://www.onorca.dev/docs)
- [Download Orca](https://www.onorca.dev/download)
- [Mobile companion docs](https://www.onorca.dev/docs/mobile)
- [Parallel worktrees docs](https://www.onorca.dev/docs/model/worktrees)
- [Orca CLI overview](https://www.onorca.dev/docs/cli/overview)
- [Privacy & telemetry docs](https://www.onorca.dev/docs/telemetry)
- [License (MIT)](https://github.com/stablyai/orca/blob/main/LICENSE)
- [Repository README](https://github.com/stablyai/orca#readme)