# Handoff

## Goal

Build the nine-file `AI-AppSec-Engineer` repository from `MASTER_PROMPT_AI_AppSec_8_PARTS.md`.

## Current state

All nine files are **complete (substantive, audited)**:

- `README.md`
- `AI_SECURITY_ENGINEER_SYSTEM_PROMPT.md`
- `SECURITY_KNOWLEDGE_BASE.md`
- `REVIEW_METHODOLOGY.md`
- `SECURITY_TOOL_INTEGRATION.md`
- `VULNERABILITY_DETECTION_RULES.md`
- `SECURITY_REPORT_TEMPLATE.md`
- `SECURE_DEVELOPMENT_GUIDANCE.md`
- `REFERENCES.md`

The directory contains no other files. Local Markdown links resolve, all files are non-empty, and the Section 14 traceability audit passed. No real application was assessed.

## Decisions made

- The master prompt is the sole binding specification.
- Use the six named system layers, nine named methodology phases, required tool inventory, Critical/High/Medium/Low severity scale, and six validation statuses exactly as written in the repository.
- Use evidence-first language: scanner alerts are not confirmed findings; missing evidence is a coverage limitation; “no findings detected” is not “secure.”
- Testing guidance is authorized, bounded, non-destructive, and distinguishes filesystem/repository agents from chat-only agents.
- `AI-AppSec-Engineer/` must contain only the nine required Markdown files.

## Verified references

Checked 2026-10-16:

- OWASP Top 10: https://owasp.org/projects/top-ten — official page states current released edition 2025.
- OWASP API Security Top 10: https://api-security.owasp.org/ — official portal; 2023 edition was visible.
- OWASP Mobile Top 10: https://owasp.org/projects/mobile-top-10 — official project page; 2024 release was visible.
- MASVS: https://mas.owasp.org/MASVS/ and MASTG: https://mas.owasp.org/MASTG/.
- OWASP ASVS: https://owasp.org/www-project-application-security-verification-standard/; Cheat Sheets: https://cheatsheetseries.owasp.org/.
- MITRE CWE/CWE Top 25: https://cwe.mitre.org/ and https://cwe.mitre.org/top25/.
- NIST SP 800-218 landing page: https://csrc.nist.gov/pubs/sp/800/218/final.
- Android security best practices, Keystore, Network Security Configuration, and Play Integrity official pages under https://developer.android.com/.
- Apple Platform Security, Developer Security, Keychain Services, and NSAppTransportSecurity official pages under https://support.apple.com/ and https://developer.apple.com/.
- RFC 6749, RFC 9700, and RFC 7519 at https://www.rfc-editor.org/; OpenID specs at https://openid.net/developers/specs/.
- Official tool documentation URLs are recorded and availability-checked in `REFERENCES.md` for Checkmarx, SonarQube, Semgrep, Snyk, Dependabot, OWASP Dependency-Check, MobSF, OWASP ZAP, Gitleaks, TruffleHog, and Trivy.

## Unverified or version-sensitive

Exact current editions/releases for MASVS, MASTG, ASVS, CWE Top 25, NIST SP 800-218 publication metadata, OpenID specifications, and tool products were not asserted beyond what the official page visibly stated. SonarSource’s original path redirected to a moved/not-found page; use its current documentation index and verify the exact page before adding claims. Tool installation, licensing, feature availability, execution, and scan results remain unverified.

## Next steps

1. In a fresh session, read this file and the master prompt.
2. Inspect the nine existing files; preserve correct content.
3. Re-check any edition/version claim that needs stronger evidence, especially the entries listed above.
4. If required, expand or repair gaps against Section 14, then rerun file-count, non-empty, internal-link, and traceability checks.
5. Do not assess a real application unless new scope and evidence are supplied.

## Blockers and uncertainties

No blocker prevents continuation. The repository is a reusable framework, not an application assessment; target architecture, platform, source, runtime access, credentials, manifests, configurations, and authorized tool outputs are absent. Current-version claims must be reverified when the reference library is updated.

## Do not

- Do not regenerate completed files.
- Do not overwrite correct content unnecessarily.
- Do not create extra files inside `AI-AppSec-Engineer/`.
- Do not assume unverified versions, tool availability, scan execution, findings, or security assurance.
