# Zylos Zalo

> Zalo Bot Platform communication channel for the Zylos agent runtime. Enables two-way messaging, group chat routing, and media forwarding between a Zylos AI agent and Zalo users via polling or webhook delivery.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | Part of [Zylos / COCO ecosystem](https://coco.xyz/) |
| **Repository** | [github.com/zylos-ai/zylos-zalo](https://github.com/zylos-ai/zylos-zalo) |
| **Status** | `Active` — initial release 2026-05-20; rapid iteration through 2026-05-25 |
| **Openness** | `Open source (MIT)` |
| **Deployment** | `Self-hosted` — installed as a Zylos skill component; runs alongside Zylos core via PM2 |
| **First release** | 2026-05-20 |
| **Last release / commit** | 2026-05-25 |
| **Language / Stack** | JavaScript (Node.js 20+); zero npm dependencies |
| **License** | MIT |

## What It Does

Zylos Zalo is a communication bridge that connects a Zylos AI agent to the Zalo Bot Platform. It acts as a channel plugin within the Zylos component system, handling inbound and outbound messages, images, and stickers while enforcing access policies for DMs and group chats.

The plugin supports two delivery modes — long polling for quick local testing without a public URL, and webhook for production deployments. All messages are routed through the Zylos C4 communication bridge, giving the agent a unified consciousness across Telegram, Lark, web console, and Zalo.

## Key Mechanisms

- **Dual delivery modes**: Long polling (default, no public URL needed) and webhook (production with timing-safe secret verification, rate limiting, and short-window replay deduplication)
- **DM access control**: Configurable policies — owner auto-binding, explicit allowlist, open, or owner-only — preventing unauthorized users from interacting with the agent
- **Group routing**: Allowlisted group chats with per-group sender allowlists, replayed context history, and mention-only or open reply modes
- **Inbound media handling**: Downloads received Zalo images into component media storage and forwards them to the C4 bridge as file attachments; sticker support in both directions
- **Outbound formatting**: Markdown is flattened before sending; long messages are split on paragraph boundaries; typing indicators are sent while the agent generates a response
- **Zero npm dependencies**: Built entirely on Node.js built-in APIs for minimal supply-chain surface
- **Admin CLI**: Scripts for viewing and modifying configuration (DM policy, delivery mode, allowlists) without hand-editing JSON

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Single Zylos agent runtime with channel-agnostic consciousness; Zalo is one of multiple parallel channels (Telegram, Lark, Web Console) |
| **Coordination mechanism** | C4 bridge routes all Zalo messages into the agent's unified session; the agent responds once and the bridge dispatches the reply back to the originating channel |
| **Human oversight** | Owner binding and allowlist policies gate who can trigger the agent; group policies restrict which chats the agent participates in |
| **Multi-agent protocol** | N/A — this is a channel adapter, not a multi-agent orchestrator; multi-agent behavior is handled by the underlying Zylos core |

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | Zylos core manages persistent memory and SQLite audit logs; this plugin stores configuration in `~/zylos/components/zalo/config.json` and media downloads in component-local storage |
| **Data portability** | Configuration is plain JSON; media files are local files on disk. Full portability depends on the underlying Zylos core |
| **Offline capability** | Polling mode works without a public URL but still requires outbound internet to reach Zalo APIs. Webhook mode requires public ingress |
| **Vendor lock-in risk** | **Low** for the plugin itself (MIT, plain JSON config, local files). Messaging is tied to the Zalo Bot Platform API, but the C4 abstraction allows swapping to other channels without changing agent logic |

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Open source | $0 | Self-host alongside Zylos core; bring your own Zalo bot token |

Zalo Bot Platform API usage may incur charges from Zalo depending on volume; the plugin itself has no monetization.

## Ecosystem & Integrations

- **Agent runtime**: Zylos core (Claude Code or Codex runtime via tmux)
- **Communication bridge**: Zylos C4 bridge for unified cross-channel routing
- **Platform**: Zalo Bot Platform (bot-api.zaloplatforms.com)
- **Sibling channels**: [zylos-core](https://github.com/zylos-ai/zylos-core) supports Telegram, Lark, and Web Console through analogous plugins
- **Deployment**: PM2 process management; Docker via Zylos core image
- **Community**: GitHub Issues on [zylos-ai/zylos-zalo](https://github.com/zylos-ai/zylos-zalo)

## Screenshots / Demo

- [Zylos Core repository — architecture diagram showing C4 bridge and channel plugins](https://github.com/zylos-ai/zylos-core)
- [Zylos Zalo repository — configuration examples and admin CLI usage](https://github.com/zylos-ai/zylos-zalo)

## References

- [Zylos Zalo repository](https://github.com/zylos-ai/zylos-zalo)
- [Zylos Core repository](https://github.com/zylos-ai/zylos-core)
- [COCO homepage](https://coco.xyz/)
- [Zalo Bot Platform](https://bot.zaloplatforms.com/)
