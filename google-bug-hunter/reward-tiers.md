# Google VRP: Reward Tier Updates (May 2026)

**Task:** t_4c2217a3
**Parent:** t_21502fb6
**Sister task:** t_cc013f56 (Bug Bounty participation roadmap)

## Overview

This document tracks the current reward tier structures across Google's vulnerability reward programs as of May 2026. Parent task t_21502fb6 established the participation roadmap; this document focuses specifically on reward amounts and tier changes.

---

## Google VRP (General)

**Max reward:** $151,515 (since March 2024 increase from ~$31,337)

The general Google VRP covers Google products and services not covered by specialized programs. Rewards based on severity and exploit complexity.

**Source:** security.googleblog.com/2024/03/increasing-google-alphabet-vrp-rewards-up-to-151515

---

## Chrome VRP

**Max reward:** $250,000

Chrome VRP is one of Google's most lucrative programs. Tiers based on impact level:
- RCE with renderer sandbox escape: up to $250,000
- Full Chrome browser RCE: up to $180,000
- UX bypasses, information disclosure: lower tiers

**Key change (2024):** Chrome rewards peaked at $250,000 (previously lower).

**Source:** bughunters.google.com blog post referenced in 2024 VRP update.

---

## Mobile VRP (Android)

**Max reward:** $300,000 (for critical vulnerabilities in top-tier apps)

Android-specific VRP covering the Google Play ecosystem:
- Critical severity in high-profile apps: up to $300,000
- Lower severity / less critical targets: tiered below this

**Key change:** Mobile VRP saw reward increases in 2024 as part of the broader VRP restructure.

**Source:** bughunters.google.com/blog/5792192022577152/one-year-of-mobile-vrp-reward-increases-and-lessons-learned

---

## Cloud VRP

**Max reward:** $151,515

Covers Google Cloud Platform vulnerabilities. Reward tiers based on impact scope and sensitivity of affected infrastructure.

**Source:** bughunters.google.com/about/rules/google-friends/4849867320328192/cloud-vulnerability-reward-program-rules

---

## kvmCTF

**Reward tiers:**

| Impact Level | Reward |
|---|---|
| Full VM escape | $250,000 |
| Arbitrary memory write | $100,000 |
| Arbitrary memory read | $50,000 |
| Relative memory write | $50,000 |
| Denial of service | $20,000 |
| Relative memory read | $10,000 |

kvmCTF is a lab-based CTF-style program for KVM hypervisor vulnerabilities. Zero-day only (no n-day exploits rewarded).

**Source:** security.googleblog.com (kvmCTF announcement post)

---

## Patch Rewards

**Max reward:** $10,000 per plugin

For Tsunami scanner plugins and OSV-SCALIBR plugins detecting vulnerabilities in open source software.

- Memory-safe language contributions (Rust): reward multipliers apply
- OSV-SCALIBR track launched August 2025 — less competition than Tsunami track

**Source:** bughunters.google.com/blog/new-patch-rewards-program-for-osv-scalibr

---

## 2024 Year in Review Stats

- Total awarded in 2024: just shy of $12 million
- Total researchers paid: over 600
- Programs active: VRP, Mobile VRP, Cloud VRP, Chrome VRP, Abuse VRP, Patch Rewards, kvmCTF

**Source:** security.googleblog.com VRP 2024 roundup post

---

## Key Takeaways for Participation

1. **Highest per-bug:** Chrome VRP ($250K max) and kvmCTF ($250K VM escape)
2. **Specialized high-value:** Mobile VRP top-tier apps ($300K max)
3. **Easiest entry point:** Patch Rewards (write a plugin — no competition on finding bugs, just on quality of detection)
4. **Memory-safe multiplier:** Rust contributions to Patch Rewards get enhanced rewards

---

## Monitoring for Updates

Bookmark these for tracking tier changes:
- https://security.googleblog.com — VRP announcements
- https://bughunters.google.com — official program pages (requires JS rendering for current tiers)

Last updated: 2026-05-21