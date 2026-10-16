# Security Tool Integration

Tools supply evidence; they do not prove exploitability, safety, or coverage. Confirm authorization, target ownership, environment, data-handling rules, and rate limits first. Record tool/version, invocation configuration, scope, timestamp, raw-output location, parser assumptions, and result limitations. Never copy active secrets into reports or logs.

## Tool families

| Family | Named tools | Contribution | Boundary |
|---|---|---|---|
| Static Application Security Testing (SAST) | Checkmarx, SonarQube, Semgrep | Pattern/data-flow and code-quality leads | Cannot establish runtime reachability or business impact alone. |
| Software Composition Analysis (SCA) | Snyk, Dependabot, OWASP Dependency-Check | Dependency/package advisory intelligence | Name/version matches need identity, affected-range, reachability, and upgrade-context review. |
| Dynamic Application Security Testing (DAST) | OWASP ZAP | Dynamic alerts against an authorized running target | Requires scope, auth, safe configuration, and does not replace source/design review. |
| Mobile | MobSF | Static/dynamic mobile-artifact analysis | Package results require platform/context validation. |
| Secret detection | Gitleaks, TruffleHog | Candidate credentials and secret material | Treat results as sensitive; do not echo values and rotate exposed valid secrets. |
| Infrastructure/container/cloud | Trivy | Artifact/configuration vulnerability and misconfiguration signals | Coverage depends on supplied artifacts and enabled scanners. |

Other user-supplied scanner outputs are admissible evidence if their source, scope, schema, timestamp, and limitations are preserved.

## Per-tool integration

