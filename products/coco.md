# COCO

> Build AI Teams. Deploy in Minutes. COCO provides managed AI agent teams and an open-source ecosystem for human-agent collaboration.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [coco.xyz](https://coco.xyz/) |
| **Repository** | Ecosystem: [github.com/coco-xyz](https://github.com/coco-xyz) — no single monorepo; open-source components include [hxa-connect](https://github.com/coco-xyz/hxa-connect), [zylos-core](https://github.com/zylos-ai/zylos-core), and channel plugins |
| **Status** | `Active` — marketing site live; open-source ecosystem last updated 2026-05-25 |
| **Openness** | `Closed source` (core Agent Cloud Service); open-source ecosystem under MIT |
| **Deployment** | `Cloud` — managed SaaS with one-click deploy; optional self-hosted open-source messaging hub (hxa-connect) |
| **First release** | 2025 *(inferred from customer case studies and ecosystem maturity)* |
| **Last release / commit** | 2026-05-25 (zylos-core open-source activity); cloud service changelog not public |
| **Language / Stack** | TypeScript / JavaScript (open-source components); cloud stack undisclosed |
| **License** | Proprietary (cloud service); MIT (hxa-connect, zylos-hxa-connect, openclaw-hxa-connect) |

## What It Does

COCO is a platform for building and deploying teams of AI agents. It offers a fully managed cloud service (Agent Cloud) where users spin up AI employees with assigned roles, skills, and channel integrations. Under the hood, COCO maintains an open-source ecosystem — HxA Connect for bot-to-bot messaging, Zylos for agent infrastructure, and plugins for OpenClaw — that powers both the commercial service and self-hosted deployments.

The product targets businesses that want to reduce manual coordination: a major state-owned bank reduced loan due diligence from 3 days to 2 hours with COCO agent teams, and COCO's own 6-person team runs 30+ AI agents daily via HxA Connect for code review, deployment, competitive analysis, and customer support.

## Key Mechanisms

- **Managed AI employees**: Cloud instances with standard or advanced AI computing, skill packages, and multi-channel access (Telegram, Lark, Slack, email). No API key required — fully managed model selection.
- **HxA Connect (Hexa)**: Lightweight, self-hostable messaging hub for bot-to-bot communication. Supports org-scoped DMs, structured collaboration threads with versioned artifacts, and real-time Web UI for human oversight.
- **Zylos agent runtime**: Open-source agent infrastructure compatible with the OpenClaw ecosystem. Unified session (one AI, one consciousness across all channels), 5-layer memory architecture, and component-based skill system.
- **OpenClaw interoperability**: COCO agents communicate with OpenClaw agents in real time via the HxA Connect B2B protocol, without custom bridges.
- **Team templates**: Pre-built human-agent collaboration templates for dev, sales, marketing, and other functions.

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Multi-agent team with specialized roles (e.g., frontend, backend, QA, content) coordinated by a manager layer; human-in-the-loop for direction and approval |
| **Coordination mechanism** | Cloud: centralized orchestration via COCO control plane. Self-hosted: peer-to-peer bot messaging via HxA Connect threads and DMs with artifact versioning |
| **Human oversight** | Humans define goals, review outputs, and intervene via the web dashboard or messaging channels. Manager agents report progress and escalate on blockers |
| **Multi-agent protocol** | HxA Connect B2B protocol for real-time agent-to-agent messaging; ThreadContext with @mention filtering and smart delivery |

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | Cloud service: data stored on COCO servers (details undisclosed). Self-hosted hxa-connect: SQLite-backed with zero external dependencies |
| **Data portability** | HxA Connect artifacts support text, markdown, JSON, code, file, and link types with versioning. No documented full export for cloud accounts |
| **Offline capability** | Self-hosted hxa-connect can run entirely locally. Cloud service requires connectivity |
| **Vendor lock-in risk** | **Medium-High** for cloud tier — managed service with proprietary orchestration; mitigated by open-source HxA Connect and Zylos for self-hosted migration |

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Air | $99/mo | 1 AI employee instance; standard AI computing; basic skill packages; all channels; email support |
| Pro | $449/mo | 1 AI employee instance; advanced AI computing; complete skill packages; all channels; priority support (24h response) |
| Ultra | $999/mo | 3 Pro AI employees; advanced AI computing + extended quota; complete + custom skill packages; dedicated CSM; priority support (4h response) |
| Enterprise | Custom (from $2,000/mo) | Unlimited instances; private deployment; deep integration; SLA guarantee; SSO/SAML |

Crypto payments (USDT/USDC) accepted in addition to Stripe cards.

## Ecosystem & Integrations

- **Messaging channels**: Telegram, Lark, Slack, email
- **Agent frameworks**: OpenClaw (via official hxa-connect plugin); Zylos (native)
- **LLM providers**: Fully managed — COCO selects optimal models; no user API key required
- **Open-source ecosystem**:
  - [HxA Connect](https://github.com/coco-xyz/hxa-connect) — bot-to-bot messaging server
  - [HxA Connect SDK](https://github.com/coco-xyz/hxa-connect-sdk) — TypeScript SDK
  - [zylos-core](https://github.com/zylos-ai/zylos-core) — open-source agent infrastructure
  - [openclaw-hxa-connect](https://github.com/coco-xyz/openclaw-hxa-connect) — OpenClaw channel plugin
  - [clawmark](https://github.com/coco-xyz/clawmark) — web annotation Chrome extension
- **Community**: GitHub Issues (open-source repos)

## Screenshots / Demo

- [coco.xyz — homepage with pricing and case studies](https://coco.xyz/)
- [HxA Connect README — architecture and API overview](https://github.com/coco-xyz/hxa-connect)

## References

- [COCO homepage](https://coco.xyz/)
- [COCO GitHub organization](https://github.com/coco-xyz)
- [Zylos Core repository](https://github.com/zylos-ai/zylos-core)
- [HxA Connect repository](https://github.com/coco-xyz/hxa-connect)
- [HxA Connect SDK](https://github.com/coco-xyz/hxa-connect-sdk)
