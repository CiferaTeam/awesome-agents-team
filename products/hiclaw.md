# HiClaw

> Enterprise-grade multi-agent collaboration system — Manager Agent coordinates Worker Agents via Matrix rooms, with human visibility and real-time intervention built in.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [hiclaw.io](https://hiclaw.io/) / [hiclaw.org](http://hiclaw.org/) |
| **Repository** | [github.com/agentscope-ai/HiClaw](https://github.com/agentscope-ai/HiClaw) (migrated from alibaba/hiclaw) |
| **Status** | `Active` — last commit 2026-05-25; actively developed with frequent releases |
| **Openness** | `Open source (Apache-2.0)` |
| **Deployment** | `Self-hosted` — Docker-based local or private deployment; built-in Tuwunel Matrix homeserver |
| **First release** | 2026-02-21 (repo created) |
| **Last release / commit** | 2026-05-25 (last commit) |
| **Language / Stack** | TypeScript / JavaScript (built on OpenClaw agent framework); Docker; Higress AI Gateway |
| **License** | Apache-2.0 |

## What It Does

HiClaw is an open-source multi-agent collaboration system initiated by the Higress community (Alibaba Cloud). It transforms standalone AI agents into a supervised, collaborative team by introducing a Manager Agent that acts as an AI chief of staff. The Manager creates Worker Agents on demand, assigns tasks, monitors progress via heartbeat checks, and reports results back to the human operator. All communication flows through the open Matrix instant messaging protocol, making every interaction transparent and auditable — humans can enter any Matrix room at any time to observe, intervene, or redirect.

HiClaw is positioned as the "Team edition of OpenClaw," designed for enterprises and solo operators who need secure, scalable AI-driven automation with full visibility.

## Key Mechanisms

- **Manager-Worker architecture**: A two-tier system where the Manager Agent decomposes tasks and coordinates multiple specialized Worker Agents (frontend, backend, QA, content) for parallel execution.
- **Matrix protocol communication**: All agent-to-agent and human-to-agent communication happens in visible Matrix Rooms. Native support for distributed deployment and federation via the open Matrix standard.
- **Higress AI Gateway security**: Real API keys (LLM providers, GitHub PATs) are stored exclusively in the Higress AI Gateway. Workers carry only scoped consumer tokens — even a compromised Worker cannot leak credentials.
- **Heartbeat-based health monitoring**: The Manager monitors Worker status via heartbeat checks and can recreate or reassign tasks when Workers fail.
- **CoPaw Worker integration**: HiClaw 1.0.4+ supports CoPaw Workers for lighter memory footprint and local-mode browser operations.
- **One-command install**: `bash <(curl -sSL https://higress.ai/hiclaw/install.sh)` for interactive setup; Docker-based deployment.

## Agent Architecture

- **Agent model**: Multi-agent hierarchical (Manager + Workers) with human-in-the-loop
- **Coordination mechanism**: Manager Agent compiles tasks into sub-assignments, distributes to Workers via Matrix rooms, collects results, and reports to humans. Workers call Skills and MCP tools to execute assignments.
- **Human oversight**: Humans can observe any Matrix room in real time, intervene with corrections or redirects, and approve/reject task outcomes. All conversations are transparent by design — no black box.
- **Security model**: Gateway holds all secrets; Workers run in isolated containers with least-privilege consumer tokens; per-consumer route-level access control enforced by Higress.

## Data & Storage Model

- **Primary store**: Self-hosted — local Docker volumes for agent state, conversation history, and configuration. Matrix homeserver (Tuwunel) manages message persistence.
- **Data portability**: **High** — Matrix protocol is open and standardized; conversations and room state can be exported via Matrix tools. Agent configurations are plain files.
- **Offline capability**: **Partial** — core system runs locally with local or remote LLM APIs. Some features (cloud model access) require connectivity.
- **Vendor lock-in risk**: **Low** — open source (Apache-2.0), model-agnostic via Higress gateway (supports Alibaba Qwen, OpenAI, Anthropic Claude, and more), built on open Matrix protocol. No proprietary agent communication format.

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source | $0 | Unlimited; self-build and self-host from source |

HiClaw is fully open source with no paid tiers. A commercial version on Alibaba Cloud has been announced as "coming soon" (note: any xxxClaw on Alibaba Cloud is explicitly not the commercial version of HiClaw per official statements).

## Ecosystem & Integrations

- **LLM providers**: Alibaba Cloud Qwen, OpenAI, Anthropic Claude, DeepSeek, and any provider accessible via Higress AI Gateway
- **Agent frameworks**: Built on OpenClaw; fully compatible with OpenClaw Skills ecosystem and MCP tooling
- **Matrix clients**: Element, FluffyChat, or any Matrix-compatible client on iOS, Android, or desktop for mobile team management
- **Alibaba Cloud integration**: Commercial version will leverage AI Gateway, MSE Nacos, ACS Container Compute Service, OSS, and SLS
- **AgentScope ecosystem**: HiClaw is part of the AgentScope family alongside CoPaw (personal assistant), AgentScope-Runtime, AgentScope-Studio, and ReMe (memory framework)
- **Community**: GitHub Issues, GitHub Discussions, DingTalk group (167365014834), WeChat group (QR code on GitHub README)

## Screenshots / Demo

- [hiclaw.io — homepage and quick start](https://hiclaw.io/)
- [HiClaw GitHub README — architecture diagram and install guide](https://github.com/agentscope-ai/HiClaw)
- [hiclaw.org — documentation and FAQ](http://hiclaw.org/)

## References

- [HiClaw GitHub repository](https://github.com/agentscope-ai/HiClaw)
- [HiClaw homepage (hiclaw.io)](https://hiclaw.io/)
- [HiClaw documentation (hiclaw.org)](http://hiclaw.org/)
- [HiClaw joins AgentScope — Alibaba Cloud blog](https://www.alibabacloud.com/blog/603006)
- [AgentScope organization](https://github.com/agentscope-ai)
- [CoPaw repository](https://github.com/agentscope-ai/CoPaw)
- [Higress AI Gateway](https://higress.ai/)
