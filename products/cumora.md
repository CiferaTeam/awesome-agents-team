# Cumora

> Desktop-first team chat where humans and AI agents are coworkers — persistent memory, proactive initiative, and agent-to-agent collaboration in shared workspaces.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [cumora.ai](https://cumora.ai/) |
| **Repository** | Unknown — no public product repo found on GitHub |
| **Status** | `Active` — public preview; desktop downloads for macOS, Windows, Linux |
| **Openness** | `Freemium` — "Free during preview" on homepage; no public source repo |
| **Deployment** | `Hybrid` — native desktop app ("running locally"); web client and mobile share live state with cloud sync (implied) |
| **First release** | Unknown — preview period; exact launch date not published |
| **Last release / commit** | Unknown — desktop builds distributed from homepage |
| **Language / Stack** | Electron desktop app (per homepage meta keywords); backend stack unverified |
| **License** | Unverified — no public source or license file found |

## What It Does

Cumora is a team collaboration surface positioned against "chatbox you babysit" agents: agents are room members with personas, private workspaces, and social memory ("climate" toward teammates). Humans invite colleagues by email or link, organize agents into companies/projects, and work across desktop, web, and mobile with shared live state. Idle agents can wake on a schedule, observe the room, and initiate DMs, posts, or small-group threads without a human prompt.

## Key Mechanisms

- **Persistent agent memory**: Each agent keeps a private workspace (files, notes, observations) and remembers prior conversations and room mood.
- **Proactive initiative**: Configurable timer cadence lets idle agents decide whether to message someone, post a thought, or convene a subgroup.
- **Personas**: Agents ship with editable role, voice, and system prompt; default starter cast (Atlas, Iris, Bram, Nova) can be replaced.
- **Agent-to-agent**: Agents DM each other; "whisper" rooms expose agent-only threads to humans without joining.
- **Convene**: Agents can open a focused decision session with attendees, topic, and recorded outcome.
- **Cross-platform workspace**: Desktop (macOS Apple silicon/Intel, Windows x64, Linux AppImage/.deb), plus web and mobile sharing the same state.

## Agent Architecture

- **Agent model**: Multi-agent peer + human-in-loop; default hierarchical flavor via PM/researcher/designer/engineer starter roles
- **Coordination mechanism**: Real-time workspace/chat state (cloud-synced across clients); proactive scheduler; Convene for structured decisions
- **Human oversight**: Humans invite members, edit personas, and observe whisper rooms; agents can initiate but operate inside workspace policy

## Data & Storage Model

- **Primary store**: Unverified — homepage emphasizes local desktop execution and agent private workspaces; multi-client sync implies hosted coordination state
- **Data portability**: Unknown — no documented export path
- **Offline capability**: Partial — desktop app advertised; continuous sync across web/mobile suggests online dependency for team state
- **Vendor lock-in risk**: **Medium** — preview SaaS with no public repo; workspace and conversation history likely tied to Cumora cloud

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Preview | $0 | "Free during preview" — post-preview pricing unverified |

## Ecosystem & Integrations

- **Clients**: macOS, Windows, Linux desktop; web and mobile (mentioned on homepage)
- **IDE integrations**: None confirmed
- **External services**: None confirmed in public marketing copy
- **API / extensibility**: Unknown
- **Community**: Unknown — no Discord/forum link on homepage

## Screenshots / Demo

- [Cumora homepage](https://cumora.ai/)
- [Open Graph preview image](https://cumora.ai/assets/og-image.png)

## vs GitIM

| Dimension | Cumora | GitIM |
|-----------|--------|-------|
| Data ownership | Likely cloud workspace + local agent files; export path unknown | Git repo — coordination and artifacts user-owned |
| Agent coordination | Realtime chat, proactive timers, whisper/Convene UX | Git commits / workspace events — async, append-only, auditable |
| Offline / local-first | Desktop runs locally; team state syncs online | Git-native; meaningful offline until push |
| Openness | Closed preview product; no public source | Open coordination model on Git |
| Team collaboration UX | Familiar chat + autonomous agents; low Git literacy bar | Commit/channel model for developers; auditable but steeper for non-devs |
| Ecosystem | Packaged desktop + personas; early, integrations TBD | Entire Git/CI/review toolchain |

**Summary:** Cumora fits productized proactive multi-agent chat with persona-rich coworkers. GitIM fits when the coordination record must live in Git.

## References

- [Cumora homepage](https://cumora.ai/)
- [Multica](https://multica.ai/)
- [Slock](https://slock.ai/)
