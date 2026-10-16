# Secure Development Guidance

This guidance turns findings from [Part 5](VULNERABILITY_DETECTION_RULES.md) into remediation and prevention. Select controls for actual architecture, data, compatibility, migration, and operational constraints; validate with tests and the official sources in [REFERENCES.md](REFERENCES.md).

## Build security into design and delivery

**Risk mitigated:** insecure design, inconsistent controls, and late discovery. **Approach:** define security requirements, data classification, abuse cases, threat models, trust boundaries, authorization matrix, logging requirements, and verification conditions before development. Use defense in depth, failure containment, secure defaults, segmentation, and privilege separation. **Implementation:** make design review a change gate for new trust boundaries and privileged/data-sensitive flows. **Verification:** retain threat-model decisions and test each security acceptance criterion during release and regression testing.

## Safer libraries and technology selection

**Risk mitigated:** introducing an unmaintained, incompatible, or insecure component while attempting remediation. **Approach:** choose maintained platform- or vendor-supported libraries that fit the language, threat model, interoperability requirements, and operational support model; use current authoritative guidance rather than calling any library universally “best.” **Implementation:** record package identity, supported versions, maintenance signals, advisory history, transitive dependencies, relevant license or access constraints, migration effort, data-format impact, and rollback plan before adoption. **Verification:** review manifests and lockfiles, run applicable tests and SCA checks, inspect official support/security information, and document residual compatibility or migration risk in Part 6 using [REFERENCES.md](REFERENCES.md).

## Identity, authorization, and sessions

**Risk mitigated:** account takeover, session fixation, BOLA/IDOR, and privilege escalation. **Approach:** use a reviewed identity architecture appropriate to client type; enforce authorization server-side for every object, function, and mutable property; deny by default; minimize role/service privileges.

**Implementation:** validate OAuth 2.0/OIDC redirects and token issuer, audience, signature, algorithm, expiry, scope, and nonce/state where applicable. Define session lifetime, renewal, logout/invalidation, refresh-token rotation/revocation, recovery controls, MFA/step-up conditions, password policy, and credential-stuffing/rate-limit response. Passwords use a purpose-built hash such as Argon2id or bcrypt where appropriate, unique salts, and supported work factors; never reversible storage or fast general-purpose hashes.

**Verification:** unit/integration-test ownership and role changes, cross-tenant access, logout/revocation, recovery, token rejection, and rate-limited abuse paths with test identities. Review changes against the authentication and authorization rules.

## API hardening and coding practices

**Risk mitigated:** injection, XSS, unsafe uploads, data exposure, and abuse. **Approach:** publish an API inventory and bounded contracts; authenticate and authorize at the server; validate structure/type/range/allowlists at trust boundaries; encode output for its exact context; treat third-party responses as untrusted.

**Implementation:** use parameter binding rather than query construction; avoid command interpreter calls; use safe directory/query APIs; constrain templates; validate uploads by independently checking type/content/size and isolate storage; set timeouts/resource limits; rate-limit and monitor sensitive business flows; use headers and caching controls suited to the protocol. Sanitization is not a substitute for validation or contextual output encoding.

**Verification:** automated negative tests for validation, authorization, injection sinks, encoding contexts, uploads, resource limits, and third-party failure responses; peer review the sink and enforcement point, not only the input helper.

## Mobile protection

**Risk mitigated:** local-data disclosure, component abuse, interception, and tampering. **Approach:** apply MASVS controls and MASTG testing where a mobile client exists. Store secrets/tokens only through appropriate platform storage; minimize permissions and exposed components; use TLS with sound certificate validation; make resilience proportionate to assets and adversary.

**Android:** make components non-exported unless necessary; validate all IPC/deep-link data; use explicit intents internally; minimize permissions; use Android Keystore appropriately; review Network Security Configuration and cleartext exceptions; use Play Integrity as a risk signal with server-side decisions.

**iOS:** use Keychain with suitable accessibility/access control; minimize entitlements; keep ATS exceptions narrow and justified; validate URL handling and server trust; account for jailbreak signals as non-exclusive risk signals.

**Verification:** inspect released artifacts and build configuration, execute authorized platform tests, and check backups, logs, screenshots, notifications, local databases, and network traffic. Do not claim reverse-engineering resistance is absolute.

## Cryptography, secrets, and sensitive data

**Risk mitigated:** disclosure, tampering, key compromise, and secret leakage. **Approach:** use maintained platform/vendor primitives and managed key services where compatible; segregate keys from data; use cryptographically secure randomness; rotate/revoke secrets; minimize collection/retention.

**Implementation:** keep secrets out of source/history/logs and deliver them with scoped identities and audited secret stores. Design encryption, signing, key derivation, TLS, and lifecycle choices from current official guidance and the actual interoperability/migration requirement. Plan migration and backward compatibility before changing crypto or password formats.

**Verification:** secret scans with protected output, key-access review, TLS/certificate tests, rotation exercises, and data-flow/log-redaction tests.

## Dependencies, deployment, and operations

**Risk mitigated:** known-vulnerable components, supply-chain compromise, misconfiguration, and exposed runtime. **Approach:** maintain manifests/lockfiles/SBOMs; monitor advisories; assess reachability and upgrade impact; prefer maintained compatible libraries based on official support/security information, not a generic “best library” claim.

**Implementation:** pin and update through tested workflows; protect build provenance and credentials; minimize container base images and runtime privileges; use distinct environments; restrict network/identity permissions; secure IaC defaults; protect admin interfaces; configure non-sensitive errors and useful audit logging. Test data migration, API compatibility, rollback, and operational capacity before architectural changes.

**Verification:** SCA/container/configuration scans plus manual package/configuration review; deployment policy checks; smoke/regression tests; incident-response exercises; and exception records with owners/expiry.

## Deployment security controls

**Risk mitigated:** insecure release configuration, exposed administration surfaces, build compromise, and excessive runtime privilege. **Approach:** separate environments, protect CI/CD identities and signing material, minimize network and workload permissions, use secure defaults, and treat deployment configuration as security-relevant code. **Implementation:** review IaC, container images and base-image provenance, secret delivery, service identities, ingress/egress, debug and release settings, admin interfaces, TLS, logging, backups, rollback, and cloud/container policy. Do not infer live deployment state from a template or scanner result alone. **Verification:** inspect supplied deployment evidence when authorized, compare it with the intended architecture, run bounded configuration/container checks, exercise rollback and health controls, and record omitted environments, unavailable evidence, and exception expiry.

## Continuous security

**Risk mitigated:** regression and unmanaged residual risk. **Approach:** require security code review, threat-model updates for material changes, automated tests and policy gates where agreed, vulnerability monitoring, dependency updates, regression suites for every validated finding, and incident-response plans.

**Verification:** track remediation evidence and residual-risk acceptance; regularly re-run authorized checks after material changes; measure remediation age, exception expiry, coverage gaps, and alert quality. A gate is configurable and should fail safely only when ownership, triage capacity, and false-positive process are established.
