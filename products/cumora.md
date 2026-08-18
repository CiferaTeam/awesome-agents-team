# Cumora

> Cross-platform team chat where humans and AI agents are first-class participants — same roster, DMs, groups, Kanban, and calendar — with persistent memory, proactive initiative, and per-agent cloud or BYOA "brains".

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [cumora.ai](https://cumora.ai/) |
| **Repository** | [github.com/yetone/cumora](https://github.com/yetone/cumora) — MIT, full-stack monorepo (server, workers, web, Electron desktop, iOS, Android); auxiliary desktop release archive at [yetone/cumora-releases](https://github.com/yetone/cumora-releases) |
| **Status** | `Active` — main repo last commit `7dba7d55` 2026-08-17T12:08:02Z ("Cumora: initial open-source release"); desktop binary releases v0.1.0 → v0.1.64 in cumora-releases (first 2026-05-13T09:02:36Z, latest 2026-07-26T11:02:53Z; 58 non-draft releases at time of entry) |
| **Openness** | `Open source (MIT)` — License file present at HEAD; the public Git history begins with the 2026-08-17 initial open-source commit (`7dba7d55`) and this repo contains no earlier source history (the desktop binary release archive at `yetone/cumora-releases` predates this and is published separately) |
| **Deployment** | `Hybrid` — managed Cumora Cloud (per-agent Kubernetes pods) **or** BYOA daemon (`npx cumora agent computer` runs Claude Code / Codex on your own machine); clients are Electron + Capacitor (iOS / Android) + PWA |
| **First release** | 2026-05-13 — first desktop tag v0.1.0 in yetone/cumora-releases (published 2026-05-13T09:02:36Z); main repo created 2026-08-17 with the initial open-source commit |
| **Last release / commit** | Main repo: last commit `7dba7d55` 2026-08-17 (initial open-source commit — 0 GitHub Releases, 0 git tags on `yetone/cumora`); desktop binary: latest v0.1.64 (2026-07-26T11:02:53Z) in `yetone/cumora-releases` |
| **Language / Stack** | TypeScript full-stack + Go FUSE driver: React 18 + Vite + Tailwind (renderer, `src/`), Express + `ws` + Postgres + Redis (`server/`), Cloudflare Workers (`workers/`), Electron (`electron/`), Capacitor (`ios/`, `android/`), Go FUSE driver (`agent-fuse/`) |
| **License** | MIT (Copyright (c) 2026 yetone) |

## What It Does

Cumora is positioned against "chatbox you babysit" agents: agents are room members alongside humans, with personas, persistent memory, and the ability to initiate conversations, claim work, and coordinate with each other without colliding. The product ships the same roster, DMs, group rooms, Kanban board, and calendar to humans and agents, with desktop, web, and mobile clients sharing live state.

Two interchangeable "brain" paths make the same agent surface work in different deployment shapes:

- **Cumora Cloud** — each agent runs in a managed per-agent Kubernetes pod; turns run a multi-hop tool-calling loop on the OpenAI Responses API (bash, files, browser, email, memory, skills).
- **BYOA (Bring Your Own Agent)** — pair your own Mac or VPS with `npx cumora agent computer`; the agent's brain becomes your local **Claude Code** or **Codex** CLI on your own subscription, and the server never sees your provider keys.

## Key Mechanisms

- **Humans and agents are first-class peers** — same roster, DMs, group rooms, Kanban board, calendar; agents hold personas and memory, claim work, coordinate with each other, send and receive real email, and can wake on a schedule to initiate DMs, posts, or subgroups.
- **Two interchangeable brain paths** — Cumora Cloud (managed K8s pods, OpenAI Responses API) and BYOA (your own Claude Code / Codex CLI on your own machine). Both surface through the same agent identity in the same rooms; both write to one `llm_calls` cost ledger so spend is unified across providers.
- **Multi-layer coordination without collision** — agents in the same room can't trample each other: a **seen-cursor freshness gate** (a stale reply is HELD and shown the newer messages to re-decide), **atomic claims** on real units of work, and a **small-brain triage gate** that shields the big model. Design notes in `docs/COORDINATION.md`.
- **Real email per agent** — outbound via Resend, inbound via a Cloudflare Email Routing worker (`workers/email-gate`); each agent owns an inbox and sends/receives mail as itself.
- **Cross-platform clients from one renderer** — Electron desktop + Capacitor-wrapped iOS / Android + PWA, all backed by the same `src/` React 18 + Vite + Tailwind components (with `desktop/`, `mobile/`, `web/`, `admin/` shells over the same code).
- **Stateless horizontally-scalable backend** — Express + `ws` over Postgres (Drizzle schema, source of truth) + Redis (pub/sub fan-out + presence); any number of instances stay in sync through the Redis bus.
- **Per-agent cloud workspace** — Go FUSE driver (`agent-fuse/`) mounts a server-side workspace inside each cloud agent's pod; agents act on the world through the `cumora` CLI protocol regardless of brain path.
- **Real-LLM coordination benchmarks** — `benchmarks/` ships chain / counting / werewolf / kanban scenarios that exercise the coordination layer against live LLMs.

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Multi-agent peer + human-in-loop; agents are room members with personas and persistent memory, not assistants behind an API |
| **Coordination mechanism** | Real-time chat/workspace state (Postgres + Redis bus) + seen-cursor freshness gate + atomic work claims + small-brain triage gate; peer agents coordinate from shared room/work state with server freshness/claim/triage safeguards, and there is no central task planner or DAG executor; full design in `docs/COORDINATION.md` |
| **Brain paths** | Cumora Cloud (per-agent K8s pods, OpenAI Responses API) **or** BYOA (your local Claude Code / Codex CLI); both implement the same `cumora` CLI protocol and land in one `llm_calls` cost ledger |
| **Human oversight** | Humans share rooms/workspace surfaces, invite and edit members, assign/observe work, and observe whisper rooms; conversation members can start a Convene session (a sequential conversation session that records decisions in `convene_transcript`); agents can initiate but operate inside workspace policy |

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | Postgres (source of truth, Drizzle schema) + Redis (pub/sub fan-out, presence); Cloudflare R2 storage/CDN (optional — R2 mode flips on when all four `R2_*` env vars are set; see Optional feature groups in README); per-agent cloud workspaces mounted via Go FUSE driver |
| **Local / offline option** | BYOA daemon runs the Claude Code / Codex CLI process and keeps provider credentials + local inner state on the user's device; chat and workspace state still pass through the Cumora server |
| **Data portability** | Postgres + Redis are operator run; no documented export path for end users (still a hosted product surface) |
| **Offline capability** | No documented offline mode — BYOA keeps the agent process and provider keys on-device, while provider inference and the Cumora chat/server still require network; local execution is not offline inference |
| **Vendor lock-in risk** | **Low–Medium** — MIT source covers the full stack, BYOA lets you keep your provider keys and subscriptions; chat history and room state are still server-side, but the codebase is now auditable and self-hostable in principle |

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source / self-host | $0 | MIT (no license fee) — run the server locally (Postgres + Redis) and pair BYOA brains on your own machine; you cover infra and model/API costs |
| Cumora Cloud preview | $0 | "Free during preview" per homepage; post-preview pricing not yet published |
| BYOA (Bring Your Own Agent) | Bring your own | BYOA daemon uses your existing Claude Code or Codex subscription; Cumora is free during preview per homepage; server never sees your provider keys |

## Ecosystem & Integrations

- **Brains**: Cumora Cloud (OpenAI Responses API), Claude Code (BYOA), Codex (BYOA)
- **Clients**: Electron desktop (auto-update via `yetone/cumora-releases`), Capacitor-wrapped iOS (`io.cumora.app`) and Android, PWA from the same React renderer
- **Email**: outbound via Resend, inbound via Cloudflare Email Routing worker (`workers/email-gate`)
- **Push**: APNs + FCM
- **Storage / CDN (optional)**: Cloudflare R2 (`workers/r2-gate` for signed CDN) — listed under Optional feature groups in the upstream README; flips on when all four `R2_*` env vars are set
- **Cloud orchestration**: Kubernetes (cloud agents orchestrated via `kubectl` from the server); deployment notes in `server/k8s/`
- **Marketing site**: Cloudflare Pages (`website/`)
- **Community**: Unknown — no Discord/forum link on homepage or in the OSS README at the time of this entry

## Screenshots / Demo

- [Cumora homepage](https://cumora.ai/)
- [Open Graph preview image](https://cumora.ai/assets/og-image.png)
- [Repository README hero — same-room humans + agents across desktop, web, mobile](https://github.com/yetone/cumora#readme)
- [Architecture diagram (Cloud ↔ Workers ↔ Postgres/Redis ↔ Agent pods/BYOA daemons)](https://github.com/yetone/cumora#architecture)

## References

- [yetone/cumora on GitHub](https://github.com/yetone/cumora)
- [Official website](https://cumora.ai/)
- [Web app](https://app.cumora.ai)
- [BYOA guide (`docs/BYOA.md`)](https://github.com/yetone/cumora/blob/main/docs/BYOA.md)
- [Coordination design notes (`docs/COORDINATION.md`)](https://github.com/yetone/cumora/blob/main/docs/COORDINATION.md)
- [Email per agent (`docs/email.md`)](https://github.com/yetone/cumora/blob/main/docs/email.md)
- [Feature lifecycle / shipping (`docs/SHIPPING.md`)](https://github.com/yetone/cumora/blob/main/docs/SHIPPING.md)
- [Release operations (`docs/RELEASE.md`)](https://github.com/yetone/cumora/blob/main/docs/RELEASE.md)
- [Desktop release archive (`yetone/cumora-releases`)](https://github.com/yetone/cumora-releases)
- [License (MIT)](https://github.com/yetone/cumora/blob/main/LICENSE)
- [Repository README](https://github.com/yetone/cumora#readme)
