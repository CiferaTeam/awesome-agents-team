# TheoremOS

> Browser workbench where researchers guide AI agents through formal proofs in Lean 4 with Mathlib.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [theoremos.top](https://theoremos.top/en/) |
| **Repository** | [HuggingMath/TheoremOS](https://github.com/HuggingMath/TheoremOS) (public documentation, proof records, and verification materials) |
| **Status** | `Active` (research preview) |
| **Openness** | `Closed source` runtime |
| **Deployment** | `Cloud-hosted` (no local Lean installation required for the browser preview) |
| **First release** | 2026-11 (public research preview) |
| **Last release / commit** | 2026-11 (public repository) |
| **Language / Stack** | Lean 4 and Mathlib for formal verification. Hosted runtime stack unknown. |
| **License** | Proprietary runtime. Public artifacts retain their individual terms. |

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
- **Offline capability.** Downloadable verification kits include Lean files, pinned project settings, and instructions for repeating a check locally. Once the Lean dependencies are available, the check runs without a model call.
- **Vendor lock-in risk.** Moderate. Agent coordination depends on the hosted workbench. The exported proof files use standard Lean tooling.

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Research preview | $0 platform fee | Apply for access to run new tasks. Bring a key from a supported model provider and pay that provider for inference. |

## Ecosystem & Integrations

- **IDE integrations.** Unknown.
- **External services.** The workbench connects to selected model providers through the Responses API.
- **API / extensibility.** CLI collaboration is available by arrangement for multi-file Lake projects, custom toolchains, or research on strategies and scheduling.
- **Community.** [GitHub Issues](https://github.com/HuggingMath/TheoremOS/issues).

## vs GitIM

GitIM stores messages and task cards as Git commits. TheoremOS gives the researcher and agents a shared proof plan in a hosted workspace, with the formal goal and Lean check results alongside it. [GitIM documentation](https://github.com/CiferaTeam/GitIM)

## Screenshots / Demo

- In the public rehearsal, approve a plan for a preset problem, inspect a failed attempt, and choose a repair. The final screen shows the recorded Lean checks for that route. The rehearsal requires no account or API key. [Try the rehearsal](https://app.theoremos.top/practice.html?lang=en)
- The public archive contains proof records and verification material from completed and ongoing work. [Browse the archive](https://theoremos.top/en/archive)
- Researchers can apply for preview access to run a new task with their own model key. [Request access](https://github.com/HuggingMath/TheoremOS/issues/new?template=early-access.yml)

![TheoremOS statement review page showing an example problem and its generated Lean statement](https://raw.githubusercontent.com/HuggingMath/TheoremOS/61d105500484327dfa85ff69849ab7bd1b2ec69b/assets/guide/statement-review-en.png)

## References

- [Capabilities and access](https://github.com/HuggingMath/TheoremOS/blob/61d105500484327dfa85ff69849ab7bd1b2ec69b/docs/CAPABILITIES.md)
- [Workbench tutorial and export instructions](https://github.com/HuggingMath/TheoremOS/blob/61d105500484327dfa85ff69849ab7bd1b2ec69b/docs/GETTING-STARTED.md)
- [Local verification guide](https://raw.githubusercontent.com/HuggingMath/TheoremOS/61d105500484327dfa85ff69849ab7bd1b2ec69b/docs/VERIFY.md)
- [Research preview release](https://github.com/HuggingMath/TheoremOS/releases/tag/v0.1.0-preview.1)
- [Public materials and licensing](https://github.com/HuggingMath/TheoremOS/blob/61d105500484327dfa85ff69849ab7bd1b2ec69b/docs/PUBLIC-MATERIALS.md)
