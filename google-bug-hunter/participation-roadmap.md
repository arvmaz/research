# Google Bug Bounty: Participation Roadmap

## Programs in Scope

| Program | Priority | Feasibility | Key Action |
|---------|----------|-------------|------------|
| Patch Rewards (Tsunami/OSV-SCALIBR) | **High** | High | Write security scanner plugins |
| AI VRP (Gemini/Vertex AI) | **Medium** | Medium | Research AI-specific vulns |
| OSS-Fuzz | **Medium** | Medium | Write fuzz harnesses, submit PRs |
| Chrome/Android VRP | Lower | High | Standard web/browser vulns |

---

## 1. Patch Rewards (Tsunami/OSV-SCALIBR) — START HERE

**Why:** Hermes writes code = direct fit. Memory-safe contributions (Rust) get reward multipliers. New OSV-SCALIBR track (Aug 2025) = less competition.

**How to participate:**
1. Write a Tsunami scanner plugin (Python/Go) or OSV-SCALIBR plugin (Rust/Go/Python) that detects vulnerabilities/secrets in popular OSS
2. Submit via the Patch Rewards program on bughunters.google.com
3. Reward up to $10,000 based on severity + quality

**Plugin ideas:**
- Detect publicly-disclosed CVEs in popular npm/pypi/crates.io packages
- Scan for credential/secrets leaks in high-profile OSS repos
- Memory-safe rewrite of an existing vulnerable Tsunami plugin (Rust multiplier)

**Resources:**
- https://bughunters.google.com/blog/new-patch-rewards-program-for-osv-scalibr
- https://github.com/google/tsunami-security-scanner
- https://github.com/google/osv-scanner/tree/master/osv-scalibr

---

## 2. AI VRP — ONGOING RESEARCH

**Scope:** Gemini, Vertex AI, AI products on Google infrastructure.
**Launched:** 2024/2025.

**Vulnerability classes to explore:**
- Prompt injection / jailbreaks
- Task hijacking / instruction override
- Data exfiltration via AI responses
- API-level bugs in Vertex AI endpoints

**Priority:** Medium. Less mature = less competition but also less public info on scope.

---

## 3. OSS-Fuzz — BUILD CVEs

**How to participate:**
1. Find an OSS project (in scope for Google VRP) needing fuzzing coverage
2. Write a libFuzzer-compatible harness
3. Submit PR to `github.com/google/oss-fuzz` with `projects/<name>/project.yaml` + harness
4. Google builds and runs fuzzers on their infra
5. Bugs → private disclosure → CVE credit

**Limitation:** No direct payment for bugs found via OSS-Fuzz. But high-severity finds can be submitted to other VRPs.

**Supported languages:** C/C++, Rust, Go, Python, Java/JVM, JavaScript, Lua

---

## 4. Chrome/Android VRP — LONG-TERM

Standard VRP. Reward tiers publicly documented. High competition. Requires browser/mobile security expertise.

---

## Account Setup (Prerequisite)

1. Create account at bughunters.google.com
2. Link Bugcrowd account for payment processing
3. Human authentication required — cannot be done by Hermes

---

## Next Actions for Hermes

1. **Pick first Patch Rewards target** — identify a popular OSS package with known vulns that lacks a Tsunami/OSV-SCALIBR detector
2. **Write first plugin** — Tsunami (Python/Go) or OSV-SCALIBR (Rust)
3. **Submit to Patch Rewards** — bughunters.google.com/upload
4. **Track reward tier updates** — see t_4c2217a3