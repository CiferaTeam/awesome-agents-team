# Awesome Agents Team

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

> A curated, opinionated list of AI agent collaboration tools — with deep-dive comparisons to help you understand what makes each one different.

This is a **hybrid-depth** awesome list. The index below gives you a one-line summary of each tool. For key products, we maintain dedicated pages in [`products/`](products/) with structured analysis, and cross-cutting comparison tables in [`comparisons/`](comparisons/).

---

## Contents

- [How to Read This List](#how-to-read-this-list)
- [Category Index](#category-index)
  - [Open Source](#open-source)
  - [Closed Source](#closed-source)
- [Products](#products)
- [Comparisons](#comparisons)
- [Contributing](#contributing)

---

## How to Read This List

Each product entry follows this format:

```
**[Product Name](products/x.md)** — One-sentence positioning. `tag` `tag`
```

Common tags: `local-first` / `cloud` / `hybrid` / `open-source` / `freemium` / `git-based`

Products link to a dedicated deep-dive page in [`products/`](products/).

---

## Category Index

### Open Source

> Source code is publicly available under an OSI-approved or source-available license.

- [GitIM](products/gitim.md) — Git-native agent collaboration layer: channels, DMs, and Kanban cards stored as plain-text commits; three local binaries, no server. `local-first` `git-based`
- [Lantor](products/lantor.md) — Local-first AI agent workspace for Codex and Claude. `local-first`
- [Multica](products/multica.md) — Task board that treats AI coding agents as first-class members; local daemon, optional self-hosted server, shared Skills library. `hybrid` `source-available · Modified Apache-2.0`
- [OpenTeams](products/openteams.md) — Multi-agent collaboration workspace that brings AI coding agents into one shared session. `local-first` `open-source`
- [Synapse](products/synapse.md) — Self-hosted AI workspace with shareable AI teammates and governed plugin access. `self-hosted` `open-source`

### Closed Source

> Source code is not publicly available.

- [Bloome](products/bloome.md) — Consumer hiring agent: explained job matches and application drafts on a cloud-only stack. `cloud` `freemium`
- [Cumora](products/cumora.md) — Desktop team chat with proactive agents, whisper rooms, and Convene decision sessions. `hybrid`
- [Helio](products/helio.md) — AI-native workspace: named teammates share channels, tickets, and approval-gated shipping workflows. `cloud`
- [Niuma AI](products/niuma.md) — Local-first AI workstation: documents, task orchestration, and multi-model runs with data on-device by default. `local-first`
- [Slock](products/slock.md) — Slack-like channels and DMs: agents claim tasks locally, coordinate through Botiverse cloud. `hybrid` `freemium`

---

## Products

> See [`products/`](products/) for deep-dive pages.

| Product | Openness | Deployment | Status | Use Case | Deep Dive |
|---------|----------|-----------|--------|----------|-----------|
| [GitIM](products/gitim.md) | Open source (Apache-2.0) | Local-first | Active | Agent coordination / IM | 📄 |
| [Lantor](products/lantor.md) | Open source (Apache-2.0) | Local-first | Active | Local AI agent workspace | 📄 |
| [Multica](products/multica.md) | Source available (Modified Apache-2.0) | Hybrid | Active | Project & task management | 📄 |
| [OpenTeams](products/openteams.md) | Open source (Apache-2.0) | Local-first | Active | Multi-agent collaboration | 📄 |
| [Synapse](products/synapse.md) | Open source (Apache-2.0) | Self-hosted | Active | Self-hosted AI workspace | 📄 |
| [Bloome](products/bloome.md) | Closed source | Cloud | Active / Beta | Consumer job search | 📄 |
| [Cumora](products/cumora.md) | Closed source | Hybrid | Active (preview) | Chat collaboration | 📄 |
| [Helio](products/helio.md) | Closed source | Cloud | Active | AI-native team workspace | 📄 |
| [Niuma AI](products/niuma.md) | Closed source | Local-first | Active | Local productivity & orchestration | 📄 |
| [Slock](products/slock.md) | Closed source | Hybrid | Active | Chat collaboration | 📄 |

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
