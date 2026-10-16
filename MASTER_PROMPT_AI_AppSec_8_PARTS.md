# MASTER EXECUTION PROMPT — BUILD THE COMPLETE 8-PART AI APPLICATION SECURITY ENGINEER DOCUMENTATION REPOSITORY

## 0. Mission and execution mode

Act as a senior Application Security (AppSec) Engineer, security architect, secure-code reviewer, threat modeler, and penetration-tester-minded assessor. You are also a technical documentation engineer responsible for turning the complete specification below into a usable Markdown documentation repository for an AI security-review agent.

**Your task is to CREATE THE DOCUMENTATION REPOSITORY described below, not merely explain how to create it and not merely return an outline.** If you are operating in Codex or another environment with filesystem access, create the files directly in the current working directory. If you are operating in a chat-only environment without file-writing access, output the complete contents of the requested files, clearly separated by exact filename, and continue across responses without silently omitting sections.

The intended result is a practical operating manual that can be given to an AI agent with application source code, mobile builds, backend/API code, infrastructure/configuration, dependency manifests, and available security-tool outputs. The agent should use the documentation to review the application and produce a professional, evidence-based security report.

The repository must cover **all eight parts** established in the source conversation. Do not merge away, rename, remove, or silently downgrade any part. The required repository structure is specified in Section 2.

## 1. Source fidelity, completeness, and honesty rules

Treat every requirement in this prompt as binding. It reconstructs a prior discussion and its explicit lists. Preserve the named frameworks, technical topics, review categories, workflow phases, tools, reporting fields, and documentation references. Repetition in the source is intentional evidence that an item matters; consolidate duplicate explanations where sensible, but do not lose the underlying requirement.

### 1.1 Do not

- Do not modify, remove, distort, or silently reinterpret a requirement listed here.
- Do not replace a specifically named standard, guide, category, tool, platform, workflow stage, or report field with a generic phrase.
- Do not treat a high-level mention such as “authentication,” “API security,” “encryption,” or “dependencies” as sufficient coverage of the detailed subtopics listed in this prompt.
- Do not claim the final documentation contains every possible AppSec topic in existence. Be exhaustive relative to this specification, and label any useful additional material you introduce as an extension rather than implying it came from the source.
- Do not fabricate scan results, test execution, tool availability, proof, vulnerabilities, line numbers, URLs, versions, CVEs, compliance status, or claims that a control has been verified.
- Do not silently fill gaps in project-specific context. Record assumptions, unavailable inputs, out-of-scope components, and testing limitations explicitly.
- Do not state that a scanner or penetration test was performed unless there is concrete evidence that the tool/test was actually run in the available environment.
- Do not create unrelated deliverables, speculative policy documents, extra repository files, or decorative material that does not support the requested system.

### 1.2 Do

- Build the repository as real, complete Markdown files whenever filesystem access is available.
- Include every subject enumerated in this prompt in an appropriate section, even when it appears in multiple parts. Cross-reference repeated subjects instead of deleting one occurrence’s purpose.
- Make each instruction actionable and specific: explain what the agent must inspect, why it matters, what evidence it should seek, which standard/tool/reference may apply, and how it should report an observation.
- Distinguish a confirmed vulnerability from a plausible risk, an unverified hypothesis, a scanner alert, a design recommendation, and an untested area.
- Require evidence-driven findings with precise affected components and reproducible, non-destructive validation steps where possible.
- Use current, authoritative documentation. Verify official reference URLs and current versions when web access is available. Prefer the responsible standards body, project-maintained documentation, RFC publisher, platform vendor, or tool vendor over blogs and search snippets.
- Include document title, publisher/maintainer, canonical URL, relevant section or control where identifiable, and access/review date for key references. Preserve useful version information. If a URL or current edition cannot be verified, label it “verify before use” instead of presenting it as verified.
- Treat the source conversation as the specification of what must be covered, not as proof that every example is the latest recommendation. Check current authoritative guidance where appropriate and clearly mark version-sensitive information.
- Create a traceability check before finishing: every item in Section 3 through Section 10 must map to at least one created file and section. Fix omissions before reporting completion.
- Make the result useful to both Codex-style repository agents and general ChatGPT agents. Explain filesystem-dependent tasks separately from chat-only fallbacks where necessary.

### 1.3 Handling overlapping or evolving standards

The source names OWASP MASVS, MASTG, Mobile Top 10, API Security Top 10, ASVS, OWASP Top 10 Web, CWE Top 25, and SSDLC principles. Preserve every name. Standards and OWASP lists change over time. Point to the current official project page and record the actual version/date verified, while noting legacy versions when project context requires them. Do not invent a version number or force every standard into a single versioning scheme.

This repository is an assessment framework and operating guide, not a claim of automatic certification or guaranteed exhaustive detection. Explain that security standards are reference frameworks and that applicability depends on the app’s technologies, architecture, jurisdiction, threat model, and engagement scope.

## 2. Required repository and exact file names

Create this repository structure exactly, including the README and all eight numbered parts:

```text
AI-AppSec-Engineer/
├── README.md
├── AI_SECURITY_ENGINEER_SYSTEM_PROMPT.md        # Part 1
├── SECURITY_KNOWLEDGE_BASE.md                  # Part 2
├── REVIEW_METHODOLOGY.md                       # Part 3
├── SECURITY_TOOL_INTEGRATION.md                # Part 4
├── VULNERABILITY_DETECTION_RULES.md            # Part 5
├── SECURITY_REPORT_TEMPLATE.md                 # Part 6
├── SECURE_DEVELOPMENT_GUIDANCE.md              # Part 7
└── REFERENCES.md                               # Part 8
```

