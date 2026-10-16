# Official Reference Library

Reference baseline verified 2026-10-16:

- OWASP Top 10:2025 is current. Verified at https://top10.owasp.org/2025/ and https://github.com/OWASP/Top10.
- OWASP API Security Top 10: verify the current edition at the official API Security project page. If confirmed, record it. If not, label it “verify before use.”

Entries marked **verified** had their canonical official URL checked in this work. A checked URL establishes availability, not applicability to a particular system. Versions not published or not individually confirmed are stated as “verify before use.” This library supports the other parts; it does not replace reading the current source.

## Core standards and knowledge

| Resource / publisher | Use in this repository | Canonical URL | Version/date status | Used by |
|---|---|---|---|---|
| OWASP Top 10 / OWASP Foundation | Web-risk awareness and mappings | https://top10.owasp.org/2025/ ; https://github.com/OWASP/Top10 | **Verified:** OWASP Top 10:2025 is current, checked 2026-10-16 | Parts 1, 2, 5–7 |
| OWASP API Security Top 10 / OWASP Foundation | API review and mappings | https://api-security.owasp.org/ | **Official portal lists 2023 as the latest listed edition checked 2026-10-16; verify before use if the portal changes** | Parts 1–7 |
| OWASP MASVS / OWASP Foundation | Mobile verification objectives | https://mas.owasp.org/MASVS/ | **Verified:** canonical documentation checked 2026-10-16; version label not asserted here | Parts 1–3, 5, 7 |
| OWASP MASTG / OWASP Foundation | Mobile testing knowledge/evidence | https://mas.owasp.org/MASTG/ | **Verified:** canonical documentation checked 2026-10-16; version label not asserted here | Parts 1–3, 5, 7 |
| OWASP Mobile Top 10 / OWASP Foundation | Mobile-risk awareness | https://owasp.org/projects/mobile-top-10 | **Verified:** official project page checked 2026-10-16; page identifies 2024 release | Parts 1, 2, 5–7 |
| OWASP ASVS / OWASP Foundation | Application verification requirements | https://owasp.org/www-project-application-security-verification-standard/ | **Official page identifies 5.0.0 as the latest stable content; project page labels 5.0.0 latest (Bleeding Edge), checked 2026-10-16** | Parts 1–3, 5–7 |
| OWASP Cheat Sheet Series / OWASP Foundation | Implementation-specific safe patterns | https://cheatsheetseries.owasp.org/ | **Verified URL; living guidance** | Parts 1, 2, 7 |
| OWASP Password Storage Cheat Sheet / OWASP Foundation | Password hashing, salts, work factors, and recovery-related implementation review | https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html | **Verified URL; check current recommendations before selecting parameters** | Parts 2, 5, 7 |
| OWASP Cryptographic Storage Cheat Sheet / OWASP Foundation | Data-at-rest and key-management design review | https://cheatsheetseries.owasp.org/cheatsheets/Cryptographic_Storage_Cheat_Sheet.html | **Verified URL; apply to the actual use case** | Parts 2, 5, 7 |
| OWASP Secrets Management Cheat Sheet / OWASP Foundation | Secret lifecycle, storage, delivery, and rotation review | https://cheatsheetseries.owasp.org/cheatsheets/Secrets_Management_Cheat_Sheet.html | **Verified URL; current guidance is living** | Parts 2, 5, 7 |
| OWASP Session Management Cheat Sheet / OWASP Foundation | Session identifiers, lifecycle, invalidation, and cookie/session controls | https://cheatsheetseries.owasp.org/cheatsheets/Session_Management_Cheat_Sheet.html | **Verified URL; apply controls appropriate to the session architecture** | Parts 1–3, 5, 7 |
| CWE and CWE Top 25 / MITRE | Weakness taxonomy and supportable mappings | https://cwe.mitre.org/ ; https://cwe.mitre.org/top25/ | **CWE Top 25:2025 is identified as the current list; checked 2026-10-16. Use the current CWE catalog for individual mappings.** | Parts 1, 2, 5, 6 |
| NIST SP 800-218 SSDF / NIST | Secure software lifecycle practices | https://csrc.nist.gov/pubs/sp/800/218/final | **Final Version 1.1, published February 2022, checked 2026-10-16** | Parts 1–3, 7 |

## Platform and protocol sources

