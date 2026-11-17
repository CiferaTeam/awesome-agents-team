# kwant

> Self-hosted team of named AI bots in one Rust binary: bots hand work to each other with an @mention, and a task is marked Verified only when kwant runs the check itself.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [kwant.si](https://kwant.si) |
| **Repository** | [github.com/alexsergivan/kwant](https://github.com/alexsergivan/kwant) |
| **Status** | `Active` (desktop apps for Linux and Windows are beta) |
| **Openness** | `Open source (AGPL-3.0)`, with an optional commercial license for embedding or resale |
| **Deployment** | `Self-hosted` / `Local-first`: Mac app, Linux `.deb` / AppImage, Windows installer, or `kwnt serve` on a server (binary, systemd or Docker Compose) |
| **First release** | 2026-10 |
| **Last release / commit** | 2026-11 (0.8.0) |
| **Language / Stack** | Rust (Tokio, Axum, SQLite), React web app embedded in the binary |
| **License** | AGPL-3.0-only |

## What It Does

kwant runs a team of AI bots that share chats, channels and teams. Each bot has its own role, voice and model, and bots pass work to each other by @mentioning a teammate. In a channel, kwant routes each message to the bot that fits and shows why it was picked. Work becomes cards on a Mission board, and a card only turns Verified when kwant runs a check itself (for example a test or a file check) and stores the receipt. The bots run on the Claude, Codex or Grok CLI the user is already signed in to, on Anthropic, OpenAI or xAI API keys, or on any OpenAI- or Anthropic-compatible server, including local models.

## Key Mechanisms

- **@mention handoffs**: a bot hands the next step to a teammate by mentioning it; a team lead can run short discussions and post one summary.
- **Verified by kwant, not by the bot**: Mission board cards need a check that kwant executes itself; attached files count as evidence to review, never as proof.
- **Spaces**: separate spaces (for example work and home), each with its own bots, teams, channels, routines, accounts, approval rule and hiring rule.
- **Several accounts per engine**: a default and a priority order; when one account runs out of usage, the turn moves to the next one and the chat says so.
- **Approvals with a fixed floor**: modes are ask, ask only when risky (default) or off; payment-like commands and checkouts always ask, and only the person can change the mode or answer cards.
- **Routines and an Inbox**: scheduled routines (bots can set them up on request, with Undo), self-scheduled follow-ups, and an Inbox of what is waiting, finished or failed.
- **Dev mode**: a bot that did not write a pull request reviews it; a pre-push card checks for secrets, new packages and weakened tests before a bot pushes.

## Agent Architecture

- **Agent model**: Multi-agent peer team with an optional team lead; per-message routing in channels
- **Coordination mechanism**: Shared chats and channels, @mention handoffs, Mission board cards with kwant-run checks
- **Human oversight**: Approval cards for risky steps (exact command shown, allow once / always / deny), payments always ask, person-only API routes for approvals, vault and settings, and an Inbox for decisions

## Data & Storage Model

- **Primary store**: Local SQLite in the `~/.kwnt` data folder, shared by the desktop apps and `kwnt serve`
- **Data portability**: Data stays in the local data folder; bots can be imported from OpenClaw and Hermes Agent workspaces, Codex AGENTS.md, Paperclip, Claude Code subagents, SKILL.md files and JSON exports
- **Offline capability**: The app and data are local; model turns need the chosen provider, or a local OpenAI-compatible model server
- **Vendor lock-in risk**: Low: AGPL source, local storage, and any of several model providers or a self-hosted model

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source | $0 | Full app under AGPL-3.0; the user pays only for the AI accounts or API keys they bring |
| Commercial license | Contact | Only needed to sell, host or embed kwant without publishing changes |

## Ecosystem & Integrations

- **Agent runtimes**: Claude Code CLI, Codex CLI, Grok CLI, Anthropic / OpenAI / xAI API keys, OpenAI- or Anthropic-compatible servers
- **External services**: MCP tool servers, Telegram, optional read-only IMAP inbox and GitHub issues / pull requests, a shared Chromium browser for bots, saved passwords with an optional Bitwarden store
- **API / extensibility**: HTTP/SSE API, inbound MCP endpoint so an outside coding agent can ask a kwant bot for work (it cannot approve or act as the user), per-bot skills and memory
- **Community**: [GitHub Discussions](https://github.com/alexsergivan/kwant/discussions)

## Screenshots / Demo

- [README screenshots](https://github.com/alexsergivan/kwant#why-kwant)
- [Features page with screenshots](https://kwant.si/features)

## References

- [Quickstart docs](https://kwant.si/docs/quickstart)
- [Approvals guide](https://github.com/alexsergivan/kwant/blob/1e49dbd5ec7849d5e2e542e6488321b54424859d/docs/approvals.md)
- [Mission board](https://github.com/alexsergivan/kwant/blob/1e49dbd5ec7849d5e2e542e6488321b54424859d/docs/mission-control.md)
- [Dev mode](https://github.com/alexsergivan/kwant/blob/1e49dbd5ec7849d5e2e542e6488321b54424859d/docs/dev-mode.md)
- [Connecting outside agents over MCP](https://github.com/alexsergivan/kwant/blob/1e49dbd5ec7849d5e2e542e6488321b54424859d/docs/agents-connect.md)
- [Changelog](https://github.com/alexsergivan/kwant/blob/main/CHANGELOG.md)
- [Releases](https://github.com/alexsergivan/kwant/releases)
