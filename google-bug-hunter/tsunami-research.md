# Tsunami Security Scanner — What It Is and How It Works

## What is Tsunami?

A **general purpose network security scanner** developed by Google. It has an extensible plugin system for detecting high severity vulnerabilities with high confidence.

**Not a direct bug bounty program.** Tsunami is the *tool* — Patch Rewards is the *bounty program* that pays for Tsunami plugins.

---

## How Tsunami Works

1. Tsunami scans a network endpoint for known vulnerability patterns
2. It uses **plugins** (called "detectors") to check for specific CVEs or misconfigurations
3. Plugins run against target hosts and report findings with high confidence

**Scanner engine** ≠ **plugins**. The scanner itself is maintained by Google. Plugins are contributed by researchers and reviewed/accepted via PR to `google/tsunami-security-scanner-plugins`.

---

## Plugin Types (from official corpus)

| Type | Examples |
|------|----------|
| **RCE detectors** | Ray CVE-2023-48022, Apache Spark RCE, Triton Inference Server RCE |
| **Exposed UI detectors** | PyTorch Serve exposed notebook, Argo Workflow exposed API, Gradio CVE |
| **Weak credentials** | MLflow weak creds, ZenML weak creds, generic weak cred detector |
| **Credentials/Secrets** | MinIO sensitive info disclosure |
| **Auth bypass** | Apache Airflow CVE-2020-17526 auth bypass RCE |

---

## Reward Structure (Patch Rewards Program)

From the Tsunami docs:

| Detector Type | Reward (up to) |
|---------------|----------------|
| **Wishlist detector** | $3,177 |
| Exposed interface detector | ~$1,500–$2,000 |
| Weak credentials detector | $2,000 |
| Other detectors | $1,500 |

**Wishlist = vulnerability Google cares deeply about** (based on internal priorities, explicit on each PR).

**Since March 2024:** AI-related plugins get special `ai-bounty-prp` label for faster review.

---

## How to Write a Tsunami Plugin

### Structure
```
google/detectors/rce/ai/cve202348022/
├── README.md
├── build.gradle
├── settings.gradle
└── src/
    ├── main/java/.../RayCVE202348022Detector.java
    └── test/java/.../RayCVE202348022DetectorTest.java
```

### Requirements
1. **Java** — plugins are Java/Gradle based
2. **Docker images** — must provide vulnerable + fixed version containers for testing
3. **Unit tests** — must pass CI
4. **High confidence** — minimal false positives, RCE-like severity preferred
5. **Fast execution** — non-intrusive, executes quickly

### Review Process
- PR submitted to `google/tsunami-security-scanner-plugins`
- Google reviews for: correct vulnerable/fixed containers, unit tests passing, detection quality, exploit chain completeness
- Reward determined by detector type + quality + impact

---

## Can Hermes Write Tsunami Plugins?

**Yes — directly.** This is a strong fit:

| Hermes capability | Tsunami requirement |
|------------------|---------------------|
| Writing code (Java) | Detector must be Java |
| Research (CVE gaps) | Find unpatched CVEs with no detector |
| PR submission | Submit to google/tsunami-security-scanner-plugins |
| Docker setup | Docker available on this system |

**Key constraint:** Plugin must be Java (not Python). Hermes can write Java.

**Another constraint:** Must provide Docker images for vulnerable + patched versions. Hermes can create these with `docker build`.

---

## Priority for Hermes

**High.** Best direct participation path in Google's ecosystem.

**Why:**
- Writing code = core capability
- Clear deliverable: a working Java detector
- Reward up to $3,177 for wishlist detectors, $1,500–$2,000 for others
- AI-related plugins have `ai-bounty-prp` label (faster review, aligned with current research)

**Next steps (child tasks):**
1. Find a CVE with no existing Tsunami detector (high severity, RCE-like)
2. Set up Gradle project structure
3. Write the detector in Java
4. Build Docker test environment
5. Submit PR

---

## Key Resources

- Main repo: https://github.com/google/tsunami-security-scanner
- Plugins repo: https://github.com/google/tsunami-security-scanner-plugins
- Docs: https://google.github.io/tsunami-security-scanner/
- Contributing: https://github.com/google/tsunami-security-scanner-plugins/blob/master/docs/contributing.md
- Public review process: https://github.com/google/tsunami-security-scanner-plugins/blob/master/docs/publicreviewprocess.md