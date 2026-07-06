# WorkBuddy (Tencent WorkBuddy)

> Desktop AI agent / AI teammate for everyday office work, built by Tencent Cloud.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [workbuddy.ai](https://www.workbuddy.ai/) — international; [codebuddy.cn/work](https://www.codebuddy.cn/work/) — Chinese |
| **Repository** | `Closed source` — no public GitHub org/repo confirmed |
| **Status** | `Active` — launched 2026-03-09 by Tencent Cloud |
| **Openness** | `Freemium` — closed source with a credit model; 5,000 free credits for new users |
| **Deployment** | `Local-first` — desktop app with local execution; optional cloud hosting for long-running tasks; sandboxed file operations |
| **First release** | 2026-03-09 |
| **Last release / commit** | Unknown — desktop app distributed from homepage |
| **Language / Stack** | Unknown (desktop application) |
| **License** | Proprietary |

## What It Does

WorkBuddy positions itself as an **AI teammate for everyday office work**. Users install a desktop agent that can decompose tasks, operate local and web apps, read and write files inside a sandbox, schedule work, and collaborate through common office tools. It is designed to handle multi-step office automations — such as drafting documents, gathering information from multiple sources, updating project trackers, or coordinating messages across chat platforms — with parallel multi-agent execution and human checkpoints.

## Key Mechanisms

- **Local-first execution**: The desktop app runs tasks on the user's machine by default; only long-running or cloud-dependent workloads can be offloaded to optional Tencent Cloud hosting.
- **Sandboxed file operations**: File-system access is constrained, reducing the risk of accidental cross-project changes.
- **Parallel multi-agent orchestration**: Supports task decomposition, planner–executor splits, and multiple agents running in parallel.
- **MCP and OpenClaw skill compatibility**: Uses the Model Context Protocol (MCP) for tool access and advertises compatibility with OpenClaw skills.
- **Multi-model switching**: Users can choose among domestic models including Hunyuan, DeepSeek, GLM, Kimi, and MiniMax.
- **Office and dev tool integrations**: Native connectors for WeCom (WeChat Work), QQ, Feishu, DingTalk; international connectors include GitHub, GitLab, Jira, Confluence, Google Drive, Gmail, Notion, and Slack.
- **Credit-based consumption**: Freemium model with a free-credit allowance and per-task/per-model-call consumption afterward.

## Agent Architecture

- **Agent model**: Multi-agent peer specialists coordinated by a central planner; human-in-the-loop for plan approval and sensitive actions.
- **Coordination mechanism**: Task decomposition with parallel execution; agents access tools through MCP and can hand off subtasks to one another.
- **Human oversight**: Users review high-level plans, confirm cross-app actions, and retain local control over files and model credentials.

## Data & Storage Model

- **Primary store**: Local device by default; optional cloud persistence when cloud hosting is enabled for long-running tasks.
- **Data portability**: Local files remain user-visible; no public documentation on structured export or migration.
- **Offline capability**: Core local execution can run offline; cloud models and cloud-hosted tasks require network access.
- **Vendor lock-in risk**: **Medium–High** — proprietary desktop app, credit-based pricing, and optional Tencent Cloud hosting tie workflows to the vendor's platform.

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Free | $0 | 5,000 free credits for new users |
| Pay-as-you-go | Credit-based | Credits consumed per task / model call; exact rates not publicly listed |
| Enterprise | Contact | Custom deployment, support, and billing |

## Ecosystem & Integrations

- **Domestic chat / collaboration**: WeCom (WeChat Work), QQ, Feishu, DingTalk
- **International chat / collaboration**: Slack
- **Productivity / docs**: Notion, Confluence, Google Drive, Gmail
- **Development / project tracking**: GitHub, GitLab, Jira
- **Models**: Hunyuan, DeepSeek, GLM, Kimi, MiniMax
- **Agent protocols / skills**: MCP, OpenClaw skill compatibility
- **Distribution**: Desktop application from [workbuddy.ai](https://www.workbuddy.ai/); Chinese site at [codebuddy.cn/work](https://www.codebuddy.cn/work/)

## Screenshots / Demo

- [International homepage](https://www.workbuddy.ai/)
- [Chinese homepage](https://www.codebuddy.cn/work/)
- [Documentation overview](https://www.workbuddy.ai/docs/workbuddy/Overview)

## References

- [WorkBuddy international homepage](https://www.workbuddy.ai/)
- [WorkBuddy Chinese homepage](https://www.codebuddy.cn/work/)
- [WorkBuddy documentation](https://www.workbuddy.ai/docs/workbuddy/Overview)
- [Tencent Cloud Techpedia — WorkBuddy](https://www.tencentcloud.com/techpedia/144100)
