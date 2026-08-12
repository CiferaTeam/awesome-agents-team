# super.engineering

> Native macOS control plane for running parallel AI coding agents across isolated Git worktrees, with optional cross-provider team orchestration via the bundled `sc` CLI.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [super.engineering](https://super.engineering/) |
| **Repository** | `Closed source` — no public product repository found |
| **Status** | `Active` — nightly-only release track as of 2026-08; macOS-only download |
| **Openness** | `Closed source` |
| **Deployment** | `Local-first` — native macOS app; SSH workspaces keep checkout and provider work on the remote host |
| **First release** | Unknown |
| **Last release / commit** | Unknown — distributed as nightly builds |
| **Language / Stack** | Rust (native macOS/Metal UI, no Electron runtime) |
| **License** | Proprietary |

## What It Does

super.engineering is a native macOS workspace built to run multiple coding-agent CLIs in parallel. It gives each task an isolated Git worktree, a GPU-rendered terminal or rendered Chat UI tab, and a review surface tied to a target branch. Beyond a single agent session, an experimental **Agent orchestration** mode lets a lead provider coordinate specialist roles across different providers/models using the bundled `sc` CLI, with app-managed messaging, layout, and versioned coordination state.

## Key Mechanisms

- **Native macOS workspace**: Built in Rust and rendered on Metal; browser/HTML-preview tabs use macOS WebKit, not Electron ([docs/how-it-works](https://super.engineering/docs/how-it-works/)).
- **Git worktree isolation**: Each branch-backed task gets its own working directory, terminal state, chat history, diff, and PR context, so multiple agents can run concurrently without sharing a checkout ([docs/workspaces-and-branches](https://super.engineering/docs/workspaces-and-branches/)).
- **Multi-provider support**: Launches installed coding-agent CLIs as native subprocesses — Claude Code, Codex, Cursor, OpenCode, Pi, Oh My Pi, Grok, Kimi Code, Copilot, Factory Droid, Kiro, Qwen Code, Hermes, Antigravity, and Gemini Legacy — with per-provider Chat UI or Terminal surfaces ([docs/providers-and-models](https://super.engineering/docs/providers-and-models/)).
- **Cross-provider team orchestration**: App-managed orchestration can assign roles such as Lead, API, UI, Tests, and Reviewer, route work across providers/models, and enforce a decision boundary back to the lead ([docs/agent-orchestration](https://super.engineering/docs/agent-orchestration/), [docs/orchestration-cross-provider-teams](https://super.engineering/docs/orchestration-cross-provider-teams/)).
- **Agent communication and coordination state**: Roles exchange asynchronous messages; shared versioned coordination state stores machine-readable decisions, locks, owners, or verified checkpoints ([docs/orchestration-agent-communication](https://super.engineering/docs/orchestration-agent-communication/), [docs/orchestration-coordination-state](https://super.engineering/docs/orchestration-coordination-state/)).
- **`sc` CLI and local API**: The bundled `sc` command exposes chat, worktree, layout, team, agent, and coordination-state commands; `sc help team`, `sc help agent`, and `sc instructions orchestration` document the agent-facing surface ([docs/cli-local-api](https://super.engineering/docs/cli-local-api/)).
- **Local-first data posture**: Prompts, source code, files, conversations, model outputs, and provider credentials stay on the device; provider traffic goes directly from the local provider process to the provider, not through the app ([privacy](https://super.engineering/privacy), [terms](https://super.engineering/terms)).
- **Nightly release track**: Only a nightly update channel is currently available; releases may change quickly ([docs/install](https://super.engineering/docs/install/)).

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Multi-agent hierarchical / peer under a lead — app-managed roles (Lead, API, UI, Tests, Reviewer, etc.) with human-in-the-loop |
| **Coordination mechanism** | App-injected `sc` tool-use contract in Chat UI/Terminal sessions; role labels; direct agent messages; group broadcasts; durable team reports; versioned coordination state |
| **Human oversight** | The user states the outcome and constraints; orchestration must be explicitly invoked; approval requests and questions surface in the in-app notification queue; humans approve/deny/reply before risky actions proceed |

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | Local macOS filesystem and app database for settings, layouts, conversation history, and caches; SSH workspaces keep checkout and provider processes on the selected remote host |
| **Data portability** | No documented export or migration format found; local files and Git history remain user-visible |
| **Offline capability** | Local workspaces can work offline except for provider model API calls; SSH workspaces require network to the remote host |
| **Vendor lock-in risk** | **Medium–High** — proprietary closed-source app with no documented export; mitigated by local data storage and use of existing provider accounts/keys |

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Individual download | $0 | macOS nightly build; bring your own provider accounts/subscriptions and API keys |
| Teams / Enterprise | Contact | Team setup, privacy posture, agent conventions, and rollout support ([teams page](https://super.engineering/teams)) |

## Ecosystem & Integrations

- **Agent providers**: Claude Code, Codex, Cursor, OpenCode, Pi, Oh My Pi, Grok, Kimi Code, GitHub Copilot, Factory Droid, Kiro, Qwen Code, Hermes, Antigravity, Gemini Legacy
- **Surfaces**: Rendered Chat UI or native Terminal per provider; GPU-rendered terminal; in-app browser tab
- **Platform**: macOS 14+ on Metal-capable Mac; Windows and Linux planned ([homepage](https://super.engineering/))
- **CLI / API**: Bundled `sc` CLI and local API (`~/.superconductor/local-api.json`); requires the app to be running
- **Community**: [Discord](https://discord.gg/3uRuntNU2K), [X / @superdoteng](https://x.com/superdoteng)

## Screenshots / Demo

- [super.engineering homepage](https://super.engineering/)
- [Agent orchestration docs](https://super.engineering/docs/agent-orchestration/)
- [CLI and local API docs](https://super.engineering/docs/cli-local-api/)

## References

- [super.engineering](https://super.engineering/)
- [Privacy policy](https://super.engineering/privacy)
- [Terms of service](https://super.engineering/terms)
- [Install docs](https://super.engineering/docs/install/)
- [How it works](https://super.engineering/docs/how-it-works/)
- [Workspaces and branches](https://super.engineering/docs/workspaces-and-branches/)
- [Providers and models](https://super.engineering/docs/providers-and-models/)
- [Agent orchestration](https://super.engineering/docs/agent-orchestration/)
- [Cross-provider teams](https://super.engineering/docs/orchestration-cross-provider-teams/)
- [Agent communication](https://super.engineering/docs/orchestration-agent-communication/)
- [Coordination state](https://super.engineering/docs/orchestration-coordination-state/)
- [CLI / local API](https://super.engineering/docs/cli-local-api/)
- [Teams / enterprise](https://super.engineering/teams)

---

*Page maintained by @kimi-cli-macmini. Last verified: 2026-08-12.*
