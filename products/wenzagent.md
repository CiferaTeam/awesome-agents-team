# WenzAgent

> Pure Dart AI agent management framework with LAN device discovery, RPC cross-device calling, and an extensible skill system. Zero native dependencies, cross-platform.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [github.com/lyming99/wenzagent](https://github.com/lyming99/wenzagent) |
| **Repository** | [github.com/lyming99/wenzagent](https://github.com/lyming99/wenzagent) |
| **Status** | `Active` — 37 GitHub stars; latest release v1.0.2 |
| **Openness** | `Open source (Apache-2.0)` |
| **Deployment** | `Self-hosted` — Dart binary or library import; LAN host/client mode |
| **First release** | 2026-04-04 |
| **Last release / commit** | 2026-05-23 (v1.0.2) |
| **Language / Stack** | Dart (>= 3.11.0); SQLite for persistence |
| **License** | Apache-2.0 |

## What It Does

WenzAgent is a Dart-native framework for creating, managing, and orchestrating AI agents across a local network. It treats each agent as an "employee" with its own LLM backend, toolset, and state. Devices on the same LAN auto-discover each other via WebSocket, enabling cross-device agent creation and remote procedure calls without cloud dependency. The skill system supports MCP, folder-based prompts, and YAML-configured behaviors.

## Key Mechanisms

- **Pure Dart, zero native dependencies** — Runs anywhere Dart runs (Windows, macOS, Linux, mobile). No external runtime or Docker required
- **Agent-as-Employee model** — Each agent binds to an LLM backend (OpenAI, Anthropic, Google, Ollama) with independent system prompts, tools, and lifecycle state (create → run → pause → stop)
- **LAN auto-discovery and communication** — Host broadcasts itself; clients auto-connect. Real-time messaging, topic-based channels, and chunked file transfer with resume support
- **RPC framework** — Request-response and notification modes for cross-device remote agent management. Agents can spawn and control agents on other devices
- **Extensible skill system** — MCP protocol integration, folder-based prompt skills, YAML-configured skills, and custom Skill interface implementations
- **Built-in toolset** — File operations, command execution, Git operations, with allowlist/denylist control per agent
- **Cron task scheduler** — Built-in Cron expression parser for timed agent operations
- **SQLite persistence** — Messages, sessions, and agent states stored locally

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Single-agent-per-instance with RPC-based remote proxying. Each agent is an "employee" with its own LLM adapter, tool set, and state tracker |
| **Coordination mechanism** | LAN WebSocket mesh with topic channels. Host/client topology for device discovery; RPC for cross-device agent control. No central coordinator — devices peer through the LAN host |
| **Human oversight** | SDK-level tool allowlists/denylists (`excludeBuiltinTools`, `onlyBuiltinTools`) gate agent capabilities at creation time |

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | Local SQLite database per device; file-based storage for skills and agent configs |
| **Data portability** | **High** — agents defined as Dart code + YAML configs; SQLite files are local and movable |
| **Offline capability** | **Full** — LAN communication works without internet; LLM calls require network unless using Ollama locally |
| **Vendor lock-in risk** | **Low** — open source (Apache-2.0), multi-provider LLM support, pure Dart with no platform lock-in |

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source / self-hosted | $0 | Self-build or import as Dart package; bring your own LLM API keys |

## Ecosystem & Integrations

- **LLM providers**: OpenAI, Anthropic, Google, Ollama (local)
- **Protocol**: MCP (Model Context Protocol) for external tool integration
- **Related**: [wenzflow](https://wenzflow.com) — integrated notes, docs, and AI productivity tool from the same author
- **Community**: QQ group 1102616387

## Screenshots / Demo

- [WenzAgent GitHub repository — README with architecture and quickstart](https://github.com/lyming99/wenzagent)
- [演示视频](https://github.com/lyming99/wenzagent#-%E6%BC%94%E7%A4%BA%E8%A7%86%E9%A2%91)

## References

- [WenzAgent GitHub repository](https://github.com/lyming99/wenzagent)
- [WenzAgent design docs](https://github.com/lyming99/wenzagent/tree/main/doc)
