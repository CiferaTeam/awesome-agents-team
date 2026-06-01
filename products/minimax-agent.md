# MiniMax Agent

> AI-native workspace with desktop cowork, expert agents, and autonomous computer use — build apps and automate workflows without writing code.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [agent.minimax.io](https://agent.minimax.io/) |
| **Repository** | `Closed source` |
| **Status** | `Active` — Desktop app + Web 2.0; latest release v2.0 |
| **Openness** | `Freemium` |
| **Deployment** | `Hybrid` — Desktop app for macOS and Windows; Web UI; cloud-hosted MaxClaw agents |
| **First release** | 2026-01 |
| **Last release / commit** | 2026-05 |
| **Language / Stack** | TypeScript, Electron, React; backend powered by MiniMax M2.5 model |
| **License** | Proprietary |

## What It Does

MiniMax Agent is an AI-native workspace that combines a desktop cowork environment with customizable expert agents. Users can create specialized AI assistants for domains like law, finance, or software development through natural language prompts, and the agents can operate the user's computer, browse the web, read and write files, generate full-stack applications, and connect to external services. The platform targets both technical and non-technical users who want to automate workflows and build software without writing code.

## Key Mechanisms

- **Expert Agent** — Users create domain-specific agents via natural language (e.g. "create a tax consultant agent proficient in Chinese tax law"). The system auto-loads relevant regulations, cases, and templates, generating a professional assistant capable of end-to-end tasks with tool calling
- **Desktop Cowork** — Desktop app operates directly on macOS and Windows with full on-device processing. Connects local files, email, calendars, GitLab repositories, and logs. Zero external data transmission for local operations
- **Computer Use** — Agent can view the screen and operate mouse/keyboard. Four tool domains: Desktop Control, Window Manager, Browser Engine, and Clipboard (60+ tools total). Relative-to-absolute coordinate conversion for Retina and 4K displays
- **MaxClaw** — Managed always-on agent mode powered by OpenClaw, running natively on MiniMax M2.5. Deploy in under 10 seconds with no model deployment or API setup required. Includes 10,000+ pre-configured Experts covering content hunting, research teams, and financial modeling
- **Inbox Workflow** — Manage AI conversations like emails with statuses: Todo, In Progress, Pending Review, Completed. Flag important sessions and track work at a glance
- **Full-stack app generation** — Generate frontend (React) and backend code from natural language prompts. Live preview and deploy-ready output. Use cases include landing pages, CRM systems, lead scoring dashboards, and ecommerce comparison tools
- **Multi-platform bridge** — Remote control the desktop via Telegram, Feishu (Lark), WeChat, and Slack. Send commands through messaging apps; agent performs tasks and returns results to the original conversation
- **Permission control** — Three modes: Read-only, Ask to Edit, Auto Execute. One-click switch. Sensitive actions require user confirmation via interactive cards or text commands
- **Hooks & Automation** — Event-driven hooks for file changes, session events, and more. Built-in cron scheduling and cross-model orchestration
- **Media generation** — Built-in image and video understanding, web extraction, visual search, text-to-image, and text-to-video generation without external API keys
- **Native rendering** — Built-in PDF, image, JSON preview; native data tables and spreadsheets; Mermaid diagrams with ELK layout engine

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Multi-agent hierarchical — general workspace agents + domain-specific Expert Agents. MaxClaw provides always-on managed agents with pre-configured Expert templates |
| **Coordination mechanism** | Inbox Workflow for session status tracking; task delegation between agents via natural language instructions; scheduled automation via cron hooks |
| **Human oversight** | Three-tier permission model (Read-only / Ask to Edit / Auto Execute); interactive confirmation cards for sensitive Computer Use actions; human review gates in Inbox Workflow |

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | Local-first for Desktop Cowork (files, email, calendars, GitLab remain on device); cloud storage for MaxClaw deliverables and web dashboard sync |
| **Data portability** | **Medium** — app-generated code and documents are exportable; agent configurations and conversation history portability depends on platform features |
| **Offline capability** | Partial — Desktop Cowork operates locally without internet for file and system tasks; LLM inference and cloud-synced features require connectivity |
| **Vendor lock-in risk** | **Medium** — proprietary platform with freemium model; generated code is standard (React, Node.js, Python) and portable, but agent configs and conversation history are platform-bound |

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Free trial | $0 | 1,000 credits on signup; 200 free credits daily on login |
| MaxClaw | $19/mo | Includes pre-trained Experts, no additional API fees, 200 daily credits, cross-platform membership |
| Credits | Pay-as-you-go | Credits consumed per app generation, code output, or video generation |

## Ecosystem & Integrations

- **AI model**: MiniMax M2.5 (4M token context, 100 tokens/sec, SWE-Bench Verified 80.2%, BrowseComp 76.3%)
- **IDE / code**: Generates React, Node.js, Python full-stack apps with live preview
- **External services**: GitLab, email, calendar, Slack, Notion, databases
- **Chat platforms**: Telegram, Feishu (Lark), WeChat, Slack (for remote desktop control)
- **Protocols**: MCP (Model Context Protocol) for tools like knowledge graph and web search
- **Skills**: 17 bundled skills including PDF, Excel, PPT, Word, email, Playwright automation, video generation, web search, weather, cron tasks
- **Platforms**: macOS, Windows, Web (desktop browsers); limited mobile support
- **Languages**: Chinese, English, Japanese, Korean, Traditional Chinese

## Screenshots / Demo

- [MiniMax Agent official site](https://agent.minimax.io/)
- [MiniMax Agent — Product intro video](https://www.testingcatalog.com/minimax-launches-managed-always-on-maxclaw-ai-agent/)

## References

- [MiniMax Agent official website](https://agent.minimax.io/)
- [MiniMax launches MaxClaw AI Agent — TestingCatalog](https://www.testingcatalog.com/minimax-launches-managed-always-on-maxclaw-ai-agent/)
- [MiniMax Agent Desktop 2.0 launch — AI Base](https://news.aibase.com/news/24803)
- [MiniMax Agent Chatbot architecture (community demo)](https://github.com/codedwithlikhon/minimax-agent-chatbot)
