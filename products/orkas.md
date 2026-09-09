# Orkas

> Open-source, local-first desktop AI workforce coordinated by a Commander through one chat.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [orkas.ai](https://orkas.ai/?source=gh_cifera) |
| **Repository** | [Orkas-AI/Orkas](https://github.com/Orkas-AI/Orkas) |
| **Status** | Active |
| **Openness** | Open source (MIT) |
| **Deployment** | Local-first desktop application |
| **First release** | Unknown |
| **Last release / commit** | 2026-09 |
| **Language / Stack** | TypeScript, Electron |
| **License** | MIT |

## What It Does

A Commander turns goals into executable plans and coordinates specialist agents in parallel or sequence. The desktop workspace supports research, coding, documents, slides, and media work.

## Key Mechanisms

- **Commander**: Coordinates specialists through one conversation.
- **Local agents**: Can drive Claude Code, Codex, and other local runtimes.
- **Persistent context**: Agents retain private skills and memory.

## Agent Architecture

- **Agent model**: Hierarchical multi-agent coordination.
- **Coordination mechanism**: Commander dispatch and task handoff.
- **Human oversight**: Users direct work through chat and configured tool permissions.

## Data & Storage Model

- **Primary store**: Local application data and files.
- **Data portability**: Local work artifacts; complete export format is not specified here.
- **Offline capability**: Depends on the selected model endpoint and tools; remote providers require a network.
- **Vendor lock-in risk**: MIT source and user-selected model providers reduce dependence on a hosted service.

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source | $0 | Model-provider usage may cost extra |
| Optional managed models | Usage-based credits | Separate from the open-source application |

## Ecosystem & Integrations

- **Local coding agents**: Claude Code and Codex.
- **Extensibility**: Skills and connectors.
- **Community**: GitHub issues in the canonical repository.

## Compared with GitIM

GitIM stores collaboration events as Git commits. Orkas provides an Electron desktop workspace with Commander-led planning and local application state; it does not use Git as its conversation protocol.

## Screenshots / Demo

- [Repository screenshots and demo](https://github.com/Orkas-AI/Orkas#screenshots)

## References

- [Orkas README](https://github.com/Orkas-AI/Orkas#readme)
- [Orkas releases](https://github.com/Orkas-AI/Orkas/releases)
