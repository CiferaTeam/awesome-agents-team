# Devin (Cognition)

> AI software engineer that plans and executes complex engineering tasks end-to-end, from coding and debugging to deployment and documentation.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [devin.ai](https://devin.ai) |
| **Repository** | `Closed source` |
| **Status** | `Active` — publicly available; last major docs update 2026-05-23 |
| **Openness** | `Closed source` |
| **Deployment** | `Cloud-hosted` — web app with optional local CLI |
| **First release** | 2024-03 (initial announcement) |
| **Last release / commit** | Unknown — continuously updated |
| **Language / Stack** | Unknown |
| **License** | Proprietary |

## What It Does

Devin is an end-to-end AI software engineering agent developed by Cognition. It can tackle tasks in parallel — from Linear/Jira tickets and feature builds to bug fixes, code migrations, and PR reviews — executing independently while providing real-time progress updates through a web interface and embedded IDE.

## Key Mechanisms

- **Autonomous task execution**: Devin plans and executes complex engineering tasks requiring thousands of decisions, recalling context at every step and learning from feedback.
- **Full developer environment**: Built-in shell, code editor, and browser for reading docs, testing apps, and downloading dependencies.
- **Parallel task handling**: Multiple tasks can run simultaneously before they hit the backlog, including feature development, testing, and documentation.
- **Devin CLI + cloud handoff**: Local CLI (`curl -fsSL https://cli.devin.ai/install.sh | bash`) for quick fixes and exploration; `/handoff` sends longer tasks to cloud Devin.
- **Checkpointed review**: Work proceeds through defined checkpoints where humans can review, steer, or take over in the embedded IDE.

## Agent Architecture

- **Agent model**: Single autonomous agent per task + human-in-loop at checkpoints
- **Coordination mechanism**: Task-based sessions with real-time shell, IDE, and browser access; progress reported in batches via the web UI
- **Human oversight**: Humans define tasks with clear completion criteria, review at checkpoints, and can take over in the embedded IDE or via CLI

## Data & Storage Model

- **Primary store**: Cloud-hosted by Cognition — workspace state, code, and conversation history live in Devin's cloud environment
- **Data portability**: Code is written to connected GitHub/GitLab repositories; other workspace state export is unknown
- **Offline capability**: No — cloud-hosted; CLI requires connectivity
- **Vendor lock-in risk** | **Medium** — code ships to standard git repos, but the execution environment, conversation history, and workflow configuration are proprietary

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Individual | Unknown | Available via app.devin.ai signup |
| Teams | Unknown | Available via app.devin.ai signup |
| Enterprise | Contact | Custom deployment and SLAs |

## Ecosystem & Integrations

- **IDE / surfaces**: Web app with embedded IDE, Devin CLI for local workflow
- **External services**: GitHub, GitLab, Slack, Teams, Linear, Jira
- **API / extensibility**: Devin API available for programmatic access
- **Community**: Slack Connect for Teams users; feedback via support@cognition.ai

## Screenshots / Demo

- [Devin Docs — Get Started](https://docs.devin.ai/get-started/devin-intro)
- [Cognition blog](https://www.cognition.ai/blog)

## References

- [devin.ai](https://devin.ai)
- [Devin Documentation](https://docs.devin.ai)
- [Devin CLI installation](https://docs.devin.ai/get-started/devin-intro#devin-cli)
