# agentUniverse

> Multi-agent framework originating from AntGroup financial practices — build domain-expert agent teams with collaborative patterns, visual workflows, and extensive model support.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [github.com/agentuniverse-ai/agentUniverse](https://github.com/agentuniverse-ai/agentUniverse) |
| **Repository** | [github.com/agentuniverse-ai/agentUniverse](https://github.com/agentuniverse-ai/agentUniverse) |
| **Status** | `Active` — 2,263 GitHub stars; latest release v0.0.19 |
| **Openness** | `Open source (Apache-2.0)` |
| **Deployment** | `Self-hosted` — Python pip install; local or cloud deployment |
| **First release** | 2024-04-23 |
| **Last release / commit** | 2025-11-17 (v0.0.19) / 2026-04-24 |
| **Language / Stack** | Python |
| **License** | Apache-2.0 |

## What It Does

agentUniverse is a Python-based multi-agent framework that enables developers to build collaborative agent applications. Originating from real-world financial business practices at AntGroup, it provides a rich set of pre-built multi-agent collaborative pattern components (a "pattern factory") that allow agents to perform their respective duties and maximize capabilities when solving domain-specific problems. The framework emphasizes integrating domain expertise into agent workflows, helping enterprises construct domain-expert-level intelligent agents.

## Key Mechanisms

- **Pattern factory** — Pre-built multi-agent collaborative patterns tested in real business scenarios:
  - **PEER pattern** — Plan, Execute, Express, Review: breaks complex problems into manageable steps, executes sequentially, and iteratively improves based on feedback. Typical use cases: event interpretation, industry analysis
  - **DOE pattern** — Data-fining, Opinion-inject, Express: improves effectiveness for data-intensive tasks requiring high computational precision and expert opinions. Typical use cases: financial report generation
- **Flexible agent scaffolding** — Standard project structure for single agents and multi-agent apps. Supports tools, knowledge bases, RAG, memory modules, and prompt management
- **Extensive model integration** — Simple configuration-based LLM switching. Supports DeepSeek, OpenAI (GPT-4o, o1, o3-mini), Claude (3.7 Sonnet, 3.5 Sonnet, 3 Opus), Gemini (2.5 Pro, 2.0 Flash), Qwen (qwen3 series), Llama, KIMI, WenXin (ERNIE), ChatGLM, Baichuan, Doubao
- **Visual agentic workflow platform** — Canvas-based visual workflow builder (jointly developed with difizen). Install via `pip install magent-ui ruamel.yaml` and run sample platform bootstrap
- **MCP server support** — Use and publish MCP (Model Context Protocol) servers within the framework
- **Observability** — Standardized observability framework based on OpenTelemetry. Comprehensive data collection and monitoring for agents, LLMs, and tools, enabling full lifecycle tracking
- **Domain experience integration** — Framework designed to smoothly integrate domain-specific expertise into agent workflows, not just general-purpose LLM prompting
- **Agent templates** — Create reusable agent pattern templates to accelerate subsequent agent construction and facilitate team dissemination

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Multi-agent hierarchical / peer — agents collaborate through pre-defined patterns (PEER, DOE). Planner assigns tasks; workers execute; reviewers validate. Pattern factory allows domain-specific orchestration |
| **Coordination mechanism** | Pattern-based coordination through the pattern factory. Agents register, communicate, and delegate through framework-provided pattern components. PEER uses sequential step execution with feedback loops; DOE uses data-pipeline + opinion injection |
| **Human oversight** | Human review gates in PEER/DOE patterns; visual workflow platform for manual inspection and adjustment; OpenTelemetry-based observability for full lifecycle tracking |

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | Framework-managed; agents use configured knowledge bases and RAG systems. Data storage depends on deployment setup (local filesystem, databases, or cloud storage) |
| **Data portability** | **Medium-High** — Apache-2.0 open source; agent definitions and configurations are plain Python/YAML files. Knowledge base portability depends on chosen storage backend |
| **Offline capability** | Partial — local deployment supports offline execution with local models (Ollama, etc.); cloud-model-based agents require internet |
| **Vendor lock-in risk** | **Low** — open source (Apache-2.0); extensive model provider support prevents single-vendor dependency. Agent definitions are portable Python code |

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source | $0 | Free framework; bring your own API keys or local models |

## Ecosystem & Integrations

- **AI models**: DeepSeek, OpenAI (GPT-4o, o1, o3-mini), Claude (3.7 Sonnet, 3.5 Sonnet, 3 Opus), Gemini (2.5 Pro, 2.0 Flash), Qwen (qwen3 series), Llama, KIMI, WenXin (ERNIE), ChatGLM, Baichuan, Doubao
- **Protocols**: MCP (Model Context Protocol) for tool/server integration
- **Observability**: OpenTelemetry-based full lifecycle tracking
- **Visual platform**: Canvas-based workflow builder (jointly developed with difizen)
- **Install**: `pip install agentUniverse`
- **Language**: Python
- **Origin**: AntGroup financial business practices

## Screenshots / Demo

- [agentUniverse GitHub repository — README with quick start and patterns](https://github.com/agentuniverse-ai/agentUniverse)
- [Visual agentic workflow platform guide](https://github.com/agentuniverse-ai/agentUniverse/tree/master/docs/guidebook/en/How-to/Guide%20to%20Visual%20Agentic%20Workflow%20Platform)

## References

- [agentUniverse GitHub repository](https://github.com/agentuniverse-ai/agentUniverse)
- [agentUniverse documentation](https://github.com/agentuniverse-ai/agentUniverse/tree/master/docs/guidebook/en)
- [AntGroup](https://github.com/antgroup) — Origin organization
