# OpenMausBot

> Local-first macOS chat app for a roster of bring-your-own CLI agents, with source-backed one-hop delegation between peers through `list_bots` and `ask_bot`.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [supamaus.com/products/openmausbot](https://www.supamaus.com/products/openmausbot) |
| **Repository** | [github.com/milind-soni/OpenMausBot](https://github.com/milind-soni/OpenMausBot) |
| **Status** | `Early / Active` — repository created 2026-08-11; 513 stars and 90 forks as of 2026-08-13; source checkout `0537096` passed 82 tests and TypeScript type-checking |
| **Openness** | `Open source (MIT)` — OSI-approved |
| **Deployment** | `Local-first` — signed and notarized Apple-silicon macOS app; source development requires macOS, Node 24+, pnpm, and at least one supported CLI |
| **First release** | v0.1.0 (2026-08-11) |
| **Last release / commit** | Binary release v0.1.8 (2026-08-12); source version 0.1.9 at commit `0537096` (2026-08-12 UTC) |
| **Language / Stack** | TypeScript, React 19, Electron, Node.js harness, HTTP + SSE, JSON-RPC / ACP / MCP provider bridges |
| **License** | MIT (Copyright © 2026 Milind Soni and contributors) |

## What It Does

OpenMausBot presents multiple local AI agents as contacts in a messaging app. Each bot has its own identity, model selection, thread, provider resume cursor, connected apps, and optional computer; the local harness owns the agent processes and normalizes their native protocols into one event stream.

Its multi-agent primitive is bounded peer delegation. On a user-initiated turn, an eligible bot can discover another bot with `list_bots`, call it synchronously with `ask_bot`, wait for that bot to complete a real turn under its own model and permissions, and fold the reply into its answer.

## Key Mechanisms

- **One-hop peer delegation**: `ask_bot(bot_id, message)` runs a full turn on the target and waits up to four minutes for its text reply. `MAX_COMMS_DEPTH = 1` prevents the delegated bot from starting another peer call.
- **Capability-gated callers**: The harness only injects peer tools into drivers advertising `agentsMcp`. In source version 0.1.9, that flag is implemented by the shared ACP driver used for Grok and Gemini; Claude and Codex bots can be delegation targets, while their current drivers do not receive `list_bots` / `ask_bot` as caller tools.
- **Mention-assisted routing**: A user can tag another visible bot in the composer. The initiating agent receives a prompt hint with the target bot ID and chooses whether to call `ask_bot`.
- **Busy handling and visible cost**: A busy target returns promptly without preemption. The caller's thread receives an activity entry for each outbound peer request, and the target thread records the attributed inbound message.
- **Real harness coverage**: `server/comms.test.ts` boots the harness with a fake ACP fleet and verifies A → proxy → B depth-1 turn → reply folded into A, including endpoint authorization and visibility in both threads.
- **Provider harness**: Built-in drivers cover Claude Code, Codex, Grok CLI, Gemini CLI, Grok API, and the optional Box computer agent. Each bot keeps its own provider binding and resume cursor.
- **Human approval surface**: Tool activity, shell commands, file edits, and questions can appear as inline approval cards. Provider configuration can also enable full-auto modes, so the effective safety boundary depends on the selected driver settings.

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Peer roster — independent bot identities and threads under one local harness |
| **Coordination mechanism** | Synchronous, single-hop `ask_bot` calls over an injected MCP proxy; optional `@name` hint from the user; reply returns to the initiating turn |
| **Scope boundary** | Peer question/delegation rather than a central planner: no shared task graph, common memory, or parallel fan-out primitive is present in the current source |
| **Human oversight** | The user starts the top-level turn, sees cross-bot activity in chat, can interrupt a busy bot, and handles provider permission requests through approval cards |

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | `~/.openmausbot`: `bots.json`, per-thread message JSON, per-thread event NDJSON, native provider state, and `config.json` |
| **Secrets** | Provider and service keys are stored in local `config.json`; the config API returns configured-state booleans rather than secret values. The file is local JSON rather than an encrypted vault. |
| **Internal comms security** | Harness binds to `127.0.0.1`; peer endpoints require a random bearer token regenerated each boot. The local HTTP API otherwise trusts the local user account. |
| **Data portability** | Bot and transcript state is plain JSON / NDJSON on disk. There is no documented in-app export or import workflow. |
| **Offline capability** | The desktop shell, harness, and stored state are local. Model turns require the selected CLI/provider to be available; connected apps and cloud computers require their external services. |
| **External data flows** | PostHog analytics is initialized with autocapture and app lifecycle events; submitting onboarding email identifies the PostHog person, while email entry is skippable. Composio and Box receive data only when those optional integrations are configured and used. |
| **Vendor lock-in risk** | **Low–Medium** — MIT source and plain local state reduce product lock-in; model execution, connected apps, analytics, and cloud-computer features depend on their respective vendors. |

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| OpenMausBot app | $0 | MIT source and macOS binaries; early-stage Apple-silicon release |
| Agent runtimes | Bring your own | Uses the user's installed and authenticated Claude, Codex, Grok, or Gemini CLI; subscription or provider usage terms apply |
| Optional connected apps / cloud computer | Vendor-priced | Composio keys unlock connected apps; a Box token unlocks per-bot cloud computers. Accounts, quotas, and charges are controlled by those services. |

## Ecosystem & Integrations

- **Agent runtimes**: Claude Code CLI, Codex CLI, Grok CLI over ACP, Gemini CLI over ACP, Grok API, and the Box computer agent
- **Connected apps**: Composio Connect marketplace; curated examples include Gmail, Slack, GitHub, Notion, Linear, Google Calendar, Jira, Figma, Stripe, and others
- **Computer use**: Local Mac through the Electron-hosted CUA driver, or a persistent Linux desktop through box.ascii.dev
- **Extensibility**: Small provider driver interface under `server/drivers/`; MCP proxies bridge permissions, computers, Composio, and peer-agent communication
- **Distribution**: Source repository plus signed and notarized Apple-silicon DMG / ZIP releases in the separate public `openmausbot-releases` repository

## Screenshots / Demo

- [README product walkthrough and screenshots](https://github.com/milind-soni/OpenMausBot#readme)
- [Latest signed macOS release](https://github.com/milind-soni/openmausbot-releases/releases/latest)

## References

- [OpenMausBot source repository](https://github.com/milind-soni/OpenMausBot)
- [OpenMausBot binary releases](https://github.com/milind-soni/openmausbot-releases/releases)
- [v0.1.8 release](https://github.com/milind-soni/openmausbot-releases/releases/tag/v0.1.8)
- [`list_bots` / `ask_bot` MCP proxy](https://github.com/milind-soni/OpenMausBot/blob/0537096b881a616a7e7ff6c6a9d6ee79b4163090/server/drivers/agents-proxy.ts)
- [Harness recursion, busy, and visibility controls](https://github.com/milind-soni/OpenMausBot/blob/0537096b881a616a7e7ff6c6a9d6ee79b4163090/server/index.ts)
- [Agent-to-agent end-to-end test](https://github.com/milind-soni/OpenMausBot/blob/0537096b881a616a7e7ff6c6a9d6ee79b4163090/server/comms.test.ts)
- [ACP driver capability gate](https://github.com/milind-soni/OpenMausBot/blob/0537096b881a616a7e7ff6c6a9d6ee79b4163090/server/drivers/acp/core.ts)
- [Local persistence implementation](https://github.com/milind-soni/OpenMausBot/blob/0537096b881a616a7e7ff6c6a9d6ee79b4163090/server/store.ts)
- [Security policy](https://github.com/milind-soni/OpenMausBot/blob/0537096b881a616a7e7ff6c6a9d6ee79b4163090/SECURITY.md)
- [Analytics implementation](https://github.com/milind-soni/OpenMausBot/blob/0537096b881a616a7e7ff6c6a9d6ee79b4163090/src/lib/analytics.ts)
