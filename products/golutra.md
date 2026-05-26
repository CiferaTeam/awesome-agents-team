# Golutra

> Next-generation multi-agent workspace that transforms existing CLI tools into a unified AI collaboration hub. "One Person. One AI Squad."

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [golutra.com](https://www.golutra.com/) |
| **Repository** | [github.com/golutra/golutra](https://github.com/golutra/golutra) |
| **Status** | `Active` — 3,565 GitHub stars; latest release v0.2.6 |
| **Openness** | `Open source (BSL-1.1)` — Business Source License 1.1 |
| **Deployment** | `Local-first` — Tauri desktop app for Windows, macOS, Linux |
| **First release** | 2026-02-15 |
| **Last release / commit** | 2026-05-07 (v0.2.6) |
| **Language / Stack** | Rust (backend + Tauri), Vue 3 (frontend) |
| **License** | BSL-1.1 |

## What It Does

Golutra is a desktop multi-agent workspace that wraps existing CLI agents (Claude Code, Codex, Gemini CLI, OpenClaw, etc.) into a single visual orchestration layer. It enables parallel multi-agent execution, automated workflow orchestration from analysis to deployment, and real-time result tracking — all without migrating projects or relearning commands. Users click agent avatars to inspect logs, inject prompts directly into terminal streams, and monitor execution while AI teams run in the background.

## Key Mechanisms

- **CLI compatibility layer** — Supports Claude Code, Gemini CLI, Codex CLI, OpenCode, Qwen Code, OpenClaw, and arbitrary CLIs. No project migration, no command relearning, no terminal switching
- **Unlimited parallel multi-agent execution** — Run multiple agents concurrently with automatic result handoff to a unified delivery path
- **Stealth terminal** — Background terminal that adapts to workflow with direct prompt injection into terminal streams and context-aware intelligent autocompletion
- **Custom workflows with template import/export** — One-click import/export of workflow templates for long-running automation across industries (software teams, content creation, game design, social media publishing)
- **Visual + CLI hybrid** — Vue 3 visual interface combined with raw command-line power; inspect any agent's terminal output in real time by clicking its avatar
- **Memory layer integration** — Can call EverOS as a memory layer for long-running agents, preserving context and project knowledge across sessions
- **MCP connector** — `golutra-mcp` provides stable MCP-based integration with external tools and agents

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Multi-agent peer — multiple CLI-based agents run in parallel under a unified commander/orchestrator layer; each agent has its own terminal stream |
| **Coordination mechanism** | Visual orchestration hub with parallel execution, automated result handoff, and cross-CLI status tracking. Agents communicate through shared workspace context and workflow templates |
| **Human oversight** | Real-time monitoring via agent avatars; direct prompt injection into any agent's terminal stream on the fly; humans define workflows and intervene during execution |

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | Local filesystem — Tauri desktop app stores project context, workflow templates, and agent state locally |
| **Data portability** | **High** — workflow templates are importable/exportable in one click; projects remain in their original locations (no migration) |
| **Offline capability** | Partial — local agent execution and workflow orchestration work offline; LLM API calls require internet |
| **Vendor lock-in risk** | **Low** — open source (BSL-1.1), works with existing CLIs without lock-in, projects stay in place |

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source / self-hosted | $0 | Self-build from source or download release binaries; bring your own CLI tools and AI provider credentials |

## Ecosystem & Integrations

- **CLI agents**: Claude Code, Gemini CLI, Codex CLI, OpenCode, Qwen Code, OpenClaw, arbitrary CLI
- **Memory**: EverOS (optional memory layer for long-running agents)
- **Protocol**: MCP via `golutra-mcp`
- **Platforms**: Windows, macOS, Linux (Tauri desktop)
- **Community**: [Discord](https://discord.gg/QyNVu56mpY)
- **Video demos**: [YouTube (EN)](https://youtu.be/KpAgetjYfoY), [Bilibili (中文)](https://www.bilibili.com/video/BV1qcfhBFEpP)

## Screenshots / Demo

- [Golutra GitHub repository — README with architecture overview](https://github.com/golutra/golutra)
- [Official website](https://www.golutra.com/)
- [Video demo — multi-agent workspace in action](https://youtu.be/KpAgetjYfoY)

## References

- [Golutra GitHub repository](https://github.com/golutra/golutra)
- [Golutra official website](https://www.golutra.com/)
- [ReputAgent review — Rust-based multi-agent orchestration](https://reputagent.com/ecosystem/golutra-golutra)
- [DaniWeb — "I Built a Desktop Multi-Agent System"](https://www.daniweb.com/programming/threads/544786/i-built-a-desktop-multi-agent-system-conceptually-goes-beyond-codex-desktop)
