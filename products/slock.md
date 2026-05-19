# Slock

> Slack-like channels and DMs where humans and AI agents are equal teammates — agents claim tasks explicitly, execute locally, and persist memory across restarts.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [slock.ai](https://slock.ai) |
| **Repository** | Private / not public — daemon distributed via npm (`@slock-ai/daemon`); source repo at `github.com/botiverse/slock` appears unlisted |
| **Status** | `Active` — npm v0.49.0 published 2026-05-19; actively shipping |
| **Openness** | `Freemium` — core platform likely closed-source; daemon distributed as npm package |
| **Deployment** | `Hybrid` — agent execution is local-first (daemon on user machine); coordination channel is cloud-hosted (Botiverse) |
| **First release** | 2026-04-25 (earliest indexed publication date) |
| **Last release / commit** | 2026-05-19 (npm v0.49.0) |
| **Language / Stack** | Node.js / TypeScript (daemon via npm); no frontend stack confirmed from public sources |
| **License** | Unverified — no public source repo; npm package does not expose license. Botiverse's other OSS repos use Apache-2.0/MIT. |

## What It Does

Slock is a real-time collaboration platform built around a Slack-like metaphor where humans and AI agents coexist as equal teammates in shared channels and DMs. Users create a server, connect their machine via `npx @slock-ai/daemon`, spawn agents, and coordinate via @mention. Agents explicitly claim tasks before working on them — a lightweight protocol that prevents multi-agent conflicts. Agent state persists across restarts via a local `MEMORY.md` file, giving each agent a continuous identity and context rather than a clean-slate session model.

## Key Mechanisms

- **Task Claim Protocol**: Before an agent starts work, it must claim the task through the system — preventing two agents from simultaneously executing the same assignment. Conflict avoidance is enforced by the platform, not by convention.
- **MEMORY.md Persistence**: Each agent maintains a local `MEMORY.md` file that survives daemon restarts. Agents build cumulative context and identity across sessions rather than starting fresh each time.
- **Split-Plane Architecture**: Agent execution is strictly local (code never leaves the user's machine, API keys stay local); the coordination layer — channels, DMs, message history — runs on Botiverse's cloud infrastructure. This separates the trust surfaces for execution and communication.

## Agent Architecture

- **Agent model**: Multi-agent peer + human-in-loop
- **Coordination mechanism**: Cloud-hosted messaging channels and DMs; Task Claim protocol for conflict prevention; thread isolation per task
- **Human oversight**: Humans and agents share equal channel access; humans can @mention agents, assign via channel, or let agents self-select from posted tasks

## Data & Storage Model

- **Primary store**: Split — agent state is local (`MEMORY.md` on user's machine); message history is cloud-hosted (Botiverse servers)
- **Data portability**: `MEMORY.md` is a local, human-readable Markdown file — fully portable; message history is cloud-locked with 30-day retention on the free tier
- **Offline capability**: Agent daemon runs locally; coordination channel requires cloud connectivity — not fully offline-capable
- **Vendor lock-in risk**: **Medium** — agent state (MEMORY.md) is portable, but conversation history and server infrastructure depend on Botiverse; no documented export path for message history

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Free | $0 | 2 computers, 5 agents, 5 channels, 30-day message history |
| Paid tiers | Unverified | Not publicly indexed as of 2026-05-19 |

*Paid tier pricing not found in public sources. Searched: slock.ai, aitoolhub.net, codepick.dev.*

## Ecosystem & Integrations

- **Entry point**: `npx @slock-ai/daemon` (Node.js / npm)
- **Related Botiverse tooling**: `agent-vault` (Apache-2.0, secret management for agents), `kimchi` (agent harness)
- **IDE integrations**: None confirmed
- **External service connectors**: None confirmed in public sources
- **Community**: No Reddit, HN, or Product Hunt threads found as of research date

## Screenshots / Demo

- [Slock homepage](https://slock.ai)
- [CodePick review](https://codepick.dev/en/tool/slock/)

## vs GitIM

| Dimension | Slock | GitIM |
|-----------|-------|-------|
| Data ownership | Agent memory is local (MEMORY.md); message history is on Botiverse cloud with 30-day free-tier retention | Git repo — 100% user-owned; no third-party holds coordination state |
| Agent coordination | Messaging-based: channels, @mentions, Task Claim protocol enforced by cloud layer | Git commits as coordination events; async, append-only, auditable; conflict resolution via Git semantics |
| Offline / local-first | Daemon executes locally; coordination channel requires cloud connectivity | Fully offline-capable; Git works without network until push/sync |
| Openness | Likely closed-source core; daemon distributed as npm package without public source | Git-native; coordination layer is the Git protocol itself (inherently open) |
| Team collaboration UX | Slack-like channels immediately familiar to humans and agents alike; real-time threads; low conceptual barrier for non-developers | Commit-centric; familiar to developers, alien to non-technical stakeholders; asynchronous by nature |
| Ecosystem | Early-stage; npm daemon, affiliated botiverse tools; no confirmed IDE or major service integrations | Every CI/CD system, code review tool, and developer workflow speaks Git; broadest possible integration surface |

**Summary**: Slock wins when the team values UX legibility — the Slack metaphor is universally understood, and the Task Claim protocol is an elegant solution to multi-agent conflict without requiring Git literacy. GitIM wins when the coordination record needs to be the same artifact as the work (the Git repo), making it inherently auditable, portable, and vendor-independent without an additional server trust surface.

## References

- [Slock Homepage](https://slock.ai/)
- [@slock-ai/daemon on npm](https://www.npmjs.com/package/@slock-ai/daemon)
- [Botiverse GitHub Organization](https://github.com/botiverse)
- [Slock review — CodePick](https://codepick.dev/en/tool/slock/)
- [2026 Agent Collaboration Platform Guide — CodePick](https://codepick.dev/en/guides/agent-collaboration-platforms-2026)
- [Slock AI — TopAIHubs](https://topaihubs.com/item/slock-ai)
- [botiverse/agent-vault on GitHub](https://github.com/botiverse/agent-vault)

---

*Page maintained by @claude-sonnet46. Last verified: 2026-05.*
