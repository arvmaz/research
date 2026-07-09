# Google OSS-Fuzz: Researcher Participation via Hermes

**Date:** 2026-05-21
**Source:** https://google.github.io/oss-fuzz/

---

## What is OSS-Fuzz?

OSS-Fuzz is Google's free fuzzing-as-a-service for open source projects. It runs continuous automated fuzzing (guided in-process fuzzing with libFuzzer, AFL++, Honggfuzz, Centipede) across 1,000+ projects and has found 10,000+ security vulnerabilities and 36,000+ stability bugs since launching in 2016.

**It is NOT a bug bounty program.** It's a continuous fuzzing service for open source project maintainers. Google ClusterFuzz drives the execution; issues are reported to the project's contacts privately, then disclosed publicly after 90 days.

---

## How Projects Join OSS-Fuzz

Projects must be accepted. Criteria: significant user base and/or critical IT infrastructure. Submission is a PR to the [oss-fuzz](https://github.com/google/oss-fuzz) repository containing:

- `projects/<name>/project.yaml` — metadata (homepage, main_repo, language, primary_contact email)
- `projects/<name>/Dockerfile` — container environment
- `projects/<name>/build.sh` — build script inside Docker

Contact email must belong to an established project committer and be associated with a Google account. This is the project's human-facing interface.

---

## The Researcher Participation Problem

There is **no formal researcher participation pathway** in OSS-Fuzz itself. The service is designed for project maintainers who own the code being fuzzed.

Three relevant paths exist across the Google ecosystem:

### 1. Submit a New Project (Maintainer Path)

If we maintain an open source project, we can submit it to OSS-Fuzz ourselves. Requires:

- Significant user base or critical infrastructure role
- A Google-account-associated email for the primary contact
- A proper Docker build environment with fuzz targets integrated
- One fuzz target example: boringssl, SQLite, go-fuzz, syzkaller

This is the path for projects we actually own and maintain. Not applicable if we're just researching OSS-Fuzz target projects.

### 2. Find Vulnerabilities via Standard Bug Hunters (No OSS-Fuzz Involvement)

The standard Google Bug Hunters VRP covers Chrome, Android, GCP, and Google's own OSS. OSS-Fuzz is orthogonal to this. A vulnerability found by OSS-Fuzz gets reported to the project's contacts on the OSS-Fuzz tracker — not to the researcher's Bug Hunters profile.

If we want bug bounty income, the Bug Hunters VRP is the path, not OSS-Fuzz.

### 3. Patch Rewards for Third-Party OSS Security Improvements

From the prior report (t_4e3d905d), the Patch Rewards program rewards researchers who contribute security improvements (Tsunami scanner plugins, memory safety fixes) to third-party open source projects. This is the closest analogue to "researcher participation via OSS-Fuzz" — but it operates entirely outside of OSS-Fuzz's infrastructure.

The Patch Rewards program is about contributing fixes, not finding bugs through fuzzing.

---

## For Hermes: What We Actually Have

We do not own or maintain an open source project that would qualify for OSS-Fuzz submission. We are researchers interested in security income via Google's programs.

**The practical path for us:**
- Bug Hunters VRP (Chrome, Android, Google Cloud, AI VRP) for directly found vulnerabilities
- Patch Rewards for contributing security improvements to third-party OSS
- The AI VRP (2024/2025 launch) may be less saturated and worth investigating

OSS-Fuzz participation is not a direct revenue pathway unless we become maintainers of a qualifying project.

---

## Recommendations

1. **Do not invest in OSS-Fuzz integration** for income purposes — it does not pay researchers directly
2. **Focus on Bug Hunters VRP** — the established path with known reward tiers and payment via Bugcrowd
3. **Investigate AI VRP** — new program, potentially less competitive, launched 2024/2025
4. **Patch Rewards is a complement** if we contribute to OSS security — not a primary fuzzing income path

---

## References

- OSS-Fuzz docs: https://google.github.io/oss-fuzz/
- Accepting new projects: https://google.github.io/oss-fuzz/getting-started/accepting-new-projects/
- Bug disclosure: 90-day deadline, 14-day grace period
- Bug Hunters platform: https://bughunters.google.com/
- AI VRP: launched late 2024, covers Gemini, Vertex AI
- Patch Rewards: up to $10,000 per valid security improvement contribution