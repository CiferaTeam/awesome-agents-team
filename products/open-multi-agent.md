# open-multi-agent

> TypeScript multi-agent orchestration framework that turns a goal into a runtime task DAG: a coordinator plans the work, a deterministic scheduler dispatches it across agents, and the whole run is inspectable, approvable, and replayable locally.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [open-multi-agent.com](https://open-multi-agent.com) |
| **Repository** | [github.com/open-multi-agent/open-multi-agent](https://github.com/open-multi-agent/open-multi-agent) |
| **Status** | `Active` — 6,700 GitHub stars; latest release v1.14.0 (2026-08-01) |
| **Openness** | `Open source (MIT)` |
| **Deployment** | `Self-hosted` — Node.js 20+ npm package; runs locally, offline, or air-gapped on your own infrastructure |
| **First release** | 2026-04 |
| **Last release / commit** | 2026-08-01 (v1.14.0) |
| **Language / Stack** | TypeScript (Node.js >= 20) |
| **License** | MIT |

## What It Does

open-multi-agent (OMA) is a backend-oriented TypeScript framework for building multi-agent systems. Developers create a team of agents and call `runTeam()` with a plain goal; the coordinator generates a task DAG at runtime, assigns work, and synthesizes the result. It also supports `runAgent()` for single-agent calls and `runTasks()` for explicit pipelines, with checkpoints, traces, and an offline Run Viewer for debugging and audit.

## Key Mechanisms

- **Dynamic goal-to-DAG orchestration** — `runTeam()` turns a goal into a task graph at runtime; no hand-wired graph is required
- **Deterministic scheduling** — Event-driven task DAG execution with pluggable strategies: dependency-first, round-robin, least-busy, capability-match, and composite
- **Multiple execution modes** — `runAgent()` for single agents, `runTeam()` for auto-orchestrated teams, and `runTasks()` for explicit pipelines
- **Shared memory and checkpoints** — Agents share context through pluggable memory; interrupted runs resume from checkpoints without repeating completed tasks
- **Human oversight and governance** — Preview and approve plans or individual dispatches; declare required roles and order via `governanceIntent` when topology cannot drift
- **Offline observability** — Stable run identity, execution receipts, trace store, and an offline Run Viewer; optional OpenTelemetry adapter for centralized stacks
- **Broad model support** — Built-in Anthropic/OpenAI/Azure/Copilot/Grok/DeepSeek and Chinese providers; Ollama, vLLM, LM Studio, OpenRouter, and AI SDK adapters for local or custom endpoints
- **Tool and MCP integration** — Built-in tools are default-deny; custom tools, MCP servers, and guarded `delegate_to_agent` handoffs are opt-in

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Multi-agent hierarchical — a coordinator plans the DAG, a scheduler dispatches tasks, and worker agents execute with optional shared memory |
| **Coordination mechanism** | Runtime task DAG with dependency-aware dispatch, task-scoped results, structured handoffs, and shared memory |
| **Human oversight** | Plan approval (`planOnly`, `onPlanReady`), per-dispatch approval (`onTaskDispatch`), and structured governance declarations for required roles/order |

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | Pluggable shared memory and checkpoint store; in-memory and file-based trace stores are available without a hosted service |
| **Data portability** | **High** — runs produce inspectable data that can be replayed; traces and checkpoints are owned by the host application |
| **Offline capability** | **Yes** — core runtime works locally and offline; LLM calls require network unless using local models |
| **Vendor lock-in risk** | **Low** — open source (MIT), self-hosted, multi-provider, and air-gapped capable |

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source / self-hosted | $0 | npm install; bring your own LLM API keys or use local models |

## Ecosystem & Integrations

- **Package**: [`@open-multi-agent/core`](https://www.npmjs.com/package/@open-multi-agent/core) on npm
- **Scaffolder**: `npm create oma-app@latest` with starter templates and a no-key deterministic demo
- **Optional telemetry**: [`@open-multi-agent/otel`](https://github.com/open-multi-agent/open-multi-agent/tree/main/packages/otel) for OpenTelemetry export
- **Examples**: 50+ runnable examples covering basics, cookbook workflows, patterns, providers, and integrations
- **Backends**: Process and ACP backends let Claude Code, Gemini CLI, and Codex participate on the same DAG
- **Community**: [GitHub Discussions](https://github.com/open-multi-agent/open-multi-agent/discussions)

## Screenshots / Demo

- [GitHub repository README with quickstart and dashboard demo](https://github.com/open-multi-agent/open-multi-agent#readme)
- [Official documentation](https://open-multi-agent.com/getting-started/introduction/)
- [npm package page](https://www.npmjs.com/package/@open-multi-agent/core)

## References

- [open-multi-agent GitHub repository](https://github.com/open-multi-agent/open-multi-agent)
- [open-multi-agent documentation](https://open-multi-agent.com/getting-started/introduction/)
- [`@open-multi-agent/core` on npm](https://www.npmjs.com/package/@open-multi-agent/core)
- [GitHub Discussions](https://github.com/open-multi-agent/open-multi-agent/discussions)
