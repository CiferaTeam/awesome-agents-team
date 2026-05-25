# RunFusion (Fusion)

> Open-source multi-node agent orchestrator that turns rough ideas into production code through auto-specification, isolated git worktrees, and review-gated shipping.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [runfusion.ai](https://runfusion.ai) |
| **Repository** | [github.com/runfusion/fusion](https://github.com/runfusion/fusion) |
| **Status** | `Active` — shipping daily; last commit 2026-05-24 |
| **Openness** | `Open source (MIT)` |
| **Deployment** | `Hybrid` — local daemon + multi-node mesh across laptop, server, cloud VM, and phone |
| **First release** | Unknown — no tagged releases yet |
| **Last release / commit** | 2026-05-24 (last commit) |
| **Language / Stack** | TypeScript (primary); npm-distributed CLI and desktop apps |
| **License** | MIT |

## What It Does

Fusion is an open-source orchestrator for autonomous AI agents and full agent companies. It takes a rough task description, auto-writes a PROMPT.md spec with acceptance criteria, then plans, executes, reviews, and ships code in isolated git worktrees. Work can be distributed across a mesh of machines you own, with shared board state and mission progress tracking.

## Key Mechanisms

- **Auto-specification (Triage)**: A planning agent turns a plain-language idea into a structured PROMPT.md with concrete acceptance criteria before any code is written.
- **Plan → review → execute → review loop**: Every task flows through gated states; agents pause for human or automated review at each configured gate.
- **Git worktree isolation**: Each task runs in its own branch and worktree, enabling parallel work with zero file collisions.
- **Multi-node mesh**: Auto-discovery across LAN or cloud; shard tasks across devices while keeping settings, missions, and board state in sync.
- **Mission hierarchy**: Large projects decompose into Mission → Milestone → Slice → Feature → Task with autopilot progress tracking.

## Agent Architecture

- **Agent model**: Multi-agent hierarchical (importable agent companies with CEO, CMO, CTO, COO roles) + human-in-loop
- **Coordination mechanism**: Shared board with task states and inter-agent mailbox messaging; agents delegate, clarify, and coordinate via structured messages
- **Human oversight**: Humans steer agents mid-flight, approve or reject at each review gate, and define mission scope upfront

## Data & Storage Model

- **Primary store**: Local-first with sync across mesh nodes; git repositories and worktrees hold all code state
- **Data portability**: All code lives in standard git repos; PROMPT.md specs and plans are plain markdown
- **Offline capability**: Partial — local planning and execution work offline; multi-node sync and cloud providers require connectivity
- **Vendor lock-in risk**: **Low** — open-source (MIT), standard git, no proprietary data format

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source | $0 | Unlimited; self-host and self-build from source |

## Ecosystem & Integrations

- **IDE / surfaces**: Desktop app (macOS, Windows, Linux), mobile (iOS, Android), web, and CLI (`npx` + `brew`)
- **External services**: GitHub issue/PR sync, Paperclip agent-company import (`npx companies.sh add`)
- **API / extensibility**: Plugin system compatible with Pi extensions; custom workflows and quality gates
- **Community**: GitHub at [runfusion/fusion](https://github.com/runfusion/fusion)

## Screenshots / Demo

- [RunFusion homepage demo sections](https://runfusion.ai)

## References

- [runfusion/fusion on GitHub](https://github.com/runfusion/fusion)
- [Paperclip agent companies](https://paperclip.ai) — compatible import format
