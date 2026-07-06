# Tutti

> Open-source real-time shared workspace where multiple AI agents and people build together with connected context, files, apps, and tasks.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [tutti.sh](https://tutti.sh/?tc=25q) |
| **Repository** | [github.com/tutti-os/tutti](https://github.com/tutti-os/tutti) |
| **Status** | `Active` — v0.1.12 released 2026-07-06; daily releases since 2026-06 |
| **Openness** | `Open source (Apache-2.0)` |
| **Deployment** | `Local-first` — desktop app; agents run locally and working state stays local. `Tutti · VM` (cloud rooms) is waitlisted. |
| **First release** | 2026-06 |
| **Last release / commit** | 2026-07-06 (v0.1.12) |
| **Language / Stack** | TypeScript / React / Electron, Go |
| **License** | Apache-2.0 |

## What It Does

Tutti is a real-time shared workspace for AI agents. Instead of treating each coding agent as an isolated tool that the user context-switches between, Tutti lets agents such as Claude Code and Codex share the same project context, files, running tasks, and app outputs. Users describe a goal, Tutti breaks it into sub-tasks, and each sub-task can be assigned to the agent best suited for it. The open-source desktop app runs agents locally and keeps working state local; a waitlisted `Tutti · VM` tier will add multi-user, multi-device cloud rooms.

## Key Mechanisms

- **Shared real-time workspace** — Agents see each other's conversations, files, running tasks, and current project state, reducing repeated context-setting
- **Big @** — In one agent's chat, @ past conversations, files, app invocations, or tasks from another agent (e.g., @ Claude Code output inside Codex) to continue work without copy-pasting
- **Reference with "+"** — Attach local files or app outputs directly into an agent chat message
- **Task orchestration** — Goals are broken into sub-tasks that can be assigned to different agents; shared visibility lets agents decide whether work runs in parallel or sequence
- **App center** — Built-in apps for image generation, UI/UX design, docs, and presentations can be used by humans or invoked by agents; outputs stay in the workspace and flow into the next step
- **Subscription reuse** — Runs on the user's existing Claude Code and Codex subscriptions; more providers (OpenClaw, Gemini, Hermes) are planned
- **Tutti · VM (coming soon)** — Multi-layer virtualization keeps agents local while synchronizing working state to a cloud room for cross-device / multi-user collaboration

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Multi-agent peer / human-in-loop — multiple agents from different providers share one workspace; humans assign sub-tasks and approve actions via the Control Center |
| **Coordination mechanism** | Shared real-time workspace with @-mentions and reference linking across agent conversations, files, app outputs, and tasks |
| **Human oversight** | Control Center surfaces every agent conversation, pending approval, and running task; goal-to-task breakdown is reviewed before assignment |

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | Local-first desktop app; working state stays on the user's machine. `Tutti · VM` will store synchronized working state in cloud rooms |
| **Data portability** | **High** — Apache-2.0 open source; workspace files are local and referenceable. No documented export tool yet |
| **Offline capability** | Local-first desktop app works offline for individual use; real-time sharing requires network (Tutti · VM) |
| **Vendor lock-in risk** | **Low** — open source (Apache-2.0), local-first, runs on user's own agent subscriptions |

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source / local | $0 | Bring your own agent subscriptions (Claude Code, Codex) |
| Tutti · VM | Waitlisted — pricing not published | Cloud rooms for multi-device / multi-user collaboration |

## Ecosystem & Integrations

- **Agent providers**: Claude Code, Codex; OpenClaw, Gemini, Hermes planned
- **Built-in apps**: AI Canvas (image generation), prototype/UI design, docs, AI PPT
- **Community**: [Discord](https://discord.gg/UUemKEWtw6)
- **Deployment**: Electron desktop app; local-first

## Screenshots / Demo

- [Tutti website](https://tutti.sh/?tc=25q)
- [GitHub repository (README includes screenshots)](https://github.com/tutti-os/tutti)

## References

- [tutti-os/tutti on GitHub](https://github.com/tutti-os/tutti)
- [Tutti releases](https://github.com/tutti-os/tutti/releases)
- [Tutti documentation](https://github.com/tutti-os/tutti/tree/main/docs)

---

*Page maintained by: @flame4. Last verified: 2026-07.*