Official documentation: [Checkmarx](https://docs.checkmarx.com/), [SonarSource](https://docs.sonarsource.com/), [Semgrep](https://docs.semgrep.dev/), [Snyk](https://docs.snyk.io/), [Dependabot](https://docs.github.com/en/code-security/how-tos/secure-your-supply-chain), [OWASP Dependency-Check](https://jeremylong.github.io/DependencyCheck/), [MobSF](https://mobsf.github.io/docs/), [OWASP ZAP](https://www.zaproxy.org/docs/), [Gitleaks](https://github.com/gitleaks/gitleaks), [TruffleHog](https://trufflesecurity.com/docs), and [Trivy](https://trivy.dev/docs/latest/guide/). Use [Part 8](REFERENCES.md) for publisher, checked date, and uncertainty.

### Evidence and output record

Do not invent an export format. When documentation/configuration establishes it, retain the native report or documented API/export format and record the schema/version; otherwise retain the original report with a checksum and document the format as unknown. Parse only fields actually present: tool/rule or advisory identifier, component/path/location, package/version, result/severity/confidence, timestamp, target, configuration, and evidence reference. The following matrix states the minimum artifact each tool family should contribute.

| Tool | Appropriate input | Expected documented evidence | Inappropriate shortcut |
|---|---|---|---|
| Checkmarx | Authorized source/project | Scan/project/rule/location result from configured product export/API | Treating a dashboard count as a confirmed flaw |
| SonarQube | Analyzed project/branch | Analysis, rule key, component/location, quality/security status | Equating a quality gate with security assurance |
| Semgrep | Applicable source/rules | Rule ID, path/location, finding metadata from documented result | Applying irrelevant rules or unreviewed custom rules |
| Snyk | Manifest/lockfile/integration | Project, package/advisory/version/fix context from documented result | Assuming a dependency alert is reachable |
| Dependabot | Enabled repository ecosystem | Alert/update metadata and dependency context | Assuming it is enabled or executed |
| Dependency-Check | Supported artifact/manifest | Component/CPE/advisory candidate and suppression context | Treating CPE matching as identity proof |
| MobSF | Authorized mobile artifact/source | Artifact hash/version and static/dynamic report section | Treating a static flag as runtime proof |
| OWASP ZAP | Authorized running target | Alert, target, request/response evidence redacted, confidence | Active scanning an unapproved target |
| Gitleaks | Authorized source/history/artifact | Redacted rule/path/commit evidence | Reprinting or attempting unauthorized use of secrets |
| TruffleHog | Authorized source/history/integration | Redacted detector/location evidence | Validating credentials through abuse |
| Trivy | Authorized artifact/image/IaC/SBOM | Artifact identity, database time, package/config result | Inferring live-cloud state from a scan alone |

The official URL, publisher, and known access uncertainty for every row are in [REFERENCES.md](REFERENCES.md); consult the relevant current page before choosing command syntax or an export parser.

### Checkmarx — SAST

- **Use:** Source-oriented analysis and triage under the organization’s configured product/service. **Not for:** proving runtime exploitability or scanning an unauthorized target.
- **Inputs:** authorized source/build context and organization credentials/configuration. Follow the official documentation rather than assuming CLI flags, licensing, query packs, or output schema.
- **Triage:** identify the sink, path, sanitization/encoding context, reachable route, and whether a result duplicates another tool. Record scan identity and state `tool-reported-unvalidated` until validated.

### SonarQube — static analysis

- **Use:** configured static/code-quality/security rules and quality gates. **Limits:** rule coverage and branch/analysis configuration vary; an issue is not automatically exploitable.
- **Procedure:** consume an authorized project/branch report, rule key, component/location, severity, engine/version, and analysis timestamp. Review rule rationale and surrounding code before reporting.

### Semgrep — static analysis

- **Use:** rule-driven source inspection; official documentation also describes code, supply-chain, and secret scanning capabilities. **Procedure:** select only language/framework rules applicable to supplied code, preserve rule IDs and paths, then manually trace context. Custom rules require peer review and test cases.

### Snyk — SCA and related products

- **Use:** dependency, code, container, and cloud findings according to enabled product/scope. **Inputs:** manifest/lockfile or approved integration. **Triage:** preserve package/version/advisory/path and project context; assess direct/transitive, reachable/applicable, fixed versions, and upgrade impact.

### GitHub Dependabot — dependency update evidence

- **Use:** repository-hosted dependency update/security alert workflow where enabled. **Limits:** availability and advisories depend on repository settings/ecosystem. Record alert/update metadata and never claim Dependabot ran merely because configuration exists.

### OWASP Dependency-Check — SCA

- **Use:** identifies known-vulnerable component candidates from supported artifacts. **Inputs:** authorized project artifacts and maintained vulnerability-data access. **Triage:** validate CPE/package identification, version, false-positive suppression rationale, and whether the component is actually used.

### MobSF — mobile analysis

- **Use:** authorized APK/AAB/IPA/source analysis and, where configured, dynamic evidence. **Limits:** static flags need manifest, source, and runtime context; encrypted/protected builds may reduce visibility. Preserve artifact hash/version, analysis mode, and report section.

### OWASP ZAP — DAST

- **Use:** authorized scanning/proxy/automation of a controlled target. **Safety:** define target URLs, accounts, scope exclusions, safe policy, rate limits, data handling, and stop conditions before execution. Do not use active scanning against production or third parties without explicit approval.
- **Triage:** alert risk/confidence is not final severity. Capture request/response evidence only after redaction, reproduce safely, confirm reachability and impact, and label alerts unvalidated where needed.

### Gitleaks and TruffleHog — secret detection

- **Use:** scan authorized source/history/artifacts for possible credentials. **Handling:** restrict access to raw output, redact values, determine validity only under authorization, rotate/revoke confirmed exposed credentials, and avoid turning secret verification into credential abuse.
- **Limits:** entropy/signature matches can be false positives; absence does not prove secret-free history.

### Trivy — infrastructure/container/cloud

- **Use:** authorized filesystem, image, repository, SBOM, and configuration scanning according to enabled features. **Triage:** retain artifact digest/tag, scanner database time, package/config location, base-image provenance, deployment relevance, and remediation constraints. Do not infer live-cloud state from IaC alone.

## Required per-tool execution record

Use the following record for every named tool. It supplements the tool-specific guidance above and prevents a tool name from being mistaken for an execution claim.

| Tool | Safe integration and prerequisites | Output, triage, and Part 6 mapping | CI/CD and unavailable status |
|---|---|---|---|
| Checkmarx | Confirm authorized source/project, product configuration, credentials, scope, and stop conditions; follow the vendor documentation rather than inventing commands. | Preserve the documented project/export/API result, rule/location, and analysis metadata; validate the code path and map only supported observations to the Part 6 finding fields. | A gate is optional and policy-controlled. If unavailable or not run, record the reason and affected coverage. |
| SonarQube | Confirm the analyzed project, branch, quality/security profile, permissions, and analysis configuration. | Preserve rule key, component/location, engine/version, status, and timestamp; review code context before mapping to Part 6. | A quality gate is not security assurance. Record unavailable server, missing analysis, or unreviewed branches explicitly. |
| Semgrep | Select applicable language/framework rules and authorized source scope; peer-review custom rules before relying on them. | Preserve rule ID, path/location, message, and documented result metadata; manually trace context and map validated issues to Part 6. | CI use may enforce agreed rules and exception expiry. If rules were not run or source was incomplete, record that limitation. |
| Snyk | Confirm the supplied manifest/lockfile or approved integration and enabled product scope. | Preserve project, package, version, advisory, fix, and direct/transitive context; assess reachability and map validated risk to Part 6. | Policy gates are configurable by risk and workflow. Record missing integration, database, or execution evidence as not available/not run. |
| GitHub Dependabot | Confirm repository ecosystem, enabled alert/update settings, permissions, and the relevant alert or update evidence. | Preserve alert/update metadata and dependency context; do not treat configuration alone as a scan result or confirmed finding. | Record whether alerts or updates actually existed and were reviewed; otherwise mark not run or not available with scope impact. |
| OWASP Dependency-Check | Confirm supported artifact inputs, vulnerability-data availability, version, and suppression policy. | Preserve component, CPE/advisory candidate, version, evidence, and suppression rationale; validate identity and applicability before Part 6 mapping. | Run only in an authorized build or review workflow. If the database or project inputs were unavailable, record the resulting coverage gap. |
| MobSF | Confirm authorized APK/AAB/IPA/source artifact, artifact hash/version, analysis mode, and handling of sensitive output. | Preserve report section and artifact identity; correlate static flags with manifest/source/runtime context before Part 6 mapping. | CI use is optional and artifact-dependent. Record unsupported, encrypted, missing, or unanalysed artifacts as limitations. |
| OWASP ZAP | Confirm owned or explicitly authorized target, URLs, accounts, exclusions, safe policy, rate limits, stop conditions, and data handling. | Preserve redacted alert, target, request/response evidence, confidence, and timestamp; validate reachability and impact before Part 6 mapping. | Active testing must be an approved gate or test activity. A missing target, authorization, or run is not a pass. |
| Gitleaks | Confirm authorized source/history/artifact scope and secure handling of raw secret findings. | Preserve only redacted rule/path/commit evidence; rotate or revoke a secret only when authorized and map the exposure without reproducing the value. | CI scanning and blocking are configurable. If history or artifacts were not scanned, record the omitted scope and status. |
| TruffleHog | Confirm authorized source/history/integration scope and prohibit credential abuse during validation. | Preserve redacted detector/location evidence and validation status; do not print or test a credential outside authorization before Part 6 mapping. | CI use is optional and policy-controlled. Record unavailable integrations, skipped history, or unvalidated detections explicitly. |
| Trivy | Confirm authorized image, filesystem, repository, SBOM, or configuration input, artifact digest/tag, scanner features, and database time. | Preserve package/config location, advisory or misconfiguration identifier, artifact identity, and deployment relevance; do not infer live-cloud state before Part 6 mapping. | CI gates may be configured for agreed thresholds and exceptions. Record missing artifacts, database, or execution as not run/not available. |

## Common result-to-report procedure

1. Preserve a redacted evidence record and actual execution status.
2. Normalize component, location, rule/advisory, affected version, and duplicate identity.
3. Establish applicability, reachable/enforced context, false-positive likelihood, and safe validation.
4. Map to OWASP/CWE only where supportable.
5. Populate every [Part 6 finding field](SECURITY_REPORT_TEMPLATE.md), including `Evidence`, `Validation Status`, and `Limitations/Assumptions`.
6. Make CI/CD policy gates configurable by agreed risk thresholds, confidence, exception expiry, and remediation workflow; never assume a blocking gate exists.

Canonical documentation and verification status are maintained in [REFERENCES.md](REFERENCES.md).