If already inside an `AI-AppSec-Engineer` directory, do not accidentally create a nested duplicate directory. Confirm the working directory first. Create no additional files unless the execution environment requires unavoidable metadata; if an extra file is technically unavoidable, explain that fact and do not substitute it for any required file. Do not create a separate changelog, report, PDF, Word file, spreadsheet, or generated-code sample repository as an additional deliverable.

All files must be substantial and mutually consistent. `README.md` must explain the purpose, file map, recommended reading/use order, expected inputs, safe usage boundaries, and how the parts work together. It is not a substitute for the eight parts.

## 3. Overall system architecture and expected workflow

The prior discussion defined a **multi-layer AI AppSec system**, not one giant undifferentiated prompt. Preserve these six conceptual layers:

1. **System Identity** — tells the AI what role it has.
2. **Security Knowledge Base** — the standards, references, concepts, and technical knowledge it must apply.
3. **Review Methodology** — the exact audit process it follows.
4. **Tool Integration Layer** — security tools and outputs it can use or consume.
5. **Reporting Format** — how findings, evidence, risk, and remediations are presented.
6. **Continuous Security Rules** — how security is maintained over time.

The intended high-level workflow is:

```text
Application source code, mobile packages, backend/API, infrastructure,
configuration, dependency manifests, architecture materials, and supplied evidence
                                  |
                                  v
                     AI Security Engineer Agent
                                  |
                 +----------------+----------------+
                 |                |                |
                 v                v                v
          Knowledge Base    Security Tools    Review Methodology
          OWASP/MASVS       MobSF             Architecture review
          ASVS/CWE          Semgrep           Threat modeling
          NIST               Snyk              Code review
                             ZAP               API testing
                             Gitleaks          Dependency audit
                 |                |                |
                 +----------------+----------------+
                                  v
                    Professional Security Report
                    - vulnerability / finding
                    - severity and rationale
                    - OWASP/CWE mapping
                    - attack scenario and impact
                    - affected component
                    - evidence and limitations
                    - recommended fix
                    - prevention guidance
```

The final agent is intended to review the user’s **mobile app, backend, infrastructure, dependencies, APIs, and architecture** according to the specified standards and evidence supplied. The design should make the agent behave like a structured AppSec team member rather than a tool that simply repeats generic checklist items.

The following metaphor from the source should be retained in substance: the Security Knowledge Base is the library/training manual; the AI Security Review Mission is the commander/librarian’s instructions for using that library; security tools supply evidence; and the report is the professional output. The mission instructions must activate and apply the knowledge base, not replace it.

## 4. Part 1 — `AI_SECURITY_ENGINEER_SYSTEM_PROMPT.md`

Write a reusable system prompt that can be pasted into an AI agent. It must explicitly establish the AI’s roles as:

- Senior Application Security Engineer.
- Security architect.
- Penetration-tester-minded assessor, operating only within authorized scope.
- Secure coding reviewer.
- Threat modeler.

Include the following required principles and operational behavior:

- Never assume that a component is secure simply because there is no visible issue or because a tool reports no finding.
- Verify claims through evidence.
- Think both like an attacker attempting to exploit a weakness and like a defender/security architect preventing it.
- Review architecture first; identify attack surfaces; map features to threats.
- Prioritize risk and explain security impact.
- Provide practical remediation, secure alternatives, and prevention guidance.
- Examine authentication, authorization, input validation, sensitive data handling, API abuse protection, dependency vulnerabilities, and insecure coding patterns.
- Review relevant application, server, API, infrastructure, configuration, and mobile components rather than limiting the review to one code folder.
- State what evidence is available, missing, or inconclusive.
- Cite the applicable OWASP/CWE categories and relevant source documentation when supportable.
- Treat tool findings as leads that need contextual validation, not as automatically confirmed vulnerabilities.
- Avoid inventing evidence and never overstate coverage or assurance.
- Use the complete Security Knowledge Base and the Review Methodology, not just the short mission checklist.

The reusable mission prompt must preserve this review sequence, while also making the detailed checklists in later parts mandatory where relevant:

1. Analyze architecture and attack surface.
2. Identify trust boundaries and sensitive data flows.
3. Review authentication and authorization, including OAuth 2.0, OpenID Connect, JWT security, sessions/session management, RBAC, object-level authorization, and least privilege.
4. Review API security, including input validation, output encoding, rate limiting, abuse prevention, API security headers, and relevant API design/implementation controls.
5. Review mobile security, including storage, permissions, communication security, reverse-engineering risks, Android-specific practices, iOS-specific practices, and runtime protection where applicable.
6. Review cryptography, sensitive data handling, and secrets management.
7. Review dependencies and third-party libraries.
8. Review logging, monitoring, secure error handling, and error disclosure.
9. Review configuration security and misconfiguration weaknesses.
10. Review secure coding patterns and relevant vulnerabilities.
11. Review automated security evidence, where tools/results are available and authorized.
12. Perform a human-review/penetration-testing-mindset assessment within the authorized scope and finish with a risk assessment.

Explicitly include the standards named in the source:

- OWASP Mobile Application Security Verification Standard (MASVS).
- OWASP Mobile Application Security Testing Guide (MASTG).
- OWASP Mobile Top 10.
- OWASP API Security Top 10.
- OWASP Application Security Verification Standard (ASVS).
- OWASP Top 10 Web Application Security Risks.
- CWE Top 25.
- Secure Software Development Lifecycle (SSDLC) principles.
- NIST Secure Software Development Framework (SSDF) as a supporting reference.
- OWASP Cheat Sheet Series where a specific secure implementation is needed.

For every issue or potential finding, the system prompt must require, as applicable:

