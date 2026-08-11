# Crewargo

> Desktop workspace where one main agent, Argo, coordinates a team of specialist agents in a single chat thread, with local-first execution and model routing.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [crewargo.com](https://www.crewargo.com/) (English), [crewargo.com/zh](https://www.crewargo.com/zh/) (Chinese) |
| **Repository** | `Closed source` — no public product repo found |
| **Status** | `Active` — early preview; invite-code access; Windows and macOS desktop downloads |
| **Openness** | `Closed source` / `Freemium` |
| **Deployment** | `Local-first` — desktop app runs on the user's machine; only prompts/context go to connected model providers |
| **First release** | Unknown — in early preview as of 2026-08 |
| **Last release / commit** | Unknown — desktop builds distributed from homepage |
| **Language / Stack** | Unknown (desktop application) |
| **License** | Proprietary |

## What It Does

Crewargo is a desktop workspace built around a single main agent, Argo, that users talk to directly. Argo breaks a request into jobs, assigns specialist agents to each part, coordinates parallel work, and reports back in one thread. The product targets research, writing, coding, data analysis, and recurring team tasks, aiming to replace the manual work of copying context between separate chat windows and stitching together results.

## Key Mechanisms

- **Main-agent coordination**: Argo is the single point of contact; it delegates, tracks progress, and reconciles specialist outputs.
- **Specialist agents**: Different agents are matched to different models and skills based on the task — e.g., design, engineering, research, writing, data analysis.
- **Group chat as workspace**: All agent handoffs and intermediate outputs happen in one shared thread; users can `@` specialists directly.
- **Local-first execution**: The workspace and files stay on the user's machine; only chosen prompts and context are sent to model providers.
- **Model routing**: Tasks are routed to the model or runtime considered best-fit for that job; users can also bring their own Claude or GPT keys.
- **Skills and talent pool**: Agents are assembled from installed skills and a talent pool, making specialist capabilities explicit rather than role-played.
- **Parallel task execution**: Free and paid tiers differ by the number of simultaneous tasks (2/3/8).

## Agent Architecture

- **Agent model**: Multi-agent hierarchical — one coordinator (Argo) plus specialist sub-agents; human-in-the-loop for planning and final calls.
- **Coordination mechanism**: Shared chat thread / workspace with explicit delegation; agents pass information among themselves within the group chat.
- **Human oversight**: Users describe the outcome, can review Argo's plan before specialists run, redirect specialists, and approve final outputs.

## Data & Storage Model

- **Primary store**: Local device — workspace and files remain on the user's computer.
- **Data portability**: Unknown — no documented export or migration path found.
- **Offline capability**: Partial — local tasks run on-device; model calls and any in-app token routing require network access.
- **Vendor lock-in risk**: **Medium–High** — closed-source desktop app with invite-only preview; skills/talent configuration and conversation history may be tied to the Crewargo workspace format.

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Free | $0 | Bring your own Claude/GPT key; run 2 tasks simultaneously; self-configured |
| Pro | $20/mo | Run 3 tasks simultaneously; 2,000 credits/mo; model routing included; priority response; email support |
| Plus | $100/mo | Run 8 tasks simultaneously; 10,000 credits/mo; model routing included; priority response; email support |
| Max | $200/mo | Run 8 tasks simultaneously; 40,000 credits/mo; model routing included; priority response; dedicated support |

## Ecosystem & Integrations

- **Clients**: Windows x64, macOS Apple Silicon desktop apps.
- **Models**: Supports Claude, GPT, and other models via BYO key or in-app token routing.
- **Skills / protocols**: Built-in skills library and talent-pool system; mentions compatibility with Claude and Codex-style coding tools.
- **IDE integrations**: None confirmed beyond coding-oriented specialist agents.
- **External services**: None explicitly documented.
- **Community**: Early preview waitlist via homepage.

## Screenshots / Demo

- [Crewargo homepage](https://www.crewargo.com/)
- [Crewargo guides index](https://www.crewargo.com/guides)

## References

- [Crewargo homepage](https://www.crewargo.com/)
- [Crewargo Chinese homepage](https://www.crewargo.com/zh/)
- [Crewargo guides](https://www.crewargo.com/guides)
- ["What Is a Personal AI Agent? Meet Argo" guide](https://www.crewargo.com/guides/personal-ai-agent)
