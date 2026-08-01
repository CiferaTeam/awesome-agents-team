# CodexLoom

> Long-lived Codex domain agents woven into a governed agent organization: each agent owns a durable domain, teams collaborate through agent-to-agent Messages and Topics, and Interface Agents deliver capabilities outward.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [codexloom.ai](https://codexloom.ai/) |
| **Repository** | [github.com/yan5xu/codexloom](https://github.com/yan5xu/codexloom) |
| **Status** | `Active` — 52 stars, 4 forks; no GitHub Release yet; last push 2026-08-01 |
| **Openness** | `Source available (Elastic License 2.0)` — source-available, not OSI open source |
| **Deployment** | `Self-hosted` — local-first; runs from source with the `codex` CLI, WebUI at localhost:4870 |
| **First release** | No GitHub Release yet — first tag `v0.1.0-dev.1` (2026-07-16) is a checkpoint milestone |
| **Last release / commit** | No GitHub Release yet — latest main commit `0797c1f2` (2026-08-01) |
| **Language / Stack** | Go, Codex-native |
| **License** | Elastic License 2.0 (ELv2) |

## What It Does

CodexLoom turns a Codex thread into the continuing workspace of a long-lived Domain Agent, then adds durable identity, Profile, Team relationships, bounded coordination, human governance, and governed external delivery. Instead of organizing code agents around one-off tasks, it keeps agents responsible for a domain over time, so later work resumes from accumulated context instead of restarting cold.

## Key Mechanisms

- **Long-lived Domain Agents**: A stable ID, name, Profile, and primary Thread define who the agent is and what it remains responsible for; the thread carries the work trajectory across tasks.
- **Agent-to-agent communication**: `loom` CLI discovery, delivery, queuing, replies, and status inspection over Messages with preserved delivery state and response relationships.
- **Governed team structure**: Organization, Collaboration, and Activity maps separate formal responsibility, declared cross-domain work, and message evidence; Lead / Internal Agent / Interface Agent are organizational patterns.
- **Bounded coordination**: Topics coordinate cross-agent work across turns and time; managed Artifacts hand off files; Needs You requests explicit Owner decisions.
- **Interface Agents**: Governed external boundaries (Feishu, Slack, Parall) route scoped work to Domain Agents with authorization and disclosure controls.
- **Continuous operations**: Schedules, durable external Triggers, backups, and graceful restart after active turns finish.

## Agent Architecture

- **Agent model**: Multi-agent hierarchical (Lead coordinates Internal Agents) + human-in-loop
- **Coordination mechanism**: Agent-to-agent Messages with queuing/replies, Topics for bounded coordination, managed Artifact handoffs; Profile serves as a discoverability and collaboration contract
- **Human oversight**: Owner sets Profiles, relationships, and Conversation Memberships; explicit Needs You decisions; authorization and information boundaries on external delivery

## Data & Storage Model

- **Primary store**: Local — Codex thread history plus CodexLoom state for agents, Profiles, Messages, Topics, and runtime; backups on demand
- **Data portability**: High — thread history is Codex-native; state is local and backed up on demand
- **Offline capability**: Yes — local-first runtime; model access depends on the Codex account / local models
- **Vendor lock-in risk**: Low — self-hosted and local-first; depends on Codex (the agent runtime and clients), with source-available code under ELv2

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Self-hosted | $0 | Requires the `codex` CLI and a ChatGPT account; source-available under ELv2 |

## Ecosystem & Integrations

- **Agent runtime**: Built on Codex — Codex provides threads, the agent runtime, and Desktop/Mobile clients
- **CLI**: `loom` for agent create, profile set, thread send, and cross-agent messaging
- **External platforms**: Feishu (Lark), Slack, Parall via Interface Agents (Microsoft Teams TODO)
- **Surfaces**: Codex Desktop / Mobile, CodexLoom WebUI, and the `loom` CLI
- **Community**: CodexLoom Feishu community

## Screenshots / Demo

- [GitHub README with visual identity and product description](https://github.com/yan5xu/codexloom#readme)
- [English documentation map](https://github.com/yan5xu/codexloom/blob/main/docs/README.md)

## References

- [GitHub repository](https://github.com/yan5xu/codexloom)
- [Official website](https://codexloom.ai/)
- [Owner guide (English)](https://github.com/yan5xu/codexloom/blob/main/docs/owner-guide.md)
- [Documentation map (English)](https://github.com/yan5xu/codexloom/blob/main/docs/README.md)
- [License (Elastic License 2.0)](https://github.com/yan5xu/codexloom/blob/main/LICENSE)
