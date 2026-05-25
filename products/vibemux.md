# Vibemux

> AI coding delivery platform that routes tasks to real workstations, tracks execution logs, and brings back branches, commits, and reviewable results.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [vibemux.com](https://vibemux.com) |
| **Repository** | `Closed source` |
| **Status** | `Active` — web app live; supports macOS, Linux, and Web |
| **Openness** | `Closed source` |
| **Deployment** | `Hybrid` — cloud control plane with real workstation execution |
| **First release** | Unknown |
| **Last release / commit** | Unknown |
| **Language / Stack** | Unknown |
| **License** | Proprietary |

## What It Does

Vibemux is a platform for routing AI coding tasks to real workstations, tracking execution logs in real time, and returning completed work as reviewable branches and commits. It is designed to keep AI-generated code visible, routed, and under human control — particularly for small engineering teams managing limited people and machines.

## Key Mechanisms

- **Real workstation routing**: Tasks are dispatched to actual machines rather than abstract cloud runtimes, preserving local development environments and toolchains.
- **Live execution log tracking**: Full visibility into what the AI is doing on the workstation while it works.
- **Branch-and-commit return model**: Results come back as proper git branches with commits, ready for human review and merge.
- **Human control by design**: Built around reviewable, approvable outputs rather than autonomous deployment.

## Agent Architecture

- **Agent model**: Single AI coding agent per routed task + human-in-loop review
- **Coordination mechanism**: Cloud-based task queue and routing to connected workstations; real-time log streaming
- **Human oversight**: Humans review branches and commits before merge; tasks are initiated and inspected through the web interface

## Data & Storage Model

- **Primary store**: Hybrid — cloud task queue and routing state; code and execution logs on the connected workstations
- **Data portability**: Code lives in standard git repositories on the user's own machines
- **Offline capability**: No — requires connectivity to the Vibemux control plane for routing and log streaming
- **Vendor lock-in risk**: **Medium** — git-based outputs reduce lock-in, but the routing and orchestration layer is proprietary

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Free | $0 | Unknown limits |

## Ecosystem & Integrations

- **Platforms**: Web, macOS, Linux
- **External services**: Git (branches, commits, review workflow)
- **API / extensibility**: Unknown
- **Community**: Unknown

## Screenshots / Demo

- No public demo found.

## References

- [vibemux.com](https://vibemux.com)
- [Small Engineering Teams use case](https://vibemux.com/use-cases/small-engineering-teams)
