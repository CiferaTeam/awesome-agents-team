# Hivekeep

> Self-hosted platform to run a team of specialized AI agents that collaborate, remember, and build their own tools — reachable from a web UI and from Telegram, Slack, Discord, and Matrix.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [hivekeep.app](https://hivekeep.app) |
| **Repository** | [github.com/MarlBurroW/hivekeep](https://github.com/MarlBurroW/hivekeep) |
| **Status** | `Active` |
| **Openness** | `Open source (MIT)` |
| **Deployment** | `Self-hosted` |
| **First release** | 2026-06 |
| **Last release / commit** | 2026-07 |
| **Language / Stack** | TypeScript, Bun, SQLite |
| **License** | MIT |

## What It Does

Hivekeep is a self-hosted platform for running a team of specialized AI agents. Each agent has persistent long-term memory, its own toolset, and can collaborate with the other agents to complete tasks. Agents can extend themselves by building their own tools, mini-apps, and plugins, and they are reachable both from a built-in web UI and from chat channels (Telegram, Slack, Discord, Matrix). It ships as a single container backed by Bun and SQLite, so a full multi-agent setup runs on one small host with no external services.

## Key Mechanisms

- **Specialized agent team**: Multiple named agents, each with its own role, system prompt, memory, and tools; they delegate to and message each other.
- **Persistent memory**: Long-term memory per agent (facts, preferences, decisions) with scoped sharing across agents.
- **Self-built tooling**: Agents can author their own tools, sidebar mini-apps, and plugins at runtime instead of being limited to a fixed toolset.
- **Multi-channel reach**: The same agents answer from a web UI and from Telegram, Slack, Discord, and Matrix.
- **Single-container deploy**: Bun + SQLite in one container; no separate database or vector service required.

## Agent Architecture

- **Agent model**: Multi-agent peer team with delegation (an agent can spawn sub-tasks and hand work to specialists)
- **Coordination mechanism**: Inter-agent messaging (request/inform) plus shared memory and a shared contact/registry layer
- **Human oversight**: Humans configure agents, approve tool/permission grants, and can be prompted for input mid-task; all activity is visible in the web UI

## Data & Storage Model

- **Primary store**: Local SQLite (single file), with an encrypted vault for secrets
- **Data portability**: All state lives in the local data directory; the SQLite database and files can be copied/backed up directly
- **Offline capability**: Runs fully self-hosted; only the chosen LLM provider requires network access
- **Vendor lock-in risk**: Low — MIT-licensed, self-hosted, provider-agnostic (any OpenAI-compatible or supported LLM backend)

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source / self-hosted | $0 | Self-host the container; bring your own model API keys |

## Ecosystem & Integrations

- **LLM providers**: Provider-agnostic; OpenAI, Anthropic, Gemini, and any OpenAI-compatible endpoint
- **Messaging platforms**: Telegram, Slack, Discord, Matrix
- **Extensibility**: Agent-authored tools, sidebar mini-apps, plugins, and MCP support
- **Community**: [GitHub Issues](https://github.com/MarlBurroW/hivekeep/issues)

## Screenshots / Demo

- [GitHub README (screenshots and quickstart)](https://github.com/MarlBurroW/hivekeep)
- [Project site](https://hivekeep.app)

## References

- [Hivekeep on GitHub](https://github.com/MarlBurroW/hivekeep)
- [Hivekeep project site](https://hivekeep.app)
