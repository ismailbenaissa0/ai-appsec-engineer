# Security Knowledge Base

This is the technical map used with the [system prompt](AI_SECURITY_ENGINEER_SYSTEM_PROMPT.md) and [methodology](REVIEW_METHODOLOGY.md). Apply controls only where architecture and evidence make them relevant; a standard is a reference framework, not automatic certification. OWASP Top 10 mappings that cite an edition must identify 2025 as current; a legacy edition is acceptable only when the project evidence requires it and must be labelled superseded. The API Security Top 10 edition is recorded in [REFERENCES.md](REFERENCES.md) only after checking the official project page.

## Security foundations

Use a Secure Software Development Lifecycle (SSDLC) and shift security left: define security requirements and verification conditions before implementation; classify sensitive data; identify assets, actors, entry points, privileged operations, and trust transitions; model threats; plan authentication and authorization; and make security acceptance criteria testable. Revisit them at design, release, and change time.

Architecture review maps client, service, API, data store, identity provider, integration, build, runtime, administration, and deployment surfaces. Mark trust boundaries whenever identity, privilege, network zone, tenant, or data classification changes. Trace sensitive data from collection through processing, storage, sharing, logging, backup, retention, and deletion.

Assess defense in depth: independent controls, failure containment, secure defaults, backup protections, segmentation, least privilege, and privilege separation. A mobile client is not an authorization boundary; enforce access decisions on a trusted server-side enforcement point.

## Mobile application security

Use OWASP MASVS for mobile control objectives and verification expectations, and MASTG for testing knowledge and evidence techniques. Use the current OWASP Mobile Top 10 as awareness material; do not apply mobile controls to a non-mobile system without marking them not applicable. Apply official Android Security Best Practices and iOS Security Best Practices according to the actual platform and release context.

### Android

Inspect manifest and build configuration for exported activities, services, receivers, and content providers; permissions; explicit versus implicit intents; deep links/App Links; PendingIntent behavior; debug/release flags; signing; backups; WebViews; and component exposure. Inspect secure local storage for tokens, files, databases, preferences, clipboard, notifications, screenshots, and logs. Review Android Keystore use for non-exportable key handling and platform-backed protection where suitable; review Network Security Configuration, TLS/certificate validation, cleartext exceptions, and Play Integrity integration only as an input signal, not authorization by itself.

### iOS

Inspect Keychain access controls/access groups, local files/databases/UserDefaults, backups, pasteboard, screenshots, logs, custom URL schemes/universal links, entitlements, app extensions, and App Transport Security (ATS) exceptions. Review certificate/server-trust handling, secure communication, platform authentication, jailbreak/tampering assumptions, signing/build settings, and resilience measures proportionate to the threat model.

### Cross-platform mobile

Review secure authentication flows, token/cookie storage, biometrics as local gates rather than server authentication, permission management and minimization, privacy/consent, reverse-engineering protection, tampering, root/jailbreak/virtual-device considerations, runtime protection, and update behavior. Require evidence from source, package, runtime, or platform configuration; absence of evidence is not a pass.

## Backend, API, authentication, and authorization

Apply OWASP API Security Top 10 and ASVS where relevant. Inventory routes, methods, versions, schemas, authentication mechanisms, service-to-service calls, API gateways, and third-party integrations. Secure design requires input validation at each trust boundary, context-appropriate output encoding, and sanitization only where transformation is appropriate; these are different controls.

Review OAuth 2.0 and OpenID Connect flows, redirect/callback registration, client type, PKCE where applicable, issuer/audience/signature/algorithm/expiry validation for JWTs, session creation/renewal/invalidation, token scope, expiration, refresh-token rotation/revocation, logout, Multi-Factor Authentication (MFA), password policies/storage, account recovery/reset, session fixation, broken login, and credential stuffing resistance.

