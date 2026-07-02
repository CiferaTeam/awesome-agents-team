# Octo

> Open-source, AI-native team collaboration platform where humans and AI agents work together in shared channels, threads, and spaces.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [github.com/Mininglamp-OSS](https://github.com/Mininglamp-OSS) |
| **Repository** | [github.com/Mininglamp-OSS/octo-server](https://github.com/Mininglamp-OSS/octo-server) (backend) / [github.com/Mininglamp-OSS/octo-web](https://github.com/Mininglamp-OSS/octo-web) (client) |
| **Status** | `Active` — 345 combined GitHub stars (server 163 + web 182); latest releases server v1.7.1 / web v1.5.1 |
| **Openness** | `Open source (Apache-2.0)` |
| **Deployment** | `Self-hosted` — on-premise / private cloud; Docker Compose stack available |
| **First release** | 2026-05-11 |
| **Last release / commit** | 2026-06-29 (v1.7.1 / v1.5.1) |
| **Language / Stack** | Go (server), TypeScript / React / Electron (web + desktop) |
| **License** | Apache-2.0 |

## What It Does

Octo is an open-source workplace built for human-AI agent collaboration. Instead of treating AI as a personal assistant isolated on each user's machine, Octo puts agents directly into the team collaboration layer. Agents join channels, pick up tasks, participate in discussions, and deliver work alongside human teammates through the same chat interface. The platform is designed around the idea that individual agents are already capable, but organizations need a coordination layer to make them work as one team.

## Key Mechanisms

- **Shared collaboration primitives** — Spaces → Categories → Channels → Threads hierarchy mirrors real team organization. Humans and agents share the same channels, threads, and tasks; no separate AI interface
- **Lobster agents** — OpenClaw-powered digital doubles that do the thinking and execution while humans focus on judgment ("taste"). Each agent has an AgentCard and work history with clear ownership
- **IM as distribution layer** — Real-time messaging (WuKongIM) is the coordination backbone. Pull an agent into a channel and it is live; capability distribution shifts from individual to organization level
- **Six collaboration modes** — Solo, Roundtable, Critic, Pipeline, Split, and Swarm. Context flow between agents is controlled so multiple specialized bots can collaborate under human guidance
- **Matter workflow** — Actionable discussions are turned into traceable work items (Matters) with owners, deliverables, and acceptance records from brief to conclusion
- **group.md facilitation** — Shared markdown documents co-authored under AI guidance for structured alignment: kickoffs, requirement syncs, retrospectives, decision reviews
- **Adapters ecosystem** — Self-contained adapters bridge Octo to Slack, Discord, Feishu, Telegram, OpenAI, Anthropic, Claude Agent SDK, OpenClaw channels, and webhook sinks. Agents can reach users wherever they already work
- **Browser extension (Cmd+K)** — Pull webpage content with full context (URL, title, selection) into Octo and hand it to an agent without requiring upstream tools to integrate
- **Voice input** — Context-aware voice transcription and voice-driven editing for faster intent expression
- **Three laws for agents** — (1) never harm fundamental rights or dignity; (2) transparent loyalty to owner; (3) respect knowledge creators. Public knowledge is free, internal knowledge credits creators, personal tacit knowledge is protected

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Multi-agent team — Lobster agents join spaces/channels as first-class participants alongside humans. Agents can be assigned to Matters, participate in threads, and coordinate through six collaboration modes |
| **Coordination mechanism** | IM-based distribution: WuKongIM real-time messaging with channel/thread hierarchy. Server orchestrates agent routing, session management, and tool-call execution. Context visibility is controlled per mode (Solo/Roundtable/Critic/Pipeline/Split/Swarm) |
| **Human oversight** | Humans own agents, review outputs, and confirm Matter creation. "Taste" is the human role: judgment, discernment, and final decisions. Three laws constrain agent behavior; transparent AgentCard and work history provide accountability |

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | Self-hosted MySQL-compatible database + object storage; data stays on user's infrastructure. WuKongIM handles real-time messaging |
| **Data portability** | **High** — Apache-2.0 open source; data stored in standard SQL/object storage. Work history and Matters are exportable records |
| **Offline capability** | Partial — self-hosted deployment can run on local infrastructure; real-time collaboration requires network between participants |
| **Vendor lock-in risk** | **Low** — open source (Apache-2.0), self-hostable, adapters for multiple IM/AI providers. Local-first design: anything that can run on the user's own machine should |

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source / self-hosted | $0 | Free platform; bring your own LLM/API keys and infrastructure |

## Ecosystem & Integrations

- **AI agents / providers**: OpenClaw (Lobster), Claude Code, Hermes, Codex, OpenAI, Anthropic, Claude Agent SDK
- **Chat platforms**: Slack, Discord, Feishu (Lark), Telegram (via adapters)
- **Productivity tools**: Browser extension for arbitrary webpages; webhook sinks; extensible adapter model
- **Deployment**: Docker Compose stack at `Mininglamp-OSS/octo-deployment`; Web app, desktop (Electron), mobile (iOS/Android), browser extension, CLI
- **Related Mininglamp projects**: Mano-P on-device GUI agent model; Cider inference acceleration SDK
- **Community**: Discord server with general, help, project, development, and bot ecosystem channels

## Screenshots / Demo

- [Mininglamp-OSS GitHub organization](https://github.com/Mininglamp-OSS)
- [Octo server repository — README with quickstart](https://github.com/Mininglamp-OSS/octo-server)
- [Octo adapters repository](https://github.com/Mininglamp-OSS/octo-adapters)

## References

- [Octo server (Go backend)](https://github.com/Mininglamp-OSS/octo-server)
- [Octo web/desktop client](https://github.com/Mininglamp-OSS/octo-web)
- [Octo adapters](https://github.com/Mininglamp-OSS/octo-adapters)
- [Mininglamp open-sources Octo — Dev.to](https://dev.to/mininglamp/mininglamp-open-sources-octo-designing-the-collaboration-layer-for-multi-agent-teams-2o04)
- [明略科技开源 Octo — CSDN](https://agent.csdn.net/6a42138e10ee7a33f283a964.html)
