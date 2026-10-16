# AI AppSec Engineer Reference Compendium

This repository is an operating manual for an AI application-security review agent. It turns supplied application source, mobile builds, backend and API assets, infrastructure/configuration, dependency manifests, architecture material, and authorized tool evidence into an evidence-based security assessment. It is a framework, not a certification and not proof that an application is secure.

## The six layers

1. **System Identity** — the role, safety boundaries, and evidence discipline in [Part 1](AI_SECURITY_ENGINEER_SYSTEM_PROMPT.md).
2. **Security Knowledge Base** — the technical foundations, standards, and applicability rules in [Part 2](SECURITY_KNOWLEDGE_BASE.md).
3. **Review Methodology** — the nine ordered assessment phases in [Part 3](REVIEW_METHODOLOGY.md).
4. **Tool Integration Layer** — conditional, safe use and interpretation of scanners in [Part 4](SECURITY_TOOL_INTEGRATION.md).
5. **Reporting Format** — the common finding contract and report structure in [Part 6](SECURITY_REPORT_TEMPLATE.md).
6. **Continuous Security Rules** — prevention, regression, monitoring, and remediation guidance in [Part 7](SECURE_DEVELOPMENT_GUIDANCE.md).

The knowledge base is the library and training manual; the system prompt is the mission instruction that activates it; tool outputs are evidence; and the report is the professional deliverable. The mission prompt never replaces the other parts.

## End-to-end workflow

Use the repository as one controlled flow: collect the authorized source, mobile artifacts, backend/API material, infrastructure and configuration, dependency evidence, architecture material, and supplied tool output; establish scope and evidence gaps; apply the knowledge base and ordered methodology; use only available and authorized tools; apply the detection rules to validated observations; and produce the report with the shared finding contract. Part 7 then turns validated findings into remediation, regression testing, monitoring, and incident-response work. Missing inputs remain coverage limitations rather than implicit passes.

## Files and reading order

| File | Purpose |
|---|---|
| [AI_SECURITY_ENGINEER_SYSTEM_PROMPT.md](AI_SECURITY_ENGINEER_SYSTEM_PROMPT.md) | Reusable role and behavioral prompt. |
| [SECURITY_KNOWLEDGE_BASE.md](SECURITY_KNOWLEDGE_BASE.md) | Standards-backed technical map. |
| [REVIEW_METHODOLOGY.md](REVIEW_METHODOLOGY.md) | Repeatable nine-phase audit workflow. |
| [SECURITY_TOOL_INTEGRATION.md](SECURITY_TOOL_INTEGRATION.md) | Tool scope, evidence, and triage. |
| [VULNERABILITY_DETECTION_RULES.md](VULNERABILITY_DETECTION_RULES.md) | Actionable detection catalogue. |
| [SECURITY_REPORT_TEMPLATE.md](SECURITY_REPORT_TEMPLATE.md) | Findings and report contract. |
| [SECURE_DEVELOPMENT_GUIDANCE.md](SECURE_DEVELOPMENT_GUIDANCE.md) | Remediation and prevention playbook. |
| [REFERENCES.md](REFERENCES.md) | Official-source reference library. |

Read Part 1 and then Parts 2–8 before beginning a review. Use Part 3 in order; apply Part 5 only where the technology and evidence make a rule applicable; consume authorized available tools under Part 4; and report using Part 6 with citations from Part 8. Use Part 7 to turn validated findings into safe remediation and prevention work.

## Expected inputs and coverage

Request or inventory, where relevant: source and build instructions; dependency manifests and lockfiles; mobile packages and signing/build configuration; route/API inventory and schemas; architecture and data-flow diagrams; infrastructure-as-code, container, cloud, and runtime configuration; CI/CD configuration; logs; test accounts; security requirements; and prior scanner reports. Record provenance, version/commit, access restrictions, and gaps.

Do not infer an application language, mobile platform, cloud provider, CI system, architecture, or tool availability. Missing source, runtime access, manifests, test identities, architecture evidence, or scan output constrains coverage; state that constraint as `not reviewed`, `partially reviewed`, or `not applicable`, not as a pass.

## Safe invocation pattern

Provide the repository and engagement scope, then instruct the agent to: read this README and Parts 1–8; identify available evidence and authorization; follow the nine phases in [Part 3](REVIEW_METHODOLOGY.md); run only explicitly authorized and available non-destructive checks; validate tool alerts in context; use [Part 5](VULNERABILITY_DETECTION_RULES.md); and issue a [Part 6](SECURITY_REPORT_TEMPLATE.md) report citing [Part 8](REFERENCES.md).

Security testing is authorized only within the stated target, accounts, time window, rate limits, and data-handling rules. Do not perform destructive tests, denial-of-service, production data extraction, credential abuse, or testing of third-party systems unless explicit authorization covers them. Prefer read-only inspection, synthetic/test data, and bounded validation.

## Agent environments

**Filesystem/repository agent.** Inspect project instructions, manifests, and available tools first. Review assets without modifying production code unless the user explicitly requests remediation. Save requested outputs only to approved paths.

**Chat-only agent.** Ask for the minimum relevant source, configuration, package, report, or architecture evidence. Analyze only what is supplied and label unavailable work clearly. It must not claim a tool ran, a path exists, or a control passed without evidence.

## Reference currency

Reference baseline verified 2026-10-16:

- OWASP Top 10:2025 is current. Verified at https://top10.owasp.org/2025/ and https://github.com/OWASP/Top10.
- OWASP API Security Top 10: verify the current edition at the official API Security project page. If confirmed, record it. If not, label it “verify before use.”

Use the verified editions in [REFERENCES.md](REFERENCES.md) and all OWASP mappings. Do not name 2021 as current; it is superseded by 2025. Do not invent edition numbers for other standards.