For authorization, trace decisions to the server-side enforcement point. Review RBAC, Attribute-Based Access Control (ABAC), tenant isolation, object-level, object-property-level, and function-level authorization; test for Broken Object Level Authorization (BOLA)/Insecure Direct Object Reference (IDOR), privilege escalation, and excessive service permissions. Verify least privilege for both humans and workloads.

Review SQL, NoSQL, command, LDAP, template injection, Cross-Site Scripting (XSS), deserialization where present, secure file uploads (allowlisted type/content checks, size controls, malware scanning where appropriate, isolated storage), API security headers, request limits, rate limiting, abuse/resource-consumption controls, sensitive business-flow abuse, inventory gaps, and safe handling of data received from third-party APIs, including validation of untrusted responses.

## Secure coding, data, and operations

Use the OWASP Cheat Sheet Series for technology-specific secure implementation. Manage secrets through approved delivery/storage paths; never hardcode credentials. Review key generation, storage, access, rotation, revocation, randomness, TLS/certificate validation, and protection in transit/at rest against current authoritative guidance. Do not prescribe a primitive or parameter without confirming suitability for the system.

Passwords require a purpose-built password hash such as Argon2id or bcrypt where appropriate, unique salts, correctly selected work factors, protected password-reset and account-recovery flows, and no plaintext, reversible encryption, or fast general-purpose hash.

Review client-visible errors, stack traces, secret/token/password fields in logs, log access/retention, auditability, alerting, and monitoring. Logs must support investigation without becoming a sensitive-data leak. Review dependencies (direct/transitive versions, updates, advisories, reachability where supportable), secure configuration, and container/cloud runtime controls when supplied.

## Professional security lifecycle

| Stage | Required work |
|---|---|
| Security Planning | Requirements, sensitive data, threat model, trust boundaries, authentication/authorization design. |
| Development | Secure API design, validation, sanitization, rate limiting, secure standards, dependency security. |
| Automated Security Testing | SAST: Checkmarx/SonarQube/Semgrep; SCA: Snyk/Dependabot/OWASP Dependency-Check; DAST with OWASP ZAP where authorized; MobSF for mobile artifacts; Gitleaks/TruffleHog for secrets; Trivy for container, infrastructure, or cloud artifacts where applicable. |
| Human Security Review | Application Security (AppSec) review, Information Security review (InfoSec), code review, security architecture review, penetration testing. |
| Continuous Security | Vulnerability monitoring, dependency updates, incident-response planning, security regression testing. |

Automation does not replace human review; penetration testing does not replace secure design; continuous security does not stop at release.

## Vulnerability knowledge and reusable review rules

Use OWASP Top 10 Web, API Security Top 10, Mobile Top 10, CWE Top 25, and supportable CWE entries. Map only when the weakness fits the actual edition/category. Explicitly consider broken authentication, session fixation, credential stuffing, flawed recovery; injection types; IDOR/BOLA and function/object-property authorization; misconfiguration; insecure APIs; data exposure; logs containing secrets; insecure storage; weak crypto; exposed secrets; excessive permissions; insecure mobile components; outdated dependencies; and insecure coding patterns.

For each review question: inspect the architecture first, map feature to threat, locate enforcement/data flow, gather evidence, establish applicability, validate safely, propose a secure alternative, and send a complete finding to [Part 6](SECURITY_REPORT_TEMPLATE.md). Detailed rule fields are in [Part 5](VULNERABILITY_DETECTION_RULES.md).

### Reusable AI code-review rules

The agent must review architecture before implementation details, identify attack surfaces, map features and sensitive assets to threats, and trace trust boundaries and enforcement points. It must check authentication, authorization, input validation, sensitive-data handling, API abuse protection, dependency vulnerabilities, insecure coding patterns, logging/error disclosure, configuration, and mobile controls when applicable. For each material observation, it must suggest a secure alternative and produce a report-ready record with severity, description, affected component, impact, attack scenario, root cause, evidence, validation status, OWASP/CWE mapping where supportable, recommended fix, prevention, references, and limitations. A missing artifact, absent tool result, or unreviewed platform must be recorded as an evidence gap rather than a secure result.
