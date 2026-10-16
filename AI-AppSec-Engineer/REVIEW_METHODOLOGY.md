# Review Methodology

Follow these phases in order. Use only evidence supplied or gathered under explicit authorization. Every phase records assets considered, evidence provenance, limitations, findings/status, and handoff to the [report contract](SECURITY_REPORT_TEMPLATE.md).

## 1. Architecture discovery

**Objective.** Establish the evidenced system and attack surface before judging controls.

**Inputs/actions.** Request or inspect source, mobile clients, services, APIs, integrations, identities, deployment/infrastructure, configurations, manifests, diagrams, routes, and data classifications. Inventory entry points, trust boundaries, sensitive data flows, privileged actions, tenants, and external dependencies.

**Evidence/output/exit.** Produce an asset and evidence inventory plus unknowns; use MASVS/MASTG, ASVS, API guidance, and NIST SSDF as applicable. Exit only when the inventory is sufficient to state what is unknown; missing material remains a coverage limitation.

**Tools and report handoff.** Use repository search, manifest inspection, architecture material, and authorized inventory tooling only when available. Record component identity, evidence provenance, applicability, and unknowns in the Part 6 architecture, scope, and coverage sections; do not infer a production component from a filename or a diagram alone.

## 2. Threat modeling

**Objective.** Map features, actors, assets, trust transitions, threats, controls, and abuse cases.

**Actions.** Identify attacker capabilities, privileged paths, failure modes, defense-in-depth gaps, and high-value flows including authentication, payment, recovery, administration, upload, and integrations. Validate design claims against source/configuration where possible.

**Output.** Threat/assumption register and prioritized review questions. Do not turn a theoretical threat into a confirmed finding without evidence.

**Inputs/evidence/exit.** Use the architecture inventory, data classifications, business flows, identities, and supplied requirements as inputs. Collect actor capability, asset, trust transition, abuse case, control, and residual-risk evidence. Apply SSDLC, NIST SSDF, ASVS, MASVS/MASTG, and API guidance as applicable; tools are optional and conditional. Exit with an explicit threat/assumption register, or document why missing architecture or business context prevents one. Transfer supported threats and evidence gaps to Part 6 findings or limitations.

## 3. Mobile analysis

**Applicability.** Run only if Android/iOS/mobile artifacts are in scope.

**Actions/evidence.** Inspect source or authorized packages for secure storage, permissions, exported Android components, intents/deep links, Keystore, Play Integrity, Network Security Configuration, Keychain, ATS, entitlements, communication, certificate validation, backups, privacy, reverse engineering, tampering, jailbreak/root, and runtime protection. MobSF may support evidence when available and authorized.

**Exit.** Record tested platform/version/artifact and limitations; do not mark a platform passed merely because no visible source issue exists.

**Objective/inputs/standards.** The objective is to assess mobile-specific storage, platform interaction, communication, authentication, privacy, and resilience without assuming that a mobile client exists. Use source, signed or unsigned packages, build configuration, runtime evidence, test devices, and mobile scanner output when supplied. Apply current MASVS objectives and MASTG testing knowledge, plus official Android or Apple guidance. The expected output is a per-platform evidence and applicability record, with findings mapped to Part 6; exit by recording reviewed artifacts, untested platform areas, and reasons for any not-applicable decision.

## 4. Backend/API analysis

**Actions.** Enumerate documented and evidenced routes or record inventory gaps. Trace identity, OAuth/OIDC/JWT/session lifecycle, MFA, recovery, RBAC/ABAC, object/function/property authorization, BOLA/IDOR, validation, encoding, uploads, headers, rate limits, business-flow abuse, third-party responses, and data handling.

**Evidence/exit.** Collect routes/methods, policy/configuration, request/response schemas, enforcement points, and safe test results. Dynamic work requires authorized targets, accounts, rate limits, and non-destructive scope.

**Objective/standards/output.** The objective is to determine whether server-side controls protect routes, data, and business operations. Use route inventories, schemas, gateway policy, identity-provider configuration, service identities, logs, test accounts, and authorized runtime evidence. Apply the verified OWASP API Security Top 10 edition in [REFERENCES.md](REFERENCES.md), ASVS, OAuth/OIDC RFCs, and relevant CWE mappings. Output a route/control matrix, evidence-backed observations, and explicit inventory gaps; exit only when each supplied route source has been considered or its absence is documented. Send validated issues and residual uncertainty to Part 6.

## 5. Source code review

**Actions.** Follow untrusted input to validation and sinks; follow sensitive data to storage/logs/egress; trace authorization to server enforcement. Review injection, serialization, errors, crypto/secrets, logging, uploads, configuration, mobile components, and insecure patterns. Keyword search is a lead, not a conclusion.

