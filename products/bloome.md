# Bloome

> AI agent that continuously scans the job market and delivers a small set of explained, personalized matches — positioned as a matching engine rather than a keyword job board.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [bloome.ai](https://www.bloome.ai/) |
| **Product app** | [app.bloome.ai](https://app.bloome.ai/) |
| **Repository** | `Closed source` — no public GitHub org/repo found for Bloome AI (searched GitHub for `bloome.ai`, `Bloome AI`, `bloome-ai`) |
| **Status** | `Active` / `Beta` — marketing site live; founder resume lists launch May 2025; several features described as piloting |
| **Openness** | `Freemium` — free job-seeker tier; paid subscriptions and credit-based paid actions per site copy |
| **Deployment** | `Cloud-hosted` — web app; no local daemon or self-host option advertised |
| **First release** | 2025-05 *(founder resume; unverified against independent release log)* |
| **Last release / commit** | Unknown — no public changelog |
| **Language / Stack** | Unknown publicly — privacy policy names [Clerk](https://clerk.com/) for auth; remainder undisclosed |
| **License** | Proprietary — [Terms of Service](https://www.bloome.ai/terms) state IP owned by Bloome AI |

## What It Does

Bloome targets individual job seekers (and, separately, employers via sales contact). Users upload a CV, set preferences, and receive recurring **Daily Drop** shortlists with natural-language **reasons** for each match. The product also advertises resume optimization, AI-drafted application materials, optional **Apply For Me** email sending, and employer-side shortlist generation. It is **not** a developer multi-agent coordination tool; it is a vertical consumer agent for hiring workflows.

## Key Mechanisms

*(Facts from official marketing, terms, and privacy policy unless noted.)*

- **Continuous matching engine**: Market scanning and ranking run on Bloome’s infrastructure; users review outputs rather than running searches manually.
- **Explainable Daily Drop**: Each match is paired with stated fit rationale (homepage FAQ and product copy).
- **Profile signal loop**: Matching uses CV, stated preferences, feedback, and in-product behavior over time (homepage FAQ).
- **Apply For Me**: Terms describe AI-drafted materials and email sending for eligible roles where a direct recipient exists.
- **Employer workflow (B2B)**: Homepage describes role definition in plain language → shortlist with reasoning → “hire first, pay later” positioning; pricing and SLAs not public.

*(Opinion — reviewer judgment, not vendor claims.)*

- **“Agent” framing is accurate at product level** for a single long-running assistant that acts on the user’s behalf (scan, draft, optionally apply), but there is **no peer multi-agent** or team coordination surface comparable to dev-agent stacks.

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Single personal agent per job seeker; human-in-the-loop for review, feedback, and application approval |
| **Coordination mechanism** | Centralized cloud orchestration — no shared team state, Git, or message bus exposed to users |
| **Human oversight** | User reviews Daily Drop, edits AI drafts, controls Apply For Me; terms place final responsibility on the user for submitted materials |
| **Multi-agent** | Not applicable to public product — no documented agent-to-agent protocol |

*(Unverified — founder public resume, not bloome.ai docs.)*

- **Hands-Free** pilot: end-to-end application agent “under user supervision” ([deanshabi.com resume](https://deanshabi.com/resume)).

## Data & Storage Model

| Aspect | Detail |
|--------|--------|
| **Primary store** | Cloud — account, CV, profile, match history, and application artifacts on Bloome servers |
| **Auth** | Clerk (per [privacy policy](https://www.bloome.ai/privacy-policy)) |
| **Encryption** | TLS 1.3 in transit, AES-256 at rest (privacy policy) |
| **Data portability** | Export via account settings; machine-readable copy on request (privacy policy) |
| **Deletion** | Account Settings → Privacy → Delete Account; legal contact `legal@bloome.ai` |
| **Offline capability** | No — requires connectivity to app and backend |
| **Vendor lock-in risk** | **High** for coordination history — no Git/file-native audit trail; export exists but ongoing value (matching models, employer graph) stays on platform |

**Training use (fact):** Privacy policy states aggregated, anonymized data may improve matching; personal data is **not** used to train general-purpose AI models.

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Free (job seeker) | $0 | Daily matches, application drafts, CV tooling per homepage FAQ; **Daily Drop volume cap** on free tier per [terms](https://www.bloome.ai/terms) |
| Credits (usage) | Unverified $ | Homepage FAQ: credits apply when Bloome **actively applies** or runs **deep company research** |
| Paid subscription | Unverified $ | Terms reference paid tiers with auto-renewal; **no public price table** found on bloome.ai or app landing (searched homepage, `/terms`, `/privacy-policy`, `app.bloome.ai` — 2026-05-19) |
| Employer / hiring | Contact sales | `hello@bloome.ai` — no public rate card |

## Ecosystem & Integrations

- **Inputs**: CV upload; optional LinkedIn, GitHub, portfolio links (privacy policy).
- **IDE / dev tools**: None — out of scope for this product.
- **Job boards**: Aggregates/indexes market roles (marketing: ~7M roles, 300k+ companies) — **underlying data vendors not named** publicly.
- **API / plugins**: None advertised.
- **Community**: No official Discord, forum, or docs site found — support via `hello@bloome.ai` / `legal@bloome.ai` only.

## Screenshots / Demo

- [Marketing site](https://www.bloome.ai/) — product narrative, testimonials, employer section.
- [Web app entry](https://app.bloome.ai/) — sign-up / login (content requires account).

No public demo video or screenshot gallery URL found.

## Name collisions (research log)

Searched to disambiguate **Bloome** (`bloome.ai`) from similarly named products:

| Name | Domain | Relation to this page |
|------|--------|------------------------|
| Bloom (SWE job search) | bloomhq.ai | **Different product** — auto-apply for software engineers |
| Bloom (dev orchestration) | use-bloom.dev | **Different** — YAML multi-agent dev tasks |
| Bloomneo | github.com/bloomneo | **Different** — npm agentic app scaffolds |
| video-db/bloom | github.com/video-db/bloom | **Different** — screen recording / Loom alternative |

## vs GitIM

GitIM ([gitim.io](https://gitim.io)) is a **Git-native IM and coordination layer for humans and coding agents** in a shared workspace. Bloome is a **consumer hiring agent**. Comparison is cross-domain but useful for the awesome-list “agent systems” lens.

| Dimension | Bloome | GitIM |
|-----------|--------|-------|
| Primary use case | Personal job search & applications | Team dev work: channels, cards, agents over Git |
| Data ownership | User can export/delete cloud profile; operational truth on Bloome servers | Git repo — coordination and artifacts user-controlled |
| Agent coordination | One agent ↔ one user; no team agent protocol | Multi-agent + human peers; Git commits / workspace events as coordination |
| Offline / local-first | Cloud-only | Git + local runtime; meaningful offline until sync |
| Openness | Closed source, proprietary | Open coordination model tied to Git; product/runtime openness varies by deployment |
| Team collaboration UX | Individual job seeker; employer flow is separate sales motion | Built for multi-person, multi-agent engineering teams |
| Ecosystem | Hiring / HR adjacency | CI, PR tools, IDEs, entire Git toolchain |

**Summary (opinion):** Bloome wins when the problem is **finding and applying to jobs** with a polished consumer UX and no infrastructure to run. GitIM wins when the problem is **shared, auditable, vendor-independent coordination** among humans and coding agents on real work products. They are complements at best, not substitutes.

## References

- [Bloome homepage](https://www.bloome.ai/)
- [Bloome web app](https://app.bloome.ai/)
- [Terms of Service](https://www.bloome.ai/terms) — features, subscriptions, entity: Bloome AI, Dean Shabi, IČO 21740330, Prague
- [Privacy Policy](https://www.bloome.ai/privacy-policy) — Clerk, GDPR/CCPA, export/delete
- [Founder resume — Dean Shabi](https://deanshabi.com/resume) — launch timing, Apply Pro, Hands-Free pilot *(third-party personal site)*

**Not found (2026-05-19):** public GitHub, npm package, docs portal, pricing page, status page, HN/PH launch thread, independent technical teardown.

---

*Page maintained by @cursor-composer25-fast (Phase 1 batch 1). Last verified: 2026-05.*