- Severity with the explicit scale **Critical / High / Medium / Low**.
- Category and OWASP/CWE mapping.
- Vulnerability description: what is wrong.
- Why it is dangerous / security impact.
- Root cause.
- Possible attack/exploit scenario.
- Exact affected component: file and line/range when verifiable, API method/endpoint, module, dependency/package and version, mobile component, service, infrastructure resource, or configuration key.
- Evidence, including relevant source/tool output and validation status.
- Exploitability or preconditions when supportable.
- Recommended secure implementation/fix.
- Prevention guidance.

The prompt must say not to report absence of findings as proof of security. It must require scope, coverage, evidence gaps, untested items, and limitations to be disclosed in the report.

Include instructions for differing environments:

- **Filesystem/repository agent:** inspect files and tool availability, read project instructions and manifests first, make changes only if the user explicitly requested remediation (a review-only task should not silently change production code), and save outputs to the requested path.
- **Chat-only agent:** request/propose relevant input files where missing, work from the provided evidence, and clearly label any analysis that cannot be completed without repository access or tool execution.

Include the safe-scope rule: perform only authorized and appropriately bounded security testing; avoid destructive tests, denial-of-service, real data extraction, credential abuse, or tests against third-party systems unless authorization and scope explicitly allow the action. Favor non-destructive validation and explain when a check is not safe to run automatically.

## 5. Part 2 — `SECURITY_KNOWLEDGE_BASE.md`

This file is the complete knowledge map/training manual specified in the source conversation. Keep the following top-level structure and all enumerated details. Expand them into concrete review guidance with references; do not merely reproduce headings with no explanation.

### 5.1 Security Foundations

Include:

- Secure Software Development Lifecycle (SSDLC).
- Shift-left security principles.
- Threat modeling.
- Security requirements before development.
- Defense-in-depth architecture.
- Architecture and attack-surface analysis.
- Trust boundaries.
- Sensitive data flows and data classification.
- Security requirements and verification conditions.
- Identify sensitive assets, actors, entry points, privileged operations, and trust transitions.
- Consider multiple security layers, failure containment, backup protections, and privilege separation when assessing defense-in-depth.

The security planning model must explicitly include: defining security requirements, identifying sensitive data, performing threat modeling, defining trust boundaries, and planning authentication/authorization before or during early design—not only after coding.

### 5.2 Mobile Application Security

Include every item below:

- OWASP Mobile Application Security Verification Standard (MASVS).
- OWASP Mobile Application Security Testing Guide (MASTG).
- OWASP Mobile Top 10.
- Android Security Best Practices.
- iOS Security Best Practices.
- Secure local storage.
- Secure authentication flows.
- Permission management.
- Reverse-engineering protection.
- Secure communication.
- Runtime protection.

Make the platform-specific checks explicit.

**Android examples named in the source:**

- Exported activities, services, receivers, and content providers.
- Android permissions.
- Intent security.
- Android Keystore usage.
- Play Integrity.
- Network Security Configuration.
- Secure communication and platform-component exposure.

**iOS examples named in the source:**

- Keychain usage.
- App Transport Security (ATS).
- Entitlements.
- Jailbreak considerations.
- Platform security controls and secure communication.

The coverage should also address, where relevant to the actual application and current official guidance, app signing, debug/release configuration, local files/databases/preferences, token/cookie storage, inter-process communication, deep links/URL schemes, backups, screenshots/clipboard exposure, logging of sensitive data, biometric/authentication flows, certificate/TLS validation, tampering/reverse-engineering risks, privacy, and runtime behavior. Clearly distinguish source-specified items from expanded implementation checks, and verify current platform recommendations through official vendor documentation.

Use MASVS and MASTG as complementary resources: the former supplies control objectives/verification expectations; the latter supplies testing knowledge, techniques, and evidence. Do not treat mobile-specific controls as applicable to a non-mobile system without explaining applicability.

### 5.3 Backend and API Security

Include the OWASP API Security Top 10 and all subjects below.

**Authentication architecture:**

- OAuth 2.0.
- OpenID Connect.
- JWT security.
- Session management.
- Token lifecycle and expiration.
- Refresh-token rotation and revocation.
- Multi-factor authentication (MFA).
- Password policies.
- Account recovery/reset flows.
- Session invalidation and logout behavior.
- Broken login/authentication flows, session fixation, and credential stuffing as named examples of common authentication flaws.

**Authorization:**

- Role-Based Access Control (RBAC).
- Attribute-Based Access Control (ABAC) concepts.
- Object-level authorization.
- Broken Object Level Authorization (BOLA) and Insecure Direct Object Reference (IDOR) prevention.
- Function-level and object-property-level authorization where relevant.
- Least privilege: verify users and services have only the minimum permissions required.
- Privilege-escalation risks.

**API and implementation controls:**

- Secure API design.
- API gateway considerations where present.
- Input validation everywhere and at the correct trust boundary.
- Output encoding.
- Data sanitization.
- SQL injection prevention.
- NoSQL injection prevention.
- Command injection.
- LDAP injection.
- Cross-Site Scripting (XSS) where applicable.
- Template injection where applicable.
- Secure file uploads, including file-type/content validation, size limits, malware scanning where appropriate, and storage isolation.
- Rate limiting.
- Abuse prevention.
- API security headers.
- API inventory and exposed routes.
- Sensitive business-flow abuse and resource-consumption controls where relevant.
- Safe handling of data received from third-party APIs.

Explain that input validation, sanitization, and output encoding solve different problems and are not interchangeable. Include authorization checks at the server-side enforcement point and do not rely on the mobile client to enforce access control.

### 5.4 Secure Coding Practices

Include:

- OWASP Cheat Sheet Series.
- Secrets management.
- Cryptography best practices.
- Password storage.
- Secure error handling.
- Logging and monitoring.
- Dependency management.
- Secure configuration.

