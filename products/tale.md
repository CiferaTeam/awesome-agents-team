# Tale

> Open-source project workspace where teams delegate tasks to AI agents and review their reports and deliverables.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [tale.dev](https://tale.dev) |
| **Repository** | [github.com/tale-project/tale](https://github.com/tale-project/tale) |
| **Status** | `Active` |
| **Openness** | `Open source (MIT)` |
| **Deployment** | Self-hosted or managed Cloud |
| **First release** | 2026-02 — v0.1.0 |
| **Last release / commit** | 2026-10 — v0.5.70 |
| **Language / Stack** | TypeScript, Postgres, S3-compatible storage, containerized agent runtimes |
| **License** | MIT |

## What It Does

Tale organizes work into shared projects, tasks, agent configurations, and reviewable outputs. Teams supply a brief and acceptance criteria, start an appropriately equipped agent, and inspect its report and collected files. It supports multiple coding runtimes and model providers; availability depends on the deployment, credentials, and sandbox capacity.

## Key Mechanisms

- **Persistent execution workspaces**: Project agents reuse workspace files across tasks. Runtime allocation and file retention have separate lifecycles; stopping work does not mean deleting its files.
- **Explicit equipment**: Agents receive selected skills, tools, connectors, and secret grants. Connector broker actions exposed to agents are read-only; direct tooling and explicitly granted secrets have separate access paths.
- **Task-based handoffs**: Agent reports and deliverables stay attached to tasks. Assignment alone does not start execution; a human or an authorized agent must initiate work.

## Agent Architecture

- **Agent model**: Multiple project agents with human oversight; optional manager and reviewer capabilities require explicit grants.
- **Coordination mechanism**: Shared project/task state, comments, and controlled delegation. An agent started by another agent cannot start further agents.
- **Human oversight**: People configure access, provide guidance, and review results. Required human competences and workflow approvals remain protected when an agent reviews another agent's result.

## Data & Storage Model

- **Primary store**: Postgres for application and knowledge data, S3-compatible storage for files, and organization configuration files. Self-hosted operators control those services.
- **Data portability**: Documented database, configuration, and volume backup/restore procedures. External stores and sandbox workspace files require separate backup coverage; a universal cross-product export format is not documented.
- **Offline capability**: Unknown as a complete supported mode. Self-hosting alone does not make model calls, connectors, or web retrieval independent of the network.
- **Vendor lock-in risk**: Lower for infrastructure ownership because the application is MIT-licensed and self-hostable; migration to another product still requires translating Tale's application schema and workflows.

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Community, self-hosted | $0 software license | Operator supplies infrastructure and pays chosen model providers. |
| Enterprise | Per service agreement | Managed Cloud or supported self-hosting; professional services and support. |

Community and Enterprise share the product features. Hosting and model usage are separate costs; operational usage totals are not invoices.

## Ecosystem & Integrations

- **Agent runtimes**: Documented choices include Claude Code, Codex, Cursor, Gemini CLI, Hermes, OpenClaw, OpenCode, Pi, and Qwen Code, with different credential and tool capabilities.
- **External services**: Configured connectors and separately granted GitHub tooling; provider access follows the selected runtime's supported path.
- **API / extensibility**: REST, an authenticated MCP endpoint for organization knowledge and automation tools, and WebDAV for documents. The MCP endpoint belongs to each deployment and requires an API key and organization scope.
- **Community**: [GitHub issues](https://github.com/tale-project/tale/issues).

## Compared with GitIM

GitIM uses a Git repository as the shared backend for channels, messages, and cards, with plain-text history. Tale runs an application service with databases, file storage, and a sandbox execution plane. GitIM suits teams that want Git-native collaboration primitives and their own workflow conventions; Tale supplies a project-task execution and review workflow but requires operating that service stack or using managed hosting.

## Screenshots / Demo

- [Project agent setup, with screenshots](https://docs.tale.dev/platform/projects/project-agents)

## References

- [Source and license](https://github.com/tale-project/tale)
- [Releases](https://github.com/tale-project/tale/releases)
- [Project agents](https://docs.tale.dev/platform/projects/project-agents)
- [Runtime choices](https://docs.tale.dev/platform/agents/harnesses)
- [Sandbox lifecycle](https://docs.tale.dev/platform/admin/sandboxes)
- [Self-hosted architecture](https://docs.tale.dev/self-hosted/overview)
- [Backup coverage](https://docs.tale.dev/self-hosted/operate/backups-and-restore)
- [Cloud billing](https://docs.tale.dev/cloud/billing)
- [MCP endpoint](https://docs.tale.dev/develop/mcp-endpoint)
- [GitIM's architecture and collaboration model](https://github.com/CiferaTeam/GitIM)
