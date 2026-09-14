# QuantDinger

> Self-hosted trading workspace where AI clients can research markets, author Python strategies, and request backtests through a scoped MCP gateway.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [quantdinger.com](https://www.quantdinger.com) |
| **Repository** | [OpenByteInc/QuantDinger](https://github.com/OpenByteInc/QuantDinger) |
| **Status** | Active |
| **Openness** | Open-source backend; separately licensed source-available web and mobile clients |
| **Deployment** | Self-hosted Docker Compose; hosted application also available |
| **First release** | Unknown |
| **Last release / commit** | 2026-09 |
| **Language / Stack** | Python, Flask, Celery, PostgreSQL, Redis; separate web and mobile clients |
| **License** | Apache-2.0 for the backend; client repositories have their own terms |

## What It Does

QuantDinger connects market research, Python strategy development, backtesting, and paper/live execution in a trading-specific workspace. Human users and MCP clients access a common backend service layer. Operators choose data and model providers, review strategy code, and configure execution permissions.

## Key Mechanisms

- **Strategy API V2**: Python sources declare their universe, subscriptions, warmup, and callbacks. Compilation produces a manifest used by strategy and backtest workflows.
- **Scoped Agent Gateway**: The MCP server wraps `/api/agent/v1` with tenant tokens, bounded asynchronous jobs, and idempotency keys for mutations. Clients do not receive broker credentials.
- **Explicit runtime ownership**: Separate trading workers own long-running strategies, while Celery handles finite research and backtest jobs. PostgreSQL stores durable state; separate Redis instances handle cache and jobs.

## Agent Architecture

- **Agent model**: Human-in-the-loop financial research and tool use; external AI clients connect through MCP.
- **Coordination mechanism**: API calls, persisted strategy sources, and asynchronous job IDs/results. This is a domain workflow, rather than a general peer-agent messaging protocol.
- **Human oversight**: Operators control scoped tokens, allowlists, and order limits. Agent trading defaults to paper-only; live access additionally requires token and server authorization and explicit order confirmation.

## Data & Storage Model

- **Primary store**: Operator-managed PostgreSQL with Redis cache and durable job infrastructure.
- **Data portability**: Strategy sources are Python; API contracts are documented with OpenAPI. Database backups remain the operator's responsibility; a universal one-click workspace export is not documented.
- **Offline capability**: Local hosting is supported, but external market data, hosted models, and broker connections require network access.
- **Vendor lock-in risk**: The Apache-2.0 backend and documented APIs reduce backend dependency. Model/data providers and separately licensed clients introduce their own dependencies and terms.

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Backend / self-hosted | $0 software license fee | Infrastructure, model/data services, and broker fees are separate; client licenses differ |
| Hosted / commercial services | See provider | Commercial terms and branding permissions are managed separately |

## Ecosystem & Integrations

- **MCP clients**: Documented setup for clients such as Cursor, Claude Code, and Codex; stdio, SSE, and streamable HTTP transports.
- **External services**: Crypto exchange adapters plus Alpaca and Interactive Brokers workflows; configurable AI providers.
- **API / extensibility**: Python Strategy API V2, Human API, Agent Gateway, and an included MCP server package.
- **Community**: [GitHub Issues](https://github.com/OpenByteInc/QuantDinger/issues) and community links in the project README.

## Example Workflow

For a concrete strategy-authoring walkthrough, start from the public [moving-average strategy example](https://github.com/OpenByteInc/QuantDinger/blob/main/docs/examples/strategy_v2_dual_ema_long.py). It declares daily SPY bars and compares fast and slow rolling means before setting a target allocation.

1. Install a local instance using the repository's quick start and configure a scoped Agent Token.
2. Connect the included MCP server and compile the example source with `compile_strategy_code`.
3. Submit a dated backtest with `submit_backtest`, supplying the source, capital, parameters, and a unique idempotency key; obtain results with bounded job polling.
4. Review the source and backtest assumptions before saving a strategy source or considering deployment.

This illustrates the documented workflow, not a published performance result. The sample filename says EMA, but the current implementation calculates simple rolling means. Data availability and backtest assumptions affect the result.

## Compared with GitIM

GitIM coordinates general-purpose agents through Git-backed channels, messages, and task cards. QuantDinger supplies trading-specific research, backtest, and execution tools with database-backed state. QuantDinger is a closer fit for a financial strategy workflow; GitIM is a closer fit for teams needing portable, general-purpose agent communication. QuantDinger does not replace GitIM's Git-native messaging model.

## Screenshots / Demo

- [Product animation in the official README](https://github.com/OpenByteInc/QuantDinger#watch-quantdinger-in-action)
- [Architecture diagram and process responsibilities](https://github.com/OpenByteInc/QuantDinger#architecture)

## References

- [Official repository and license boundaries](https://github.com/OpenByteInc/QuantDinger#license-and-commercial-terms)
- [MCP server source, installation, and tool workflow](https://github.com/OpenByteInc/QuantDinger/tree/main/mcp_server)
- [Agent documentation and OpenAPI](https://github.com/OpenByteInc/QuantDinger/tree/main/docs/agent)
- [Strategy runtime implementation](https://github.com/OpenByteInc/QuantDinger/tree/main/backend_api_python/app/services/strategy_v2)
- [GitIM architecture reference](gitim.md)