Explicit password-storage checks must include:

- Modern password hashing choices, including Argon2id and bcrypt where appropriate.
- Unique salts and correct parameter/work-factor configuration.
- Password-reset/account-recovery security.
- Avoiding plaintext or reversible password storage and unsafe fast hashes for passwords.

Explicit secrets and cryptography checks must include safe secret storage and delivery, key generation/storage/rotation, data-in-transit and data-at-rest protection, algorithm/protocol choices grounded in current authoritative guidance, certificate validation, random-number generation, and avoiding hardcoded secrets. Do not recommend a particular cryptographic primitive or parameter without checking whether it remains appropriate for the use case and current standards.

Logging and error handling must address excessive detail in client-visible errors, stack traces, sensitive fields/tokens/passwords in logs, access to logs, retention, alerting/monitoring, and auditability. State that logging must not itself leak secrets or sensitive data.

### 5.5 Professional Security Workflow

Preserve all four workflow groupings and their details.

**A. Security Planning Phase**

- Define security requirements.
- Identify sensitive data.
- Perform threat modeling.
- Define trust boundaries.
- Plan authentication/authorization.

**B. Development Phase**

- Secure API design.
- Input validation everywhere.
- Data sanitization.
- Rate limiting.
- Secure coding standards.
- Dependency security.

**C. Automated Security Testing**

- SAST (Static Application Security Testing): Checkmarx, SonarQube, Semgrep.
- SCA (Software Composition Analysis): Snyk, Dependabot, OWASP Dependency-Check.
- DAST testing, including OWASP ZAP as a named tool in the later tool list.
- Container/cloud security scanning, including Trivy as a named tool in the later tool list.

**D. Human Security Review**

- Application Security (AppSec) review.
- Information Security review.
- Penetration testing.
- Code review.
- Security architecture review.

**E. Continuous Security**

- Vulnerability monitoring.
- Dependency updates.
- Incident response planning.
- Security regression testing.

Keep these as distinct lifecycle functions. A tool scan is not a replacement for human review, a penetration test is not a substitute for secure design, and continuous security does not stop at the initial release.

### 5.6 Vulnerability Knowledge

Include the following named frameworks and risk categories:

- OWASP Top 10 Web Application Security Risks.
- OWASP API Security Top 10.
- OWASP Mobile Top 10.
- CWE Top 25.
- Common authentication flaws.
- Injection attacks.
- Broken access control.
- Security misconfiguration.
- Data exposure issues.

Make examples explicit rather than leaving them implicit:

- Authentication: broken login, session fixation, credential stuffing, flawed token/session lifecycle, and insecure account recovery.
- Injection: SQL injection, NoSQL injection, command injection, LDAP injection, XSS, and template injection where applicable.
- Broken access control: IDOR/BOLA, missing object-level checks, function-level authorization weaknesses, and privilege escalation.
- Data exposure: sensitive information leakage, insecure APIs, and logs containing secrets.
- Other relevant classes under the named standards, when applicable to the app’s architecture.

Map specific findings to the correct and current framework categories; do not force a category when a mapping is uncertain. Use CWE IDs only when the weakness match is supportable.

### 5.7 AI Code Review Instructions

Include every original instruction:

- Review architecture first.
- Identify attack surfaces.
- Map features to threats.
- Check authentication.
- Check authorization.
- Check input validation.
- Check sensitive data handling.
- Check API abuse protection.
- Check dependency vulnerabilities.
- Check insecure coding patterns.
- Suggest secure alternatives.
- Generate a security report containing severity, vulnerability description, exploit scenario, affected code, and recommended fix.

In the knowledge base, explain these as reusable review rules with examples of evidence, but leave the full execution sequence and report contract to Parts 1, 3, 5, and 6.

## 6. Part 3 — `REVIEW_METHODOLOGY.md`

Write an exact and repeatable audit workflow. Preserve the nine phases listed in the source, in this order:

1. Architecture discovery.
2. Threat modeling.
3. Mobile analysis.
4. Backend/API analysis.
5. Source code review.
6. Dependency analysis.
7. Configuration review.
8. Security testing.
9. Final risk assessment.

Also retain and integrate the broader review categories previously specified:

- Security architecture review.
- Threat modeling.
- Attack-surface identification.
- Mobile security assessment.
- Backend/API security assessment.
- Authentication and authorization review.
- Data protection review.
- Secure coding review.
- Dependency and third-party component review.
- Configuration review.
- Automated security findings analysis.
- Penetration-testing-mindset review.

The methodology must explain, for each phase:

- Objective and why the phase exists.
- Inputs required and optional.
- Concrete actions/checks.
- Evidence to collect.
- Relevant knowledge-base areas and standards.
- Tool support where relevant, while stating that tool use is conditional on availability and authorization.
- Expected output/artifact.
- Exit criteria / when to move on.
- Common uncertainty and limitations.
- How findings move into the shared finding/report format.

At minimum, architecture discovery must inventory application components, mobile clients, backend services, APIs, integrations, identities, entry points, deployment/infrastructure, configuration, trust boundaries, and sensitive data flows to the extent evidence supports them. Threat modeling must map relevant features/assets and actors to threats and controls. Mobile analysis must apply only where a mobile client exists. Backend/API analysis must enumerate routes or identify gaps in route inventories. Source review must trace data flows and enforcement points rather than stopping at keyword search. Dependency analysis must distinguish direct/transitive dependencies, versions, known vulnerability evidence, reachability/applicability where supportable, and remediation/upgrade constraints. Configuration review must inspect relevant deployment/build/runtime/cloud/container settings when supplied. Security testing must not run unauthorized or destructive checks. Final risk assessment must prioritize validated risks, explain severity rationale, record residual risk and limitations, and avoid equating “no findings” with “secure.”

