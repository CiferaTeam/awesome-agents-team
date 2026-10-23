# Agent Barn

> Open-source (Apache-2.0) control plane for running AI agent teams on your own Kubernetes cluster.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [agentbarn.dev](https://agentbarn.dev) |
| **Repository** | [github.com/aai-labs/agent-barn](https://github.com/aai-labs/agent-barn) |
| **Status** | `Active` |
| **Openness** | `Open source (Apache-2.0)` |
| **Deployment** | `Self-hosted` (Kubernetes via Helm); hosted cloud option |
| **First release** | 2026 |
| **Last release / commit** | 2026-10 |
| **Language / Stack** | Python, Kubernetes, Helm |
| **License** | Apache 2.0 |

## What It Does

Agent Barn is a control plane for AI agents. Team members talk to agents in the chat tools they already use (Slack, Teams, Telegram, Discord, email, web chat), and agents do work across connected tools like Jira, GitHub and Confluence. Every conversation, tool call, log and cost is recorded in one place, so teams get a single audited view of what their agents did.

## Key Mechanisms

- **Multi-channel front ends**: Slack, Teams, Telegram, Discord, email and web chat all route into the same control plane.
- **Full audit trail**: every conversation, tool call, log and cost is recorded for review.
- **Runtime orchestration on Kubernetes**: runs agent runtimes like Hermes and OpenClaw on your own cluster, deployed with Helm.

## Agent Architecture

- **Agent model**: Multi-agent teams under one control plane, human-in-loop through chat channels
- **Coordination mechanism**: central control plane routes conversations and tasks to agent runtimes; agents act through connected work tools
- **Human oversight**: humans interact with agents directly in their chat tools and can review the complete audit log of actions, tool calls and costs

## Data & Storage Model

- **Primary store**: self-hosted on the user's own Kubernetes cluster
- **Data portability**: self-hosted deployment keeps data on user infrastructure
- **Offline capability**: N/A - requires the cluster and model providers
- **Vendor lock-in risk**: Low - open source (Apache-2.0), self-hosted, standard Kubernetes/Helm deployment

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Self-hosted (OSS) | $0 | Full control plane on your own cluster |
| Cloud | Free tier | Limited usage |
| Pilot | $1,000 | Pilot program |

## Ecosystem & Integrations

- **Chat platforms**: Slack, Microsoft Teams, Telegram, Discord, Email, Web Chat
- **External services**: Jira, GitHub, Confluence and more
- **Agent runtimes**: Hermes, OpenClaw
- **API / extensibility**: Open-source codebase (Python) deployable via Helm charts

## Screenshots / Demo

- [Homepage](https://agentbarn.dev)

## vs GitIM

GitIM is a Git-native collaboration layer where channels, DMs and Kanban cards are plain-text commits with no server. Agent Barn is a server-based control plane focused on running agent runtimes (Hermes, OpenClaw) on Kubernetes with multi-channel chat front ends and centralized audit logging.

## References

- [Homepage](https://agentbarn.dev)
- [GitHub repository](https://github.com/aai-labs/agent-barn)
