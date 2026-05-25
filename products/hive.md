# Hive (Aden)

> Multi-agent harness for production AI — state management, failure recovery, observability, and human oversight so agents actually run.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [adenhq.com](https://adenhq.com) |
| **Repository** | [github.com/aden-hive/hive](https://github.com/aden-hive/hive) |
| **Status** | `Active` — last commit 2026-05-22; actively developed with frequent releases |
| **Openness** | `Open source (Apache-2.0)` |
| **Deployment** | `Self-hosted` — Python runtime with web dashboard; deploy via Docker or source |
| **First release** | 2026-05-02 |
| **Last release / commit** | 2026-05-22 (last commit) |
| **Language / Stack** | Python 3.11+ (primary); uv workspace; LiteLLM for model routing; Next.js dashboard |
| **License** | Apache-2.0 |

## What It Does

Hive is a production-grade multi-agent execution harness. Instead of manually wiring agents together, you describe a goal in natural language and the runtime auto-generates a strict, graph-based execution DAG that coordinates specialized agents to execute tasks in parallel. It provides the runtime layer — session isolation, checkpoint-based crash recovery, cost enforcement, and real-time observability — that makes agents reliable enough to run real business processes rather than one-off demos.

## Key Mechanisms

- **Natural-language goal → auto-generated agent graph**: Describe an objective in plain English; the runtime compiles a strict DAG with specialized worker nodes, connection code, and test cases.
- **Self-healing graph execution**: On failure, the system captures the error, evolves the graph structure, and redeploys automatically without manual intervention.
- **Role-based memory**: Persistent, project-scoped memory that intelligently evolves with context across sessions and agent interactions.
- **Production harness layer**: Checkpoint-based crash recovery, granular budget controls, real-time cost tracking, and policy enforcement at team, agent, or workflow level.
- **Human-in-the-loop intervention nodes**: Configurable pause points with timeouts and escalation policies, allowing seamless collaboration between human experts and AI agents.

## Agent Architecture

- **Agent model**: Multi-agent hierarchical (queen agent + worker agents) + human-in-loop
- **Coordination mechanism**: Graph-based DAG executor with actor wakeups, session isolation, and shared buffers; agents communicate through the compiled graph topology
- **Human oversight**: Humans define goals and approve via intervention nodes; budget and policy limits enforce guardrails automatically

## Data & Storage Model

- **Primary store**: Self-hosted — runtime state, conversation history, and agent memory managed by the Hive server; local filesystem for agent workspaces
- **Data portability**: Unknown — no documented export format
- **Offline capability**: Partial — local models supported via LiteLLM/Ollama; dashboard and some features require server connectivity
- **Vendor lock-in risk**: **Low** — open source (Apache-2.0), model-agnostic via LiteLLM, self-hosted by design

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source | $0 | Unlimited; self-build and self-host from source |

## Ecosystem & Integrations

- **LLM providers**: 100+ via LiteLLM (OpenAI, Anthropic, Google Gemini, DeepSeek, Mistral, Groq, OpenRouter, Hive LLM, local Ollama)
- **Tool access**: MCP tools, browser use, native extensions, business system connectivity (CRM, support, messaging, data APIs)
- **Platform**: Python 3.11+; uv workspace; cross-platform (macOS, Linux, Windows including native PowerShell support)
- **Community**: Discord, GitHub Issues at [aden-hive/hive](https://github.com/aden-hive/hive/issues)

## Screenshots / Demo

- [GitHub README (includes architecture diagram and intro video)](https://github.com/aden-hive/hive)

## References

- [adenhq.com — documentation and guides](https://adenhq.com)
- [HoneyComb — community job automation marketplace](https://honeycomb.ai)
- [Developer Guide](https://github.com/aden-hive/hive/blob/main/docs/)
