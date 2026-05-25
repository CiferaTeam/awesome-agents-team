# Metaswarm

> A self-improving multi-agent orchestration framework for Claude Code, Gemini CLI, and Codex CLI. Coordinate 18 specialized AI agents through a rigorous 9-phase software development lifecycle, from GitHub issue to merged PR, with recursive orchestration, parallel review gates, and a git-native knowledge base.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [dsifry.github.io/metaswarm](https://dsifry.github.io/metaswarm/) |
| **Repository** | [github.com/dsifry/metaswarm](https://github.com/dsifry/metaswarm) |
| **Status** | `Active` — 277 GitHub stars; extracted from a production-tested codebase with hundreds of autonomous PRs |
| **Openness** | `Open source (MIT)` |
| **Deployment** | `Self-hosted` — installed as a plugin / extension for Claude Code, Gemini CLI, or Codex CLI; requires Node.js 18+ |
| **First release** | 2026-02-02 (repository created) |
| **Last release / commit** | 2026-05-16 |
| **Language / Stack** | TypeScript / JavaScript (Node.js 18+); shell adapters for cross-platform CLI integration |
| **License** | MIT |

## What It Does

Metaswarm transforms a single AI CLI into a full engineering team by orchestrating 18 specialized agent personas through a structured, quality-gated workflow. It is not a standalone runtime — it is a skill / plugin layer that sits on top of Claude Code, Gemini CLI, or Codex CLI, managing the entire SDLC from issue ingestion to PR merge.

Users describe what they want in plain English (or link a GitHub issue), and Metaswarm handles the rest: research, planning, parallel design review, work-unit decomposition, TDD-based implementation, adversarial code review, and autonomous PR shepherding. Every handoff is enforced by blocking quality gates — there is no instruction path from FAIL to COMMIT.

## Key Mechanisms

- **18 specialized agent personas** — Researcher, Architect, Coder, Security Auditor, PR Shepherd, Product Manager, Designer, CTO, and others, each with defined responsibilities and rubrics
- **9-phase workflow** — Research → Plan → Design Review Gate → Work Unit Decomposition → Orchestrated Execution → Final Review → PR Creation → PR Shepherd → Closure & Learning
- **4-Phase Orchestrated Execution Loop** — Every work unit runs IMPLEMENT → VALIDATE → ADVERSARIAL REVIEW → COMMIT. The orchestrator validates independently (never trusts subagent self-reports), and adversarial reviewers check Definition-of-Done compliance with file:line evidence
- **Parallel Design Review Gate** — 5 specialist agents (PM, Architect, Designer, Security, CTO) review the design in parallel with a 3-iteration cap before human escalation
- **Recursive orchestration** — Swarm Coordinators spawn Issue Orchestrators, which spawn sub-orchestrators for complex epics (swarm of swarms)
- **Cross-model adversarial review** — Optionally delegates implementation and review tasks to OpenAI Codex CLI and Google Gemini CLI, with one rule: the writer is always reviewed by a different model
- **Git-native task tracking** — Uses BEADS (`bd` CLI) for issue/task management, dependencies, and knowledge priming; all task state lives in version control
- **JSONL knowledge base** — Structured fact store for patterns, gotchas, decisions, and anti-patterns. Agents prime selectively from relevant subsets before every task
- **Self-learning reflection** — After every PR merge, `/self-reflect` extracts patterns from review feedback, build failures, and architectural decisions, feeding them back into the knowledge base
- **Visual review** — Playwright-based screenshot capture for reviewing web UIs, presentations, and rendered pages at multiple viewports
- **PR lifecycle automation** — Autonomous CI monitoring, review comment handling, thread resolution, and merge shepherding

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Hierarchical multi-agent swarm — Swarm Coordinator → Issue Orchestrator → sub-orchestrators → specialized worker agents (Coder, Auditor, etc.) |
| **Coordination mechanism** | BEADS-backed task state machine. Agents coordinate via git-native database records, not chat messages. Orchestrator validates independently; no trust in subagent self-reports |
| **Human oversight** | Proactive checkpoints at planned review points; automatic escalation after 3 failed iterations or ambiguous decisions. Humans can intervene at any gate |
| **Multi-agent protocol** | Spec-driven with blocking quality gates. Agents do not skip design review, plan review, or knowledge capture. Cross-model review enforces writer ≠ reviewer |

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | BEADS (`bd` CLI) — git-native issue/task tracking with dependency graphs and knowledge priming. Execution state persists to disk, surviving context compaction and session interruption |
| **Data portability** | **High** — all issues, knowledge, specs, and task state are stored in the local git repository as plain text and JSONL. No external SaaS dependency |
| **Offline capability** | Partial — local orchestration and BEADS work offline, but agent runtimes that call cloud LLM APIs require internet |
| **Vendor lock-in risk** | **Low** — open source (MIT), git-native by design, supports multiple host CLIs (Claude Code, Gemini CLI, Codex CLI). External tool delegation is opt-in per project |

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source | $0 | Self-install as plugin / extension; bring your own LLM API keys and CLI subscriptions |

## Ecosystem & Integrations

- **Host CLIs**: Claude Code (plugin marketplace), Gemini CLI (extension), Codex CLI (plugin marketplace)
- **Cross-model delegation**: OpenAI Codex CLI, Google Gemini CLI — enabled via `.metaswarm/external-tools.yaml`
- **Task tracking**: BEADS by Steve Yegge — git-native, AI-first issue tracking system
- **PR automation**: GitHub CLI (`gh`) — recommended for autonomous PR creation and shepherding
- **Visual testing**: Playwright — optional, used for UI screenshot review
- **Foundational skills**: Builds on Superpowers by Jesse Vincent (brainstorming, TDD, systematic debugging, plan writing)
- **Creator**: Dave Sifry — founder of Technorati, Linuxcare, and Warmstart; former tech executive at Lyft and Reddit

## Screenshots / Demo

- [Metaswarm GitHub repository — README with architecture diagram and quickstart](https://github.com/dsifry/metaswarm)
- [Metaswarm documentation site — installation and usage guides](https://dsifry.github.io/metaswarm/)

## References

- [Metaswarm GitHub repository](https://github.com/dsifry/metaswarm)
- [Metaswarm documentation](https://dsifry.github.io/metaswarm/)
- [BEADS — git-native issue tracking](https://github.com/steveyegge/beads)
- [Superpowers — agentic skills framework](https://github.com/jessecrossen/superpowers)
- [Ry Walker Research — Autonomous Agentic Engineering Tools Compared](https://rywalker.com/research/autonomous-agentic-engineering-tools)
- [MCP Market — Metaswarm Multi-Agent Orchestrator](https://mcpmarket.com/tools/skills/metaswarm-multi-agent-orchestrator)
