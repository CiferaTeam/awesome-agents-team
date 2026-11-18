# Mel

> Multi-agent, multi-model AI terminal for coding: agent teams work in real panes on macOS, Windows and Linux, with a VS Code extension and configurable approvals.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [openmel.dev](https://www.openmel.dev) |
| **Repository** | `Closed source` — no public product repo |
| **Status** | `Active` |
| **Openness** | `Closed source` / `Freemium` |
| **Deployment** | `Local-first` — desktop terminal runs on the user's machine; only prompts/context go to connected model providers |
| **First release** | Unknown |
| **Last release / commit** | 2026-11 — actively shipped (website lists current downloads for macOS, Windows and Linux) |
| **Language / Stack** | Unknown (desktop terminal application with CLI workers) |
| **License** | Proprietary |

## What It Does

Mel is an agentic terminal: a real terminal (tabs, splits, sessions) where a lead agent decomposes work, spawns worker agents in their own panes, and integrates their results. Workers run on any supported model, so one task can use several providers side by side. It targets coding workflows — builds, tests, repo changes, deployments — and also ships a VS Code extension. Approvals for writes and commands are configurable per conversation, from card-by-card confirmation to fully autonomous mode.

## Key Mechanisms

- **Lead + worker agents**: the lead coordinates while workers own disjoint file scopes and run in parallel panes; reports are integrated, not trusted blindly.
- **Multi-model routing**: any supported model (Claude, GPT, Gemini, DeepSeek, Qwen and more) per agent; BYOK on the free tier.
- **Configurable approvals**: sensitive writes and commands go through approval cards unless the user enables autonomous mode.
- **Skills system**: saved procedures the agents load and follow, per project or global.
- **Conversation persistence**: every session is saved locally and survives quit or crash.

## Agent Architecture

- **Agent model**: Multi-agent hierarchical — lead agent spawns and polls workers; human-in-the-loop via approvals.
- **Coordination mechanism**: Panes and shared project memory (remember/recall); workers report back to the lead, which verifies against the diff.
- **Human oversight**: Approval cards for file edits and shell commands, adjustable up to full autonomy; users can inspect any worker pane directly.

## Data & Storage Model

- **Primary store**: Local device — conversations and settings live on the user's machine.
- **Data portability**: Conversations are stored as local files under the user's data directory.
- **Offline capability**: Partial — the terminal runs locally, but model calls require network access.
- **Vendor lock-in risk**: **Medium** — closed-source app, but BYOK means model spend is not locked to one vendor.

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Free | $0 | Bring your own API key; provider usage charges apply |
| Pro | $20/mo | Hosted credits; includes Pro terminal features |
| Max | $200/mo | Higher hosted-credit allowance |
| Business | $50/seat/mo | Per-seat team tier |

## Ecosystem & Integrations

- **Clients**: macOS, Windows, Linux desktop terminals; VS Code extension.
- **Models**: Claude, GPT, Gemini, DeepSeek, Qwen and others via BYOK or hosted credits.
- **Protocols**: MCP servers/connectors supported.
- **External services**: CLI-based account sign-ins (GitHub, Vercel, Stripe, cloud providers) usable from agents.
- **Community**: Unknown — none documented.

## Screenshots / Demo

- [Mel homepage](https://www.openmel.dev)

## References

- [Mel homepage](https://www.openmel.dev)
