# Omnigent

> Open-source meta-harness for AI coding agents — orchestrate Claude Code, Codex, Cursor, OpenCode, Hermes, Pi, and custom agents in a common layer with cross-vendor review, policies, sandboxing, and device-agnostic sessions.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [omnigent.ai](https://omnigent.ai) |
| **Repository** | [github.com/omnigent-ai/omnigent](https://github.com/omnigent-ai/omnigent) |
| **Status** | `Active` — 8518 GitHub stars, 1292 forks; latest release v0.8.1 (2026-08-03); last push 2026-08-11 (within 24h of this entry); README badges `Status: alpha` |
| **Openness** | `Open source (Apache-2.0)` — Apache License 2.0; OSI-approved |
| **Deployment** | `Hybrid` — local-first CLI / web UI / macOS desktop app; self-hostable server with Postgres; optional cloud-sandbox hosts (Modal, Daytona, Blaxel, E2B, Islo, CoreWeave, Kubernetes, OpenShell, Boxlite, Databricks) for sessions that should not run on a laptop |
| **First release** | 2026-06-19 (v0.2.0) |
| **Last release / commit** | Last release 2026-08-03 (v0.8.1); last commit `0da23edd` (2026-08-11) |
| **Language / Stack** | Python (primary, requires 3.12+) + TypeScript (web UI, pnpm) + Rust (helper crates) + Swift / Kotlin / Ruby (per-platform desktop shells); shell installer; Docker deploy images |
| **License** | Apache License 2.0 |

## What It Does

Omnigent is the orchestration layer **above** individual coding-agent runtimes. Rather than choosing one harness and rebuilding workflows around it, you describe an agent in a short YAML file and pick its executor (`claude-sdk`, `codex`, `cursor`, `hermes`, `opencode`, `pi`, or the native CLI of each harness). The same session can be opened from the terminal, the local web UI, the native macOS desktop app, or a phone on the same network — chat history, sub-agents, terminals, and files stay in sync across surfaces.

The product thesis from the README: *"a common orchestration layer over Claude Code, Codex, Cursor, OpenCode, Hermes, Pi, and the agents you write yourself: swap or combine harnesses without rewriting, enforce policies and sandboxing, and collaborate in real time from any device."* Multi-agent orchestration is the central capability — supervisors can delegate to sub-agents declared as `type: agent` in YAML, and review work can be routed to a different vendor than the one that wrote it.

## Key Mechanisms

- **Meta-harness with multi-harness support**: Native wrappers `omnigent claude` / `codex` / `cursor` / `opencode` / `hermes` / `pi` launch the underlying CLI inside a tmux/PTY, with `bwrap` (Linux) or `seatbelt` (macOS) OS-sandboxing. SDK-based harnesses (`claude-sdk`, `codex`, `cursor`, `hermes`, `opencode`, `pi`, `agents-sdk`, `antigravity`, `copilot`) run from YAML without the native terminal wrappers.
- **Sub-agents and supervisor delegation**: An agent YAML can declare other agents as tools (`type: agent`); the supervisor decides when to call them. Cross-vendor review is the canonical pattern — **Polly**, the bundled example, "plans, delegates the work to coding sub-agents (Claude Code, Codex, or Pi) in parallel git worktrees, then routes each diff to a reviewer from a different vendor than the one that wrote it."
- **Multi-head reasoning**: **Debby**, another bundled example, runs two heads (one Claude, one GPT) on every question and lays their answers side by side; `/debate` makes them critique each other for several rounds before converging.
- **Device-agnostic sessions**: Sessions started in the terminal continue in the browser (`http://localhost:6767`) or the macOS desktop app, and remain reachable from a phone on the same network. State sync covers chat, sub-agents, terminals, and files.
- **Cloud sandboxes (managed hosts)**: Per-session provisioning into Modal, Daytona, Blaxel, Islo, E2B, CoreWeave, Kubernetes, OpenShell, Boxlite, or Databricks sandboxes. No laptop needs to stay online. Self-hosted server keeps the control plane; sandboxes supply ephemeral execution.
- **Governance policies**: Server-wide / per-agent / per-session rules that allow, block, or pause for approval before each tool call. Builtins include spend caps (`cost_budget`), shell-approval gates (`ask_on_os_tools`), and tool-call ceilings (`max_tool_calls_per_session`).
- **Multi-user collaboration**: Shared sessions (watch + chat), co-drive (`omnigent attach`), and conversation forks (`omnigent run --fork`). Invite-only auth or OIDC (Google / GitHub / Okta / Microsoft) when deployed.
- **Model-agnostic credentials**: API key, vendor subscription (Claude Pro/Max, ChatGPT), any OpenAI- or Anthropic-compatible gateway (OpenRouter, LiteLLM, Ollama, vLLM, Azure), or Databricks workspace profile. Defaults are per agent; switch mid-session with `/model`.

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Multi-agent hierarchical with cross-vendor delegation — supervisors call `type: agent` sub-agents, and reviewer roles can be assigned to a different vendor than the writer |
| **Coordination mechanism** | YAML-defined agents with executor + tools + sub-agents; the Omnigent server routes messages, holds shared session state, and connects to sandboxes; `trajectoryMetadata` propagates sub-agent identity upward so the Agents rail and chat header show the right role per cascade |
| **Human oversight** | Humans intervene via approval gates in policies, shared sessions, co-drive, and fork; opt-in notifications on the desktop app; spend caps surface as Chat cards when thresholds are hit |

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | Local SQLite for the CLI/desktop session log; Postgres for the self-hosted server; YAML files in the workspace for agent definitions; sessions state lives in `~/.omnigent` with on-demand backup |
| **Data portability** | **High** — agent specs are plain YAML; sessions are exportable; the project itself is Apache-2.0; cloud sandboxes are disposable by design |
| **Offline capability** | **Partial** — CLI + daemon run locally without a server; the server (self-hosted or hosted) is required for cross-device sync, sub-agent routing, and shared sessions; cloud sandboxes require network |
| **Vendor lock-in risk** | **Low** — open source server, multiple model credentials (API key / subscription / gateway / Databricks), and per-session choice of executor; cloud sandbox providers are pluggable |
| **Telemetry** | Anonymized usage data is collected by default; opt-out documented in `docs/deploy/telemetry`; no PII |

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source / self-hosted | $0 | Apache-2.0; install via `pip` / `uv` / Homebrew / bootstrap script; bring your own model credentials and (optionally) cloud-sandbox providers |
| Cloud sandboxes (managed hosts) | Provider pricing | Per-session provisioning into Modal / Daytona / Blaxel / Islo / E2B / CoreWeave / Kubernetes / OpenShell / Boxlite / Databricks; you pay the third-party provider directly |

## Ecosystem & Integrations

- **Agent runtimes**: Claude Code, Codex, Cursor, OpenCode, Hermes, Pi, Kiro (optional), OpenClaw (via ACP), Antigravity, Copilot, Agents SDK, custom YAML agents
- **Model providers**: Anthropic API, OpenAI API, OpenRouter, LiteLLM, Ollama, vLLM, Azure, Databricks (model serving); vendor subscriptions (Claude Pro/Max, ChatGPT) via the official CLIs
- **Sandbox / managed-host providers**: Modal, Daytona, Blaxel, Islo, E2B, CoreWeave, Kubernetes, OpenShell (NVIDIA), Boxlite, Databricks Apps
- **Storage / memory**: S3-compatible buckets, `hindsight` memory layer
- **Surfaces**: Terminal (`omnigent` / `omni` CLI), web UI at `http://localhost:6767`, macOS desktop app (download from `omnigent.ai/download/mac`), phone browser on the LAN
- **Distribution**: PyPI [`omnigent`](https://pypi.org/project/omnigent/); Homebrew tap [`omnigent-ai/tap/omnigent`](https://github.com/omnigent-ai/homebrew-tap); Docker images; one-click deploys to Render, Railway, Fly.io, Hugging Face Spaces, Modal, Cloudflare (serverless), Databricks Apps
- **Auth**: Invite-only local accounts; OIDC for Google / GitHub / Okta / Microsoft on deployed servers; `header` proxy auth mode
- **Community**: Discord ([discord.gg/omnigent](https://discord.gg/omnigent)), GitHub Issues / Discussions

## Screenshots / Demo

- [Desktop app screenshot (README)](https://github.com/omnigent-ai/omnigent#readme)
- [Polly — multi-agent coding orchestrator example](https://github.com/omnigent-ai/omnigent/tree/main/examples/polly/)
- [Debby — multi-head reasoning example](https://github.com/omnigent-ai/omnigent/tree/main/examples/debby/)
- [Deep Research — single-agent MCP example](https://github.com/omnigent-ai/omnigent/tree/main/examples/deep-research/)
- [Agent YAML spec](https://github.com/omnigent-ai/omnigent/blob/main/docs/AGENT_YAML_SPEC.md)
- [Policies guide](https://github.com/omnigent-ai/omnigent/blob/main/docs/POLICIES.md)
- [Deployment guide](https://github.com/omnigent-ai/omnigent/blob/main/deploy/README.md)

## References

- [omnigent-ai/omnigent on GitHub](https://github.com/omnigent-ai/omnigent)
- [Official website](https://omnigent.ai)
- [Repository README](https://github.com/omnigent-ai/omnigent#readme)
- [Documentation map (`docs/`)](https://github.com/omnigent-ai/omnigent/tree/main/docs)
- [License (Apache-2.0)](https://github.com/omnigent-ai/omnigent/blob/main/LICENSE)
