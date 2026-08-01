# QM

> Multiplayer agent harness for work: each employee and each shared room gets its own scoped agent with isolated memory, files, keychain, and sandbox, while a central core routes work between personal agents and channel agents.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [qm.ycombinator.com](https://qm.ycombinator.com) |
| **Repository** | [github.com/yc-software/qm](https://github.com/yc-software/qm) |
| **Status** | `Active` — 4,035 GitHub stars, 372 forks; last push 2026-08-01; latest release `v0.1.4` (2026-07-31) |
| **Openness** | `Open source (MIT)` |
| **Deployment** | `Self-hosted` — organization-owned deployment repo targeting Fly.io or AWS; runs in the operator's cloud account |
| **First release** | 2026-07 — earliest tag `v0.1.2` (2026-07-31) |
| **Last release / commit** | `v0.1.4` (2026-07-31); latest main commit `7f2c916` (2026-07-31); repository last push 2026-08-01 |
| **Language / Stack** | TypeScript (Node, Fastify, Bolt for Slack, Vite + Lit for web UI), Postgres, Docker sandbox |
| **License** | MIT |

## What It Does

QM is a headless agent core and surrounding harness designed for an entire company rather than a single user. Every person has a private agent context, and every shared room (Slack channel, group, project) has a channel-scoped agent context. The same identity moves between Slack DMs and the web app, but each scope keeps its own memory, files, credentials, permissions, crons, and durable sandbox. The core is model-agnostic and can drive Pi, OpenCode, Codex, and Claude Code through the same loop.

## Key Mechanisms

- **Scoped agents per person and per room**: each scope owns its own memory, file tree, keychain view, permissions, crons, web apps, and durable sandbox; a Postgres store holds sessions, memory, and queued runs.
- **Agent-to-agent handoff in Slack**: a channel agent can ask a teammate's personal agent to run a task that needs that person's private setup, via the `[[ask-agent: <@USER> | task]]` directive parsed by the Slack plugin.
- **Human-approved personal-agent runs**: the request is surfaced in the original thread as `#channel agent → Name's personal agent`, the target user receives a DM with **Run with my setup** / **Decline** buttons, and the result is posted back as `Name's personal agent → #channel agent`.
- **Colleague agents in channels**: the Slack surface lists bots in a channel as `agent` in the "People here" line and instructs the agent to `@mention` them directly in-thread for ordinary collaboration, treating multiple agents as distinct participants.
- **Shared skills with grants**: skills are scope-owned, shareable by grant, and can be promoted org-wide by an admin; skill packs can be imported from git repositories.
- **Model-agnostic core**: the agent loop sits behind an interface and can be driven by Pi, OpenCode, Codex, or Claude Code; the deployment directory wires the chosen substrates.
- **Org-level policy posture**: every tool call follows a predeclared command policy; scopes can tighten the org's chosen posture (Strict, Auto, Dangerous) but never loosen it.

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Multi-agent peer / human-in-loop — personal agents and channel agents are distinct scoped instances; one agent can delegate to another |
| **Coordination mechanism** | Scoped context routing through the central core; Slack plugin parses agent-request directives and bridges turns between channel and personal scopes; `@mentions` let agents address each other in shared threads |
| **Human oversight** | Dangerous commands require explicit approval buttons; personal-agent handoffs require the target user's explicit **Run with my setup** approval; audit logging covers agent actions |

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | Postgres for sessions, memory, queue, and durable state; per-scope sandbox for files and installed tools |
| **Data portability** | Medium — deployment repo is operator-owned; data lives in the operator's Postgres and object stores; no documented export tool found |
| **Offline capability** | Low — core is self-hosted but relies on Slack/web surfaces and model-provider APIs; local sandbox can run offline if already provisioned |
| **Vendor lock-in risk** | Low-Medium — open-source core and self-hosted data; model/harness/sandbox substrates are swappable via interfaces, but switching cloud targets still requires operator migration |

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source / self-hosted | $0 | Operator brings own cloud account (Fly.io or AWS), model API keys, and infrastructure |

## Ecosystem & Integrations

- **Agent runtimes / harnesses**: Pi, OpenCode, Codex, Claude Code
- **Chat surfaces**: Slack (Bolt Socket Mode, in-process plugin), web UI (Vite + Lit), admin panel, public portal
- **Deployment targets**: Fly.io or AWS via `qm init`; private fork workflow supported
- **Extensibility**: Deployment directory carries org-specific skills, tools, sandbox layers, and infrastructure config; skills importable from git repos
- **Community**: GitHub Issues/PRs; Hacker News discussion

## Screenshots / Demo

- [Official homepage](https://qm.ycombinator.com)
- [GitHub README](https://github.com/yc-software/qm#readme)

## References

- [github.com/yc-software/qm](https://github.com/yc-software/qm)
- [QM homepage](https://qm.ycombinator.com)
- [Getting started docs](https://github.com/yc-software/qm/blob/main/docs/getting-started.md)
- [Deployment directory docs](https://github.com/yc-software/qm/blob/main/docs/deploy-directory.md)
- [Hacker News discussion](https://news.ycombinator.com/item?id=49132130)
