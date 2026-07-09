# Bug Bounty — Master Tracking

**Created:** 2026-05-21
**Repo:** github.com/arvmaz/bug-hunter

## Research Status

| Document | Task | Status |
|----------|------|--------|
| google-bug-bounty-report.md | t_4e3d905d | ✅ Complete |
| oss-fuzz-research.md | t_ed89e998 | ✅ Complete |
| tsunami-research.md | t_1575fe8d | ✅ Complete |
| patch-rewards-plugin-research.md | t_228e561e | ✅ Complete |
| participation-roadmap.md | t_cc013f56 | ✅ Complete |
| ai-vrp-research.md | t_f980e178 | ✅ Complete |
| reward-tiers.md | t_4c2217a3 | ✅ Complete |
| bugcrowd-setup.md | t_2c97bce9 | ✅ Complete |

## Next Action: Write First Tsunami Plugin

**Target:** OpenSSH CVE-2024-6387 (regreSSHion)
**Path:** `/plugin-development/openssh-cve-2024-6387/`
**Status:** Not started

See `patch-rewards-plugin-research.md` for full target selection rationale.

## Key Findings

1. **Best entry point:** Patch Rewards (Tsunami/OSV-SCALIBR plugins) — Hermes writes code directly
2. **Memory safety multiplier:** Rust/C contributions to Patch Rewards get boosted rewards
3. **OSV-SCALIBR is newer** (Aug 2025) — less competition
4. **AI VRP** is less mature — potential opportunity
5. **OSS-Fuzz is NOT a researcher pathway** — it's fuzzing infra for maintainers

## Account Setup Required (Human)

- [ ] Register at bughunters.google.com
- [ ] Link Bugcrowd account for payments
- [ ] Verify email

## Related

- AI research repo: github.com/arvmaz/AI (OSS-Fuzz findings in non-llm-ai-approaches.md)
- Auditor skill repo: github.com/arvmaz/auditor-skill-validation
