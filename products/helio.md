# Helio

> AI-native team workspace where AI teammates sit in the same channels, take the same tickets, and ship the same work as human collaborators.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [helio.im](https://helio.im/) |
| **Repository** | `Closed source` — no public GitHub org/repo found |
| **Status** | `Active` — macOS desktop app available; web app at app.helio.im; Windows listed as coming soon |
| **Openness** | `Commercial` — no public pricing page; free tier status unverified |
| **Deployment** | `Cloud-hosted` — macOS desktop app and web app; no self-host or local-first option advertised |
| **First release** | Unknown |
| **Last release / commit** | Unknown |
| **Language / Stack** | Supports Claude Code, Codex, Custom MCP, and Docker as agent runtimes; backend stack unverified |
| **License** | Proprietary |

## What It Does

Helio positions AI as full teammates rather than sideline tools: named AI agents (e.g. Ada, Hopper) inhabit the same channels and task queues as human team members, pick up tickets, write code, submit PRs for review, and handle async work like email drafting. Humans retain control through approval workflows that gate high-risk actions. The goal is to eliminate context-switching between a separate AI assistant and the team's actual work surface.

## Key Mechanisms

- **Named AI teammates**: Each AI has a named persona and role (e.g. Ada for coding, Hopper for other workflows) rather than being a generic assistant invoked on demand.
- **Unified channel model**: Humans and AI share the same channels and task assignments — no separate AI sidebar or chatbot interface.
- **Approval gates**: High-risk agent actions (e.g. sending emails, deploying) require explicit human sign-off before execution.
- **Flexible agent runtimes**: Supports Claude Code, Codex, Custom MCP servers, and Docker as the underlying execution environment.
- **Chat adapter layer**: Connects to Slack, Lark (Feishu), Microsoft Teams, and Discord to surface Helio agents in existing team chat without migration.

## Agent Architecture

- **Agent model**: Multi-agent with role specialization — distinct named AI teammates per function
- **Coordination mechanism**: Shared channels and task queue; agents pick up tickets and submit artifacts (PRs, drafts) into existing workflows
- **Human oversight**: Approval workflow layer for high-risk actions; humans review AI-submitted PRs and drafts before merge/send

## Data & Storage Model

- **Primary store**: Cloud — Helio hosts channel and task state; no local-first or self-host option described on site
- **Data portability**: Unverified — no export documentation found
- **Offline capability**: No — requires connectivity; cloud-hosted coordination surface
- **Vendor lock-in risk**: **Medium–High** — team coordination history (channels, task assignments, AI interactions) lives on Helio's platform; no Git-native or file-native audit trail described

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Unknown | Unknown | No public pricing page found on helio.im |

Contact: hello@helio.im

## Ecosystem & Integrations

- **Chat adapters**: Slack, Lark (Feishu), Microsoft Teams, Discord
- **Agent runtimes**: Claude Code, Codex, Custom MCP, Docker
- **Dev tools**: GitHub (PR submission), Linear (tickets), Vercel (deploy)
- **Communication**: Gmail/SES (email drafting), Zoom, Google Meet (meeting transcription, listed as coming soon)
- **API / extensibility**: MCP (Model Context Protocol) supported as a custom runtime option
- **Community**: No public Discord, forum, or docs site found — contact via hello@helio.im

## Screenshots / Demo

- [Homepage](https://helio.im/) — product positioning, teammate demos, integration list
- [Web app](https://app.helio.im/) — sign-up / login (content requires account)

## vs GitIM

| Dimension | Helio | GitIM |
|-----------|-------|-------|
| Primary use case | AI teammates embedded in team channels and task queues | Multi-human, multi-coding-agent coordination over a Git workspace |
| Data ownership | Cloud platform — coordination state on Helio servers | Git repository — coordination and artifacts user-owned |
| Agent coordination | Shared channels + task assignment; approval gates | Async Git events, channels, cards — commit-backed audit trail |
| Offline / local-first | Cloud-only | Git-native offline until push |
| Openness | Closed source, proprietary | Open coordination model tied to Git |
| Team collaboration UX | Familiar chat-adjacent UX; works inside Slack/Teams via adapters | Commit/channel model for developers; steeper for non-devs |
| Ecosystem | Dev tools (GitHub, Linear, Vercel) + chat platforms | CI, PR, IDE, entire Git toolchain |

**Summary:** Helio fits teams that want AI embedded in their existing chat and task surfaces with minimal workflow change. GitIM fits teams where the coordination record must live in Git and be auditable across humans and coding agents.

## References

- [Helio homepage](https://helio.im/)
- [@helioim_ai on X](https://x.com/helioim_ai)
