# Security Report Template

Use this template for a specific assessment. Populate only with supplied or independently collected authorized evidence; retain unavailable fields and state the limitation rather than guessing.

## Report control

- Assessment name, date, assessor, report version, evidence cut-off, and distribution classification.
- Scope: in-scope assets, environments, repositories/commits, endpoints, mobile packages, cloud/configuration, exclusions, authorization, and testing window.
- Inputs reviewed: source, build artifacts, manifests/lockfiles, diagrams, configurations, logs, accounts, scanner reports, and their provenance.

## Executive summary

State the business/security objective, material validated risks, key scope limits, overall risk posture only to the extent evidence supports it, and immediate priorities. “No findings detected” means only that no findings were detected in stated coverage; it never means secure.

## Architecture and attack surface

Describe only evidenced components, identities, trust boundaries, data classifications/flows, entry points, integrations, privileged operations, and deployment surfaces. Link unknowns to coverage limitations.

## Standards and methodology

List the exact versions/dates of MASVS, MASTG, OWASP Mobile/API/Web Top 10, ASVS, CWE, NIST SSDF, and other standards actually used. Record phases completed: Architecture discovery; Threat modeling; Mobile analysis; Backend/API analysis; Source code review; Dependency analysis; Configuration review; Security testing; Final risk assessment.

## Tools and evidence

| Evidence source | Executed? | Scope/configuration | Timestamp/provenance | Limitation |
|---|---|---|---|---|
| SAST/SCA/DAST/mobile/secrets/container-cloud/human review | Yes / No / Not available | [state] | [state] | [state] |

Never mark an unavailable tool as passed. Correlate duplicate alerts and preserve only non-sensitive evidence references.

Record each named tool separately when it is in scope:

| Tool | Executed? | Version/configuration/scope | Evidence reference and timestamp | Result status and limitation |
|---|---|---|---|---|
| Checkmarx | Yes / No / Not available | [state] | [state] | [state] |
| SonarQube | Yes / No / Not available | [state] | [state] | [state] |
| Semgrep | Yes / No / Not available | [state] | [state] | [state] |
| Snyk | Yes / No / Not available | [state] | [state] | [state] |
| GitHub Dependabot | Yes / No / Not available | [state] | [state] | [state] |
| OWASP Dependency-Check | Yes / No / Not available | [state] | [state] | [state] |
| MobSF | Yes / No / Not available | [state] | [state] | [state] |
| OWASP ZAP | Yes / No / Not available | [state] | [state] | [state] |
| Gitleaks | Yes / No / Not available | [state] | [state] | [state] |
| TruffleHog | Yes / No / Not available | [state] | [state] | [state] |
| Trivy | Yes / No / Not available | [state] | [state] | [state] |

## Coverage matrix

| Area | Status: reviewed / partially reviewed / not reviewed / not applicable | Evidence and reason |
|---|---|---|
| Architecture, mobile, backend/API, source, dependencies, configuration, testing | [state] | [state] |

## Risk method

Use `Critical / High / Medium / Low`. Weigh plausible impact, exposure, affected assets/data, exploitability, attacker privileges/preconditions, reachability, compensating controls, and confidence. CVSS, if supplied or calculated under the current official specification, informs but does not automatically replace the required category. Explain uncertainty and do not rank a scanner alert as definitive without validation.

## Findings prioritized by risk

### [Vulnerability Title]

- Severity: Critical / High / Medium / Low
- Category: [security category]
- OWASP/CWE Mapping: [applicable mapping, or “Not established”]
- Affected Component: [file and line/range when verifiable; endpoint/method; module; package/dependency and version; mobile component; infrastructure/configuration item]
- Vulnerability Description: [what is wrong]
- Root Cause: [why the weakness exists]
- Security Impact: [why it matters / what could be exposed or affected]
- Attack Scenario: [plausible exploitation path and preconditions]
- Exploitability: [contextual assessment, when supportable]
- Evidence: [relevant code, configuration, test/tool result, trace, or other concrete proof; protect secrets]
- Validation Status: [confirmed / likely / potential / tool-reported-unvalidated / not reproducible / not applicable]
- Recommended Fix: [specific secure implementation]
- Prevention: [process/design/testing guidance that prevents recurrence]
- References: [official standard, OWASP/CWE entry, vendor documentation, or other reliable reference]
- Limitations/Assumptions: [what could not be verified, when relevant]

## Supported strengths and residual risk

List positive controls only with evidence. State residual risks, assumptions, blockers, untested areas, and implications of missing inputs.

## Remediation plan and continuous security

Separate urgent containment/fixes from sequenced architectural improvements. Assign owners and verification evidence where supplied. Recommend security regression tests, dependency/vulnerability monitoring, incident-response preparation, code-review gates, and repeat assessment triggers.
