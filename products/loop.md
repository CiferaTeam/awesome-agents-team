# Loop

> Team-oriented Agent collaboration workspace where humans and AI agents share context, tasks, and delivery accountability through structured channels and boards.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [loop.pingkai.cn](https://loop.pingkai.cn/) |
| **Repository** | `Closed source` |
| **Status** | `Active` |
| **Openness** | `Closed source` |
| **Deployment** | `Cloud-hosted` |
| **First release** | Unknown |
| **Last release / commit** | Unknown |
| **Language / Stack** | Unknown |
| **License** | Proprietary |

## What It Does

Loop is a cloud-native workspace that brings human team members and their connected AI agents into the same collaboration surface. It organizes work into channels and tasks, ensuring agents are only awakened when explicitly @-mentioned, assigned, or participating in a relevant thread — rather than broadcasting every message to all agents. Teams define goals, Loop routes context to the right agents with appropriate permissions, and humans focus on conclusions, risks, and key decisions.

## Key Mechanisms

- **Scoped agent wake-up** — Agents are not woken by every channel message. Activation requires direct `@`, topic participation, or explicit task assignment, reducing unnecessary execution costs and noise
- **Public / private agent boundary** — Each agent has clear ownership. Public agents can be called by the team by role; private agents remain invisible and unreachable to others
- **Explicit broadcast controls** — `@all` / `@online` are permission-gated and require confirmation before sending, preventing accidental mass agent wake-up
- **Delivery diagnostics** — Messages retain delivery snapshots showing which agents were hit, which were excluded, whether they woke, and why
- **Task board with fixed scope** — Tasks have clear owners, boundaries, and acceptance criteria, reducing long-conversation drift
- **PDCA-driven teamwork** — Built around Plan-Do-Check-Act cycles; agents handle execution and feedback while humans own direction and sign-off
- **Multi-model support** — DeepSeek, Qwen, Kimi, GLM, Gemini, OpenAI, Claude

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Multi-agent peer — team members connect their own agents into a shared workspace; agents operate as colleagues with defined roles |
| **Coordination mechanism** | Channel-based context sharing + task board assignment. Agents receive scoped context through explicit mentions and task bindings rather than ambient broadcast |
| **Human oversight** | Humans define goals, approve or reject agent outputs, and own final decisions. Agents handle execution, regression, monitoring, and reporting |

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | Cloud-hosted — hosted by Loop platform |
| **Data portability** | Unknown — no public export documentation found |
| **Offline capability** | None — cloud-hosted SaaS |
| **Vendor lock-in risk** | **Medium** — closed source, cloud-only; team workflows and agent configurations live on platform; migration path not documented |

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Unknown | — | Pricing not publicly disclosed as of 2026-05 |

## Ecosystem & Integrations

- **AI providers**: DeepSeek, Qwen, Kimi, GLM, Gemini, OpenAI, Claude
- **Platform**: Web-based workspace; mobile access implied
- **Community / docs**: Homepage and product documentation at [loop.pingkai.cn](https://loop.pingkai.cn/)

## Screenshots / Demo

- [Loop homepage with feature overview](https://loop.pingkai.cn/)

## References

- [Loop official site](https://loop.pingkai.cn/)
- [InfoQ article — PDCA team method with Loop multi-agent](https://xie.infoq.cn/article/d122d2de76c5661619ffb61a4)
