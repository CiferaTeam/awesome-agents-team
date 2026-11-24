# TheoremOS

> Open-source browser workbench and CLI from [WestlakeNLP](https://westlakenlp.com/) (Westlake University), where researchers guide AI agents through formal proofs in Lean 4 with Mathlib.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [theoremos.top](https://theoremos.top/en/) |
| **Repository** | [HuggingMath/theorem-os](https://github.com/HuggingMath/theorem-os) (workbench & CLI) · [HuggingMath/TheoremOS](https://github.com/HuggingMath/TheoremOS) (website, proof archive & verification kits) |
| **Status** | `Active` (research preview) |
| **Openness** | `Open source (AGPL-3.0-only)` — source-available workbench and CLI; hosted preview free with BYOK |
| **Deployment** | `Cloud-hosted` (browser preview, no local Lean setup required) or `Self-hosted` (Linux CLI & Docker Compose) |
| **First release** | 2026-11 (public research preview & AGPL-3.0-only release) |
| **Last release / commit** | 2026-11 (`HuggingMath/theorem-os` & `HuggingMath/TheoremOS`) |
| **Language / Stack** | TypeScript (Bun / Node.js), Lean 4, Mathlib, Docker |
| **License** | AGPL-3.0-only (workbench & CLI); archived proofs and third-party components retain their documented terms |

## What It Does

A researcher starts a task with a mathematical problem in prose or LaTeX, or a single Lean file that may contain an unfinished proof. The workbench keeps the problem and proof plan alongside the candidates and their compiler diagnostics. When an attempt fails, the researcher can open the source that produced the error and suggest what to try next. Continuing from a saved source version starts a fresh run against the same formal statement, with its own Lean checks.

## Key Mechanisms

- For a problem in prose or LaTeX, a separate model translates the generated Lean statement back into prose. The researcher compares both versions against the original problem to catch changes in meaning, such as a missing assumption or a change in quantifier order, before confirming the statement.
- Agents can test whether assuming proposed helper lemmas suffices for the main goal. They can then prove the helpers individually and check the combined proof.
- In **Advanced Lean**, researchers can inspect the types, premises, and source code of lemmas in a verified catalog. The run uses a fixed version of the chosen catalog and checks reused lemmas in its Lean environment.
- A separate Lean kernel check records which formal goals a completed candidate proves. For tasks that began in prose or LaTeX, the workbench reports separately whether the researcher confirmed the statement.

## Agent Architecture

- **Agent model.** The default **Work together** mode uses two agents to draft an initial plan and work through attempts. **Advanced Lean** lets users configure one to four agents for collaborative work on shared subgoals or independent parallel search. Agent roles depend on the task.
- **Coordination mechanism.** The proof plan lists dependencies between subgoals. That gives the researcher and agents a way to see which unfinished lemmas block later work.
- **Human oversight.** In **Work together**, the agents draft a plan after the researcher confirms the formal statement. The researcher can edit the plan before approving proof search. Time and token limits are set separately for formalization and proving. The proof timer pauses while the workbench is waiting solely for human review.

## Data & Storage Model

- **Primary store.** The hosted workbench retains run records, saved source versions, and check results.
- **Data portability.** Researchers can download the Lean source and verification report separately. The JSON archive contains saved run data, including source versions, agent actions, and checks. Importing the archive creates a draft from the saved input and settings.
- **Offline capability.** Downloadable verification kits and the CLI proof replay run locally without model API calls once Lean dependencies are available.
- **Vendor lock-in risk.** **Low** — workbench and CLI are open source (`AGPL-3.0-only`), support self-hosted Docker Compose deployment with any supported model provider, and export standard Lean tooling and JSON archives.

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source / self-hosted | $0 | Self-host via Bun/Node CLI or Docker Compose (`AGPL-3.0-only`); bring your own model API key |
| Hosted research preview | $0 platform fee | Apply for allowlist access on the hosted preview; bring your own Responses API key and pay provider for inference |

## Ecosystem & Integrations

- **IDE integrations.** Unknown.
- **External services.** Connects to supported model providers via the Responses API.
- **API / extensibility.** Exposes five replaceable TypeScript solver modules (`M1`–`M5`: execution sandbox, Lean evidence retrieval, scheduling, context assembly, and role allocation) and the local Bun CLI (`bun run math`) in [`HuggingMath/theorem-os`](https://github.com/HuggingMath/theorem-os).
- **Community.** [HuggingMath/TheoremOS Issues](https://github.com/HuggingMath/TheoremOS/issues) · [WestlakeNLP Lab](https://westlakenlp.com/).

## vs GitIM

GitIM stores messages and task cards as Git commits. TheoremOS gives the researcher and agents a shared proof plan in a hosted workspace, with the formal goal and Lean check results alongside it. [GitIM documentation](https://github.com/CiferaTeam/GitIM)

## Screenshots / Demo

- In the public rehearsal, approve a plan for a preset problem, inspect a failed attempt, and choose a repair. The final screen shows the recorded Lean checks for that route. The rehearsal requires no account or API key. [Try the rehearsal](https://app.theoremos.top/practice.html?lang=en)
- The public archive contains proof records and verification material from completed and ongoing work. [Browse the archive](https://theoremos.top/en/archive)
- Researchers can apply for preview access to run a new task with their own model key. [Request access](https://github.com/HuggingMath/TheoremOS/issues/new?template=early-access.yml)

![TheoremOS statement review page showing an example problem and its generated Lean statement](https://raw.githubusercontent.com/HuggingMath/TheoremOS/61d105500484327dfa85ff69849ab7bd1b2ec69b/assets/guide/statement-review-en.png)

## References

- [TheoremOS workbench & CLI repository (AGPL-3.0-only)](https://github.com/HuggingMath/theorem-os)
- [TheoremOS website & proof archive repository](https://github.com/HuggingMath/TheoremOS)
- [WestlakeNLP Lab (Westlake University)](https://westlakenlp.com/)
- [Capabilities and access](https://github.com/HuggingMath/TheoremOS/blob/main/docs/CAPABILITIES.md)
- [Workbench tutorial and export instructions](https://github.com/HuggingMath/TheoremOS/blob/main/docs/GETTING-STARTED.md)
- [Local verification guide](https://github.com/HuggingMath/TheoremOS/blob/main/docs/VERIFY.md)
- [Research preview release](https://github.com/HuggingMath/TheoremOS/releases/tag/v0.1.0-preview.1)
- [Public materials and licensing](https://github.com/HuggingMath/TheoremOS/blob/main/docs/PUBLIC-MATERIALS.md)
