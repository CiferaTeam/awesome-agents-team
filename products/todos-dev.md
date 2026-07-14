# Todos.dev

> The product workspace for small teams and agents.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [todos.dev](https://todos.dev/) |
| **Repository** | `Closed source` — no public GitHub org/repo confirmed |
| **Status** | `Active` — site live; pricing and terms updated July 2026 |
| **Openness** | `Freemium` — closed source; free to start, single paid tier per team |
| **Deployment** | `Hybrid` — cloud web app/APIs orchestrate tasks; `tds` CLI executes builds and agent tasks on user-controlled machines |
| **First release** | Unknown |
| **Last release / commit** | Unknown — continuously updated web app |
| **Language / Stack** | Unknown (web application and CLI) |
| **License** | Proprietary |

## What It Does

Todos.dev is a product workspace where small teams assign work to a team of agents. The service provides project and todo management, planning, implementation, and review workflows; agents run on machines the user owns or controls using the user's own model credentials. A persistent "Chief" agent tracks projects, queues builds, and waits for human approval before running them.

## Key Mechanisms

- **Hybrid execution model**: The cloud service (web app, APIs) stores project state and orchestrates work; the `tds` CLI runs builds and agent turns on executor machines the user provides and controls.
- **Bring-your-own models and keys**: Users configure their own AI providers (e.g. Anthropic, OpenAI, GitHub Copilot) on their executors; inference is never metered or marked up by Todos.
- **Human assignment with agent planning/building/review**: Humans assign todos; agents handle planning, implementation, and an intermediate review step before a final human approval gate.
- **Persistent Chief agent**: A "Chief" tracks every project, lines up the next builds, and runs them once approved.
- **MCP integration**: Agents can access tools and context through the Model Context Protocol.
- **Conversation rewind and structured questions**: The workspace supports replaying conversations and asking structured follow-ups to keep agents aligned.
- **Fine-grained permissions and code review**: Team members and agents get scoped access; code changes move through a review state to a merge-ready pull request.

## Agent Architecture

- **Agent model**: Multi-agent team (planner, builder, reviewer, Chief) alongside human teammates; human-in-the-loop for assignment and final approval
- **Coordination mechanism**: Cloud service dispatches tasks to user-controlled executor machines via `tds`; results, conversation state, and project status are rendered in the web app
- **Human oversight**: Humans assign work, approve Chief-queued builds, review agent output, and retain control of executor machines and model credentials

## Data & Storage Model

- **Primary store**: Cloud-hosted project/todo state, conversations, and attachments; execution artifacts and model credentials stay on the user's executor machines
- **Data portability**: Unknown — no public documentation on export or migration of project state
- **Offline capability**: No — cloud orchestration and web app require connectivity; the executor CLI may run while disconnected, but coordination requires the service
- **Vendor lock-in risk**: **Medium** — proprietary workspace and CLI; execution on own machines and BYOK reduce data/model lock-in, but project workflows are tied to the service

## Pricing

> "One flat price per team. Every plan includes the full product, with no per-seat charges and no usage bills."

| Tier | Price | Limits |
|------|-------|--------|
| Free | $0 forever | 3 members, 2 machines, 3 parallel builds, 1 GB storage |
| Team | $20/month per team ($16/month billed annually) | 10 members, 20 machines, 20 parallel builds, 100 GB storage |

The free tier requires no credit card. Agents run on the user's own machines with their own model keys; inference is not metered or marked up.

## Ecosystem & Integrations

- **Surfaces**: Web app at [todos.dev](https://todos.dev/), APIs, and `tds` command-line tool
- **Authentication**: GitHub, Google, or email sign-in
- **Agent protocols**: Model Context Protocol (MCP)
- **Models**: User-configured AI providers on their own executors (e.g. Anthropic, OpenAI, GitHub Copilot)
- **Version control**: GitHub integration mentioned in terms

## Screenshots / Demo

- [Homepage](https://todos.dev/)
- [Features](https://todos.dev/features)
- [Pricing](https://todos.dev/pricing)

## References

- [Todos homepage](https://todos.dev/)
- [Features](https://todos.dev/features)
- [Pricing](https://todos.dev/pricing)
- [Terms of Service](https://todos.dev/terms)
