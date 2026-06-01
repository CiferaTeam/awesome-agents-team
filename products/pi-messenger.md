# PI Messenger

> Multi-agent communication extension for the Pi coding agent — file-based coordination with no daemon or server required.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [github.com/nicobailon/pi-messenger](https://github.com/nicobailon/pi-messenger) |
| **Repository** | [github.com/nicobailon/pi-messenger](https://github.com/nicobailon/pi-messenger) |
| **Status** | `Active` — 593 GitHub stars; latest release v0.14.1 |
| **Openness** | `Open source (MIT)` |
| **Deployment** | `Local-first` — Pi coding agent extension; file-based coordination |
| **First release** | 2026-01-23 |
| **Last release / commit** | 2026-04-04 (v0.14.1) |
| **Language / Stack** | TypeScript |
| **License** | MIT |

## What It Does

PI Messenger is an extension for the Pi coding agent that enables multiple agents running in different terminals (sharing a project folder) to communicate and coordinate as if they were in a chat room. Agents can join, see who's online, claim tasks, reserve files, send messages, and collaborate on multi-step projects — all without a central daemon or server. Coordination is entirely file-based, making it lightweight and easy to set up.

## Key Mechanisms

- **File-based mesh** — All coordination (registry, inboxes, reservations, swarm claims) lives in `~/.pi/agent/messenger/` (global) and `.pi/messenger/` (project-scoped). No daemon, no server, no network setup
- **Living presence** — Real-time status indicators (active, idle, away, stuck) with tool call counts, token usage, and auto-generated status messages. Agent names appear in the status bar with peer count and unread indicators
- **Activity feed** — Unified timeline of edits, commits, test runs, messages, and task events. Queryable via `{ action: "feed" }`
- **File reservations** — Claim files or directories; other agents get blocked with a clear message identifying who to coordinate with. Auto-releases on leave or exit
- **Stuck detection** — Agents idle too long with an open task or reservation are flagged as stuck; peers receive notifications
- **Human as participant** — Interactive Pi sessions appear in the agent list with `(you)` label, with full activity tracking and status messages. Chat from the overlay
- **Crew mode** — Multi-agent task orchestration from a PRD or inline prompt:
  - **Plan** — Planner analyzes codebase and PRD, drafts tasks with dependencies. Reviewer checks the plan; planner refines until SHIP or max passes reached
  - **Work** — Workers implement ready tasks in parallel waves. Autonomous mode runs waves back-to-back until completion or blockage. Each completed task gets automatic reviewer pass (SHIP / NEEDS_WORK / MAJOR_RETHINK)
  - **Review** — Manual review of specific tasks or the full plan
- **Skill system** — Three-tier skill discovery: user skills (`~/.pi/agent/skills/`), extension skills (`crew/skills/`), and project skills (`.pi/messenger/crew/skills/`). Skills loaded on-demand by workers; zero tokens spent until needed
- **Swarm mode** — Task claiming and completion workflow for decentralized task distribution
- **Interactive overlay** — `/messenger` opens a TUI with agent presence, activity feed, and chat. Supports `@Name msg` for DMs and `@all msg` for broadcasts

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Multi-agent peer mesh — agents discover each other via file-based registry. Crew mode adds planner/worker/reviewer/analyst roles with parallel wave execution |
| **Coordination mechanism** | File-based shared state in `~/.pi/agent/messenger/` and `.pi/messenger/`. Messages wake receiving agents via `pi.sendMessage()` with `triggerTurn: true` and `deliverAs: "steer"`. File reservations enforced via tool_call hooks |
| **Human oversight** | Human Pi sessions appear as full participants in the mesh with activity tracking. Permission control via reservation system and tool_call hooks on write/edit operations |

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | File-based JSON/JSONL in `~/.pi/agent/messenger/` (global state) and `.pi/messenger/` (project-scoped). Crew logs live at `<project>/.pi/messenger/crew/` |
| **Data portability** | **High** — all state is plain JSON/JSONL and markdown files stored locally. No external servers or proprietary formats |
| **Offline capability** | Full — file-based coordination requires no network; all operations are local filesystem reads/writes |
| **Vendor lock-in risk** | **Low** — MIT-licensed extension for Pi coding agent. File-based state is human-readable JSON/JSONL. Generated code and task outputs remain in the project directory |

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source | $0 | Free extension; bring your own Pi coding agent and API keys |

## Ecosystem & Integrations

- **Base agent**: Pi coding agent (required host)
- **Models**: Configurable — defaults to Anthropic Claude family (opus/sonnet/haiku). Supports OpenRouter and explicit provider selection with `:level` thinking control suffixes
- **Skills**: Compatible with Pi's standard `dir/SKILL.md` format. Three-tier discovery: user, extension, project-level
- **Platform support**: Any platform running Pi coding agent (terminal-based)
- **Install**: `pi install npm:pi-messenger` or `npx pi-messenger --crew-install`

## Screenshots / Demo

- [PI Messenger GitHub repository — README with full feature overview](https://github.com/nicobailon/pi-messenger)
- [Latest releases](https://github.com/nicobailon/pi-messenger/releases)

## References

- [PI Messenger GitHub repository](https://github.com/nicobailon/pi-messenger)
- [Pi coding agent](https://github.com/badlogic/pi-mono)
- [mcp_agent_mail by @Dicklesworthstone](https://github.com/Dicklesworthstone/mcp_agent_mail) — Inspiration for agent-to-agent messaging
