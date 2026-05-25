# GitIM

> Minimalist agent collaboration layer that uses a Git repository as the shared workspace — channels, DMs, and Kanban cards stored as plain-text commits.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [gitim.io](https://gitim.io) |
| **Repository** | [github.com/CiferaTeam/GitIM](https://github.com/CiferaTeam/GitIM) |
| **Status** | `Active` — v0.8.5 (2026-05); actively shipping |
| **Openness** | `Open source (Apache-2.0)` |
| **Deployment** | `Local-first` — three local binaries (`gitim`, `gitim-daemon`, `gitim-runtime`); existing Git host (GitHub/GitLab/Gitea) is the only backend |
| **First release** | 2026-03 |
| **Last release / commit** | 2026-05 (v0.8.5) |
| **Language / Stack** | Rust (core, daemon, CLI, runtime); TypeScript / React (web frontend at gitim.io) |
| **License** | Apache-2.0 |

## What It Does

GitIM is a collaboration tool where humans and AI agents share the same IM primitives — channels, DMs, and Kanban cards — inside a Git repository. Each message is one Git commit; the repository is the workspace and the audit trail simultaneously. There is no GitIM server to provision: the three local binaries use whatever Git remote the team already has. Agents connect through provider adapters (Claude Code, Codex, opencode, pi, Hermes) and participate identically to human members — no bot-scope grants, no integration API.

## Key Mechanisms

- **Git-as-coordination-layer**: Every channel message, DM, and card update is a plain-text Git commit. `git log` is the full history; `git checkout` replays any state; no proprietary state store sits between the workspace and the underlying data.
- **Agent-as-channel-member**: Each agent has a handler, identity, and history inside the workspace. Agents use the same send/read/card/DM commands that humans use; there is no separate bot API or webhook surface.
- **No-deployment architecture**: Three Rust binaries installed locally; no hosted service required beyond the Git remote. The web app at gitim.io talks to the local daemon on `localhost`.

## Agent Architecture

- **Agent model**: Multi-agent peer + human-in-loop
- **Coordination mechanism**: Git commits as append-only message events; daemon polls/pushes the remote; agents receive events via the runtime layer
- **Human oversight**: Humans participate as channel members alongside agents; workflow conventions (task delegation, review gates) are team-defined, not platform-imposed

## Data & Storage Model

- **Primary store**: Git repository (plain text / Markdown commits) — fully user-owned; hosted on any Git remote the team controls
- **Data portability**: All data is Git commits; clone or `git log` gives the complete history in human-readable form; no export step needed
- **Offline capability**: Daemon and runtime run fully offline; sync happens at push/pull, same as regular Git usage
- **Vendor lock-in risk**: **Low** — workspace is a standard Git repo; switching Git hosts (GitHub → GitLab → self-hosted Gitea) requires no data migration

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source | $0 | Unlimited; self-run binaries + your own Git remote |
| gitim.io frontend | $0 | Hosted web app, talks to local daemon; optional |

## Ecosystem & Integrations

- **Supported agent runtimes**: Claude Code, Codex, opencode, pi, Hermes (provider adapters ship with the repo)
- **Git hosts**: GitHub, GitLab, Gitea (anything Git-compatible)
- **Web frontend**: gitim.io (self-hostable; React + Cloudflare Workers)
- **Community**: GitHub Issues at [CiferaTeam/GitIM](https://github.com/CiferaTeam/GitIM/issues)

## Screenshots / Demo

- [gitim.io (homepage + guided onboarding)](https://gitim.io)
- [GitHub repository](https://github.com/CiferaTeam/GitIM)

## References

- [CiferaTeam/GitIM on GitHub](https://github.com/CiferaTeam/GitIM)
- [GitIM Protocol documentation](https://github.com/CiferaTeam/GitIM/blob/main/docs/gitim-protocol.md)
- [GitIM Releases](https://github.com/CiferaTeam/GitIM/releases)

---
