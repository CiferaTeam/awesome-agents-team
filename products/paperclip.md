# Paperclip

> The open-source app everyone uses to manage agents at work. Paperclip is not an agent framework — it is the organizational layer that runs a company made of existing AI agents.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [paperclip.ing](https://paperclip.ing/) |
| **Repository** | [github.com/paperclipai/paperclip](https://github.com/paperclipai/paperclip) |
| **Status** | `Active` — 67k+ GitHub stars; rapid community growth since March 2026 |
| **Openness** | `Open source (MIT)` |
| **Deployment** | `Self-hosted` — Node.js 20+ with embedded PostgreSQL; runs on localhost, LAN, or Tailnet |
| **First release** | 2026-03-02 (repository created) |
| **Last release / commit** | 2026-05-25 (last commit) |
| **Language / Stack** | TypeScript (Node.js 20+, pnpm 9.15+); React dashboard; PostgreSQL |
| **License** | MIT |

## What It Does

Paperclip is an open-source orchestration platform that treats a fleet of AI agents as a functioning company. Rather than building agents from scratch, it provides the management layer — org charts, goal assignment, budget enforcement, ticketing, and governance — for agents that already exist. You "hire" any agent runtime (Claude Code, Codex, Cursor, OpenClaw, or custom webhooks), assign it a role and a manager, and Paperclip coordinates the team toward high-level business goals.

The central abstraction is a **company**: a hierarchical organization with departments, roles, reporting lines, and budget limits. A CEO agent reads the product backlog, breaks goals into projects, and delegates to department leads, which further assign tasks to individual agents. Every instruction, response, tool call, and decision is recorded as a ticket with full tracing.

## Key Mechanisms

- **Bring Your Own Agent**: Paperclip does not prescribe how agents are built. Any runtime that can receive a heartbeat — Claude Code, Codex, Cursor, OpenClaw, Gemini Local, or custom webhooks — can be onboarded into the org chart.
- **Org Chart & Roles**: Agents have titles, job descriptions, bosses, and reporting lines. The hierarchical structure prevents duplicated effort and surfaces blocked dependencies.
- **Goal Alignment**: Every task traces back to a top-level mission. The CEO agent decomposes goals into projects, which are then broken into tasks with explicit dependencies.
- **Budget Control**: Monthly spending limits are enforced per agent and per department. When an agent hits its budget, it stops — no runaway API costs.
- **Ticket System**: All work is communicated through tickets. Every tool call, decision, and response is logged with full tracing and an audit trail.
- **Heartbeat Scheduling**: Agents wake at configured intervals, check their task queue, execute pending work, and return to idle. Heartbeats are scheduled per agent and survive server restarts.
- **Governance & Approval**: Humans approve hires, override strategy, and can pause or terminate any agent at any time. Approval gates exist for high-stakes decisions.
- **Skills Library**: Portable, reusable knowledge blocks that agents load on demand. Agents can be equipped with domain-specific skills (e.g., Remotion video rendering) without hardcoding prompts.
- **Model Agnostic**: No vendor lock-in to a single LLM provider. Agents bring their own models and prompts; Paperclip coordinates the organization.

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Hierarchical multi-agent company — CEO agent delegates to department leads, which manage individual worker agents. Any external runtime can be a worker. |
| **Coordination mechanism** | Org-chart-based task routing with heartbeat polling. Dependencies are tracked so agents do not start work blocked by unfinished upstream tasks. |
| **Human oversight** | Humans retain ultimate control: approve hires, set budgets, review CEO strategy, and can pause or terminate agents. Dashboard provides unified operational visibility. |
| **Multi-agent protocol** | Ticket-based async communication with full audit logging. Agents do not chat directly; they create and respond to tickets within the Paperclip system. |

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | PostgreSQL — stores agent memory, task context, org structure, tickets, and audit logs. An embedded PostgreSQL instance is created automatically on first run. |
| **Data portability** | **High** — self-hosted with full database access; org structures and ticket histories are in a standard relational schema |
| **Offline capability** | Partial — local heartbeat scheduling works without external connectivity, but agent runtimes that call cloud LLM APIs require internet |
| **Vendor lock-in risk** | **Low** — open source (MIT), self-hosted by design, BYO-agent model means no runtime lock-in |

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source / self-hosted | $0 | Self-build and self-host; bring your own agent runtimes and model API keys |

## Ecosystem & Integrations

- **Agent runtimes**: Claude Code, Codex, Cursor, OpenClaw, Gemini Local, and any webhook-compatible custom agent
- **Skills marketplace**: Skills.sh and community skill repositories; agents load skills as reusable code blocks
- **Deployment options**: `npx paperclipai onboard --yes` for quick local start; manual git clone + `pnpm dev`; LAN or Tailnet bind presets for shared access
- **Database**: Embedded PostgreSQL (zero setup) or connect to an external Postgres instance
- **Community**: 67k+ GitHub stars; active social media presence; featured in multiple ecosystem comparison articles

## Screenshots / Demo

- [paperclip.ing — homepage](https://paperclip.ing/)
- [GitHub repository — README with quickstart](https://github.com/paperclipai/paperclip)

## References

- [Paperclip homepage](https://paperclip.ing/)
- [Paperclip GitHub repository](https://github.com/paperclipai/paperclip)
- [MindStudio — What Is Paperclip?](https://www.mindstudio.ai/blog/what-is-paperclip-zero-human-ai-company-framework/)
- [The Automators — Paperclip AI: Open-Source Agent Orchestration](https://theautomators.ai/blog/paperclip-ai-open-source-agent-orchestration-business/)
- [Hostinger — Paperclip use cases](https://www.hostinger.com/tutorials/paperclip-ai-use-cases)
- [Flowtivity — OpenClaw vs Paperclip comparison](https://flowtivity.ai/blog/openclaw-vs-paperclip-ai-agent-framework-comparison/)
- [VersusTool — Paperclip vs CrewAI](https://versustool.com/paperclip-vs-crewai)