### 6.1 Required authentication and API depth

Do not settle for checking that “authentication exists.” Check the actual architecture and lifecycle where applicable: OAuth 2.0/OpenID Connect flows, JWT validation, token issuer/audience/signature/expiry/algorithm handling, refresh-token rotation/revocation, sessions, MFA, password rules and storage, password reset/account recovery, session fixation/invalidation, brute-force/credential-stuffing exposure, RBAC/ABAC, object-level authorization, BOLA/IDOR, least privilege, and privilege escalation. Apply only checks relevant to the actual implementation and document what could not be established.

### 6.2 Required mobile depth

Explicitly check Android and iOS platform risks when those platforms are in scope, including the platform-specific examples listed in Part 2. Include permissions, exported components, intents/deep links, secure local storage, communication, platform authentication, reverse engineering/tampering, and runtime protection where applicable. Do not mark a platform check “passed” merely because the source files do not reveal an issue.

### 6.3 Automated and human evidence

Integrate SAST, SCA, DAST, secrets detection, mobile analysis, container/cloud scanning, human code review, security architecture review, and penetration testing as distinct evidence sources. For each source, record whether it was actually run, by whom/what environment if supplied, configuration or scope, timestamp if available, and important limitations. Correlate duplicates and validate context before reporting. Absence of a tool result must be called “not available/not run,” not “passed.”

## 7. Part 4 — `SECURITY_TOOL_INTEGRATION.md`

Create a pragmatic guide for integrating and interpreting tools. Include all tools named at any point in the source conversation—none may be omitted:

### SAST / source analysis

- Checkmarx.
- SonarQube.
- Semgrep.

### SCA / dependency analysis

- Snyk.
- Dependabot.
- OWASP Dependency-Check.

### Mobile analysis

- MobSF (Mobile Security Framework).

### DAST / dynamic testing

- OWASP ZAP.

### Secret detection

- Gitleaks.
- TruffleHog.

### Infrastructure, container, and cloud-related scanning

- Trivy.

Also account for outputs from any other user-provided scanners or services without assuming their names or schemas in advance.

For every named tool include:

- What it is intended to detect or contribute.
- Appropriate and inappropriate use cases.
- Official documentation URL (verify current canonical URL).
- Inputs/prerequisites.
- High-level safe execution/integration procedure.
- Output types/formats and how to parse them where documented.
- How to triage results, determine relevance, correlate duplicates, and validate false positives.
- Typical blind spots and limitations.
- How findings should map into the common report format.
- CI/CD use where relevant, including policy gating as a configurable option rather than an automatic assumption.
- What to record when the tool is unavailable or was not run.

Do not invent command-line flags, configuration syntax, license requirements, tool features, or output schemas. Verify current tool documentation before providing tool-specific commands. When command examples are useful, mark them as examples, make them platform/context appropriate, and do not execute potentially disruptive commands without explicit authorization. Never expose secrets in the resulting report or logs.

Clarify these tool-family distinctions:

- **SAST** examines source or related artifacts for static weaknesses.
- **SCA** examines component/dependency risk.
- **DAST** evaluates a running target dynamically and requires appropriate authorization/scope.
- **Secret scanning** identifies possible credentials/secrets and requires careful handling so secrets are not reprinted or leaked.
- **Mobile analysis** helps inspect mobile packages and artifacts; findings still require context.
- **Container/cloud/infrastructure scanning** evaluates the artifacts and configurations supported by the actual tool and scope.
- **Human AppSec review and penetration testing** provide contextual assessment and are not replaced by automation.

## 8. Part 5 — `VULNERABILITY_DETECTION_RULES.md`

Create a structured, actionable detection catalogue. It must include every explicitly named category below and map applicable checks to the relevant standards, CWE references, code/artifact evidence, and Part 6 report fields.

Required categories from the source:

- Broken authentication.
- Broken authorization.
- Injection.
- Insecure storage.
- Exposed secrets.
- Weak cryptography.
- Insecure APIs.
- Insecure dependencies.
- Misconfiguration.
- Data leaks.
- Excessive permissions.
- Insecure mobile components.

Also explicitly cover all detailed examples raised in the discussion:

- Architecture and attack surface.
- Trust boundaries and sensitive data flows.
- Defense-in-depth gaps, insufficient failure containment, and privilege separation where relevant.
- OAuth 2.0, OpenID Connect, JWT, session management, token lifecycle, refresh-token rotation/revocation, MFA, password policies, account recovery, session invalidation, broken login, session fixation, and credential stuffing.
- RBAC, ABAC concepts, object-level authorization, BOLA/IDOR, object-property authorization, function-level authorization, least privilege, and privilege escalation.
- Input validation, output encoding, sanitization, SQL/NoSQL injection, command injection, LDAP injection, XSS, template injection, and secure file uploads (file-type/content validation, size limits, malware scanning where appropriate, and storage isolation).
- Rate limiting, abuse prevention, API headers, sensitive business-flow abuse, resource-consumption issues, and unsafe use of third-party API responses where applicable.
- Secure local storage, secure communication, mobile permissions, exported Android components, intents, Android Keystore, Play Integrity, Android Network Security Configuration, iOS Keychain, App Transport Security, entitlements, jailbreak considerations, reverse-engineering protection, and runtime protection where applicable.
- Secrets management, cryptography/key management, password hashing including Argon2id/bcrypt and salts where appropriate, secure error handling, logging/monitoring, dependency management, and secure configuration.
- Vulnerable/outdated dependencies and relevant third-party components, validated against supplied lockfiles/manifests and current reliable vulnerability sources when available.
- Container/cloud security configuration where relevant.
- Sensitive information leakage, insecure API exposure, secrets in logs, security misconfiguration, and error-condition handling.
- Insecure coding patterns and secure alternatives.

