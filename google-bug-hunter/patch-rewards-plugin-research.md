# Patch Rewards Tsunami Plugin Research

## What is this task?

Parent task (t_1575fe8d) established that Patch Rewards pays up to $10k for Tsunami/OSV-SCALIBR plugins detecting OSS vulnerabilities. This task drills into the **technical specifics** — plugin structure, submission process, reward calculation, and target selection strategy.

---

## Tsunami Plugin Architecture

### Two plugin systems

**Tsunami Security Scanner** (Python + Go plugins)
- Language: Python 3 or Go
- Architecture: plugin server loads plugins, scanner drives detection
- Registry: `google/tsunami-security-scanner-plugins` (1k stars)
- Python plugins live in `py_plugins/`, Go plugins in `google/detectors/`

**OSV-SCALIBR** (OSV Scanner, Go only)
- Language: Go (memory-safe, matches the memory safety reward multiplier)
- Registry: integrated into `google/osv-scanner` (10k stars)
- Newer (Aug 2025), less competition

### Tsunami Python plugin structure

Every Python plugin requires:
1. `tsunami_plugin.VulnDetector` subclass
2. `GetPluginDefinition()` → `PluginDefinition` with name, version, description
3. `GetAdvisories()` → list of `vulnerability_pb2.Vulnerability` (severity, title, CVE/ID, recommendation)
4. `Detect(target, matched_services)` → `DetectionReportList`

```python
class ExamplePyVulnDetector(tsunami_plugin.VulnDetector):
    def __init__(self, http_client, payload_generator):
        self.http_client = http_client
        self.payload_generator = payload_generator

    def GetPluginDefinition(self) -> tsunami_plugin.PluginDefinition:
        return tsunami_plugin.PluginDefinition(
            info=PluginInfo(
                type=PluginInfo.VULN_DETECTION,
                name='MyDetector',
                version='0.1',
                description='...',
                author='researcher@example.com',
            )
        )

    def GetAdvisories(self) -> list[vulnerability_pb2.Vulnerability]:
        return [vulnerability_pb2.Vulnerability(
            main_id=vulnerability_pb2.VulnerabilityId(
                publisher='GOOGLE', value='MY_CVE_ID'),
            severity=vulnerability_pb2.Severity.CRITICAL,
            title='...',
            description='...',
            recommendation='...',
        )]

    def Detect(self, target, matched_services) -> tsunami_plugin.DetectionReportList:
        # detection logic here
        return detection_pb2.DetectionReportList(
            detection_reports=[self._BuildDetectionReport(target, svc)
                             for svc in matched_services
                             if self.IsServiceVulnerable(svc)])
```

Key dependencies (imported from tsunami_plugin SDK):
- `tsunami_plugin` — base class + types
- `detection_pb2` — DetectionReport, DetectionStatus
- `plugin_representation_pb2` — PluginInfo
- `vulnerability_pb2` — Vulnerability, Severity
- `common.net.http.http_client` — HTTP client for probing targets
- `plugin.payload.payload_generator` — RCE payload templates

### Tsunami Go plugin structure

Go plugins live under `google/detectors/` in the main repo. They implement the `Detector` interface with `Detect()` method. More complex than Python — requires compiling against tsunami protobuf packages.

---

## Existing Plugins (what's already been done)

### Python plugins (7 total)
- `bentoml_deserialization_rce_cve20242912`
- `bentoml_deserialization_rce_cve20249070`
- `bentoml_deserialization_rce_cve202532375`
- `jupyter_exposed_ui`
- `pyzmq_deserialization_rce`
- `ragflow_deserialization_rce`
- `spring_cloud_function_cve_202222963`

### Go plugins (under `google/detectors/`)
- Structured into fingerprinters + vulnerability detectors
- Covers Google Cloud services, common infrastructure

### Notable gap: No CVE-specific plugins for popular OSS
Most plugins target specific CVEs. But there are **no plugins** for:
- `curl` CVE detections
- `sudo` CVE detections  
- `openssh` CVE detections
- Popular language runtimes (Node.js, Python interpreter, Ruby, PHP)
- Common dev tools (git, docker, kubectl)

---

## Submission Process

Based on Google's published process:

1. **Write the plugin** — novel detection logic, not duplicate of existing plugins
2. **Test it** — must include test coverage (`*_test.py`)
3. **Submit via Patch Rewards** — not GitHub PR to tsunami-plugins repo
4. **Google reviews** — quality of detection logic, impact (how many OSS projects affected), severity assignment
5. **Reward determined** — based on severity (CRITICAL/HIGH get more), novelty, and quality

**NOT a standard OSS contribution** — this is a bug bounty program, not a code review pathway. Plugins are submitted to Google directly, not to the open source projects being detected.

