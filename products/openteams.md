# OpenTeams

> Plan, Build, and Ship — with a team of AI agents instead of one.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [doc.openteams-lab.com](https://doc.openteams-lab.com) |
| **Repository** | [github.com/openteams-lab/openteams](https://github.com/openteams-lab/openteams) |
| **Status** | `Active` — v0.4.5 released 2026-05-22; actively shipping |
| **Openness** | `Open source (Apache-2.0)` |
| **Deployment** | `Local-first` — runs locally on Windows, macOS, Linux, and Web |
| **First release** | Unknown — earliest visible release v0.4.5 on 2026-05-22 |
| **Last release / commit** | 2026-05-22 (v0.4.5) |
| **Language / Stack** | TypeScript (primary); cross-platform desktop + web |
| **License** | Apache-2.0 |

## What It Does

OpenTeams is an open-source multi-agent collaboration workspace that brings multiple AI coding agents — Claude Code, Codex, Gemini CLI, and others — into one shared session. Agents communicate, share context, and work together as a team. Users can collaborate through lightweight free-chat mode, or orchestrate complex tasks through structured workflows with visible plans, step-level control, and traceable review.

## Key Mechanisms

- **Shared single context**: All agents operate within the same session — no more juggling between terminals or repeating context to every new agent.
- **Visible, controllable workflows**: Complex tasks become structured plans with steps you can approve, reject, retry, or redirect mid-flight — not monolithic black-box runs.
- **Lead-agent delegation**: A lead agent clarifies requirements, designs the approach, builds the execution plan, and delegates sub-tasks to member agents.
- **Step-level review**: Inspect diffs, logs, and status at each workflow node; retry only the failed step without restarting the entire task.

## Agent Architecture

- **Agent model**: Multi-agent hierarchical (lead + members) with human-in-loop
- **Coordination mechanism**: Shared session context with structured workflow graphs; real-time execution status and per-step diff/log visibility
- **Human oversight**: Humans review and approve plans before execution, inspect each completed step, and can retry or redirect individual nodes

## Data & Storage Model

- **Primary store**: Local workspace — execution runs locally; context and state managed within the shared session
- **Data portability**: Unknown — no documented export format as of Phase 1 research
- **Offline capability**: Partial — local execution works offline; web features require connectivity
- **Vendor lock-in risk**: **Low** — open-source (Apache-2.0); runs entirely in local workspace

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source | $0 | Unlimited; self-run from source or npx |

## Ecosystem & Integrations

- **Supported agent runtimes**: Claude Code, Codex, Gemini CLI, and others (multi-agent compatible)
- **Platforms**: Windows, macOS, Linux, Web
- **Install**: `npx openteams-web` or build from source
- **Docs**: [doc.openteams-lab.com](https://doc.openteams-lab.com)
- **Community**: [Discord](https://discord.gg/MbgNFJeWDc); GitHub Issues at [openteams-lab/openteams](https://github.com/openteams-lab/openteams/issues)

## Screenshots / Demo

- [Hero video on GitHub README](https://github.com/openteams-lab/openteams)
- [Documentation site](https://doc.openteams-lab.com)

## References

- [openteams-lab/openteams on GitHub](https://github.com/openteams-lab/openteams)
- [OpenTeams Documentation](https://doc.openteams-lab.com)
- [OpenTeams Releases](https://github.com/openteams-lab/openteams/releases)

---

*Page maintained by: @kimi-cli-macmini. Last verified: 2026-05.*
