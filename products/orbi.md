# Orbi

> GitHub-native delivery line for coding agents: a labeled Issue is implemented in an isolated worktree by one agent session, reviewed and repaired by a separate session, and merged only at the reviewed head.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [orbi.build](https://orbi.build/?ref=dir-agents-team) |
| **Repository** | [github.com/orbi-build/orbi](https://github.com/orbi-build/orbi) |
| **Status** | `Active` — frequent releases (v0.7.14 on 2026-10-21) |
| **Openness** | `Open source (AGPL-3.0)` — Sustainable Use License v1.0 offered as an alternative; hosted version (Orbi Cloud) is a paid service |
| **Deployment** | `Self-hosted` (Linux systemd / macOS launchd user timer) or `Cloud-hosted` (Orbi Cloud) |
| **First release** | 2026-09 (v0.1.0) |
| **Last release / commit** | 2026-10 |
| **Language / Stack** | Python ≥ 3.14; GitHub CLI; Pi as the coding-agent runtime; Docker images on GHCR and Docker Hub |
| **License** | AGPL-3.0 (or Sustainable Use License v1.0) |

## What It Does

Orbi turns GitHub Issues into reviewed, merged pull requests. A maintainer writes the goal and acceptance criteria in an Issue and labels it `ai-ready`; Orbi claims it, creates a feature branch and isolated worktree from a frozen base SHA, and a coding-agent session plans, implements, tests and commits. The runner opens the PR, a separate review session reviews it and fixes findings, and a merge gate merges only the reviewed head once CI passes. Releases are not automatic: a human opens a release Issue, and Orbi then cuts the tag and publishes the GitHub Release.

## Key Mechanisms

- **Issues as the only state store**: the `ai-ready` label dispatches work; comments, PRs and CI form the delivery record. No database, queue or daemon.
- **Implementer / reviewer separation**: the session that writes the code is not the session that reviews it; the reviewer can repair findings and re-run tests before the merge gate.
- **Exact-head merge gate**: only the commit the review passed can merge; AI never pushes protected branches. Branch protection with required approvals makes Orbi stop and wait for a human.
- **Fail fast to a human**: unrecoverable failures label the Issue `ai-blocked` for a human decision instead of silently retrying.
- **Run IDs end to end**: branch, worktree, logs, PR and progress comments share one `run_id`; retries create a new run and keep the old evidence.

## Agent Architecture

- **Agent model**: Multi-agent hierarchical — a scheduler-driven runner dispatches separate implementer and reviewer sessions per task.
- **Coordination mechanism**: GitHub Issues, labels, PRs and commits; a systemd/launchd timer ticks every 5 minutes.
- **Human oversight**: humans write and label Issues, decide on `ai-blocked` items, can require approving reviews before merge, and are the only ones who apply the `ai-release` label.

## Data & Storage Model

- **Primary store**: the GitHub repository itself (Issues, PRs, comments, releases), plus local journal logs.
- **Data portability**: High — all state is ordinary GitHub data in your own repositories.
- **Offline capability**: No — requires GitHub and a model provider.
- **Vendor lock-in risk**: Medium — tied to GitHub as the task store; the engine itself is open source and self-hostable with your own model configuration.

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Self-hosted (OSS) | $0 | Bring your own model provider and runner machine |
| Orbi Cloud trial | $0 | 3 merged deliveries, no credit card |
| Orbi Cloud Solo | $29/mo (or $290/yr) | 1 repository, 400M tokens/month included, no overage billing |
| Orbi Cloud Pro | $79/mo (or $790/yr) | 1.2B tokens/month included, no overage billing |

## Ecosystem & Integrations

- **IDE integrations**: N/A (works through GitHub); the repository ships a Claude Code plugin (`integrations/claude-plugin`) and a Cursor plugin manifest (`.cursor-plugin`)
- **External services**: GitHub (Issues, PRs, Actions CI, Releases), model providers via Pi
- **API / extensibility**: `orbi` CLI (`add`, `status`, `session`, `doctor`, `install-units`); on PyPI as `orbi-cli`
- **Community**: [GitHub Discussions](https://github.com/orbi-build/orbi/discussions)

## Screenshots / Demo

- [95-second film](https://youtu.be/zvPnE2whb08)
- One real loop: [Issue #1367](https://github.com/orbi-build/orbi/issues/1367) → [PR #1370](https://github.com/orbi-build/orbi/pull/1370) → [Release v0.5.47](https://github.com/orbi-build/orbi/releases/tag/v0.5.47)

## References

- [Documentation](https://docs.orbi.build/)
- [Workflow (state chain, labels, release)](https://docs.orbi.build/workflow)
- [Orbi Cloud and pricing](https://orbi.build/cloud/)
- [README](https://github.com/orbi-build/orbi#readme)