For each category, structure detection rules using these fields where appropriate:

1. Rule/category name.
2. What to inspect.
3. Why it matters.
4. Evidence/signals to look for.
5. Context and applicability conditions.
6. Safe validation approach.
7. Common false positives or limitations.
8. Severity considerations (do not preassign a severity without context).
9. Relevant OWASP mapping and CWE mapping if supportable.
10. Remediation principle and secure alternative.
11. Required report evidence.
12. Related tools and authoritative references.

Detection guidance must not become a weaponized exploitation manual. Keep testing within authorized scope, prefer safe proof and synthetic/test data, and avoid destructive actions. Explain exploit scenarios at a level sufficient to understand risk and validate safely, without instructing unauthorized exploitation.

## 9. Part 6 — `SECURITY_REPORT_TEMPLATE.md`

Provide a reusable professional report template. The following detailed template fields are mandatory for each finding, reflecting all versions of the reporting structure discussed in the source:

```markdown
## [Vulnerability Title]

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
```

Do not delete any field above simply because another is similar. The prior source explicitly requested severity, vulnerability description, exploit scenario, affected code/component, recommended fix, why dangerous/security impact, root cause, OWASP/CWE mapping, exploitability, evidence, and prevention guidance.

The report as a whole must also contain:

- Executive summary.
- Scope and assets reviewed.
- Architecture / attack-surface understanding based on available evidence.
- Standards and versions used.
- Methodology and phases completed.
- Tools used and not used (and whether each was actually executed).
- Coverage matrix showing reviewed, partially reviewed, not reviewed, and not applicable areas.
- Findings prioritized by risk.
- Positive controls/strengths only when evidence supports them.
- Residual risk, assumptions, blockers, and limitations.
- Remediation priorities or sequence, distinguishing urgent fixes from longer-term improvements.
- Security regression and continuous-monitoring recommendations.

Use Critical / High / Medium / Low exactly as the required severity scale. Define a consistent, risk-based severity methodology in the report documentation using exploitability, impact, exposure, privileges/preconditions, affected assets, and contextual factors. If CVSS or another scoring framework is used, cite the official version and show how the score informs—not automatically replaces—the required severity category. Do not assign a definitive severity without adequate context; explain uncertainty.

The template must distinguish confirmed vulnerabilities from scanner alerts and unvalidated hypotheses. “No findings detected” must never be represented as “the application is secure.”

## 10. Part 7 — `SECURE_DEVELOPMENT_GUIDANCE.md`

Provide practical, actionable guidance for the remediation and prevention side. Include all improvement categories named in the source:

- Secure architecture patterns.
- Safer libraries.
- Authentication improvements.
- API hardening.
- Coding practices.
- Deployment security.

Connect this guidance to all the foundations and review areas enumerated earlier. In particular, include:

- SSDLC and shift-left practices.
- Security requirements before development.
- Threat modeling and trust boundaries.
- Defense-in-depth, failure containment, and privilege separation.
- Secure API design, authorization enforcement, input validation, output encoding, sanitization, injection prevention, secure file uploads, rate limiting, and abuse prevention.
- Authentication architecture and the token/session lifecycle, MFA, password storage, account recovery, and least privilege.
- Secure local mobile storage, mobile permission/component configuration, secure communication, and platform-specific Android/iOS guidance.
- Cryptography and secrets management.
- Error handling, security logging, monitoring, and sensitive-data protection.
- Dependency selection, updates, vulnerability monitoring, and software-supply-chain considerations supported by current references.
- Secure configuration, container/cloud deployment practices where applicable.
- Automated testing and code-review gates, security regression testing, incident response planning, and continuous security.

For each recommendation, explain the risk it mitigates, the recommended approach, practical implementation considerations, verification/testing, and relevant authoritative references. Prefer specific safe patterns and standards-backed advice over vague commands such as “use encryption” or “sanitize inputs.”

When suggesting a safer library or technology, validate that it is appropriate, maintained, compatible, and supported by current authoritative information. Do not invent libraries, versions, or “best” choices without evidence. Do not prescribe a migration that ignores architectural requirements, backward compatibility, operational constraints, or data migration risk. Separate immediate remediation from architectural work where useful.

## 11. Part 8 — `REFERENCES.md`

Build an organized official documentation library. Include all families specified in the source:

- OWASP standards and projects.
- NIST SSDF.
- MITRE CWE.
- Android security documentation.
- iOS / Apple security documentation.
- Tooling documentation.
- Protocol specifications relevant to OAuth 2.0, OpenID Connect, JWT, and session/authentication work.

At minimum, cover the named resources below and add other authoritative references when needed to support all eight parts. **Verify each URL and the current edition/version when web access is available.** Do not rely solely on copied search snippets. Keep the reference library organized by subject and indicate how each reference is used by the AI agent.

### 11.1 Core application-security standards and knowledge

- OWASP Mobile Application Security Verification Standard (MASVS): `https://mas.owasp.org/MASVS/`
- OWASP Mobile Application Security Testing Guide (MASTG): `https://mas.owasp.org/MASTG/`
- OWASP Mobile Application Security (MAS) project: `https://owasp.org/www-project-mobile-app-security/` or the current official MAS project page, verified at execution time.
- OWASP Mobile Top 10: use the current official OWASP Mobile Top 10 project page, verified at execution time.
- OWASP API Security Top 10 / API Security Project: `https://owasp.org/www-project-api-security/` or the current official API Security project/documentation page, verified at execution time.
- OWASP Application Security Verification Standard (ASVS): `https://owasp.org/www-project-application-security-verification-standard/`
- OWASP Top 10 Web Application Security Risks: use the current official OWASP Top 10 page and record the version actually verified. The source specifically requires OWASP Top 10 Web; preserve it even when the current edition differs from editions referenced by legacy code.
- OWASP Cheat Sheet Series: `https://cheatsheetseries.owasp.org/`
- MITRE CWE: `https://cwe.mitre.org/`
- MITRE CWE Top 25: `https://cwe.mitre.org/top25/`
- NIST Secure Software Development Framework (SSDF), SP 800-218: `https://csrc.nist.gov/pubs/sp/800/218/final`

