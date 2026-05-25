# LobeHub

> Chief Agent Operator that organizes your agents into 7×24 operations by hiring, scheduling, and reporting on your entire AI team.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [github.com/lobehub/lobehub](https://github.com/lobehub/lobehub) |
| **Repository** | [github.com/lobehub/lobehub](https://github.com/lobehub/lobehub) |
| **Status** | `Active` — last commit 2026-05-25; early development, actively evolving |
| **Openness** | `Source available (LobeHub Community License)` — based on Apache-2.0 with commercial derivative-work restrictions |
| **Deployment** | `Hybrid` — cloud service with self-hosted option (Vercel, Docker, Alibaba Cloud) |
| **First release** | Unknown |
| **Last release / commit** | 2026-05-25 (last release) |
| **Language / Stack** | TypeScript (Next.js + Vite SPA); pnpm monorepo |
| **License** | LobeHub Community License |

## What It Does

LobeHub is a work-and-lifestyle space to find, build, and collaborate with agent teammates that grow with you. It treats agents as the unit of work, providing an infrastructure where humans and agents co-evolve. You can hire agents via the Agent Builder, schedule them to run at specific times, organize them into projects and workspaces, and let them collaborate in parallel through shared pages with full context.

## Key Mechanisms

- **Chief Agent Operator**: A unified layer that hires, schedules, and reports on an entire AI team operating 7×24.
- **Agent Groups for parallel collaboration**: The system assembles the right agents for a task, enabling parallel work and iterative improvement with shared context.
- **Personal Memory with white-box editing**: Structured, editable memory that learns from how you work, giving you full control over what agents remember.
- **10,000+ skills via MCP-compatible plugins**: Connect agents to everyday tools through a large plugin library and custom plugin SDK.
- **Project / Workspace / Page organization**: Structured work areas — Pages for content refinement, Projects for tracking, Workspaces for team-wide visibility.

## Agent Architecture

- **Agent model**: Multi-agent peer (agent teammates) + human-in-loop
- **Coordination mechanism**: Schedule-based and event-driven agent group assembly with shared context pages; IM gateway for chat-based agent interaction
- **Human oversight**: Humans define goals, configure agents, review outputs, and administer workspace permissions

## Data & Storage Model

- **Primary store**: Cloud (hosted) or self-hosted — state lives in the deployment you control
- **Data portability**: Unknown — no documented export format
- **Offline capability**: No — requires connectivity even in self-hosted mode (relies on external LLM APIs)
- **Vendor lock-in risk**: **Medium** — plugin ecosystem and memory are platform-specific; source available reduces risk but license restricts derivative works without permission

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Self-hosted | $0 | Bring your own API keys and infrastructure |
| Cloud | Unknown | Not publicly documented |

## Ecosystem & Integrations

- **LLM providers**: OpenAI (primary); customizable model list and proxy URL support; other providers via configuration
- **Plugins**: 10,000+ tools, MCP-compatible, with plugin development SDK and gateway
- **Deploy options**: Vercel, Zeabur, Sealos, RepoCloud, Alibaba Cloud, Docker Compose
- **Related projects**: Lobe UI, Lobe Icons, Lobe TTS, Lobe i18n, Lobe Commit
- **Community**: GitHub Issues, GitHub Discussions

## Screenshots / Demo

- [GitHub README (includes demo video)](https://github.com/lobehub/lobehub)

## References

- [Official documents](https://github.com/lobehub/lobehub/tree/canary/docs)
- [Changelog](https://github.com/lobehub/lobehub/blob/canary/CHANGELOG.md)
- [Blog](https://github.com/lobehub/lobehub/discussions/categories/blog)
