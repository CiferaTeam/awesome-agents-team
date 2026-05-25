# Synapse (zai-org)

> Self-hosted AI workspace with shareable AI teammates, shared conversations, memory, and governed access to plugins, MCP tools, and local devices. **Early phase — schema and runtime protocol may change rapidly.**

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [github.com/zai-org/Synapse](https://github.com/zai-org/Synapse) |
| **Repository** | [github.com/zai-org/Synapse](https://github.com/zai-org/Synapse) |
| **Status** | `Active` — early phase; last commit 2026-05-20; schema and protocol subject to rapid change |
| **Openness** | `Open source (Apache-2.0)` |
| **Deployment** | `Self-hosted` — Web workspace with local execution; deploy via Docker or source |
| **First release** | Unknown — no tagged releases yet |
| **Last release / commit** | 2026-05-20 (last commit) |
| **Language / Stack** | TypeScript (primary); event-driven architecture with conversation-centric runtime |
| **License** | Apache-2.0 |

## What It Does

Synapse is a self-hosted AI collaboration workspace that treats conversation itself as the runtime. Humans, native platform Actors, and external Remote Agents share the same conversation boundary — with memory, permissions, plugins, MCP Relay tools, and event sources governed at the Workspace level. AI teammates can be shared across workspaces through a contact-like relationship network, rather than being isolated per-room bots.

## Key Mechanisms

- **Conversation-as-runtime**: The conversation is the collaboration boundary; participants, visibility, actor wakeups, execution context, and memory handoff all revolve around it.
- **Shareable AI teammates**: Workspace members, Actors, and Remote Agents can be shared across workspaces and added via a contact-style relationship graph.
- **Governed resource layer**: Plugins, skills, MCP Relay capabilities, and event sources are Workspace-level resources that can be explicitly authorized, audited, and revoked.
- **Cloud collaboration, local execution**: Teams coordinate in the web workspace, but execution can fall back to local browsers, desktops, filesystems, intranet services, or external agent runtimes.

## Agent Architecture

- **Agent model**: Multi-agent peer (native Actors + bridged Remote Agents) + human-in-loop
- **Coordination mechanism**: Conversation-centric session runtime with actor wakeups, session context, and event-driven automation; IM transport and external webhooks bind back into the same conversation model
- **Human oversight**: Resource access is explicitly authorized per Workspace; humans participate as conversation members and control plugin/MCP scope

## Data & Storage Model

- **Primary store**: Self-hosted — conversation state, memory, and resource runtime managed by the Synapse server; local execution falls back to user devices
- **Data portability**: Unknown — no documented export format as of early phase
- **Offline capability**: Partial — local execution paths work offline; web workspace and sync require server connectivity
- **Vendor lock-in risk**: **Low** — self-hosted by design; source code is Apache-2.0

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Self-host | $0 (Apache-2.0) | Unlimited; requires own infrastructure |

## Ecosystem & Integrations

- **Agent types**: Native Actors (Synapse-managed) and Remote Agents (bridged external runtimes)
- **Tool access**: Plugins, MCP Relay, local devices, event sources
- **Transport**: Web chat, remote-agent bridge, IM transport (external endpoints bind into conversations)
- **Automation**: Scheduled tasks, custom webhooks, GitHub/GitLab integrations
- **Community**: GitHub Issues at [zai-org/Synapse](https://github.com/zai-org/Synapse/issues)

## Screenshots / Demo

- [GitHub README (includes architecture diagram)](https://github.com/zai-org/Synapse)

## References

- [zai-org/Synapse on GitHub](https://github.com/zai-org/Synapse)
- [Deploy documentation](https://github.com/zai-org/Synapse/blob/main/deploy.md)

---
