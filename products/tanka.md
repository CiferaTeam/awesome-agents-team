# Tanka

> AI-powered collaboration platform with persistent long-term memory — an enterprise "second brain" that remembers conversations, decisions, and business context across all connected tools.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [tanka.ai](https://www.tanka.ai) |
| **Repository** | `Closed source` |
| **Status** | `Active` — Beta; waitlist-based early access with 1,200+ signups and 35% weekly retention |
| **Openness** | `Closed source` |
| **Deployment** | `Cloud-hosted` — web app with third-party native macOS wrapper available |
| **First release** | Unknown |
| **Last release / commit** | Unknown |
| **Language / Stack** | Unknown |
| **License** | Proprietary |

## What It Does

Tanka is an AI-native communication and collaboration hub designed to eliminate information fragmentation in teams. Instead of scattering context across Slack, email, calendars, and documents, Tanka ingests conversations and files from connected platforms, builds a persistent long-term memory graph, and surfaces context-aware smart replies, summaries, and task suggestions. It positions itself as an "AI Second Brain" for organizations — every team member gets a personal AI assistant within chat groups that remembers past interactions and evolves with the business.

## Key Mechanisms

- **AI long-term memory**: Stores and recalls past conversations, decisions, and interactions based on neuroscience research principles, providing contextually rich assistance that improves over time.
- **Universal chat hub**: Consolidates messages from Slack, WhatsApp, Outlook, Gmail, Telegram, and Teams into a single, searchable interface.
- **Smart Reply**: Generates context-aware, AI-powered responses to messages and emails by analyzing real-time conversations plus accumulated team knowledge.
- **Per-user AI assistant**: Each team member gets an AI assistant within chat groups capable of summarizing conversations, retrieving key information, scheduling tasks, translating languages, and analyzing documents.
- **Cross-app workflow automation**: Extracts action items from chats, sends contextual reminders, and automates task tracking across integrated platforms.
- **Collaborative memory**: Creates a shared knowledge base for team projects, surfacing relevant insights based on shared data and historical decisions.

## Agent Architecture

- **Agent model**: Single AI assistant per user with shared collaborative memory across the organization
- **Coordination mechanism**: Memory-driven context surfacing — the AI retrieves and synthesizes relevant historical data across connected apps to inform replies and suggestions
- **Human oversight**: Humans define organization knowledge base, approve integrations, and review AI-generated replies before sending; configurable automation levels

## Data & Storage Model

- **Primary store**: Cloud-hosted — all conversation history, memory graph, and organizational knowledge stored on Tanka's infrastructure
- **Data portability**: Supports exports (marketed as "Tanka keeps it open: exports, native AI, and memory that lasts")
- **Offline capability**: No — requires connectivity to Tanka cloud services
- **Vendor lock-in risk**: **High** — closed source, memory and context are platform-specific; deep integration with communication stack creates switching friction

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Free (Teams <= 50 users) | $0 | Basic team usage |
| Pro (per user) | $23/mo billed yearly ($29/mo monthly) | Recommended tier for growing teams |
| Business (per user) | $159/mo billed yearly ($199/mo monthly) | Advanced features |
| Enterprise (> 50 users) | Custom pricing ($299/mo flat or contact sales) | Everything in Teams plus enterprise support |

## Ecosystem & Integrations

- **Messaging**: Slack, Telegram, WhatsApp, Microsoft Teams, Google Workspace
- **Email & Calendar**: Gmail, Outlook, major calendar applications
- **Productivity**: Notion, Trello, Figma
- **CRM & Support**: Salesforce, HubSpot, Freshdesk, Intercom, Zendesk
- **Development**: GitHub, GitLab, Jira
- **Automation**: Zapier
- **Desktop client**: Native macOS wrapper available via Homebrew (`brew install --cask yousiki/tanka/tanka`)
- **Community**: Waitlist-based; account-managed onboarding with personalized demo

## Screenshots / Demo

- [tanka.ai homepage](https://www.tanka.ai)
- [Product Hunt listing](https://www.producthunt.com/products/tanka) — #1 Product of the Week

## References

- [Tanka.ai — Company Collaboration Software](https://www.tanka.ai/tools/en/company-collaboration-software-with-ai)
- [Tanka Blog — DeepSeek vs ChatGPT](https://www.tanka.ai/blog/posts/deepseek-vs-chatgpt)
- [JustCall AI Agent Directory — Tanka](https://justcall.io/ai-agent-directory/tanka/)
- [G2 Reviews — Tanka](https://www.g2.com/products/tanka/reviews)