| Resource / publisher | Use | Canonical URL | Status | Used by |
|---|---|---|---|---|
| Android security best practices / Google | Android implementation review | https://developer.android.com/privacy-and-security/security-best-practices | **Verified URL** | Parts 2, 3, 5, 7 |
| Android Keystore / Google | Key handling | https://developer.android.com/privacy-and-security/keystore | **Verified URL** | Parts 2, 5, 7 |
| Android Network Security Configuration / Google | Transport policy review | https://developer.android.com/privacy-and-security/security-config | **Verified URL** | Parts 2, 5, 7 |
| Play Integrity API / Google | Device/app integrity signal | https://developer.android.com/google/play/integrity | **Verified URL; check current recommended use** | Parts 2, 5, 7 |
| Apple Platform Security / Apple | Apple platform controls | https://support.apple.com/guide/security/welcome/web | **Verified URL; current guide content verify before use** | Parts 2, 5, 7 |
| Apple Developer Security / Apple | Security overview | https://developer.apple.com/security/ | **Verified URL** | Parts 2, 7 |
| Keychain Services / Apple | Secure secret storage | https://developer.apple.com/documentation/security/keychain-services | **Verified URL** | Parts 2, 5, 7 |
| NSAppTransportSecurity / Apple | ATS configuration | https://developer.apple.com/documentation/bundleresources/information-property-list/nsapptransportsecurity | **Verified canonical path; checked 2026-10-16** | Parts 2, 5, 7 |
| RFC 6749 / RFC Editor | OAuth 2.0 framework | https://www.rfc-editor.org/rfc/rfc6749 | **Verified RFC 6749** | Parts 1–3, 5, 7 |
| RFC 9700 / RFC Editor | OAuth 2.0 security best current practice | https://www.rfc-editor.org/rfc/rfc9700 | **Verified RFC 9700** | Parts 1–3, 5, 7 |
| RFC 7519 / RFC Editor | JSON Web Token | https://www.rfc-editor.org/rfc/rfc7519 | **Verified RFC 7519** | Parts 1–3, 5, 7 |
| OpenID Connect specifications / OpenID Foundation | OpenID Connect protocol | https://openid.net/developers/specs/ | **Verified URL; select applicable specification/version before use** | Parts 1–3, 5, 7 |
| RFC 7636 / RFC Editor | OAuth 2.0 proof-key protection (PKCE) | https://www.rfc-editor.org/rfc/rfc7636 | **Verified RFC URL; apply only where relevant** | Parts 1–3, 5, 7 |
| RFC 8725 / RFC Editor | JWT implementation security guidance | https://www.rfc-editor.org/rfc/rfc8725 | **Verified RFC URL; select guidance applicable to the implementation** | Parts 1–3, 5, 7 |

### Control and section pointers

- MASVS control families `MASVS-STORAGE`, `MASVS-CRYPTO`, `MASVS-AUTH`, `MASVS-NETWORK`, `MASVS-PLATFORM`, `MASVS-CODE`, `MASVS-RESILIENCE`, and `MASVS-PRIVACY` support the mobile rules in Parts 2, 3, 5, and 7; use the current control text rather than assuming a fixed release label.
- OWASP API Security Top 10:2023 entries `API1` through `API10` support authorization, resource-consumption, business-flow, configuration, inventory, and unsafe-consumption checks where the official portal confirms that edition remains applicable.
- RFC 6749, RFC 9700, and RFC 7636 support OAuth flow and client-protection review; RFC 7519 and RFC 8725 support JWT validation and algorithm-handling review.
- The OWASP Cheat Sheet Series, including its password-storage, cryptographic-storage, secrets-management, and session-management guidance, supports Parts 2, 5, and 7. Consult the current individual sheet before prescribing an implementation or parameter.

## Tool documentation

| Tool / maintainer | Use | Canonical URL | Status / limitation | Used by |
|---|---|---|---|---|
| Checkmarx / Checkmarx | SAST/SCA docs | https://docs.checkmarx.com/ | **Verified URL; product/access depends on organization** | Part 4 |
| SonarQube / SonarSource | Static analysis | https://docs.sonarsource.com/ | **Verified publisher docs; product page path changed, inspect current docs before use** | Part 4 |
| Semgrep / Semgrep | Static/code/supply-chain/secrets analysis | https://docs.semgrep.dev/ | **Verified canonical redirect** | Part 4 |
| Snyk / Snyk | Dependency/code/container/cloud scanning | https://docs.snyk.io/ | **Verified URL; enabled products/access vary** | Part 4 |
| Dependabot / GitHub | Dependency updates/security workflows | https://docs.github.com/en/code-security/how-tos/secure-your-supply-chain | **Verified canonical redirect** | Part 4 |
| OWASP Dependency-Check / OWASP project | Known-vulnerable component candidates | https://jeremylong.github.io/DependencyCheck/ | **Verified URL; identity false positives/negatives possible** | Part 4 |
| MobSF / Mobile Security Framework | Mobile analysis | https://mobsf.github.io/docs/ | **Verified URL; deployment/features verify before use** | Part 4 |
| OWASP ZAP / ZAP Dev Team | Authorized DAST | https://www.zaproxy.org/docs/ | **Verified URL** | Part 4 |
| Gitleaks / gitleaks project | Secret detection | https://github.com/gitleaks/gitleaks | **Verified official maintained repository; protect scan output** | Part 4 |
| TruffleHog / Truffle Security | Secret detection | https://trufflesecurity.com/docs | **Verified canonical redirect** | Part 4 |
| Trivy / Aqua Security | Container/IaC/artifact scanning | https://trivy.dev/docs/latest/guide/ | **Verified canonical redirect** | Part 4 |

## Selection rules and uncertainty

Consult the primary publisher first, then the exact edition/control/rule relevant to the supplied technology. Tool repositories may be an official source where they are maintained by the project; they are not a claim that the tool is installed, licensed, configured, or authorized. For password storage, cryptography, TLS, key management, authorization, and library selection, use current vendor/standards documentation suited to the language/platform; no unverified version or compatibility claim should be copied from this library.
