# Google Bug Bounty Program — Payment Options & Practicality Report

**Date:** 2026-05-21
**Source:** https://bughunters.google.com/

---

## Overview

Google runs a family of Vulnerability Reward Programs (VRPs) through the Bug Hunters platform at bughunters.google.com. The programs pay researchers for finding security bugs in Google products. The platform has evolved significantly — in June 2024, Google added Bugcrowd as an integrated payment option.

---

## Payment Options

### 1. Bugcrowd (Primary Payment Platform)

In **June 2024**, Google announced Bugcrowd as an official payment option on bughunters.google.com. This is the main way to receive monetary rewards:

- Payments are processed through Bugcrowd's platform
- Bugcrowd supports: PayPal, bank transfer (various countries), gift cards, and charity donations
- Minimum payouts and processing times vary by method

**Practicality for us:**
Bugcrowd is well-established in the bug bounty space and supports multiple currencies and withdrawal methods including international options. This is likely the most practical path for receiving payments.

### 2. Direct Bank Transfer (Legacy)

Historically, Google VRP offered direct bank transfers for larger rewards. With the Bugcrowd integration, this may have been partially deprecated in favor of the Bugcrowd platform.

### 3. Swag / Merchandise (Legacy)

Early programs offered Google-branded merchandise (t-shirts, stickers) for valid reports, especially for lower-severity findings or when monetary rewards were not applicable. This appears to have been largely replaced by monetary rewards.

### 4. Certificate of Appreciation

Researchers receive a digital recognition profile on bughunters.google.com showing their CVE counts, report history, and ranking. This has reputational value but no direct monetary component.

---

## Reward Structure

Google VRP rewards are tiered by severity and impact:

| Severity | Typical Reward Range |
|----------|---------------------|
| Low | $100 – $1,000 |
| Medium | $1,000 – $7,500 |
| High | $7,500 – $15,000 |
| Critical | $15,000 – $151,515 |

**Key updates (2024–2026):**

- **July 2024:** Google increased max VRP rewards up to **$151,515** (5x previous maximum)
- **April 2026:** Chrome & Android VRPs restructured with "Information Tiers" and "Action Criticality" for AI-era bug categories
- **March 2025:** Android VRP offers **$1,000 bonus** for reports with AutoRepro test cases
- **AI Vulnerability Reward Program** (launched 2024): Separate program for AI/ML-focused vulnerabilities

---

## All Google Programs

### 1. Google VRP

Scope: google.com, Chrome, Android apps, and general Google products. The main program.

### 2. Chrome VRP

Scope: Chrome browser, ChromeOS. One of the highest-rewarding programs.

### 3. Android VRP

Scope: Android OS, Pixel devices. Includes $1,000 bonus for AutoRepro test cases.

### 4. Google Cloud VRP

Scope: GCP services. Enhanced reward transparency as of September 2025.

### 5. AI Vulnerability Reward Program (AI VRP)

Launched late 2024 / early 2025. Covers Gemini, Vertex AI, and AI products. May be less mature and less competitive than established programs — potential opportunity.

### 6. Google OSS VRP (Open Source VRP)

Scope: **Google-maintained open source projects** (not third-party OSS). Recent updates in March 2026 streamlined rules to filter low-quality reports and focus on real-world impact. This program specifically rewards finding vulnerabilities in Google's own open source work — the code Google writes and maintains, not arbitrary OSS.

**Key note:** OSS VRP is distinct from Patch Rewards (below). OSS VRP is about finding bugs IN Google's OSS. Patch Rewards is about contributing security improvements TO third-party OSS.

### 7. Patch Rewards Program (Third-Party OSS)

Rewards for **security improvements to third-party open source projects**, not Google-owned code. Uses the Tsunami scanner plugin system.

- **Up to $10,000** per valid plugin or security improvement
- **January 2025 update:** increased reward amounts, introduced memory safety reward multipliers
- **August 2025:** new Patch Rewards program specifically for **OSV-SCALIBR** plugins (inventory, vulnerability, or secret detection)
- Memory safety contributions (Rust, C memory-safe alternatives) get boosted rewards

