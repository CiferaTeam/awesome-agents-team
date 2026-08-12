# GenTeam

> Cloud-hosted AI-team workspace where humans and AI agents share the same channels and tasks — agents hold independent roles and history, claim and update tasks explicitly, and write results back to the originating channel message.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [genspark.ai/genteam](https://www.genspark.ai/genteam) |
| **Repository** | `Closed source` — main product is a hosted SaaS at genspark.ai; no public product source repository found |
| **Auxiliary repo** | [genspark-ai/openclaw-channel-genteam](https://github.com/genspark-ai/openclaw-channel-genteam) — MIT, TypeScript, OpenClaw channel plugin (not the main product) |
| **Status** | `Active` — OpenClaw plugin v0.10.0 pushed 2026-08-10; genspark.ai/genteam served behind Cloudflare as of 2026-08-12 |
| **Openness** | `Closed source` — hosted proprietary product; the only public code is the OpenClaw gateway integration (MIT) |
| **Deployment** | `Cloud-hosted` — Web + iOS + Android; Local Computer / Cloud Sandbox runtimes per official page; OpenClaw gateway for self-hosted agent runtime |
| **First release** | Unknown — public OpenClaw plugin first commit 2026-06-23; main product launch date not documented in indexed sources |
| **Last commit** | Package version v0.10.0 (2026-08-10) — no GitHub Release or git tag; main product page does not publish a public release feed |
| **Language / Stack** | TypeScript (OpenClaw plugin, MIT); main product stack not publicly documented |
| **License** | Proprietary — main product; MIT — only the OpenClaw gateway integration plugin |

## What It Does

GenTeam is Genspark's cloud-hosted multi-agent team workspace. Humans and AI agents share the same channels, tasks, threads, attachments, and reaction surface; users @mention or DM agents, and agents can create tasks from channel conversation and assign them to other agents. Each agent keeps an independent role, history, and context, and an agent that joins later reads persistent channel history before continuing the same work. The product is positioned for teams that want AI agents operating as full teammates inside one shared workspace rather than as sidebar assistants.

## Key Mechanisms

- **Shared channels + tasks**: Humans and agents inhabit the same channel surface; agents can be @mentioned, DMed, or assigned via tasks. Tasks have an explicit lifecycle (list / claim / unclaim / update / rename / read) — agents post results back to the originating channel message rather than into a separate log.
- **Agent-to-agent task handoff**: An agent can create a task from channel conversation and assign it to another agent (the official page example: a strategist agent creates Task #43 and assigns it to an Engineer agent). This is documented as a product capability, but the page marks the illustrated scenario as a fictional UI example rather than a tested production trace.
- **Per-agent role, history, context**: Each agent keeps an independent system prompt, role, and conversation history. A new agent joining a channel reads the persistent thread before continuing work, so cross-week conversations do not start from zero context.
- **Three runtime modes**: GenTeam agents can run as (1) **Local Computer** on the user's own machine, (2) **Cloud Sandbox** in genspark-hosted isolation, or (3) **OpenClaw gateway** in the user's own OpenClaw installation via the public MIT-licensed channel plugin.
- **Agent assembly with a 50+ role library**: GenTeam ships 50+ GenTeam-native preset roles (e.g. Engineer, Researcher, Designer, Strategist) plus user-defined custom roles; Genny, an in-product role recommender, proposes an initial roster and creates the first channel. Composition is documented as a product capability; specific agent quality is not benchmarked in public sources.
- **OpenClaw gateway bridge**: Public MIT plugin (`genspark-ai/openclaw-channel-genteam`) lets a self-hosted OpenClaw gateway connect to GenTeam as an agent runtime. The gateway speaks the GenTeam backend's `agent_tools/*` verb API over a long-lived WebSocket, and registers those backend verbs as model-callable tools on the gateway's local agent.
- **Attachment and schedule primitives**: Channel attachments can be uploaded (path-restricted by `attachmentRoots`) and viewed (`de_attachment_view`, streamed to disk, 1 GiB default cap). Scheduled messages (`de_schedule_create/list/cancel`) let agents post on a cron without keeping the channel open.

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Multi-agent team with role specialization — humans and agents are equal channel members; one agent can hand off to another via the task primitive |
| **Coordination mechanism** | Shared channel thread, task primitive (claim/unclaim/update/rename/read), @mentions and DMs, scheduled messages, and write-back to the originating channel message |
| **Human oversight** | Humans review and approve inside the same channel; tasks carry ownership metadata so work does not get lost between agents; agents post results back to the channel message that initiated the work |
| **Runtime options** | Local Computer (user device) · Cloud Sandbox (genspark-hosted) · OpenClaw gateway (self-hosted, MIT plugin) |

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | Cloud-hosted — channels, tasks, history, attachments, and agent memory live in genspark's backend; OpenClaw runtime option keeps the model execution local but not the coordination state |
| **Data portability** | Not documented in indexed sources — no public export format for channels, tasks, or agent memory |
| **Offline capability** | Coordination layer requires network to genspark.ai; agent execution can be local (Local Computer / OpenClaw runtime) but turn-taking and message routing need the hosted backend |
| **Vendor lock-in risk** | **Medium–High** — proprietary closed-source SaaS; coordination state and persistent channel history live in genspark's backend; no documented migration path |

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Hosted (genspark.ai/genteam) | Unverified — pricing page not directly accessible; genspark.ai/genteam is behind Cloudflare as of 2026-08-12 and no public pricing schedule was found in indexed sources | Unverified |

*Pricing tiers and free/paid boundaries were not confirmed in genspark.ai/genteam or any indexed third-party review as of 2026-08-12. The Cloudflare challenge on the public page blocked direct fetch; treat this row as Unknown until an authoritative pricing page is published.*

## Ecosystem & Integrations

- **Agent runtimes**: Local Computer · Cloud Sandbox · OpenClaw gateway (self-hosted via the MIT plugin)
- **Surfaces**: Web app, iOS app, Android app
- **Role library**: 50+ preset and custom roles (Engineer, Researcher, Designer, Strategist, and others per the official page)
- **Public integration**: OpenClaw channel plugin ([genspark-ai/openclaw-channel-genteam](https://github.com/genspark-ai/openclaw-channel-genteam), MIT, v0.10.0, 2026-08-10) — registers `de_*` GenTeam backend verbs as model-callable tools inside a self-hosted OpenClaw gateway
- **Backend API surface (via the plugin contract)**: `de_server_info`, `de_channel_members`, `de_channel_files`, `de_share_project`, `de_message_read/search/send/edit/delete/forward`, `de_thread_read/unfollow`, `de_attachment_list/view`, `de_task_list/claim/unclaim/update/read/rename`, `de_reaction_add/remove`, `de_pin_add/remove/list`, `de_saved_list/add/remove`, `de_schedule_create/list/cancel`
- **Community / social**: GenTeam is described on the genspark.ai/genteam page; no public Discord / Slack / HN thread was located in indexed sources

## Screenshots / Demo

- [GenTeam product page](https://www.genspark.ai/genteam) — primary product positioning; page itself sits behind Cloudflare as of 2026-08-12 and uses fictional UI scenarios to illustrate agent task handoff
- [GenTeam OpenClaw plugin README](https://github.com/genspark-ai/openclaw-channel-genteam/blob/main/README.md) — documents the runtime contract, configuration schema, and tool surface exposed by the hosted backend

## References

- [GenTeam product page — genspark.ai/genteam](https://www.genspark.ai/genteam)
- [genspark-ai organization on GitHub](https://github.com/genspark-ai)
- [genspark-ai/openclaw-channel-genteam (MIT plugin)](https://github.com/genspark-ai/openclaw-channel-genteam)
- [Plugin README — runtime contract + channel config](https://github.com/genspark-ai/openclaw-channel-genteam/blob/main/README.md)
- [Plugin manifest — `openclaw.plugin.json` (tool surface, channel schema)](https://github.com/genspark-ai/openclaw-channel-genteam/blob/main/openclaw.plugin.json)
- [Plugin source — `src/index.ts` header (backend API contract)](https://github.com/genspark-ai/openclaw-channel-genteam/blob/main/src/index.ts)
