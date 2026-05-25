# Syncless

> Stop being the middleman. An agent that works across your browsers, MacBooks, servers, clusters, and even your teammates.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [syncless.ai](https://syncless.ai/) |
| **Repository** | Issue tracker: [github.com/langgenius/syncless-issue](https://github.com/langgenius/syncless-issue) — core platform is closed source |
| **Status** | `Active` — public beta with Discord community; mobile app coming soon |
| **Openness** | `Closed source` |
| **Deployment** | `Cloud` — managed SaaS; client runs on macOS and browsers |
| **First release** | Unknown |
| **Last release / commit** | Unknown — no public changelog |
| **Language / Stack** | Unknown — client-side binaries for macOS; cloud stack undisclosed |
| **License** | Proprietary — Copyright © 2025 LangGenius, Inc. |

## What It Does

Syncless is a cross-device, cross-person AI agent orchestration platform built by LangGenius. Instead of making humans copy-paste context between tools, Syncless lets you `@` any connected device or teammate and have the agent carry context, files, and actions across the boundary automatically.

The platform centers on **Project Templates** — reusable workflows where each step defines what an agent (or human) should do, which machine to run on, and where to hand off results. A typical template might chain three tasks: monitor an API documentation change, open a GitHub issue, implement the feature in a local workspace, open a PR, review it, and publish a new release — all without a human relaying intermediate results.

## Key Mechanisms

- **Cross-device `@` mentions**: Address any connected browser, MacBook, server, or cluster directly from the chat interface. The agent executes actions on the target device natively.
- **Device interconnection**: Devices talk to each other through Syncless' cloud relay, moving files, context, and partial results across machines without manual transfer.
- **Human-in-the-loop delegation**: `@` a colleague to request input or approval. The agent pauses the workflow, delivers the context to the human, and resumes when they respond.
- **Project Templates**: Pre-defined multi-step pipelines with explicit handoffs. Each task specifies actor (agent or human), target machine, working directory, and output destination.
- **Official API + CLI wrapper**: Syncless exposes a public API ([docs.syncless.ai](https://docs.syncless.ai/)). The community maintains `syncless-cli` ([github.com/ACAne0320/syncless-cli](https://github.com/ACAne0320/syncless-cli)) for terminal and agent-native usage.
- **Mobile web control**: Manage connected devices and running projects from a phone browser; native mobile app is listed as coming soon.

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Single coordinator agent that dispatches tasks to device-local runners and human participants |
| **Coordination mechanism** | Cloud-managed Project Templates with explicit step ordering and handoff points; human `@` mentions create blocking checkpoints |
| **Human oversight** | Humans are `@`-mentioned at decision points; they receive full workflow context and can approve, reject, or redirect without losing state |
| **Multi-agent protocol** | Device-to-device context passing via Syncless cloud relay; no documented open protocol |

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | Cloud-hosted by LangGenius; local device state is ephemeral and synced through the relay |
| **Data portability** | Unknown — no documented export format for projects, tasks, or conversation history |
| **Offline capability** | Limited — device-local actions may work without connectivity, but coordination and handoffs require cloud relay |
| **Vendor lock-in risk** | **High** — closed-source platform with proprietary template format and cloud relay; API exists but coverage and stability are unverified |

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Unknown | Unknown | Pricing not publicly disclosed as of current research |

## Ecosystem & Integrations

- **Platforms**: macOS client, web dashboard, browser extension; mobile app (coming soon)
- **API**: [docs.syncless.ai](https://docs.syncless.ai/)
- **Community CLI**: [syncless-cli](https://github.com/ACAne0320/syncless-cli) — unofficial Node.js wrapper around the official API
- **Community**: [Discord](https://discord.gg/syncless)
- **Issue tracker**: [github.com/langgenius/syncless-issue](https://github.com/langgenius/syncless-issue)

## Screenshots / Demo

- [syncless.ai — homepage](https://syncless.ai/)
- [Syncless documentation](https://docs.syncless.ai/)

## References

- [Syncless homepage](https://syncless.ai/)
- [Syncless documentation](https://docs.syncless.ai/)
- [Syncless issue tracker (LangGenius)](https://github.com/langgenius/syncless-issue)
- [syncless-cli — unofficial community wrapper](https://github.com/ACAne0320/syncless-cli)
- [LangGenius, Inc.](https://langgenius.ai/)
