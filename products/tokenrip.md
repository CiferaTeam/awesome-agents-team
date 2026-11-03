# Tokenrip

> Hosted shared project records for people and agents running in their existing tools.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [tokenrip.com](https://tokenrip.com/) |
| **Repository** | Hosted service; [open-source CLI client](https://github.com/tokenrip/cli) |
| **Status** | Active |
| **Openness** | Closed-source hosted service; freemium; MIT CLI client |
| **Deployment** | Cloud-hosted |
| **First release** | Unknown |
| **Last release / commit** | 2026-11 (CLI repository) |
| **Language / Stack** | TypeScript CLI; hosted-service implementation unknown |
| **License** | MIT for CLI; hosted service subject to its terms |

## What It Does

Tokenrip stores project files, tables, decisions and tasks that connected agents can read and update. People can continue work across Claude, ChatGPT, Codex and other tools using the same project record. Agents stay in their existing hosts; Tokenrip does not supply the model or execute those hosts for them.

## Key Mechanisms

- **Shared records**: Files, tables, tasks and pinned decisions provide explicit project context across connected agents.
- **Write history**: Workspace content changes record the agent and a reason for the change.
- **Guarded coordination**: Tables can enforce one unique key; plain append can reserve an action and revision-guarded updates reject stale writes. This does not make external effects exactly-once.

## Agent Architecture

- **Agent model**: Multiple independently connected agents plus people.
- **Coordination mechanism**: Shared cloud workspace state through CLI, API or remote MCP.
- **Human oversight**: People inspect records and review proposals; external actions remain subject to each host and the person's instructions. No universal external-action approval gate is claimed.

## Data & Storage Model

- **Primary store**: Hosted workspace service; underlying database unknown.
- **Data portability**: Records are readable through the CLI/API. A complete lossless export guarantee is unknown.
- **Offline capability**: Hosted service requires a network connection.
- **Vendor lock-in risk**: Hosted state and API dependency; a Git-native storage guarantee is not documented.

## Compared with GitIM

GitIM's documented primary store is a Git repository and it runs local binaries. Tokenrip instead offers hosted project records through CLI/API/MCP while agents remain in their existing hosts. Choose based on the storage and operational model needed; Tokenrip is not a GitIM runtime adapter or a local Git message transport.

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Free | $0 | One person, unlimited guests/workspaces/agents, 2,500 actions/month, 1 GB |
| Pro | $20/member/month | Each member adds 25,000 actions/month and 5 GB |
| Power | $60/member/month | Each member adds 100,000 actions/month and 20 GB |
| Enterprise | Contact | Custom arrangements |

AI provider subscriptions are separate. See current pricing for billing terms.

## Ecosystem & Integrations

- **Agent hosts**: Claude, ChatGPT, Codex and other compatible agents; setup depends on host capabilities.
- **External services**: Unknown; no direct CRM or messaging connector coverage is asserted here.
- **API / extensibility**: Open-source CLI, HTTP API and hosted Streamable HTTP MCP endpoint at `https://api.tokenrip.com/mcp`.
- **Community**: Public CLI GitHub issues; other community channels unknown.

## Screenshots / Demo

- [Homepage interactive example workspace](https://tokenrip.com/#product) (illustrative example, not customer outcome evidence)
- [Agent setup guide](https://tokenrip.com/setup)

## References

- [Official documentation](https://docs.tokenrip.com/)
- [Table coordination](https://docs.tokenrip.com/concepts/tables#coordinating-agents)
- [Pricing](https://tokenrip.com/pricing)
- [CLI source](https://github.com/tokenrip/cli)
- [GitIM reference page](gitim.md)