### 11.2 Platform and protocol references

- Android Developers security best practices: locate and verify the current official Android security guidance.
- Android Keystore documentation: locate and verify the current official Android Developers page.
- Android Network Security Configuration: locate and verify the current official Android Developers page.
- Google Play Integrity API: `https://developer.android.com/google/play/integrity` (verify the canonical current page and its recommended use).
- Apple Platform Security: use the current official Apple Platform Security guide, including Keychain-related guidance where appropriate.
- Apple Developer Security overview: `https://developer.apple.com/security/`
- Apple Keychain Services documentation: locate and verify the current official Apple Developer page.
- Apple App Transport Security / `NSAppTransportSecurity`: locate and verify current official Apple Developer documentation.
- OAuth 2.0 framework and current security best practice: use the applicable current RFCs from the RFC Editor; at minimum verify RFC 6749 and RFC 9700 where relevant: `https://www.rfc-editor.org/rfc/rfc6749` and `https://www.rfc-editor.org/rfc/rfc9700`.
- JSON Web Token (JWT): RFC 7519, `https://www.rfc-editor.org/rfc/rfc7519`, plus any more current applicable security guidance.
- OpenID Connect: `https://openid.net/developers/specs/` and the applicable current specifications.
- Any further standards relevant to password storage, cryptography, TLS, key management, or authorization must be official and verified.

### 11.3 Tool documentation

Include verified official documentation for every tool in this list:

- Checkmarx.
- SonarQube.
- Semgrep.
- Snyk.
- GitHub Dependabot.
- OWASP Dependency-Check.
- Mobile Security Framework (MobSF).
- OWASP ZAP.
- Gitleaks.
- TruffleHog.
- Trivy.

Use the project/vendor’s canonical documentation rather than assuming a URL remains valid. Repositories may be cited where they are the official maintained source or where no better primary documentation exists; distinguish repository pages from user guides. Record licensing/access constraints only after verifying them, and do not assume a paid tool is available to the user.

### 11.4 Reference entry format

For each major reference, record:

- Resource/document title.
- Publisher/maintainer.
- Subject and why the AI agent should consult it.
- Canonical URL.
- Version, release year, RFC number, or last-updated information where published and verified.
- Relevant parts/sections of this repository that depend on it.
- Date checked.
- Any access limitation or uncertainty.

Do not copy extensive source text into the repository. Summarize in the knowledge base and link to the official material. Use short quotations only when necessary and follow the publisher’s applicable terms.

## 12. Cross-file consistency requirements

The eight parts must function as one system, not eight independent essays.

- Part 1 establishes the role and mandatory behavior.
- Part 2 defines the knowledge map and the standards/topics the agent must apply.
- Part 3 defines the ordered audit process.
- Part 4 explains the tools and evidence they produce.
- Part 5 turns the knowledge into actionable vulnerability-detection rules.
- Part 6 defines the exact reporting contract.
- Part 7 turns findings into secure development and prevention guidance.
- Part 8 points to the official primary sources that support the other parts.
- The README ties the files together and explains how to use them.

Use stable Markdown links between related files, such as linking detection rules to methodology phases and reference entries. Do not allow file names, severity labels, validation statuses, terminology, or phase names to drift across documents.

The following reporting fields must stay consistent everywhere: severity, category, OWASP/CWE mapping, vulnerability description, affected component, root cause, security impact, attack scenario, evidence, exploitability where supportable, recommended fix, prevention guidance, and limitations where relevant.

The review methodology must refer to the same standards and tools listed in the knowledge base and references. The tool guide must not state that a tool is mandatory or successfully run merely because it is named. The secure-development guidance must map back to the classes of weaknesses in the detection rules. The reference library must support the actual standards, techniques, and tools discussed in the files.

## 13. Practical execution and document-quality requirements

1. Inspect the working directory and any user-supplied project/context material before writing files.
2. Do not infer application language, framework, mobile platform, backend design, cloud provider, CI system, or tool availability in advance. Make the documentation technology-aware and applicability-based.
3. Write substantial documentation; do not deliver placeholders such as “add checks here,” empty headings, abbreviated summaries, or unexplained acronyms.
4. Expand acronyms at first use in each file where useful. Use consistent terminology throughout.
5. Keep Markdown readable: meaningful headings, tables only where they improve traceability, checklists for operational tasks, and code blocks only for exact examples or templates.
6. Avoid redundant bloating. Repeated requirements should remain represented, but shared principles may be cross-referenced if the relevant file still gives enough operational detail.
7. Be explicit about evidence quality. Explain which conclusions require source code, built mobile packages, runtime access, configuration, dependency manifests/lockfiles, logs, test accounts, architecture diagrams, or scanner output.
8. When relevant project inputs are absent, describe the missing inputs and the effect on coverage; do not make up a system architecture.
9. Make safety and authorization boundaries explicit for scanning, dynamic tests, penetration testing, secret handling, and tool commands.
10. Make a careful distinction between detection, verification, remediation, and prevention.
11. Keep the severity scale Critical / High / Medium / Low, while documenting how risk is assessed and how uncertainty is handled.
12. Ensure source-specified items are not silently removed during editing or optimization.
13. If web access is available, verify references before inserting a claim about a current edition or feature. If web access is unavailable, provide known official landing pages only where reasonably certain and label any unverified links/versions.
14. In `REFERENCES.md`, include not only a list of URLs but also enough descriptions to help the AI select the right source for a question.
15. In the README, explain a practical invocation pattern, for example: provide the application repository and scope, instruct the agent to read Part 1 and Parts 2–8 before reviewing, run only authorized available tools, follow Part 3 in order, apply Part 5, and report with Part 6 while citing Part 8.
16. Do not add hidden prompts, invisible instructions, unrelated commentary, or unsupported claims.

