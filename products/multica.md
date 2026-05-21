# Multica

> Open-source task board that treats AI coding agents as first-class team members — assign issues to agents, watch them execute, accumulate reusable Skills.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [multica.ai](https://multica.ai) |
| **Repository** | [github.com/multica-ai/multica](https://github.com/multica-ai/multica) |
| **Status** | `Active` — v0.3.2 released 2026-05-18, daily releases throughout May 2026 |
| **Openness** | `Source available (Modified Apache-2.0)` + managed cloud tier (waitlisted) |
| **Deployment** | `Hybrid` — local daemon for agent execution; server layer is cloud or self-hosted (Docker Compose / Helm) |
| **First release** | 2026-04 (estimated; earliest visible GitHub release is v0.2.26 on 2026-05-06) |
| **Last release / commit** | 2026-05 (v0.3.2) |
| **Language / Stack** | TypeScript 47% (Next.js 16), Go 46% (Chi + WebSocket), PostgreSQL 17 + pgvector |
| **License** | Modified Apache-2.0 — prohibits using Multica as a third-party SaaS, managed hosting, or embedded commercial product without authorization |

## What It Does

Multica is a project management and agent-orchestration layer that lets human developers and AI coding agents share the same issue board. You create GitHub-style issues, assign them to any supported agent (Claude Code, Codex, Cursor, Copilot, Gemini, and 8 others), and a local daemon picks up assigned tasks, executes them via the agent's CLI, and streams progress back via WebSocket. Completed solutions can be saved as team-wide "Skills" — callable procedures that any agent can reuse, building institutional memory over time.

## Key Mechanisms

- **Skill Compounding**: Solved tasks can be saved as named Skills (e.g., `deploy-to-staging`, `run-code-review`). All agents on the team share the Skill library, so successful patterns compound across agents and sessions rather than being lost at context expiry.
- **Squad Routing** (v0.3.0+): A lead agent receives an issue and delegates sub-tasks to member agents, enabling hierarchical multi-agent execution within a single project without human re-assignment.
- **Daemon + Split-Plane Privacy**: Agent execution runs entirely on the user's machine — API keys never leave the local daemon. Only task state, logs, and Skill metadata sync to the server (cloud-managed or self-hosted), creating a meaningful data boundary between execution and coordination.

## Agent Architecture

- **Agent model**: Multi-agent hierarchical (Squads) with human-in-loop
- **Coordination mechanism**: Task board state in PostgreSQL; real-time updates via WebSocket; hierarchical routing via Squad lead/member assignment
- **Human oversight**: Humans assign issues, unblock agents via comments, and promote solutions to Skills — agents cannot self-assign or self-promote without human initiation at the issue level

## Data & Storage Model

- **Primary store**: PostgreSQL 17 (task state, issue history, Skill library) — user-controlled if self-hosted
- **Data portability**: No explicit export tooling documented as of Phase 1 research; self-hosted PostgreSQL gives direct data access
- **Offline capability**: Daemon is local and can execute tasks without cloud connectivity; task state sync and board UI require server connectivity
- **Vendor lock-in risk**: **Low** (self-hosted) / **Medium** (cloud tier) — self-host option via Docker Compose/Helm gives full data sovereignty; cloud tier stores task history server-side with no documented export path

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Self-host | $0 (Apache-2.0) | Unlimited; requires own infrastructure |
| Multica Cloud | Unverified — waitlisted as of 2026-05 | Not publicly published |

*Cloud tier pricing not indexed in any public source as of 2026-05-19. Searched: multica.ai/pricing, stork.ai review, tulsk.io comparison.*

## Ecosystem & Integrations

- **Supported agent runtimes**: Claude Code, Codex, Cursor, GitHub Copilot, Gemini, Hermes, Kimi, Kiro CLI, OpenCode, OpenClaw, Pi (11 confirmed)
- **External services**: GitHub (issue sync, comments)
- **Self-host**: Docker Compose, Helm chart
- **Desktop app**: macOS confirmed; other platforms unverified
- **Community**: GitHub Discussions; 29,300+ stars (2026-05)

## Screenshots / Demo

- [Homepage demo](https://multica.ai)
- [GitHub repo (includes screenshots in README)](https://github.com/multica-ai/multica)

## References

- [multica-ai/multica on GitHub](https://github.com/multica-ai/multica)
- [Multica Homepage](https://multica.ai/)
- [Multica Docs](https://multica.ai/docs)
- [Multica Releases](https://github.com/multica-ai/multica/releases)
- [AIToolly: Multica — open-source hosted agent platform (2026-04)](https://aitoolly.com/ai-news/article/2026-04-12-multica-the-open-source-hosted-agent-platform-transforming-ai-into-collaborative-team-members)
- [Tulsk vs Multica comparison](https://tulsk.io/compare/multica)
- [Stork.ai review](https://www.stork.ai/en/multica)

---
