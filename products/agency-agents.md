# agency-agents (The Agency)

> A collection of 144+ production-ready AI agent personalities across 12 divisions, with native integration for Claude Code, GitHub Copilot, Cursor, and 10 other agentic coding tools.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [github.com/msitarzewski/agency-agents](https://github.com/msitarzewski/agency-agents) |
| **Repository** | [github.com/msitarzewski/agency-agents](https://github.com/msitarzewski/agency-agents) |
| **Status** | `Active` — 104k+ stars; last commit 2026-04-12 |
| **Openness** | `Open source (MIT)` |
| **Deployment** | `Local-first` — agent files install into local tool directories |
| **First release** | Unknown — earliest visible activity 2025-10 |
| **Last release / commit** | 2026-04-12 (last commit) |
| **Language / Stack** | Markdown (agent definitions) + shell scripts (convert/install) |
| **License** | MIT |

## What It Does

agency-agents provides meticulously crafted, specialized AI agent personalities for every major agentic coding tool. Each agent includes identity, personality traits, core mission, critical rules, technical deliverables with code examples, workflow processes, and success metrics. Rather than generic prompts, these are domain-deep specialists designed to be activated by name inside your existing tools.

## Key Mechanisms

- **Personality-driven specialization**: Every agent has a distinct voice, communication style, and domain depth — not a generic prompt template.
- **Multi-tool native integration**: Ships with conversion and install scripts for Claude Code, Copilot, Cursor, Aider, Windsurf, Gemini CLI, OpenCode, OpenClaw, Qwen Code, Kimi Code, and Antigravity.
- **Deliverable-focused design**: Each agent defines concrete outputs, success metrics, and step-by-step workflows rather than vague guidance.
- **Cross-division roster**: 12 divisions covering Engineering, Design, Marketing, Sales, Product, PM, Testing, Support, Finance, Game Dev, Spatial Computing, and Academia.

## Agent Architecture

- **Agent model**: Single specialist agents activated on-demand within existing coding tool sessions
- **Coordination mechanism**: Human invokes agents by name inside their IDE/CLI; agents operate within the host tool's context window and file system
- **Human oversight**: Humans initiate every agent activation, review all generated outputs, and retain full control over execution

## Data & Storage Model

- **Primary store**: Local file system — agents install as markdown files into tool-specific directories (`~/.claude/agents/`, `.cursor/rules/`, etc.)
- **Data portability**: Plain markdown files; can be copied, versioned, or moved between machines with standard tools
- **Offline capability**: Fully offline — no network required after installation
- **Vendor lock-in risk**: **Low** — markdown files work across any tool; easy to migrate or adapt

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source | $0 | Unlimited agents and conversions |

## Ecosystem & Integrations

- **IDE / tool support**: Claude Code, GitHub Copilot, Cursor, Aider, Windsurf, Gemini CLI, OpenCode, OpenClaw, Qwen Code, Kimi Code, Antigravity
- **External services**: None — operates inside existing tool contexts
- **API / extensibility**: Add new agents by following the template structure; regenerate integrations with `./scripts/convert.sh`
- **Community**: GitHub Discussions and Issues at [msitarzewski/agency-agents](https://github.com/msitarzewski/agency-agents); Reddit r/ClaudeAI

## Screenshots / Demo

- [GitHub README with full roster and use cases](https://github.com/msitarzewski/agency-agents)

## References

- [msitarzewski/agency-agents on GitHub](https://github.com/msitarzewski/agency-agents)
- [Community translations (zh-CN)](https://github.com/jnMetaCode/agency-agents-zh)
