# Bloome

> AI agent that continuously scans the job market and delivers a small set of explained, personalized matches — positioned as a matching engine rather than a keyword job board.

## Overview

| Field | Value |
|-------|-------|
| **Homepage** | [bloome.ai](https://www.bloome.ai/) |
| **Product app** | [app.bloome.ai](https://app.bloome.ai/) |
| **Repository** | `Closed source` — no public GitHub org/repo found |
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

- **Continuous matching engine**: Market scanning and ranking run on Bloome’s infrastructure; users review outputs rather than running searches manually.
- **Explainable Daily Drop**: Each match is paired with stated fit rationale (homepage FAQ and product copy).
- **Profile signal loop**: Matching uses CV, stated preferences, feedback, and in-product behavior over time (homepage FAQ).
- **Apply For Me**: Terms describe AI-drafted materials and email sending for eligible roles where a direct recipient exists.
- **Employer workflow (B2B)**: Homepage describes role definition in plain language → shortlist with reasoning → “hire first, pay later” positioning; pricing and SLAs not public.

## Agent Architecture

| Aspect | Detail |
|--------|--------|
| **Agent model** | Single personal agent per job seeker; human-in-the-loop for review, feedback, and application approval |
| **Coordination mechanism** | Centralized cloud orchestration — no shared team state, Git, or message bus exposed to users |
| **Human oversight** | User reviews Daily Drop, edits AI drafts, controls Apply For Me; terms place final responsibility on the user for submitted materials |
| **Multi-agent** | Not applicable to public product — no documented agent-to-agent protocol |

- **Hands-Free** pilot: end-to-end application agent under user supervision ([deanshabi.com resume](https://deanshabi.com/resume)).

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

Privacy policy states aggregated, anonymized data may improve matching; personal data is not used to train general-purpose AI models.

## Pricing

| Tier | Price | Limits |
|------|-------|--------|
| Free (job seeker) | $0 | Daily matches, application drafts, CV tooling per homepage FAQ; Daily Drop volume cap on free tier per [terms](https://www.bloome.ai/terms) |
| Credits (usage) | Unverified | Credits apply when Bloome actively applies or runs deep company research (homepage FAQ) |
| Paid subscription | Unverified | Terms reference paid tiers with auto-renewal; no public price table on marketing site or app landing |
| Employer / hiring | Contact sales | `hello@bloome.ai` |

## Ecosystem & Integrations

- **Inputs**: CV upload; optional LinkedIn, GitHub, portfolio links (privacy policy).
- **IDE / dev tools**: None — out of scope for this product.
- **Job boards**: Aggregates/indexes market roles (marketing cites large role/company counts; underlying data vendors not named publicly).
- **API / plugins**: None advertised.
- **Community**: No official Discord, forum, or docs site found — support via `hello@bloome.ai` / `legal@bloome.ai`.

## Screenshots / Demo

- [Marketing site](https://www.bloome.ai/)
- [Web app entry](https://app.bloome.ai/)

## References

- [Bloome homepage](https://www.bloome.ai/)
- [Bloome web app](https://app.bloome.ai/)
- [Terms of Service](https://www.bloome.ai/terms)
- [Privacy Policy](https://www.bloome.ai/privacy-policy)
- [Dean Shabi resume](https://deanshabi.com/resume)
