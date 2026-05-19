# 牛马AI (Niuma AI)

> Local-first AI workstation for individuals and teams — parse documents, orchestrate tasks, switch models freely, and keep data on-device by default.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [niuma.limyai.com](https://niuma.limyai.com/) |
| **Repository** | `Closed source` — no public GitHub org/repo confirmed |
| **Status** | `Active` — marketing site and security whitepaper live (updated 2026-02 per site) |
| **Openness** | `Freemium` — core features free; enterprise tier advertised on homepage |
| **Deployment** | `Local-first` — local storage and optional fully offline use with on-device models; optional cloud model APIs via encrypted relay or user API keys |
| **First release** | Unknown |
| **Last release / commit** | Unknown — desktop app distributed from homepage ("GET IT FREE") |
| **Language / Stack** | Next.js site; "Powered By Kova" (homepage footer); entity **NewMax AI** |
| **License** | Proprietary |

## What It Does

牛马AI (branded **Niuma AI** in English contexts) positions itself as a **localized human–machine collaboration hub** for privacy-sensitive professionals and solo operators. Users run an on-device agent that ingests mixed media (PDF, Office, audio/video), executes multi-step workflows, switches among cloud or local LLMs, connects to local creative tools (e.g. CapCut, Photoshop, Figma), and pushes completion alerts to Feishu or WeCom webhooks. Prebuilt **牛马棚** expert agents cover research, media, data, content, and speech workflows.

## Key Mechanisms

- **Local-first data plane**: Conversations, files, and config stay on the device; vendor claims no user content on their servers ([security whitepaper](https://niuma.limyai.com/security)).
- **Optional cloud models with relay or BYOK**: Cloud LLM calls can go through encrypted pass-through (no content logging per whitepaper) or direct via user-supplied API keys.
- **Offline / local models**: Supports Ollama, LM Studio, and similar local inference for air-gapped use.
- **Multi-format knowledge ingestion**: Parses documents and AV into a private knowledge base for agent use.
- **Task orchestration**: Decomposes instructions and invokes local tools/apps in sequence.
- **牛马棚 expert library**: Curated agent personas for vertical tasks (research digests, AV pipelines, Excel/SQL analytics, WeChat/RedNote publishing, meeting transcription).
- **Notification integrations**: Feishu, WeCom webhooks, and custom bots on job completion.

## Agent Architecture

- **Agent model**: Primarily single-user assistant with a **library of specialist agents** (牛马棚); human-in-the-loop for review and approval
- **Coordination mechanism**: Local task orchestration and scheduled/event triggers — not a shared team message bus
- **Human oversight**: User defines jobs, reviews outputs, controls model keys and network mode (offline vs cloud)

## Data & Storage Model

- **Primary store**: Local device database and filesystem (per security whitepaper)
- **Data portability**: Local files user-visible; uninstall removes local data per vendor documentation
- **Offline capability**: Yes with local models; cloud models require network
- **Vendor lock-in risk**: **Low–Medium** for data (local retention) / **Medium** for workflows tied to proprietary app and 牛马棚 templates

Anonymous usage telemetry (launch counts, feature frequency, crashes without chat content, coarse geo) is collected per the security whitepaper; conversation content is claimed excluded.

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Core | $0 | Homepage states core functionality is free |
| Enterprise | Unknown | Mentioned on site; no public price table |

## Ecosystem & Integrations

- **Cloud LLMs**: GPT, Gemini, Kimi, Minimax, Qwen, DeepSeek, Zhipu; third-party API proxies supported
- **Local LLMs**: Ollama, LM Studio, and similar
- **Creative / productivity**: CapCut (剪映), Photoshop, Figma (local app bridging per marketing copy)
- **Notifications**: Feishu, WeCom webhooks, custom bots
- **Founder / distribution**: Promoted via founder [@yangyi](https://x.com/yangyi) on X (verified); also listed on 小红书, 即刻, WeChat 公众号 **Yangyigrow**
- **Related product**: [xaicreator.com](https://xaicreator.com) — social management tool from same founder (per public profiles)

## Screenshots / Demo

- [Homepage](https://niuma.limyai.com/)
- [Security whitepaper](https://niuma.limyai.com/security)

## vs GitIM

| Dimension | 牛马AI (Niuma) | GitIM |
|-----------|----------------|-------|
| Primary use case | Personal/team productivity agent on local files and apps | Multi-human, multi-coding-agent coordination over a Git workspace |
| Data ownership | Local device + optional cloud LLM vendors | Git repository — coordination and artifacts user-owned |
| Agent coordination | Orchestrated tasks and expert library on one machine | Async Git events, channels, cards — team-visible audit trail |
| Offline / local-first | Core positioning; local models supported | Git-native offline until push |
| Openness | Closed-source desktop app | Open coordination model on Git |
| Team collaboration UX | Individual/small-team automation; IM webhooks for alerts | Built for engineering teams sharing repo-backed state |
| Ecosystem | CN productivity stack (Feishu/WeCom, local creative apps) | CI, PR, IDE, entire Git toolchain |

**Summary:** 牛马AI fits privacy-sensitive solo or small-team **local AI work** with rich file/tool integrations. GitIM fits **shared, auditable multi-agent engineering** where the coordination record must live in Git.

## References

- [牛马AI homepage](https://niuma.limyai.com/)
- [Security whitepaper](https://niuma.limyai.com/security)
- [@yangyi on X](https://x.com/yangyi)
- [xaicreator.com](https://xaicreator.com)
