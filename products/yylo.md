# YYLO

> Command-line orchestrator for coding agents: typed task lifecycle, enforced validation and review gates, and receipt-backed repository changes across per-task git worktrees.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [github.com/yylo-dev/yylo](https://github.com/yylo-dev/yylo) |
| **Repository** | [github.com/yylo-dev/yylo](https://github.com/yylo-dev/yylo) |
| **Status** | `Active` — near-daily pushes; npm `@yylo/cli` 0.2.2 (2026-09); ~780 downloads/month |
| **Openness** | `Open source (MIT)` |
| **Deployment** | `Local-first` — npm-installed CLI (`npm install -g @yylo/cli`); Node.js 20.10+; no server |
| **First release** | 2026-01 |
| **Last release / commit** | 2026-09 |
| **Language / Stack** | TypeScript + Python (Node.js CLI; commands `yylo` and `yy`) |
| **License** | MIT |

## What It Does

YYLO is a command-line orchestrator for coding agents and repeatable workflows. It wraps a bring-your-own coding agent (Pi is documented via `yy pi` / `ypl`; workflow examples also use `yy cc`) in a typed task lifecycle: `task start` freezes the protected target SHA, creates a dedicated branch/worktree, and hydrates dependencies before implementation begins; `preflight` catches closure defects read-only; `finish` queues a clean committed tip; and a separate merge queue owns risk-based review before anything lands. It is aimed both at developers who want a quick agent loop and at project operators who need typed task, validation, merge, and release-readiness boundaries.

## Key Mechanisms

- **Per-task worktree isolation**: `task start` freezes the target SHA and creates a dedicated branch/worktree; product edits and focused tests happen only there, keeping controller metadata and integration-owner bytes under separate authorities.
- **Risk-based merge queue**: low-risk changes get no semantic reviewer, normal risk at most one, and high risk two sequential predecessor-bound reviewers on one frozen candidate. After one repair candidate and one delta-review group, unresolved findings stop as `REVIEW_FINDINGS_EXHAUSTED` — bounded review instead of an unbounded loop.
- **Controlled agent iterations**: `-i` bounds iterations inside a single agent invocation; `yy loop -n` bounds the outer command workflow; reusable multi-step contracts can be saved as `flow.yaml`.
- **Receipt-backed changes**: task and Kanban state is stored by the companion YYLO Ledger as hash-chained Markdown inside the repository, with per-task receipts and archives.
- **Fenced mutations**: target mutation is serialized under one fencing owner and expected-old-SHA compare-and-swap; conflicts and unrelated dirty bytes are preserved and recovered through explicit packets (`yy merge resolve`) rather than reset/stash/force.
- **Sealed release epochs**: `release train` emits read-only release readiness after target CAS and member reconciliation; tagging, push, publication, deploy, and cleanup remain separate explicit authorities.

## Agent Architecture

- **Agent model**: single BYO coding agent per invocation with bounded iteration loops; multi-party review happens in the merge queue (0/1/2 reviewers by risk). Model aliases span OpenAI-Codex and Anthropic-Claude model families.
- **Coordination mechanism**: git itself — task branches and worktrees, frozen SHAs, and typed state transitions recorded in YYLO Ledger Markdown.
- **Human oversight**: human merge authority throughout — merge is a separate queue-owned step, preflight checks are read-only observation, and push/release/deploy require separate explicit authority.

## Data & Storage Model

- **Primary store**: the git repository itself — task state as hash-chained Markdown (YYLO Ledger), controller metadata, receipts, and archives; no server and no external database.
- **Data portability**: high — everything is plain Markdown and git; the ledger is also a separately installable CLI (`yylo-ledger`).
- **Offline capability**: runs locally against the repository; only the chosen coding-agent providers require network access.
- **Vendor lock-in risk**: low — MIT, npm-distributed, agent-agnostic subagent surface.

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source | $0 | Bring your own coding-agent subscriptions and provider keys |

## Ecosystem & Integrations

- **Coding agents**: BYO — Pi documented (`yy pi`, `ypl` = `yy pi --live`); other subagents (e.g. `yy cc`) usable in loops and workflows.
- **Companion packages**: YYLO Ledger (Git-native task/record store) and YYLO Benchmark (evaluation/evidence package), invoked via `yy ledger` / `yy benchmark` delegation.
- **Community**: [GitHub Issues](https://github.com/yylo-dev/yylo/issues)

## Screenshots / Demo

- [GitHub README (quickstart, workflow examples, safety invariants)](https://github.com/yylo-dev/yylo)

## References

- [YYLO on GitHub](https://github.com/yylo-dev/yylo)
- [npm @yylo/cli](https://www.npmjs.com/package/@yylo/cli)
- [YYLO Ledger](https://github.com/yylo-dev/yylo-ledger)
- [YYLO Benchmark](https://github.com/yylo-dev/yylo-benchmark)