**Output.** Verifiable component references and evidence excerpts with secrets redacted.

**Objective/inputs/tools.** The objective is to trace behavior from untrusted source to validation, authorization, sensitive-data sinks, and security-relevant configuration. Use source, generated code where supplied, build files, tests, configuration, and code-review evidence. SAST tools are optional leads; manual review remains required. Apply the detection rules, ASVS, OWASP Top 10:2025 when an edition-specific web mapping is appropriate, CWE, and platform guidance. Exit when in-scope high-risk paths have been traced or the missing source/build context is recorded; every observation moves to Part 6 with location, evidence, validation status, and limitations.

## 6. Dependency analysis

**Actions.** Inspect manifests/lockfiles/SBOMs; distinguish direct from transitive dependencies and versions. Correlate advisories with package identity, affected range, reachability/applicability, upgrade/migration constraints, and compensating controls. Use SCA only when available.

**Exit.** Never equate a name match with exploitable exposure; record unavailable lockfiles, databases, or execution evidence.

**Objective/inputs/standards.** The objective is to establish component identity and actionable dependency risk, not merely to count packages. Inputs include direct and transitive manifests, lockfiles, SBOMs, build resolution, advisory data, licenses where supplied, and reachability evidence. Snyk, Dependabot, and OWASP Dependency-Check are conditional evidence sources; retain their actual execution status and database timestamp when available. Apply supply-chain guidance, CWE-1104 where supportable, and the current tool documentation. Output a dependency/advisory matrix with package, version, path, affected range, reachability, fix constraints, and limitations; hand each validated risk to Part 6.

## 7. Configuration review

**Actions.** Inspect supplied build, runtime, cloud, container, infrastructure-as-code, secrets delivery, identity, network, logging, TLS, and release settings. Apply Trivy or other tooling conditionally. Compare secure defaults against the actual deployment context.

**Output.** Configuration keys/resources with provenance, not inferred production state.

**Objective/inputs/standards.** The objective is to identify insecure build, runtime, cloud, container, network, identity, secret-delivery, logging, and release settings in the supplied environment. Use IaC, deployment manifests, images, build profiles, policy files, cloud exports, and configuration evidence; do not infer live state from a template. Trivy and other configuration scanners are optional and must be scoped and recorded. Apply ASVS, API guidance, Android/iOS platform guidance, NIST SSDF, and applicable vendor documentation. Exit after supplied configuration surfaces are reviewed or gaps are stated; report configuration findings with exact keys/resources and evidence in Part 6.

## 8. Security testing

**Actions.** Correlate SAST, SCA, DAST, secret, mobile, container/cloud scans, human review, architecture review, and penetration-testing evidence. Record who/what ran it, scope, configuration, timestamp, raw report location, and limitations. Triage duplicates and false positives.

**Safety.** No unauthorized scanning, denial-of-service, real-data extraction, credential abuse, or third-party testing. Prefer passive/read-only checks, test accounts, synthetic data, and bounded validation.

**Inputs/outputs/exit.** Inputs are authorized source, artifacts, test targets, accounts, scanner reports, configuration, and human-review notes. Record each evidence source separately: SAST, SCA, DAST, secret detection, mobile analysis, container/cloud scanning, code review, architecture review, and penetration testing. Tools are never implied by their names; if unavailable or not run, record that status. Output a redacted evidence register and validated or unvalidated observations; exit when the approved test plan, stop conditions, and supplied evidence have been exhausted, then hand all results to Part 6.

## 9. Final risk assessment

**Actions.** Validate and prioritize findings by impact, exposure, assets, exploitability, privileges/preconditions, controls, and confidence. Assign `Critical / High / Medium / Low` only with rationale. Distinguish confirmed findings from tool-reported or potential observations.

**Output/exit.** Complete Part 6: executive summary, scope, architecture, standards, phases, tools run/not run, coverage matrix, prioritized findings, supported strengths, residual risk, blockers, remediation sequence, and regression/monitoring recommendations. “No findings detected” is not a security assertion.

**Inputs/standards/limitations.** Use all prior phase outputs, evidence provenance, validation status, business impact, and residual-risk decisions. Apply the verified standard editions recorded in [REFERENCES.md](REFERENCES.md), but do not force a mapping when the weakness or edition is uncertain. The final output must distinguish confirmed, likely, potential, tool-reported-unvalidated, not reproducible, and not applicable states; identify missing evidence and untested assets; and state that no real application assurance follows from this framework alone.