**How it works:** Researchers write Tsunami scanner plugins that detect vulnerabilities in open source projects. Plugins must be novel and provide meaningful security improvement. Reward based on impact and quality.

### 8. InternetCTF

A bug bounty program structured as a CTF (capture the flag). Up to **$10,000** total for finding novel remote code execution vulnerabilities in OSS AND providing Tsunami plugin patches for them.

---

## Programs at a Glance

| Program | What it covers | Reward range |
|---------|----------------|--------------|
| Google VRP | google.com, general products | $100 – $151,515 |
| Chrome VRP | Chrome, ChromeOS | $100 – $151,515 |
| Android VRP | Android OS, Pixel | $100 – $151,515 + $1k AutoRepro bonus |
| Cloud VRP | GCP services | $100 – $151,515 |
| AI VRP | Gemini, Vertex AI, AI products | varies |
| **OSS VRP** | **Google's own open source projects** | varies |
| **Patch Rewards** | **Third-party OSS via Tsunami plugins** | **up to $10,000** |
| InternetCTF | OSS RCE + Tsunami plugin | up to $10,000 |

---

## Practicality Assessment for Our Use Case

| Factor | Assessment |
|--------|------------|
| **Eligibility** | Anyone can register and submit reports |
| **Payment Speed** | Bugcrowd processes payments on standard schedules |
| **International** | Bugcrowd supports many countries |
| **Minimum Payout** | Varies by method — Bugcrowd has lower minimums than direct transfer |
| **Tax Implications** | Rewards may be taxable income depending on jurisdiction |
| **Effort Required** | Finding valid, novel vulnerabilities requires significant skill and time |

---

## Key Caveats

- The bughunters.google.com site is heavily JavaScript-rendered — it requires browser interaction to access most content. Direct API exploration via curl was not successful.
- The Bugcrowd integration was announced publicly in June 2024 — details of the exact payment mechanics (fees, currencies, withdrawal limits) should be confirmed directly via the platform.
- Reward amounts are at Google's discretion and depend heavily on report quality, reproducibility, and security impact.

---

## Recommendations

1. **If the goal is receiving money:** Register on bughunters.google.com and set up the Bugcrowd integration. This is the official and most practical payment path.
2. **If the goal is maximizing reward value:** Focus on critical/high-severity vulnerabilities in Chrome, Android, or Google Cloud — these have the highest reward potential.
3. **For AI-related research:** The AI VRP (launched 2024) may be less mature and potentially less competitive — could be an opportunity.
4. **For open source contributions:** The Patch Rewards Program offers rewards for Tsunami scanner plugins (up to $10,000) — lower barrier to entry than finding novel CVEs.
5. **To contribute to Google's OSS:** The OSS VRP rewards findings in Google's own open source projects — different from Patch Rewards which targets third-party OSS.
6. **For structured research with clear goals:** InternetCTF offers a CTF-format challenge with up to $10,000 for RCE + plugin submissions.

---

## Sources

- https://bughunters.google.com/ (homepage — JS-rendered SPA)
- https://bughunters.google.com/blog/announcing-bugcrowd-as-a-new-bughuntersgooglecom-payment-option (June 2024)
- https://bughunters.google.com/blog/increasing-google-alphabet-vrp-rewards-up-to-151515 (July 2024)
- https://bughunters.google.com/blog/evolving-the-android-chrome-vrps-for-the-ai-era (April 2026)
- https://bughunters.google.com/blog/standardizing-rewards-in-google-vrp (April 2026)
- https://bughunters.google.com/blog/ossvrp-rule-updates-2026 (March 2026)
- https://bughunters.google.com/blog/level-up-your-open-source-karma-and-your-wallet-by-improving-security (January 2025)
- https://bughunters.google.com/blog/new-patch-rewards-program-for-osv-scalibr (August 2025)
- https://bughunters.google.com/blog/capturing-the-flags-of-the-internet-find-0-days-in-oss-and-write-scanners-to-detect-them (January 2025)
- https://bughunters.google.com/blog/announcing-googles-new-ai-vulnerability-reward-program (October 2025)
- https://bughunters.google.com/feed/en (RSS — Security Engineering Blog)