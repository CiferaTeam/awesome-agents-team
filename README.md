# Awesome Agents Team

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

> A curated, opinionated list of AI agent collaboration tools — with deep-dive comparisons to help you understand what makes each one different.

This is a **hybrid-depth** awesome list. The index below gives you a one-line summary of each tool. For key products, we maintain dedicated pages in [`products/`](products/) with structured analysis, and cross-cutting comparison tables in [`comparisons/`](comparisons/).

**Maintainer note**: We are particularly interested in how these tools compare to [GitIM](https://gitim.io) — an agent collaboration system built on Git as the shared coordination layer. Entries include an explicit "vs GitIM" dimension.

---

## Contents

- [How to Read This List](#how-to-read-this-list)
- [Category Index](#category-index)
  - [By Deployment Model](#by-deployment-model)
  - [By Primary Use Case](#by-primary-use-case)
  - [By Openness](#by-openness)
  - [By Data & Storage Model](#by-data--storage-model)
  - [By Agent Architecture](#by-agent-architecture)
- [Products](#products)
- [Comparisons](#comparisons)
- [Contributing](#contributing)

---

## How to Read This List

Each product entry follows this format:

```
**[Product Name](url)** — One-sentence positioning. `status` `deployment`
> Key differentiator in one clause.
```

Where:
- `status` = `open-source` / `closed-source` / `freemium` / `commercial`
- `deployment` = `local-first` / `cloud` / `hybrid`

Products with a 📄 link have a dedicated deep-dive page in [`products/`](products/).

---

## Category Index

### By Deployment Model

#### Local-first

> Runs primarily on your machine. Data stays local by default.

- [Niuma AI (牛马AI)](products/niuma.md) — Local-first AI workstation: documents, task orchestration, and multi-model runs with data on-device by default.

#### Cloud-hosted

> Primary value delivered through cloud infrastructure.

- [Bloome](products/bloome.md) — Consumer hiring agent: explained job matches and application drafts on a cloud-only stack.

#### Hybrid

> Meaningful local component + cloud sync or orchestration.

- [Multica](products/multica.md) — Open-source task board: local agent daemon, optional self-hosted server, Skills library across coding agents.

---

### By Primary Use Case

#### Multi-agent Orchestration

> Tools focused on coordinating multiple AI agents toward a shared goal.

<!-- products go here in Phase 1 -->

#### Chat-based Collaboration

> Team communication with AI participants as first-class members.

- [Slock](products/slock.md) — Slack-like channels and DMs: agents claim tasks locally, coordinate through Botiverse cloud.

#### Project & Task Management

> Issue tracking, sprint planning, or workflow management with AI integration.

- [Helio](products/helio.md) — AI-native workspace: named teammates share channels, tickets, and approval-gated shipping workflows.

#### Development Tooling

> Code generation, review, or pair-programming focused.

<!-- products go here in Phase 1 -->

---

### By Openness

#### Open Source

<!-- products go here in Phase 1 -->

#### Commercial / Closed Source

<!-- products go here in Phase 1 -->

#### Freemium

<!-- products go here in Phase 1 -->

---

### By Data & Storage Model

#### Git-based

> Git is the source of truth for coordination state, not just code.

<!-- products go here in Phase 1 -->

#### Local Files / SQLite

<!-- products go here in Phase 1 -->

#### Cloud Database (proprietary)

<!-- products go here in Phase 1 -->

#### Hybrid / Pluggable

<!-- products go here in Phase 1 -->

---

### By Agent Architecture

#### Single agent + tools

> One LLM call chain with access to external tools.

<!-- products go here in Phase 1 -->

#### Multi-agent (peer or hierarchical)

> Multiple independent agent processes coordinating.

- [Cumora](products/cumora.md) — Desktop team chat with proactive agents, whisper rooms, and Convene decision sessions.

#### Human-in-the-loop

> Architecturally requires human approval at defined checkpoints.

<!-- products go here in Phase 1 -->

---

## Products

> See [`products/`](products/) for deep-dive pages.

| Product | Deployment | Status | Use Case | Data Model | Deep Dive |
|---------|-----------|--------|----------|------------|-----------|
| [Multica](products/multica.md) | Hybrid | Active | Project & task management | PostgreSQL (self-host or cloud) | 📄 |
| [Slock](products/slock.md) | Hybrid | Active | Chat collaboration | Local agent state + cloud messages | 📄 |
| [Bloome](products/bloome.md) | Cloud | Active / Beta | Consumer job search | Cloud account & profile | 📄 |
| [Cumora](products/cumora.md) | Hybrid | Active (preview) | Chat collaboration | Local desktop + synced workspace | 📄 |
| [Niuma AI](products/niuma.md) | Local-first | Active | Local productivity & orchestration | On-device storage | 📄 |
| [Helio](products/helio.md) | Cloud | Active | AI-native team workspace | Cloud platform | 📄 |

---

## Comparisons

> Cross-cutting comparison tables. See [`comparisons/`](comparisons/).

- [Agent coordination models](comparisons/agent-coordination-models.md) _(Phase 1)_
- [Data ownership & portability](comparisons/data-ownership.md) _(Phase 1)_
- [Local-first vs cloud tradeoffs](comparisons/local-vs-cloud.md) _(Phase 1)_

---

## Contributing

We welcome contributions! Please read [CONTRIBUTING.md](CONTRIBUTING.md) before submitting a PR.

**Quick checklist**:
- Use the product template at [`products/_template.md`](products/_template.md)
- One product per PR
- Fill in the "vs GitIM" section honestly — criticism is welcome

---

*Licensed under [CC BY-SA 4.0](LICENSE). See [CONTRIBUTING.md](CONTRIBUTING.md) for how to add entries.*
