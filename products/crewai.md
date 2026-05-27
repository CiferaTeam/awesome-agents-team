# crewAI

> Lean, standalone Python framework for orchestrating multi-agent automations through role-based Crews and event-driven Flows — built from scratch with no LangChain dependency.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [crewai.com](https://www.crewai.com/) |
| **Repository** | [github.com/crewAIInc/crewAI](https://github.com/crewAIInc/crewAI) |
| **Status** | `Active` — 52,238 GitHub stars; latest release v1.14.5 |
| **Openness** | `Open source (MIT)` |
| **Deployment** | `Self-hosted` — Python package via pip/uv; cloud option via CrewAI AMP |
| **First release** | 2023-10-27 |
| **Last release / commit** | 2026-05-18 (v1.14.5) |
| **Language / Stack** | Python (>= 3.10, < 3.14) |
| **License** | MIT |

## What It Does

crewAI is a Python-native framework for building multi-agent automations. Developers define agents with roles, goals, and backstories, then assign them tasks that can be executed sequentially, in parallel, or hierarchically (with an automatic manager). The framework provides two primary abstractions: **Crews** for autonomous agent collaboration and **Flows** for precise, event-driven workflow control. It is built entirely from scratch without LangChain dependencies, emphasizing speed and low-level customization.

## Key Mechanisms

- **Crews** — Teams of agents with defined roles collaborate autonomously through sequential, parallel, or hierarchical processes. Hierarchical mode auto-assigns a manager agent to coordinate planning and execution via delegation
- **Flows** — Enterprise-grade, event-driven workflows with fine-grained control over execution paths, conditional branching (`@router`, `@listen(or_`, `@listen(and_)`), and secure state management via Pydantic models
- **Standalone framework** — Built from scratch with zero LangChain or external framework dependencies; optimized for speed and lighter resource usage
- **YAML-driven configuration** — Agents and tasks defined in `agents.yaml` and `tasks.yaml`; `crewai create crew <name>` scaffolds a full project structure
- **Skill plugins for coding agents** — Official skills teach Claude Code, Cursor, Codex, and Windsurf how to scaffold projects, design agents/tasks, and follow crewAI patterns
- **CrewAI Tools** — Built-in and extensible tool system for web search, file operations, and custom integrations
- **Memory and delegation** — Agents can retain context across tasks and delegate work to other agents when appropriate
- **Human-in-the-loop** — Built-in support for human review and approval at task boundaries
- **Structured output** — Tasks can enforce Pydantic models or JSON schemas via `output_pydantic` and `output_json`

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Multi-agent peer — agents have explicit roles, goals, backstories, and toolsets. Hierarchical crews add a manager agent for delegation and validation |
| **Coordination mechanism** | Process-based: sequential (default), parallel, or hierarchical. Flows add event-driven orchestration with `@start`, `@listen`, `@router` decorators and logical operators (`or_`, `and_`) |
| **Human oversight** | Human input supported at task boundaries; manager agent in hierarchical mode reviews and validates subordinate outputs before proceeding |

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | In-memory during execution; task outputs can be written to files (e.g., `output_file: 'report.md'`). No built-in persistent state database |
| **Data portability** | **High** — crews defined as Python code + YAML configs; portable across environments with the same Python version |
| **Offline capability** | Partial — framework runs offline; LLM calls require network unless using local models (Ollama, LM Studio) |
| **Vendor lock-in risk** | **Low** — open source (MIT), multi-LLM support, no LangChain dependency, self-hosted by default |

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source / self-hosted | $0 | Install via pip/uv; bring your own LLM API keys |
| CrewAI AMP (enterprise) | Contact | Cloud or on-premise control plane with tracing, observability, security, 24/7 support |

## Ecosystem & Integrations

- **LLM providers**: OpenAI, Anthropic, Google, Ollama, LM Studio, and others via LiteLLM-compatible interfaces
- **Tools**: Built-in tools (web search, file operations) + extensible custom tool system via `@tool` decorator
- **CLI**: `crewai create crew`, `crewai run`, `crewai install`, `crewai update`
- **Skills for coding agents**: Claude Code plugin, Cursor/Codex/Windsurf via `npx skills add crewaiinc/skills`
- **Learning**: learn.crewai.com with 100,000+ certified developers
- **Community**: GitHub Discussions, Discord, Forum
- **Examples**: Landing Page Generator, Trip Planner, Stock Analysis, Job Descriptions

## Screenshots / Demo

- [crewAI GitHub repository — README with quickstart and examples](https://github.com/crewAIInc/crewAI)
- [Official documentation](https://docs.crewai.com/)
- [CrewAI examples repository](https://github.com/crewAIInc/crewAI-examples)
- [Learn crewAI — courses and tutorials](https://learn.crewai.com/)

## References

- [crewAI GitHub repository](https://github.com/crewAIInc/crewAI)
- [crewAI official docs](https://docs.crewai.com/)
- [crewAI examples](https://github.com/crewAIInc/crewAI-examples)
- [crewAI vs LangGraph comparison](https://github.com/crewAIInc/crewAI?tab=readme-ov-file#how-crewai-compares)