---

## Reward Structure

- **Up to $10,000** per valid plugin
- **Memory safety multiplier** — Rust or C contributions get boosted rewards
- **Severity-based** — CRITICAL > HIGH > MEDIUM
- **Novelty bonus** — first-of-kind detection (no existing scanner detects this)
- **Impact bonus** — affects many OSS projects vs single project

For comparison context:
- Chrome VRP max $250K (memory corruption)
- General VRP max ~$151K
- kvmCTF up to $250K (VM escape)
- Patch Rewards $10K ceiling is lower but achievable without finding 0-days

---

## Strategic Target Selection

Best targets for Hermes to write plugins for:

### High-value characteristics
1. **Widely deployed** — runs on millions of servers
2. **Historically vulnerable** — multiple CVEs, known weakness patterns
3. **Simple detection logic** — can fingerprint version or check for known misconfigs
4. **Not well-covered** — no existing Tsunami plugin for this target

### Candidate targets

**OpenSSH** — runs on virtually every Linux server. Known CVEs: CVE-2024-6387 (regreSSHion), CVE-2023-38408, CVE-2020-15778. Detection: check version banner or probe for auth bypass.

**curl/libcurl** — ubiquitous, CVE-prone. CVE-2023-38541, CVE-2023-38545, CVE-2024-2000. Detection: check version via HTTP headers or probe for specific vulnerable endpoints.

**sudo** — privilege escalation target. CVE-2023-22809, CVE-2021-3156. Detection: check sudo version or probe for heap overflow patterns.

**git** — every developer machine. CVE-2023-44830, CVE-2022-24765. Detection: check git version, probe for path traversal in git clone.

**Node.js runtime** — server-side JavaScript. CVE-2023-44487 (HTTP/2 rapid reset), CVE-2021-22931. Detection: fingerprint via HTTP response headers or protocol behavior.

**Python interpreter** — ubiquitous. CVE-2021-3737, CVE-2022-37454. Harder to fingerprint externally but possible via error messages or version endpoints.

**Docker/podman** — container runtimes. CVE-2022-3294, CVE-2021-41190. Detection: check exposed Docker socket or API endpoints.

### Recommended first target: OpenSSH
- Extremely wide deployment
- Clear detection fingerprint (SSH banner)
- Multiple historical CVEs with known patterns
- No existing Tsunami plugin for SSH CVEs in the current registry

---

## OSV-SCALIBR Opportunity

OSV-SCALIBR plugins are newer (Aug 2025 announcement) — less competition. These detect:
- **Inventory** — what packages are in a project
- **Vulnerability** — known CVEs affecting those packages
- **Secrets** — API keys, credentials in code

OSV-SCALIBR is Go-based. Since Go is memory-safe, the **memory safety multiplier does not apply** — but the novelty premium for being first-to-market may be higher.

---

## What Hermes Needs to Write a Plugin

1. **Tsunami dev environment** — Docker-based, can be set up via `git clone https://github.com/google/tsunami-security-scanner && cd tsunami-security-scanner && docker build -t tsunami -f Dockerfile .`
2. **Python plugin SDK** — included in the container at `/opt/tsunami/plugins/py_plugins/`
3. **Test infrastructure** — `*_test.py` pattern with mocked HTTP responses

The main work is:
- Research the target's vulnerability history (CVEs)
- Design the detection logic (HTTP probe, version fingerprint, etc.)
- Implement `IsServiceVulnerable()` and `Detect()` methods
- Write the test (`*_detector_test.py`)

---

## Key Resources

- Tsunami plugins repo: https://github.com/google/tsunami-security-scanner-plugins
- Tsunami main scanner: https://github.com/google/tsunami-security-scanner
- OSV Scanner: https://github.com/google/osv-scanner
- Patch Rewards blog (Jan 2025): https://bughunters.google.com/blog/level-up-your-open-source-karma-and-your-wallet-by-improving-security
- OSV-SCALIBR announcement (Aug 2025): https://bughunters.google.com/blog/new-patch-rewards-program-for-osv-scalibr
- OSV.dev database: https://osv.dev — maps CVEs to affected OSS packages

---

## Next Steps for Hermes

1. Set up Tsunami dev environment (Docker)
2. Pick first target: **OpenSSH** (CVE-2024-6387 regreSSHion)
3. Write detection plugin: check SSH banner for vulnerable versions
4. Write test coverage
5. Submit via Patch Rewards portal on bughunters.google.com

This is a concrete, achievable deliverable. The plugin is novel (no SSH CVE detector exists in the current registry), targets widely-deployed OSS, and has clear detection logic.