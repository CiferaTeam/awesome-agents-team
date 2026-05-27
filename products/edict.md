# Edict

> OpenClaw-based multi-agent orchestration system inspired by China's "Three Departments and Six Ministries" imperial governance structure — 12 specialized AI agents with institutional review, real-time dashboard, and full audit trails.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [github.com/cft0808/edict](https://github.com/cft0808/edict) |
| **Repository** | [github.com/cft0808/edict](https://github.com/cft0808/edict) |
| **Status** | `Active` — 15,876 GitHub stars |
| **Openness** | `Open source (MIT)` |
| **Deployment** | `Self-hosted` — local Python + React dashboard, Docker, or systemd |
| **First release** | 2026-02-23 |
| **Last release / commit** | 2026-05-26 |
| **Language / Stack** | Python (backend, stdlib-only server), React 18 + TypeScript + Vite (frontend), Redis (event bus) |
| **License** | MIT |

## What It Does

Edict (三省六部制) is a multi-agent orchestration framework built on top of OpenClaw that models AI collaboration after China's imperial governance system. Tasks flow through a rigid hierarchy: the Crown Prince sorts messages, the Secretariat plans, the Chancellery reviews and can veto, the Department of State dispatches, and the Six Ministries execute in parallel. Every state transition is protected by a state machine, every action is audited, and a real-time dashboard ("Military Affairs Office") gives humans full visibility and intervention capability.

## Key Mechanisms

- **Three Departments + Six Ministries hierarchy** — 12 agents with rigid role boundaries: Crown Prince (sorting), Secretariat (planning), Chancellery (review/veto), Department of State (dispatch), Six Ministries (execution: data, docs, engineering, compliance, infrastructure, HR), plus Morning Briefing Officer
- **Institutional veto power (Chancellery)** — The Chancellery must approve every plan before execution; it can reject and send back for rework. This is architectural, not optional
- **Protected state machine** — `kanban_update.py` enforces valid state transitions; illegal jumps are rejected and logged
- **Permission matrix** — Strict rules on which agent can message which; no agent can bypass the hierarchy
- **Real-time dashboard (Military Affairs Office)** — Single-file ~2500-line HTML dashboard + React frontend; live Kanban, timeline, agent health, token consumption, task intervention (pause/cancel/resume)
- **Agent thinking visualization** — Real-time display of agent reasoning, tool calls, and results
- **Outbox Relay + EventBus** — Redis Streams for decoupled async communication; transaction Outbox pattern guarantees at-least-once delivery
- **Parallel dispatch engine** — Exponential backoff retry, resource locks, DAG-based task decomposition
- **Remote Skills ecosystem** — Import skills from GitHub/any HTTPS URL via CLI, API, or dashboard UI; version management and updates
- **Template library (Imperial Edicts)** — 9 preset templates: weekly report, code review, API design, competitive analysis, data report, blog post, deployment plan, email copy, standup summary
- **Agent performance scoring (Merit Book)** — Tracks agent performance for model recommendation and cost optimization
- **News aggregation + Feishu push** — Daily morning briefing with news digest

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Multi-agent hierarchical — 12 agents in a strict chain-of-command with the Chancellery as a mandatory review gate |
| **Coordination mechanism** | Hierarchical flow + async EventBus (Redis Streams). Crown Prince → Secretariat → Chancellery → Department of State → Six Ministries. State machine protects all transitions; Outbox Relay guarantees event delivery |
| **Human oversight** | Humans act as the Emperor — issue commands via Feishu/Telegram/Signal, monitor via real-time dashboard, intervene (pause/cancel/resume) at any point. Manual approval mode (Imperial Review) available |

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | Local filesystem + Redis (event bus). Runtime data in `data/` directory; SQLite/SQLAlchemy for backend models |
| **Data portability** | **High** — tasks exported as JSON with full audit trails; skills importable/exportable; no cloud dependency |
| **Offline capability** | Partial — local execution and dashboard work offline; LLM API calls and news fetching require internet |
| **Vendor lock-in risk** | **Low** — open source (MIT), self-hosted by design, built on OpenClaw (extensible to other CLI agents), skills from arbitrary URLs |

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source / self-hosted | $0 | Self-build and self-host; bring your own OpenClaw setup and AI provider credentials |

## Ecosystem & Integrations

- **Base agent runtime**: OpenClaw (with compatibility for other CLI agents)
- **Frontend**: React 18 + TypeScript + Vite + Zustand (13 components)
- **Backend**: Python stdlib `http.server` (~2300 lines, zero dependencies) + SQLAlchemy + Redis Streams
- **Messaging**: Feishu, Telegram, Signal
- **Skills sources**: GitHub, Gitee, any HTTPS URL
- **Deployment**: Docker (`docker run -p 7891:7891 cft0808/edict`), systemd service, or manual install
- **Community**: GitHub Issues, WeChat public account

## Screenshots / Demo

- [Edict GitHub repository — README with architecture diagram and demo video](https://github.com/cft0808/edict)
- [Docker demo image](https://hub.docker.com/r/cft0808/sansheng-demo) — pre-built with simulated data

## References

- [Edict GitHub repository](https://github.com/cft0808/edict)
- [Task dispatch architecture documentation](https://github.com/cft0808/edict/blob/main/docs/task-dispatch-architecture.md)
- [Getting started guide](https://github.com/cft0808/edict/blob/main/docs/getting-started.md)
- [Remote Skills guide](https://github.com/cft0808/edict/blob/main/docs/skills-guide.md)