## 14. Completion audit — mandatory traceability checklist

Before declaring completion, audit the created repository against this checklist. Mark each item complete only after locating it in a real file/section. If an item is absent, fix the corresponding file first.

### Structure and role

- [ ] `README.md` plus all eight exactly named part files exist and contain substantive content.
- [ ] System Identity, Security Knowledge Base, Review Methodology, Tool Integration, Reporting Format, and Continuous Security Rules are explained.
- [ ] Senior AppSec Engineer, security architect, penetration-testing mindset, secure-code reviewer, and threat modeler roles appear.
- [ ] Evidence-based, risk-prioritized, attacker-and-defender-oriented behavior appears.

### Standards and foundations

- [ ] SSDLC, shift-left, threat modeling, pre-development security requirements, defense-in-depth, attack-surface analysis, trust boundaries, sensitive data flows, and security planning.
- [ ] OWASP MASVS, MASTG, Mobile Top 10, API Security Top 10, ASVS, OWASP Top 10 Web, CWE Top 25, NIST SSDF, and OWASP Cheat Sheet Series.
- [ ] OWASP Top 10 / API / Mobile and CWE mappings are version-aware and not silently hardcoded to an unverified edition.

### Mobile

- [ ] Android and iOS best practices, secure local storage, authentication flows, permissions, reverse engineering, secure communication, and runtime protection.
- [ ] Android exported components, permissions, intents, Keystore, Play Integrity, and Network Security Configuration.
- [ ] iOS Keychain, ATS, entitlements, and jailbreak considerations.

### Backend, API, auth, and data

- [ ] OAuth 2.0, OpenID Connect, JWT, sessions, token lifecycle, refresh rotation/revocation, MFA, password policies, account recovery, and session invalidation.
- [ ] RBAC, ABAC, object-level authorization, BOLA/IDOR, least privilege, and privilege escalation.
- [ ] Secure API design/gateways where relevant, validation, output encoding, sanitization, SQL/NoSQL/command/LDAP injection, XSS, template injection, secure upload controls, rate limiting, abuse prevention, API headers, and third-party API response handling.
- [ ] Sensitive data, encryption/cryptography, secrets management, secure storage, secure error handling, logging/monitoring, dependency management, secure configuration, password hashing, salts, Argon2id/bcrypt where appropriate, and password reset security.

### Workflow and tools

- [ ] Security Planning, Development, Automated Security Testing, Human Security Review, and Continuous Security stages and their listed details.
- [ ] Nine methodology phases in the required order.
- [ ] SAST: Checkmarx, SonarQube, Semgrep.
- [ ] SCA: Snyk, Dependabot, OWASP Dependency-Check.
- [ ] DAST: OWASP ZAP.
- [ ] Mobile tool: MobSF.
- [ ] Secrets tools: Gitleaks, TruffleHog.
- [ ] Infrastructure/container/cloud: Trivy.
- [ ] Human AppSec/InfoSec review, penetration testing, code review, architecture review, vulnerability monitoring, dependency updates, incident response planning, and security regression testing.
- [ ] Tool output validation, false-positive handling, evidence records, unavailable/not-run status, and safe-scope requirements.

### Vulnerability catalogue and reporting

- [ ] Broken authentication/authorization, injection, insecure storage, exposed secrets, weak crypto, insecure APIs, insecure dependencies, misconfiguration, data leaks, excessive permissions, and insecure mobile components.
- [ ] Broken login, session fixation, credential stuffing, BOLA/IDOR, privilege escalation, logs containing secrets, and the named injection classes.
- [ ] Each detection rule includes inspection targets, evidence, applicability, safe validation, limitations, severity context, mappings, remediation, and references.
- [ ] Each report finding includes title, Critical/High/Medium/Low severity, category, OWASP/CWE mapping, affected component, description, impact, attack scenario, root cause, evidence, exploitability where supportable, recommended fix, prevention, references, validation status, and relevant limitations.
- [ ] Overall report includes summary, scope, versions, phases, tools run/not run, coverage, findings, supported strengths, residual risks, limitations, remediation priorities, and regression/continuous-monitoring recommendations.

### Secure development and references

- [ ] Secure architecture patterns, safer libraries, authentication improvements, API hardening, coding practices, and deployment security.
- [ ] Official documentation for every listed OWASP, MITRE, NIST, Android, Apple, protocol, and security tool reference is covered in Part 8.
- [ ] Links/versions are checked where possible and uncertain entries are labelled honestly.
- [ ] Cross-file links and terminology are consistent; no required item is represented only by a vague heading.

## 15. Final delivery behavior

When complete, provide a concise completion message that:

- States whether the exact repository/files were created or whether only file contents could be supplied.
- Lists the required files and confirms the eight parts are present.
- States whether official reference links/versions were verified or whether any remain unverified.
- Discloses any genuine blocker or remaining limitation.
- Does not claim the system has been tested against a real application unless it actually has.

Do not stop after writing Part 1. Do not promise to create the remaining parts in a later turn. Complete the repository as far as the current environment permits and perform the traceability audit now.
