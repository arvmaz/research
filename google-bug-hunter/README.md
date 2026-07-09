# Google Bug Bounty — Research & Participation Tracker

Private research repository for Google VRP (Vulnerability Reward Program) activities.

## What's Here

- `google-bug-bounty-report.md` — Full program overview: payment options, reward tiers, all programs
- `oss-fuzz-research.md` — Google OSS-Fuzz participation analysis (free fuzzing infra, NOT a bug bounty)
- `tsunami-research.md` — Tsunami Security Scanner architecture, plugin types, reward structure
- `patch-rewards-plugin-research.md` — Detailed Tsunami/OSV-SCALIBR plugin development guide, target selection
- `participation-roadmap.md` — Actionable roadmap: which programs to target, first steps
- `ai-vrp-research.md` — AI VRP coverage (Gemini, Vertex AI)
- `reward-tiers.md` — Current reward maximums per program (May 2026)
- `bugcrowd-setup.md` — Bugcrowd account setup notes

## Programs in Scope

| Program | Priority | How to Participate |
|---------|----------|-------------------|
| Patch Rewards (Tsunami/OSV-SCALIBR) | **High** | Write scanner plugins |
| AI VRP | Medium | Find AI/ML vulnerabilities |
| Chrome/Android VRP | Long-term | Standard web/browser vulns |

## Key Distinction

- **OSS VRP** = find bugs IN Google's own open source
- **Patch Rewards** = write security improvements TO third-party OSS (via Tsunami plugins)
- **OSS-Fuzz** = free fuzzing service for OSS maintainers (not a researcher pathway)
