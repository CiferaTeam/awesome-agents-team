# Moxt

> Agent-native workspace where every teammate gets a persistent AI assistant, and shared AI colleagues collaborate across your team in real time.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [moxt.ai](https://moxt.ai/) |
| **Repository** | `Closed source` |
| **Status** | `Active` — Agent-native workspace platform |
| **Openness** | `Freemium` |
| **Deployment** | `Cloud-hosted` — Web-based workspace with Slack and Feishu integrations |
| **First release** | 2026 |
| **Last release / commit** | 2026 |
| **Language / Stack** | Proprietary |
| **License** | Proprietary |

## What It Does

Moxt is an agent-native workspace that gives every human teammate a persistent AI assistant ("momo") and allows teams to create shared AI colleagues with specialized roles. AI agents work 24/7, learn from corrections across the team, and collaborate directly with humans in a shared workspace. The platform integrates with Slack and Feishu so agents can be @mentioned in chat, ask clarifying questions, and drop finished work back into conversations. Moxt emphasizes persistent context — agents remember everything across sessions, so users never need to re-explain background.

## Key Mechanisms

- **Persistent personal agent (momo)** — Every human gets a dedicated AI assistant with long-term memory that learns work style, preferences, and context over time. Memory is stored in editable system files (`user_profile.md`, `MEMORY.md`, `AGENTS.md`) that users can inspect and modify
- **Shared team memory** — Correct one agent's mistake and every agent on the team learns from it. Context compounds across the whole organization
- **AI Teammates** — Create specialized AI colleagues for specific functions (copywriting, analysis, coding, etc.). Each teammate has configurable roles, rules, skills, and memory files. Agents follow the same rules and coordinate across functions
- **Slack / Feishu integration** — @ agents directly in chat; they reply, ask clarifying questions, and return finished work to the shared workspace. No context switching required
- **Skill pipelines** — Chain skills into automated workflows (e.g. de-AI-ify → style rewrite → WeChat formatting). Intermediate versions preserved in workspace
- **Scheduled tasks (Cron)** — Set up recurring agents like a "trend monitor" that scrapes Twitter, newsletters, and Hacker News daily, clusters topics, and outputs a tech brief automatically
- **Webhook automation** — Trigger agents from external events. Example: GitHub Issues auto-sorted into bug fixes, feature requests, or FAQ drafts; agent handles triage before alerting humans
- **Visual deliverables** — AI outputs go beyond text to interactive dashboards (ECharts), structured presentations, and product demos (Tailwind CSS single-file pages)
- **AI-native document formats** — Native support for Markdown, CSV, and HTML. Uploaded files auto-convert to Markdown. AI understands all workspace content without repeated context-setting
- **Privacy and isolation** — Sensitive files isolated locally. Team Space and Personal Space with Admin/Member permission layers

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Multi-agent team — each human has a personal momo agent; shared AI Teammates fill specialized roles. Agents share context and act as one coordinated unit |
| **Coordination mechanism** | Shared workspace with team-wide memory. Agents communicate through the workspace and integrated chat platforms (Slack/Feishu @mentions). Skill pipelines chain agent outputs into multi-step workflows |
| **Human oversight** | Human review at task boundaries; agents ask clarifying questions before executing. Permission layers (Admin/Member) control workspace access. Correctable memory files (`AGENTS.md`) let humans directly edit agent behavior rules |

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | Cloud-hosted workspace with local isolation for sensitive files. Documents, memory files, and agent configs stored in platform-managed infrastructure |
| **Data portability** | **Medium** — native support for Markdown, CSV, HTML exports. Agent configurations stored as editable text files (`AGENTS.md`, `MEMORY.md`). Full platform export capabilities depend on vendor features |
| **Offline capability** | None — cloud-hosted platform requires internet connectivity |
| **Vendor lock-in risk** | **Medium-High** — proprietary freemium platform with persistent memory and skill configurations stored in cloud. While individual files are portable Markdown/HTML, the collaborative workspace and cross-agent memory are platform-bound |

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Free / trial | $0 | Limited credits/points; core features accessible for evaluation |
| Paid | Credit-based | Points consumed per task execution and agent usage |

> Pricing details are not fully transparent beyond the credit-based model.

## Ecosystem & Integrations

- **Chat platforms**: Slack, Feishu (Lark) — deep integration with @mention support
- **Code / development**: Built-in AI coding experience; GitHub webhook support for Issue triage
- **Data visualization**: ECharts interactive dashboards, structured presentations, Tailwind CSS demos
- **Document formats**: Native Markdown, CSV, HTML; automatic file-to-Markdown conversion
- **Automation**: Cron scheduling, webhook triggers
- **Platform**: Web-based; no desktop app or mobile app mentioned
- **Languages**: Primarily Chinese and English interface

## Screenshots / Demo

- [Moxt official website](https://moxt.ai/)
- [Moxt深度体验 — 稀土掘金](https://juejin.cn/post/7634079284186562611)

## References

- [Moxt official website](https://moxt.ai/)
- [Moxt深度体验 — 稀土掘金](https://juejin.cn/post/7634079284186562611)
- [Moxt介绍 — AI工具导航](https://www.aig123.com/sites/8480.html)
- [Moxt — AI工具集](http://ai.kukuwg.com/sites/76261.html)
